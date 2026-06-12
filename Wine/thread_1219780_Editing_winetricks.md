---
title: "Editing winetricks"
date: 2009-07-22
forum: Wine
---

### Post by acdragon101 on 2009-07-22
Hi,

  I just want to ask is it possible to edit wineprefix default installation of wine because I've change the location of wine folder and its wineprefix using wineboot. Actually I'm trying to run wine without installing it on any ubuntu so that I can use it without any root access.It was successful but the problem is that most application won't run because it needed some files that is in the wineprefix but the problem is that it wont run unless the wine is natively installed but mine is not native so that's a problem.

Could you please help me how to edit this lines that are in winetricks 

my WINEPREFIX=$HOME/Desktop/open
my location of WINE is WINEPREFIX=$/HOME/Desktop/weny/usr/bin/wine

I've actually tried editting it with this lines but I've got a lot of errors so this is my last resort

This are the code from the winetrickss

# Name of this version of winetricks (YYYYMMDD)
VERSION=20090716

# Default values for important settings if not already in environment.
# These settings should not need editing here.
WINE=${WINE:-wine}
WINEPREFIX=${WINEPREFIX:-$HOME/.wine}

# Internal variables; these locations are not too important
WINETRICKS_CACHE=$HOME/winetrickscache
# Default to hiding the directory, by popular demand
test -d "$WINETRICKS_CACHE" || WINETRICKS_CACHE=$HOME/.winetrickscache
WINETRICKS_TMP="$WINEPREFIX"/drive_c/winetrickstmp
mkdir -p "$WINETRICKS_TMP"
WINETRICKS_TMP_WIN='c:\winetrickstmp'

WINDIR="$WINEPREFIX/drive_c/windows"

# Which sourceforge mirror to use.  Rotate based on time, since 
# their mirror picker sometimes persistantly sends you to a broken
# mirror.
case `date +%S` in
*[01]) SOURCEFORGE=http://internap.dl.sourceforge.net/sourceforge ;;
*[23]) SOURCEFORGE=http://easynews.dl.sourceforge.net/sourceforge ;;
*)     SOURCEFORGE=http://downloads.sourceforge.net;;
esac

case "$1" in
-V|--version) 
  echo "Winetricks version $VERSION.  (C) 2007-2009 Dan Kegel et al.  LGPL."
  exit 0
  ;;
esac

die() {
  echo "$@"

  case x"$GUI" in
  x1) xmessage -center "               Winetricks error: $@                 " ;;
  *) ;;
  esac

  exit 1
}

if [ ! -x "`which "$WINE"`" ]
then
  die "Cannot find wine ($WINE)"
fi



Thanks in advance !!!

---

