---
title: "Network Logistics"
date: 2006-07-27
forum: Server Platforms
---

### Post by tastefulasever on 2006-07-27
I'm wondering about setting up a small network consisting of about 7 terminals, 1 server, and 1 WinXP box.  My family's business needs to runs 2 Windows programs (otherwise windows would be out of my life), and we would like to run them from any terminal in our shop.  The plan is to run all the terminals through a Linux server, which will be connected to the windows box running WinXP Pro.  I know that WinXP Pro can support up to 3 Remote Desktop sessions.  So, will I be able to start multiple RDP sessions on WinXP, from the terminals, through the server?

Here's an illustration
[FONT="Courier New"]
     :)
     ||           
     \/           
T T T T T T T     
     ||           
     \/          
   Server---->Internet
     ||           
     \/           
    WinXP

:) = Me
T = Terminal
[/FONT]

Still confused?
Basically, as far as the windows machine is concerned, all RDP sessions are being initiated by the server.  So, can one initiate multiple RDP sessions between the same two machines?

Because WinXP Pro only allows 3 RDP sessions, I would like to be able to terminate any session from any terminal, even if the session was initiated from another terminal, and I would like to be able to transfer a session from one terminal to another.  Can the same user be logged onto the server from multiple terminals?

Further more, all documents that our WinXP programs use will be stored on the server, along with all other data that isn't relevant to the WinXP OS or the terminal OS'.
Each terminal has speakers and a microphone, so I hope to have an intercom system, as well as internet access and a music database.

The hardware I have right now is:

7 Dell Optiplex GX110 computers w/
500mhz Pentium III
128 MB ram
1 ethernet card
These are the terminal machines

1 Dell Precision 340 computer w/
2.2 Ghz Pentium 4
1 GB ram
1 ethernet card   (I think I need 2?)
This is the machine I intend to use as the server

I have yet to buy the machine I will use to run WinXP, and I also don't know what sort of switchboard/router I need between the server and terminals. 


Thanks in advance for everyones help, advice, criticism, insults, pieces of the puzzle, etc.

---

### Post by hasimir44 on 2006-07-27
Is there a reason why the windows box will only be connected to one Linux box? Why not use a router, then you wouldn't have to worry about multiple rdp connections at the same time from the same server. 

You can terminate an rdp connection from windows task manager (users tab) as long as you're an administrator. 

I know nothing about intercom systems. Good Luck.

---

### Post by inthewayboy on 2006-07-27
Firstly, you do know using three RDP's to an XP Pro is not legit, but it is possible with the right files.

Next, I think the plan you have should work, except for a few pot holes. For instance, these applications sound like they might be somewhat proprietary, and that can often mean that certain things don't work. We have an application that locks the data file, and if the users don't exit correctly it can lead to data corruption. You idea of logging off and on to different terminals makes me worry...of course if it's stable stuff then you should be okay.

A suggestion would be to somehow integrate Virtual Machines into this. I can't really think of how it would be useful here, but I'm sure there is a great solution. You could at least use it to bypass having to buy a box to host XP, since you could run that off the linux server as well. I'm a big fan of vmware in particular.

The questions you pose about the user being logged on to multiple machines is another problem. Again, since it's not legit I don't think there are published details as to how the user sessions work with 3xRDP. In a Terminal Server environment you can enforce settings that regulate this. But I don't think that level of management is in XP. Looking at gpedit.msc, there are Terminal Server settings, but I can't say if they actually apply to XP. But that would be a great place to start.

And I'm just curious, what will you be using as the terminals host OS? Something like this looks like a good idea for some form of PXE distro, so you can boot from the network. I've seen some pretty slick ones that basically boot to an open source RDP client, but it doesn't give you much else. The one I've seen is at 2x.com, and I think it's free. They have some nice products, and many are free for small sites like yours.

---

### Post by Socratez on 2006-07-28
I agree with the previous poster. I would move towards a vmware solution to better suite your needs. Assume of course the application is able to avoid the data corruption as stated. I would load some more RAM into the DELL and run your XP Pro as a VM. You can probably fix the Remote connection problem witha solution like this [http://sig9.com/articles/concurrent-remote-desktop](http://sig9.com/articles/concurrent-remote-desktop). That allows concurent sessions to be logged into a XP Pro machine. As for the terminals a nice PXE or light weight Ubuntu/Xubuntu install should suite your needs. Make sure to lookup your hardware specs to ensure the Hardware meets the rewquirements to run them. 

Good Luck

---

### Post by tastefulasever on 2006-07-28
I am planning to run debian on the terminal machines.

I didn't realize that running 3 RDP sessions in XP Pro was illegitimate.  I suppose it is also illegitimate to run the same copy of XP on more than one virtual machine?  I might be able to live with owning several copies of XP Home.

Okay, I just read the XP SP2 EULA and it makes no reference to virtual machnies, so I guess that means I can run XP as much as I want on VMWare and still be within my rights.

New question; The two windows programs that we use (MasterCAM 9 and kCDW) require USB keys. Does anyone think it will be a problem to access these USB keys from VMWare?

---

### Post by LordHunter317 on 2006-07-28
To do this legally, you're goign to have to run some edition of Windows Server and get the right licenses.  SBS 2K3 may be your best choice, though it comes with lots of stuff you will not need.

I'm pretty sure that Windows XP is licensed for running on one machine only.  You can't use the same instance on multiple seperate virtual machines.  Some versions of server are licensed for this in some secnarios.  The right people to ask of course, are MS.

You should probably just buy another GB of RAM for the server and virtualize Windows using VMWare server.  It seems somewhat senseless to buy another whole box just for that.

Also, do not put the Windows box on a seperate network as you showed, whatever you do.  That's senseless and bad network design.  You're complicating topology for no gain.

VMWare can access the USB keys, though VMWare server may have some limitations.

---

### Post by tastefulasever on 2006-07-28
After having wading through MS SBS 2003 licensing crapola, I have come to the conclusion that these (insert expletive here) have got me by the balls.  My understanding is that on top of the standard server license, I need one user CAL (client access license) for each person/device that is accessing the server, plus one TS CAL (terminal services client access license) for each windows session that is started from a terminal.  From my understanding, you can't even do any system administration without at least 1 CAL.  Maybe someone can shed some light on the situation.  For me, this is about to turn into "Another reason to hate microsoft" thread.  They make it so easy to feel better about breaking the EULA than to pay for proper licensing.

Anyhow, I installed QEMU and I'm installing XP right now to see if MCAM and kCDW are going to work.  If QEMU doesn't work out, I'll give VMWare a shot.

---

### Post by LordHunter317 on 2006-07-28
> **tastefulasever said:**
> My understanding is that on top of the standard server license, I need one user CAL (client access license) for each person/device that is accessing the server, plus one TS CAL (terminal services client access license) for each windows session that is started from a terminal.That is correct.  SBS2K3 ships with like 5 user CALs though.  Still have to get the TS cals.

It's possible to purchase plain Server with CALs, but I'm not up on costs and options recently.

> Anyhow, I installed QEMU and I'm installing XP right now to see if MCAM and kCDW are going to work.  If QEMU doesn't work out, I'll give VMWare a shot.I wouldn't even bother with QEMU.  Performance and management won't be good enough to be worthwhile.

---

