---
title: "Allowing users to add themselves."
date: 2008-03-22
forum: Server Platforms
---

### Post by SuperTeece on 2008-03-22
Hi,

I've done some searching here and on google but am not finding what I'm looking for.

I'm setting up a 7.10 server and plan on allowing some of my classmates use it to practice ssh, telnet, and other remote activities. My question is on how to allow them to log in using a guest/generic account and then create their own un/pw combo. I don't even mind if they have root access, seeing as how this is an admin class.

Thanks,

TC

---

### Post by ubernoob on 2008-03-22
Why not just give them the password for the root account? That would be the same.
then they can add more accounts as they like. Alternativly, you can make a new account and add it to the sudoers list.

Or am i misunderstanding the question?

---

### Post by SuperTeece on 2008-03-22
Sounds pretty simple. I can make a sudoer account and post that in the class boards. They log in and make their own account with that.

Much easier than I thought it would be.

---

### Post by ubernoob on 2008-03-22
yupp. but within a week, your class mates would probably trash your machine, so you will have to reinstall it all. ;)

---

### Post by SuperTeece on 2008-03-22
That is what it is there for.

BTW, I made an account, guest. Set the password, but it fails to log in. When I type the UN/PW remotely using putty, it doesn't return the pw prompt, putty just closes. When I try on the server, I get the Ubuntu disclaimer and it returns me to the login prompt. Any ideas?

Ohh, my main account works just fine.

---

### Post by SuperTeece on 2008-03-22
Never mind.

I was using adduser --system -gid 0 {username}

I took out --system and all is well.

---

