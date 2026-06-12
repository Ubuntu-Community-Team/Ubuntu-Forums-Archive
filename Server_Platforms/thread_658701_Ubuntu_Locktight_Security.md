---
title: "Ubuntu Locktight Security"
date: 2008-01-04
forum: Server Platforms
---

### Post by Awayne on 2008-01-04
I'm looking at securing Ubuntu 6.06.1 Dapper Drake and Ubuntu Gutsy Gibbon. My server runs Dapper LTS and my desktop runs Gutsy. Both will be upgraded to Hardy when  released, with the only possible exception being the server waiting 3 months for stability reasons. I've been using the "shred" command and wiping sensitive files, but it's not enough. Because I'm about to store a lot of sensitive information such as bank details, household accounts, business accounts, home address lists, E-Mail lists and the like. I want to secure my systems as tight as possible. I'm not worried about a break in from the Internet side, but I am worried about thieves. I am looking at using the shred command to wipe out certain parts of the filesystem before removing root if an authorization code isn't given by a custom shell script on boot. A 2 minute grace period before it executes. It must be given as "root@box" rather than "user@box" which, with Ubuntu using by default, sudo, should make it a challenge for even the most talented cracker. As well as this, "kill switches" to automatically wipe systems the same way within 10 secs if an override isn't given in case of attempted burglaries while I'm at the systems. As a failsafe to this, to prevent anyone who knows Linux, an encrypted filesystem using twofish to encrypt an entire HDD so all they get is scrambled mess, assuming they can manage to mount the devices. To add to this I need to alter a command line firewall to secure it even further as an additional failsafe to any would-be-cracker sat outside with kismet. Due to the personal information being stored on both my desktop and server I would like to go to sleep at night knowing it would take the CIA to break them, that's if they could. Is anyone able to advise me, walk me through or point me at any tutorials to do this? I really don't know how to start so any help would be incredibly helpful and greatly appreciated. Even if it's a comment on what to look for, it would really help me out. Thanks for your time.

---

### Post by HermanAB on 2008-01-05
It is simple really.

1. Forget shred - it doesn't really work.
2. Encrypt your /home share (and other data shares you may have), as well as /swap and /tmp.
3. Use long passwords of at least 9 characters for all accounts.
4. Install Shorewall or Firestarter as firewall.
5. Only use encrypted protocols over the internet: SSH, IMAPS, POPS and so on.
6. Disable root login for SSH.
7. Do not give root an email account.

I hope that gives you some ideas.

Cheers,

Herman

---

### Post by Awayne on 2008-01-05
> **HermanAB said:**
> It is simple really.

1. Forget shred - it doesn't really work.
2. Encrypt your /home share (and other data shares you may have), as well as /swap and /tmp.
3. Use long passwords of at least 9 characters for all accounts.
4. Install Shorewall or Firestarter as firewall.
5. Only use encrypted protocols over the internet: SSH, IMAPS, POPS and so on.
6. Disable root login for SSH.
7. Do not give root an email account.

I hope that gives you some ideas.

Cheers,

Herman
Thanks for the suggestions, I have implemented some of them though. Although en encrypted filesystem is something I really need, as well as a way of destroying data without being around if my systems are stolen.
3, 5, 6 & 7 I have already done on my server, the desktop has no outside access, only local. The firewalls and encryption are needed. Shred doesn't work? I thought it did, otherwise why is the binary installed in the first place?

---

### Post by HermanAB on 2008-01-05
Shred works with Ext2, but no-one in his right mind uses Ext2 anymore.  On log structured file systems, it is pretty much impossible to erase a file, since nothing is ever actually overwritten.   So all shred will do is add a bunch of zeroes and what not in a different place on the disk while leaving the old data untouched. Therefore, on a modern file system like Ext3, XFS, JFS, ReiserFS and NTFS, shred doesn't really work.

In general, Unix utilities are never removed once introduced, since it may break some old scripts.  Therefore shred will hang around for some decades more, even though it is basically useless.

The only way to *really* delete data off a disk, is to encrypt the whole file system and then go on a nice relaxing holiday to forget the key...

Cheers,

Herman

---

### Post by Awayne on 2008-01-05
> **HermanAB said:**
> Shred works with Ext2, but no-one in his right mind uses Ext2 anymore.  On log structured file systems, it is pretty much impossible to erase a file, since nothing is ever actually overwritten.   So all shred will do is add a bunch of zeroes and what not in a different place on the disk while leaving the old data untouched. Therefore, on a modern file system like Ext3, XFS, JFS, ReiserFS and NTFS, shred doesn't really work.

In general, Unix utilities are never removed once introduced, since it may break some old scripts.  Therefore shred will hang around for some decades more, even though it is basically useless.

The only way to *really* delete data off a disk, is to encrypt the whole file system and then go on a nice relaxing holiday to forget the key...

Cheers,

Herman
Thank you for the explanation. Do you know any good tutorials for beginners on how to encrypt over 400GBs using twofish? If encryption is my best bet then I really should encrypt the HDDs. I know there are programs for Windows like PGP Full Disk Encryption, but I'm not sure what OSS sources are open to me. Again, thanks.

---

### Post by HermanAB on 2008-01-05
The present Linux 'standard' is dm-crypt with LUKS.  It is configured with cryptsetup, which is in synaptic.  The best encryption to use is probably AES, but twofish is good too.  Some Googling will find tons of information to get you going, but the best information would be on the dm-crypt web site.

Cheers,

Herman

---

### Post by Awayne on 2008-01-05
Thanks for your help, really appreciate it. I'll hit Google later today to find more information.

---

### Post by HermanAB on 2008-01-05
Yeah, I don't want to give you any misleading info on dm-crypt.  It is best to Google a bit and go to the project web site and read everything yourself.

Gotta catch some Zzzzzzz...  1h25 already.... Zzzzzzsnore...

---

### Post by HermanAB on 2008-01-05
Basically what you gotta do, is open a terminal with ctrl-alt f2, change to runlevel 3, with init 3 to kill off your X session, become root with sudo -i, copy you data somewhere safe, then umount /home to free the partition.  Now only, can you configure dm-crypt to encrypt all of /home.  Once done, mount /home and copy your data back.

Uhhh, sleep, yawn...

---

### Post by Awayne on 2008-01-05
Cheers mate. Going to look into it soon, taking your advice. Have a good rest. :)

---

### Post by HermanAB on 2008-01-05
Uhmmm, probably the most important tip:  
Only use Ext3 on encrypted partitions.  Don't use any other file system, since the slightest error on disk will cause you to lose *all* your data.  For some obscure reason, Ext3 is more resilient to this kind of thing than either JFS or ReiserFS - can't speak for the others, but both JFS and ReiserFS have broken on me on encrypted volumes causing a total loss of the partition.

Sooo, if you use encryption, making (encrypted) backups is *extremely extraordinarily* important.

Cheers,

H

---

