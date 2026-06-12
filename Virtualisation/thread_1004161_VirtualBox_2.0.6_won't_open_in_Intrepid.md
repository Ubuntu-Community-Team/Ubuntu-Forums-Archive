---
title: "VirtualBox 2.0.6 won't open in Intrepid"
date: 2008-12-06
forum: Virtualisation
---

### Post by piine on 2008-12-06
Hello all. I am have a problem with virtualbox. When I click on the icon, run the shell command, or the original executable, it does absolutely nothing, except for when I click the Icon, it flashes like it's about to open, but does nothing from that point. It never shows uo in the system monitor and it doesn't log anything. Please HELP!!!!!.

I have tried unistalling and reinstalling, both the restricted and open source. Also, I am using Intrepid and VirtualBox 2.0.6, upgraded from Hardy. 

P.S. When I install, the is no error and the vboxdrv starts. The only error that I get thru the entire process is that " The group `vboxusers' already exists". Nothing more, nothing less. Again,  Please HELP!!!!!.

---

### Post by jayson.rowe on 2008-12-07
Make sure that you have added yourself to the "vboxusers" group. The installer creates the group, but doesn't add anyone too it by default (yeah, I know that's stupid, but that's how it does it).

To do this, (assuming you are using Ubuntu w/ GNOME), click on System -> Administration -> Users and Groups. Now, click the "Unlock" button, and enter your sudo password. After that, click on the button "Manage Groups", and select "vboxusers" from the list (it should be the last one) and click on the "Properties" button, and put a tick in the box next to your name. You will have to at least log out, and back in (but shouldn't need to reboot).

Please post back and let me know if this solved your issue - if not, we can try some other troubleshooting steps.

Cheers!
Jayson

---

### Post by piine on 2008-12-07
Already check that. It was working yesterday and all of my setting are the same. 
I did try reinstalling again and this time it deleted the ICON and when I run it in the shell, I get this error... [FONT=monospace]"[/FONT]Qt WARNING: VirtualBox: cannot connect to X server".

I just tried installing QT3, but I am not sure which files to install. { I am trying QT3 before I ran across 4 or 5 forums saying that VBox uses QT3 !QT4 }

---

### Post by bodhi.zazen on 2008-12-07
Run Virtualbox and tell us what error messages you get.

Cannot connect to X server sounds like a permissions problem. Were you doing something as root ?

If so, consider using ```
sudo -i
``` or gksu to obtain root access (shell or gui application)

I suggest you :

```
sudo ls -la $HOME | grep root
```Change the ownership of any file (? .Xauthority) back to your user.

```
sudo chown -R user.user /home/user
```Where "user" == you log in name.

---

### Post by piine on 2008-12-07
I will try that, however, I've tried to run as root and still the same thing, both "sudo VirtualBox" & also "sudo su -l"   ->    "VirtualBox", I will change the permissions, however, I don't think that's the case.

---

### Post by jjmatt on 2008-12-15
Has anyone found a solution to this yet? I'm having the same problem, but after running ```
sudo ls -la | grep root 
``` the only things listed are the parent directory and .dbus so i changed the owner and group of dbus to mine, but still get the same error.

virtualbox worked fine until I got a "floating point exception" (no clue) a few days ago, so I reinstalled it, and now I'm getting the Qt thing...

---

### Post by jjmatt on 2008-12-15
Hey, so, I just restarted (a second time) and now its back to giving me the same ```
$ VirtualBox 
Floating point exception

```

Anyone know how I can fix this?

Danke Schön

---

### Post by piine on 2008-12-16
I am really, really going insane. I really don't want to reinstall ubuntu. Now I am getting this
```

$ /usr/bin/VirtualBox
mkdir: cannot create directory `/home/administrator/.VirtualBox': File exists
Floating point exception

```
I don't know why!!! It is attempting to make a directory??? Why is that??? Could it be malicious??? 

Someone, please help. I've had to resort to using my laptop for all my windows stuff and it is a pain. I really don't have the time or patience to reload ubuntu at this time, this computer is critical to my business and I will be set back to far to do anything drastic.

---

### Post by piine on 2008-12-16
Just something I've found...
I tried...
```

# dpkg-reconfigure virtualbox

```
and got this...
```

/usr/sbin/dpkg-reconfigure: virtualbox is broken or not fully installed


```

---

### Post by piine on 2008-12-16
I have found an "alternative", vboxgtk
```

# sudo apt-get install vboxgtk

```
bout to play with it. It does not have some features, like mounting ISO's.

---

