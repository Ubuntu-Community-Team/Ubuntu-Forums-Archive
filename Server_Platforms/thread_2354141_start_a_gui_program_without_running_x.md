---
title: "start a gui program without running x"
date: 2017-02-28
forum: Server Platforms
---

### Post by asgard2 on 2017-02-28
Hello,

is it possible to start a gui program without the gui output from ssh (or redirect it to a fake screen)?

I need to start a few calculations, this could take a few days.

The calculation program starts a GUI, but I do not need to interact.

Using ssh -X makes it much slower and I can not disconnect.

Regards,
asgard2

___
I found a possible solution with xvfb-run -a , but the program is crashing:
[http://askubuntu.com/questions/50599/how-do-you-run-a-gui-application-without-gui-gui-application-as-daemon-on-headl](http://askubuntu.com/questions/50599/how-do-you-run-a-gui-application-without-gui-gui-application-as-daemon-on-headl)

> Unsupported screen format: depth: 8, red_mask: 0, blue_mask: 0
QXcbIntegration: Cannot create platform OpenGL context, neither GLX nor EGL are enabled
Unsupported screen format: depth: 8, red_mask: 0, blue_mask: 0
QXcbIntegration: Cannot create platform OpenGL context, neither GLX nor EGL are enabled
Unsupported screen format: depth: 8, red_mask: 0, blue_mask: 0
Unsupported screen format: depth: 8, red_mask: 0, blue_mask: 0
Unsupported screen format: depth: 8, red_mask: 0, blue_mask: 0
Unsupported screen format: depth: 8, red_mask: 0, blue_mask: 0
Unsupported screen format: depth: 8, red_mask: 0, blue_mask: 0
Unsupported screen format: depth: 8, red_mask: 0, blue_mask: 0
Unsupported screen format: depth: 8, red_mask: 0, blue_mask: 0
Unsupported screen format: depth: 8, red_mask: 0, blue_mask: 0
QWidget::paintEngine: Should no longer be called
QPainter::begin: Paint device returned engine == 0, type: 1
QWidget::paintEngine: Should no longer be called
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::save: Painter not active
Caught signal SIGSEGV!
Trying to force 'normal' shutdown ...
(next signal will force an immediate exit)


my current config:

xvfb-run -a -e ${datafolder}/${file}_screen.log -s '-screen 0 1280x800x24 -ac +extension GLX +render -noreset'

returns:
/usr/bin/xvfb-run: 184: /usr/bin/xvfb-run: 0: not found


Any hint?

thx

---

