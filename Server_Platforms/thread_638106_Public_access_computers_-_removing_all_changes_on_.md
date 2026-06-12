---
title: "Public access computers - removing all changes on reboot"
date: 2007-12-11
forum: Server Platforms
---

### Post by stickmangumby on 2007-12-11
I'm setting up some public access computers with Ubuntu, and I'm trying to lock them down as much as possible. I've got most things sorted out in my head, but one thing that I'm wondering about is the following... when I was in school, all the computers (Windows 2000) had software installed that nuked any changes you made when you restarted. Any files in temp directories, any programs you managed to install (good old Windows user accounts :P), and any settings you changed and so on were gone.

Does anyone know of any software to do this? Is it necessary at all under Linux?

---

### Post by Whiffle on 2007-12-11
You could  make a script to delete everything in the home directory, and then replace it with a home directory you create, either on login or reboot.

---

### Post by HermanAB on 2007-12-11
The easiest solution is to install Ubuntu with VMware, then install your kiosk system on a VM.  Back up this VM to a tar ball.  Whenever you end a client session, shut down the VM and untar the tarball again, then restart the VM.

---

### Post by Whiffle on 2007-12-11
> **HermanAB said:**
> The easiest solution is to install Ubuntu with VMware, then install your kiosk system on a VM.  Back up this VM to a tar ball.  Whenever you end a client session, shut down the VM and untar the tarball again, then restart the VM.

I think that would be alot of unnecessary work for the computer, untaring and retarring a several gigabyte file every time someone logs on is bound to be tedious.  Its especially unnecessary since presumably whatever user is logged in won't have rights to install anything, so the only things they can change is in their home directory.

---

### Post by rsw686 on 2007-12-12
Your school probably used [Deep Freeze]("http://www.faronics.com/html/deepfreeze.asp"), which restores the system at every reboot. The college I attend uses this on all their WinXP workstations as well. It really does come in handy. There is a [linux version]("http://www.faronics.com/html/DFLinux.asp") available, but I don't know the details on it.

---

### Post by HermanAB on 2007-12-13
Untarring a VM is quick.  A kiosk VM is tiny.  If it isn't, then you are doing something wrong.  If you want it to be really quick and you are too lazy to cut Ubuntu down to size, use Puppy Linux.

Cheers,

Herman

---

### Post by gaten on 2007-12-13
While the VM idea sounds good, it does seem like alot of work. Why not combine the two ideas already presented? 

Make a tarball of a "default" /home folder, and just replace whatever is in /home on boot with your "default" /home folder?

---

### Post by Richie2010 on 2007-12-13
> **gaten said:**
> While the VM idea sounds good, it does seem like alot of work. Why not combine the two ideas already presented? 

Make a tarball of a "default" /home folder, and just replace whatever is in /home on boot with your "default" /home folder?



I am also a newbie - How do i do this. What are the step and the commands i issue and where to put them.  I too would like the added security that when the computer is rebooted that everything is exactly as it was.  The only issue would be that the tar ball could become large. Right now my public work stations are xp and near 40 gigs. So i will be converting all my workstations to Linux. 

Thanks for the help :-)

---

### Post by gaten on 2007-12-13
Well, the VM is a better idea for security, but it might be overkill. 

As far as what I was talking about, simply make a tar archive of the /home folder. Or you could just make it of your user;'s folder. 

Note, you will want to create another user OTHER than the one created during installation; that user has too many priviliges. 

This is done via:
```
tar -cvvf home.tar /home
```


Then throw that in some protected directory, like /usr/var or something. Then you'll need to create a boot script in /etc/init.d. Put something like this in it:

```
#!/bin/bash
tar -C .home -xf home.tar 

```

Then make it executable (chmod +x), then reboot and see what happens. 

NOTE: You should try this on a fake directory first (ie: one without data in it), I probably forgot something and I haven;t tested it.

Let me know how it turns out.

Also, you could just keep the machine running and make it cron job to be executed every night.

---

### Post by Blown306 on 2007-12-13
I run VMWare, create a snapshot of the deployed state, lock the snapshot and set the "power off" options to "revert to snapshot".  This will always start the virtual machine in the state of the orignal snapshot (deployment state).

This is how I run our training room computers...

---

### Post by gaten on 2007-12-14
> I run VMWare, create a snapshot of the deployed state, lock the snapshot and set the "power off" options to "revert to snapshot". This will always start the virtual machine in the state of the orignal snapshot (deployment state).

This is how I run our training room computers...

Now THAT is a much better idea. Ignore me, this guy (gal?) has the right idea. And the best part is, as the whole thing is in a VM, even if they do manage to own the box, you couldn't care less.

---

### Post by Richie2010 on 2007-12-14
Thank you all for the replies.  If using a VM - what would be the lowest memory needed to run a computer that runs games like Warcraft Dota. If VM and Dota are running at one time - memory might be the biggest issue.... My desktops only have 256k memory.

---

### Post by Richie2010 on 2007-12-14
> **gaten said:**
> Well, the VM is a better idea for security, but it might be overkill. 

As far as what I was talking about, simply make a tar archive of the /home folder. Or you could just make it of your user;'s folder. 

Note, you will want to create another user OTHER than the one created during installation; that user has too many priviliges. 

This is done via:
```
tar -cvvf home.tar /home
```


Then throw that in some protected directory, like /usr/var or something. Then you'll need to create a boot script in /etc/init.d. Put something like this in it:

```
#!/bin/bash
tar -C .home -xf home.tar 

```

Then make it executable (chmod +x), then reboot and see what happens. 

NOTE: You should try this on a fake directory first (ie: one without data in it), I probably forgot something and I haven;t tested it.

Let me know how it turns out.

Also, you could just keep the machine running and make it cron job to be executed every night.


I forgot to thank you for this information.   These machines will be for a internet cafe where kids try to install and change anything and everything they can. So that is why i need to make sure that one the computer reboots as fast as possible and two that it is exactly the same image each time the system is rebooted.  I am so new at linux that i dont know yet how to set up a user and have that be the account that will boot up. BUT i am trying to find the information. Deep Freeze on windoz is good because my friend has me test his system that runs DF and i deleted folders and did all kinds of things and we rebooted and sure enough it rebooted very fast and it was returned to normal. But DF for Linux is only avail for one other distro but not Ubuntu yet.  If you know of any pdf guides - the real meat and potatoes of installing, system security, user set ups etc. Please let us know.

---

