---
title: "Paste your linux hardcore command here!"
date: 2012-02-27
forum: The Cafe
---

### Post by sostentado on 2012-02-27
let me start..not really hard but could be core.. :guitar:

proxychains wget -r -l 0 -k -m -p -H -N -c -t1 -L -4 -x -P . -E -erobots=off --user-agent="" --follow-ftp -A.exe A.zip -A.rar -A.tar.gz -A.tar -A.gz -A.tar.bz2 -A.bz2 -A.iso -A.bz -A.vmx -A.vmdk -A.db -A.sqlite -A.accdb -A.sql -A.xls -A.xlsx -A.doc -A.docx -A.ppt -A.zipx -A.bin -A.py -A.pl -A.pyc -A.pdf -A.c -A.cpp -A.h -A.pst -A.php -A.asp -A.aspx -A.js -A.css -A.avi -A.mpg -A.mov -A.flv -A.wmv -A.webm -A.mp4 -A.dmg  -A.xml --quota=10000M [http://www.nasa.gov/](http://www.nasa.gov/)

---

### Post by eriktheblu on 2012-02-27
I'm sure there are faster ways to fill your hard drive.

---

### Post by |{urse on 2012-02-27
Nice pipe. Is that a meerschaum?

---

### Post by BHEJU on 2012-02-27
kill -9 -1

:)

---

### Post by nikonian on 2012-02-27
Best command I ever learned...

```
sudo apt-get remove ubuntu
```


Way to get your life back.

---

### Post by MG&amp;TL on 2012-02-27
> **BHEJU said:**
> kill -9 -1

:)

o.0

Just read the manpage. 

```
cat /dev/urandom | aplay -
```

Stolen from [http://techfreaks4u.com/blog/posts/geekist-things-i-ever-did-in-linux/](http://techfreaks4u.com/blog/posts/geekist-things-i-ever-did-in-linux/), but I had the idea on my own. :)

---

### Post by nikonian on 2012-02-27
> **MG&TL said:**
> o.0

Just read the manpage. 

```
cat /dev/urandom | aplay -
```Stolen from [http://techfreaks4u.com/blog/posts/geekist-things-i-ever-did-in-linux/](http://techfreaks4u.com/blog/posts/geekist-things-i-ever-did-in-linux/), but I had the idea on my own. :)

Ahh, back to the old analogue TV days! ^_^

Hisssssssssssssssssssssss


Grub for the blind...

```

sudo dd if=/dev/sda bs=512 | aplay -

```

---

### Post by |{urse on 2012-02-27
Here's a safe to paste but fun one. 

> xmessage -center "hello, `whoami`" -buttons "Hey There":0]

---

### Post by nikonian on 2012-02-27
> **|{urse said:**
> Here's a safe to paste but fun one.

That's assuming it's installed :P

---

### Post by |{urse on 2012-02-27
it is, well at least last I checked it's installed by default
:)

---

### Post by nikonian on 2012-02-27
> **|{urse said:**
> it is smartypants
:)

Yes, on *your* setup. The title is "Paste your linux hardcore command here!"

Not

"Paste your *personal* setup of linux hardcore command here!"

or

"Paste your *Ubuntu* linux hardcore command here!"

Therein lies the difference... smartypants fail! ^_^

---

### Post by |{urse on 2012-02-27
sudo apt-get install cowsay fortune && xmessage -center  "Hello, `whoami` `fortune | cowsay` " -buttons "Hey There":0]

Interactive fortune-telling cow lol

---

### Post by |{urse on 2012-02-27
You can append x11-utils which provides xmessage to the above command but I assure you most everyone's linux distro already has it installed.

---

### Post by |{urse on 2012-02-27
> **yeshuaiseverything said:**
> Yes, on *your* setup. The title is "Paste your linux hardcore command here!"

Not

"Paste your *personal* setup of linux hardcore command here!"

or

"Paste your *Ubuntu* linux hardcore command here!"

