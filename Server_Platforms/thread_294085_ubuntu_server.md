---
title: "ubuntu server"
date: 2006-11-06
forum: Server Platforms
---

### Post by magpy on 2006-11-06
Hi everyone, I'm new to Ubuntu and linux

I have just installed the server edition.
It installed o.k.

But I have some problems:

During installation the network wasn't able to configure with DHCP.  I did this manually:

ip address - 12.57.62.1
subnetmask - 255.255.255.0
gateway address - 12.57.62.254
nameservers - 12.57.62.2.
hostname - cm

I was not sure about the proxy information - so I left it out

-----------

There are several command prompts that I cannot get to work, which result in permission denied [even when using sudo].

These are:

/etc/hosts
/etc/network/interfaces
/etc/resolv.conf

Also I cannot install the desktop using the command:

sudo apt-get install ubuntu-desktop

I get this imformation displayed:

building dependency tree...
could'nt find package ubuntu-desktop

thanks for your help - much needed

---

### Post by kidders on 2006-11-06
Hi there,

/etc/hosts, /etc/network/interfaces, /etc/resolv.conf are not commands ... they are simply configuration files.

> building dependency tree...
couldn't find package ubuntu-desktop

Is your internet connection working? You should check /etc/apt/sources.list to make sure your package sources are sensible.

---

### Post by Kangaroo on 2006-11-06
Was the IP-Address assigned to you by your ISP ? 

Looks to me like a Class A Network Adress but the subnet mask is for Class C Networks.

---

### Post by magpy on 2006-11-06
Hi thanks for advice it's shed light on a few things

The computer is not conected to the internet and the ip address I assigned myself.  

What I'm trying to do is have the server running on ubuntu connected to a win xp computer.

I have a few further questions:

Do you have to be connected to the internet in order to get the
ubuntu-desktop running?

thanks for the help

---

### Post by kidders on 2006-11-06
> **magpy said:**
> The computer is not conected to the internet and the ip address I assigned myself.
In that case, you should probably stick to the convention, and assign yourself IPs in one of the ranges reserved for private use. 12.57.62.1, for instance, belongs to AT&T's New York infrastructure.

> **magpy said:**
> Do you have to be connected to the internet in order to get the ubuntu-desktop running?

Strictly speaking, you don't *need* an internet connection, but it is a convenient way of getting hold of new software.

---

### Post by magpy on 2006-11-06
cheers I would'nt want any corporate bods on my back.

But does that mean I should be able to run:

sudo apt-get install ubuntu-desktop 

without internet connection.

Also this may seem like such a simply stupid question, but how do you get to the directives/files:

/etc/apt/sources.list
/etc/resolv.conf
/etc/network/interfaces
and
/etc/hosts

many thanks

---

### Post by kidders on 2006-11-06
You can "apt-get install" anything you want, provided you have (or can get) all the necessary .deb packages. Without an internet connection, you'd have to get them some other way and copy them onto your hard disk.

Generally, you can modify system configuration files in any text editor. So, for instance, if you were interested in switching DNS server, you could do it with **nano -w /etc/resolv.conf**. It's always worth reading the man page for a particular file before you tweak it though ... mistakes can often open security holes or break your system. You should also be careful not to make unwise changes to their file access permissions.

---

### Post by magpy on 2006-11-06
Thanks

That must mean that the server edition does not come with ubuntu-desktop because I tried to apt-get it but to no avail.
[or if the server edition iso did come with the ubuntu-desktop then does this indicate another different problem?

I will experiment with the nano text editor.

Thanks

---

### Post by kidders on 2006-11-06
No, the server version of Ubuntu is primarily intended to run on a server, so weighing it down with graphical environments, etc. is not seen as desirable. You can still install one if you want to though :-)

---

### Post by magpy on 2006-11-06
Thanks

That must mean that the server edition does not come with ubuntu-desktop because I tried to apt-get it but to no avail..

