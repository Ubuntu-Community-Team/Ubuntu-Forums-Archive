---
title: "How to get the admins pass..."
date: 2009-09-03
forum: Security
---

### Post by Steam. on 2009-09-03
So, i think we are gonna have edubuntu this year, and maybe a linux server, so do you know how to get the admin's pass from a normal user account?

---

### Post by howlingmadhowie on 2009-09-03
> **Steam. said:**
> So, i think we are gonna have edubuntu this year, and maybe a linux server, so do you know how to get the admin's pass from a normal user account?

tricky, very tricky.

every now and then a security hole is found allowing a normal user to gain root access.  finding the admin password is more difficult, because the admin password isn't actually stored in the system, but rather its sha1 hash (i think it's sha1, it may be md5).

---

### Post by Steam. on 2009-09-03
So, basically, not possible.

(unless i'm very lucky :)

or i could reset CMOS and format and put win 7.

---

### Post by greyaline on 2009-09-03
Recovery mode, [http://ubuntuforums.org/showthread.php?t=648336](http://ubuntuforums.org/showthread.php?t=648336)

---

### Post by sisco311 on 2009-09-03
> **Steam. said:**
> ... so do you know how to get the admin's pass from a normal user account?

Why?

---

### Post by cdenley on 2009-09-03
Passwords are hashed with crypt's SHA-512 algorithm (MD5 for Ubuntu <= 8.04). FYI, crypt's algorithms are not the same as the standard algorithm with the same name, but a more complicated algorithm involving the standard one. If you have physical access, you can retrieve the hash then attempt to crack it, which may not be feasible depending on the strength of the password. Even with a weak password, it would take a long time. It would be much easier to reset the password.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

If you require passwords which can easily be cracked with physical access, Windows would be a better solution.

---

### Post by Steam. on 2009-09-03
> **sisco311 said:**
> Why?

Edubuntu, at school.

Add/Remove doesn't work without a pass.

So without a pass, no MSN.

---

### Post by sisco311 on 2009-09-03
> **Steam. said:**
> Edubuntu, at school.

Add/Remove doesn't work without a pass.

So without a pass, no MSN.

Ask the system administrator to install MSN for you.

---

### Post by scorp123 on 2009-09-03
> **Steam. said:**
> Add/Remove doesn't work without a pass.
So without a pass, no MSN. I don't recommend doing that. Manipulating computers that do not belong to you might have legal consequences. They might kick you from your school if nothing else? Or even better: Something else goes wrong ... and they simply blame you for it?

So instead of manipulating computers ... why not simply use Meebo?

[http://www.meebo.com](http://www.meebo.com)

Meebo is a web site that allows you to login to your IM accounts. So you get MSN, Yahoo, MySpace, AIM, GTalk, ICQ, Jabber ... All on one web site.

So for as long as there is a browser on the system you could simply go to meebo.com, login ... and voila. Chat away. All without manipulating any passwords.

I have used Meebo myself (e.g. when visiting customers who have rather restrictive settings) and it works tip top.

---

### Post by Steam. on 2009-09-04
Yeah, but it doesn't work sometimes, so Ebuddy, but ebuddy you can't send cyrilic, files, screens.Neither in meebo.

So MSN it is.

Anyways, cdenley thank you.That really helped.

And like the teacher's will install that for me...

But yeah, this can be locked now.

Thanks again for your help.

---

### Post by mikewhatever on 2009-09-04
> **Steam. said:**
> Edubuntu, at school.

Add/Remove doesn't work without a pass.

So without a pass, no MSN.

We can't help you circumvent the school's security policies, don't ask again.[-X

---

### Post by aysiu on 2009-09-04
> **mikewhatever said:**
> We can't help you circumvent the school's security policies, don't ask again.[-X
Agreed.

---

