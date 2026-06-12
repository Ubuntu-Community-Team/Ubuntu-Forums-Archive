---
title: "Accidentally messed up AppArmor for Chromium"
date: 2012-12-03
forum: Security
---

### Post by Stonecold1995 on 2012-12-03
I've been playing around with AppArmor trying to get the hang of it, and I think I stupidly messed up the profile for Chromium.  I ran aa-update-browser and somehow messed up the Chromium profile.  I use to have a perfectly functioning profile, but now many things seem to be denied, preventing the browser from doing things like opening dialog boxes ([screenshot](http://www.pictureshack.us/images/18494_kdialog.png)).
```
Dec  2 23:28:16 kubuntu kernel: [203560.159464] type=1400 audit(1354519696.566:23029): apparmor="DENIED" operation="open" parent=25414 profile="/usr/lib/chromium-browser/chromium-browser" name="/home/alex/.directory" pid=25637 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Dec  2 23:28:43 kubuntu kernel: [203586.558757] type=1400 audit(1354519723.002:23043): apparmor="DENIED" operation="file_lock" parent=25650 profile="/usr/lib/chromium-browser/chromium-browser" name="/home/alex/.config/Trolltech.conf" pid=25651 comm="kdialog" requested_mask="k" denied_mask="k" fsuid=1000 ouid=1000
Dec  2 23:28:43 kubuntu kernel: [203586.568476] type=1400 audit(1354519723.014:23044): apparmor="DENIED" operation="file_lock" parent=25650 profile="/usr/lib/chromium-browser/chromium-browser" name="/home/alex/.config/Trolltech.conf" pid=25651 comm="kdialog" requested_mask="k" denied_mask="k" fsuid=1000 ouid=1000
Dec  2 23:28:43 kubuntu kernel: [203586.572799] type=1400 audit(1354519723.018:23045): apparmor="DENIED" operation="file_mmap" parent=25650 profile="/usr/lib/chromium-browser/chromium-browser" name="/usr/lib/kde4/plugins/styles/oxygen.so" pid=25651 comm="kdialog" requested_mask="m" denied_mask="m" fsuid=1000 ouid=0
Dec  2 23:28:43 kubuntu kernel: [203586.608745] type=1400 audit(1354519723.054:23046): apparmor="DENIED" operation="file_lock" parent=25650 profile="/usr/lib/chromium-browser/chromium-browser" name="/home/alex/.config/Trolltech.conf" pid=25651 comm="kdialog" requested_mask="k" denied_mask="k" fsuid=1000 ouid=1000
Dec  2 23:28:43 kubuntu kernel: [203586.657393] type=1400 audit(1354519723.102:23048): apparmor="DENIED" operation="file_lock" parent=25650 profile="/usr/lib/chromium-browser/chromium-browser" name="/home/alex/.config/Trolltech.conf" pid=25651 comm="kdialog" requested_mask="k" denied_mask="k" fsuid=1000 ouid=1000
Dec  2 23:28:43 kubuntu kernel: [203586.662723] type=1400 audit(1354519723.106:23049): apparmor="DENIED" operation="open" parent=25650 profile="/usr/lib/chromium-browser/chromium-browser" name="/home/alex/.kde/share/apps/kfileplaces/bookmarks.xml" pid=25651 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Dec  2 23:28:43 kubuntu kernel: [203586.663578] type=1400 audit(1354519723.110:23050): apparmor="DENIED" operation="mknod" parent=25650 profile="/usr/lib/chromium-browser/chromium-browser" name="/home/alex/.kde/share/apps/kfileplaces/bookmarks.xml.tbcached25651.new" pid=25651 comm="kdialog" requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
Dec  2 23:28:43 kubuntu kernel: [203586.663668] type=1400 audit(1354519723.110:23051): apparmor="DENIED" operation="mknod" parent=25650 profile="/usr/lib/chromium-browser/chromium-browser" name="/home/alex/.kde/share/apps/kfileplaces/bookmarks.xmlj25651.new" pid=25651 comm="kdialog" requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
Dec  2 23:28:48 kubuntu kernel: [203591.882087] type=1400 audit(1354519728.334:23052): apparmor="DENIED" operation="open" parent=25650 profile="/usr/lib/chromium-browser/chromium-browser" name="/home/alex/.local/share/user-places.xbel" pid=25651 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Dec  2 23:28:48 kubuntu kernel: [203591.912752] type=1400 audit(1354519728.366:23053): apparmor="DENIED" operation="open" parent=25650 profile="/usr/lib/chromium-browser/chromium-browser" name="/home/alex/.directory" pid=25651 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Dec  2 23:28:48 kubuntu kernel: [203591.913655] type=1400 audit(1354519728.366:23054): apparmor="DENIED" operation="open" parent=25650 profile="/usr/lib/chromium-browser/chromium-browser" name="/home/alex/.directory" pid=25651 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Dec  2 23:28:48 kubuntu kernel: [203592.283168] type=1400 audit(1354519728.738:23055): apparmor="DENIED" operation="open" parent=25650 profile="/usr/lib/chromium-browser/chromium-browser" name=2F686F6D652F616C65782F416E6F6E796D6F757320746F6F6C732F2E6469726563746F7279 pid=25651 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Dec  2 23:28:48 kubuntu kernel: [203592.293595] type=1400 audit(1354519728.746:23056): apparmor="DENIED" operation="open" parent=25650 profile="/usr/lib/chromium-browser/chromium-browser" name="/home/alex/Documents/.directory" pid=25651 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Dec  2 23:28:48 kubuntu kernel: [203592.294985] type=1400 audit(1354519728.750:23057): apparmor="DENIED" operation="open" parent=25650 profile="/usr/lib/chromium-browser/chromium-browser" name=2F686F6D652F616C65782F466C6173682070726F6772616D732F2E6469726563746F7279 pid=25651 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Dec  2 23:28:48 kubuntu kernel: [203592.301682] type=1400 audit(1354519728.754:23058): apparmor="DENIED" operation="open" parent=25650 profile="/usr/lib/chromium-browser/chromium-browser" name="/home/alex/Music/.directory" pid=25651 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Dec  2 23:28:48 kubuntu kernel: [203592.302588] type=1400 audit(1354519728.758:23059): apparmor="DENIED" operation="open" parent=25650 profile="/usr/lib/chromium-browser/chromium-browser" name=2F686F6D652F616C65782F4E445320686F6D65627265772F2E6469726563746F7279 pid=25651 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Dec  2 23:28:48 kubuntu kernel: [203592.303210] type=1400 audit(1354519728.758:23060): apparmor="DENIED" operation="open" parent=25650 profile="/usr/lib/chromium-browser/chromium-browser" name=2F686F6D652F616C65782F4F7065726174696E672073797374656D732F2E6469726563746F7279 pid=25651 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Dec  2 23:28:48 kubuntu kernel: [203592.303967] type=1400 audit(1354519728.758:23061): apparmor="DENIED" operation="open" parent=25650 profile="/usr/lib/chromium-browser/chromium-browser" name="/home/alex/Pictures/.directory" pid=25651 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
```

