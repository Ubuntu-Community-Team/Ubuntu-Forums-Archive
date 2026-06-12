---
title: "Xubuntu daily 25th March on USB persistent install - very solid"
date: 2012-03-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by keithpeter on 2012-03-25
Hello All

For a change, I thought I would try out the Xubuntu daily, responding to [effenberg0x0's post]("http://ubuntuforums.org/showthread.php?t=1946388") about beta testing.

Hardware: A recycled HP Xeon quad core xw6200 workstation with an Nvidia GeForce GT520 video card.

Downloaded the image, used the startup disc creator to make a bootable USB with persistent storage on a 4Gb usb stick, booted, installed xubuntu-restricted-extras and LibreOffice, and now doing some Impress slides for tomorrows lesson with [Andy Sheppard]("http://www.andysheppard.co.uk/") providing the music via gnumusic.

I'm most impressed with the way Xubuntu live image starts with compositing on by default, presumably using the nouveau drivers. Neither mutter (Gnome-Shell) or Compiz (Unity) will work without the proprietary drivers installed. Window moving is smooth without any tearing at all, and that includes LibreOffice 100+ page documents and Firefox with flash heavy pages.

The only hiccup so far was the need to puggle about with alsamixer to get the sound routed correctly to external amplifier and not the built in tiny speaker.

Does anyone have any bugs/issues they want me to check out?

I may proceed to a hard drive installation later on tonight.

---

### Post by keithpeter on 2012-03-25
Oops, spoke to soon.

Installer had funny colours (black background when I have set a light theme). Halted at 'removing conflicting operating system files'. The details link suggests it was trying to import settings from my PUIAS partition...

```
Mar 25 18:01:30 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdb1
Mar 25 18:01:31 xubuntu migration-assistant: info: setting ostype from: '/dev/sda1:PUIAS Linux  release 6.2 (Pisa):RedHat:linux'
Mar 25 18:01:31 xubuntu migration-assistant: info: got ostype of: 'linux', mountpoint is: '/mnt/migrationassistant'
Mar 25 18:01:31 xubuntu kernel: [  307.126797] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Mar 25 18:01:31 xubuntu ubiquity[4661]: switched to page migrationassistant
Mar 25 18:01:39 xubuntu ubiquity[4661]: debconffilter_done: ubi-migrationassistant (current: ubi-migrationassistant)
Mar 25 18:01:39 xubuntu ubiquity[4661]: Step_before = stepMigrationAssistant
Error opening file for reading: Permission denied

** (ubiquity:4661): CRITICAL **: unable to create '/root/.cache/dconf'; dconf will not work properly.
Mar 25 18:17:01 xubuntu CRON[12841]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

Trying again from a fresh uncustomised USB stick.

---

