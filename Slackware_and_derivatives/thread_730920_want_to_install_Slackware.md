---
title: "want to install Slackware"
date: 2008-03-21
forum: Slackware and derivatives
---

### Post by niethslim on 2008-03-21
Well, I got pretty bored with Ubuntu so I decides to try Slackware.
I want to dual boot it with windows like I do with ubuntu.
If I will leave my /home partition as it is and install slack over the Ubuntu installation partition, will it work properly? What are the chances for /home data loss?
What do I need to know about my hardware before installing?
Any tips you have for a Slackware newb would be welcome.

I'll ask more question after I get some replies.

Thanks in advance,

---

### Post by Bachstelze on 2008-03-21
Yes, installing Slack over Ubuntu and keeping your /home partiton will work. However, I would sugges using another login name or moving your old home directory (somthing like *sudo mv /home/user /home/user.ubuntu*) so you don't get any conflicts.

You don't really need to know anything about your hardware. Slackware comes with a generic kernel with pretty much all the modules like Ubuntu does, so you don't have to compile your own. However, Slackware sticks with the official kernel, so you might have to hunt for drivers that are not in it (graphics, wifi, whatever).

---

### Post by Junglizer on 2008-03-22
Though compiling your own is fun, and thats often a good place to at least check if you're having problems getting something specific working. I always have to fiddle around in there to get APM or ACPI working properly.

---

### Post by digger95 on 2008-04-14
Hey just wanted to say 'have fun with Slackware'!  I love it myself and can't see me using any other distro again, ever.  It really gets under your skin and once you get to know its simplicity and stability you really just don't want to leave it.  I have great respect for Ubuntu because it's the distro that finally teased me away from Windows, but Slackware got to me pretty quick and I'll never go back now.  :)

---

### Post by cardinals_fan on 2008-04-14
Slack is fun, no doubt about it.

---

### Post by saulgoode on 2008-04-15
Well this is a little bit belated, but for posterity's sake I will provide some of my own opinions.
> **niethslim said:**
> If I will leave my /home partition as it is and install slack over the Ubuntu installation partition, will it work properly? What are the chances for /home data loss?
I would not recommend this. There won't be much chance for data loss but you might very well experience other, less critical, problems. For example, your webbrowser profile in Ubuntu might conflict with that of SW (particular WRT extensions, bookmarks, and cookies), or some of your environment variables in .bashrc might be different. 

You can, however, share a great deal of your data files between the two partitions by using links between directories. For example, you could have a symbolic link from a /home/niethslim/Pictures directory to /mnt/ubuntu/home/niethslim/Pictures (similarly for a Documents directory, et cetera). This way, any files saved to that directory actually get placed on your Ubuntu partition.

For this to work, you will want to have the numeric userID be the same in Ubuntu as in Slackware. You would do this by running '**id -u**' in Ubuntu and then using the resulting number when you do an "adduser" in Slackware. (This is necessary because permissions are based on the numeric ID, not the name.)

> **niethslim said:**
> What do I need to know about my hardware before installing?
I wouldn't worry too much about H/W information; just let the Slackware install detect it and set it up (although you might wish to note your printer setup, as Slackware relies on CUPS's setup for configuration). You may wish to make note of your network setup: your gateway's IP, the nameserver(s), and your hostnames (and IPs, if you are using static IP addresses).

---

