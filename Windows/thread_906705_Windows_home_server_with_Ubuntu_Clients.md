---
title: "Windows home server with Ubuntu Clients"
date: 2008-08-31
forum: Windows
---

### Post by asmith3006 on 2008-08-31
Hi,

How does windows home server react with ubuntu clients and mac clients? Does it use normal windows shares or is it a bit weird?

I'm going to be buying a home server for the family and WHS looks like a good option. I'm the only one who uses linux and mac, the rest use windows so the advantages are obvious from their perspective, just need to be sure I'll be able to use it.

Obviously the automated backups wont work, but can I access shares and printers and so on?

Thanks.

Andrew.

---

### Post by tuskenraider on 2009-01-01
anyone had any luck with the WHS OS? i just aquired a hp mediasmart ex475... anyone got any input???


tusken

---

### Post by jrusso2 on 2009-01-02
The different part is the backup has a Windows client.  So it won't do the auto matic backups with Linux or OS X.

---

### Post by Toady00 on 2009-01-07
I'm new to Linux but I've been running a WHS I built myseld for over a year now. As far as the server itself, it is hands down the best software MS has ever put out. It has been running non stop for over a year and never had even a hiccup. As far as Linux and WHS together, I'm having a hard time accessing my shares from my Ubuntu Laptop. I have a post up asking for help but so far I still can't access it.

---

### Post by donkyhotay on 2009-01-07
Isn't this sort of backwards? I mean windows is (essentially) the de-facto standard for desktop clients while linux controls the server market.

---

### Post by jrusso2 on 2009-01-07
Actually Windows makes are pretty good server for small business and home use.  I only worry about Windows server in a large environment where Linux, or even Free BSD or Open Solaris would be a better choice.  Especially for database.

---

### Post by donkyhotay on 2009-01-08
> **jrusso2 said:**
> Actually Windows makes are pretty good server for small business and home use.  I only worry about Windows server in a large environment where Linux, or even Free BSD or Open Solaris would be a better choice.  Especially for database.

I know many people use windows for their server, just like many people use linux for their desktop. It's just goes against the cliche on both sides though.

---

### Post by WIVO_Riley on 2009-01-09
> **Toady00 said:**
> I'm new to Linux but I've been running a WHS I built myseld for over a year now. As far as the server itself, it is hands down the best software MS has ever put out. It has been running non stop for over a year and never had even a hiccup. As far as Linux and WHS together, I'm having a hard time accessing my shares from my Ubuntu Laptop. I have a post up asking for help but so far I still can't access it.

Want to REALLY like WHS?  Get perfect disk 2008WHS version- kicked it into overdrive.  Son streams movies through his xbox with it- too cool!


AND- I've got the same problems- with connecting to the shares (or any windows shares on this distro.

---

### Post by woodp on 2009-01-09
> **asmith3006 said:**
> Obviously the automated backups wont work, but can I access shares and printers and so on?

You're right about the automatic backups not working, and as far as printers are concerned, Ubuntu includes a Printer setup program. That just leaves the shares.

First, you need to create a mount point in your Ubuntu file system. The command from Terminal is:

```
sudo mkdir /mnt/music
```
Then you need to tell Ubuntu where the network share is and mount it:

```
sudo mount -t cifs -o username=**xxx**,password=**yyy** //192.168.1.**zzz**/Music /mnt/music
```
*Obviously, you need to put the values appropriate to your setup in xxx, yyy and zzz.*

Now go to Place | Computer | Filesystem | mnt | Music and you should see the WHS files.

Repeat as required for the photo, video and any other directory you want to share.

Good luck!

---

### Post by WIVO_Riley on 2009-01-09
> **woodp said:**
> You're right about the automatic backups not working, and as far as printers are concerned, Ubuntu includes a Printer setup program. That just leaves the shares.

First, you need to create a mount point in your Ubuntu file system. The command from Terminal is:

```
sudo mkdir /mnt/music
```
Then you need to tell Ubuntu where the network share is and mount it:

```
sudo mount -t cifs -o username=**xxx**,password=**yyy** //192.168.1.**zzz**/Music /mnt/music
```
*Obviously, you need to put the values appropriate to your setup in xxx, yyy and zzz.*

Now go to Place | Computer | Filesystem | mnt | Music and you should see the WHS files.

Repeat as required for the photo, video and any other directory you want to share.

Good luck!

EUREKA!!!!!!!!!!!!!!!  SUCCESS!!!!!!!!!!!

I've been driving myself nuckin futs trying to get this figured out.  Thanks so very very much!!!!!  

Any idea on how to connect to the PRINTER that I have hooked up to WHS and used as a network printer?  Very Much Appreciated!!!

---

### Post by WIVO_Riley on 2009-01-10
OK, restarted and it went away.

Once I did:

sudo mount -t cifs -o username=xxx,password=xxx //192.168.1.x/Music /mnt/music

it came back, but I'd REALLY like to make those files show up every time I restart.

AND I still can't get the printer figured out (it's connected to WHS)

Any ideas?

---

### Post by Xizorbg on 2009-01-15
If you go to printers under "system" on the ubuntu, you should be able to browse to the printer and set it as default.  Make sure you are sharing the printer on the WHS system.  

Here is a guide to that:
[http://www.wegotserved.co.uk/wiki/index.php?title=Sharing_a_Printer_on_your_WHS](http://www.wegotserved.co.uk/wiki/index.php?title=Sharing_a_Printer_on_your_WHS)

Good luck!

Now if someone can figure out how to backup my /home partition onto my WHS!!!

---

