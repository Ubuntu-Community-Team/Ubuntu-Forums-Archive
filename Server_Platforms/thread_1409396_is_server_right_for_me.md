---
title: "is server right for me?"
date: 2010-02-17
forum: Server Platforms
---

### Post by dbowlin17 on 2010-02-17
I want to be able to share folders files and print between multiple computers. I understand that my wireless network could do that, but I want to be able to connect to the files and printers when I am away from my home network. I want it to be a domain based network where I can sign into something and get access to my files... is this what I want to use to accomplish this? Also, Would I be able to have my each computers hard drive ( desktop and laptop) be accessable? I would like to have access to my desktop files. should I just put small (120 or less) hard drives in the computers and have a larger hard drive in the server for storage of all personal data...?

---

### Post by kamaji792 on 2010-02-17
> I want to be able to share folders files and print between multiple computers.

This single requirement says server to me.

I am sure a server would allow you to accomplish your other requirements, with the exception of connecting to the hard drives on your other computers.  But if you store all your files on a server do you need to see the hard drives of the other computers?

As for the size of the disk, well you will have to see how much data you need to store and add some head room.  Personally, working in a 5 PC office and at home, I have not got above 40GB.

atb

---

### Post by Iowan on 2010-02-17
Sounds a bit like an [LDAP]("https://help.ubuntu.com/community/OpenLDAPServer") server.

---

### Post by dbowlin17 on 2010-02-17
If i have all data stored on the server I don't need to use the hard drives of each machine for anything but applications, and that would be individual and not accessed remotely. By the 40gb do you mean per computer, or server size? and also, Iowan, would you care to explain the LDAP server a bit more, because I am a n00b-ish

---

### Post by Iowan on 2010-02-17
I began to study LDAP a few years ago - thinking it might be the Linux version of Active Directory (of which I also know almost nothing). I got sidetracked so many times, I don't remember when I got totally confused. 
I also remember considering making my Samba server a Domain Controller... but didn't get far doing that either, but
 did find another [LDAP]("http://books.google.com/books?id=fcW1xl1BejUC&dq=ldap&printsec=frontcover&source=in&hl=en&ei=HLt8S6mHMc2ttgftvYCcBQ&sa=X&oi=book_result&ct=result&resnum=12&ved=0CDAQ6AEwCw#v=onepage&q=&f=false") link that might be useful.

---

### Post by pirateghost on 2010-02-17
e-box, smeserver, or clearos might be an appropriate operating system for this.

---

### Post by tlsarles on 2010-02-18
> **pirateghost said:**
> e-box, smeserver, or clearos might be an appropriate operating system for this.

2nd'ed

---

### Post by KnottyMars on 2010-02-18
Part of your initial statement mentions being able to connect to the server while you are away from your home network. Just make sure you have your networking square. A static IP would be the best way to ensure you can setup what you want. 

Also when you say a domain environment, in windows land, that usually means a central place to admin permissions and user accounts. Sounds like you just need access to it yourself (and maybe a couple others) if so, a domain like environment might be a little overkill. 

I would say setup samba with a couple users, throw a couple 500GB drives (or more) in the server and share out some space. I have a similar setup, but just LAN access for movies, music and other files. I use one set of credentials for everything so I dont get confused. 

Good luck on the setup. A network based mass of storage is a nice thing.

---

### Post by joberly on 2010-02-18
You don't need a full LDAP setup just to store some data and access it from multiple computers. Keep it simple! No need to do any extra work that isn't required. Save the enterprise stuff for the enterprise. 

For the remote stuff, what are you trying to access AWAY from your local network? That will give a clearer picture for the implementation of that specific need.

As far as the local network is concerned, you can setup simple SMB/CIFS shares and have them mount automatically on the computers that require access. Simple. You don't even NEED a DNS server running....unless you want to create your own domain just to play with.

If you want to get full blown remote/roaming profiles with user /home data stored remotely and do network logins, you can do that. However, it's a LOT more work, and doesn't seem like you need such a thing based on your requirements. You can access all files on your home network, while you are away, through a few different methods. But what do you need to access? That will help determine your needs.

For example, you can do a lot of things over SSH, and it's very secure when setup properly.

---

### Post by dbowlin17 on 2010-02-19
I just want to access documents and music. personal files. thats all.

---

### Post by kamaji792 on 2010-02-20
> **dbowlin17 said:**
> If i have all data stored on the server I don't need to use the hard drives of each machine for anything but applications, and that would be individual and not accessed remotely. By the 40gb do you mean per computer, or server size? and also, Iowan, would you care to explain the LDAP server a bit more, because I am a n00b-ish

By 40BG I mean my home server runs under 40GB.  Now I think about it my work server runs at over 40GB  but less than 80GB.

Just look at the data you need to store.  The only thing I have that uses up disk space is my record collection (6.5GB) and my photo collection (12GB).  The rest of my data fits in under 2GB.

Looking at the other posts in this thread I think you just need a basic SAMBA server.  LDAP I think would be over the top.

I use the Ubuntu server 8.04lts and I like the Ubuntu server guide [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

atb

---

