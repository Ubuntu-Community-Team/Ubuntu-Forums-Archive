---
title: "Problem to install rrdtool 1.3.6 from source"
date: 2009-03-31
forum: Server Platforms
---

### Post by rado3105 on 2009-03-31
I have problem to install rrdtool 1.3.6 from source, using ./configure, it shows this:

> IEEE Math Checks
checking for fpclassify... no
checking for fpclassify with <math.h>... yes
checking for isinf... yes
checking whether isfinite is broken... no
checking if IEEE math works out of the box... yes

Resolve Portability Issues
checking if msync with MS_ASYNC updates the files mtime... yes
checking for getopt_long... yes
checking if realloc can deal with NULL... yes
checking if ctime_r need special care to act posixly correct... no
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... no
checking whether pthreads work with -Kthread... no
checking whether pthreads work with -kthread... no
checking for the pthreads library -llthread... no
checking whether pthreads work with -pthread... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking for cc_r... gcc
checking do we need malloc/malloc.h... nope, works out of the box

Find 3rd-Party Libraries
checking for cairo_font_options_create in -lcairo... no
checking for pkg-config... pkg-config
configure: WARNING:
----------------------------------------------------------------------------
* I found a copy of pkgconfig, but there is no cairo-png.pc file around.
  You may want to set the PKG_CONFIG_PATH variable to point to its
  location.
----------------------------------------------------------------------------
			
