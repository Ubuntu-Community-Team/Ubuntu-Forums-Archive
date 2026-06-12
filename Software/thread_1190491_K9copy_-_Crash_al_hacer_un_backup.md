---
title: "K9copy - Crash al hacer un backup"
date: 2009-06-17
forum: Software
---

### Post by NickCis on 2009-06-17
Hola, quiero hacer un backup de un dvd. Depsues de configurar como qiero que lo guarde (que le baje el tamaño, etc,etc ), hago click en copy. Despues de un rato, el k9copy se cierra.
Si lo ejecuto por consola me devuelve este error:
```
newpc@newpc-desktop:~$ k9copy
Object::connect: No such signal k9Process::wroteStdin( KProcess* )
Object::connect:  (receiver name: 'MPlayer')
QString::arg: Argument missing: totalSize(9.96131e+07)=gettotalSize()(6.45775e+09)+menuSize(1.12908e+08) -(fforced(6.32163e+09))-m_inbytes(0), 0
"totalSize(9.96131e+07)=gettotalSize()(6.45775e+09)+menuSize(1.12908e+08) -(fforced(6.32163e+09))-m_inbytes(0)"
"minfactor(1.40041)=(fforced(6.32163e+09) -m_frinbytes(0))/(MacSize(4.61373e+09)-totalSize(9.96131e+07)-m_outbytes(0) - m_frcoutbytes(0))"
QString::arg: Argument missing: totalSize(3.93732e+07)=gettotalSize()(6.45775e+09)+menuSize(1.12908e+08) -(fforced(6.32163e+09))-m_inbytes(0), 150599680
"totalSize(3.93732e+07)=gettotalSize()(6.45775e+09)+menuSize(1.12908e+08) -(fforced(6.32163e+09))-m_inbytes(0)"
"minfactor(1.41811)=(fforced(6.32163e+09) -m_frinbytes(0))/(MacSize(4.61373e+09)-totalSize(3.93732e+07)-m_outbytes(116570112) - m_frcoutbytes(0))"
force factor : 1.430000   min:1.418107
"First video packet in sequence starting at 2062 misses PTS or DTS, flags=1"
Unable to start Dr. Konqi
newpc@newpc-desktop:~$

```

y si lo ejecuto normalmente, me devuelve esto:

