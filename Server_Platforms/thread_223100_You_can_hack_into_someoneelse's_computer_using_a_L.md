---
title: "You can hack into someoneelse's computer using a Live CD?"
date: 2006-07-25
forum: Server Platforms
---

### Post by H.E. Pennypacker on 2006-07-25
I recently started thinking about this.  You could hack into someone's computer by starting that computer, loading a Linux Live CD, auto-mounting partitions, and stealing the owner's files only using a Live CD.  Am I wrong and am I missing something?

I know you can already do this, but I am checking to make sure with those who know more than me.  That means I am not an expert and I could be wrong! No arrogance on my behalf.

Don't get me wrong, I am not trying to break into anyone's computer.  I am just worried that someone could steal my laptop, and peer into my files using a Live CD.  I am not sure what's stopping anyone.

Has this been talked about before here or anywhere else?  I would have no idea, and if it already has been, let me know of a link, and I'll read up on this.  I want to know how to protect myself.  It's a disturbing thought.

---

### Post by GuitarHero on 2006-07-25
The likelihood that a laptop-stealing hacker uses ubuntu is probably slim to none.

---

### Post by aysiu on 2006-07-25
If someone has physical access to your computer, she also has access to all of your files.

---

### Post by daniel of sarnia on 2006-07-25
It will work unless the drive is encrypted, I'd also like to note that booting a disk and mounting the hard drive really is not much of any hack.

---

### Post by Iandefor on 2006-07-25
> **daniel of sarnia said:**
> It will work unless the drive is encrypted, I'd also like to note that booting a disk and mounting the hard drive really is not much of any hack. If it were, I'd be the most amazing hacker in the world!

:-D

---

### Post by VirtuAlex on 2006-07-25
> BSD, Lunix, Debian and Mandrake are all versions of an illegal hacker operation system, invented by a Soviet computer hacker named Linyos Torovoltos, before the Russians lost the Cold War.
[http://adequacy.org/public/stories/2001.12.2.42056.2147.html]("http://adequacy.org/public/stories/2001.12.2.42056.2147.html")

---

### Post by Iandefor on 2006-07-25
> **VirtuAlex said:**
> [http://adequacy.org/public/stories/2001.12.2.42056.2147.html](http://adequacy.org/public/stories/2001.12.2.42056.2147.html) That website always makes me laugh.

---

### Post by dasunst3r on 2006-07-25
If you would like to keep this from happening, you should do this:
1. Go into your BIOS
2. Set the boot order so that your hard drive boots first
3. Make it so that people have to enter a password in order to change your BIOS settings.

---

### Post by aysiu on 2006-07-25
What's to then stop someone from physically removing the hard drive and putting it in another computer?

If someone has physical access to your computer, she has access to your files.

---

### Post by VirtuAlex on 2006-07-25
But seriously you can employ three basic ways to handle this problem:
1. Protect your computer from unauthorized physical access;
2. Protect sensitive data by encrypting it;
3. Just ignore it and make plenty of backups in case data gets physically stolen or corrupted.
Or any combination of above.

---

### Post by KaeseEs on 2006-07-25
If your computer is physically compromised, all data therein should be assumed equally compromised.  You're best bet for a laptop is to have a three-layer security system:

1)  Keep an eye on it.

2)  Lock it with a good lock.

3)  Go into the BIOS and set a boot password.


Note that #2 and #3, while prudent, are defeatable; thus you ought to do both, but really worry about #1.

---

### Post by wifiabc on 2006-07-26
Encrypt your data especially if it's in your laptop.

---

### Post by RavenOfOdin on 2006-07-26
I don't consider that real cracking. . .but meh.

To each their own.

---

### Post by H.E. Pennypacker on 2006-07-27
Thanks for clearing this up.  I may have to buy a lock, and encrypt all partitions.

> The likelihood that a laptop-stealing hacker uses ubuntu is probably slim to none.

Well, just about any Linux distro could do the same (auto-mount other partitions).

[QUOTE=aysiu]If someone has physical access to your computer, she also has access to all of your files.[/QUOTE]

