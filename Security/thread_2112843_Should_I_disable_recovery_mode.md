---
title: "Should I disable recovery mode?"
date: 2013-02-05
forum: Security
---

### Post by TheGuyWithTheFace on 2013-02-05
I recently saw this article on how to reset Ubuntu passwords:

[http://www.liberiangeek.net/2012/09/recover-lost-passwords-in-ubuntu-12-04-recovery-mode/](http://www.liberiangeek.net/2012/09/recover-lost-passwords-in-ubuntu-12-04-recovery-mode/)

While I can see how useful it would be to be able to reset a lost password, isn't this a bit of a major security hole? I mean, if someone were to steal my computer, even though I have my /home encrypted, wouldn't they just be able to boot into recovery mode and reset my password to gain access to all my files? Surely I'm misunderstanding something, because so far, Ubuntu and Linux/GNU systems in general seem so secure, and it seems rather odd for something like this to be possible...

That being said, if I did read that right, and this is possible, would it be advisable to just disable recovery mode? My /home is on a separate partition from my system, so worst case scenario, if I managed to blow up my system, I could just do a fresh install rather than try to fix it via recovery mode. 

This article mentioned just a few pros and cons about recovery mode, but does anyone else have any thoughts? (Also, for anyone interested, it also says how to disable it.)
[http://www.liberiangeek.net/2012/09/disable-the-recovery-mode-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/09/disable-the-recovery-mode-in-ubuntu-12-04-precise-pangolin/)

---

### Post by CharlesA on 2013-02-05
Not a security risk. Physical access == root access.

You can password protect GRUB and you can password protect your BIOS.

Unless you want to be stuck if/when an update completely borks your system, you should keep recovery mode enabled.

Even if someone was able to get access to your hard drive, with an encrypted home folder, wouldn't that data be unreadable?

[http://ubuntuforums.org/showthread.php?t=2036124](http://ubuntuforums.org/showthread.php?t=2036124)
[http://ubuntuforums.org/showthread.php?t=1933746](http://ubuntuforums.org/showthread.php?t=1933746)

---

### Post by collisionystm on 2013-02-05
Yes, it is a security problem but it is a convenient way to help someone that forgot their password, recover their system. It is placed there for use with friendly intentions.

Although I personally do not use an ecrypted home nor have I ever used the recovery boot, I would imagine that changing the passcode in recovery boot would render your encrypted home inaccessible. I would imagine the recovery mode would simply update the /etc/passwd and /etc/shadow file, but not the key required to access the encrypted file system. 

I could be and am probably wrong, but who knows, maybe my common sense is going strong tonight.

Feel free to disable it, It's really just all about personal preference. It is your computer and you can do as you wish.

---

### Post by TheGuyWithTheFace on 2013-02-05
> **CharlesA said:**
> 
Even if someone was able to get access to your hard drive, with an encrypted home folder, wouldn't that data be unreadable?


That's the idea, but since my /home is decrypted when I logon, then if someone were to reset my password with recovery mode, they could then log on and have access to my data, right? That's the main thing I'm worried about.

> **collisionystm said:**
> I would imagine that changing the passcode in recovery boot would render your encrypted home inaccessible. I would imagine the recovery mode would simply update the /etc/passwd and /etc/shadow file, but not the key required to access the encrypted file system. 


Oh, that would be very good, I certainly hope so, but I'll have to test that later. I'll report back when I find out.

> **CharlesA said:**
> 
Unless you want to be stuck if/when an update completely borks your system, you should keep recovery mode enabled.

Well, I was prepared to accept that risk, but I think I'll wait and see try collisionystm's theory before I go mess things up. I'll test that sometime tomorrow, hopefully!

---

### Post by collisionystm on 2013-02-05
Good luck!

---

### Post by CharlesA on 2013-02-05
> **TheGuyWithTheFace said:**
> Well, I was prepared to accept that risk, but I think I'll wait and see try collisionystm's theory before I go mess things up. I'll test that sometime tomorrow, hopefully!

I think that is how it works (passphrase is tied to your user account via the keyring), but I am not 100% sure as I haven't bothered to encrypt my home directory.

In theory if the login password and keyring password don't match, it won't give you access to the encryption passphrase.

Good luck with your testing!

---

### Post by tubbygweilo on 2013-02-06
TheGuyWithTheFace, I trust that you have good, tried & tested backups of all that you could loose if things do not quite unfold as expected?

---

### Post by collisionystm on 2013-02-06
> **tubbygweilo said:**
> TheGuyWithTheFace, I trust that you have good, tried & tested backups of all that you could loose if things do not quite unfold as expected?


Backups are for men with no sense of adventure!

---

### Post by TheGuyWithTheFace on 2013-02-06
> **tubbygweilo said:**
> TheGuyWithTheFace, I trust that you have good, tried & tested backups of all that you could loose if things do not quite unfold as expected?

Yes, thanks for your concern.

> **collisionystm said:**
> Backups are for men with no sense of adventure!

Data you don't have three copies of is data you don't want!

That being said... Does anyone know of a way that I could run the dialogue one gets at first boot about recording your encryption passphrase? I remember running it, and then I lost it/didn't write it down, but that may come in handy in case I can't access my data. I haven't tried anything yet with recovery mode, but I guess knowing my encryption passphrase would be a good thing just in case.

---

### Post by Cheesemill on 2013-02-06
> **TheGuyWithTheFace said:**
>  Does anyone know of a way that I could run the dialogue one gets at first boot about recording your encryption passphrase? I remember running it, and then I lost it/didn't write it down, but that may come in handy in case I can't access my data.
Just run the following command once you are logged in...
```
ecryptfs-unwrap-passphrase
```

---

### Post by TheGuyWithTheFace on 2013-02-06
Great, it worked. Thanks, Cheesemill!

---

### Post by TheGuyWithTheFace on 2013-02-10
Well, I haven't had the opportunity to Test anything yet, sorry. I'll try to do that sometime this week, but I felt inclined to tell you guys.

---

### Post by TheGuyWithTheFace on 2013-02-10
Alright! I changed my password via recovery mode using the aforementioned article, but I can confirm that when I booted back in, when I entered the correct password, The login screen simply refreshed! Once I went back into recovery mode and changed my password back, I was able to log in normally!

Good call collisionystm, and thank you everyone for your thoughts. I feel much safer knowing that someone can't access my encryped /home through recovery mode, so I think I'll leave it on. I should have known that ubuntu wouldn't be that easy to crack!

---

### Post by collisionystm on 2013-02-11
> **TheGuyWithTheFace said:**
> Alright! I changed my password via recovery mode using the aforementioned article, but I can confirm that when I booted back in, when I entered the correct password, The login screen simply refreshed! Once I went back into recovery mode and changed my password back, I was able to log in normally!

Good call collisionystm, and thank you everyone for your thoughts. I feel much safer knowing that someone can't access my encryped /home through recovery mode, so I think I'll leave it on. I should have known that ubuntu wouldn't be that easy to crack!


Cool!

Thanks for taking the time to test it out!

---

### Post by TheGuyWithTheFace on 2013-02-11
> **collisionystm said:**
> Cool!

Thanks for taking the time to test it out!

It's the least I can do after the help you guys have provided. :D

---

### Post by SeijiSensei on 2013-02-11
Just an aside, but removing the GRUB entry for recovery mode won't block anyone from accessing single-user mode.  If you can force the GRUB menu, for instance by holding down Shift while rebooting, you can edit the "kernel" entry and add "S" to the list of kernel options.  That will boot into single-user mode and let you change the password.

---

### Post by TheGuyWithTheFace on 2013-02-11
well, one more reason not to disable recovery mode...

---