Therein lies the difference... smartypants fail! ^_^

yeah because 

```
sudo apt-get remove ubuntu
```

is totally compatible with all linux distros, mmhmm.

Here's your ball, go home now. :D

---

### Post by sostentado on 2012-03-01
> **eriktheblu said:**
> I'm sure there are faster ways to fill your hard drive.

yeah, pretty sure...

---

### Post by jerrrys on 2012-03-01
sudo apt-get xxx

---

### Post by cgroza on 2012-03-01
```

emacs -nw

```

---

### Post by BeRoot ReBoot on 2012-03-02
Open emacs
Press a random combination of modifier keys
Spell out your name

:popcorn:

---

### Post by stmiller on 2012-03-03
```
yes
```

:P

---

### Post by emperorpsf on 2012-04-02
get-porn ;)

---

### Post by santosh83 on 2012-04-02
> **sostentado said:**
> let me start..not really hard but could be core.. :guitar:

proxychains wget -r -l 0 -k -m -p -H -N -c -t1 -L -4 -x -P . -E -erobots=off --user-agent="" --follow-ftp -A.exe A.zip -A.rar -A.tar.gz -A.tar -A.gz -A.tar.bz2 -A.bz2 -A.iso -A.bz -A.vmx -A.vmdk -A.db -A.sqlite -A.accdb -A.sql -A.xls -A.xlsx -A.doc -A.docx -A.ppt -A.zipx -A.bin -A.py -A.pl -A.pyc -A.pdf -A.c -A.cpp -A.h -A.pst -A.php -A.asp -A.aspx -A.js -A.css -A.avi -A.mpg -A.mov -A.flv -A.wmv -A.webm -A.mp4 -A.dmg  -A.xml --quota=10000M [http://www.nasa.gov/](http://www.nasa.gov/)
Do NOT attempt to run it unless you want to cold-reset your system! :-)
[https://en.wikipedia.org/wiki/Fork_bomb](https://en.wikipedia.org/wiki/Fork_bomb)

---

### Post by nothingspecial on 2012-04-02
Can we leave the stuff that breaks systems out of this thread please.

:popcorn:

---

### Post by Lucradia on 2012-04-02
After installing mini.iso of Debian, I open up the following text document in a command line text editor:

```
## Remember to use alsamixer then, after quitting it with desired settings, use alsactl store.
## In pcmanfm, make sure it's the desktop manager.
## .config/openbox/autostart.sh
## ## Add pcmanfm -d
## ## Add conky
## /etc/apt/sources.list
## ## Add deb http://www.debian-multimedia.org testing main non-free
## ## Add contrib to all the debian repos.
## After installing flash, replace it with 11.1, as it's much faster.
apt-get install openbox obmenu menu obconf openbox-themes gtk-themes-murrine gtk-chtheme alsa-utils iceweasel xorg pcmanfm gnome-icon-theme stalonetray conky flashplugin-nonfree xsane gimp pidgin pidgin-libnotify gstreamer0.10-x gstreamer0.10-ffmpeg ffmpeg faad faac totem freepats x264 libdvdcss2 sakura htop scrot unclutter xdg-utils usbmount --no-install-recommends
```

and follow its instructions (or have it printed out, or on my smartphone.) After installing, and logging in via the command line (as I did NOT install a DM) I use startx. Ah, good 'ol startx, the ultimate security for people who steal computers. It's too bad though xmessage no longer executes this properly:

```
#!/bin/bash

xmessage "Are you sure you want to log out?" -center -title "Log Out" -font "Sans bold 10" -default "Cancel" -buttons "_Cancel":1,"_Log out":2,"_Reboot":3,"_Shut down":4 >/dev/null

case $? in
   1)
      echo "Exit";;
   2)
      openbox --exit;;
   3)
      sudo shutdown -r now;;
   4)
      sudo shutdown -h now;;
esac
```

(If xmessage has to bring up sudo, when the above was made, it will auto-open a terminal window. Now, it won't, so you have to do it manually.)

> **nothingspecial said:**
> Can we leave the stuff that breaks systems out of this thread please.

:popcorn:

Seeing as the OP did it...

---

### Post by Bandit on 2012-04-02
Used for extracting multiple TAR files in the same directory from the CLI.. 
```
find . -name "*.tar" -exec tar -xvf \{\} \;
```

---

### Post by mtron on 2012-04-02
remove old Linux images & headers (keeps latest kernel image untouched)

```
sudo apt-get remove $(dpkg -l|awk '/^ii  linux-image-/{print $2}'|sed 's/linux-image-//'|awk -v v=`uname -r` 'v>$0'|sed 's/-generic//'|awk '{printf("linux-headers-%s\nlinux-headers-%s-generic\nlinux-image-%s-generic\n",$0,$0,$0)}')
```

---

### Post by philinux on 2012-04-02
> **mtron said:**
> remove old Linux images & headers (keeps latest kernel image untouched)

```
sudo apt-get remove $(dpkg -l|awk '/^ii  linux-image-/{print $2}'|sed 's/linux-image-//'|awk -v v=`uname -r` 'v>$0'|sed 's/-generic//'|awk '{printf("linux-headers-%s\nlinux-headers-%s-generic\nlinux-image-%s-generic\n",$0,$0,$0)}')
```

I'd do a dry run first.
```

dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get --dry-run remove
```

Also credits where they are due. ;)
[Remove Old Kernels]("http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/#Remove%20Old%20Kernels")

---

### Post by nothingspecial on 2012-04-02
Surely this is the definitive linux "hardcore" command

```
mplayer -really-quiet http://65.60.32.242:8600 < /dev/null &
```

---

### Post by mtron on 2012-04-02
> **philinux said:**
> 
Also credits where they are due. ;)
[Remove Old Kernels]("http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/#Remove%20Old%20Kernels")

