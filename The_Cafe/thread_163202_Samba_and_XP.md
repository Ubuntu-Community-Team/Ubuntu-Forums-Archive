---
title: "Samba and XP"
date: 2006-04-20
forum: The Cafe
---

### Post by prizrak on 2006-04-20
This is not a request for help as I'd like to figure it out on my own ;)
My question is have any of you had issues with connecting to Samba shares from your Ubuntu machine to Windows XP Pro machines. Basically no matter how I log in and what permissions I get to the shares I do not have the "write" permission to them. Even if I log in with my own username that is explicitly allowed full control to every single file in that folder.
I'm wondering because I had the issue with my laptop (running Breezy) when dealing with SMB shares on two different XP machines one of which used to work just fine and I changed nothing. My only guess is the latest Windows patches might have broken that as I have not updated SMB on my Ubuntu.

---

### Post by Robgould on 2006-04-20
It works for me.  In your fstab line indicate the rights you want to have to the share.

---

### Post by prizrak on 2006-04-20
[QUOTE=Robgould]It works for me.  In your fstab line indicate the rights you want to have to the share.[/QUOTE]
I'll try but that's the thing I changed nothing so was wondering if it's my personal problem.

---

