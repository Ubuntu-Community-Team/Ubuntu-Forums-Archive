---
title: "Sudo with new gazelle on 11.04"
date: 2011-04-28
forum: System76 Support
---

### Post by Kacey on 2011-04-28
I am trying to run a sudo command in 11.04 and I get the following error.


```

username@username-Gazelle-Professional:~$ sudo ls
[sudo] password for username: **
GLib-GIO:ERROR:/build/buildd/glib2.0-2.28.6/./gio/gdbusconnection.c:2279:initable_init: assertion failed: (connection->initialization_error == NULL)

```

Is this coming from the fingerprint scanner?

---

### Post by Kacey on 2011-04-28
Has anyone else seen this? It really is making things very hard not being able to sudo.

Also I should add that I am getting the error even when I run gksudo.

---

### Post by domolicious on 2011-04-29
Hi,

I had the same problem after upgrading to 11.04 on my Thinkpad. I entered recovery mode and purged fingerprint-gui and now sudo is working. Is it related to Unity? Because the fingerprint-gui was working fine in recovery mode. 

Thanks for the tip.

---

### Post by justfortherec on 2011-04-29
I upgraded to 11.04 yesterday and experienced the same problem. Uninstalling fingerprint-gui (and dependencies like libfprint0) solved that issue. (Of course) The fingerprint-scanner doesn't work anymore though.

---

### Post by Yan.Sereda on 2011-04-29
I have Thinkpad SL510 with fingerprint sensor
And new installed UBUNTU 11.04

I switch to text console (CTRL + ALT + F1)
login to my account (with fingerprint :-) )
make sudo - its absolutley work.
(CTRL + ALT + F7 - return to Gnome Desktop)

in gnome-terminal its not work. 
its output from console:
> 
droid@SL510:~$ sudo su
Password: **
GLib-GIO:ERROR:/build/buildd/glib2.0-2.28.6/./gio/gdbusconnection.c:2279:initable_init: assertion failed: (connection->initialization_error == NULL)



may be its help any other man :-)

sorry for my bad Eng.
And Welcome to Ukraine in 2012
:popcorn::guitar:):P

---

### Post by MnCC on 2011-04-29
On error, just press "enter" and type password to login.

ThinkPad L412

---

### Post by Bufke on 2011-04-29
I have this too on my gazelle, I don't think it's necessary to uninstall fingerprint-gui. It still works for me in many but not all places. As mentioned you can just type in the password and ignore this error. Plus if you keep it installed you'll get the update once it's fixed.

---

### Post by jugs on 2011-04-30
Note to self: This is why you don't update too soon...

I love the fingerprint support.

---

### Post by clarkyzl on 2011-05-01
I have the same problem, I am not for sure whom should this bug be submitted to.

---

### Post by b8e5n on 2011-05-09
> **MnCC said:**
> On error, just press "enter" and type password to login.

ThinkPad L412

Don't even need to press return! Just type your password as usual!
VAIO VPCS11

---

### Post by gperezbrun on 2011-09-24
Hi, I have the same issue. Figerprint scanner work fine but loose the sudo password. if I don't write any password y pass to sudo enviroment.
What can i do to fix it????


user@ThinkPad-T410i:~$ sudo -s
Password: **
GLib-GIO:ERROR:/build/buildd/glib2.0-2.28.6/./gio/gdbusconnection.c:2279:initable_init: assertion failed: (connection->initialization_error == NULL)

[sudo] password for gonzalo: 
root@gonzalo-ThinkPad-T61:~# exit
exit
user@ThinkPad-T410i:~$

---

### Post by isantop on 2011-09-26
It looks like you have a ThinkPad. I'm not very familiar with the ThinkPad hardware, but have you installed the correct driver for the fingerprint reader? The instructions available on System76 sites is very specific to our fingerprint readers, and is only applicable to other systems if they have the same fingerprint reader manufacturer (Which is not necessarily tied to a particular brand of laptop).

---

