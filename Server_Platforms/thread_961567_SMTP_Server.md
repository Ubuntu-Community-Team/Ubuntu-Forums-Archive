---
title: "SMTP Server"
date: 2008-10-28
forum: Server Platforms
---

### Post by kyle1984 on 2008-10-28
Hey Guys,

I just took over a tech support position and they run a smtp server on unbuntu, i have no idea how to navigate linux, but im pretty handy with computers. I think we have a stuck email message that is trying to go out, however its slowed all outgoing email to a crawl, so i was wondering if someone could help me with the commands to see whats in the que and or delete the hung message.

Thanks,
Kyle

---

### Post by Titan8990 on 2008-10-28
There are tons of different SMTP server out there and it would be dependant on which you use.

Also, no matter how much you know about computers the move to Linux often means throwing all your previous knowledge in the trash and relearning.

---

### Post by DrMelon on 2008-10-28
Before taking on Tech Support jobs, you should at least equip yourself with rudimentary knowledge of most operating systems.

You should know that most webservers use UNIX or Linux as a base.

---

### Post by kyle1984 on 2008-10-28
Ok, so where would i look to see what smpt is running?

---

### Post by alienprdkt on 2008-10-28
> **DrMelon said:**
> Before taking on Tech Support jobs, you should at least equip yourself with rudimentary knowledge of most operating systems.

You should know that most webservers use UNIX or Linux as a base.

Agreed!!!

