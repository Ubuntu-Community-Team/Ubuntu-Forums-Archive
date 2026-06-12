---
title: "Kmess en Gnome (se tilda y se cierra)"
date: 2009-10-14
forum: Software
---

### Post by miloo on 2009-10-14
Hola gentee! Tengo un problema con mi cliente de mensajeria Kmess.. creo que el drama tiene que ver mas que nada con el hecho de que sea para KDE. Si bien funciona en Gnome (y es el entorno que yo uso), en un cierto punto se tilda el programa, me avisa que "No se puede cerrar normalmente y que si quiero Forzar cerrar", y eso que nunca le puse cerrar ni nada parecido. Siempre sucede cuando lo hago trabajar, que me muestre los contactos, o al abrir una conversación o casos por el estilo.

El error que me tira (en una ventanita) al cerrarse del todo es:


A Fatal Error Occurred
The application KMess (kmess) crashed and caused the signal 6 (SIGABRT).


y desplegando los detalles me muestra:

```

Application: KMess (kmess), signal SIGABRT
[Current thread is 0 (LWP 4538)]

Thread 3 (Thread 0xafbe4b90 (LWP 4711)):
#0  0xb80a0430 in __kernel_vsyscall ()
#1  0xb59fa0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb5dc32ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb6aff9b2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#4  0xb6a0b152 in ?? () from /usr/lib/libQtNetwork.so.4
#5  0xb6afe96e in ?? () from /usr/lib/libQtCore.so.4
#6  0xb59f64ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb5db449e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xaf125b90 (LWP 4755)):
#0  0xb80a0430 in __kernel_vsyscall ()
#1  0xb5dac7b1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb6bd0380 in ?? () from /usr/lib/libQtCore.so.4
#3  0xb6afe96e in ?? () from /usr/lib/libQtCore.so.4
#4  0xb59f64ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#5  0xb5db449e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb5756700 (LWP 4538)):
[KCrash Handler]
#6  0xb80a0430 in __kernel_vsyscall ()
#7  0xb5cfb6d0 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb5cfd098 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0x081dccc0 in CrashHandler::kmessCrashed ()
#10 <signal handler called>
#11 0xb669b333 in QSortFilterProxyModel::parent () from /usr/lib/libQtGui.so.4
#12 0xb6655aeb in ?? () from /usr/lib/libQtGui.so.4
#13 0xb6655dcb in ?? () from /usr/lib/libQtGui.so.4
#14 0xb6655ee7 in QTreeView::viewportEvent () from /usr/lib/libQtGui.so.4
#15 0xb656bf55 in ?? () from /usr/lib/libQtGui.so.4
#16 0xb6bf1c5a in QCoreApplicationPrivate::sendThroughObjectEventFilters () from /usr/lib/libQtCore.so.4
#17 0xb6098e7a in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#18 0xb60a0723 in QApplicationPrivate::dispatchEnterLeave () from /usr/lib/libQtGui.so.4
#19 0xb60a0d7a in QApplicationPrivate::sendMouseEvent () from /usr/lib/libQtGui.so.4
#20 0xb611097e in ?? () from /usr/lib/libQtGui.so.4
#21 0xb610fca7 in QApplication::x11ProcessEvent () from /usr/lib/libQtGui.so.4
#22 0xb613ac6a in ?? () from /usr/lib/libQtGui.so.4
#23 0xb5928b88 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#24 0xb592c0eb in ?? () from /usr/lib/libglib-2.0.so.0
#25 0xb592c268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#26 0xb6c1e438 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#27 0xb613a365 in ?? () from /usr/lib/libQtGui.so.4
#28 0xb6bf106a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#29 0xb6bf14aa in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#30 0xb6bf3959 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#31 0xb6098d17 in QApplication::exec () from /usr/lib/libQtGui.so.4
#32 0x08231581 in main ()

```

por ahí encontre que una causa puede ser que las librerias Qt deben ser actualizadas a la version 4.5.2, y en Ubuntu 9.04 tengo la version 4.5.0 y bueno... No se como actualizar :(


Datos de mi sistema:

Ubuntu 9.04 jaunty
Nucleo Linux 2.6.28-15-generic
Gnome 2.26.21
 
Procesador AMD Sempron(tm) 3400+
Memoria RAM de 1,5 GB

Gracias! :)

---

