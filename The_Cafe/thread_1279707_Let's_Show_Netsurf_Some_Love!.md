---
title: "Let's Show Netsurf Some Love!"
date: 2009-10-01
forum: The Cafe
---

### Post by Mark76 on 2009-10-01
For those of you who don't know Netsurf is a fully graphical web browser originally created for the RISC OS platform that has since been ported to *nix, Haiku and AmigaOS.  It's currently at release 2.1 and although it lacks some things users of more well supported browsers take for granted (like bookmarks and plugin support) it is, nevertheless, a fairly stable lightweight browser.

Unlike the popular side Netsurf isn't built on Gecko or Webkit/KHTML but has been created from the ground up, rendering engine and all.

If you want to try Netsurf. And perhaps even contribute to its development you should first download, untar, make and make install the following packages:

[libnsgif]("http://www.netsurf-browser.org/projects/releases/libnsgif-0.0.1-src.tar.gz")

[libnsbmp]("http://www.netsurf-browser.org/projects/releases/libnsbmp-0.0.1-src.tar.gz")

[libharu]("http://libharu.org/files/libharu-2.1.0.tar.gz")

[Hubbub]("http://www.netsurf-browser.org/projects/releases/hubbub-0.0.1-src.tar.gz")

[libparserutils]("http://www.netsurf-browser.org/projects/releases/libparserutils-0.0.1-src.tar.gz")

Once you have these installed download the source code for Netsurf-2.1 (or the nightly build if you're feeling adventurous), untar and edit the makefile.defaults file as shown below (note: ignore anything that isn't gtk or Linux related)

> #
# NetSurf default build configuration
#
# Some of these options support an 'AUTO' option, as well as YES and NO.
# When an option is set to AUTO, the Makefile will attempt to detect if that
# feature is available, enabling it if possible.
#
# Options marked "highly recommended" have a severe impact on NetSurf's
# use as a web browser and should be set to YES unless there is a particularly
# good reason not to.
#
# This file should be treated as INVIOLATE and only altered to alter
# the defaults by a core developer. If you wish to configure the build
# of NetSurf then instead please create a file called Makefile.config
# and simply override the statements you require in that.  Remember
# that Makefile.config cannot override the TARGET. That must be set on
# the commandline. i.e. 'make TARGET=framebuffer' However
# Makefile.config can use the TARGET variable to control what to set
# the configuration options to.
#

# ----------------------------------------------------------------------------
# Options relating to all versions of NetSurf
# ----------------------------------------------------------------------------

# Enable NetSurf's use of libnsbmp for displaying BMPs and ICOs
# Valid options: YES, NO
NETSURF_USE_BMP := YES

# Enable NetSurf's use of libnsgif for displaying GIFs
# Valid options: YES, NO				  (highly recommended)
NETSURF_USE_GIF := YES

# Enable NetSurf's use of libjpeg for displaying JPEGs
# Valid options: YES, NO				  (highly recommended)
NETSURF_USE_JPEG := YES

# Enable NetSurf's use of libpng for displaying PNGs.  If MNG and PNG
# are both enabled then NetSurf will choose libpng for PNGs, leaving
# MNGs and JNGs to libmng.
# Valid options: YES, NO	  (at least one of PNG/MNG highly recommended)
NETSURF_USE_PNG := YES

# Enable NetSurf's use of libmng for displaying MNGs, JNGs and PNGs
# Valid options: YES, NO	  (at least one of PNG/MNG highly recommended)
NETSURF_USE_MNG := YES

# Enable NetSurf's use of libharu for PDF export and GTK printing support.
# There is no auto-detection available for this, as it does not have a
# pkg-config file.
# Valid options: YES, NO
NETSURF_USE_HARU_PDF := YES

# Enable stripping the NetSurf binary
# Valid options: YES, NO
NETSURF_STRIP_BINARY := NO

# Template used for constructing the User Agent: string.  The first two
# replacements are major/minor version, second two are OS and architecture.
# Please don't be tempted to mention Mozilla here!  Let's let that lie die.
NETSURF_UA_FORMAT_STRING := "NetSurf/%d.%d (%s; %s)"

# Default home page, if one is not defined by the user.  Note that this
# option does not apply to the RISC OS version, as it has its own local
# home page, and it can be changed by editing the end of gui_init2() in
# riscos/gui.c
NETSURF_HOMEPAGE := "http://www.netsurf-browser.org/welcome/"

# Force using glibc internal iconv implementation instead of external libiconv
# Valid options: YES, NO
NETSURF_USE_LIBICONV_PLUG := YES

# Initial CFLAGS. Optimisation level etc. tend to be target specific.
CFLAGS := 

# Default installation/execution prefix
PREFIX := /usr/local

# ----------------------------------------------------------------------------
# RISC OS-specific options
# ----------------------------------------------------------------------------
ifeq ($(TARGET),riscos)

  # Enable NetSurf's use of libsvgtiny for displaying SVGs
  # Valid options: YES, NO
  NETSURF_USE_NSSVG := YES

  # Enable NetSurf's use of pencil for Drawfile export
  # Valid options: YES, NO
  NETSURF_USE_DRAW := YES

  # Enable NetSurf's support for displaying RISC OS Sprites
  # Valid options: YES, NO
  NETSURF_USE_SPRITE := YES

  # Enable NetSurf's use of AWRender for displaying ArtWorks files
  # Valid options: YES, NO
  NETSURF_USE_ARTWORKS := YES

  # Enable NetSurf's support for the Acorn plugin protocol
  # Valid options: YES, NO
  NETSURF_USE_PLUGINS := NO

  # Optimisation levels
  CFLAGS += -O2 -Wuninitialized

