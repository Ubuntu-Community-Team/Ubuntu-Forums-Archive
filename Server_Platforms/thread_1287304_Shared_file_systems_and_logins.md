---
title: "Shared file systems and logins?"
date: 2009-10-10
forum: Server Platforms
---

### Post by DejitaruJin on 2009-10-10
Okay, I've done everything I possibly can to crush, destroy, and otherwise obliterate any sort of security measures on my Samba file server that could potentially prevent anyone from doing anything they please to any shared file. However, every once in a while, there are still permission issues. Rather than waste any further time hacking away at whatever still stands in my way, I want to try to use file permissions to my advantage.

I still want all of my Windows machines to maintain their current guest logon capabilities. There is no domain here, and certainly no network login system, and I won't be making one. But on my Linux desktop - my main system - instead of just accessing files as a guest (the "nobody" account), I want it to actually log in as the main user on the server. You know how SSH asks for the login, and then everything you do is done *as* the user you just logged in as? *Exactly* like that.

The problem is, I'm not sure exactly how to go about doing that. I'm fairly certain I need to use Samba, because NFS uses more advanced networking that I won't deal with here. I specifically need whatever I use to actually be accessing the main user account on the server, not some custom login settings made just for file sharing. Now how the heck do I do that?

---

### Post by kevin11951 on 2009-10-10
> **DejitaruJin said:**
> Okay, I've done everything I possibly can to crush, destroy, and otherwise obliterate any sort of security measures on my Samba file server that could potentially prevent anyone from doing anything they please to any shared file. However, every once in a while, there are still permission issues. Rather than waste any further time hacking away at whatever still stands in my way, I want to try to use file permissions to my advantage.

I still want all of my Windows machines to maintain their current guest logon capabilities. There is no domain here, and certainly no network login system, and I won't be making one. But on my Linux desktop - my main system - instead of just accessing files as a guest (the "nobody" account), I want it to actually log in as the main user on the server. You know how SSH asks for the login, and then everything you do is done *as* the user you just logged in as? *Exactly* like that.

The problem is, I'm not sure exactly how to go about doing that. I'm fairly certain I need to use Samba, because NFS uses more advanced networking that I won't deal with here. I specifically need whatever I use to actually be accessing the main user account on the server, not some custom login settings made just for file sharing. Now how the heck do I do that?

You could actually use ssh if you wanted to, there is a program called sshfs, works like ssh, but lets you mount folders using it.  It can also be used with fstab.

---

### Post by DejitaruJin on 2009-10-10
Oh really now... Hmm, I did not know that. That may very well be precisely what I was looking for. Thanks for the tip!

---

