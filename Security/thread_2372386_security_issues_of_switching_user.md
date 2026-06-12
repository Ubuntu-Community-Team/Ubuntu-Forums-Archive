---
title: "security issues of switching user"
date: 2017-09-24
forum: Security
---

### Post by Peter_Brandon on 2017-09-24
I use my admin account for general purpose safe uses, but also have another non-admin user where I visit more dangerous websites.  Sometimes I need to switch back and forth between my admin and non-admin account using ctrl-alt F7 and F8 (say I need to do some admin things or am waiting for software to download etc. on on the non-admin acct).  The first time I switch from my non-admin user on F8 to my admin user on F7, I'm asked for a password.  Subsequently, no password is required.  I'm worried that that means that any malicious software in my non-admin account could easily access my admin account and / or also get admin privileges.  Is this concern realistic?

---

### Post by Peter_Brandon on 2017-09-24
PS I don't think the access issue is any different if I use the GUI rather than ctrl-alt F7/F8.  Either way, once I give my admin password, I can subsequently ctr-alt switch to that user w/o a password.

---

### Post by deadflowr on 2017-09-24
> Is this concern realistic?
In this particular case, no.
Logging in and authenticating for elevated rights are different things.
Just because you'v established two separate users can log in, does not grant elevated rights to do anything system related.
You still need to invoke the admin's password to make system changes.

Worst case is that a non-admin can now muddle around with the files and folders in the admin's home directory.
And vice versa.

---

### Post by Peter_Brandon on 2017-09-24
Thanks!  I think that answers the question, though it raises some as well.

It's still a big concern for me because one of the purposes of the non-admin account is that I be anonymous.  Anyone with access to my admin account files (or likely even just file names) could figure out who I am.  

It seems like a security flaw that Ubuntu (sddm or lightdm?--not sure which my system is using; both installed) allows switching without a password.

I don't suppose password-less switching can be turned off somehow?

---

### Post by HermanAB on 2017-09-26
You are not anonymous when you connect to something on a net.  The connection is a two way street.

---

