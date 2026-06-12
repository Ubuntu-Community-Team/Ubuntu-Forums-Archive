---
title: "LDAP is crazy too difficult, to impossible"
date: 2010-01-10
forum: The Cafe
---

### Post by frenchn00b on 2010-01-10
[http://www.openldap.org/doc/admin24/quickstart.html](http://www.openldap.org/doc/admin24/quickstart.html)

Give a try to make a server for samba and your users :) good luck

I do not understand why linux tolerate this : [here]("http://yellowprotoss.ye.funpic.org/website/ubuntu_installing_ldap/linux_ldap_frenchn00b.gif")

---

### Post by steveneddy on 2010-01-10
Do not start multiple threads about the same subject.

---

### Post by the yawner on 2010-01-10
What was your stumbling block? I found it a little bit complex to absorb in just one sitting when I was trying to build a mail server. But with patience I was able to create a webmail server with LDAP as an authentication/address book back end.

---

### Post by frenchn00b on 2010-01-11
> **the yawner said:**
> What was your stumbling block? I found it a little bit complex to absorb in just one sitting when I was trying to build a mail server. But with patience I was able to create a webmail server with LDAP as an authentication/address book back end.

wow, really?  I can even not add a single user or account :(
Could you please (if you have little time) post a tar.gz of the most relevant folders of a basic installation /etc/ldap (with removing the password) ... ?

---

### Post by coutts99 on 2010-01-11
I've had samba/ldap working for a few years now, it's not that difficult really, just do a LOT of reading

---

### Post by SciFi-Bob on 2011-06-24
I know this is an old thread, but still, some poor victims may come by and read this.

> **coutts99 said:**
> I've had samba/ldap working for a few years now, it's not that difficult really, just do a LOT of reading

Why do I have to do a LOT of reading?

I successfully got a ldap server up and running with no fuzz a couple of years ago, but after they decided to abandon the slapd.conf, and replace it with a ldap like file system, which no one is ever gonna figure out without dreaming ldap in their sleep, this is a killer for new users.

It is impossible for a newbie to install slapd, and populate it with useful data, so what do they want? Do they want all of the worlds citizens to learn their weird ldap language?

Dream on, people want it easy, therefore they walk over to Microsoft, a supplier which is delivering the kind of functionality that people want.

Please, get a grip on reality, and develop some kind of user friendly interface to the backend.
Or get lost. Yeah, that's where you are heading if you don't get a grip on the gui.

Right now I really HATE ldap, but I need it. My only other alternative is Windows (because I know Active Directory).
It's getting more and more tempting..

Yes, I know, this is like talking to a wall. These people does not want anyone to change their way of programming.

I just know this: If I install slapd on my Maverick server, I't useless.
There is no way that I can (in a user friendly way) add any admin accounts to the root, because THERE IS NO ROOT!
The morons have decided that it is time to install a defunct version, with no data.

That is just what I wanted. A braindead ldap server..

---

### Post by Thewhistlingwind on 2011-06-24
> **SciFi-Bob said:**
> I know this is an old thread, but still, some poor victims may come by and read this.

**Okay, that's acceptable.**


Dream on, people want it easy, therefore they walk over to Microsoft, a supplier which is delivering the kind of functionality that people want.

**I've never used active directory or LDAP, I don't even know what they're for. (Or at least, didn't until I searched wiki.) **

Please, get a grip on reality, and develop some kind of user friendly interface to the backend.
Or get lost. Yeah, that's where you are heading if you don't get a grip on the gui.

***shrug* **

Right now I really HATE ldap, but I need it. My only other alternative is Windows (because I know Active Directory).
It's getting more and more tempting..

**Okay**

That is just what I wanted. A braindead ldap server..

I don't know why people tolerate it, they just do. Ranting on Ubuntu forums won't change it, and your post isn't helping anyone.

---

### Post by SciFi-Bob on 2011-06-24
> **Thewhistlingwind said:**
> I don't know why people tolerate it, they just do. Ranting on Ubuntu forums won't change it, and your post isn't helping anyone.

I know, and I already regret ranting here, it just made me feel a lot better..
But I really think it will help, at least when people like me searches for a reason that ldap is not the world savior.

On the bright side: When I find a solution, I will post it here.

---

### Post by Thewhistlingwind on 2011-06-24
> **SciFi-Bob said:**
> 

On the bright side: When I find a solution, I will post it here.

Write a GTK/tkinter/etc application front end for it after you've trudged through hell?

---

### Post by SciFi-Bob on 2011-06-24
> **Thewhistlingwind said:**
> Write a GTK/tkinter/etc application front end for it after you've trudged through hell?

Nope, but maybe after I find a phpldapadmin solution.. I will try..

---

### Post by coutts99 on 2011-06-25
> **SciFi-Bob said:**
> I know this is an old thread, but still, some poor victims may come by and read this.

I posted that over a year ago, when I had been successfully using Samba/LDAP for a few years, and at that time it wasn't too difficult.

I haven't touched it for ages now, maybe things have changed.

I might try a install later on and see.

---

### Post by coutts99 on 2011-06-25
> **SciFi-Bob said:**
> I successfully got a ldap server up and running with no fuzz a couple of years ago, but after they decided to abandon the slapd.conf, and replace it with a ldap like file system, which no one is ever gonna figure out without dreaming ldap in their sleep, this is a killer for new users.

This [http://www.openldap.org/doc/admin24/quickstart.html](http://www.openldap.org/doc/admin24/quickstart.html) still appears to referenece slapd.conf

*EDIT*

Just installed on Natty, urrghh, yes the LDAP directory, is this an Ubuntu only thing?

The slapd binary still accepts -f for the config file.

---

### Post by coutts99 on 2011-06-25
> **SciFi-Bob said:**
> Please, get a grip on reality, and develop some kind of user friendly interface to the backend.
Or get lost. Yeah, that's where you are heading if you don't get a grip on the gui.

I used this successfully for years [http://phpldapadmin.sourceforge.net/wiki/index.php/Main_Page](http://phpldapadmin.sourceforge.net/wiki/index.php/Main_Page)

---

### Post by slooksterpsv on 2011-06-25
I set up an LDAP Server and a LDAP Client for Logins pretty much within 45 min. The longest part was installing the OS on the VMs hehe. Other than that, I've also setup an LDAP Server with NFS Home Directories, that was awesome =D

---

### Post by szymon_g on 2011-06-25
> **SciFi-Bob said:**
> 
Right now I really HATE ldap, but I need it. My only other alternative is Windows (because I know Active Directory).

use eDirectory or Directory Server from Red Hat

---

