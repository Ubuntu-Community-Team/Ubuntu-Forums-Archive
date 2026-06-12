---
title: "Ubuntu Server on Windows Domain"
date: 2009-10-22
forum: Server Platforms
---

### Post by jordanjae on 2009-10-22
I am a tech aide at the high school I am going to and we are setping up a Ubuntu 9.0.4 server on our current domain, we already have a Windows server setup and its on a domain, but I need to learn how to setup a Ubuntu server (which I know how to do) but it needs to be able to login to the windows server from linux computers. 
 
If that makes no since here is what needs to happen. 
 
A student at the school needs to be able to use the same login they would for the Window computers for a Linux computer, with all their files there. So if they saved something to the windows server they need to be able to access it on the linux one as well. 
 
And they have to be on the same domain. So I need to know how to setup an Ubuntu 9.0.4 server, with access to the Windows XP server... Any links to guides, tips, or anything else you can offer would be great. 
 
<snip>

---

### Post by jordanjae on 2009-10-22
I am a tech aide at the high school I am going to and we are seting up a Ubuntu 9.0.4 server on our current domain, we already have a Windows server setup and its on a domain, but I need to learn how to setup a Ubuntu server (which I know how to do) but it needs to be able to login to the windows server from linux computers. 

If that makes no since here is what needs to happen. 

A student at the school needs to be able to use the same login they would for the Window computers for a Linux computer, with all their files there. So if they saved something to the windows server they need to be able to access it on the linux one as well. 

And they have to be on the same domain. So I need to know how to setup an Ubuntu 9.0.4 server, with access to the Windows XP server... Any links to guides, tips, or anything else you can offer would be great. 

<snip>

---

### Post by cariboo on 2009-10-22
please don't double post. I have merged your two threads

---

### Post by ivicks on 2009-10-23
I might be missing something but all you would need to do is setup Samba and add the server to your existing domain. This would allow the students to use their same user account and access all their files, share, and printers.

But like I said I may have misunderstood.

---

### Post by openfly on 2009-10-23
He may mean server authentication... as in ssh to the linux machine and use ad credentials on it.

There's two approaches to that... one is using AD as an LDAP source and that's fairly well documented.  Biggest problem usually is ensuring you have posix user schema in your ad tree.

Other option is to use kerberos authentication from AD.

In this case the best approach is to setup an MIT Kerb5 KDC and then setup a cross realm trust.  There's even a putty version put out by CSS that can handle gssapi auth using AD tokens.  This method is of moderate difficulty.

---

### Post by R.Bucky on 2009-10-24
I joined an AD domain using likewise-open. Not exactly sure what you are looking at accomplishing.

---

