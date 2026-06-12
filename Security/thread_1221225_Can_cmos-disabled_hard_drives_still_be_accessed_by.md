---
title: "Can cmos-disabled hard drives still be accessed by malware?"
date: 2009-07-23
forum: Security
---

### Post by Ulysses_ on 2009-07-23
I was thinking of physically removing the hard drive of a computer and using the computer only with a liveCD, for security.    But is disabling the hard drive in the cmos just as secure?  Or does software exist that can still access the hard drive?

---

### Post by lisati on 2009-07-23
my guess is that as a basic measure, disabling a praticular device would help protect your system to a point, but wouldn't absolutely guarantee that someone/something seriously intent on doing mischief would be blocked.

---

### Post by estyles on 2009-07-23
> **Ulysses_ said:**
> I was thinking of physically removing the hard drive of a computer and using the computer only with a liveCD, for security. 

Talk about overkill...

---

### Post by Ulysses_ on 2009-07-23
> **estyles said:**
> Talk about overkill...

Everyone can and should do this, or the equivalent.  Antivirus, antispyware, antitrojan, anti-whatever software become obsolete. Even a firewall becomes non-essential. The endless security holes and spyware in microsoft windows and other 'reputable' software are not much of a worry any more: **you just power off and the baddies are gone**.  And they cannot access your private data because it's physically separate from your browser. That is, if the only hard drive is cmos-disabled or external, that you only connect at the end of a trusted session to save downloaded data, then it is impossible to get infected permanently.
Now if the cmos disable is equivalent to physically removing the hard drive, then you save buying an external enclosure, you'd just need a cheap flash drive for transfers to the usually disabled hard drive.

---

### Post by estyles on 2009-07-23
> **Ulysses_ said:**
> Everyone can and should do this, or the equivalent.  Antivirus, antispyware, antitrojan, anti-whatever software become obsolete. Even a firewall becomes non-essential. The endless security holes and spyware in microsoft windows and other 'reputable' software are not much of a worry any more: **you just power off and the baddies are gone**.  And they cannot access your private data because it's physically separate from your browser. That is, if the only hard drive is cmos-disabled or external, that you only connect at the end of a trusted session to save downloaded data, then it is impossible to get infected permanently.
Now if the cmos disable is equivalent to physically removing the hard drive, then you save buying an external enclosure, you'd just need a cheap flash drive for transfers to the usually disabled hard drive.

If you don't browse with your tin-foil hat on, it's all for naught.  They'll just download your brainwaves.

---

### Post by cdenley on 2009-07-23
You're better off using a guest session for everyday browsing stuff. Nothing which the guest user can write is permanent. You can still access your admin user if you want to install a new package or change a configuration.

Having your whole system non-persistent would not be practical, especially if you're using a livecd. It would be difficult to keep security updates current when you're running a CD. You could at least mount your root filesystem non-persistently, but then it's still a pain to make any permanent changes.

Just because the livecd can't write permanent changes doesn't mean it can't be compromised just as easily. Any malware would be removed after a reboot, but your sensitive data could have been stolen already.

---

### Post by Ulysses_ on 2009-07-23
> **estyles said:**
> If you don't browse with your tin-foil hat on, it's all for naught.  They'll just download your brainwaves.

No, what I'll do instead is go around hurling personal attacks on strangers on the internet as a passtime while ignoring technical issues presented (such as antivirus software becoming obsolete).  If you know the answer to the technical question, say it.  If not, gift us with your absence.

---

### Post by Ulysses_ on 2009-07-23
Cdenley, thanks for the input.  I don't see how your personal data can be stolen if it is not available to an infected computer.  Remember, you only enable the hard drive in a session that does not include internet access.

---

### Post by cdenley on 2009-07-23
> **Ulysses_ said:**
> Cdenley, thanks for the input.  I don't see how your personal data can be stolen if it is not available to an infected computer.  Remember, you only enable the hard drive in a session that does not include internet access.

Your browser saves sensitive data (passwords, cookies, etc). People often work with data which can be considered sensitive which would have to be accessible while the computer is running. What is the point in storing data on the hard drive if you can't access it? Wouldn't it be simpler to encrypt a partition, then mount it as needed?

---

### Post by tgalati4 on 2009-07-23
You need to shield your keyboard as well since keystrokes can be detected in your home's electrical grounding.

Your tinfoil hat should come down to your jawline since the jawbone can radiate brainwaves and act as an antenna for intruder microwaves.

---

### Post by cdenley on 2009-07-23
> **tgalati4 said:**
> You need to shield your keyboard as well since keystrokes can be detected in you home's electrical grounding.

That's PS/2 keyboards, not USB.

---

### Post by Whiffle on 2009-07-23
I think disabling in your bios would probably work.  But if you're really that worried about it, get something hot swappable.  Then you can just plug it in when you want your files.  

But if someone gets physical access to your computer, all bets are off.

I for one, see no reason to worry about it.

---

### Post by Ulysses_ on 2009-07-23
> **cdenley said:**
> Your browser saves sensitive data (passwords, cookies, etc).  But these I knowingly transmit to my destination, they're not private.  As long as I only visit just one trusted site in a session and then boot up, this private data cannot be stolen by hackers infecting the computer in subsequent sessions (or previous sessions).  > People often work with data which can be considered sensitive which would have to be accessible while the computer is running. What is the point in storing data on the hard drive if you can't access it?  You only access the hard drive in a trusted session we said. That's the idea.  Only untrusted sessions are without a hard disk.  > Wouldn't it be simpler to encrypt a partition, then mount it as needed?  And mount it during a trusted session only?  That's a thought.  Still have to boot up between sessions though.

More to the title of the topic, does anyone know where to look for software that can do this, if such software exists?

