---
title: "Error al iniciar plasma luego de logear (Ubuntu 9.10 con KDE 4.3.4)"
date: 2009-12-06
forum: Software
---

### Post by emiliano_raso on 2009-12-06
Luego de iniciar sesión, me aparece el siguiente aviso, y plasma no inicia.
Ayer funcionaba bien. Apagué la computadora, hoy temprano la prendí y dejó de funcionar KDE.
No hice ninguna actualización, ni ninguna modificación.

Alguien sabe cual es el problema?

Saludos, gracias.

---

### Post by emiliano_raso on 2009-12-06
Esto es lo que me dice la pestaña "Para desarrolladores"
```
Application: Área de trabajo de Plasma (kdeinit4), signal: Segmentation fault
[KCrash Handler]
#6  0x053926ce in Plasma::Applet::flushPendingConstraintsEvents() () from /usr/lib/libplasma.so.3
#7  0x053b67fd in Plasma::Corona::loadLayout(QString const&) () from /usr/lib/libplasma.so.3
#8  0x053b78de in Plasma::Corona::initializeLayout(QString const&) () from /usr/lib/libplasma.so.3
#9  0x014aa1d6 in ?? () from /usr/lib/libkdeinit4_plasma-desktop.so
#10 0x014aa4da in ?? () from /usr/lib/libkdeinit4_plasma-desktop.so
#11 0x014aa733 in ?? () from /usr/lib/libkdeinit4_plasma-desktop.so
#12 0x0072e263 in QMetaObject::activate(QObject*, int, int, void**) () from /usr/lib/libQtCore.so.4
#13 0x0072eec2 in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#14 0x00733387 in ?? () from /usr/lib/libQtCore.so.4
#15 0x0073349c in ?? () from /usr/lib/libQtCore.so.4
#16 0x007283bf in QObject::event(QEvent*) () from /usr/lib/libQtCore.so.4
#17 0x03828f54 in QApplicationPrivate::notify_helper(QObject*, QEvent*) () from /usr/lib/libQtGui.so.4
#18 0x0383067c in QApplication::notify(QObject*, QEvent*) () from /usr/lib/libQtGui.so.4
#19 0x00fe31aa in KApplication::notify(QObject*, QEvent*) () from /usr/lib/libkdeui.so.5
#20 0x007186cb in QCoreApplication::notifyInternal(QObject*, QEvent*) () from /usr/lib/libQtCore.so.4
#21 0x007457ce in ?? () from /usr/lib/libQtCore.so.4
#22 0x007430e0 in ?? () from /usr/lib/libQtCore.so.4
#23 0x00844e88 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#24 0x00848730 in ?? () from /lib/libglib-2.0.so.0
#25 0x00848863 in g_main_context_iteration () from /lib/libglib-2.0.so.0
#26 0x0074302c in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#27 0x038c9be5 in ?? () from /usr/lib/libQtGui.so.4
#28 0x00716c79 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#29 0x007170ca in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#30 0x0071953f in QCoreApplication::exec() () from /usr/lib/libQtCore.so.4
#31 0x03828dd7 in QApplication::exec() () from /usr/lib/libQtGui.so.4
#32 0x0148d80d in kdemain () from /usr/lib/libkdeinit4_plasma-desktop.so
#33 0x0804dde1 in _start ()
```

---

### Post by emiliano_raso on 2009-12-06
SOLVED:
El problema es el applet de Google Traductor o el pyweather (tenia ambos asi que alguno de esos es).
Eliminando el archivo plasma-desktop-appletsrc en /home/USUARIO/.kde/share/config se eliminan las configuraciónes personalizadas de los applets y vuelve a recien instalado, entonces ya no está el applet problematico y lesto... problema solucionado.

Bueno... solucionado en cierto sentido. Porque ahora hay que saber porque no anda ese applet.

---

