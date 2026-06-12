---
title: "Ubuntu Server dist-upgrade 12.04 --&gt;14.04 : boot problems[SOLVED]"
date: 2016-02-03
forum: Server Platforms
---

### Post by coolnicklas on 2016-02-03
Hi,

Some weeks ago I did a dist-upgrade of my Ubuntu 12.04 server to 14.04. Yesterday I rebooted the server and went to bed and today i noticed the server was down.

So tried to boot it and the following happens:

1. After Grub the following message appear: grub disk filter writes are not supported (I googled this, and it should not cause the symptoms following this)
2. Ubuntu boots to a blank screen. There is a cursor in the left corner. I can type characters - but they have no effect.
3. I can ping the server for a short time from another machine, before Ubuntu automatically shutdowns the server.
4. One time I did see the login prompt a few seconds and then I did see something like tty0 sending term signal stopping...

If I boot in failsafe mode. Everything seems normal (Except that it is in fail safe mode).

I did boot the system with the repair-disk and extracted a lot of info which can be seen here:
[URL="http://paste.ubuntu.com/14872422/"]http://paste.ubuntu.com/14872422/

[/URL]EDIT: A combination of things caused this behavior:

1. Removing "quiet" and adding "nomodeset" to the boot command in Grub gave me the boot output in the console (Add [FONT=courier new]*"nomodeset"*[/FONT] and remove [FONT=courier new]*"quiet" *[/FONT]to the line* [FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT=[/FONT] *in the file[I] [FONT=courier new]/etc/default/grub[/FONT])

[/I]2. I forgot I had a NUT client configured to monitor the NUT server on my Synology NAS. The Synology NAS had lost connection to the UPS and NUT on my server was configured to shutdown after 5 seconds. Lessons learned - Add a more verbose output in NUT configuration when it calls the shutdown command.

---

