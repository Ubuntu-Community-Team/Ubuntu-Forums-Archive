---
title: "Server is hanging from time to time"
date: 2008-02-21
forum: Server Platforms
---

### Post by trymbill on 2008-02-21
I'm using Ubuntu 6.06 server on a Virtual Server 2005 from M$ ...

... I know this is maybe not the right place to post this question, but I just wanted to check if someone here knew how to troubleshoot this.

My problem is, that my server (A Windows 2003 SBS Server) hangs for maybe 1 and a half minute possibly once every 2 hours, something like that.  I don't understand why, but this is also effecting my Virtual Server.  So basically, everything on my server stops for over a minute a few times a day.

I don't know how to troubleshoot this.  I don't know where to begin and have no clue how I can possibly solve this problem or if it is even possible.

If some one here knows how I can do this, please let me know! :)

Sincerely,
Magnus

---

### Post by 0x845fed on 2008-02-21
If you can open a terminal, run the top command.

---

### Post by igknighted on 2008-02-22
> **0x845fed said:**
> If you can open a terminal, run the top command.

I didn't think Windows Server 2003 had that command :confused:

---

### Post by lespaul_rentals on 2008-02-22
I don't work with Microsoft server software, so I'm not sure how to help you.  I would be willing to bet that it's either a Microsoft issue or a virtualization issue (maybe an IRQ conflict or something).  Just curious, if you are running Ubuntu Server 6.06 as a virtual machine and using it to deliver services, why not just switch over completely?  I use Ubuntu Server 6.06 on my home server (I'm obviously very casual, while it sounds like you are enterprise level) and it never hangs or has issues like that.

---

### Post by jonabyte on 2008-02-22
You may want to check what other services are running on Windows, or is the computer downloading av updates every hour?

It could be a number of things, you may want to check what "manage your server" shows as being installed like a file/print server, asp server, etc.

Unfortunately, I have to admin a windows server at my work :( :lolflag:

---

### Post by trymbill on 2008-02-26
> **lespaul_rentals said:**
> I don't work with Microsoft server software, so I'm not sure how to help you.  I would be willing to bet that it's either a Microsoft issue or a virtualization issue (maybe an IRQ conflict or something).  Just curious, if you are running Ubuntu Server 6.06 as a virtual machine and using it to deliver services, why not just switch over completely?  I use Ubuntu Server 6.06 on my home server (I'm obviously very casual, while it sounds like you are enterprise level) and it never hangs or has issues like that.

I'm running M$ Server because I've got to use Exchange ... if Ubuntu had anything close to as nice and simple as Exchange, I would change over to only Ubuntu.  For now, I'm running Ubuntu for Apache2, PHP5, MySQL and some file sharing.

I'm going to check "top" on my Ubuntu machine and I also have installed "Big Brother" software on my Windows server ... I should be able to see what's going on on my server :-)

Thanks for your replies!

---

### Post by astrotech226 on 2008-02-26
> **trymbill said:**
> I'm running M$ Server because I've got to use Exchange ... if Ubuntu had anything close to as nice and simple as Exchange, I would change over to only Ubuntu.  For now, I'm running Ubuntu for Apache2, PHP5, MySQL and some file sharing.

I'm going to check "top" on my Ubuntu machine and I also have installed "Big Brother" software on my Windows server ... I should be able to see what's going on on my server :-)

Thanks for your replies!

Are you seriously running Exchange and a virtual machine on the same server?  Is the Exchange server also the domain controller?  If so, it's no wonder it's locking up.  You are probably running on the verge of your resource limits and I'll bet the Windows machine is doing some swapping to disk.  How many CPU's do you have and how much RAM?

---

### Post by igknighted on 2008-02-26
> **trymbill said:**
> I'm running M$ Server because I've got to use Exchange ... if Ubuntu had anything close to as nice and simple as Exchange, I would change over to only Ubuntu.  For now, I'm running Ubuntu for Apache2, PHP5, MySQL and some file sharing.

I'm going to check "top" on my Ubuntu machine and I also have installed "Big Brother" software on my Windows server ... I should be able to see what's going on on my server :-)

Thanks for your replies!

Look at Zimbra and Scalix.  They are similarly featured and are much easier to admin than exchange.  If you want a drop-in linux alternative to exchange, look at postpath.  Consider it an exchange server on linux, as windows can't tell the difference between the two.

Exchange (and the similar linux email apps I mentioned) pretty much require a dedicated server.  Trying to run a VM or anything else on that server will probably cause the lockups you mention.

---

### Post by jonabyte on 2008-02-26
> **trymbill said:**
> 

I'm going to check "top" on my Ubuntu machine and I also have installed "Big Brother" software on my Windows server ... I should be able to see what's going on on my server :-)


Running exchange AND vm is most likely why your server hangs...

---

### Post by tubezninja on 2008-02-26
> **igknighted said:**
> I didn't think Windows Server 2003 had that command :confused:

Windows doesn't have top, but it does have [the task manager]("http://support.microsoft.com/kb/323527"), which will give the information he needs.

To the OP: try opening task manager (use the link above for instructions, but you probably already know how to do this) and see what tasks are taking up CPU resources.  As other have stated, you probably have too much going on in one piece of hardware.

---

### Post by dca on 2008-02-26
Wow, I would rather VM Exchange Server into a RHEL box so that way it's easier to b/u...

---

