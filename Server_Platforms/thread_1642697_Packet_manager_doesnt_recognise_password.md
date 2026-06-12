---
title: "Packet manager doesnt recognise password"
date: 2010-12-10
forum: Server Platforms
---

### Post by Wader_WS on 2010-12-10
Hi there,

just setup ubuntu server 10.10 on my new home server, installing usual stuff ect and came to install TCL, however had a couple of errors and done a bit of digging, come across a thread here that told me i needed to enable the 'repositories' packets in my packet manager, then went to open the packet manager and its doesn't recognize my password, although i can use sudo just fine.

can anyone shine some light?

sorry if its a bit vague or stupid, im a bit of a linux newbie :p

Thanks in advance

~Wader

---

### Post by garryconn on 2010-12-10
Hey Wader,

I'm pretty new to Linux/Ubuntu as well. I'm really not sure how useful I can be with helping you. But based on what you've explained, it sounds like you're trying to install the software without sudo. I don't think you can ever do that. You always have to use sudo for anything administrative.

For example, you can't apt-get install ... you have to sudo apt-get install. It doesn't have anything to do with entering in the right or wrong password. It's just that your username doesn't have the proper privileges to execute administrative things.

---

### Post by Wader_WS on 2010-12-10
> **garryconn said:**
> Hey Wader,

I'm pretty new to Linux/Ubuntu as well. I'm really not sure how useful I can be with helping you. But based on what you've explained, it sounds like you're trying to install the software without sudo. I don't think you can ever do that. You always have to use sudo for anything administrative.

For example, you can't apt-get install ... you have to sudo apt-get install. It doesn't have anything to do with entering in the right or wrong password. It's just that your username doesn't have the proper privileges to execute administrative things.

hey garryconn, 

i understand how to use sudo and that it enables a user to use super admin commands/privileges.

however when i open my packet manager im asked for a password (i have GUI installed), now in normal ubuntu its the same as your user password, however in my case this isnt working. I just keep getting password incorrect displayed. Which is causing me some problems

i was hoping of a way to find/reset this info

~Wader

---

### Post by garryconn on 2010-12-10
>  i was hoping of a way to find/reset this info


Just curious, were you in there playing around with the settings prior?

---

### Post by Wader_WS on 2010-12-10
> **garryconn said:**
> Just curious, were you in there playing around with the settings prior?

nope not had any access to it. Was the first time i needed to access it. I have used the same password for everything. 

~Wader

---

### Post by garryconn on 2010-12-10
I wish I could help you further. But don't worry I'm sure someone will chime in soon. ;)

---

### Post by ingeva on 2010-12-11
> **garryconn said:**
> I wish I could help you further. But don't worry I'm sure someone will chime in soon. ;)

I suggest that you try this:

From the main menu, choose System, Administration, then Users and Groups.
Change your password there.
If it works then, fine. If not I suggest you install your system again.
After install, log in and give these command before you proceed:

sudo aptitude -y dist-upgrade
sudo dpkg --configure -a

If you don't have scripts to do the other installs, I suggest you gradually build such a script (or a set of them) so you can install again fast if you ever have to re-install.
Instead of upgrading to a newer version, I always re-install instead.
It may take more time, but it tends to clean up things.
Tip: Keep you files away from the home directory. That's a dangerous place. :)

---

### Post by Wader_WS on 2010-12-11
> **ingeva said:**
> I suggest that you try this:

From the main menu, choose System, Administration, then Users and Groups.
Change your password there.
If it works then, fine. If not I suggest you install your system again.
After install, log in and give these command before you proceed:

sudo aptitude -y dist-upgrade
sudo dpkg --configure -a

If you don't have scripts to do the other installs, I suggest you gradually build such a script (or a set of them) so you can install again fast if you ever have to re-install.
Instead of upgrading to a newer version, I always re-install instead.
It may take more time, but it tends to clean up things.
Tip: Keep you files away from the home directory. That's a dangerous place. :)

I tried changing my password to no avail, then proceeded for a fresh install (didnt matter to much as it was a fresh install in itself anyway), then put in the 2 commands as above, then proceeded to install the gnome GUI and still the same problem :(

---

### Post by amsterdamharu on 2010-12-11
Is there any output if you try the following command from a commandline?
```
gksu /usr/sbin/synaptic
```

If you right click on the desktop and create a new launcher with the following command does it work?
```
gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
```

---

### Post by Wader_WS on 2010-12-11
> **amsterdamharu said:**
> Is there any output if you try the following command from a commandline?
```
gksu /usr/sbin/synaptic
```If you right click on the desktop and create a new launcher with the following command does it work?
```
gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
```

yes they both open the Synaptic packet manager, although they both still recognize the password as incorrect.

---

### Post by Wader_WS on 2010-12-11
suddenly had a brain wave when accessing my VPS. 

i used *sudo su* to swap to the root user. From there i used *passwd* and changed the password to my own preference.

Ubuntu server 10.10 x64

sorry for troubles caused.

~Wader

---

