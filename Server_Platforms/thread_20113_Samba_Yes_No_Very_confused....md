---
title: "Samba? Yes? No? Very confused..."
date: 2005-03-15
forum: Server Platforms
---

### Post by ElricOfGrans on 2005-03-15
G'Day,

At work, we've just started migrating from an XP set up to Ubuntu. As a Debian user at home, this is quite welcome - and this seems quite a refreshing Distro, especially the speed and ease of installation! The trouble is that networks are not my area, and I'm trying to set up a server through which mail, printing and file-sharing is handled. I'm fairly sure I can work out the mail myself, but the file/print sharing has me a little confused. I've read around a little, and I think I get the gist of the idea, but I also think I may be barking up the wrong tree ;) To make things worse, the network shall remain a mixture of Ubuntu, XP and OS X even after the migration.

I *think* what I need to do is configure a Samba server on the (Ubuntu) server system, and establish the basic share rules here (and only have the daemons running off this system), then configure sharing rules (for files and printers) on each separate system. The bit that makes me think I'm getting this wrong is that it seems like you set up sharing when you configure the server, yet obviously the server cannot specify the shares of other systems... right? This then leads me to thinking that I need to set up a server on each system, but that is obviously NOT the solution. Logic dictates that I configure a Samba server on the server system, then do some sort of client configuration on the Ubuntu, XP and OS X systems, and it's just I misunderstood something somewhere.

If anyone could help this programmer pass as a network manager for this one week, it would be really appreciated ;) All I should need is a basic run-down on what needs to be done, and I should then be able to use HOWTOs to actually follow this process.

I'll also apologise in advance if anything funny happens when I post (double-post or something): my home connection has been extremely unreliable recently.

---

### Post by BoBoB on 2005-03-15
Basically you need to run a file server on each pc you want to share files on.

In Windows it's easy as file sharing pretty much is pre-configured, but on Linux you need to run something like Samba or NFS Server. (Samba is more easy in a mixed Win/Linux environment).

On Linux you need to specify each folder you want to share in the Samba configuration with the proper rights.

As far as I know it is not possible to create remote shares on other pc's..

There are thousands of Samba howto's out there, so a search on Google should return a lot of useful info.

---

### Post by ElricOfGrans on 2005-03-16
Thanks for that! I would never have thought you really DID have to configure a server on each system. It took a little bit of fiddling about, but it's now mostly sorted out. I just need to make a few tweaks here and there, but the worst of it is out of the way now. If anything, Samba ended up being easier than the mail server has been so far ;)

---

### Post by BoBoB on 2005-03-16
[QUOTE=ElricOfGrans]If anything, Samba ended up being easier than the mail server has been so far ;)[/QUOTE]

I must agree to that. It took me several weeks to get my postfix+courier+mysql setup fixed...

---

### Post by brousch on 2005-03-16
It is not clear to me what you are trying to set up.

In most businesses, you will have a main server, providing shares to the network. These shares are located on the server. The workstations connect to the server shares and store their data there, for ease of backup and sharing. In this case, only the main server needs samba server setup.

If you are trying to setup a peer-to-peer network, where each workstation shares its **local** files, then each workstation would need its own samba server.

In a situation with more than 3 or 4 workstations, you would want a central server, and no workstation shares. This way you only need to backup 1 computer (the server), and everyone knows where to look for the files they need (all files are on the server).

In the case of printer sharing, where the printer is locally attached to a workstation, you would also need samba server setup on that workstation. Again, in an environment with many workstations it is better to put those printers directly on the network (or hooked up to a dediacted printer sharing server) for ease of sharing. If you are only doing sharing of locally-attached printers, that printer is unavailable if the workstation it is hooked to is shut down/rebooting/broken.

---

### Post by ElricOfGrans on 2005-03-17
It's only a small set-up: one pure-ubuntu system, one XP/ubuntu dual boot, and (currently) two OS X systems (one will be ubuntu eventually). It's more or less working now, though the printer is giving me a headache.

If I print a (cups) test page from the ubuntu system with the printer, it's fine. If I send a test page from the XP/ubuntu system, the output is messed up (it's printing the postscript file as if it were plain text, and so the output is all the PS gibberish (``IncludeResource: font Helveltica'', etc). The files I find in /var/spool/cups are identical for the test pages from both PCs, and likewise if I print the either file myself (from the command line with lp or lpr) I get the same output. Presumably the error is in my print command, but countless different commands have given the same output. Here's the section for the relevant infor from smb.conf as it currently stands:

[global]
(snip)
	printing = cups
	printcap name = cups
   	load printers = yes
(snip)

[printers]
	comment = All Printers
   	path = /var/spool/samba
   	browseable = no
   	printable = yes
	printing = cups
	printcap name = cups
   	public = yes
  	writable = no
   	create mode = 0700
	guest ok = Yes

[HPLaserJet6MP]
	comment = HP LaserJet 6MP
	path = /var/spool/samba
	printer name = LaserJet-6MP
	printable = yes
	printing = cups
	print command = lp -d %p -o raw %s; rm -f %s
	printer driver = HP LaserJet 6MP
	users = (snip)

I'm fairly sure I'm close (it prints, just not what I want it to), but am sure the problem lies in the print command.

EDIT: I've fiddled with things a little more, and am not so sure now. When I send a document, it creates two files in /var/spool/cups: a PDP-11 UNIX/RT ldp file named c(serial number) and a postscript file called d(serial number)-001. It seems to be printing the former when I want the latter.

---

### Post by brousch on 2005-03-18
Unfortunately (well, for you, but not for me), I have never run into a problem like this with printer sharing. Most of my printers are on the network, and the one I do have shared has always worked.

I just took a look at my smb.conf for that printer share and I see it is using lprng, not cups (redhat 7 server).

[FONT=Courier New][global]
printcap name = /etc/printcap
load printers = yes
printing = lprng[/FONT]


I guess you could install lprng and give it a try. Other than that, I am clueless.

---

### Post by Arto on 2005-03-18
[QUOTE=ElricOfGrans]It's only a small set-up: one pure-ubuntu system, one XP/ubuntu dual boot, and (currently) two OS X systems (one will be ubuntu eventually). It's more or less working now, though the printer is giving me a headache.[/QUOTE]

I'd recommend using NFS instead of Windows shares (= Samba) between Ubuntu and Mac OS X, as both are Unices. We've got a similar setup here and NFS seems to be somewhat more transparent and reliable than Windows sharing. Naturally you still need Samba for the Windows machines. Just my two cents.

---

### Post by brousch on 2005-03-18
It would be nice if Ubuntu could find network NFS shares as easily as it does Samba.

I agree NFS is better for *nix to *nix, but I cannot figure out how to get it to work easily. But I have not spent much time on it since Ubuntu has such nice Samba support.

---

### Post by garyng on 2005-03-18
I would say WebDAV if you don't have complex ACL requirement(or performance). Install Apache2 and  Mac/Window/linux can access it.

BTW, even printer sharing don't need samba, CUPS is fine as it speaks IPP.

---

