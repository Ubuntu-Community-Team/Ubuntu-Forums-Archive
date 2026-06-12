---
title: "KDEnlive crashes on startup"
date: 2008-08-15
forum: Ubuntu Studio
---

### Post by tostrye on 2008-08-15
I installed kdenlive through the synaptic package manager in Hardy. I just searched synaptic for kdenlive and i installed what was there. When I go in a terminal and type kdenlive, it trys to start and then crashes. It says it is signal 11 and gives me a backtrace of:
> (no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb66e86c0 (LWP 7753)]
[New Thread 0xb35c2b90 (LWP 7772)]
[New Thread 0xb3dc3b90 (LWP 7771)]
[New Thread 0xb4fc6b90 (LWP 7770)]
[New Thread 0xb47c5b90 (LWP 7769)]
0xb7f6e410 in __kernel_vsyscall ()
#0  0xb7f6e410 in __kernel_vsyscall ()
#1  0xb6ada881 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb683fdff in _xcb_conn_wait (c=0x82c79d0, cond=0xbfb03008, vector=0x0, 
    count=0x0) at xcb_conn.c:342
#3  0xb6841bdd in xcb_wait_for_reply (c=0x82c79d0, request=24589, e=0xbfb03078)
    at xcb_in.c:344
#4  0xb766e1eb in _XReply (dpy=0x82c7490, rep=0xbfb030a0, extra=0, discard=1)
    at ../../src/xcb_io.c:364
#5  0xb765c230 in XQueryPointer (dpy=0x82c7490, w=82, root=0xbfb03120, 
    child=0xbfb0311c, root_x=0xbfb03118, root_y=0xbfb03114, win_x=0xbfb03110, 
    win_y=0xbfb0310c, mask=0xbfb03108) at ../../src/QuPntr.c:50
#6  0xb79a04a0 in QCursor::pos () from /usr/lib/libqt-mt.so.3
#7  0xb7bbaf74 in QTabBar::paint () from /usr/lib/libqt-mt.so.3
#8  0xb7bba76e in QTabBar::paintEvent () from /usr/lib/libqt-mt.so.3
#9  0xb7aa722b in QWidget::event () from /usr/lib/libqt-mt.so.3
#10 0xb7bb915d in QTabBar::event () from /usr/lib/libqt-mt.so.3
#11 0xb7a04c36 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#12 0xb7a07564 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#13 0xb6f77672 in KApplication::notify () from /usr/lib/libkdecore.so.4
#14 0xb799528d in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#15 0xb79d04af in QWidget::repaint () from /usr/lib/libqt-mt.so.3
#16 0xb7aae037 in QWidget::repaint () from /usr/lib/libqt-mt.so.3
#17 0xb7aac16c in QWidget::repaint () from /usr/lib/libqt-mt.so.3
#18 0xb7bb808c in QTab::setText () from /usr/lib/libqt-mt.so.3
#19 0xb6f6a34a in KAcceleratorManagerPrivate::calculateAccelerators ()
   from /usr/lib/libkdecore.so.4
#20 0xb6f6a889 in KAcceleratorManagerPrivate::manage ()
   from /usr/lib/libkdecore.so.4
#21 0xb6f6a95e in KAcceleratorManager::manage () from /usr/lib/libkdecore.so.4
#22 0xb6f6a995 in KAcceleratorManager::manage () from /usr/lib/libkdecore.so.4
#23 0xb6f6a9d3 in KCheckAccelerators::checkAccelerators ()
   from /usr/lib/libkdecore.so.4
#24 0xb6f6afaf in KCheckAccelerators::autoCheckSlot ()
   from /usr/lib/libkdecore.so.4
#25 0xb6f6b033 in KCheckAccelerators::qt_invoke ()
   from /usr/lib/libkdecore.so.4
#26 0xb7a70704 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#27 0xb7a711e9 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#28 0xb7e02320 in QTimer::timeout () from /usr/lib/libqt-mt.so.3
#29 0xb7a97d0e in QTimer::event () from /usr/lib/libqt-mt.so.3
#30 0xb7a04c36 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#31 0xb7a06a5f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#32 0xb6f77672 in KApplication::notify () from /usr/lib/libkdecore.so.4
#33 0xb799528d in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#34 0xb79f7b19 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#35 0xb79aa64b in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#36 0xb7a1ff90 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#37 0xb7a1fc8e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#38 0xb7a067df in QApplication::exec () from /usr/lib/libqt-mt.so.3
#39 0x081c5a9e in main ()

Can somebody tell me what I'm doing wrong?

---

### Post by Creative2 on 2008-08-16
try with this
[http://ubuntuforums.org/showthread.php?t=791355](http://ubuntuforums.org/showthread.php?t=791355)

---

### Post by tostrye on 2008-08-19
I was away for a few days dorry.
Thanks, that worked. But now I only can use a resolution of 800x600. I can go as high as 1920x1200. I use an ATI Radeon x300.

---

### Post by Creative2 on 2008-08-20
what did you do ?

there was only to install some packages ...

---

### Post by tostrye on 2008-08-20
It did install a few packages. Then I reset X, and my resolution went to 800x600. I played with xorg.conf, and that didn't work. So I reset it to what it was, but it is still at 800x600.

---

### Post by tostrye on 2008-08-20
Hi, I'm stupid. I re-installed flgrx and forgot to goto System>Hardware drivers And then Enable it.

---

### Post by Creative2 on 2008-08-20
then you should set solved this topic by clicking forum tools--> set as solved

---

