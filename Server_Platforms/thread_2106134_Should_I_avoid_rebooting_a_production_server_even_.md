---
title: "Should I avoid rebooting a production server even if **system restart required**?"
date: 2013-01-18
forum: Server Platforms
---

### Post by mli111 on 2013-01-18
This is a basic question nevertheless it's very important for me so I hope someone with due experience and some patience can sort me out =)

**BACKGROUND**

I have a ubuntu 12.04 LTS server that is in production (hosting web sites for clients). It's a basic LAMP stack + ISPconfig and webmin.

I'm in the beginning of starting up my own business and I believe I have managed to cover a lot of rookie-mistakes which means that I have had to reinstall the server on more than one occassion :(

**Q: SHOULD I REBOOT THE SERVER WHEN I SEE THE MESSAGE **SYSTEM RESTART REQUIRED** ?**

At the first sight this seems like a rethoric question... well, why not restart? But unfortunately I have had bad experience with the server freezing after a reboot and there seem to be some consensus on the net that you should NEVER restart a production server unless absolutely necessary!

Well - a message "system restart required" would seem to make it "necessary"? Or not?!

(I have right now configured so only security updates are installed automatically - I don't install any other updates -- which also seems to be in line with consensus that you should leave a "production server" alone as much as possible).

Looking forward to some "heads up" on this issue!

Kindly,
Mikael  -> beginning of learning how to administer Linux server
Sweden

---

### Post by Grenage on 2013-01-18
I will generally restart a server after updates, and don't install updates until such time as it can be restarted.

---

### Post by mli111 on 2013-01-18
Well, the main question (as I see it) is the perceived "RISK" vs "BENEFIT" of restaring a production server.

So, what's the "risk" of restarting a server that has "only" installed security updates?

And what's the benefits of:

a) restart
b) not restarting

This is what I got so far.

BENEFITS NOT RESTARTING

* The server will continue to work (me and my clients are happy)

BENEFITS OF RESTARTING

* Security updates will be implemented?
* Killing "dud processes" that eats at the cpu / internal memory?

..but I'm an absolute n00b in this water so I'd really like to hear what the more experienced server admins think about this?

Cheers,
Mikael

---

### Post by Grenage on 2013-01-18
As far as I'm aware, while security updates may fix weaknesses, the old version isn't necessarily replaced in memory, and could still be running.

I'm sure I'll be corrected if that's not the case. ;)

---

### Post by mörgæs on 2013-01-18
You should have a development / toy server running an identical environment. On this one you install the updates and reboot as necessary.

This server could be running on some old left-over hardware, as there is not much load.

When you have seen that it works, you apply the same procedure to the production server. 

In general problems due to a reboot are very rare, in fact I reboot my production (Windows) servers once in a while to prevent problems. The risk due to running old software with security holes is much worse.

---

### Post by darkod on 2013-01-18
My experience is limited so i might be wrong, but here is how I understand that message (I get it on my home server too).

The security updates got installed automatically as you configured it, but in order for the process to fully finish and be applied, a restart is needed. So, in fact, I think the updates are not fully applied until you do so.

If that is correct, then leaving the server without a reboot indefinitely makes your setting to install security updates obsolete. It's like they are not being done at all.

I can't see another reason why a linux server would ask you to reboot except after installing some security updates like you told it to do.

---

### Post by craigp84 on 2013-01-18
> **mli111 said:**
> there seem to be some consensus on the net that you should NEVER restart a production server unless absolutely necessary!


I'd confirm the credentials of anyone offering this advice. I'd be explicit and query how many years experience they have as a sys admin and what is the nature of their experience. E.g. are they a production sysadmin for a fortune 500 company for 10+ years or are they running a home server for friends for which no money exchanges hands.

The problem is it's easy to give advice, but you need proven techniques in your situation - where clients are paying for services you have a much greater responsibility.

Most experienced SysAdmins will warn you away from a situation where you are dependant on your host's not being rebooted - because ultimately you can't control when they will next crash!

The ideal situation is to not treat your servers as special - not to care if you need to reboot one during the day. To get to this situation you need to be absolutely confident in your architecture that there will be 0 client impact (because workload will be taken by other servers which are online).

That ideal situation's quite hard to get to, especially if you're just starting a new business! It's a lot of expense to have duplicate servers / network equipment etc.

> 
I have right now configured so only security updates are installed automatically - I don't install any other updates

That's a sensible approach.

To a large extent it depends on your budget. Since you are starting a company i'm going to assume a budget of 0 - on the logic that even if you have a small budget, there are better things to spend it on (such as advertising) for a new company than to spend on computers.

