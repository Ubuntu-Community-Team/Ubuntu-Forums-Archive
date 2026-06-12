---
title: "Format disk at keyword entry"
date: 2012-02-02
forum: Security
---

### Post by philippsfrt on 2012-02-02
Ok now i think this might sound a little odd but if like to know if its possible. What i would like to do is the following.

On some modern safes, when you enter a certain combination (not the actual one) a silent alarm is sent out and an extra protection mechanism engaged. 

What i would like is that at the login screen if i enter my normal password i log in...but if i enter the other password the computer locks up and begins to format and overwrite the hard disk.

Does anyone know if this is somehow doable? I had something similar going on a windows machine a couple of years ago but cant seem to find the application i had used to do this with and nothing came out of a google search.

Help please?

---

### Post by tubbygweilo on 2012-02-04
philippsfrt,
If wanting this feature so that if being forced to sign on while under duress so as to "wipe" your machine then I expect those with a gun to your head will not be too pleased. They may even pull the trigger.

If you wish to keep your machine safe from prying eyes then a long pass phrase and full disk encryption may be the answer although they may still pull the trigger but you machine will be safe.

---

### Post by Porcini M. on 2012-02-06
You could always create a separate user that you'd sign in as under duress (but with a plausible-looking username), then set up the wiping to be a task that starts on login.

---

### Post by iisjman07 on 2012-02-08
This won't matter to anyone with physical access. If law enforcement take your machine away, they'll forensically clone your drive to another as a backup, then analyse the data while the host operating system is offline. Also, I'm not sure about how well things will turn out if you format the disk that the operating system is currently running on, and simply formatting wouldn't remove the data, you'd need to wipe/shred the drive (eg: dban, hdd secure erase) or use hdparm/hdd secure erase to invoke the firmware command to wipe the drive.

I would suggest using truecrypt's hidden volume feature, might be worth reading about

---

### Post by Grenage on 2012-02-08
I've looked into similar systems, simply out of curiosity.  I eventually concluded that the best system was a large encrypted volume with a duress password.

A) Securely overwriting a drive takes a while.
B) If you do not sign in and I take your PC, I can get your data.

You can't know how much data is on an encrypted volume, so with a duress password, any assailant would have to know that something *should* be there.

I never put it into practice; no armed goons were after my Firefox history, WoW account, or sheet music.

---

