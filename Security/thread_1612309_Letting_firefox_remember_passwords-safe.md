---
title: "Letting firefox remember passwords-safe?"
date: 2010-11-03
forum: Security
---

### Post by dogdo on 2010-11-03
At the moment ive let firefox remember my firefox sync password and sync decryption code-is it safe to let firefox do this?

---

### Post by David Batty on 2010-11-03
It's safer than writing it on the wall!

---

### Post by David Batty on 2010-11-03
> **David Batty said:**
> It's safer than writing it on the wall!
What I meant is that there is no such thing as "safe", just degrees of "un safe". I let Firefox remember my passwords and I haven't had a problem so far.

---

### Post by wilee-nilee on 2010-11-03
I use FF sync but I only have passwords that are no consequence in breaking. It would be pretty hard to actually break them anyway. Any passwords that are sensitive are not even on the computer.

---

### Post by Brakkez on 2010-11-04
Saved passwords in Firefox are quite easy to read.
Tools -> Options -> Security -> Passwords -> Saved Passwords.

If you then press the 'Show Passwords'-button you can see your passwords in plain text.

You can prevent this by using a master password, but it is not enabled by default. 
If you use this master password, it will be "less unsafe" to store your passwords in firefox. :)

---

### Post by The Cog on 2010-11-05
If your laptop gets stolen and FF knows all your passwords, then so does the thief. FF has an option to store them encrypted which would probably prevent this.

It does worry me that a flaw it FF might be found that leaks stored password info. I'm sure I read last week of an exploit that makes FF remember passwords even if you told it not to - not the same thing but it shows that people are looking for flaws in that general area.

---

### Post by dogdo on 2010-11-05
> **The Cog said:**
> If your laptop gets stolen and FF knows all your passwords, then so does the thief. FF has an option to store them encrypted which would probably prevent this.

It does worry me that a flaw it FF might be found that leaks stored password info. I'm sure I read last week of an exploit that makes FF remember passwords even if you told it not to - not the same thing but it shows that people are looking for flaws in that general area.

I have a good password for the firefox master password-is this what encrypts the other stored passwords? does it use AES? 

I also have my home folder encrypted upon installation-but are firefox passwords stored in the home folder?

---

### Post by The Cog on 2010-11-06
> I have a good password for the firefox master password-is this what encrypts the other stored passwords?Yes> does it use AES? I don't know.> are firefox passwords stored in the home folder?Yes. Under ~/.mozilla somewhere.

That all looks safe to me.

---

### Post by lovinglinux on 2010-11-06
> **dogdo said:**
> I have a good password for the firefox master password-is this what encrypts the other stored passwords?

Yes.

> **dogdo said:**
> does it use AES?

[http://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=44595&forumId=1](http://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=44595&forumId=1)

> **dogdo said:**
> I also have my home folder encrypted upon installation-but are firefox passwords stored in the home folder?

The master password is saved in key3.db and passwords are saved in signons.sqlite database, both stored under your Firefox profile folder. So they are protected by the password manager encryption and by your home encryption.

---