aysiu, you said you're a guy, right?  I am never sure whether you're male or female, not that it is really relevant.  Here's why though...I am absolutely amazed (short of shocked) you regularly say something like "if someone...she also..." meaning you always use "she."  That is unbelievably out of norm for most people.  Technically, neither she or he can be used, but most people use "he" and it is used so often that it has almost become part of the language.  

I bring this up because of how strange it is you regularly use "she" instead of "he."  Using "she" also is out of place.  It jumps at me.

> mounting the hard drive really is not much of any hack.

True, hacking is something entirely different, but in the most common sense, people understand hacking to be gaining any unauthorized access to someoneelse's computer.

---

### Post by Raistlin355 on 2006-07-27
Are you kidding?!?!   I do that all the time at work when Windoze messes up and I have to rescue files!!

---

### Post by MrHorus on 2006-07-28
Booting off a CD is an old trick tbh.

You could set the system up only to boot from the HD and disallow floppy and CD-ROM booting and protect the BIOS but a determined cracker will open the case and reset the BIOS jumper and of course, if they are opening the case they may as well just take the HD out and put it in an external caddy.

Moral of the story?

Do your best to make sure the laptop is secure and if it has critical data on it, encrypt it.

---

### Post by Randomskk on 2006-07-28
> **H.E. Pennypacker said:**
> 
aysiu, you said you're a guy, right?  I am never sure whether you're male or female, not that it is really relevant.  Here's why though...I am absolutely amazed (short of shocked) you regularly say something like "if someone...she also..." meaning you always use "she."  That is unbelievably out of norm for most people.  Technically, neither she or he can be used, but most people use "he" and it is used so often that it has almost become part of the language.  

I bring this up because of how strange it is you regularly use "she" instead of "he."  Using "she" also is out of place.  It jumps at me.
'She' is used quite a lot in technical things, it seems.
I've seen it used a lot talking about people who are, most of the time, male :P

As far as getting into your computer, as aysiu said, if someone has physical access to your machine, they've got your data (and everything else on the machine - such as passwords you may use for other things as well).

Most people have a blank password for the Administrator on a Windows machine, or (with Ubuntu) no root password protecting the Recovery Mode - in both cases, it's easy (press F8 and load safe mode with windows, or Recovery Mode with Ubuntu) to boot the system to a state where you can access any of the data. Live CDs work as well, and so does taking the drive.

Encryption is only as secure as the key - how will you store this? If it's on a USB key, it's pretty likely your laptop will be stolen with the key, or someone could get the key separately.

Or what if you've left your laptop powered on, look away for a second and someone takes it? The encryption is useless, as it's already powered on and anyone can view your files.

Realistically, if someone has physical access, they have your data - so the best way to secure a laptop would be to prevent someone from getting their hands on it in the first place.
Of course, encryption helps, as do things like BIOS and Administrator passwords, and most common thieves are (currently) more interested in the hardware than the data anyway.
With identity theft on the rise, though, more and more thieves may also look through your data.

---

### Post by LordHunter317 on 2006-07-28
> **MrHorus said:**
> You could set the system up only to boot from the HD and disallow floppy and CD-ROM booting and protect the BIOSMany bioses don't let you do that anymore, even without a password.  Even if you disable floopy and CD-ROM from the normal boot order, they still show up if you select the 'Boot Menu' at startup.  Virtually all Dells are this way, for example.

Plus, many BIOSes have fairly well known backdoor passwords on them.

> **RandomSKK]'She' is used quite a lot in technical things, it seems.[/quote]Well, you use the femal pronoun to refer to a non-specific object, not people.

So if I'm talking about a computer, or a car, or a tank, I use 'she'.  If I'm talking about a person, I use 'he'.

Those are the "traditional" rules.  These days, the lines are more blurred said:**
> Most people have a blank password for the Administrator on a Windows machine, or (with Ubuntu) no root password protecting the Recovery Mode - in both cases, it's easy (press F8 and load safe mode with windows, or Recovery Mode with Ubuntu)Actually, Windows lets you disable the recovery console but it's still fairly easy to get around.  You just have to boot with a Linux CD and adjust the registry entry.  Just FYI.

