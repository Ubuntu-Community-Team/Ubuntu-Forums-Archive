---
title: "(firefox-bin:3141): GLib-WARNING **: g_set_prgname() called multiple times"
date: 2010-10-19
forum: Software
---

### Post by mama21mama on 2010-10-19
me salio este mensaje al iniciar el firefox

> mama@zeusa:~$ /opt/firefox/firefox

(firefox-bin:3141): GLib-WARNING **: g_set_prgname() called multiple times
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkTreeView::odd-row-color' of type `GdkColor' from rc file value "((GString*) 0xb68ceb90)" of type `GString'


ando mirando [este link]("http://ubuntuforums.org/showthread.php?t=1349192&page=2") 

Alguna idea?. Saludos

---

### Post by alfplayer on 2010-10-19
Pero hay un problema en Firefox?

---

### Post by mama21mama on 2010-10-19
No inicia.

solo inicia con ```
/opt/firefox/firefox --safe-mode
```

---

### Post by alfplayer on 2010-10-19
Probablemente es causado por una extensión. Probá deshabilitar extensiones hasta que encuentres la responsable.

---

### Post by mama21mama on 2010-10-19
desabilite la **prism** y furula bien.
Gracias, saludos.

---

