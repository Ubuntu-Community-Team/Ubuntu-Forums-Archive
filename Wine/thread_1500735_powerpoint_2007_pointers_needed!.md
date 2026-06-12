---
title: "powerpoint 2007 pointers needed!"
date: 2010-06-03
forum: Wine
---

### Post by dan1973 on 2010-06-03
Hello all,

Have installed office 2007 under wine 1.1.42 (ubuntu lucid) Have word and excel working fine. Powerpoint will not start-up.

Have read in the wine wiki that i need to do the following: 

> riched20: Set riched20 to 'native' in winecfg. DO NOT INSTALL IT YOURSELF. Office 2007 comes with its own version of riched20. Without using it, Powerpoint will not launch, and some dialog boxes will not display properly. Do not set this override globally unless Office is installed in a separate wineprefix. 

I found a winecfg in /usr/bin and it looks like this - no mention of 'riched20' - could someone offer some help please.
```

#!/bin/sh
#
# Wrapper script to start a Winelib application once it is installed
#
# Copyright (C) 2002 Alexandre Julliard
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA 02110-1301, USA
#

# determine the app Winelib library name
appname=`basename "$0" .exe`.exe

# first try explicit WINELOADER
if [ -x "$WINELOADER" ]; then exec "$WINELOADER" "$appname" "$@"; fi

# then default bin directory
if [ -x "/usr/bin/wine" ]; then exec "/usr/bin/wine" "$appname" "$@"; fi

# now try the directory containing $0
appdir=""
case "$0" in
  */*)
    # $0 contains a path, use it
    appdir=`dirname "$0"`
    ;;
  *)
    # no directory in $0, search in PATH
    saved_ifs=$IFS
    IFS=:
    for d in $PATH
    do
      IFS=$saved_ifs
      if [ -x "$d/$0" ]; then appdir="$d"; break; fi
    done
    ;;
esac
if [ -x "$appdir/wine" ]; then exec "$appdir/wine" "$appname" "$@"; fi

# finally look in PATH
exec wine "$appname" "$@"
```

Many thanks,

---

### Post by cogadh on 2010-06-03
Run winecfg (either type "winecfg" in the terminal or go to Application > Wine > Configure Wine), go to the Libraries tab and add a native override for riched20.

---

### Post by dan1973 on 2010-06-03
Sorted, many thanks - starting up no probs.:guitar:

---