(and why can't I seem to get a Tech-Support job?)

---

### Post by Titan8990 on 2008-10-28
That would be a start, yes.

Most likely it will be one of these three:


Exim

Postfix

Sendmail


Exim is the official Debian SMTP server. Postfix is the official for Ubuntu. Sendmail has been around forever and won't die for whatever reason...


Due to it's difficulty setting up and configuring you will want to hope that it is not sendmail.


> Before taking on Tech Support jobs, you should at least equip yourself with rudimentary knowledge of most operating systems.

You should know that most webservers use UNIX or Linux as a base.

This is very true:

[http://survey.netcraft.com/Reports/200809/](http://survey.netcraft.com/Reports/200809/)

---

### Post by Titan8990 on 2008-10-28
Just saw the post asking how to find out. This is an odd case as you would normally know which SMTP server was running because you installed it....


I would search for the servers listed in my post above using ps aux piped through grep:


ps aux | grep exim

ps aux | grep sendmail

ps aux | grep postfix


Here is an example on my system that is running a Exim4 mail server:

```
pjordan@einstein:~$ ps aux | grep exim
113       6214  0.0  0.0  12036  1232 ?        Ss   Oct20   0:00 /usr/sbin/exim4 -bd -q30m
jordan   24777  0.0  0.0   2976   776 pts/0    S+   15:17   0:00 grep exim

```

---

### Post by kyle1984 on 2008-10-28
Like I said in my original plea for help, I just took this position over, I have a degree in system administration and networking, I've got about 8 yrs of production support under my belt, however, coming into this position, I'm the only support person, and I get to pick up the pieces from the last guy. The management has know idea what technology they have behind the scenes. So I was not aware there was a linux box in the server room until after I was hired, this is my 4th day on. So no I didn’t install the server or the smtp server software. I'm guessing the last person in the job was a linux geek and decided to do this, rather then run a windows box or use the ISP's smtp server, and for the past few hours I’ve discovered a lot of equipment depends on this linux box working, and it would take forever to switch everything’s smtp settings to the isp, so any help that is provided will be greatly appreciative and for those who seem to want to only provide sarcasm, THANKS.

---

### Post by Titan8990 on 2008-10-28
Did you not try my last suggestion in the post above?

> I'm guessing the last person in the job was a linux geek and decided to do this, rather then run a windows box


Could this be because Exchange is proprietary and causes a server to take 30min to reboot? Not to mention it's history of security holes.


Edit: personally, I'm a big fan of small paragraphs on forums as it makes everything much easier to read.

---

### Post by kyle1984 on 2008-10-28
Yes i ran the commands, they all return a single line similar to your first line, but nothing about /usr ect...

---

### Post by kyle1984 on 2008-10-28
It appears VMWARE is running on the machine

---

### Post by Titan8990 on 2008-10-28
Alright post the contents of the following and I will have a look for you:


ls /etc/init.d

---

### Post by bodhi.zazen on 2008-10-28
> **Titan8990 said:**
> Also, no matter how much you know about computers the move to Linux often means throwing all your previous knowledge in the trash and relearning.

So true :lolflag:

> **DrMelon said:**
> Before taking on Tech Support jobs, you should at least equip yourself with rudimentary knowledge of most operating systems.

You should know that most webservers use UNIX or Linux as a base.

I know we all have good intentions, but sometimes one can get the wrong impression. All too often I get sustained silence when discussing Linux with Tech support, lets teach them how to use something other then windows :)

---

### Post by kyle1984 on 2008-10-28
acpid                     inetd                            rcS
acpi-support              kdm                              readahead
alsa-utils                keymap.sh                        readahead-desktop
anacron                   klogd                            README
apmd                      laptop-mode                      reboot
atd                       linux-restricted-modules-common  rmnologin
bluez-utils               loopback                         rsync
bootclean.sh              lvm                              screen
bootlogd                  makedev                          sendsigs
bootmisc.sh               mdadm                            single
brltty                    mdadm-raid                       skeleton
checkfs.sh                module-init-tools                ssh
checkroot.sh              mountall.sh                      stop-bootlogd
console-screen.sh         mountdevsubfs                    stop-readahead
cron                      mountvirtfs                      sysklogd
cupsys                    mtab                             udev
dbus                      networking                       umountfs
displayconfig-hwprobe.py  nvidia-kernel                    umountnfs.sh
dns-clean                 pcmcia                           umountroot
evms                      pcmciautils                      urandom
glibc.sh                  powernowd                        usplash
halt                      powernowd.early                  vbesave
hdparm                    ppp                              vmware
hostname.sh               pppd-dns                         waitnfs.sh
hotkey-setup              procps.sh                        x11-common
hplip                     rc                               xinetd
hwclock.sh                rc.local

---

### Post by alienprdkt on 2008-10-28
you said that there was VMware on this machine, Try running the same command from inside the Virtual Machine. I don't see a mail server app listed here.

---

### Post by kyle1984 on 2008-10-28
I'm logged in as root@vmhost:~#

Does that mean im in the ap?

---

### Post by alienprdkt on 2008-10-28
It depends how the guy set you up, it could mean either the virtual machine itself, or the machine hosting the virtual machine... really hard to tell just from the name.

Hopfully more people will comment on this, and help shed some light on this for you.

---

### Post by alienprdkt on 2008-10-28
just never ran a vm without a gui, sure someone in here has.

---

### Post by kyle1984 on 2008-10-28
Ok this is wierd, I've discovered that, the machine is running ubuntu, vmware is running on the machine, I logged into the vmware server console, and found another copy of unbuntu running within that, and POSTFIX is running

---

### Post by alienprdkt on 2008-10-28
atleast we found that you have postfix for your smtp

---

### Post by alienprdkt on 2008-10-28
found some links for you

[http://www.howtoforge.com/forums/archive/index.php/t-1919.html](http://www.howtoforge.com/forums/archive/index.php/t-1919.html)

[http://beginlinux.com/server_training/mail-server/1071-postfix-manual](http://beginlinux.com/server_training/mail-server/1071-postfix-manual)

[http://www.postfix.org/docs.html](http://www.postfix.org/docs.html)

---

### Post by Titan8990 on 2008-10-28
Looks like everyone picked up where I left off. 


Good luck to the OP.

---

### Post by kyle1984 on 2008-10-28
Thanks everyone, I think im on the right track.

---

