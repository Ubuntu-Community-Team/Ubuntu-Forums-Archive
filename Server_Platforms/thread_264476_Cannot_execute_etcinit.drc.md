---
title: "Cannot execute /etc/init.d/rc"
date: 2006-09-24
forum: Server Platforms
---

### Post by coastdweller on 2006-09-24
Recently I've converted all of my machines at the house to Ubuntu/Kubuntu and after having a great couple weeks with Ubuntu server running a local web site I seem to have killed my server.

It was up for 6 days and then all of a sudden I couldnt create new SSH sessions. Simply said "Connection closed".

I had two other sessions going and thought well, I am just logged in too many times.

Later I closed those two sessions and attempted to start another session in a bit of time after that. Same thing, connection closed.

Now I'm thinking its a service issue and I need to just restart the server.

After restarting it wont boot, says:

> Uncompressing Linux... Ok, booting the kernel.
*INIT cannot execute "/etc/init.d/rcS"
*INIT Entering runlevel: 2
*INIT cannot execute "/etc/init.d/rc"

Ubuntu 6.06.1 LTS (none) tty1

(none) login:

So I've done something damaging to it, surely.

It is a LAMP server running webmin, awstats, webalizer, and postfix.

If someone reads this and can help me rescue this puppy it would be greatly appreciated.

My commitment to Ubuntu is to get through these problems, having succesfully fixed a couple desktops I broke :p 

So I turn to the forums for help.

How do I "fix" this, get this to boot to where it was, running a very fast web site (And eating all of my time haha)

---

### Post by henriquemaia on 2006-09-25
Check if those files have execute permission.

---

### Post by coastdweller on 2006-09-25
> **henriquemaia said:**
> Check if those files have execute permission.

Ok, I keep running into a problem saying "Read-only file system".

When I try to boot normally I can't get into the system to look around, make changes or even check to see if those are executable.

Its like the system is chewed up, just dont understand it being "That" bad since its a fairly new install.

One error is: unable to initiate PAM: no such file or directory.

When I boot without recovery I can't login.

Update: Booting into recovery mode I guess leads me to the understanding that there are no scripts (Not sure how this can happen), unless the server has been hacked, I guess very possible).

I attempted a reinstall, but not seeing an option to leave the file system intact I backed out of writing to the partitions.

How do I "Overinstall" without writing over /home, thats all I care about really.

I'm thinking the only way to do this is to hook the drive to another system and copying home (But it doesnt save the databases) and just reinstall. Really dont want to do that at this point yet, its a non-critical machine.

Update 2: When attempting a reinstall after partition editor it says :No root partition:, something weird here... haha but! I'm hanging in there, just need help.

---

### Post by henriquemaia on 2006-09-25
Do you have a separate /home partition?

---

### Post by coastdweller on 2006-09-25
> **henriquemaia said:**
> Do you have a separate /home partition?

I'm not sure, I used the recommended partition scheme when installing 3 weeks ago.

Update: When reinstalling and looking at the "Manually edit partition table" I see:

> #1 primary 79.2gb B K ext3 /media/hda1
#2 logical 3.1gb F swap swap

Update 2: When reading the "Help on partitioning" I see that the K denotes that it is already partitioned and will be used, and F it will format, in this case the swap partition will be formatted but /media/hda1 will not.

Problem is when I attempt to write changes and continue it says "no root file system specified" with a red background.

This isn't the worst thing that can happen to me but it does suck =)

If I have to I'll completely wipe out the thing and start over, just sucks to lose the site. (Yes, this is a lesson on backing up..)

---

### Post by henriquemaia on 2006-09-25
Use the liveCD and boot through it. Then mount the partition where you keep the files and backup them remotely (or to a CD, for example). Then you can wipe everything out peacefully.

---

### Post by coastdweller on 2006-09-25
> **henriquemaia said:**
> Use the liveCD and boot through it. Then mount the partition where you keep the files and backup them remotely (or to a CD, for example). Then you can wipe everything out peacefully.

I have a kubuntu cd, you don't mean the server cd right?

I'll give this a shot, wont be until tonight though, have a day of work to get through lol, damn work.

Thanks for the help, I'll report tongiht how it goes.

---

### Post by henriquemaia on 2006-09-25
Any liveCD will do. But it has to be a liveCD, not an installation one. Good work to you.

---

### Post by coastdweller on 2006-09-25
> **henriquemaia said:**
> Any liveCD will do. But it has to be a liveCD, not an installation one. Good work to you.

Cool, I found my kubuntu and have loaded with the livecd, I've just copied the profile folder and now hunting if its even possible to find the database (MySQL).

Thats the only thing i would mind losing, but if i lost it, oh well but hey! I have a mounted file system, that's new for me =)

Thanks again for your help, I probally was getting frustrated and wouldnt have thought of booting with the livecd to even get the data! thank you.

Update: I found the database located at: /var/lib/mysql/joomla

I've pico'd some of the files and indeed that's the content that I'm looking for.

I know I'm in disaster recovery now and should probally open a new thread.. yep, I should. I just don't know how to effectively back this database up to then use in the future with a new install of the server and scripts (Site scripts).

**Update Final**: Well I found I could tar -cf joomla.tar *.* into joomla.tar

I then mv'd the file to the live desktop and then moved it to the remote server.

I'm reinstalling the server from fresh.

Ultimately this box was the last one I expected to get trashed first. I figured the box I'm on (My main desktop) would be the one I would kill first lol.

I'm glad I wasn't relying on it foolishly and have a chance to actually learn remote backup procedures for this next install (That is primary for me to learn next).

Server reinstalled =( lol

Now to document everything I do..

---

### Post by henriquemaia on 2006-09-25
Don't forget the most basic lesson of them all: always keep backups of your important things. Always!

---

### Post by coastdweller on 2006-09-25
> **henriquemaia said:**
> Don't forget the most basic lesson of them all: always keep backups of your important things. Always!

This is a non-critical machine, I run 4 linux production serve4rs remotely with dual rives and off server backup so this is more me trying to learn linux front to back without losing anything critical, it was just a personal site I put togehter real quick.

My home was to fix it, not just reload it so I could learn but I dont think that was possible so just blew it out.

---

