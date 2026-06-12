---
title: "Ubuntu Server vs MS Server"
date: 2008-04-04
forum: Server Platforms
---

### Post by garfonzo on 2008-04-04
Hey there,

I am trying to figure out what would be best suited for my needs; Ubuntu Server or MS Server Enterprise 2003. First off, I get MS Server for free through my university, so cost is not an issue. 

Here are my needs/wants (this is for home use, 2-4 comps):
1. Have each comp in house (WinXP, Vista, Ubuntu) have their "My Documents" location mapped to the server's hard drive
2. Have a software RAID 1 (mirroring) on the server for data security and data loss prevention (ya, I do additional backups beyond just RAID)
3. Print server for all home comps
4. Fax server (somehow). Currently I remote client into a WinXP box and fax that way, so it isn't really "served" right now
5. Have my files accessible beyond my home LAN (at work/friends, etc.)
6. Stream my music library to locations beyond my home LAN (work/friends, etc.)
7. Have photos available beyond my home LAN (not really necessary, but cool none the less).
8. Have it able to download files so the main computers don't need to do that (torrent or just normal downloads)

So, which would better suite my needs in your opinion? Any thoughts as far as pros/cons to either Ubuntu or MS? I'll be running the server on a slower machine (P3, 933mhz, 448RAM, lotsa hard drive space) so I know that Ubuntu would be faster on this and it will be headless. I was thinking of Debian too, but I have no real reasoning as to why (seemed more 'mature' than Ubuntu).

I do have experience (by no means extensive) in the Linux environment with editing files, doing command line stuff so I'm not scared of doing everything with no GUI if that would be better. For some reason, having no GUI seems more fun, but it isn't important.

Long post, indeed, but I really appreciate any feedback!

Cheers,

Garfonzo
:)

---

### Post by garfonzo on 2008-04-04
Perhaps I should mention what I've got now.

On the machine mentioned above (P3, 933mhz) I just have WinXP sharing our printer. I've made a hard drive "shared" and we dump random files onto it. Weekly, WinXP will backup the entire "data" hard drive to a second one. No one has their "My Documents" mapped to any drive so I'm terrified of a hard drive crashing and losing valuable data (happened once, now I'm paranoid about backups).

Cheers

---

### Post by adamitj on 2008-04-04
Hello garfonzo! Let's ride a bit among the Ubuntu universe, presenting the benefits of using Ubuntu Server ;)

1. Have each comp in house (WinXP, Vista, Ubuntu) have their "My Documents" location mapped to the server's hard drive

You can do it easily by changing you "My Documents" location on your clients, it is possible on Windows by right-clicking this folder and changing it to a shared folder in Ubuntu main server, wich you had previously shared on samba.

2. Have a software RAID 1 (mirroring) on the server for data security and data loss prevention (ya, I do additional backups beyond just RAID)

Ok, Linux kernel offers support for many adaptec cards, and if you don't find the right driver, you can compile a new one by downloading driver on vendor's website.

Notice that backups on Linux are very simple, you can make a very nice backup shell script or using other packages as Bacula backup.

3. Print server for all home comps

Use CUPS, and a few configurations. This one is a little more complicated than Windows Server printer management, but is as so functional as Microsoft solution.

4. Have my files accessible beyond my home LAN (at work/friends, etc.)

Just share some folders using SAMBA!

5. Stream my music library to locations beyond my home LAN (work/friends, etc.)

Streamming like what? You'll ned to search if your purporsed streammings are avaliable on linux, but this subject is not my speciality.

6. Have photos available beyond my home LAN (not really necessary, but cool none the less).

I do not see any problem if you use a designed shared folder on server.

7. Have it able to download files so the main computers don't need to do that (torrent or just normal downloads)

Yes! Ubuntu does it very well. I think in a better way than Windows. But if you really want a graphical interface, just use Ubuntu Desktop version instead of a Server Version.

You have so far one good alternative to administrate your new Ubuntu server by installing the WebMin application, so you can handle every single parameter of OS by web connection. It is awesome!

---

### Post by garfonzo on 2008-04-04
Hey adamitj,

Thanks for the smoking fast reply. I kinda knew that posting such a topic in the Ubuntu forums would elicite many pro-Ubunut responses - which is cool! 

As far as data backup (RAID), I was thinking more of a software RAID since I don't have a RAID card and don't want to spend a dime on one. Instead of RAID, I was also thinking of RSYNC to do data backup.

How about doing faxing through Ubuntu? The soon-to-be-server tower has a fax modem which we use now and then. Is there a solution so that all computers would have access to faxing? Currently I just use remote desktop into the WinXP "server" and fax from within. 

Thanks again!

---

### Post by adamitj on 2008-04-05
Sure, you can do a software RAID using MDADM tool - wich one is too much better than any other type of software RAID options. The advantages of using mdadm is that you do not need two physical disks of same model and same capacity or vendor.

In other subject, the use of fax-modem on ubuntu runs out of my knowledge. But I think you can post a specific thread about it on this forum, and you will have a good answer ASAP.

Of course here you'll get more answers encouraging the use of Ubuntu, but really, depending on your specific needs, maybe MS Windows Server could be your best choice. Even I had to choice many times between Linux and MS Windows Server 2003 on our customers, and many times I choiced Windows too... however, I start from the premise that linux is better, faster and more reliable, but if it cannot handle all needs, finally Windows Server comes in place.

---

### Post by freebeer on 2008-04-06
I use both Windows Server 2003 and Ubuntu.  The Ubuntu server is generally more reliable, with far less crashes/lockups.  It's also marginally faster than my Windows box, despite having lower specs (but marginally, too).

I backup the Windows box to the Ubuntu box via rsync, then backup the ubuntu box via rsync to an off-site box.

I've never tried sharing files outside the network via Samba, so I don't know the issues there, but I do feel that the Ubuntu server will be a lot more secure than the Windows one if you're going to open it up to the interwebs.

I also don't know about the faxing thing.  I've never set up a dial-up modem on Ubuntu.  However, you may run into issues especially if you've got a so-called winmodem.  It's my understanding that these can be very difficult, if not impossible to get to work under Linux.  Blame the hardware manufacturer for that, though.

If you're familiar with Windows, and unfamiliar with Ubuntu (or any Linux), Ubuntu will be harder to set up because its so different from what you're used to.  BUT you will learn a lot about computers, networking, etc. that is translatable to both systems.  Linux just gives you more control out-of-the-box.

I suppose you can always try dual-booting and experiment in parallel.  :D

I hope that gives you some data points to consider.

---

### Post by adamitj on 2008-04-07
Very well done, freeber.

Altought I said "*but if it cannot handle all needs, finally Windows Server comes in place.*", I mean "*when one customer's applications get some linux incompatibilities, Windows Server comes in place*".

This means some backup softwares and/or a couple of custom applications from minor vendors.

---

