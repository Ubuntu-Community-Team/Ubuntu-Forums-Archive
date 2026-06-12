---
title: "Share &quot;HP 1210&quot; with Samba"
date: 2005-12-28
forum: Server Platforms
---

### Post by Hpatoio on 2005-12-28
Hello everybody, I've an "HP 1210 All-in-one" and I want to share it with Samba, because I need to printYscan from my laptop (Windows XP).

On the server I have and Ubuntu installation without any windows manager.

Can anyone tell me if this is possible and point me a resource where I can find more info.

Thanks

Simone

---

### Post by ingo on 2005-12-28
pure command line samba? have fun! first make sure you install the samba server and then check /usr/share/doc/packages/samba/Samba3-HOWTO.pdf

although I'm getting my info from suse, I'm pretty sure that this is cross distro.

HTH

---

### Post by peanut butter on 2005-12-29
first do this command butinsert your breezycdfirst
apt-get -i ubuntu-desktop
then you will have gnome and its pretty easy after that

---

### Post by narcolept on 2005-12-29
I believe the original poster's goal was to not install a window manager, as this appears to be his home server.  If you have cups/foomatic installed and your printer set up with the server, even though there's no window manager installed, I'm sure that the samba manual or a quick google search will let you know how to share a usb printer, if it's possible.

---

### Post by peanut butter on 2005-12-30
its will probably take twice as long to set it up and if there is an error it is much easier to debug with a wm.

and scaning across a network has never worked for me

---