configure: WARNING:
----------------------------------------------------------------------------
* I could not find a working copy of cairo-png. Check config.log for hints on why
  this is the case. Maybe you need to set LDFLAGS and CPPFLAGS appropriately
  so that compiler and the linker can find libcairo and its header files. If
  you have not installed cairo-png, you can get it either from its original home on

     [http://cairographics.org/releases/](http://cairographics.org/releases/)

  You can find also find an archive copy on

     [http://oss.oetiker.ch/rrdtool/pub/libs](http://oss.oetiker.ch/rrdtool/pub/libs)

  The last tested version of cairo-png is 1.4.6.

       LIBS=-lm 
   LDFLAGS=
  CPPFLAGS=

----------------------------------------------------------------------------
                
checking for cairo_svg_surface_create in -lcairo... no
checking for pkg-config... (cached) pkg-config
configure: WARNING:
----------------------------------------------------------------------------
* I found a copy of pkgconfig, but there is no cairo-svg.pc file around.
  You may want to set the PKG_CONFIG_PATH variable to point to its
  location.
----------------------------------------------------------------------------
			
configure: WARNING:
----------------------------------------------------------------------------
* I could not find a working copy of cairo-svg. Check config.log for hints on why
  this is the case. Maybe you need to set LDFLAGS and CPPFLAGS appropriately
  so that compiler and the linker can find libcairo and its header files. If
  you have not installed cairo-svg, you can get it either from its original home on

     [http://cairographics.org/releases/](http://cairographics.org/releases/)

  You can find also find an archive copy on

     [http://oss.oetiker.ch/rrdtool/pub/libs](http://oss.oetiker.ch/rrdtool/pub/libs)

  The last tested version of cairo-svg is 1.4.6.

       LIBS=-lm 
   LDFLAGS=
  CPPFLAGS=

----------------------------------------------------------------------------
                
checking for cairo_pdf_surface_create in -lcairo... no
checking for pkg-config... (cached) pkg-config
configure: WARNING:
----------------------------------------------------------------------------
* I found a copy of pkgconfig, but there is no cairo-pdf.pc file around.
  You may want to set the PKG_CONFIG_PATH variable to point to its
  location.
----------------------------------------------------------------------------
			
configure: WARNING:
----------------------------------------------------------------------------
* I could not find a working copy of cairo-pdf. Check config.log for hints on why
  this is the case. Maybe you need to set LDFLAGS and CPPFLAGS appropriately
  so that compiler and the linker can find libcairo and its header files. If
  you have not installed cairo-pdf, you can get it either from its original home on

     [http://cairographics.org/releases/](http://cairographics.org/releases/)

  You can find also find an archive copy on

     [http://oss.oetiker.ch/rrdtool/pub/libs](http://oss.oetiker.ch/rrdtool/pub/libs)

  The last tested version of cairo-pdf is 1.4.6.

       LIBS=-lm 
   LDFLAGS=
  CPPFLAGS=

----------------------------------------------------------------------------
                
checking for cairo_ps_surface_create in -lcairo... no
checking for pkg-config... (cached) pkg-config
configure: WARNING:
----------------------------------------------------------------------------
* I found a copy of pkgconfig, but there is no cairo-ps.pc file around.
  You may want to set the PKG_CONFIG_PATH variable to point to its
  location.
----------------------------------------------------------------------------
			
configure: WARNING:
----------------------------------------------------------------------------
* I could not find a working copy of cairo-ps. Check config.log for hints on why
  this is the case. Maybe you need to set LDFLAGS and CPPFLAGS appropriately
  so that compiler and the linker can find libcairo and its header files. If
  you have not installed cairo-ps, you can get it either from its original home on

     [http://cairographics.org/releases/](http://cairographics.org/releases/)

  You can find also find an archive copy on

     [http://oss.oetiker.ch/rrdtool/pub/libs](http://oss.oetiker.ch/rrdtool/pub/libs)

  The last tested version of cairo-ps is 1.4.6.

       LIBS=-lm 
   LDFLAGS=
  CPPFLAGS=

----------------------------------------------------------------------------
                
checking for pango_cairo_context_set_font_options in -lpango-1.0... no
checking for pkg-config... (cached) pkg-config
configure: WARNING:
----------------------------------------------------------------------------
* I found a copy of pkgconfig, but there is no pangocairo.pc file around.
  You may want to set the PKG_CONFIG_PATH variable to point to its
  location.
----------------------------------------------------------------------------
			
configure: WARNING:
----------------------------------------------------------------------------
* I could not find a working copy of pangocairo. Check config.log for hints on why
  this is the case. Maybe you need to set LDFLAGS and CPPFLAGS appropriately
  so that compiler and the linker can find libpango-1.0 and its header files. If
  you have not installed pangocairo, you can get it either from its original home on

     [http://ftp.gnome.org/pub/GNOME/sources/pango/1.17](http://ftp.gnome.org/pub/GNOME/sources/pango/1.17)

  You can find also find an archive copy on

     [http://oss.oetiker.ch/rrdtool/pub/libs](http://oss.oetiker.ch/rrdtool/pub/libs)

  The last tested version of pangocairo is 1.17.

       LIBS=-lm 
   LDFLAGS=
  CPPFLAGS=

----------------------------------------------------------------------------
                
checking for xmlParseFile in -lxml2... no
checking for pkg-config... (cached) pkg-config
configure: WARNING:
----------------------------------------------------------------------------
* I found a copy of pkgconfig, but there is no libxml-2.0.pc file around.
  You may want to set the PKG_CONFIG_PATH variable to point to its
  location.
----------------------------------------------------------------------------
			
configure: WARNING:
----------------------------------------------------------------------------
* I could not find a working copy of libxml-2.0. Check config.log for hints on why
  this is the case. Maybe you need to set LDFLAGS and CPPFLAGS appropriately
  so that compiler and the linker can find libxml2 and its header files. If
  you have not installed libxml-2.0, you can get it either from its original home on

     [http://xmlsoft.org/downloads.html](http://xmlsoft.org/downloads.html)

  You can find also find an archive copy on

     [http://oss.oetiker.ch/rrdtool/pub/libs](http://oss.oetiker.ch/rrdtool/pub/libs)

  The last tested version of libxml-2.0 is 2.6.31.

       LIBS=-lm 
   LDFLAGS=
  CPPFLAGS= -I/usr/include/libxml2

----------------------------------------------------------------------------
                
configure: error: Please fix the library issues listed above and try again.
r-c@rclr-srv:~/rrdtool-1.3.6$ 

---

### Post by snova on 2009-03-31
Install these packages:

libcairo2-dev
libpango1.0-dev
libxml2-dev

I am assuming you have a reason to be compiling from source, since it's in the repos.

---