```
Aplicación: k9copy (k9copy), señal SIGSEGV
[Current thread is 0 (LWP 16310)]

Thread 3 (Thread 0xb06e5b90 (LWP 16318)):
#0  0xb80d9430 in __kernel_vsyscall ()
#1  0xb60ce0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb64a62ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb66bf902 in ?? () from /usr/lib/libQtCore.so.4
#4  0xb66baf05 in QMutex::lock () from /usr/lib/libQtCore.so.4
#5  0x0813c1fa in ?? ()
#6  0x080752bd in _start ()

Thread 2 (Thread 0xb1ae8b90 (LWP 16360)):
[KCrash Handler]
#6  0xb60cb9e0 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb64a64b6 in pthread_mutex_lock () from /lib/tls/i686/cmov/libc.so.6
#8  0xb66c0e90 in QWaitCondition::wakeAll () from /usr/lib/libQtCore.so.4
#9  0x081521ab in ?? ()
#10 0x08152cc5 in ?? ()
#11 0x08153f17 in ?? ()
#12 0x081541bc in ?? ()
#13 0x08154486 in ?? ()
#14 0xb66c025e in ?? () from /usr/lib/libQtCore.so.4
#15 0xb60ca4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb649749e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb5bd7700 (LWP 16310)):
#0  0xb80d9430 in __kernel_vsyscall ()
#1  0xb648f7b1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb5dcfca7 in ?? () from /usr/lib/libxcb.so.1
#3  0xb5dd030e in ?? () from /usr/lib/libxcb.so.1
#4  0xb5dd06b7 in xcb_writev () from /usr/lib/libxcb.so.1
#5  0xb6271afa in _XSend () from /usr/lib/libX11.so.6
#6  0xb6271c23 in _XReply () from /usr/lib/libX11.so.6
#7  0xb624e3b9 in XGetImage () from /usr/lib/libX11.so.6
#8  0xb6d4405f in QX11PixmapData::toImage () from /usr/lib/libQtGui.so.4
#9  0xb6d318bb in QPixmap::toImage () from /usr/lib/libQtGui.so.4
#10 0xb6d65233 in QBrush::textureImage () from /usr/lib/libQtGui.so.4
#11 0xb6e0a7d1 in ?? () from /usr/lib/libQtGui.so.4
#12 0xb6e0b86b in ?? () from /usr/lib/libQtGui.so.4
#13 0xb6e0fff9 in ?? () from /usr/lib/libQtGui.so.4
#14 0xb6d9bd2c in QPainter::drawPath () from /usr/lib/libQtGui.so.4
#15 0xb6d95baf in ?? () from /usr/lib/libQtGui.so.4
#16 0xb6d982e8 in QPainter::drawRects () from /usr/lib/libQtGui.so.4
#17 0xb6d991a2 in QPainter::drawPixmap () from /usr/lib/libQtGui.so.4
#18 0x0813c174 in ?? ()
#19 0xb6cb869e in QWidget::event () from /usr/lib/libQtGui.so.4
#20 0xb6c61bcc in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#21 0xb6c69fc2 in QApplication::notify () from /usr/lib/libQtGui.so.4
#22 0xb7f12e0d in KApplication::notify () from /usr/lib/libkdeui.so.5
#23 0xb67b449b in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#24 0xb6c6cd2e in QCoreApplication::sendSpontaneousEvent () from /usr/lib/libQtGui.so.4
#25 0xb6cc0439 in QWidgetPrivate::drawWidget () from /usr/lib/libQtGui.so.4
#26 0xb6cc0bde in QWidgetPrivate::paintSiblingsRecursive () from /usr/lib/libQtGui.so.4
#27 0xb6cc002a in QWidgetPrivate::drawWidget () from /usr/lib/libQtGui.so.4
#28 0xb6cc0bde in QWidgetPrivate::paintSiblingsRecursive () from /usr/lib/libQtGui.so.4
#29 0xb6cc002a in QWidgetPrivate::drawWidget () from /usr/lib/libQtGui.so.4
#30 0xb6cc0bde in QWidgetPrivate::paintSiblingsRecursive () from /usr/lib/libQtGui.so.4
#31 0xb6cc002a in QWidgetPrivate::drawWidget () from /usr/lib/libQtGui.so.4
#32 0xb6e7edca in ?? () from /usr/lib/libQtGui.so.4
#33 0xb6cb0ee6 in QWidgetPrivate::syncBackingStore () from /usr/lib/libQtGui.so.4
#34 0xb6cb8b05 in QWidget::event () from /usr/lib/libQtGui.so.4
#35 0xb6c61bcc in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#36 0xb6c69fc2 in QApplication::notify () from /usr/lib/libQtGui.so.4
#37 0xb7f12e0d in KApplication::notify () from /usr/lib/libkdeui.so.5
#38 0xb67b449b in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#39 0xb67b50f5 in QCoreApplicationPrivate::sendPostedEvents () from /usr/lib/libQtCore.so.4
#40 0xb67b52ed in QCoreApplication::sendPostedEvents () from /usr/lib/libQtCore.so.4
#41 0xb67e027f in ?? () from /usr/lib/libQtCore.so.4
#42 0xb5e85b88 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#43 0xb5e890eb in ?? () from /usr/lib/libglib-2.0.so.0
#44 0xb5e89268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#45 0xb67dfec8 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#46 0xb6d03765 in ?? () from /usr/lib/libQtGui.so.4
#47 0xb67b5566 in QCoreApplication::processEvents () from /usr/lib/libQtCore.so.4
#48 0x0806e5cf in _start ()

```

Alguna idea?

Saludos :P

Edit:
Si desactivo "Enable prohibited user operations" de el menu de opciones del k9copy, me devuelve esto:
```
Esta traza inversa parece inútil.
Probablemente se deba a que sus paquetes están generados de forma que eviten la creación de trazas inversas adecuados, o la pila se ha corrompido seriamente durante el fallo de la aplicación.

```

---

### Post by NickCis on 2009-06-18
Es un bug?, lo debo reportar?.

Saludos...

---

### Post by pablo.s on 2009-06-18
> **NickCis said:**
> Es un bug?, lo debo reportar?.

Está [reportado]("https://bugs.launchpad.net/ubuntu/+source/k9copy/+bug/105909").

---

