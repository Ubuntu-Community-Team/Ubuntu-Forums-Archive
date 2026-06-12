---
title: "Unable to log in with Root account after new install"
date: 2010-01-11
forum: Server Platforms
---

### Post by cmccullough on 2010-01-11
This may sound a bit odd, but after installing Ubuntu Server 9.10 64-bit version, I can't seem to log in with the root account that I created.  My user account works fine.  I thought that I may have fat fingered the password when I created it so I ran the installer again since it takes very little time to do so.  When creating the new root account password, I was very careful to type it correctly.  After the install was complete, I am still unable to use the root account.  I'm unable to SU from my normal user account, too.  I just receive the Login incorrect error.

Is there something with using root accounts with Ubuntu server that I'm missing?

Thanks for your help.

---

### Post by slakkie on 2010-01-11
Have a look at the rootsudo documentation on the wiki. 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by HighCommander540 on 2010-01-11
> **cmccullough said:**
> This may sound a bit odd, but after installing Ubuntu Server 9.10 64-bit version, I can't seem to log in with the root account that I created.  My user account works fine.  I thought that I may have fat fingered the password when I created it so I ran the installer again since it takes very little time to do so.  When creating the new root account password, I was very careful to type it correctly.  After the install was complete, I am still unable to use the root account.  I'm unable to SU from my normal user account, too.  I just receive the Login incorrect error.

Is there something with using root accounts with Ubuntu server that I'm missing?

Thanks for your help.

The link cmccullough posted will tell you everything, but to put it simply. Ubuntu doesn't allow root access by default. It is more secure. What you need to do if you want to run a command with root privileges is type "sudo" then the command and it will ask you for your password. Sudo is kinda of like su, but on a one at a time basis, because it can also make you act as a nother user other than root.

---

### Post by cmccullough on 2010-01-11
aaahhhh.....thanks.  it's a little different with ubuntu server than with the normal desktop version.

thanks for the info!

---

### Post by slakkie on 2010-01-11
> **HighCommander540 said:**
> The link [s]cmccullough[/s] slakkie posted will tell you everything

That's better.

---

### Post by cmccullough on 2010-01-11
yep!  the link i was given explains it all.  running as root is always a bit dangerous and i can see how it would be even more dangerous on a server.  i've been using linux for a little more than 12 years (microsoft-free for more than 10 years), now, but this is my first adventure on the server side.  was able to purchase a Dell PowerEdge server on the Dell site from their "discount" page.  this should be a very nice learning experience.

thanks for the help!

---

### Post by HighCommander540 on 2010-01-11
> **cmccullough said:**
> aaahhhh.....thanks.  it's a little different with ubuntu server than with the normal desktop version.

thanks for the info!

Actually, it is exactly the same.

> **slakkie said:**
> That's better.

Lol, my bad.

---

### Post by cmccullough on 2010-01-29
Sorry.  What I meant by saying that it's different than the desktop version is that under the desktop version, it allows for using SU.

Sorry about the confusion.

---

### Post by llawwehttam on 2010-01-29
> **cmccullough said:**
> Sorry.  What I meant by saying that it's different than the desktop version is that under the desktop version, it allows for using SU.

Sorry about the confusion.

err no. Ubuntu desktop does not let you su to root unless you have unlocked the root account.

It may have been different in older versions of ubuntu, I came over from fedora at about Dapper 6.06 ( it think)

---

