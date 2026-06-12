---
title: "Setting up a server for small business"
date: 2007-01-21
forum: Server Platforms
---

### Post by Crashmaxx on 2007-01-21
I work for a small business that does a lot of military prototype work. So we are basically a machine shop, but we do the design work also. We are moving to a new shop and want to redo the whole network. All the workstations are Windows XP Pro, and that can't change, unfortunately. I could probably convince my boss to switch to Linux, except we use a lot of propriety CAD software and some other weird bits here and there to run the machines. So that's not even an option. But I have been put in charge of setting-up a server for the new shop and configuring the network. But I'm not really sure how to do a lot of things, cause I'm primarily a desktop user, though I did make a home server for practice, but it doesn't do much other then download torrents.

For hardware, I am looking at a setup like this:
Cable Modem> Server> Network Switches> Clients

I was going to have the firewall and routing and everything on the server, but that appears to be a security flaw, so should I get a separate hardware firewall to put in front of the server? And we have so many jacks that one switch won't handle them all, but how do I hook them all up to the one Ethernet port on the server?  Originally, I was going to use the modem's built in router for this and just have the server as another client of the router, but I want to use the server as a gateway and transparent proxy, so I want it to be in line.

Also, any advice on what to get in a server? A simple tower case one with RAID 1 hard drives was what I was thinking. But I need help setting-up RAID 1, cause I've never done that before.  And what would be best for backup? A usb drive, or network drive? Or maybe off-site backups?

For software, I am even more lost. Currently, then network is just a Windows peer-to peer setup, so that's why I am thinking that the firewall on the server would be more then good enough. Here are the things I want the server to do:

1. Firewall, IPtables setup properly should be fine, but how do I configure it properly?

2. Webmin, I use this on my home server and like it, but how to you add modules and can it control everything I need?

3. Proxy and Filter, so Squid and DansGardian. But I don't really want to block content, just viruses and spyware and phishing and other crap windows will download by itself. And I want it to be transparent to anyone using the network, so it it must be in line or something, no config at client level is a must.

4. Anti-virus and Anti-spyware, goes along with 3, can I make it so the windows clients can run basically insecure, no firewall, no anti-spyware, no antivirus, and have the server take care of all of this remotely? I want it to block all possible baddies and scan all the clients for crap. As well as scan its stored files for anything. Is this at all possible?

5. Windows install and patching, I've heard of this before, but have no idea. Can I set-up a default XP pro install with all the software I need and have the server install it on all the clients, or anything like this? At least some sort of ghosting so if a machine goes down, it is easy to restore.

6. File sharing, this is the whole point in the first place. I want everyone to save all their work to the server and access it all from this one place. I will use samba, but how do I configure it to be mounted as a network drive on boot? How do I use it with no user and password, but instead all LAN machines get access or similar? Maybe even different windows log-ins get different permissions. I still can't even get my edgy machine to mount my shared drive at home.

7. Backup, I was thinking of something where the server gets an incremental backup to a networked drive that normally only the server can access. And I want the server to have a RAID 1 setup. But if the server dies entirely, I want the network drive to be easily reconfigured to allow everyone access, so if the server dies, we don't lose everything, even temporarily. Or is just backing up all the needed files on the clients a better way to do this and allow local work and a failsafe if the network goes down. In that case, how would I setup the server to grab all the file changes and serve them to everyone, so any change one person makes could be seen all over the network?

8. Remote access, I want to be able to securely admin the server and have access to the network, but I want it to be done securely. Its VPN the best approach and just make it so you get secure remote access to the VPN and then you "appear" to be local? Or just simple SSH? Or what?

9. Global Windows Accounts, can I make it so everyone would have a windows login that is actually on the server and the same everywhere, and just have local admin and guest accounts and have the programs themselves be local? Or is that just a dream?

10. Local mail and messaging, we currently have some goofy local mail system accessed with outlook. How can I move this to the server and make it so tasks assigned by my boss are automatically at everyones stations? What is the best way to setup local messaging and possibly web cams?

11. Windows network host, how do I make the server the windows network server and how do I make it so all computers on the network get the same network settings automatically?

I think that is everything, any help or advice or how-to's would be great. I need to order the hardware tomorrow, but I still have time for everything else. I'm sure I can at least get the basics working, but I would really like to blow him away and make everything work better. Thanks.

---

