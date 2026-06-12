---
title: "Shoud it stay or should it go?"
date: 2012-12-10
forum: Ubuntu Development Version
---

### Post by zika on 2012-12-10
```
The following packages will be REMOVED:
  im-switch
The following NEW packages will be installed:
  dialog im-config

``````
Setting up im-config (0.19) ...
ERROR: Unknown hook file exists: /etc/X11/Xsession.d/80im-switch
``````
:~$ cat 80im-switch 
#!/bin/sh
# Copyright (C) 2005 Kenshi Muto <kmuto@debian.org> 
#  Modified for Debian package.
# Copyright (C) 1999 - 2004 Red Hat, Inc. All rights reserved. This
# copyrighted material is made available to anyone wishing to use, modify,
# copy, or redistribute it subject to the terms and conditions of the
# GNU General Public License version 2.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
#
# X Input method setup script

# Keep original values related to IM
_XIM=$XIM
_XIM_PROGRAM=$XIM_PROGRAM
_XIM_ARGS=$XIM_ARGS
_XMODIFIERS=$XMODIFIERS
_GTK_IM_MODULE=$GTK_IM_MODULE
_QT_IM_MODULE=$QT_IM_MODULE

# $LNG is locale <language>_<region> without .<encoding> and .<encoding>@EURO
LNG=${LC_ALL:-${LC_CTYPE:-${LANG}}}
LNG=${LNG%@*}
LNG=${LNG%.*}

[ -z "$LNG" ] && LNG="all_ALL" || true

echo "Setting IM through im-switch for locale=$LNG."

# Source first found configuration under $LNG locale
for f in    "$HOME/.xinput.d/${LNG}" \
        "$HOME/.xinput.d/all_ALL" \
        "/etc/X11/xinit/xinput.d/${LNG}" \
        "/etc/X11/xinit/xinput.d/all_ALL" \
        "/etc/X11/xinit/xinput.d/default" ; do
    if [ -f "$f" -a -r "$f" ]; then
    echo "Start IM through $f linked to $(readlink -f $f)."
    . "$f"
    break
    fi
done

unset LNG

# Revibe IM related environment if other values were set.
[ "$_XIM" ] && XIM=$_XIM || true
[ "$_XIM_PROGRAM" ] && XIM_PROGRAM=$_XIM_PROGRAM || true
[ "$_XIM_ARGS" ] && XIM_ARGS=$_XIM_ARGS || true
[ "$_XMODIFIERS" ] && XMODIFIERS=$_XMODIFIERS ||true
[ "$_GTK_IM_MODULE" ] && GTK_IM_MODULE=$_GTK_IM_MODULE || true
[ "$_QT_IM_MODULE" ] && QT_IM_MODULE=$_QT_IM_MODULE || true


[ -n "$GTK_IM_MODULE" ] && export GTK_IM_MODULE || true
[ -n "$QT_IM_MODULE" ] && export QT_IM_MODULE || true

# setup XMODIFIERS
[ -z "$XMODIFIERS" -a -n "$XIM" ] && XMODIFIERS="@im=$XIM" || true
[ -n "$XMODIFIERS" ] && export XMODIFIERS || true

# execute XIM_PROGRAM
if [ -n "$XIM_PROGRAM" -a -x "$XIM_PROGRAM" ]; then
     if [ -z "$XIM_PROGRAM_SETS_ITSELF_AS_DAEMON" ]; then
        {
            sleep 10
            eval "$XIM_PROGRAM $XIM_ARGS &" || true
        } &
    else
        {
            sleep 10
            eval "$XIM_PROGRAM $XIM_ARGS" || true
        } &
    fi
fi
# execute XIM_PROGRAM_XTRA
[ -n "$XIM_PROGRAM_XTRA" ] && eval "$XIM_PROGRAM_XTRA &" || true
```

This install is made from QQ via upgrade to RR so not much artefacts and atavisms present...

---

### Post by serdotlinecho on 2012-12-10
Here's what i've found about im-config:

[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2012-January/013221.html]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2012-January/013221.html")
[http://changelogs.ubuntu.com/changelogs/pool/main/i/im-config/im-config_0.19/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/i/im-config/im-config_0.19/changelog)

---

### Post by zika on 2012-12-10
For now that file is safely stored out of any path... Just the time will tell if it is needed or really surplus... I do beleive in latter...

---

### Post by dino99 on 2012-12-10
you need to purge im-switch as it "conflicts" with the now used im-config.

---

### Post by zika on 2012-12-10
> **dino99 said:**
> you need to purge im-switch as it "conflicts" with the now used im-config.Dist upgrade( as shown above) was performed... So, im-config should use purge instead of remove, that is all I can conclude... I'll try cleaning just as I finish this post... But I think that the only remnant that was present is this file that is (as written above) taken to a safe place to wait resolution. No ill-effects noticed in the meantime...
Update&#8321;: Yes, it should have been purged, it went OK, even though it was removed already by apt-get... Lesson learned... Thank You...
Update&#8322;: Reinstall of im-config went well also, just in case...
Update&#8323;: We are now persuaded to use ibus? Still not found since upgrade a nice and polite way to turn it off...

---

