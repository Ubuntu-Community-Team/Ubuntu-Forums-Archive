---
title: "efecto agua compiz y amarok en ubuntu 9.4"
date: 2009-04-26
forum: Software
---

### Post by DarkGatox on 2009-04-26
bueno, ayer actualize de intrepid a jaunty y ya no me funciona el efecto de lluvia de compiz, ni tampoco el amarok, el amarok se actualizo a la version 2 y cuando lo inicio me aparece 
algo asi
```
amarok(27464) Phonon::KdePlatformPlugin::createBackend: using backend:  "GStreamer"
Object::connect: No such slot MainWindow::showStatistics() in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/MainWindow.cpp:692
Object::connect:  (receiver name: 'MainWindow')
QLayout: Attempting to add QLayout "" to MainWindow "MainWindow", which already has a layout
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
amarok(27464) Plasma::Applet::save: saving to "1"
amarok(27464) Context::ContextView::setContainment: "" Line:  599
amarok(27464) Plasma::ThemePrivate::config: using theme for app "amarok"
amarok(27464) Plasma::Applet::save: saving to "2"
amarok(27464) Plasma::Applet::save: saving to "3"
amarok(27464) Plasma::Applet::save: saving to "4"
amarok(27464) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(27464) Context::ColumnContainment::insertInGrid: "" Line:  603
amarok(27464) LyricsApplet::init: Loading theme file:  "/usr/share/kde4/apps/amarok/images/web_applet_background.svg"
amarok(27464) Context::ColumnContainment::insertInGrid: "" Line:  603
amarok(27464) Context::ColumnContainment::insertInGrid: "" Line:  603
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
Object::connect: No such slot FileBrowser::Widget::setDir( const QString& ) in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/browsers/filebrowser/FileBrowser.cpp:112
Object::connect:  (sender name:   'KBookmarkHandler')
Object::connect:  (receiver name: 'FileBrowser::Widget')
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
amarok(27464) MagnatuneConfig::load: load
systemroot@systemroot-desktop:~$ amarok(27464) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(27464) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(27464) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x6e00064
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
amarok(27464) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(27464) Amarok::TrayIcon::event: "" Line:  115
amarok(27464) Context::ContextView::clear: "" Line:  165
amarok(27464) Context::ContextView::clear: "" Line:  165
amarok(27464) Context::ContextView::clear: "" Line:  165
amarok(27464) Context::ContextView::clear: "" Line:  165


```

y no reproduce ninguna cancion, si alguien me ayuda se lo agradesco

---

### Post by Hei Ku on 2009-04-26
Para el Amarok:

sudo apt-get install libxine1-ffmpeg

Aca esta el bug reportado:
[https://bugs.launchpad.net/ubuntu/+source/amarok2/+bug/348104](https://bugs.launchpad.net/ubuntu/+source/amarok2/+bug/348104)

Para el efecto lluvia: soy pelado, asi que el efecto mojado no me va. :D
(Uso KDE4, asi que ni idea)

---

### Post by josecuervo86 on 2009-04-26
A mi el efecto agua me anda, pero solo el de la lluvia. El de la olita cuando apretas Ctrl + Super + boton izq no me anda mas :(

---

### Post by leosr on 2009-06-01
> **josecuervo86 said:**
> A mi el efecto agua me anda, pero solo el de la lluvia. El de la olita cuando apretas Ctrl + Super + boton izq no me anda mas :(

A mi tampoco..

---

### Post by sajnox on 2009-06-01
Postea la salida de

```
aptitude search compiz 
```

---

### Post by josecuervo86 on 2009-06-01
aca va la mia

```
josecuervo86@josecuervo86-desktop:~$ aptitude search compiz
i   compiz                          - OpenGL window and compositing manager     
i   compiz-core                     - OpenGL window and compositing manager     
p   compiz-dev                      - OpenGL window and compositing manager - de
p   compiz-fusion-bcop              - Compiz option code generator              
i   compiz-fusion-plugins-extra     - Collection of extra plugins from OpenCompo
i   compiz-fusion-plugins-main      - Collection of plugins from OpenCompositing
p   compiz-fusion-plugins-unsupport - Compiz Fusion plugins - "unsupported" coll
i   compiz-gnome                    - OpenGL window and compositing manager - GN
p   compiz-kde                      - OpenGL window and compositing manager - KD
i   compiz-plugins                  - OpenGL window and compositing manager - pl
i A compiz-wrapper                  - OpenGL window and compositing manager, wra
i   compizconfig-backend-gconf      - Settings library for plugins - OpenComposi
p   compizconfig-backend-kconfig    - KConfig Settings library for plugins - Ope
i   compizconfig-settings-manager   - Compiz configuration settings manager     
v   gcompizthemer                   -                                           
p   kicker-taskbar-compiz           - modified Kicker taskbar applet made to wor
i   libcompizconfig0                - Settings library for plugins - OpenComposi
p   libcompizconfig0-dev            - Development file for plugin settings - Ope
i A python-compizconfig             - Compiz configuration system bindings  
```

---

### Post by jpmorelli on 2009-06-04
No será que ahora la olita es parte del paquete

compiz-fusion-plugins-unsupport

No lo puedo probar ahora y ese efecto no lo uso pero supongo que puede ser eso.
Suerte !

---

### Post by santiagoward2000 on 2009-06-04
> **jmorelli said:**
> No será que ahora la olita es parte del paquete

compiz-fusion-plugins-unsupport

No lo puedo probar ahora y ese efecto no lo uso pero supongo que puede ser eso.
Suerte !

No, yo instalé el **unsupported** y tampoco me anda (la opción está en ccsm, pero igual no anda).

---

