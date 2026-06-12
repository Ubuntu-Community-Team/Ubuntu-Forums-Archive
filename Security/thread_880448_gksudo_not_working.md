---
title: "gksudo not working"
date: 2008-08-05
forum: Security
---

### Post by cdmdotnet on 2008-08-05
I've followed the instructions for using the zimbra mail server as a domain controller following ( [http://www.howtoforge.com/zimbra-integration-with-samba-on-ubuntu-p3](http://www.howtoforge.com/zimbra-integration-with-samba-on-ubuntu-p3) ).

The problem I know have is when trying to log into the server the machine asks for the users password twice, which isn't too much of a problem in itself, except gksudo doesn't seem to support asking for a password twice.

It will prompt the user once for a password, then nothing.

any ideas on which specific change i made i can alter so i can use gksudo again, or better still, tell me how to get gksudo working properly.

---

### Post by hyper_ch on 2008-08-05
if you use sudo/gksudo you will granted permission for another 15min to use another sudo/gksudo command before it expires. Each new call will reset the 15min time-out timer to 0 again.

---

### Post by cdmdotnet on 2008-08-05
sudo requires the password twice before it will activate root access.
I was aware that sudo will grant root access for a while ( as you suggest 15 minutes ) however this isn't happening with gksudo because gksudo doesn't ask for the password the second time and therefore fails to action the requested operation.

at the moment i'm resorting to using a terminal window, and sudo, which isn't gksudo. If anyone can shed some light on how to get gksudo working i'd appriciate it.

---

### Post by pedja_portugalac on 2008-08-05
I also had problem using gksudo (to change property of one file), but using 

```
gksu nautilus
```

was OK. You can change "nautilus" with name of any other GUI-ced program. For example:

```
gksu clamtk
```

will start GUI front-end for ClamAV with root privileges. It all depends what you have to do.

**gksu  is a frontend to su and gksudo is a frontend to sudo.  Their primary purpose is to run graphical commands that need  root  without the need to run an X terminal emulator and using su directly. $man gksu   for more information.**

---

### Post by cariboo on 2008-08-06
Never mind

---

### Post by cdmdotnet on 2008-08-06
thanks for that, i'll give su a go when i'm runnign apps.

I've noticed that things like the network utility from the System > admin menu will work as that will ask twice for the password, but things like the update manager seem to use gksudo.

any advise on what i can do to enable the apps that internally call gksudo to work?

---

### Post by cdmdotnet on 2008-08-19
Anyone got any further ideas on this?

---

### Post by Titan8990 on 2008-08-19
I found that gksudo is "iffy" in using the server kernel (which is not meant to have a GUI, thus no use for gksudo) but not with the desktop kernel.

Are you using the server kernel?

---

### Post by cdmdotnet on 2008-08-29
I'm using the "off the cd" normal install of hardy, so i'd imagine the kernel is the standard desktoip kernel.

I took out all the i made to the config files and nothing changed

So i'm getting the idea it is something to do with either the libnss-ldap or libpam-ldap packages

---

