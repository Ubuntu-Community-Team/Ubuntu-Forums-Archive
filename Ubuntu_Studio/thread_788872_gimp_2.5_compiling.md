---
title: "gimp 2.5 compiling"
date: 2008-05-10
forum: Ubuntu Studio
---

### Post by hibernaculus on 2008-05-10
Hi guys,

 I have the problem with gimp 2.5 (exactly gegl 0.0.16 library) compiling...

 Below is log from terminal: 

 "make[4]: Wej&#347;cie do katalogu `/home/piotrk/gimp_2.5/gegl-0.0.16/docs/gallery'
--[Updating sample compositions]--
./clones.xml

(process:19985): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GeglHandler'
**
** ERROR:(gegl-buffer.c:345):gegl_buffer_constructor: assertion failed: (backend)
/bin/bash: line 1: 19985 Aborted                 GEGL_DEBUG_TIME=yes GEGL_PATH=../../operations ../../bin/gegl clones.xml -o `echo clones.png | sed s?./??` > `echo clones.png | sed s?./?? | sed -e s/png/txt/`
make[5]: *** [clones.png] B&#322;&#261;d 134
./OpenRaster-00.xml

(process:20015): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GeglHandler'
**
** ERROR:(gegl-buffer.c:345):gegl_buffer_constructor: assertion failed: (backend)
/bin/bash: line 1: 20015 Aborted                 GEGL_DEBUG_TIME=yes GEGL_PATH=../../operations ../../bin/gegl OpenRaster-00.xml -o `echo OpenRaster-00.png | sed s?./??` > `echo OpenRaster-00.png | sed s?./?? | sed -e s/png/txt/`
make[5]: *** [OpenRaster-00.png] B&#322;&#261;d 134
./OpenRaster-01.xml

(process:20045): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GeglHandler'
**
** ERROR:(gegl-buffer.c:345):gegl_buffer_constructor: assertion failed: (backend)
/bin/bash: line 1: 20045 Aborted                 GEGL_DEBUG_TIME=yes GEGL_PATH=../../operations ../../bin/gegl OpenRaster-01.xml -o `echo OpenRaster-01.png | sed s?./??` > `echo OpenRaster-01.png | sed s?./?? | sed -e s/png/txt/`
make[5]: *** [OpenRaster-01.png] B&#322;&#261;d 134
./OpenRaster-04.xml

(process:20076): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GeglHandler'
**
** ERROR:(gegl-buffer.c:345):gegl_buffer_constructor: assertion failed: (backend)
/bin/bash: line 1: 20076 Aborted                 GEGL_DEBUG_TIME=yes GEGL_PATH=../../operations ../../bin/gegl OpenRaster-04.xml -o `echo OpenRaster-04.png | sed s?./??` > `echo OpenRaster-04.png | sed s?./?? | sed -e s/png/txt/`
make[5]: *** [OpenRaster-04.png] B&#322;&#261;d 134
make[4]: *** [images.stamp] B&#322;&#261;d 2
make[4]: Opuszczenie katalogu `/home/piotrk/gimp_2.5/gegl-0.0.16/docs/gallery'
make[3]: *** [all-recursive] B&#322;&#261;d 1
make[3]: Opuszczenie katalogu `/home/piotrk/gimp_2.5/gegl-0.0.16/docs/gallery'
make[2]: *** [all-recursive] B&#322;&#261;d 1
make[2]: Opuszczenie katalogu `/home/piotrk/gimp_2.5/gegl-0.0.16/docs'
make[1]: *** [all-recursive] B&#322;&#261;d 1
make[1]: Opuszczenie katalogu `/home/piotrk/gimp_2.5/gegl-0.0.16'
make: *** [all] B&#322;&#261;d 2
"

 Thx for any advice (maybe glib version wrong? i don't know)

--
hibernaculus

---

### Post by Gvorcek48 on 2008-09-10
I've been searching for answer and found nothing... The post is so old, but still actual for my gimp 2.5.3.

So, for fix this you must use ./configure --disable-docs when compiling gegl, thats helps.

---

### Post by hibernaculus on 2008-09-10
thank you for advice :)

---

### Post by Dave_Connor on 2008-09-12
Just a suggestion since compiling isn't managed by the package manager I would just download a 32bit deb of GIMP-2.5 and getlibs to install the extra libs you need and it runs great on my system.

---

