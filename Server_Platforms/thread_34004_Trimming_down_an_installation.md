---
title: "Trimming down an installation"
date: 2005-05-13
forum: Server Platforms
---

### Post by GOwin on 2005-05-13
1) I have ubuntu installed into a system as a desktop (me not knowing anything better then) and now I'd like to convert it into a server. 

2) I'd like it to boot to console by default, and if i would need to run a GUI, i'd like to use XFCE (which I am using now) instead. 

Could someone please advise me the best way to do this?

---

### Post by dacosta123 on 2005-05-13
Don't know about stripping down but what i did was get the **server iso** instead.
Just install and no worries.

Its all about the total amount of time involved ;-)
Get the iso and install it would cost you what? 45m?
Start stripping, breaking & repairing stuff will probably lead to a complete re-install anyway (at least for me it would  ;-) )

Just my 2c

---

### Post by bazh on 2005-05-13
Do a server install by typing in 'server' at the bootprompt.

Install as normal, then when you login to your new ubuntu server system, update the repo's - [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Now type ```
sudo apt-get install x-window-system-core xfce4 synaptic gnome-sudo gdm acpi acpid powermanagement-interface
``` 

you can add extra apps onto this command, or install them later.

Once you've got xfce install, there's a setting somewhere to not start X windows automatically

---

### Post by moopere on 2005-05-13
[QUOTE=GOwin]1) I have ubuntu installed into a system as a desktop (me not knowing anything better then) and now I'd like to convert it into a server. 

2) I'd like it to boot to console by default, and if i would need to run a GUI, i'd like to use XFCE (which I am using now) instead. 

Could someone please advise me the best way to do this?[/QUOTE]
 Best way to strip down ubuntu to something close to what you get during a server install is to use aptitude and remove ubuntu-desktop.

Aptitude should remove all dependencies on ubuntu-desktop for you and leave only the ubuntu-base installation.  Probably better/cleaner to install using the 'server' option, however the method described above will get you a pretty clean system.

Cheers,
Craig

---

### Post by GOwin on 2005-05-13
I forgot to mention that I would like to continue using the services my desktop is providing to the network (egroupware, etc)

a reinstall would delete these (?)

---