> Encryption is only as secure as the key - how will you store this?Unelss you're not password protecting the key, it ought to be safe even on the disk.  Unless you're using a bad password, of course.

> as do things like BIOS and Administrator passwords,Not a bit, in the case of theft.

> and most common thieves are (currently) more interested in the hardware than the data anyway.Not anymore.

---

### Post by Randomskk on 2006-07-31
> **LordHunter317 said:**
> 
Actually, Windows lets you disable the recovery console but it's still fairly easy to get around.  You just have to boot with a Linux CD and adjust the registry entry.  Just FYI.

Does it let you disable safe mode? 
Then again, XP Pro asks you for an admin password during installation, so even safe mode still asks for a password here. XP Home, however, doesn't.
> 
Unelss you're not password protecting the key, it ought to be safe even on the disk.  Unless you're using a bad password, of course.

Not entirely relevant, but can passphrase-protected keys be brute forced (easily)? If I'm entering the passphrase for a key on this machine, and I get it wrong, the error message is instant, and it doesn't seem to be taking huge amounts of time - thus would brute forcing be plausible?

> 
Not a bit, in the case of theft.

But it could help if someone just had physical access, while the computer was still on-site.

> Not anymore.
[QUOTE=Randomskk]With identity theft on the rise, though, more and more thieves may also look through your data.[/QUOTE]
I'd still imagine many common thieves would be after the hardware itself?
Obviously smarter criminals, and other people who want the data more than the hardware would be after the data, but if a common crook saw your laptop lying around, is it really more likely than not he'd spend time looking through data, as opposed to just selling the thing on?

---

### Post by Josue Davis on 2006-08-05
well, you what, i think breaking into someone's system has a lot of definitions to give, i never heard of breaking into someones computer in that way, in fact i never heard somebody saying: hey look at me i broke into someones computer in a totally 100%!!!!!. But i know a lot of ways to shutdown remote computers and to ge them offline and back up online, there is people who says they did hacked into people's pc, but im pretty sure they have been fooled, using command prompt and figuring out computer's IP is something that could hardly take you inside someone's system, but is quiet close to that. I know that you can establish a direct connection to a remote computer anywhere in the world, or/and universe, jk!.I am totaly against the ilegal use of computer against people's system [-X, but there is a nice and not ilegal way, to find out how much you know about hacking, get 2 computers, and by using one try to break into the other one, is not like you are gonna go to jail for that. That's a pretty nice way to find out how to break into systems, but trust me, hacking into people's system is such a bad idea, even know it sounds fun and everything, but you could get infected with their viruses and a whole bunch of other risks that you may not wanna take. let's say is just as risky as overcloking your CPU. bye!!!.:D

---

### Post by dont42panic on 2006-08-05
SysAdmins use live distros for troubleshooting and recovery 
all the time. At work, we keep Knoppix around for many uses.
Out of the box, it can be set up in a matter of minutes, without any commitment to permanent storage(HDD) to do all of the following:

1: web server
2: mail server
3: DNS server
4: router, with firewalling
5: file server
6: DHCP server
7: desktop operations
8: file recovery
9: virus scanning


Because open source is mutually respectful of all operating environments, it is rare that the kernel cannot recognize the local filesystem on machine it is booted on.

And, since the partition/s are being mounted as data and not actually run, then viewing the data is simple.
 
Unless troubleshooting, your BIOS should always be password protected. Add to that, the HD should be the only boot device.
And, once booted, desktop access should only be accessed via  explicitly created user accounts with tough passwords.
Also a nice feature to have your case locked as well.


Actually, when I'm say working on a friends/colleagues machine, and have determined that the HD would be best served by being completely wiped and reinstalled(which was often the case back in the Win95/98/ME days. WinXP is a dramatic improvement), I usually slave the drive in one of my desktops and then mount, copy, and format from there.

---