### Post by genesis[OFT] on 2007-01-21
Whoa!  That's a whole 'lotta questions there, matey :eek: .  I'll have a go, nonetheless.

OK, so you're a business that does Military prototyping and design work - Can I assume that security is a large factor in your whole setup, especially if you're working in such an area?

All your Clients are running Microsoft Windows XP SP2, I hope - and even though there are CAD programs on Linux, it'd be a bit of a learning curve to swap O\Ses while you're swapping the network too, especially for the end users.  So, just stay with Windows for the moment, though I admire your enthusiasm :D.

So, down to the nitty gritty.  You want to have a setup, Internet-enabled, with said Internet access being provided by a Cable Modem.  Righto. Well, I'll suggest what it should look like after your hardware is setup:

I.S.P. <---> Cable Modem <---> Hardware Firewall <---> Server <---> Network Switches <---> Clients

Notice I added in 'Hardware Firewall'.  The reason for this is that it isn't very secure to have a File Server also take up the role of being a NAT device as well.  Reasoning for this is simple - If your router's hacked, then so are your files.  So, that's what I suggest - you could swap the 'Hardware Firewall' with a another Linux box, it doesn't have to be at all beefy either, as it'd just be doing proxying, routing and masquerading.  However, it's paramount that if you go for another Linux box, that it has at LEAST 2 network cards - a 'Hardware Firewall' would already come with 2 (and possibly more), but, yeah, you'll need at least 2.

Server Hardware?  Well, that's completely up to you.  Since you're doing CAD drawings and prototyping for CnC Machines (I imagine), I'd suggest 'lotsa space and 'lotsa redundancy.  So, 2x 500GB SATA or SCSI Hard Drives would be more than sufficient (SCSI would be the *much* more expensive option, mind you), with a RAID card\RAID-supporting motherboard.  In terms of RAID, I would say that Mylex is a very well known RAID card manufacturer, and they're very easy to setup too.  At least 1GB of RAM too, mostly for future proofing, and probably some sort of Xeon CPU as well.  Case doesn't really matter, unless you want to put it on a rack, however, redundant PSUs would be great, with a UPS protecting the server as well.

Backup wise, you'll have your first line of defense in RAID firstly, and that's pretty hard to beat anyway, however, simply a USB External Hard Drive, of respectable reliability and capacity would be OK too.  You can go overboard with nightly tape backups, offsite backups, numerous numbers of USB Hard Drives and whatever else, but, that's really up to how much money you have, and how much time you're prepared to put into the job :wink: .

Software?  Well, Canonical's Ubuntu Linux would be a great place to start, 'o course :D.  I'd suggest Ubuntu Linux 6.06 LTS (Dapper Drake) too, purely because it has 3 years Desktop and 5 years Server support - *read: LTS (Long Term Support) ;)*

I'll make another post for your questions below in just a sec. :)

---

### Post by genesis[OFT] on 2007-01-21
OK, and now your list of questions :) .

1. Firewall - yes, you will need one.  All your firewalling can be done by either that 'Hardware Firewall' or a seperate Linux box with those 2 network cards.  If you should chose the extra Linux box way, don't use IPTables - they're far too confusing to look at, especially when going through 300+ odd rules for different services and what not.  I suggest instead, looking at a IPTables frontend, like [Shorewall]("http://www.shorewall.org/").  I use it at home, and I find it FAR superior to using\sifting through IPTables manuals and setting them up.  Actually, again, if you choose a Linux box, you don't actually HAVE to run Ubuntu on that if you don't want to - there are a number of Linux Distributions that are geared towards running firewall duties - there are quite a few around:

[LIST]
[*]Endian Firewall
[*]pfSense
[*]m0n0wall
[*]Smoothwall
[*]IPCop
[*]Mandriva MultiNetwork Firewall
[/LIST]

