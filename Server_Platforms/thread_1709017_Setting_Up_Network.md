---
title: "Setting Up Network"
date: 2011-03-17
forum: Server Platforms
---

### Post by COGlory on 2011-03-17
So I recently made the switch from Windows XP to Ubuntu Server for my server.  I was blown away at first (and it took me a good ten minutes to figure out why my password wasn't working.  That's what you get for not reading anything.)  

Anyways, I neglected to set up a network at the time of installation (though I did install LAMP) and I'm now struggling through setting one up.  I've read all sorts of documentation, but whenever I type in
```
/etc/network/interfaces
``` it tells me that it doesn't exist.  If I try creating it, when I attempt to save it, it tells me that there was an error and it can't save.  (I'll write them down next time.)

I also tried going to ```
/etc/resolv.conf
``` and it tells me that doesn't exist either.  Is this due to a corrupted installation or something?  Is there an alternate way of connecting to teh interwbz?  Or do I just have the worst luck of anyone?  Also, I believe I'm running 10.10 and I'm logged in with the account I created when I installed Ubuntu Server.

Thanks!

---

### Post by SeijiSensei on 2011-03-17
> **COGlory said:**
> /etc/network/interfaces it tells me that it doesn't exist.  If I try creating it, when I attempt to save it, it tells me that there was an error and it can't save.  (I'll write them down next time.)

I also tried going to /etc/resolv.conf and it tells me that doesn't exist either.

You can't edit either of those files, or any others outside your home directory and /tmp, unless you use [sudo]("https://help.ubuntu.com/community/RootSudo") to gain root privileges.  It's possible neither of those files exist because networking wasn't set up in the first place.

---

### Post by TechSupportx86 on 2011-03-17
[COLOR=Black]I may be of some assistance (luckily SAMBA and networking are the 2 things i have a decent grasp on)

It's odd that your network hasn't been configured (even skipping DHCP setup should have given you something), but let's try anyway.[/COLOR] [COLOR=Black]

First see if this command gives any results:[/COLOR] [COLOR=Black]

[/COLOR]```
[COLOR=black]ifconfig[/COLOR]
```[COLOR=black]
mine for example looks like this:

[/COLOR]```
 [COLOR=Black]eth0      Link encap:Ethernet  HWaddr 00:e0:4d:4e:95:a8
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe4e:95b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21541228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10241382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1545593202 (1.5 GB)  TX bytes:613135016 (613.1 MB)
          Interrupt:23 Base address:0xa000

lo        Link encap:Local Loopback[/COLOR] [COLOR=Black]
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:852 errors:0 dropped:0 overruns:0 frame:0
          TX packets:852 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:61248 (61.2 KB)  TX bytes:61248 (61.2 KB)
[/COLOR]
```[COLOR=Black]You have eth0 (primary connection) and lo (loopback or "local host")

If all you have is lo then you might need to edit the /etc/network/interfaces file. Now forgive me for asking (Tho i am assuming you are new), but are you using a text editor to edit that file? or just typing in "/etc/network/interfaces"?[/COLOR] [COLOR=Black]

The reason i ask is the complete command for editing that file should be:[/COLOR] [COLOR=Black]
[/COLOR]```
[COLOR=Black]sudo nano /etc/network/interfaces[/COLOR]
``` [COLOR=Black]

and again mine looks like:[/COLOR] [COLOR=Black]
[/COLOR]```
[COLOR=Black]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
[/COLOR]
```You must hit ctrl+x, and then "y" then enter to save. Let us know what you get :KS

---

### Post by COGlory on 2011-03-17
> **SeijiSensei said:**
> You can't edit either of those files, or any others outside your home directory and /tmp, unless you use [sudo]("https://help.ubuntu.com/community/RootSudo") to gain root privileges.  It's possible neither of those files exist because networking wasn't set up in the first place.

I tried sudo nano /etc/network/interfaces and it didn't work.

**@TechSupportx86**

I manually skipped it because at the time of installation, I wasn't connected to the internet with a LAN cable.  (It's a long story but basically I have one monitor and two computers.)

I'll see what ifconfig returns, and yeah, I'm very new but I did figure out the sudo nano thing.  :)  Mine has none of the 

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface

```

it's just a blank page, and it doesn't let me save it.  (I tried the Ctrl+X and Y method already.)

---

### Post by TechSupportx86 on 2011-03-17
Post the output from ifconfig, maybe the interfaces file just got messed up

---

### Post by SeijiSensei on 2011-03-18
Personally I'd just reinstall and set up networking.  That's going to be a lot easier than trying to fix this piecemeal after the fact.

---

### Post by COGlory on 2011-03-18
> **SeijiSensei said:**
> Personally I'd just reinstall and set up networking.  That's going to be a lot easier than trying to fix this piecemeal after the fact.

Not for me!  :lol:  The IDE-2 is broken on my motherboard so I can't install a CD drive, so I have to install with USB which the BIOS gives me a hell of a time booting from.  No matter what I set it to, ubuntu always boots, not my USB (and yes, I did "burn" the .iso to it) so unless there's a way to uninstall, I doubt I'll be doing that.  (Though I may have a spare Paragon Partition Manager copy lying around somewhere, I just need to find a blasted floppy drive...)

---

### Post by volkswagner on 2011-03-18
> **COGlory said:**
> I tried sudo nano /etc/network/interfaces and it didn't work.

That is not very descriptive.... What didn't work?  did it open the file?

> **COGlory said:**
> 
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface

```