---

### Post by Ulysses_ on 2009-07-23
> **Whiffle said:**
> But if someone gets physical access to your computer, all bets are off.

I for one, see no reason to worry about it.  But surely, you have an antivirus and a firewall?  Everybody does.  Why is that?  Is it safer or simpler to have a firewall and an antivirus, than not connecting your hard disk to your computer in untrusted sessions?

---

### Post by cdenley on 2009-07-23
> **Ulysses_ said:**
> But surely, you have an antivirus and a firewall?  Everybody does.  Why is that?  Why is it safer than not connecting your hard disk to your computer in untrusted browsing sessions?

I doubt everyone using ubuntu has antivirus and a firewall. There is no known viruses which can infect a recent linux distribution. There are no services installed by default which need to be protected by a firewall. It is safer to isolate internet usage from the filesystem, just not practical. Nobody would want to reboot their computer in order to use the internet, then reboot again in order to access any of their files.

---

### Post by cdenley on 2009-07-23
> **Ulysses_ said:**
> 
More to the title of the topic, does anyone know where to look for software that can do this, if such software exists?

I think this would be within the realm of possibility, since motherboards allow the BIOS to be flashed with software. Assuming the motherboards don't allow configuration changes by software, the attacker would have to figure out how to flash the BIOS on your particular motherboard, then modify a BIOS ROM file to force your hard drive to be enabled, then they would probably have to figure out how to run their malicious BIOS flasher as root. Also, they would have to know you're running a livecd and that you have a drive physically connected but disabled in BIOS before they go through all this trouble. I don't even know of any software that can flash BIOS within linux, and I've never heard of a motherboard BIOS ROM being hacked.

---

### Post by Ulysses_ on 2009-07-23
> **cdenley said:**
> Nobody would want to reboot their computer in order to use the internet, then reboot again in order to access any of their files.  That's a valid point alright.  We're used to this way of using computers.  But if you consider most sites trusted, nothing changes, you still have your hard disk always enabled.  Only the really untrusted ones get the diskless treatment.  
If only booting up was faster.  What about a liveDVD holding a permanent hibernate image for faster bootup.

---

### Post by Ulysses_ on 2009-07-23
Or maybe two computers sharing the same display and simultaneously powered on and off: a diskless one for the internet, a normal one for all other use.  And a kvm switch to switch the display etc from one pc to the other.  And a physical ethernet switcher to disable the connection between the two, enabled only during a very trusted session.

---

### Post by Whiffle on 2009-07-23
> **Ulysses_ said:**
> But surely, you have an antivirus and a firewall?  Everybody does.  Why is that?  Is it safer or simpler to have a firewall and an antivirus, than not connecting your hard disk to your computer in untrusted sessions?

I have antivirus on my Windows install, because, well, it's Windows.  I haven't seen the need for it under Linux.  I have a firewall, which is built into my router.  I probably don't need it, but considering that i do run Windows occasionally, and so do friends/family, may as well have it.  

Is it safer or simpler to have a firewall and an antivirus, than unhooking my hard drive?   Of course its simpler, but its not *unsafe* either.

Is it as safe? Probably not.  

Is it unsafe? No.  

How do I know that?  Observation of the activities of my computer, and of how things generally go in the offline world.

But if I were really worried about people getting in over my network cable, I'd just unhook it.  If I think the internet is that risky, then its not worth using, there are other ways to do what I need to get done.  I have better things to do than jump through all the hoops that you say are absolutely necessary.

---

### Post by cdenley on 2009-07-24
> **Ulysses_ said:**
> That's a valid point alright.  We're used to this way of using computers.  But if you consider most sites trusted, nothing changes, you still have your hard disk always enabled.  Only the really untrusted ones get the diskless treatment.

What kind of untrusted sites do you visit that they require this level of paranoia? No sites should be trusted unless they are using a signed SSL certificate. The site can always be spoofed. Even with SSL, if the server is compromised, it couldn't be trusted.

---

### Post by scrooge_74 on 2009-07-24
> **tgalati4 said:**
> You need to shield your keyboard as well since keystrokes can be detected in your home's electrical grounding.

Your tinfoil hat should come down to your jawline since the jawbone can radiate brainwaves and act as an antenna for intruder microwaves.

Priceless!! :lolflag:

Also consider not using PCs at all , write everything down then memorize all and burn the papers.

Use real pidgeons to send your mail and use encripted messages

---

### Post by Ulysses_ on 2009-07-24
> No sites should be trusted unless they are using a signed SSL certificate  Cdenley, as you're beginning to understand it's not either ''trusted'' or ''not trusted'' but there are all shades of gray in between. So it is up to the user to judge if a site is dangerous and worth a boot-up, not for me to judge.    For me, many sites about suppressed news and activists are potentially dangerous because they are not by genuine researchers but fake.  One such site has allegedly downloaded child pornography to visitors' computers in order to frame selected targets.  You can live your life thinking that the flu vaccine is good for you, that Iraq is being liberated, and that Saddam had weapons of mass destruction.  Or you can open your eyes to what is really happening, which is a decay to global fascist dictatorship.  Firewalls are too complex to set up properly, and still ineffective against malicious sites.  Antivirus and other signature-based shields are always one step behind malware.  Finally the fabled perfection of linux that makes you feel happy without any security software at all is no more than a myth.

Many people are using liveCD's for security, and it turns out they are not only more secure, but also much FASTER, especially windows liveCD's like BartPE compared to persistent windows.  With some linux ones you can get even more peformance by loading your entire disk to memory using the toram cheatcode and have a very fast computer.  

Does anyone know if it would be difficult to implement the hibernate feature of windows on linux, and boot off a hibernate image in the CD/DVD to reduce boot-up time?

---