Using one of them, would of course alleviate the need for running Shorewall on a Ubuntu box, as this distros do all that and more + a nice web GUI.
2. Yes, webmin is good.  No, I don't know a lot about how to use it.  Jump in the deep end and use the console :p.
3. Yep, SQUID and DansGuardian are fine for web proxying and filtering duties - they also have the abilities to both run transparently, eliminating the need for client-side configuration.
4. You're probably better off running client side AntiVirus\AntiSpyware applications - that is, unless you want to fork out the $$$ for a Client\Server based AV\AS application, like Symantec AntiVirus.  Then again, you can install ClamAV (a Linux based AV application; doesn't do AS though) and have it connect to the C$ share of every client computer at a certain time and run a scan, however, I'm not sure how effective that'd be :confused: .
5. Yep, you can do all that in Linux too - with free applications.  There are a few Symantec Ghost clones in Linux, PartImage is one of them, however, there are more.  In terms of keeping your Windows Clients updated, your best bet is to just use Windows Update, that is, unless you want to run a Windows Server with WSUS (Windows Server Update Services) to minimize bandwidth usage by Clients downloading Windows Updates.
6. OK, that can all be done with SAMBA 3.x and a few Local Policies on the Windows machines - I suggest you read the SAMBA 3.x documentation, it'll answer most, if not all of your questions there.  And for Local Policies, fire up 'gpedit.msc' on the Windows XP clients, and have a sift through what you can play with - you'll have to set them on all your clients though, that is, again, unless you want to also setup a Windows Server with Active Directory :).
7. There are a few Network based backup programs - Bacula comes to mind, when I think of Network Backups and Linux.  I spoke about hardware backups in the previous post though - read above :).
8. You can do either, SSH is simpler to setup, however, a VPN could be more useful.  If you want to go the VPN route, I suggest looking up PoPToP, which is a PPTP VPN Server, and also OpenVPN, which is a TLS\SSL based VPN Server.  I use OpenVPN at home, and it's just great.  SSH though could be useful, especially if you wanted to have X access too - as you can tunnel VNC\XDMCP over SSH (as well as other things) and also, it interoperates with FreeNX too.  Read up on all of those for a better understanding :).
9. SAMBA 3.x again - this time, you're looking for making it a Primary Domain Controller.  That is covered in the Ubuntu Wiki as well as the SAMBA 3.x documentation.
10. E-Mail servers are not something I'm very used to on Windows or Linux, however, read the docs for Postfix, sendmail and QMail, and I'm sure you'll get the gist of things.  For WebMail access, look up SquirrelMail.  By the way, all E-Mail servers on Linux that I've come across are IMAP only - they don't serve E-Mail via POP3.
11. That's quite a large question - you're looking for DHCP, DNS and WINS servers.  DHCP can be done on the Server you'll be getting, and, because of the Network Topology that I suggested above, that's pretty much the only place you can get it going.  DNS can, and should, be done on the Server too and WINS can be on the Server as well.  WINS serving is done via SAMBA 3.x too. :) Ah it's a small world isn't it :) .

I think that's it.  I hope that you find all the information above useful.  Happy reading\learning\setting up.

---

### Post by Crashmaxx on 2007-01-21
Sorry to post such a mess of questions, but I've been thinking about this for a while now and had come upon a lot of questions. I needed to, at a minimum, write them all down.

So after some more thinking, here is the setup I am considering.

First the cable modem, which then the firewall is plugged into. This firewall is the one I'm looking at:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1527514&Sku=N100-2044](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1527514&Sku=N100-2044)
I think it should be a good and easy to use firewall and should function as a router, and should be able to be used as a VPN with remote access. It isn't as configurable as a linux box, but should be easier for my boss and coworkers to mess with, if needed.

Then having two network switches at least and the server plugged into it. These switches:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2537759&Sku=L75-1002](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2537759&Sku=L75-1002)
Which are a good price and should allow most of the primary jacks be on one, and most of the redundant ones be on the other, and I have an old 16 port t-hub for any others in non-critical locations. They are about a sixth the cost of one 48 port switch, and I don't think that we will have enough load nor does our hardware support gigabyte devices, so forget them.

And then the server will be this:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1960249&Sku=V133-6603](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1960249&Sku=V133-6603)
And it will also plug into the firewall, but I am thinking I should have no problem setting up the firewall to redirect all LAN traffic to the server so it can access the squid proxy server seamlessly and therefore have all the web traffic checked by dansguardian to block anything suspicious I can. Maybe like all executables not on a white list, just to start.

So the physical network will look something like this:
Cable
^
Firewall
^
^<Switches <LAN
^
^<Server

If that makes any sense.

And on the server, I will run:
Squid (proxy server)
DansGuardian (content filter for Squid)
Apache (just for running Squid)
Samba (to server files and act as primary domain controller)
Webmin (so someone other then myself can administrate it decently)
ClamAV (to at least check stored files)

Any help configuring any of these would be great. Some I've used, some I haven't, but none of them have a gotten setup properly.