endif

# ----------------------------------------------------------------------------
# GTK-specific options
# ----------------------------------------------------------------------------
ifeq ($(TARGET),gtk)

  # Where to search for NetSurf's resources after looking in ~/.netsurf and
  # $NETSURFRES.  It must have a trailing /
  NETSURF_GTK_RESOURCES := $(PREFIX)/share/netsurf/

  # Where to install the netsurf binary
  NETSURF_GTK_BIN := $(PREFIX)/bin/

  # Enable NetSurf's use of librsvg in conjunction with Cairo to display SVGs
  # Valid options: YES, NO, AUTO
  NETSURF_USE_RSVG := YES

  # Enable NetSurf's use of librosprite for displaying RISC OS Sprites
  # Valid options: YES, NO, AUTO
  NETSURF_USE_ROSPRITE := AUTO

  # Configuration overrides for Mac OS X
  ifeq ($(HOST),macosx)
    NETSURF_USE_LIBICONV_PLUG := NO
    NETSURF_USE_HARU_PDF := NO
  endif

  # Optimisation levels
  CFLAGS += -O2 -Wuninitialized

endif

# ----------------------------------------------------------------------------
# BeOS-specific options
# ----------------------------------------------------------------------------
ifeq ($(TARGET),beos)


  # Where to install the netsurf binary
  NETSURF_BEOS_BIN := /boot/apps/netsurf/

  # TODO:HAIKU -- not sure if ~/.netsurf applies in beos
  # Where to search for NetSurf's resources after looking in ~/.netsurf and
  # $NETSURFRES.  It must have a trailing /
  NETSURF_BEOS_RESOURCES := /boot/apps/netsurf/res/

  # Enable NetSurf's use of librosprite for displaying RISC OS Sprites
  # Valid options: YES, NO, AUTO
  NETSURF_USE_ROSPRITE := AUTO

  # Enable NetSurf's use of libharu for PDF export.
  # Valid options: YES, NO
  NETSURF_USE_HARU_PDF := NO

  # Force using glibc internal iconv implementation instead of external libiconv
  # Valid options: YES, NO
  NETSURF_USE_LIBICONV_PLUG := NO

  # Optimisation levels
  CFLAGS += -O2 -Wuninitialized

endif

# ----------------------------------------------------------------------------
# Amiga-specific options
# ----------------------------------------------------------------------------
ifeq ($(TARGET),amiga)

  # Enable NetSurf's use of librosprite for displaying RISC OS Sprites
  # Valid options: YES, NO, AUTO
  NETSURF_USE_ROSPRITE := YES

  # Enable NetSurf's use of libsvgtiny for displaying SVGs
  # (NB: Requires NETSURF_AMIGA_USE_CAIRO)
  # Valid options: YES, NO
  NETSURF_USE_NSSVG := NO

  # Enable NetSurf's use of libcairo for some plotter functions
  # This will also link NetSurf with shared objects, and
  # requires AmigaOS 4.1 or higher to run the resulting executable
  # Valid options: YES, NO
  NETSURF_AMIGA_USE_CAIRO := NO

  # Optimisation levels
  CFLAGS += -O2 -Wuninitialized

endif

# ----------------------------------------------------------------------------
# Framebuffer-target-specific options
# ----------------------------------------------------------------------------
ifeq ($(TARGET),framebuffer)
  # Optimisation levels
  CFLAGS += -O2 -Wuninitialized

  # Framebuffer frontend.
  # Valid values are: linux, sdl, vnc, able
  NETSURF_FB_FRONTEND := linux

  # Use libharu to enable PDF export and GTK printing support.
  # Valid options: YES, NO
  NETSURF_USE_HARU_PDF := NO

  # Library to use for font plotting 
  # Valid options: internal, freetype
  NETSURF_FB_FONTLIB := internal

  # Framebuffer frontends may have differing root paths for resources
  # As such, these specify the resource path and config path.
  NETSURF_FB_RESPATH_linux := $(PREFIX)/share/netsurf/
  NETSURF_FB_RESPATH_able := (tftpboot)/
  NETSURF_FB_RESPATH_dummy := ./
  NETSURF_FB_RESPATH_sdl := $(PREFIX)/share/netsurf/
  NETSURF_FB_RESPATH_vnc := $(PREFIX)/share/netsurf/

  NETSURF_FRAMEBUFFER_RESOURCES = $(NETSURF_FB_RESPATH_$(NETSURF_FB_FRONTEND))
  NETSURF_FRAMEBUFFER_BIN := $(PREFIX)/bin/

endif

# Include any local configuration
-include Makefile.config



Then 

make (or make clean if that gives you errors, followed by make)
make install (see BUILDING-GTK file in Docs folder for more details.

At the end of the process, if all has gone well, you should have a browser capable of displaying most web pages more or less corrrectly. As long as they don't have java or flash.

---

### Post by kerry_s on 2009-10-01
i tried netsurf several times, it's just a crappy browser, let it go. :lolflag:

---

### Post by Mark76 on 2009-10-01
Did you have all the libs required?

Granted, it's not perfect. I mean, for one thing it doesn't have a corporate sponsored army of developers working on it day and night. But I'd hardly call it crappy.

Which version did you try, btw?

---

### Post by rjek on 2009-10-01
No, one should change Makefile.config, not Makefile.defaults.  The defaults file, unsurprisingly, just controls the defaults.

Also, just check the source out of svn; the release versions of these libraries are ancient and won't work with the current head anyway.

---

