/**
 * JURNAL REFLEKSI DIGITAL GURU
 * script.js — PDF Export & UX Enhancements
 */

/* ── Restore placeholder behaviour for contenteditable ── */
document.querySelectorAll('[contenteditable]').forEach(el => {
  // On focus: clear placeholder appearance
  el.addEventListener('focus', () => {
    if (el.textContent.trim() === '') el.textContent = '';
  });

  // On blur: if empty, keep placeholder via CSS :empty
  el.addEventListener('blur', () => {
    if (el.textContent.trim() === '') el.textContent = '';
  });

  // Prevent paste from carrying rich HTML formatting
  el.addEventListener('paste', e => {
    e.preventDefault();
    const text = (e.clipboardData || window.clipboardData).getData('text/plain');
    document.execCommand('insertText', false, text);
  });
});

/* ── Auto-fill today's date (helper, non-intrusive) ── */
(function autoDate() {
  const dateFields = document.querySelectorAll('.editable-field[data-placeholder*="Tanggal"]');
  if (dateFields.length) {
    const today = new Date();
    const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
    const formatted = today.toLocaleDateString('id-ID', options);
    dateFields.forEach(f => {
      if (!f.textContent.trim()) f.textContent = formatted;
    });
  }
})();

/* ── PDF Download ── */
function unduhPDF() {
  const btn = document.getElementById('btnUnduh');
  const page = document.getElementById('jurnalPage');

  if (!page) {
    alert('Halaman jurnal tidak ditemukan.');
    return;
  }

  // Disable button to prevent double-click
  btn.disabled = true;
  btn.innerHTML = `
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" style="animation:spin 1s linear infinite;width:16px;height:16px">
      <circle cx="12" cy="12" r="10" stroke-dasharray="31.4" stroke-dashoffset="10"/>
    </svg>
    Menyiapkan PDF...
  `;

  // Temporarily remove dashed borders and focus styles for clean print
  const editables = page.querySelectorAll('[contenteditable]');
  editables.forEach(el => {
    el.dataset.prevOutline = el.style.outline;
    el.style.outline = 'none';
    el.blur();
  });

  // Build filename from teacher name if filled
  let namaGuru = '';
  const namaField = page.querySelectorAll('.editable-field')[1];
  if (namaField && namaField.textContent.trim()) {
    namaGuru = '_' + namaField.textContent.trim().replace(/\s+/g, '_');
  }
  const filename = `Jurnal_Refleksi_Guru${namaGuru}.pdf`;

  const opt = {
    margin:       [8, 10, 8, 10],   // mm: top, right, bottom, left
    filename:     filename,
    image:        { type: 'jpeg', quality: 0.97 },
    html2canvas:  {
      scale:       2,
      useCORS:     true,
      letterRendering: true,
      logging:     false,
      backgroundColor: '#ffffff'
    },
    jsPDF: {
      unit:        'mm',
      format:      'a4',
      orientation: 'portrait'
    },
    pagebreak: { mode: ['avoid-all', 'css', 'legacy'] }
  };

  html2pdf()
    .set(opt)
    .from(page)
    .save()
    .then(() => {
      // Restore button
      btn.disabled = false;
      btn.innerHTML = `
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M21 15v4a2 2 0 01-2 2H5a2 2 0 01-2-2v-4"/>
          <polyline points="7 10 12 15 17 10"/>
          <line x1="12" y1="15" x2="12" y2="3"/>
        </svg>
        Unduh PDF
      `;
      // Restore outlines
      editables.forEach(el => {
        el.style.outline = el.dataset.prevOutline || '';
      });
    })
    .catch(err => {
      console.error('PDF error:', err);
      btn.disabled = false;
      btn.textContent = 'Coba Lagi';
      alert('Gagal membuat PDF. Pastikan koneksi internet aktif (untuk CDN html2pdf.js) lalu coba lagi.');
    });
}

/* ── Spinner keyframes ── */
const style = document.createElement('style');
style.textContent = `
  @keyframes spin {
    from { transform: rotate(0deg); }
    to   { transform: rotate(360deg); }
  }
`;
document.head.appendChild(style);

/* ── Keyboard shortcut: Ctrl+P & Ctrl+S → trigger PDF ── */
document.addEventListener('keydown', e => {
  if ((e.ctrlKey || e.metaKey) && (e.key === 's' || e.key === 'p')) {
    e.preventDefault();
    unduhPDF();
  }
});