Assuming 0 budget, 1 server, you'll need to adopt a scheduled maintenance period. It might be weekly or fortnightly, but your SLA with your clients should give you a period, say early hours of Sunday morning, where you can opt to take your server offline for some maintenance tasks (e.g. replace a faulty hard disk, reboot to install some patches).

Make sure you know how to roll-back a patch that's installed. If you find a problem has been introduced, you want to be able to immediately roll it back instead of waiting for upstream to issue a fix you can roll forward to.

Here's a cheap technique for handling the rollback requirement,  it's what's called the split mirror upgrade. With this model we assume your host boots from a RAID 1 array. Before any patches are applied, you split the RAID 1 mirror. That is, you take one drive offline (you can do this while the system is running). Then you apply your patches. Then you reboot from your 1 upgraded drive (the raid array is still operating in degraded mode). Then you run your test suite (which is likely just a collection of scripts which speak to each of your services in turn, checking their responses are accurate (e.g. correct web page contents presented) and measuring their response times) to verify every service is working within normal boundaries - i.e. no service is down, and none are performing poorly. At this point you can then re-enable the disk mirroring, restoring your RAID functionality.

If during the procedure you found a problem, then you would reboot from the other disk (the one which was removed from the RAID array before the patches were applied).

This technique has considerations, e.g. how long to do you want to be running with only 1 disk - what if it dies during your upgrade process?

I'd recommend using free resources to maximise your chances. E.g. setup an exact copy of your system in a virtual machine (inc. multiple virtual hard disks for your RAID array etc.)

Hope this helps

---

### Post by sandyd on 2013-01-18
> **mli111 said:**
> This is a basic question nevertheless it's very important for me so I hope someone with due experience and some patience can sort me out =)

**BACKGROUND**

I have a ubuntu 12.04 LTS server that is in production (hosting web sites for clients). It's a basic LAMP stack + ISPconfig and webmin.

I'm in the beginning of starting up my own business and I believe I have managed to cover a lot of rookie-mistakes which means that I have had to reinstall the server on more than one occassion :(

**Q: SHOULD I REBOOT THE SERVER WHEN I SEE THE MESSAGE **SYSTEM RESTART REQUIRED** ?**

At the first sight this seems like a rethoric question... well, why not restart? But unfortunately I have had bad experience with the server freezing after a reboot and there seem to be some consensus on the net that you should NEVER restart a production server unless absolutely necessary!

Well - a message "system restart required" would seem to make it "necessary"? Or not?!

(I have right now configured so only security updates are installed automatically - I don't install any other updates -- which also seems to be in line with consensus that you should leave a "production server" alone as much as possible).

Looking forward to some "heads up" on this issue!

Kindly,
Mikael  -> beginning of learning how to administer Linux server
Sweden
If you are operating a production server, KSplice is one of the tools that datacenters use to apply updates without restarting.
That being, you should have a development server to test the updates on before installing them on the production server.

btw, even though it says for Ubuntu Desktop, the title is a bit misleading... [http://www.ksplice.com/uptrack/using#command-line](http://www.ksplice.com/uptrack/using#command-line)

---

### Post by tgalati4 on 2013-01-18
Any time you perform updates (and that may only be once per year!) you need to plan some time to fix services that get broken by updates.

Some updates fix small things (timezones, spelling errors, icon artwork) other updates fix big things (kernel security holes, file system data handling).  The problem is that you don't know exactly how these updates will affect your system.

The fixes to services after an update may be simple (like simply restarting apache or mysql) or complex (calling tech support about a proprietary package that won't start).  A server is all about uptime.  If you restart it and leave your customers without service, you will hear about it.  Of course if your server gets hit by a security hole that you didn't patch, then you will hear about that as well.

The same could be said about electrical power, flooding, etc.  How well prepared are your servers from those outside disasters?  What is written into your service agreements about downtime?

"System Restart" is normally flagged whenever there is a kernel-related service that got updated.  Simple application patches don't need restarts because the updated libraries will get loaded as soon as you start the application.  But for a server, every service that is running becomes a "system" service because it is being used by outside clients.  

Watch your traffic logs and pick a time when server access is low then contact your clients about the "system updates" and when they will occur.  Then prepare yourself to spend some time to test your services after the update so that you don't get surprises.  A simple test is to simply bring up each of your client's homepage (in a testing script for instance)--preferably from an outside machine.  That would give you 90% confidence that your server came up correctly.  Also check the boot logs and become familiar with each error/condition shows up in dmesg/syslog.  Any new messages could mean either a hardware problem or a kernel update that is not happy with your hardware.  

In some cases, you can boot off of an older (and working) kernel if a kernel patch breaks your system.  That would give you time to submit a bug report or investigate the problem.

90% of the time it's no big deal.  But 10% of the time you will be pulling your hair out.  So it helps to have hair.

---

