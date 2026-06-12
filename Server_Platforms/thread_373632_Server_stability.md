---
title: "Server stability"
date: 2007-03-01
forum: Server Platforms
---

### Post by dignick on 2007-03-01
I'm probably going to build a home server using ubuntu server any time.  I'm a student and will be leaving home for uni soon, and so when I'm gone I need to be sure that this server will not fail, unless of course due to hardware failure.
So my question is this; how can I be sure that either the OS or some software installed will not stop functioning correctly mid-term?  Should I just disable all non-security repositories?  Which distribution version should I use in the first place?
What about longer term - will a distribution upgrade break everything?  And when will I need to perform one?
Thanks.

---

### Post by solar george on 2007-03-01
If reliability is important I would use debian stable, most of the programs are old but it doesn't break.

---

### Post by MJN on 2007-03-01
I've had a Kubuntu server (5.10 then 6.06) up for a year now and never had it fail (aside from disk failure but that's obviously distro-independent) so from personal experience I'd recommend it.

As long as you maintain SSH access then you should be able to everything remotely that you can do sat in front of the machine.

Mathew

---

### Post by Mr. C. on 2007-03-01
You cannot ensure that software "will not stop functioning correctly".  Don't fall into the trap of believing that you can prevent failure.   All hardware fails - and pretty much most software fails in some way. Its just a matter of time.

Instead, *plan* for failure, and work on how you will solve the problems remotely when the troubles *do* occur.   Are you going to have a sufficiently-sized UPS to ensure the server stays up when the power goes out, or the housecleaning unplugs the system for need of a power source for a vacuum?  If your file system becomes corrupted due to a power failure, who's going to reboot or fix the file system for you?  Will you remotely upgrade the kernel or other critical software when exploits are found and updates are made available?  Or will you just ignore those?

If you really want reliability, consider a hosted solution, or prepare to spend a fair amount on the necessary hardware/solutions to allow remote access down to the BIOS level.

---

### Post by dignick on 2007-03-03
Thanks for your help.
I've messed with debian a bit.  It seems Ubuntu server would be easier to set up and use for some additional functions I intend to set up.  I may be wrong so I might give it another try.

Hosted is not an option, a primary use of this server is to share an internet connection and act as a firewall.  I understand I cannot prevent failure, and from time to time I will have to perform maintenance or upgrades to the system.  What I'm looking for is reliability in the 10 weeks I will be away from home each term.  If say a hard drive fails, my dad can replace the hard drive and run a script to restore a backup, but he is not literate with linux.

In general, would it be safe to leave this computer without updates for 10 weeks max?

---

### Post by Mr. C. on 2007-03-03
Define "safe".

---

### Post by dignick on 2007-03-03
:) 

Locally stored data will not be accessible.  Windows computers behind the firewall will not be vulnerable.

---

### Post by Mr. C. on 2007-03-03
Ok, then that's up to your ability to configure and secure your firewall and the system, including performing risk analysis on patch or update requirements.

Best of luck,
MrC

---

### Post by MJN on 2007-03-03
In your situation security has got to be considered more important than stability hence you'd be mad to not perform updates. Besides which, I think you're worrying too much!

Mathew

---

