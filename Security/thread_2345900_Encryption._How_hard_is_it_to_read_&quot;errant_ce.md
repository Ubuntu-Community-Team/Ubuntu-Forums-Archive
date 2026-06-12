---
title: "Encryption. How hard is it to read &quot;errant cells' on a SSD?"
date: 2016-12-09
forum: Security
---

### Post by mikodo on 2016-12-09
I wonder about the risk of having a stolen computer with SSD, that is encrypted with LUKS, or encryptfs private directory, or even gpg-symetrical folder.

Any thoughts on how easy or, hard it is, for a bad intentioned person, to be able to find in 'errant cells' data, what the original owner deems sensitive?

---

### Post by TheFu on 2016-12-09
What is **errant cells**?

Corrupted sectors?

If using encryption, solid, tested, backups are the primary solution.  If any key sectors controlling the encryption are corrupted, expect complete, total data loss.  OTOH, all storage will fail and usually not when it is convenient, so solid, versioned, tested, backups are the primary solution with or without encryption anyway.

Encrypted data is next to impossible to recover. Can't say "never", because flaws are always found in software and there's usually the rubber-hose-method to access encrypted data.  The only way I know to fight the rubber hose method is with 2FA and not having access to the 2nd factor.  

Of course, if trivial passphrases are used, all bets are off. Trivial is anything less than 16 characters today, but just a few yrs ago, that was 12 characters.  12 character brute force attacks can be unlocked in less than 24 hrs today.  If there is time, TLAs have held data for decades awaiting the speed to catch up so things from the 1990s are being decrypted today.  For that reason, keeping passphrases long and complex enough to fight what brute force methods might handle in 2045 is my goal. Since I rarely actually type these passphrases in, 45+ characters seems reasonable, but if I can, 65+ characters are used.  

If the parts of the disk are unreadable, that data is gone. Get the backups out.  Don't expect logical data recovery tools to work, though low-level byte recovery tools may be able to force a sector replacement, I wouldn't count on it.  Backups.

---

### Post by kpatz on 2016-12-09
If by "errant cells" you mean blocks that were used but have been freed but not yet erased, yes it's possible to read them, but if the entire drive is encrypted all they'll get from any cell is encrypted data.

Similarly, if "errant cell" refers to a block that's gone bad due to a defect or drive wear, once again, if the data was encrypted to begin with, any forensic data recovery used is only going to return encrypted data.

Only if non-encrypted data gets written to the drive is there any possibility of recovering it unencrypted.  If you only encrypt your home folder, and sensitive data ends up in swap or /tmp or some other non-encrypted location, it is theoretically possible to recover this data if it hasn't been overwritten.  But, if you encrypt the entire drive or partitions with LUKS or whatever, and also encrypt or disable swap, no non encrypted data should ever be written to the drive, so your data should be safe from theft.

---

### Post by mikodo on 2016-12-09
Thank you, very much folks, for your knowledgeable and thoughtful responses. I have more understanding in encryption now, than before. 

- I read, research and ponder things, from a casual-user's, old person's perspective.

- I try to approach life, with a thoughtful reasonableness. So, in the case of my using encryption, I try to weigh the benefits derived, against the risks incurred. 

- With my planning to go to SSD, the chapter in the link below, on cryptsetup,  '5.19 What about SSDs, Flash and Hybrid Drives?', has given me some pause:

[https://gitlab.com/cryptsetup/cryptsetup/wikis/FrequentlyAskedQuestions#5-security-aspects](https://gitlab.com/cryptsetup/cryptsetup/wikis/FrequentlyAskedQuestions#5-security-aspects)

- I am going to mark this thread 'solved', without going into long detail, for my inherent questions are presently answered.

Thanks, again.

---

### Post by DuckHook on 2016-12-09
Speaking only about encrypted /home or ~/Private:

These directories themselves would be very difficult to decrypt *provided* that both the encryption key and the authentication passphrase are robust. By robust, I mean what TheFu says: phrases that may seem absurdly long (and complex). Mine are not quite as long as his, but they are more than 30 characters.

If the directories themselves are properly encrypted, then the biggest problem with Linux is leakage. The typical desktop in its default configuration leaks info like a sieve. Any scoundrel with a modicum of knowledge can glean useful info from a number of areas that most users overlook.

[LIST=1]
[*]If the owner uses hibernation, then all bets are off. Hibernation pushes the whole system state into swap. But a swap set up for hibernation cannot be encrypted unless one takes really arcane measures that render the system fragile. Ergo, if you have any concern for security, don't hibernate. Suspend is even worse and is not worth analyzing.
[*]Even without hibernation, swap is potential trouble. If, in the normal course of operations, the system pushes areas of memory into swap, you have to consider those contents to be persistent. If those contents hold passwords or other credentials, you are naked. Solution: encrypt your swap.
[*]The above also holds true for the /tmp directory. Solution: if you have enough RAM, map /tmp to a tmpfs. If you don't have enough RAM, get more.
[*]/var/tmp is not as much of a problem. It was designed for temporary files that needed to persist through reboots. Here, you have to be alert to rogue apps whose developers decided to place sensitive info in /var/tmp instead of /tmp where such stuff is "supposed" to go. It's a good habit to review what's in there from time to time, to see if some app makes a habit of abusing this directory. If really paranoid, map it also to your tmpfs and live with the occasional app breakage.
[/LIST]
I encrypt only my ~/Private directory. This gives me very fine-grained control over my user environment. For example, I have a little headless backup fileserver in a basement closet used only for episodic tertiary backups, so most of the time, it is turned off. I can wake it up with a WoL signal, then ssh into it to make it do its stuff. Whole disk encryption doesn't work because it breaks ssh. Even encrypting only /home is a pain: ssh needs to see its public key to connect and can't read it because ~/home/[user]/.ssh is still encrypted. I could move the key out of /home, but through past suffering, I don't like changing system default locations because I soon forget where I put them.

[LIST=1]
[*]The way out of this pickle is to leave /home itself unencrypted, but to encrypt *everything* personal by moving it into the ~/Private directory, then soft symlink back to where the system expects to find it. This way, you can maintain functionality like ~/.ssh/authorized_keys but also secure ~/.ssh/id_rsa since the latter is just a symlink to the real file in ~/Private and cannot be read unless ~/Private has first been properly decrypted/mounted.
[*]For GUIs, a big source of leakage are thumbnails. It's amazing what info can be extracted from thumbnails. Solution: move ~/.cache/thumbnails into ~/Private and symlink back.
[*]For FireFox: move both ~/.mozilla and ~/.cache/mozilla into ~/Private and symlink back. Likewise for Thunderbird, Chrome, Evolution… you get the idea.
[*]And by moving&#8594;symlinking Pictures, Video, Documents, Downloads, etc, you lock down your personal files too. The only one I never bother with is Music. If a thief wants a copy of my music collection, he can have it. Everything is backed up.
[/LIST]
Of course, as TheFu often suggests on these forums, whole-disk encryption renders most of the above academic. But he and I have a friendly difference of opinion there. ;)

---

### Post by mikodo on 2016-12-10
^^ Thank you, for the effort given, in responding to share with us, of these things.

---

