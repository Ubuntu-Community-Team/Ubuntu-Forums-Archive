---
title: "Viruses on XP in Virtualbox"
date: 2008-08-15
forum: Security
---

### Post by Unanimated on 2008-08-15
EDIT: OKAY! At first, it started as a question, and now I'm actually doing it. Here's the link to my blog about it:

[http://winxpvirusexperiment.blogspot.com/]("http://winxpvirusexperiment.blogspot.com/")

For some weird reason, I've lately wanted to make another XP installation in Virtualbox just so I can completely infect it with viruses, spyware, adware, and any form of malware there is, just to see how bad it can really get. Before I start, will doing this make Ubuntu vulnerable or put one of the Windows viruses in Ubuntu, which I know would just take up space, but I'm just wondering. Just wanted to know before I started. I'm basically just wondering if this will make Ubuntu or any of my hardware insecure. I have Guest Additions installed, so I don't think anything will happen to my actual hardware, but again, I'm just wondering.

---

### Post by Sealbhach on 2008-08-15
One thing to consider is that it might turn your computer into a spambot so that it sends out spam onto the internet. I would hate to think I am inflicting spam on others and it might harm your internet connection speed as well.


.

---

### Post by Unanimated on 2008-08-15
Would that make Ubuntu do that or Windows? I'm planning on deleting Windows after I do this.

---

### Post by Unanimated on 2008-08-16
bump

---

### Post by adieb on 2008-08-16
Bumping after 8 hours??? Because of WINXP Virus experiments? Crazy... ;-)

Actually I don´t think it would harm your Ubuntu Installation. I think there are no ways known to get through the virtual environment with viruses/rootkits/whatever.

But if your XP-VM starts to send out spam, then it is your computer actually. It uses your inet-connection. And if you do this over NAT, it uses your Ubuntu-IP.

So what you should do is monitoring your eth-device, for example with tcpdump.

Easier could be setting up a Host-Interface Networking solution for your VM.
I works with tap-devices (new instances of your existing eth0), those would be easier to monitor.

Good Luck

PS: I´d like to read about the results of your experiments!

---

### Post by Unanimated on 2008-08-16
Would it only send spam out if the VM is "turned on?"

---

### Post by Sephoroth on 2008-08-16
I don't see how any computer could spam when turned off :wink:.  Hence, shutting down a VM should do the same.

---

### Post by Unanimated on 2008-08-16
Oh. Hehe. Stupid question. :P

Alright, I'll start a blog listing my results.

---

### Post by Chayak on 2008-08-16
My job is doing security and malware research.  My setup normally involves a linux host running VMware Workstation (for snapshots) on an isolated dirty network.  I run two VMs generally, one is the target system that has Sysinternals Procmon, Procexp, and wireshark running.  The second VM has fakeDNS, Apache, and wireshark running.

Fake DNS will capture any DNS requests pointed at it and send it to a specific IP.  That doesn't help when the callback IP of the malware is coded to use IP directly and not DNS.

Autoruns is also a handy sysinternal tool to have as you can check after malware is executed and from time to time you'll find new entries that it's written for persistance.

More often than not now I see samples that have built in rootkit functionality to hide themselves.  That means you'll have to boot off of a forensics CD to see what and where it writes to.

Before you run it do static analysis... (ie examine the file without execution)
First thing you do is run strings on the binary and look to see if it's packed.  If it is packed then you may get lucky and it'll tell you what packer was used.  I see UPX a lot but only on the amature level samples.  If it is packed/armoured against reverse engineering you'll need to learn how to use ollydbg.  It'd take forever to explain how as you need a strong background in assembly language but basically it involves stepping through a program in a debugger until it unpacks itself in memory (rarely that simple) you dump the contents of memory for it and create a new executable though there's many steps along the way that involves correcting the execution pointer and rebuilding stuff around it to get it to run properly.

Once that's done you can examine the real strings of the binary and that will normally tell you a bit about what it does.

More advanced static analysis invovles disecting it with IDA Pro but unless you know assembly you'll waste your time.

The other step is called dynamic analysis, ie running the malware on the target machine.  You set up procmon (filter out everything but file writes, file changes, and registry changes to keep it simple for starters) procexp, and wireshark.  Have them all running and ready and then take a snapshot of the VM before running the executable.  This should give you the files it writes out, registry entries to make itself persistant and any network traffic when it tries to call home.

That's kind of a very rough overview but it should give you a general idea of what to do.  I would disconnect your network from the internet before doing this though.  If your IP pops up and they get a list of processes the botherder isn't going to be happy that your trying to reverse engineer his implant and you might find yourself subject to attacks.

Oh and I've never had a cross infection to my VM host.  I've had samples turn nasty and eat the VM after detecting it, but while there is proof of concept code for escaping from a VM to the host.  I haven't seen a real world example.  That's what snapshots are for, to recover to a clean state and just in case some code trashes your image.

---

### Post by Unanimated on 2008-08-16
Okay, I started a blog.

[http://winxpvirusexperiment.blogspot.com/]("http://winxpvirusexperiment.blogspot.com/")

---

### Post by Sealbhach on 2008-08-16
> **Unanimated said:**
> Okay, I started a blog.

[http://winxpvirusexperiment.blogspot.com/]("http://winxpvirusexperiment.blogspot.com/")

Bookmarked. Looking forward to seeing what happens.


.

---

### Post by Unanimated on 2008-08-17
Just made a new post on the blog.

---

