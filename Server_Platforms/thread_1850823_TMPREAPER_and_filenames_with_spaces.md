---
title: "TMPREAPER and filenames with spaces?"
date: 2011-09-27
forum: Server Platforms
---

### Post by hzFVOW00pw on 2011-09-27
Hi, does anyone have a clue on how to make tmpreaper handle filenames with spaces? At he moment I have this in my config:

```


--snip--

for USR in max bob john; do

    if grep -q "/home/$USR\:/bin/bash" /etc/passwd; then

	TMPREAPER_PROTECT_EXTRA="\
/home/$USR/.easytag/easytagrc \
/home/$USR/.easytag/*.mask \
/home/$USR/.geeqie/geeqierc \
/home/$USR/.local/share/applications/* \
/home/$USR/.local/share/desktop-directories/* \
/home/$USR/.local/share/rhythmbox/* \
/home/$USR/.kde/share/apps/color-schemes/* \
/home/$USR/.kde/share/apps/kdenlive/* \
/home/$USR/.kde/share/apps/kwallet/* \
/home/$USR/.mozilla \
/home/$USR/.mozilla-thunderbird \
/home/$USR/.thunderbird \
"

	TMPREAPER_DIRS="\
/home/$USR/.cache/. \
/home/$USR/.cddb/. \
/home/$USR/.config/chromium/Default/Archived History \
/home/$USR/.config/chromium/Default/Bookmarks.bak \
/home/$USR/.config/chromium/Default/History \
/home/$USR/.config/chromium/Default/History Index 2011-08 \
/home/$USR/.config/chromium/Default/History Index 2011-09 \
/home/$USR/.config/chromium/Default/Visited Links \
/home/$USR/.config/chromium/Default/Current Session \
/home/$USR/.config/chromium/Default/Current Tabs \
/home/$USR/.config/chromium/Default/Last Session \
/home/$USR/.config/chromium/Default/Last Tabs \
/home/$USR/.config/chromium/Default/Web Data \
/home/$USR/.config/ghb/EncodeLogs/. \
/home/$USR/.dvdcss/. \
/home/$USR/.easytag/. \
/home/$USR/.fontconfig/. \
/home/$USR/.geeqie/. \
/home/$USR/.gimp-2.6/tmp/. \
/home/$USR/.googleearth/. \
/home/$USR/.java/. \
/home/$USR/.kde/cache-$(hostname)/. \
/home/$USR/.kde/share/applnk/. \
/home/$USR/.kde/share/apps/. \
/home/$USR/.kde/share/config/. \
/home/$USR/.kde/share/locale/. \
/home/$USR/.kde/share/mimelnk/. \
/home/$USR/.kde/share/services/. \
/home/$USR/.kde/share/servicetypes/. \
/home/$USR/.kde/tmp-$(hostname)/. \
/home/$USR/.local/share/. \
/home/$USR/.macromedia/. \
/home/$USR/.mozilla/firefox/profile/OfflineCache/index.sqlite \
/home/$USR/.mozilla/firefox/profile/cookies.sqlite \
/home/$USR/.mozilla/firefox/profile/downloads.sqlite \
/home/$USR/.mozilla/firefox/profile/formhistory.sqlite \
/home/$USR/.openoffice.org/3/user/registry/cache/. \
/home/$USR/.openoffice.org/3/user/temp/. \
/home/$USR/.pulse/. \
/home/$USR/.qt/canonrc \
/home/$USR/.qt/*.lock \
/home/$USR/.thumbnails/. \
/home/$USR/tmp/. \
\
/home/$USR/.bash_history \
/home/$USR/.xsession-* \
\
/media/data1250a/tmp/kdenlive/thumbs/. \
\
/root/.synaptic/log \
/root/.dbus \
/root/.gconf \
/root/.gconfd \
/root/.gnome2 \
/root/.gnome2_private \
/root/.gstreamer-0.10 \
/root/.gvfs \
/root/.kde \
/root/.local \
/root/.nautilus \
/root/.thumbnails \
\
/tmp/. \
\
/var/cache/apt/archives/ \
/var/lib/nagios3/spool/checkresults/. \
/var/lib/tripwire/report/. \
/var/log/*.gz \
/var/log/*.old \
/var/tmp/. \
"

    fi

done

TMPREAPER_ADDITIONALOPTIONS='--showdeleted --test'

```

I need the for loop and the user vars because the script is rsynced to multiple machines by ssh over WAN links.

However when cron runs the script I get errors like these (escaping the spaces with a backslash does not help):

```

error: Cannot chdir() to `/home/ubuntu/.config/chromium/Default/Archived' for --protect glob: No such file or directory
error: Cannot chdir() to `History' for --protect glob: No such file or directory
error: Cannot chdir() to `/home/ubuntu/.config/chromium/Default/Bookmarks.bak' for --protect glob: Not a directory
error: Cannot chdir() to `/home/ubuntu/.config/chromium/Default/History' for --protect glob: Not a directory
error: Cannot chdir() to `/home/ubuntu/.config/chromium/Default/History' for --protect glob: No such file or directory
error: Cannot chdir() to `Index' for --protect glob: No such file or directory
error: Cannot chdir() to `2011-08' for --protect glob: No such file or directory
error: Cannot chdir() to `/home/ubuntu/.config/chromium/Default/History' for --protect glob: No such file or directory
error: Cannot chdir() to `Index' for --protect glob: No such file or directory
error: Cannot chdir() to `2011-09' for --protect glob: No such file or directory
error: Cannot chdir() to `/home/ubuntu/.config/chromium/Default/Visited' for --protect glob: No such file or directory
error: Cannot chdir() to `Links' for --protect glob: No such file or directory
N

```

---

### Post by hawkmage on 2011-09-27
I have not used TMPREAPER before but try putting a "\" before the space to escape it.

---

### Post by hzFVOW00pw on 2011-09-27
> **hawkmage said:**
> I have not used TMPREAPER before but try putting a "\" before the space to escape it.

In my OP: "(escaping the spaces with a backslash does not help)"

Thanx for trying to help anyway...

---

