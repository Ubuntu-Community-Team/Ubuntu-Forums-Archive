---
title: "Can you Add Ubuntu Desktop to a Windows Domain?"
date: 2007-03-22
forum: Utah Team - US
---

### Post by Andrew Roybal on 2007-03-22
Can you add Ubuntu Desktop to a Windows Domain environment? If there is any Documentation please lead the way. 

Thanks 

BlueScreen.

---

### Post by sontek on 2007-03-22
Yes you can.  

Heres something to get you started:

[http://developer.novell.com/wiki/index.php/HOWTO:_Configure_Ubuntu_for_Active_Directory_Authentication](http://developer.novell.com/wiki/index.php/HOWTO:_Configure_Ubuntu_for_Active_Directory_Authentication)

But you just need to look into Kerberos, Samba, and OpenLDAP to get everything running

---

### Post by Andrew Roybal on 2007-03-23
Hey thanks a million Sontek... this is awesome. we we.

:).

---

### Post by snowpalmer on 2007-03-24
They really need to work on making this process less involved. I added several machines at work to our domain and there is way to much that has to be done to get it going.

---

### Post by mrtrick on 2007-05-17
I agree. It would be cool to have a tool as a part of automatix or something that lets you enter the pertinent information and have it do all the back end work for you. 

Makes me think... could be a fun project. I just want to make sure that I'm not re-inventing the wheel if someone else has done this already and we just don't know about it.

---

### Post by MWPatterson on 2007-05-29
Has any body found or got a tool to do this yet?  We are looking at rolling out about 400 machines on our AD Domain and this is the kicker.  Our people that set up the machines know windows and it will take some time to get all of them to understand and use Ubuntu.  This is a big deciding factor for us, if we have to go through alot of manual editing it will be a no go for Ubuntu for mainstream and only a few play boxes then.

---

### Post by Kemotaha on 2007-05-31
It actually isn't that bad.  Apart from the config where you need to make some changes you can do pretty much everything you need to from a script.  The join command is "net rpc join domainname" I believe.  I would have to look a little further to see if there is already a script.  

Nathan

---

### Post by peanut butter on 2007-06-04
> **Kemotaha said:**
> It actually isn't that bad.  Apart from the config where you need to make some changes you can do pretty much everything you need to from a script.  The join command is "net rpc join domainname" I believe.  I would have to look a little further to see if there is already a script.  

Nathan

dont you need to edit some pam config files too?

---

### Post by Kemotaha on 2007-06-05
Yeah, you have to add winbind to them.  You also have to add it to the nsswitch file as well.  Winbind is the daemon that does the AD authentication.  Of course it uses the smb.conf like smb and nmb.

---

### Post by peanut butter on 2007-06-06
how do i add winbind to these files?

---

### Post by Kemotaha on 2007-06-07
> **peanut butter said:**
> how do i add winbind to these files?

Here is a good link on Winbind: [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html)

I won't quote it all because it is fairly long, but the bottom part of the document has a whole setup to get winbind to authenticate with PAM.

---

### Post by steve_d on 2009-07-31
Stumbled across this thread in my searches, thought I'd update it:

Likewise open

Check out this link:

[http://www.ubuntugeek.com/how-to-add-ubuntu-804-to-win-server-2003-active-directory-domain.html]("http://www.ubuntugeek.com/how-to-add-ubuntu-804-to-win-server-2003-active-directory-domain.html")

Steve

---

### Post by GinnyBhullar on 2011-01-22
I am already using Likewise-open for Domain Integration. But the problem is it supports only one domain at a time to join. What if I want to make my machine to join 2 domains. What is required to be done ?

---

### Post by atworkwithjf on 2011-02-16
Why would you put yourself through this when you can just use likewise-open to join your machine to AD?

Likewise-Open is in the ubuntu-main repository so all you have to do is install it with apt-get or the synaptic package manager and then join the domain.

---

