---
title: "Setting up my first server-Need Direction"
date: 2012-07-19
forum: Server Platforms
---

### Post by KevinPreuss on 2012-07-19
I have a few questions first, but let me explain my needs first.

Easy stuff
1)  I need a computer/server to act as a file server for 8 employees and myself.
2)  I need to set up different folders for different projects and set up different permissions for the employees.
3)  Time tracking
4)  4TB in raid 5

Harder stuff
4)  VPN to the server
5)  Zero down time


The questions:
1)  Hardware: Do I need server hardware or can I use a desktop hardware
2)  Raid 5-Preferred??  SATA drives??
3)  I like using a GUI because I am not good at the command line, can I use regular Ubuntu or do I have to use server Ubuntu?
4)  I do not have an IP address, do I need to purchase one to VPN to the server/computer?
5)  Should I use Windows SBS or Ubuntu?

Years ago, I started working towards an associates in IT.  So I am not a total noob but I also haven't kept up with things like I should have.  Now I have my own studio, employees, my first kid on the way in another week, and I sleep about 4 hours a night.  So I know I haven't been diligent about my research.  But if this is something I can do when I take time off (about 2 1/2 weeks) when my baby girl gets here, I would like to tackle setting up my server.  Whether it be Ubuntu, Ubuntu server, or some sort of Windows server.

As a last resort, I would farm this out if that is the consensus on the forums.

Kevin

---

### Post by sffvba[e0rt on 2012-07-23
*Thread moved to **Server Platforms**.*


404

---

### Post by mw4jet on 2012-07-23
I used a how-to from Kevin Elwood, he has a PDF download about a step by step multi-purpose headless server setup. I have learned a lot from that guy. I really like Webmin, and Putty, both used in the how-to. 
 
[http://woodel.com/](http://woodel.com/)
 
I think he is mentioned in this forum and others, I have Ubuntu server 12.04, but have used it for the last few releases and although it differs slightly from the Debian in his how-to it works.

---

### Post by gordintoronto on 2012-07-23
Random jottings...

1. Use Ubuntu Desktop. Ubuntu Server would give slightly better performance for running a high-volume web site, but that's not what you want to do.

2. RAID has a learning curve!

3. 4 TB? If your business produces videos, that makes sense.

4. Desktop hardware will do, especially if you use RAID. Note that RAID will not protect you if someone deletes "this important file," so you still need to do frequent backup.

5. Every computer on a LAN has an IP address. You don't need to purchase one. You might want to Google "ubuntu static IP address"

---

### Post by kgatan on 2012-07-24
You should check out Zentyal ([www.zentyal.com]("http://www.zentyal.com")). Its based on Ubuntu and comes pre configured as a small business server.
I think it has all you need and also an easy web interface for configurations.

For hardware i would not use a desktop machine. I guess the machine will be running 24/7 and since you use it in a business environment you dont want any downtime.

If you wont run disk demanding applications on the server your bottleneck will be your network so sata drives should suffice. Id recommend to buy drives designed to run 24/7 like WD black and AV-GP series.

As other have written, raid improves performance and decreases down time, but its not a backup.
You really need to have an offsite backup.

A dedicated IP for VPN is not necessary. You can use a service like dyndns instead.

Windows SBS gives you alot for your money with Active Directory, Exchange and Sharepoint.
Id recommend it to anyone if you have a budget that allows it.

---

### Post by a2j on 2012-07-24
> **KevinPreuss said:**
> 


The questions:
1)  Hardware: Do I need server hardware or can I use a desktop hardware
2)  Raid 5-Preferred??  SATA drives??
3)  I like using a GUI because I am not good at the command line, can I use regular Ubuntu or do I have to use server Ubuntu?
4)  I do not have an IP address, do I need to purchase one to VPN to the server/computer?
5)  Should I use Windows SBS or Ubuntu?



I would not use desktop hardware. Workstation or server only. Or something that was designed to run 24/7.
For RAID5 I would use smaller drives. If 4TB RAID is a must, use RAID6.
Install Ubuntu (or Debian) server edition and use Webmin for GUI administration.
ISP usually provides you with a WAN IP address. For internal IP addresses use a dhcp  server.
Based on description of your needs, I do not see a single reason to pay for windows sBS. :)

---

### Post by gordintoronto on 2012-07-25
Oops, I meant "4 TB?"

A typical business document might be 50 KB. A million of them is, um, 50 GB.

Media, mostly video, is what requires lots of space.

---

### Post by Mr.Dee on 2012-07-25
Congrats on the baby!
 
It sounds like you might have a difficult time to get this all up and running in the time frame you are looking for.  I don't have too much experience with building a network for a business but I have worked as a network engineer and do a lot of stuff at home.  I'm basing this on your question "4) I do not have an IP address, do I need to purchase one to VPN to the server/computer?" This question is asking what is at the heart of networking,  which is understanding the flow/path.  

If you have internet access you must have an IP address yourself.  If you have a static IP that will save you a little work.  If you do not have a static IP you can look into dyndns.
 
Do not dispair you are asking the right questions.
 
Most importantly is that you sleep, lol. coffee != sleep

---

### Post by saphil on 2012-07-26
Security note:
Webmin is a place where you are using the root password on a publicly available machine.  If you set up your server so you can only reach webmin from a LAN computer and not the internet, you are showing wisdom.
Another way to show wisdom is to find an unused high port and set the default listening port of your webmin instance to that.  
It is trivially easy to write an attack script that looks for the webmin port 10000 open.  Then a concerted attack on your server can commence.

Comfort note:
You can use the server distribution and install a GUI on it at installation time, if you choose your own packages, rather than just hitting the next button.  You can also install a GUI anytime after you get your install working.

-Wolf

---

### Post by CharlesA on 2012-07-26
> **a2j said:**
> I would not use desktop hardware. Workstation or server only. Or something that was designed to run 24/7.


If it is for a company, this is the best thing to do. If it is for home, you can get by with running on desktop hardware, but I would not try it at a business (even tho the place I work tries to get away with doing so, but not for servers)

---

### Post by kevinthecomputerguy on 2012-07-27
@CharlesA, i feel your pain, my work does the same thing.

@Saphil, you are making some wild assumptions about peoples network setups, and about their allowed webmin accounts, the same could be said about ssh.

@m4wjet, thanks man

@OP, I favor raid 10 above all, with backups (backup your raid as if it wasn't raided)

-Kev

---

### Post by CharlesA on 2012-07-27
> **kevinthecomputerguy said:**
> @CharlesA, i feel your pain, my work does the same thing.

It gets annoying at times, but what can you do?

I backup my RAID array daily, to an external drive. That way, if the drives go out, I lose at most, 1 day of data.

---

### Post by saphil on 2012-07-27
> **kevinthecomputerguy said:**
> 
@Saphil, you are making some wild assumptions about peoples network setups, and about their allowed webmin accounts, the same could be said about ssh.

-Kev
I am making a wild assumption that script-kiddies pound the webmin default port and you are right, the same could be said about ssh.  If you put your ssh port in a high unused port, you won't get any worries from people beating on your actual ssh port at all.  The scripts tend to pound expected ports.  Nothing wrong with not being there, is there?

---

### Post by CharlesA on 2012-07-27
Use rate limiting or fail2ban and you will be fine.

---