And I'd still be happy to see any solutions for the other things mentioned prior. Maybe some of these things are windows server only things, or need expensive software, but I could swear I'd heard of all of these things being done in some way before.

And thanks for the help so far genesis. Anything look bad with the hardware I selected, or anything wrong with the logic behind the setup so far?

---

### Post by genesis[OFT] on 2007-01-21
Nope, that sounds good so far.  I'll be happy to help once you've got all the equipment you need and the base softwares installed :).

---

### Post by Crashmaxx on 2007-01-23
I had my boss order the hardware yesterday. Got a nicer server then I was planning on, this beast:
[http://www.tigerdirect.com/applications/searchtools/item-Details.asp?EdpNo=2224192&sku=C122-3508](http://www.tigerdirect.com/applications/searchtools/item-Details.asp?EdpNo=2224192&sku=C122-3508)

And we went with almost all gigabit network devices, though I'm not sure it will make much of a difference. I'll start installing everything later this week, hopefully. But I have a few more questions.

What kernal will work best for this AMD chip? I'll be using Dapper Server LAMP install, probably the i386 to start. Is the k7 kernal the best for this? Does it support the dual core?

I am guessing the hot-swap RAID 5 will be a seperate chip or something like that. Do I need to do anything special for it, or should ubuntu just see it as a single drive? And will SATA cause me any headaches?

I've deceided that I probably want to have a main shared folder with all the common files and important work that all the users can access, then possibly, a folder withen that for each user that only each user can access, and an additional shared folder that anyone on the LAN can see, even if they are just a customer or other non-employee.

But how do I configure samba to do this for me? I have only used it in user mode before and it was poor at best. If you try to map a drive windows won't mount it on boot, you have to enable it and put in a username and password. How can I authenticate each user automatically when the log-in to XP and have XP mount the drive with the folders they have access to inside it, to their My Documents folder? And anyone not "in the system" that gets on the LAN, can only see the public folder and nothing else? Reading through the documentation for samba, it appears it can do it, but the config file is confusing at best.

Samba is probably my biggest issue right now, I want the files to be seemlessly accessed and easy to manage, but that need to still be kept secure. I wish I could use encripted keys like ssh, but I don't think I can do anything like that.

---

### Post by Mike'sHardLinux on 2007-01-24
> **Crashmaxx said:**
> I am guessing the hot-swap RAID 5 will be a seperate chip or something like that. Do I need to do anything special for it, or should ubuntu just see it as a single drive? And will SATA cause me any headaches?

Looking at the asus website info on that motherboard, it doesn't mention supporting RAID5. I'd bet you will be setting up software RAID with that server, as I doubt it is a true hardware RAID controller. You set this up during the install. So, Ubuntu will see each individual drive, and you set up the RAID manually.


> **Crashmaxx said:**
> 
But how do I configure samba to do this for me? I have only used it in user mode before and it was poor at best. If you try to map a drive windows won't mount it on boot, you have to enable it and put in a username and password. How can I authenticate each user automatically when the log-in to XP and have XP mount the drive with the folders they have access to inside it, to their My Documents folder? And anyone not "in the system" that gets on the LAN, can only see the public folder and nothing else? Reading through the documentation for samba, it appears it can do it, but the config file is confusing at best. 

In windows xp, when you put in the user name and password, you have the option to save the information. If you check that box, the user should not have to authenticate manually any more, ever again. In windows 2000, I use a script that "logs-in" for the user, and it runs from the startup menu. I am sure there are other ways to handle this, but either way, it's pretty easy.

You can map drives to folders in both win xp and 2000. You can do it through the explorer (tools --> map network drive ), or you can make a script with the "net use" command. Again, it's easy.

> **Crashmaxx said:**
> I've deceided that I probably want to have a main shared folder with all the common files and important work that all the users can access, then possibly, a folder withen that for each user that only each user can access, and an additional shared folder that anyone on the LAN can see, even if they are just a customer or other non-employee.

How about separate folders for the public folder, and non-public folders? That is an easier way to do things, especially on the Samba side of things. Having the non-public folders inside the public folders would be harder to do, and less efficient.

---

### Post by bpmorris on 2007-01-24
Hi Guys,

I am a month old Ubuntu user as well, so I thought I should start contributing to the greater good by adding a small piece to the puzzle you have. For remote I would even consider a web access facility like [www.logmein.com](www.logmein.com) for your XP machines, its free and extremely easy to use. That way either yourself or other users can remote control their own workstation directly through a web browser and have the same experience as being in the office... I know this isn’t a "linux" solution but I have found it very effective for remote access.... just a thought.

---

### Post by Crashmaxx on 2007-02-01
So the server finally came in. And it doesn't have a hardware RAID, as suspected. And the nvidia RAID was junk, so I disabled it and used the Linux RAID and LVM. It was a pain, because I didn't quite know what I was doing and RAID 5 only makes things worse.

So now, I got RAID 5, LVM, and the LAMP server installed. I setup ssh with an RSA key, and forwarded the port. I gave the server a static LAN IP and used DynDNS.org to get the WAN IP. And I have samba installed, but now I am stuck with configuring samba.

I just don't know how to set it up for what I want. I wanted to make another LV for the shared files, but couldn't figure out how to do that. Then I want to have at least a public folder that anyone on the LAN can access and write to without any password or anything, like a normal shared XP folder. And for everyone else, have just a directory of folders with different permissions for different users, but I want it to be seemless at the client end, and based on the XP accounts. Or anything similar.

Can anyone help with samba? I have read the samba HOW-TO and docs but they just aren't clear. Do I need user authentication or share or what? Do I need a PDC, or LDAP, or some kind of active directory? I can't even figure out how to get it setup like a normal XP share that anyone can read or write for the time being.

---

### Post by Crashmaxx on 2007-02-06
I am still having trouble here. I have a few things working fine. I have the server on a static internal ip and am using dyndns.org to allow a static URL. I have ssh forwarded and encrypted with a RSA key, and got webmin running, and it is only accessible internally or with an ssh tunnel. And RAID is all cool and running fine. All that is great.

But I could only get samba configured with a basic public share folder. I need help, its config file makes no sense to me. I just want a way to allow the employees access to it without anything on their part. But have anyone not an employee only get access to the public folder. And I may want one share that is read-only for almost everyone. Sounds simple, but I don't know what I need.

For my samba shares, I would like them to be on a separate LV, and if that volume could be mapped as a network drive for employees, that would be great.

But postfix has just been killing me. I tried to follow this guide:
[http://www.howtoforge.com/virtual_postfix_mysql_quota_courier](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier)
After giving up on this one:
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

And I have a non working mail system and no clue what is going on with it. I think I am in over my head with this. What do I need for a basic mail setup that will just allow employees to email each other within the LAN, using IMAP? It needs to work with outlook, and I don't know how tasks and stuff for outlook are, but they should be mailed or linked of something.

Do I just need postfix and courier-imap? What do I need to change from their defaults? What do I need to do special for LAN only? Domain names are totally confusing me. I don't think I have a FQDN, unless my dyndns.org one is it, but does it have the server name at the front?

I pretty lost here, and have been trying this for days. Is there an easier way to do this? I heard about qmailtoaster, which is suppose to use a bunch of scripts to do it for you, but it is rpm based distros only. Anything easy like this for deb?

Thanks.

---

### Post by Brazen on 2007-02-07
This thread makes my head hurt :(

---

### Post by kooch1221 on 2007-02-07
I was recently in the same situation as you are now and used Ubuntu to setup most of the items you have listed. If I have to do it all over again I may go this route.

[http://www.clarkconnect.com/](http://www.clarkconnect.com/)

I did a mock-up server using this software and its ease of implementation and user interface was impressive.

---

### Post by Crashmaxx on 2007-02-07
I finally got postfix and everything using the first guide. Turned out, that postfix-mysql wasn't installed and apt-get wouldn't tell me because the other packages were more wrong.

So that seems to be all good now. But I still could use some help with advanced samba config.

---

### Post by Uthalin on 2007-02-07
You can try reading the SAMBA configuration part of this HOWTO.

[http://www.howtoforge.com/samba_setup_ubuntu_5.10_p4](http://www.howtoforge.com/samba_setup_ubuntu_5.10_p4)

It seems like it covers what you want to do with SAMBA.  It walks you through configuring User based sharing of home directories on the server as well as a public shared folder.  It also suppourts acting as a PDC in a Windows network if you want to go down that route.

---

### Post by awreneau on 2007-04-11
Crashmaxx,

I'm starting something up for an office that is in no way going to connect to our LAN short of a 10,000 fiber run and I just dont see MGMT springing for that.  Sounds like youve been down the road I'm about to travel.

Is all well now?

---

