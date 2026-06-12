---
title: "CryptData's enforced password key; so secure, you can't change it!"
date: 2019-09-23
forum: Ubuntu/Debian BASED
---

### Post by mrlemonyfresh on 2019-09-23
I'm doing some research into Full Data encryption works and how it relates to the issue I'm having In Pop!_Os.

I'm told that this is more an Ubuntu issue than Pop!, but please correct me if I'm wrong.
Every day, my wife needs me to become IT guy because something is either broken, requires constant setup, or is just very non-intuitive. 'CryptData' is the latest villain of usability. 
She's not a nerd, she's got a.d.d, and nobody else sets foot on her PC, so the password is yet one of too many hurdles that make her want to give up. 

So If I understand correctly, this is the solution here.

[https://askubuntu.com/questions/245112/can-i-disable-full-disk-encryption](https://askubuntu.com/questions/245112/can-i-disable-full-disk-encryption)

This solution is miles from usability. This is overly complicated, a barrier for most users, and another pointless chore for so little gain. Where do we trace this back to? Is this Ubuntu, or something else?

It needs to change. This is more than about security, this is about facilitating end-user control over their PC. This looks bad on open-source distros.
Because you see Ubuntu and say; Nice and secure; We shouldn't instead be saying; 'Nice and secure. **Against most users**'.

Kind regards,

Simon.

---

### Post by jeremy31 on 2019-09-23
Moved to Ubuntu Debian based

---

### Post by The Cog on 2019-09-23
As I understand your post, the OS has been installed with full disk encryption, and you want to remove it so as not to have to enter the password every time you boot. I've never undone full disk encryption my self, but I can well believe that reinstalling is probably the easiest solution. 

I'm not sure what you think needs to change. Making it easier to undo an encrypted install? Maybe, but that's not a common thing to want to do - most folk would just choose not to install with encryption if they didn't want it. 
Post 9 links to a way to disable the password query without reinstalling which looks fairly easy.

Either way, disabling an encryption passphrase prompt is not something a normal user would be expected to do, so I would not regard it as a "barrier for most users". It's definitely a one-off administrator task.

---

### Post by TheFu on 2019-09-23
There is some usability issue with PopOS? Something about encryption?   Encryption is never easy, anywhere.  The way that encryption works on my laptop is the same way that it works on Android and the same way it worked with TrueCrypt years ago.  

If encryption isn't desired any more, take the backups you make at least weekly, and use them to re-install the OS onto non-encrypted storage.  Backups aren't optional whenever encryption is involved. Any tiny logical issue or any physical issue with the storage devices can make all that data gone, gone, gone.  Without a backup, data recovery is impossible.  Backups and restores are how Unix people handle many issues.  There are at least 1001 issues that versioned backups solve. Not having them isn't optional, unless data loss is desired.

I boot the laptop. Get presented with a text entry to enter the disk description.  Using something I know and something I have, one of the 8 allowed passphrases is entered.  I know a 10+character password and use a Yubikey crypto-device to enter a 30+ character 2nd-half of the total password.  Press enter.  That unlocks the HDD and the partition configured so the OS can boot.   Hardly seems like anything easier could be possible.

I've chosen to use a crypto-key in my entry, but a passphrase alone could be used for significantly less security. There is no substitute for length, assuming the same complexity/alphabet is used, however.

Care to provide a clear description if what is happening there?  
How you'd make it better?

If you want to add or change the current password used, the **cryptsetup** tool allows that. There are 8 "passphrase" slots, so we can add a total of 8 users to the system, each with their own disk decryption passphrase which is unknown by others.  I use 2 different passphrases. The method described above and a nearly impossible to type, longer, one that is there as a backup, should I lose my yubikey.  The cryptsetup manpage is really excellent.```

       LUKS can manage multiple passphrases that can be  individually  revoked
       or  changed and that can be securely scrubbed from persistent media due
       to the use of anti-forensic stripes. Passphrases are protected  against
       brute-force  and  dictionary  attacks  by PBKDF2, which implements hash
       iteration and salting in one function.

       Each passphrase, also called a key in this document, is associated with
       one  of  8 key-slots.  Key operations that do not specify a slot affect
       the first slot that matches the supplied passphrase or the first  empty
       slot if a new passphrase is added.
```
So, to change a passphrase, a slot must be specified.

---

