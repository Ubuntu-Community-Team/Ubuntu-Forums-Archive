---
title: "Ubuntu Server 11.10 Joined to Active Directory with LikeWise-Open"
date: 2012-04-17
forum: Server Platforms
---

### Post by ptyo on 2012-04-17
Okay I am new to linux and have setup a Ubuntu Server 11.10 with samba and joined to our active directory domain with likewise-open, however I am unable to access a share i created with my domain credentials. If i run the command: ```
lw-enum-users
```
I get a listing of all the active directory users.
 
I found the below article that would appear to be rather old: [HTML]http://chrplunk.blogspot.com/2008/06/allow-windows-clients-in-active.html#!/2008/06/allow-windows-clients-in-active.html[/HTML]
 
I have been cruising the forums for days and have come across a vast amount of information, but nothing would seem to be current. I have seen where some people use windbind? 
 
I would greatlly appreciate it if someone could point me to a link that would walk through and explain what I need to do so I can setup a share with samba and let windows active directory check allowed credentials. Not that it should matter but my Ubuntu Server 11.10 with samba is setup on a Ubuntu Server 11.10 running KVM.
 
I have been succesful in the past using the internet and forums to research issues, but this one I am running into all kinds of road blocks and my linux understanding is greatly lacking and I just seem to be shooting in the dark getting a long way to no where and not understanding the code changes I am making. 
 
Thanks in advance for any help.

---

### Post by ptyo on 2012-04-18
There is no interest from anybody in creating a how-to on Samba and Active Directory Integration so you can use Active Directory Users / Groups to give permissions to Samba shares?

---

### Post by telecomando on 2012-04-25
I'm right there with you. All the documentation is a bit out dated even the docs provided by likewise/Beyond Trust.

Looking for help with a similar situation and there is nothing current out there.

---

### Post by D8TA on 2012-05-31
May not help now but I am using Centrify with their Centrify Samba version and all is working flawless with no changes. You might want to try that.

---

