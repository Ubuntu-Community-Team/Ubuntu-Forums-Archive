---
title: "Glitch with gnome-terminal"
date: 2015-09-19
forum: Ubuntu Development Version
---

### Post by zika on 2015-09-19
```
:~$ gnome-terminal(process:2585): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Error constructing proxy for org.gnome.Terminal:/org/gnome/Terminal/Factory0: Error calling StartServiceByName for org.gnome.Terminal: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.gnome.Terminal exited with status 8
```Yes, local characterters (OK in other apps) are gone from terminal emulation (gnome-terminal (does not open as described above), xterm and guake (that do open and, aside absence of local characters, work OK)...)...
Update1: While doing upgrade:```
perl: warning: Setting locale failed.perl: warning: Please check that your locale settings:
    LANGUAGE = "en_US",
    LC_ALL = (unset),
    LC_TIME = "sr_RS",
    LC_MONETARY = "sr_RS",
    LC_ADDRESS = "sr_RS",
    LC_TELEPHONE = "sr_RS",
    LC_NAME = "sr_RS",
    LC_MEASUREMENT = "sr_RS",
    LC_IDENTIFICATION = "sr_RS",
    LC_NUMERIC = "sr_RS",
    LC_PAPER = "sr_RS",
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```Update2: It seems that reinstall of locales is enough but (after some trials and errors) I can not promise that that is enough. But I do firmly think it is.

Since there was no traffic in this thread moderators could, if they find it appropriate, remove this thread=message &#8222;of mine&#8220;... ;)

---

### Post by tvboxspy on 2015-09-20
purging the locales fix it for me.

locale-gen --purge

---

### Post by zika on 2015-09-20
> **tvboxspy said:**
> purging the locales fix it for me.
locale-gen --purgeThat hammer was not big enough at my place... ;)

---

### Post by P-I H on 2015-09-20
Have the same problem.

In my case 
reinstall of locales didn't work.
locale-gen --purge didn't work.

For now I'm using LXTerminal

---

### Post by dino99 on 2015-09-20
i suppose you have libc6 2.22 installed : [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1497473](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1497473)

---

### Post by P-I H on 2015-09-20
Yes it's installed. 
I activated proposed some day back to enable installation of Kodi on Wily. USC is also broken on this system.

---

### Post by caribo on 2015-09-20
running locale-gen under my user account had no impact, but  running as root worked for me !

sudo locale-gen --purge

Thanks

---

### Post by tvboxspy on 2015-09-20
My exact log entries under sudo bash.

locale-gen --purge
dpkg-reconfigure locales

gnome-terminal

and reboot

---

### Post by P-I H on 2015-09-20
Thanks,
sudo locale-gen --purge worked

---

### Post by tvboxspy on 2015-09-20
Also the language selector doesn't appear to be fully installed. However, its doesn't prompt you for your password to make the changes.

sudo gnome-language-selector

in terminal to install it properly.

---

### Post by tvboxspy on 2015-09-20
Hmm...interesting the updates that caused this trouble have been pulled.

Went to update a mirror system and the language updates have gone.

---

### Post by Der_Darm on 2016-09-01
I also had this nasty issue

gnome terminal did not work under my user but worked if:
1. open xterm
2. switch to root: sudo -i
3. strat gnome-terminal

So it is user specific issue

Comparing locale output for root and a user I saw no differenses. So it probably was not directly related to locale.

I went the windows way and looked in to the "All Settings" > "Text Entry" and found out that there was no input sourses at all.

Solution:
1. Add English(US)
2. Logaout

---

### Post by cariboo on 2016-09-01
No mention of what version this is. Thread closed.

---

