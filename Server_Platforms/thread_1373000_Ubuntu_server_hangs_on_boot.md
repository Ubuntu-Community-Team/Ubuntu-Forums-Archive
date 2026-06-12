---
title: "Ubuntu server hangs on boot"
date: 2010-01-05
forum: Server Platforms
---

### Post by jeffbarish on 2010-01-05
Ubuntu server hangs when I boot with a wired Ethernet connection.  The last thing I see in the console is:

* Setting up console font and keymap...
* Starting OpenBSD Secure Shell server sshd
* Starting Samba daemons
* Reloading /etc/samba/smb.conf smbd only
* Restarting OpenBSD Secure Shell server sshd

The last 2 lines appear a second time after a few minutes.

I tried removing samba and openssh-server.  Ubuntu still hangs.  The last thing I see then in the console is:

* Setting up console font and keymap...

I can circumvent the problem with the following procedure:

- boot to recovery mode
- select "Drop to root shell prompt with networking"
- hit ^D
- select "Resume normal boot"

I have no problem when I boot to a Wifi connection even when Samba and openssh-server are installed.  I see the same sequence of lines in the console as I reported initially (including Reloading, Restarting), but then the output continues with

* Starting the Winbind daemon winbind

Both the wired and wireless connections use dhcp.  Obviously, I installed the OS using a wired connection, so it worked reliably once.  I'm stuck.

P.S. I tried dhclient -r before rebooting.  The machine did not shut down correctly and when I forced a reboot it appeared to hang at the usual place.  However, after a long delay it proceeded to boot.  Perhaps I am observing a delay due to a very long timeout.  I will try another reboot now and check again in the morning.

Edit: Nah.  It's been printing out "Reloading /etc/samba/smb.conf smbd only" every few minutes, but the boot is still stalled.  I am missing something obvious here.  Thoughts?

Edit: I reinstalled the OS on a second HDD. I upgraded with all the available packages (so that both installations run the same kernel).  I installed openssh and Samba.  Wired Ethernet works in the fresh installation.  I think I have proven that the problem with the original installation has nothing to do with openssh or Samba.  By the way, with the original installation, the OS hangs even when no wire is connected -- even when I comment out the configuration for both the wired and wireless interfaces in /etc/network/interfaces.  And I noticed one odd thing: in the fresh installation of Ubuntu, the wired interface is called "eth0".  In the original installation, it is called "eth1".  Why would the name be different?

I looked in /var/log/messages hoping to get some idea what was happening at the time the boot hangs.  The last message is

type=1505 audit (1252747497.622:9): operation="profile_replace" pid=907 name=/usr/sbin/tcpdump

Any idea what it means?

---

### Post by geordie on 2010-04-01
I have the same problem with my new install of ubuntu 9.10. Clean install didn't do the trick for me. I'm gonna try 8.04. I ran a check on the last install cd it said it was clear. I dunno thought I'd report.

---

### Post by phoenixz on 2011-01-11
As far as I know, type=1505 audit (1252747497.622:9): operation="profile_replace" pid=907 name=/usr/sbin/tcpdump is an SELinux message. Im no expert on SELinux, but google is..

---

