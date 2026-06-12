---
title: "Starting firestarter when GNOME starts"
date: 2007-06-19
forum: Server Platforms
---

### Post by cocotte on 2007-06-19
Hello,

I would like to start /usr/sbin/firestarter when GNOME starts.
I added the following line to /etc/sudoers :

benoit ALL= NOPASSWD: /usr/sbin/firestarter

I got the following error :

benoit@snoopy:~$ sudo firestarter 
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:5523): Gtk-WARNING **: cannot open display:

---

### Post by dreadlord_chris on 2007-06-19
> **cocotte said:**
> Hello,

I would like to start /usr/sbin/firestarter when GNOME starts.
I added the following line to /etc/sudoers :

benoit ALL= NOPASSWD: /usr/sbin/firestarter

I got the following error :

benoit@snoopy:~$ sudo firestarter 
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:5523): Gtk-WARNING **: cannot open display:

Is there a particular reason you want to do this? You're not thinking that you're starting the firewall that way are you? That just starts the admin GUI - your firewall gets started at boot as your network devices get brought up.

---

### Post by dmizer on 2007-06-19
firestarter is running on boot.  just because there's no little firestarter icon in your system tray doesn't mean that firestarter is not running.

if you look at your system processes in something like top, you will see firestarter running.  you can close and open firestarter gui all day long and it will continue to happily work in the background after you've closed it.

the only way to disable it is to select the "stop firewall" option from the interface.

and i'll second dreadlord_chris ... under NO circumstances should you run firestarter without the password as you've attempted to configure it to do.

---

### Post by cocotte on 2007-06-20
Thank you but when my system starts (and my connection is up), I get :

root@snoopy:~# /etc/firestarter/firestarter.sh status
Firestarter is stopped

I think firestarter service isn't started at boot time.

---

### Post by dmizer on 2007-06-20
try this instead:
```
/etc/init.d/firestarter status
```

---

### Post by cocotte on 2007-06-20
I get :

root@snoopy:~# /etc/init.d/firestarter status 
 * Firestarter is stopped

---

### Post by dmizer on 2007-06-20
open firestarter as root.

click:
edit > preferences

in the left menu click on the word "Firewall"
make sure there is a checkmark next to "Start/restart firewall on program startup" and "Start/restart firewall on DHCP lease renewal"

---

### Post by cocotte on 2007-06-21
I had done it but it doesn't work.

---

### Post by spartan777 on 2007-06-24
the reason the original poster is doing this (as am I) is because the firestarter website tells us to do so.

[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

I think they need to make it more clear that those directions are just to get the gui running at boot, the firewall runs at boot anyways.

---

### Post by dreadlord_chris on 2007-06-24
> **spartan777 said:**
> the reason the original poster is doing this (as am I) is because the firestarter website tells us to do so.

[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

I think they need to make it more clear that those directions are just to get the gui running at boot, the firewall runs at boot anyways.
New users, to Linux in general, also need to understand that **booting** your computer up and **logging in** to your computer are two totally seperate processes. Starting a process during **booting** has very different ramifications and many more things taken into consideration - then to starting a process after logging in.

If you will note from the the link you posted:
> 
Q: How can I get Firestarter to load automatically when I log in as a regular user?

these are not instructions for getting firestarter to load at boot - they are instructions for getting the *GUI interface* to automatically start *after* you log in.

A little further down that page it deals with the question of the original poster:
> 
Q: Do I have to start Firestarter after I have rebooted?
Usually, no. When Firestarter is installed from a package, the firewall is running as a service. You can query the status of the service by executing /etc/init.d/firestarter status. The excemption to this is Gentoo users, dial-up users in some cases and persons who have installed from source and not registered the Firestarter sytem service. 

For an in-depth answer, see the section on persistence of the firewall.

You'll note they talk about *booting* not *logging in* here.

---

### Post by spartan777 on 2007-06-24
I've been using Linux for about 3-4 years, and I didn't even think about the difference btw booting and logging in. I guess that should have been obvious.

---

### Post by holycrap on 2007-06-26
> **cocotte said:**
> Hello,

I would like to start /usr/sbin/firestarter when GNOME starts.
I added the following line to /etc/sudoers :

benoit ALL= NOPASSWD: /usr/sbin/firestarter

I got the following error :

benoit@snoopy:~$ sudo firestarter 
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:5523): Gtk-WARNING **: cannot open display:

1. The solution is found [here]("http://www.howtoadvice.com/AutoFirestarter/")

2. While firestarter seems to be configured to start as a service, it doesn't, Not for my box; ubuntu 7.04.  My firestarter is obtained from add/remove program.

I didn't solve that but, I found an alternative, by adding
/etc/firestarter/firestarter.sh start
to /etc/rc.local. rc.local is executed after all services are loaded and b4 login, if i read correctly.  Using (/etc/init.d/firestarter start )  didn't work. I can't explain y. Both scripts function perfectly when executed after logging on.
3. Firestarter **must be running** for firewall policies to function, for my box at least.

hope that helps.

---

### Post by i_dan on 2007-06-26
>benoit@snoopy:~$ sudo firestarter
>Xlib: connection to ":0.0" refused by server
>Xlib: No protocol specified

I also get this error.
It seems to be unrelated to the firestarter-at-boot issue though.
Running "xhost +" makes it work fine so it's an issue with the
firestarter gui bit and X.

Anyone know about this, and/or have any ideas?

Running "xhost +" is probably a very bad idea by the way as it
removes all controls as to who can attach to your xsession.

UPDATE:
Forgot i had tried the firestarter-at-boot thing.
The entry for firestarter was still in "/etc/sudoers" .
Removed it and the above error goes away.

---

