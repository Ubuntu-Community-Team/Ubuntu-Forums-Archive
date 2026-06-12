---
title: "2003 Domain"
date: 2005-10-13
forum: Server Platforms
---

### Post by Ianvn on 2005-10-13
Hi,

We are running a Windows 2003 Domain at our office.
We want to replace our existing Windows 2003 Files server with Ubuntu.

I have been looking at some of the other posts on these forums and trying them out.
Don't know if i am doing something wrong but I just don't get my Ubuntu box "joined" to the domain. 
Is there maybe a step by step guide to setting up a member server ?

Any help would be appreciated.

---

### Post by Glut on 2005-10-14
I assume that you're using SAMBA as the server. You may wish to do a search for this, even outside of ubuntu as SAMBA does not change a great deal between distros.

In some environments you need to use winbind(d) and the older RPC method to join a domain, depending on your windows setup. This was a recent issue that drove someone in my team up the wall.

---

### Post by LordHunter317 on 2005-10-14
What did you try to run?  What's your smb.conf?

---

### Post by bluck on 2005-10-17
[QUOTE=Ianvn]Hi,

We are running a Windows 2003 Domain at our office.
We want to replace our existing Windows 2003 Files server with Ubuntu.

I have been looking at some of the other posts on these forums and trying them out.
Don't know if i am doing something wrong but I just don't get my Ubuntu box "joined" to the domain. 
Is there maybe a step by step guide to setting up a member server ?

Any help would be appreciated.[/QUOTE]

samba is your friend.
read the manuals :)

its fairly straight forward.

---

