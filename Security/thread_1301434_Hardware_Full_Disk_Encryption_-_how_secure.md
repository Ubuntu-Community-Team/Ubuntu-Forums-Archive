---
title: "Hardware Full Disk Encryption - how secure?"
date: 2009-10-26
forum: Security
---

### Post by gdi2k on 2009-10-26
Greetings, 

I have a Lenovo ThinkPad X200, which supports Full Disk Encryption in hardware, configurable from the BIOS as detailed here: 
[http://www.thinkwiki.org/wiki/Full_Disk_Encryption_%28FDE%29](http://www.thinkwiki.org/wiki/Full_Disk_Encryption_%28FDE%29) 

This reads like a great set of features, and it really does work this way. What I find worrying however is that, after a system restart (as opposed to starting up cold), the encryption password is not requested and the drive remains unencrypted between restarts. 

So if the device is stolen while suspended (as opposed to powered off), the thief could switch to a VT, hit ALT+CTRL+Del to reboot, modify grub settings to boot off a Live CD or flash drive and then access my data from that environment. 

(I think it would also be possible to simply interrupt the boot process to gain root access and access the data from there?)

I always travel with my laptop suspended (it's just faster than booting each time!), and there seems to be no BIOS option to force a password request after a reboot, so in theory I'm wide open. 

On the other hand, I find it hard to believe that Intel / Lenovo / Seagate would go to so much trouble to implement such a system that could be circumvented so easily. 

Am I missing something?

---

### Post by cariboo on 2009-10-26
Yes you are missing something, smart thieves very rarely get caught, fortunately there are very, very few smart thieves. 

Most thieves only steal for money, they try to get rid of stolen property as soon as possible. A thief will have no idea what Linux is.

The people that buy stolen property also fall in to the same category as smart thieves. If they are confronted with anything other than Windows, they have no idea what to do with the computer.

This is probably the only case where security by obscurity works.

---

### Post by gdi2k on 2009-10-26
Yeh, I guess there are two kinds of thieves; 
[LIST]
[*]Those who steal to sell the hardware for profit (the vast majority).
[*]Those who steal for information.
[/LIST]
Those stealing to sell the hardware won't spend much time trying to get at the data, so obfuscation is probably effective here. 

But those stealing for information would likely be better informed. Now I'm no Fortune 500 CEO or high ranking government official (yet!! ;-) ), but you never know who wants to get what dirt on you, so for peace of mind, I would prefer something more robust. 

Since initially posting, I've read more about my hardware and grub.

It seems that grub supports encryption, see here: 
[http://wiki.linuxquestions.org/wiki/Securing_GRUB](http://wiki.linuxquestions.org/wiki/Securing_GRUB)

Assuming the implementation is solid, this would prevent the thief from booting anything without a password (including modifying boot entries to boot off CDs / Flash Drives). 

The only other way would be to change the boot priority in the BIOS. It's trivial to set a supervisor password, but it's usually also trivial to reset it - I don't have much experience with laptops, but all my desktops have a BIOS reset jumper / button that will eliminate the password, making this a waste of time. However, according to my laptop's troubleshooting guide, forgetting a password is pretty serious stuff, which is encouraging: 
[IMG]http://farm3.static.flickr.com/2689/4045715149_969444b27e.jpg[/IMG]

So on this particular hardware, as long as I use the Full Disk Encryption and set a BIOS Supervisor password, the BIOS should be safe and the hard disk fully encrypted. If I then secure Grub properly (and assuming its security is properly implemented), attacks on grub should be prevented too. 

Purely academically, can anyone think of other ways a thief could access the data on a suspended Ubuntu laptop with FDE?

---

### Post by gnuisancev3 on 2009-10-26
If i was to encrypt my hard-drive, i'd use luks rather than something provided by IBM that's no where close to being as documented.

The alternate ubuntu install cd is capable of this.

---

### Post by gdi2k on 2009-10-26
Yes, I'm doing this currently, but would really like to move away from it due to terrible performance impact. I can live with slower file transfers, but when the system slows to a crawl with 100% CPU usage when doing anything file related (resulting in jerky mouse response, sound stutters etc.), it's too much to bear. 

Maybe the home directory encryption in Karmic will be a good compromise as at least the application binaries aren't encrypted...

---

### Post by rookcifer on 2009-10-26
> **gdi2k said:**
> Yes, I'm doing this currently, but would really like to move away from it due to terrible performance impact. I can live with slower file transfers, but when the system slows to a crawl with 100% CPU usage when doing anything file related (resulting in jerky mouse response, sound stutters etc.), it's too much to bear. 

Maybe the home directory encryption in Karmic will be a good compromise as at least the application binaries aren't encrypted...

LUKS encryption should not give a noticeable performance impact.  It should be in the range of 5%.

---

### Post by gdi2k on 2009-10-27
I've been using LUKS encryption for a couple of years on a variety of systems. Performance impact is major, significantly more than 5%. But as I said, it's not so much the extra time it takes to perform file operations that bothers me, it's the CPU load that comes with it that completely kills responsiveness and makes the whole system feel sluggish. Copying photos, burning a CD, running a backup, checking a partial torrent, updatedb etc. all make the system essentially unusable for normal work. 

And if any swap ever gets used (which is also encrypted), you can forget it. Aside from a restart, I haven't found a way to recover. 

Phoronix frequently runs benchmarks on encrypted systems, but unfortunately they don't include CPU load measurements. They do show a significant performance impact on encrypted file systems though. 
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_910_encryption&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_910_encryption&num=1) 

With hardware FDE there is no performance impact, nor additional CPU load as the en / decryption is handled by dedicated hardware at a low level, hence the attractiveness.

---

### Post by gdi2k on 2009-10-31
Grumble, having upgraded to Karmic (fresh install), the aforementioned grub link describing how to secure grub is no longer applicable as Karmic uses Grub 2, and the configuration is completely different. Currently authentication in Grub 2, although possible, is not yet fully supported, see here: 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/392158](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/392158) 

Perhaps I'll just refrain from losing my laptop until it's fully supported ;-)

---

### Post by TDK800 on 2010-05-06
> **gdi2k said:**
> Purely academically, can anyone think of other ways a thief could access the data on a suspended Ubuntu laptop with FDE?


There are multiple vulnerabilities that allow doing this found in the past years, firewire port, freezing and reading memory (e.g. FDE decryption password in memory).

Here's an excellent article on how to secure notebook hardware against all known vulnerabilities and government/backdoor attacks:
[http://www.mob.com/blog.php?id=1089](http://www.mob.com/blog.php?id=1089)

The main threat now seems to be the new CEO's DOD connection:
[http://ubuntuforums.org/showthread.php?t=166015](http://ubuntuforums.org/showthread.php?t=166015)

So for uber-secure requirements, use Debian ;)

---

