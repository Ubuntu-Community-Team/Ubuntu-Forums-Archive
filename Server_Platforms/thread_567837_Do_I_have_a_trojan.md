---
title: "Do I have a trojan??"
date: 2007-10-05
forum: Server Platforms
---

### Post by Unterseeboot_234 on 2007-10-05
If I got infected, it was from a .torrent download, probably PDF with a hidden script.

Symptoms:
1. Usually at around 1pm on my machine, if I have left it sleeping for an hour, I will notice the keyboard lights above the numeric pad flashing. then Linux will shut down on its own.

2. If I go into menu: System => Administration => System Log => user.log I can see something tried to make up a DHCD. I think malicious code is trying to make a back door seeking host_name, domain_name, nis_domain_name, nis_server. Or, there will be a signal request for bluetooth.

I don't have bluetooth. I don't have redhat, but I get the following types of messages in user.log.

```
Oct  5 06:45:47 user-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
```

The 1pm timing reminds me of the CHRON trojan I found about from references online.

3. I did find forum advice from a member to aptitude the following downloads:

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install chkrootkit rkhunter
sudo chkrootkit -d
sudo rkhunter -c
```

After that runs, I get a warning:

```
* Filesystem checks
   Checking /dev for suspicious files...                      [ OK ]
   Scanning for hidden files...                               [ Warning! ]
---------------
/etc/.pwd.lock /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools 
---------------
Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory) 

[Press <ENTER> to continue]

```

Can I start deleting those folders? Or would I be better off to reinstall??

Thanks, forum.

---

### Post by netlogic on 2007-10-05
Very interesting situation. I never seen a linux trojan yet.
This is an interesting situation. Maybe, others can help. I will look into it later.

---

### Post by kvonb on 2007-10-05
It sounds more like you have auto-sleep enabled or something, maybe have a look in BIOS.

You could look in /etc/cron.daily to see what is scheduled.

Try running from the LiveCD, see if it does it then.

---

### Post by MJN on 2007-10-05
Sounds like a bug...
 
[https://bugs.launchpad.net/ubuntu/+source/dhcdbd/+bug/93360](https://bugs.launchpad.net/ubuntu/+source/dhcdbd/+bug/93360)
 
Mathew

---

### Post by Unterseeboot_234 on 2007-10-05
Thanks, Mathew. The link to the LaunchPad bug report looks right on, exactly same messages like I'm getting.

Forgive me, but I was overly paranoid. The old buffer-overflow trick using C, from my NT 3.51 experiences, was we would cause the numeric keypad keyboard lights to flash. Then, we knew we had a buffer to write to.

One day, I'll read up some more on the Linux lit sitting on my bookshelf. I've got my head stuck up things Python at the moment.

---

### Post by MJN on 2007-10-05
> **Unterseeboot_234 said:**
> I've got my head stuck up things Python at the moment.
 
Ooh, sounds painful! ;)
 
Mathew

---

### Post by netlogic on 2007-10-05
wash, rinse, and conditioning his head should be fine.
you can post your ingredients for the shampoo. maybe, we can help you reconfigure it.

---

### Post by lepus on 2007-12-16
Have a look at [http://ubuntuforums.org/archive/index.php/t-222785.html](http://ubuntuforums.org/archive/index.php/t-222785.html) for info on the rkhunter messages.

---

