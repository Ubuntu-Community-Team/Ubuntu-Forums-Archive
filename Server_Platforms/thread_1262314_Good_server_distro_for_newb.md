---
title: "Good server distro for newb?"
date: 2009-09-09
forum: Server Platforms
---

### Post by RFXCasey on 2009-09-09
What is a good distro to run your first dedicated server on? I have set one up using Debian but I am wondering if I shouldn't use something more like FreeBDS or similar.

---

### Post by Bachstelze on 2009-09-09
Just run whatever you're the most comfortable with. Debian is a perfectly valid choice.

---

### Post by nandemonai on 2009-09-09
I find BSD a little less forgiving than it's Linux cousins. Debian / Ubuntu Server is perfect for novices and experts alike in my opinion.

Whatever floats your boat essentially ;)

---

### Post by Cardale on 2009-09-09
Your on the ubuntu forums man.  Cmon Ubuntu Server is great.  It is like Debian except more polish.

---

### Post by RFXCasey on 2009-09-09
But I have read that Ubuntu does not get updated the same as debian or tested for that matter which can make it a less secure. Of the two which is them most secure?

---

### Post by Sporkman on 2009-09-10
I've been running my website on Ubuntu Server for a couple of years & haven't have any problems.

It is a fast, stable, and secure server platform.

---

### Post by mysteriousdarren on 2009-09-10
I was wondering what would be the easiest way to start a server for a server newb? I have been with Ubuntu desktop for several years, but would like to try something new. Any tips or hints?

---

### Post by jondkent on 2009-09-10
> **mysteriousdarren said:**
> I was wondering what would be the easiest way to start a server for a server newb? I have been with Ubuntu desktop for several years, but would like to try something new. Any tips or hints?

Depends upon what you want to use the server for, web server, file serving, database etc?  If you're limited hardware wise you'd be supprised how much server type software can run from a 'desktop' distro.

---

### Post by mysteriousdarren on 2009-09-10
I was wondering what the best platform is for a server newb? I have been using Ubuntu exclusively for several years and would like to try something new. Any hint or tips?

---

### Post by mysteriousdarren on 2009-09-10
Sorry about the multi post. I was going to use it for file sharing, and web server. What did u say about the desktop distro options?

---

### Post by mysteriousdarren on 2009-09-10
I was gonna maybe stream a music collection using Samba....

---

### Post by wojox on 2009-09-10
> **RFXCasey said:**
> But I have read that Ubuntu does not get updated the same as debian or tested for that matter which can make it a less secure. Of the two which is them most secure?

I started with 8.10 and upgraded to 9.04. Run it as a web server. The only thing that makes a sever less secure is the way the sysadmin configures it.

---

### Post by mysteriousdarren on 2009-09-10
So get a server disc, and go by that way? Or use the desktop version somehow?

---

### Post by wojox on 2009-09-10
> **mysteriousdarren said:**
> So get a server disc, and go by that way? Or use the desktop version somehow?

Get the server disc, but remember it's all terminal. Install LAMP when it asks you to, and ssh as well.

---

### Post by mysteriousdarren on 2009-09-10
anything else? that is important? I dont want to fly into this project blind.

---

### Post by wojox on 2009-09-10
> **mysteriousdarren said:**
> anything else? that is important? I dont want to fly into this project blind.

Yeah if there's an option for samba install that as well. I find it easier to do this on install than adding to it after.

---

### Post by jondkent on 2009-09-10
That did confuse me :P

OK, what I saying is that you can run apache, samba, NFS, mySQL etc on a desktop, assuming it is for light use.  Done this alot in the past, and I still run NFS on my main desktop so I can mount certain directories on my laptop.  You'll fine all the server software in the standard repos.

For light web use, say if you where learning apache and/or web programming, running apache or anyother web server is fine, and just a *apt-get install httpd* away from being done for a simple setup.

Pretty much dito mySQL, or anyother database, though I would warn that you'd only do this for learning/playing with, unless you have a good backup routine in place already, the database is not too large and you have the spare power to do this as well as run desktop.

At the end of the say a desktop is really just a server with X on it (just don't tell the server guys that ;) ).  Its all *NIX so it just depends upon what your hardware limitations are.

Hope that helps,

Jon

---

### Post by RFXCasey on 2009-09-10
Thanks, that's good information.:-k

---

### Post by fela on 2009-09-10
I think Debian is a great choice, so long as you chose Lenny and not any of the others.

Stable (very);
Fast;
Linux.

That's all you need to know :)

Although you might want to compile a custom kernel more geared towards servers, for example have an 100HZ timer and no kernel preemption, to get maximum throughput at the cost of higher latencies.

---

### Post by RFXCasey on 2009-09-12
So I am in possession of a Dell poweredge 2400 server. It has 2 733Mhz processors, ECC memory and 4 20Gig scsi hard drives. Would I be better off using a 2.4Ghz desktop machine instead cause I have one of those laying around too.

---

### Post by Wim Sturkenboom on 2009-09-12
I would use the poweredge as
1)
it provides a different challenge.
2)
what will you do with it if you don't use it?

---

