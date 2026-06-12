---
title: "Password Glitch?"
date: 2010-11-25
forum: Security
---

### Post by jds627 on 2010-11-25
The other day I was logging in to my computer and when I was at the login screen i decided on a whim to try and "x out" of the password prompt. After clicking on the x of each consecutive prompt, they stopped coming. It only took about five times. After this I was able to do everything I normally do. Including create and delete files. Has anyone else ever noticed this?:confused: It seems to me like it is a major security lapse!

---

### Post by CharlesA on 2010-11-25
What version of Ubuntu are you doing this on?

I tried it on Maverick and it didn't log me in at all.

---

### Post by Rubi1200 on 2010-11-25
I am also curious to know which version and whether or not you have been able to reproduce this again.

Tried and failed for me on Lucid and Maverick versions.

---

### Post by linux-hack on 2010-11-25
Do you have a password on your system ??? I rely don't think thats possible !!!!

---

### Post by jds627 on 2010-11-25
I'm using Maverick Meerkat...

---

### Post by CharlesA on 2010-11-25
> **jds627 said:**
> I'm using Maverick Meerkat...
We would really need more info on how to reproduce it if it's indeed a bug.

---

### Post by jds627 on 2010-11-25
I tried it again and was able to reproduce it. I turn on the computer and when the login box appears, I just click the x. Three to five times and I'm in.

---

### Post by CharlesA on 2010-11-25
What "x" ?

---

### Post by jds627 on 2010-11-25
I figured out what it was...It was configured to automatically log in and the screen I was referring to was actually the keyring login... It seems strange to me that it does that even when I told it to prompt for a password at login. The setting i had to change was to display available accounts and choose which to login to.

---

### Post by CharlesA on 2010-11-25
If you changed yer password from the terminal instead of from About Me, the keyring password isn't in sync with the user password. That's why it's prompting.

---

