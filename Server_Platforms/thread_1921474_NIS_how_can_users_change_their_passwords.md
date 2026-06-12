---
title: "NIS how can users change their passwords?"
date: 2012-02-06
forum: Server Platforms
---

### Post by meadmarc on 2012-02-06
Hello!

I just successfully set up a NIS server this weekend; users can log in to a client workstation through the NIS server, which maps their home directory.

All was well, until I was testing my users.  To test a few, I changed their passwords.  Tried to log in.  Couldn't on the clients.  I had to update the yellowpages database with:

make -C /var/yp 

So that got me in as a user, but when I tried to change the password from the client, it was impossible.  

Apparently, there is a yppasswdd dameon that should run, but I cannot find this in the repositories.  

Has it changed?  

How do I allow my users to change their passwords?

Is there a way for me to change their passwords without having to do this:  make -C /var/yp 

Thanks!

---

### Post by meadmarc on 2012-02-09
bump!

---

### Post by Azdour on 2012-02-10
Hi,

I also use NIS and to the best of my knowledge you can only change the password directly on the NIS server itself either throught the yppasswd command or combination of 'passwd' and 'make -c /vav/yp', see:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch30_:_Configuring_NIS#Users_Changing_Their_Own_Passwords](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch30_:_Configuring_NIS#Users_Changing_Their_Own_Passwords)

---

### Post by meadmarc on 2012-02-10
Fantastic link, many thanks!

Most of my experience has been on the, uh...  Windows side with Active Directory, and with Ubuntu LTSP Thin Clients, either of which allow client side password changes.  I though that I had mis-configured something.  But apparently, users cannot change their own passwords by design?

It also appears that, now that I have NIS working, that many are abandoning it in favor of LDAP.  Is this the case?  Should I take a look at that?

It's for a small Christian school, only about 60 users, maybe 40 workstations, little concern for security, to be honest.  Just not much to protect!

---

### Post by SeijiSensei on 2012-02-12
If NIS works for you, why change?  I've never had much success dealing with the arcana of LDAP myself.  I think it's overkill if all you want to do is password authentication.

If you're considering options, you might take a look at [RADIUS]("http://packages.ubuntu.com/lucid/freeradius") as well.  It's probably also overkill for your application, though.

---

### Post by meadmarc on 2012-02-12
Ldap would be nice, if we ever went with a mixed environment (right now, only the library computer is running windows for software reasons.)  But I agree- NIS is doing the job very nicely, and if NIS is happy, and the users are happy; well, then I am happy too!

---

