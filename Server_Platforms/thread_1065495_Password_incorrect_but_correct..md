---
title: "Password incorrect? but correct."
date: 2009-02-09
forum: Server Platforms
---

### Post by 13ojo on 2009-02-09
Hi,

I'm having troubles with ubuntu 8.10.
I installed it on a new nice whitebox i built. With the aim of it doing some NAS, CUPS, and web interface work. Just a nice fileserver that has some fancy webuis i wrote,  and also a network printer.

However, after a while all logins fail. I can't figure out what is doing this.

Via SSH if i login with the correct username and password, i am disconnected immediately. However if i use an incorrect password, i get the 5 tries until it fails. So the system still has a recording of my password.

I also tried recovery mode, but i can't run passwd, i get a segmentation fault.

What's going on?. This happened once and i blamed myself, so i re-installed. It's now happened again, when it wasn't even being used. (either i noticed or caused the problem by changing the papersize in cups).

---

### Post by hyper_ch on 2009-02-10
can you post the output whne you try to run recovery mode and reset the password?

---

### Post by 13ojo on 2009-02-10
> root@machine:~# passwd user
Segmentation fault
root@machine:~#

Apparently this is caused by PAM looping around or something.

It's bloody annoying, and i have no idea how to fix.

---

### Post by hyper_ch on 2009-02-10
is the user called "user" of whom you want to change password?

---

### Post by 13ojo on 2009-02-10
no i just didn't feel like giving out my username or the machine's name.

I tried updating the packages via recovery 

> apt-get upgrade

but the problem persists.

Also in recovery if i type "login", it then asks me for login details, and gives a segmentation fault again.

From what i gather from the internet, it seems PAMs bailing out even though its getting the right password, so it's putting me back to the login. Segfaults are probably from the bailing out of it too.

---

### Post by hyper_ch on 2009-02-10
hmm, I have no clue what's going on there but it is not good :(

---

### Post by 13ojo on 2009-02-11
This fixes it.... ish

Has to be done in recovery mode.

> dpkg --purge libpam-smbpass
mv /var/lib/samba/secrets.tdb /var/lib/samba/secrets.tdb.old
apt-get install libpam-smbpass

Of course, something like changing the default paper size in cups (because cups ignores document sizes its been sent, and makes them all default anyway). Will make the problem come straight back.

I have the run apt-get update. So i should have latest versions or so.

Someone dropped the ball big time here. I don't know how to fix it properly, but changing paper size should not bork the whole system.

---

