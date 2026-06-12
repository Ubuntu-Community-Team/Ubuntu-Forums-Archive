---
title: "server planning - Authentication question"
date: 2011-03-12
forum: Server Platforms
---

### Post by joepotter on 2011-03-12
Hello all, a little help please.

We are a small private school and we have about 30 computers running Ubuntu. We use a common account on all computers at present. I want to move to having about 50 of the students having their own account name and password with which they could be sitting at any computer. 

We presently have a server to share Internet and to filter content. So, we need to add a file server to serve the students and we need centralized account info. 

What is the best route to take? I hope to keep it simple. 

Any ideas would be appreciated.

---

### Post by SeijiSensei on 2011-03-12
The simplest approach would be using [NIS]("https://help.ubuntu.com/community/SettingUpNISHowTo") for authentication and [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") to share files and directories.

If you need to support Windows computers, you'd need to add Samba to the mix.  In a *nix-only environments NIS/NFS has been widely used for decades.

---

### Post by joepotter on 2011-03-13
> **SeijiSensei said:**
> The simplest approach would be using [NIS]("https://help.ubuntu.com/community/SettingUpNISHowTo") for authentication and [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") to share files and directories.


As I understand this, NFS would serve the files to those that log in properly on a client Ubuntu box and would yield that user his/her home directory and so the child would look at their "own desktop" from any computer that they could log on to.

The ability to log on would come from NIS. Would I only have to make a user account on the server box and this would then pass all account information to the client boxed upon log in?

If I do understand the above correctly, that sounds like the first step we would like to take. (Samba later) 

Does anyone know of a good step-by-step how-to on this issue? One that is up to date, hopefully.

---

### Post by SeijiSensei on 2011-03-13
The last time I set up NIS was quite a few years ago now, and I used the [NIS HOWTO]("http://tldp.org/HOWTO/NIS-HOWTO/index.html").  Another good source is [this book from O'Reilly]("http://oreilly.com/catalog/9781565925106/").  

You probably won't find much about NIS beyond 2005 or so, but the software hasn't really changed much in over a decade.  All the cool kids these days use LDAP, I guess.  Personally I've found setting up OpenLDAP so mind-boggling that I've tried and given up on several occasions.

---

### Post by joepotter on 2011-03-15
> **SeijiSensei said:**
> 
... All the cool kids these days use LDAP, I guess.  Personally I've found setting up OpenLDAP so mind-boggling that I've tried and given up on several occasions.

Hey, **thanks** for all the input. I am going to set up the box using NIS and NFS as you recommend. I would like to try LDAP someday as a test but I can not find any tutorials that show how to just get authentication going for a small lab. Seems like someone would have done that.

---