First you don't need a dry run cause apt-get will ask for confirmation before actually doing anyrthing and second the link you posted is a totally different command... Ok, the outcome might be similar but that's it.

The source for the command i posted is[ commandlinefu]("http://www.commandlinefu.com/commands/view/10520/remove-all-unused-kernels-with-apt-get"), and i altered it a bit to work with linux kernels 3.x

Since nobody else posted a source link (we're not on wikipedia here anyway) i wonder why you're (wrongly) bashing me for it ?!?

---

### Post by CharlesA on 2012-04-02
> **philinux said:**
> I'd do a dry run first.
```

dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get --dry-run remove
```

Also credits where they are due. ;)
[Remove Old Kernels]("http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/#Remove%20Old%20Kernels")

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1 | xargs apt-get purge --dry-run
```

Hmm, mine doesn't have awk in it and uses sed instead. Oh it keeps the previous kernel too. ;)

It's based off the one found here:
[http://ubuntuforums.org/showthread.php?t=1658648](http://ubuntuforums.org/showthread.php?t=1658648)

EDIT: If you are going to be piping things to xargs, you'll need to add --assume-yes otherwise apt-get aborts, which is why it's a good idea to do a dry-run first.

Another way you can do it is like this (thanks for the idea mtron!):

```
sudo apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1)
```

---

### Post by Elfy on 2012-04-02
> **nothingspecial said:**
> Can we leave the stuff that breaks systems out of this thread please.

:popcorn:

In fact - [http://ubuntuforums.org/announcement.php?a=54](http://ubuntuforums.org/announcement.php?a=54)
> 
I'd just like to caution those thinking of doing this that UbuntuForums has a strict zero-tolerance policy when it comes to posting dangerous commands. If you post one of them, particularly in a support thread disguised as advice, expect to be instantly and permanently BANNED, at the account, e-mail, IP, or ISP level. I do not care about intent -- if you mean it as a joke, it is not funny. If you mean it as a lesson, go teach it somewhere else. This behavior is absolutely against the Forum Guidelines and Ubuntu Code of Conduct.

---