Also I will let you know how i get on with the nano text editor.

Thanks

---

### Post by magpy on 2006-11-06
Cheers 

A couple of things - I gave "sudo apt-get install ubuntu-desktop" a try but it generated the message indicating that the dependency tree / package could not be located.

Could this indicate another problem?

----

Also I looked at the files using:

nano -w /etc/hosts

This was good - but how do you look at the files in their raw original unmodified state?


Thanks for help by the way

---

### Post by kidders on 2006-11-06
Hey again,

> **magpy said:**
> I gave "sudo apt-get install ubuntu-desktop" a try but it generated the message indicating that the dependency tree / package could not be located.
If there's a gap in the dependency tree, then you've probably forgotten to get hold of one or more required packages. Since you don't have an internet connection, you'll have to go do whatever it was you did the last time you needed extra packages, all over again ... a friend's house, maybe?

You might have overlooked the fact that an application's "immediate" dependencies may also depend on additional packages. :-( It can sometimes be hard to know for sure that you've remembered to get them all!

> **magpy said:**
> how do you look at the files in their raw original unmodified state?
Nano is just a plain, simple text editor (one of many). Files you open with it *are* in their raw original, unmodified state. I'm not quite sure I understood this question properly :-k Perhaps you are comparing it to apps like OpenOffice, that hide the _real_ data underlying your documents, and only show you an "interpreted" version of them. Plain text editors don't work that way.


Thanks for help by the way[/QUOTE]

---

### Post by r0ydster on 2006-11-08
> **magpy said:**
> Cheers 

This was good - but how do you look at the files in their raw original unmodified state?

Easiest way to only look at a file (not edit):

cat /etc/hosts

type "man cat" on the command line (without the quotes), and read, read, read!

Mike

---

### Post by magpy on 2006-11-08
Cheers all

I will look into that. If this thread appears dormant over the next few days it's becasue I'm trying to work things over.

Also does anyone know of any ubuntu - LAMP developper communities based in London?

---

### Post by kidders on 2006-11-08
> **magpy said:**
> Does anyone know of any ubuntu - LAMP developper communities based in London?

You might have already seen it, but if not, this page might be a good starting point for you ... [https://wiki.ubuntu.com/LoCoTeamList](https://wiki.ubuntu.com/LoCoTeamList)

---

### Post by magpy on 2006-11-20
Hi all

I have hit a problem.  My computer won't boot up.  Everytime I try to boot up I get an error message saying:


Disk failure 1780


Does anyone know what this means - or how to repair it?

To try and solve the problem I have tried a re-installation but this won't go ahead.

I get as far as setting up the partitioner but then cannot get any further - does anyone have any idea why this maybe?


Also I have one last question:


When I first installed ubuntu 6.06 no ethernet was detected [though there is LAN facility], also the DHCP could not configure automatically:

Are these two events related?  If so how can I get the ethernet working or recognized?


Many thanks for your help

---

### Post by funkyade on 2006-11-20
[http://www.uktsupport.co.uk/compaq/faq/comppost.htm](http://www.uktsupport.co.uk/compaq/faq/comppost.htm) for the disk error.

> 1780 - Disk 0 Failure HDD Drive / Format Error Run Computer Setup, Replace HDD

doesn't sound good.

---

### Post by magpy on 2006-11-20
I know you're right mate

Does it mean what I think it means  -  The machine has had it?

Does anyone know a way arouond this error message?

Has anyone experienced it and overcome or solved the problem and got the machine back in a workable state?

Cheers

Magpy

---

### Post by r0ydster on 2006-11-21
> **magpy said:**
> Does it mean what I think it means  -  The machine has had it?

Hopefully you have a backup of the data on that hard drive.  

More than likely, your hard drive is dead.

You should keep the "machine", just get a new hard drive.


Mike

---

### Post by magpy on 2006-11-21
understood - thanks for the help

---

