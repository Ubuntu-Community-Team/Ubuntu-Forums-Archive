---
title: "Best encryption/backup/syncronization scheme"
date: 2010-06-07
forum: Security
---

### Post by leorolla on 2010-06-07
I have been googling a lot, but there are too many 2-year-old blogs that pop up and it doesn't really help.

I would like a seamless way of having personal files encrypted (at this point I am only worried about the home directory) and synchronize these files between different computers and with an external hd.

So far my partial solution is:
1) Default Ubuntu eCryptfs solution;
2) Unison to synchronize between the upper layers of both computers via ssh (operating on the /home/$USER mounted by ecryptfs) and also between one computer and the external HD;
3) Don't know about the external hd.

Reasons:
- I don't want any pain about data loss or data leak if my hardware gets stolen;
- Data in /tmp, /var and swap are not that important for me right now;
- It is very important to synchronize fast, incrementally and properly: propagating deletions rather than reverting and detecting change-change/change-delete conflicts before miss-propagating changes, which as far as I know only Unison is good at;
- Even if I could set the same passphrase on both computers (I guess I can, but Ubuntu does not offer me to choose the ecryptfs passphrase) I want to see the true filenames that are being synchronized;
- If possible I would like to simplify the whole scheme so that each computer is doing its own job seamlessly, and operating on the upper decrypted layer looks simple and robust;
- I would like a more general and easy-to-use scheme for the external device, so other folks use it too;
- If possible I would like ext4 backups, so it remembers file permissions etc... however it would be nice to be able to open it from Windows.

Are (1) and (2) above really good solutions or am I missing something?

What are the best solutions for (3)?

So far I have seen cryptsetup/palimpset and truecrypt. The more native and floss the better, but being crossplatform is nice. What are the pros and cons, and what's their relation to FreeOTFE and other Windows tools?

Thank you very much! :)

---

### Post by HermanAB on 2010-06-07
Well, backup and encryption are separate problems.  EncFS and LUKS are both good. Unison or rsync over SSH are both good. So you are on the right track.

If you want to automate things, drop a script in /etc/cron.daily.

---

### Post by leorolla on 2010-06-07
Thanks for answering :)

What about the backup/sync done on the upper layer of ecryptfs mounted home? You think performance is compromised?

I don't sync often enough for a cron job, normally both computers are shut down, sometimes I'm using one of them and never both... sometimes I manually turn on both laptops and get them to talk through unison to figure out what I have changed on each other.

Common sense tells me to use Stack for home and Block for external devices. Is this right?

So you recommend LUKS over TrueCrypt?

Backup and sync are separate but they interact ;)
For instance, Unison can look for a huuuge set of ext4 files and realize what has changed in a couple of seconds, and I can't use an encryption that looses that.

Side comment: this is something everybody should take the time to learn. Everyone will eventually have a burned HD or stolen laptop. Not having to bother at all when these happen is really priceless.

---

### Post by leorolla on 2010-06-08
Unison synchronizing the ecryptfs upper layer:

I got "fast" synchronization.

With 25~35 thousand files it takes 3 minutes to check that nothing has changed on my stack-decrypted home (mounted from a native ext4 encrypted .Private folder).
It is not really fast for Unison standards: it takes a couple of seconds to check exactly the same bunch of files with an ext4 filesystem on a much slower external HD.

OK, I could pay the price of 3 minutes waiting to keep this encryption scheme...

Unless there is a better one.
The problem with a block encryption that would resist a cold boot attack is that it would require assistance during boot, or at some point before login (right?).
I imagine some scheme with a login script that unwraps the passphrase from a hashed file together with my password and then mounts the block-encrypted partition on the top of my home folder.
In other words, roughly the same thing that Ubuntu is doing by default but with block device instead of stacked filesystem.
Is it possible?

(Note: if anyone wants to do the same scheme, you must remove the corresponding archive inside ~/.unison. The first sync will take hours. After you migrate from native to stack-decrypted unison needs to rebuild the archive to perform fastcheck properly.)

---

### Post by leorolla on 2010-06-08
More precisely: 23.000 files. The first synchronization with a cheap external HD after each reboot takes 3 minutes for (normally the only one), to sync again takes 1~3 seconds.
Unmounting the decrypted home and mounting again still gives 1~3 seconds, only rebooting gives 3 minutes.
The very first sync took a couple of hours.

---

