---
title: "Windows Vista to make dual booting harder"
date: 2006-04-28
forum: The Cafe
---

### Post by towsonu2003 on 2006-04-28
Dapper currently cannot correctly set up Windows Vista to boot in a dual-boot system, as faras I know. /boot/grub/menu.list needs to be changed a little to fix the issue.

Now, it seems that a disk encryption system shipped with Vista will make file sharing between the OS's even harder for us. See [http://linux.slashdot.org/article.pl?sid=06/04/27/2219258&from=rss](http://linux.slashdot.org/article.pl?sid=06/04/27/2219258&from=rss)

I am still waiting for a Windows Vista feature that kills Lilo and Grub. That would be a nice gesture to EU ;)

-just wanted to give Vista testers a heads up in case they use this encryption method, or if it gets enabled by default[1].

[1]MS enabling a security feature by default out of the box? Would be a good April 1st joke to all of us.

---

### Post by tseliot on 2006-04-28
[QUOTE=towsonu2003]I am still waiting for a Windows Vista feature that kills Lilo and Grub. That would be a nice gesture to EU ;)[/QUOTE]
Oh well, nothing that couldn't be solved by a "format C:"... :p

---

### Post by htinn on 2006-04-28
[http://www.theregister.co.uk/2006/04/27/schneier_infosec/](http://www.theregister.co.uk/2006/04/27/schneier_infosec/)

> Vista is due to feature hardware-based encryption, called BitLocker Drive Encryption, which acts as a repository to protect sensitive data in the event of a PC being either lost or stolen.

Basically, you'll need to have a FAT32 partition in addition to whatever you're using for Windohs. But don't most dual-booters already do that? Looks like a total non-issue to me.

---

### Post by towsonu2003 on 2006-04-28
[QUOTE=htinn]
Basically, you'll need to have a FAT32 partition in addition to whatever you're using for Windohs.[/QUOTE]
I agree that it's not a critical issue. Even not a major one. I mean, it's optional... and requires (I think) hardware support for this. 

But -there's always a but- imagine you just switched to Linux dual boot, have all your files in ntfs (encrypted) in a 20GB partition, and a 1GB fat32. And you have no intention to transfer files from one to the other. Now, what do you do when you want to test your new toy? 

Or you just remembered that you need a file from an ntfs partition, encrypted. reboot to windows, copy to unencrypted fat32, reboot, copy to ~/ ? I always pick files from my ntfs partition, and didn't boot to windows for a while now. If it was encrypted - not good. 

These small things are the little games that MS plays after which EU gets pissed[1]. These small tricks are also the things that stop comfortable migrations. 

[1] They won't get pissed if MS publishes adequate documentation for interoperability, but they never do (answer to: why do we still have ntfs writing support as experimental?)

---

### Post by silvagroup on 2006-04-28
Could you possibly gag it.....[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by htinn on 2006-04-28
Yep. Yet another reason to not use Windows, or at least use a different hard drive.

---

### Post by towsonu2003 on 2006-04-28
[QUOTE=silvagroup]Could you possibly gag it.....[http://gag.sourceforge.net/](http://gag.sourceforge.net/)[/QUOTE]
possibly not. Because Vista is still Beta, no one is willing to support its bootloader yet, thinking that it may change at any time, making all efforts obsolete.

---

### Post by whoa_551 on 2006-04-28
I just read something interesting in a computer magazine.  Microsoft recently won a decision by the US Patent Office that makes it possible for Microsoft to patent the FAT filesystem, hence making it illegal for a (US?)Linux user to access a FAT partition with Linux, if Microsoft so decided.  It went on to talk about how many storage devices (e.g. USB flashdrives), use FAT for its filesystem, and how Microsoft could demand royalties, etc.  Wow, they never stop.  Not until Windows is the only OS on the planet, will they.  It went on to note however, that only the Courts can decide what is a legal patent or not, not the US Patent Office, and in the past the Courts have ruled against what the Patent Office recommends...

---

### Post by ade234uk on 2006-04-28
And at the end of the day when Microsoft close more doors on people they are slowly backing themselfs in to a corner that they cannot get out up. 
I am so glad I dont use that piece of shit Windows anymore.

---

### Post by htinn on 2006-04-28
Microsoft acquires patents to assist in their legal battles against scum who basically patent technology that has been around for many years. I guess the patent office doesn't give a flip about prior art. Of course, now thanks to the idiotic NTP v RIM decision, you don't even need a patent.

Microsoft may be obsessed with making profits, but even they know that you can't be profitable if the entire economy is flushed into the sewer by "intellectual property" BS.

---

