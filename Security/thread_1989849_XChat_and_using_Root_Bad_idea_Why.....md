---
title: "XChat and using Root? Bad idea? Why...."
date: 2012-05-28
forum: Security
---

### Post by listerdl on 2012-05-28
Hi 2 things - 

I am always set to root (yes yes yes I know...bad idea but I like it that way). Is it an issue to use XChat in my suspended state of ROOT? And why?

And the second thing - this post brings me to 700 beans! \\:D/\\:D/

---

### Post by Cheesemill on 2012-05-28
It is a bad idea to run any program as root.

Whenever there is a vulnerability discovered in an application, then an attacker could take over that application and use it to do things to your computer. If the application is running under a standard user account then it doesn't have access to the entire machine, only your user files so it is restricted in what damage it can do.

If you are running an application as a root user then any software vulnerability could allow an attacker to take complete control over your machine, including changing system files and installing software such as trojans and keyloggers to your machine.

The only programs that should be run as root are programs that have to be run this way for your machine to be able to function properly, running any other application as the root user is an unnecessary security risk.

---

### Post by wilee-nilee on 2012-05-28
Running as a root user in a OS not designed to run in root is a bad idea.

On the IRC you are open for being rooted by another as well this applies on the web.

---

### Post by uRock on 2012-05-28
Moved to Security Discussions.

Why run as root? To me, that is like leaving my car unlocked in the driveway with the keys in it.

---

### Post by Hungry Man on 2012-05-29
Running root offers 0 benefits. You don't get some speed boost, you don't get anything. What you get is an application that can access files it doesn't need. 

Is xchat even updated any more? I didn't think so. Regardless of that it's an internet facing program and therefor it is entirely open to attack.

Let's say a hacker attacks me running Xchat on a default Ubuntu install (ie: not root) they've got access to a ton of stuff. My entire home directory is theirs.

Imagine they've attacked you running Xchat while running it as root. They have access to **everything** and there's a lot less you can do to stop them. They  get my home directory, access to my programs, to my log files, to every single thing on my system. 

tl;dr there's literally no benefit to running as root and only serious security downsides. It's your computer and in the spirit of all things Linux I'll say that you can run it however you like, but understand what you're doing.

---

### Post by Dry Lips on 2012-05-29
If you don't want to type your password in the terminal all the time, you can use:
```
sudo -i 
``` 
And you could also do: ALT-F2 and "gksudo nautilus" if you want to do things to your system folders... But enabling root sounds like a baaaad idea.

---

### Post by Dave_L on 2012-05-29
If you insist on running as root, which as others have pointed out is not a good idea, you could reduce the risks by using sudo to run applications such as xchat as a normal user, for example:

```
sudo -u listerdl xchat
```

---

### Post by jonedney on 2012-05-29
I'm unsure why you would want to run as root anyways.  Root is disabled by default for a reason. :)

---

### Post by dodo3773 on 2012-05-30
> **Hungry Man said:**
>  What you get is an application that can access files it doesn't need. 



I could not have put this better if I tried. This is ultimately the answer to your question. If you think you need to run as root for whatever reason (I have no idea) then you should at least be running your programs as a regular user. 

Since you are probably going to keep running as root just keep this in mind: Just like you can run applications as sudo to run them as root you can also use sudo / su to run an application as a user you create. Basically this would be the oppposite of how the system is set up for you by default but it is a precaution you should take at the very least.

---

### Post by listerdl on 2012-05-30
Update from OP = Im going to un-root

Thanks

---

### Post by Hungry Man on 2012-05-30
That's a good idea.
You can also apparmor xchat. This profile will probably work on your machine. It works fine on mine.

```
# Last Modified: Mon May 14 02:51:29 2012
#include <tunables/global>

/usr/bin/xchat {
  #include <abstractions/apache2-common>
  #include <abstractions/base>

  deny capability chown,
  deny capability dac_override,
  deny capability dac_read_search,
  deny capability fsetid,
  deny capability setgid,
  deny capability setuid,
  deny capability sys_admin,
  deny capability sys_chroot,
  deny capability sys_ptrace,



  /etc/fonts/** r,
  /etc/python2.7/sitecustomize.py r,
  /home/*/.Xauthority r,
  /home/*/.cache/dconf/user rw,
  /home/*/.config/dconf/user r,
  /home/*/.config/enchant/ r,
  /home/*/.config/enchant/en_US.dic rwk,
  /home/*/.config/enchant/en_US.exc rwk,
  /home/*/.local/share/icons/ r,
  /home/*/.local/share/icons/hicolor/**/ r,
  /home/*/.local/share/mime/mime.cache r,
  /home/*/.xchat2/ r,
  owner /home/*/.xchat2/* rw,
  owner /home/*/.xchat2/** rw,
  owner /usr/bin/xchat mr,
  /usr/include/python2.7/* r,
  /usr/lib{,32,64}/** mr,
  /usr/local/lib/python2.7/*/ r,
  /usr/share/enchant/enchant.ordering r,
  /usr/share/fonts/** r,
  /usr/share/glib-2.0/schemas/gschemas.compiled r,
  /usr/share/hunspell/ r,
  /usr/share/hunspell/en_US.aff r,
  /usr/share/hunspell/en_US.dic r,
  /usr/share/icons/ r,
  /usr/share/icons/** r,
  /usr/share/mime/mime.cache r,
  /usr/share/myspell/dicts/ r,
  /usr/share/pixmaps/ r,
  /usr/share/pyshared/* r,
  /usr/share/tcltk/tcl8.5/init.tcl r,
  /usr/share/themes/Ambiance/gtk-2.0/apps/* r,
  /usr/share/themes/Ambiance/gtk-2.0/gtkrc r,
  /usr/share/themes/Default/gtk-2.0-key/gtkrc r,
  /usr/share/themes/Raleigh/gtk-2.0/gtkrc r,
  /var/cache/fontconfig/* r,
  /var/lib/dbus/machine-id r,

}
```
Just drop it in /etc/apparmor.d/usr.bin.xchat

---

