---
title: "SWAT Setup"
date: 2007-10-30
forum: Server Platforms
---

### Post by kpmaddenuk on 2007-10-30
I'm used to using SWAT to set up SAMBA in other distros but when I use it in Ubuntu I don't get the facility to access any settings. I only get "Home " "Password" and "View".

I could amend the smb.conf manually but as I haven't done this for years I'd be happier using SWAT as it's (almost) foolproof.

Can anyone tell me how to get my settings back in SWAT?

TIA - K

---

### Post by jacksonz123z on 2007-11-05
I think you need to log in as root?  Set up a root password with sudo passwd root.

---

### Post by kpmaddenuk on 2007-11-06
Thanks I'll give that a go. I didn't realise that you could set up a root password. In fact, my main issue with Ubuntu is that it doesn't allow you to log in as root. I'm a big boy now and I know what I'm doing so let me be root and not have to put sudo at the start of every line. *rant over*

I've actually set it up using vi to change the smb.conf file but SWAT is much easier.

Cheers - K

---

### Post by jacksonz123z on 2007-11-08
Yes, I used to miss root login!  If you set your root password then go to Admin>Login Window>Security and select Local system admin login you can have it all!  I like SWAT too!

---