I tried to set it to "complain" mode, but I get this:
```
root@kubuntu:/etc/apparmor.d# aa-complain usr.bin.chromium-browser
Setting /etc/apparmor.d/usr.bin.chromium-browser to complain mode.
Warning from stdin (line 1): /sbin/apparmor_parser: cannot use or update cache, disable, or force-complain via stdin
Multiple definitions for hat sanitized_helper in profile (null) exist,bailing out.
```

So I think I messed up something with the "Abstractions" by using aa-update-browser.  How do I reset that without loosing my custom profile?

---

### Post by vasa1 on 2012-12-03
> **Stonecold1995 said:**
> I've been playing around with AppArmor trying to get the hang of it, and I think I stupidly messed up the profile for Chromium.  I ran aa-update-browser ...
So I think I messed up something with the "Abstractions" by using aa-update-browser.  How do I reset that without loosing my custom profile?
Where did you find "aa-update-browser"? I haven't come across that before.

---

### Post by Stonecold1995 on 2012-12-03
```
AA-UPDATE-BROWSER(8)                                                               AppArmor                                                               AA-UPDATE-BROWSER(8)

NAME
       aa-update-browser - update browser profiles with browser abstractions

SYNOPSIS
       aa-update-browser [option] <profile>

DESCRIPTION
       aa-update-browser will list current browser abstractions in /etc/apparmor.d/abstractions/ubuntu-browsers.d as well as update browser profiles to use those
       abstractions.

OPTIONS
       aa-update-browser accepts the following arguments:

       -d  dry-run. Only show what would be done.

       -u ABSTRACTIONS
           update the specified profile with the comma-separated list of ABSTRACTIONS. Specifying '' will remove all ABSTRACTIONS.

       -l  show supported browser abstractions

       -h  show help

BUGS
       aa-update-browser will always add the plugins-common abstraction if the list of abstractions ABSTRACTIONS is not empty.

       If you find any additional bugs, please report them to Launchpad at <https://bugs.launchpad.net/ubuntu/apparmor/+filebug>.

SEE ALSO
       apparmor(7)

Canonical Ltd                                                                     2010-08-11                                                              AA-UPDATE-BROWSER(8)
 Manual page aa-update-browser(8) line 1/37 (END) (press h for help or q to quit)

```

---

### Post by vasa1 on 2012-12-03
Thanks!
Difficult to say why that should have messed up things. Could it be because you're using Chromium 2**4**? Can you repair things by restoring a backup?

---

### Post by Stonecold1995 on 2012-12-03
It has nothing to do with Chromium itself, the problem is with AppArmor.

On a related note, I have a backup from a little while ago but I created it by running dd to create an image of my encrypted hard drive.  But for some reason I can't seem to mount the encrypted image file with cryptsetup.  If I can do that I may be able to check if I have a recent enough backup.

---

### Post by Hungry Man on 2012-12-03
Have you tried setting the profile to complain, removing any deny rules, and seeing what it logs?

---

### Post by Stonecold1995 on 2012-12-03
> **Hungry Man said:**
> Have you tried setting the profile to complain, removing any deny rules, and seeing what it logs?
Read the OP again.  I said what happens when I tried doing that.  And from what I can tell, the problem is that I may have disabled some "Abstractions", and that's preventing Chromium from doing many things.  I just want to be able to reset Chromium's Abstractions or whatever it is.

---

### Post by Stonecold1995 on 2012-12-03
Meh.  I gave up and re-installed it, it's working now but without my custom profile.

---