it's just a blank page, and it doesn't let me save it.  (I tried the Ctrl+X and Y method already.)

The above appears to prove that the /etc/network/interfaces file exists. It is just short on info.

Ctrl+o saves the file, then you have to hit enter to confirm save, then Ctrl+x to exit out.

First lets see if your network card is recognized by Ubunutu.

```
lspci -v | grep Network
```

I don't see the results of your
```
ifconfig
```

---

### Post by COGlory on 2011-03-19
> **volkswagner said:**
> That is not very descriptive.... What didn't work?  did it open the file?

sudo nano /etc/network/interfaces returned with a completely blank page.  

> **volkswagner said:**
> 
The above appears to prove that the /etc/network/interfaces file exists. It is just short on info.

Exactly.  It's not there.  
> **volkswagner said:**
> 
Ctrl+o saves the file, then you have to hit enter to confirm save, then Ctrl+x to exit out.
  
Yup, I tried that.  It returned some error.  When I get time, I'll try all this stuff that's been suggested, and write down the errors.  (I've just been pretty busy the last couple days.)

> **volkswagner said:**
> 
First lets see if your network card is recognized by Ubunutu.

```
lspci -v | grep Network
```

Alright, thanks, I'll check.  

> **volkswagner said:**
> 
I don't see the results of your
```
ifconfig
```
Like I said, I've been busy.  I'll do it tomorrow though.  :)

---

### Post by COGlory on 2011-03-20
OK:

```
lspci -v | grep Network
```  

returns nothing.  I tried it with sudo as well.  Nothing happens.  

```
ifconfig
``` 

returned with

```
lo link encap: Local Network
inet addr: 127.0.0.1 Mask 255.0.0.0
inet6 addr: :: 1/128 Scope: Host
UP LOOPBACK RUNNING mtu : 16436 Metric: 1
RX Packets all returned 0 0 0 0, I forgot what it sent, etc.
TX Packets all returned 0 0 0 0 ^^
Collisions 0 txq ueuelen: 0 (might have misspelled something...)
```

I've got a small idea what this means...not really sure though.  

The errors that I get when attempting to save 

```
/etc/network/interfaces
``` is "File Directory does not exist."

---

### Post by waddle1463 on 2011-03-20
If you have lower than ubuntu 9 installed I'm pretty sure you would use 
> Gksudo. Then run your command. I used to have ubuntu 8 and I upgraded cause terminal commands were a pain in the rear end

---

### Post by HugoSerrano on 2011-03-21
Hi!

What's the output of the command:
ifconfig -a

Regards!

---

### Post by volkswagner on 2011-03-21
> **COGlory said:**
> OK:

```
lspci -v | grep Network
```  

returns nothing.  I tried it with sudo as well.  Nothing happens. 

OK, try it without detail, to see if you get anything related to network card.

```
lspci
``` 

> **COGlory said:**
> 
The errors that I get when attempting to save 

```
/etc/network/interfaces
``` is "File Directory does not exist."

This is very odd.  If the file does not exist, opening it with nano should allow you to  create the file, then saving it should not return such an error.  It appears you may have a broken system.  A reinstall may be in order.

```
sudo nano /etc/network/interfaces
```

If the above opens a truly blank page, if you type anything in it and hit ctrl+o, it should save it.  If it does not, your problems are greater than no network.

Can you try booting a live CD such as Ubuntu Desktop version, to see if your network card works?

---

### Post by COGlory on 2011-03-22
> **volkswagner said:**
> OK, try it without detail, to see if you get anything related to network card.

```
lspci
``` 



This is very odd.  If the file does not exist, opening it with nano should allow you to  create the file, then saving it should not return such an error.  It appears you may have a broken system.  A reinstall may be in order.

```
sudo nano /etc/network/interfaces
```

If the above opens a truly blank page, if you type anything in it and hit ctrl+o, it should save it.  If it does not, your problems are greater than no network.

Can you try booting a live CD such as Ubuntu Desktop version, to see if your network card works?

Alright, I'll try reinstalling.  And yes, the live version does work.

---

### Post by COGlory on 2011-04-04
So I just thought I'd let everyone know that after a heck of a lot of finagling, I finally formatted my disk and reinstalled Ubuntu Server 10.10, (this time with the cable plugged in) and it's networked and up and running now.  

Thanks everyone!

---

### Post by usatonycuba on 2011-04-04
> **COGlory said:**
> So I just thought I'd let everyone know that after a heck of a lot of finagling, I finally formatted my disk and reinstalled Ubuntu Server 10.10, (this time with the cable plugged in) and it's networked and up and running now.  

Thanks everyone!
then, you should mark  tread this as solved? ;) :P

---

### Post by COGlory on 2011-04-13
Capital idea.  :)

---

### Post by usatonycuba on 2011-04-18
> **usatonycuba said:**
> then, you should mark  tread this as solved? ;) :P

> **COGlory said:**
> Capital idea.  :)

seriously @COGlory, you CAN mark a thread as Solved by going to Thread Tools at the top of the page

In the same way you asked for help, others do, that way... the forum administrators and users who try to answer your questions, may have an idea of whether the thread  has outstanding unsolved problems, or its SOLVED.

Thanks

---

### Post by garycahill on 2011-05-24
If you look up examples of iproute2 then you can manually add and remove IPs to check your cables are working and correct.

gary

---

