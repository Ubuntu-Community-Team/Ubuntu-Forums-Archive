---
title: "Noob server question...Cannot Sudo?"
date: 2010-01-31
forum: Server Platforms
---

### Post by Tdonohue on 2010-01-31
I'm almost embarrassed to ask this because the answer has to be right in front of my face.

I just installed Gutsy server.  It is the only  disk i can get to boot on this old PC trying to salvage.  I'm at the "SERVER LOGIN" prompt.

I created one user during the install.  I can login as that user, but that user has "...IS NOT IN THE SUDOERSFILE."

How do I setup this user to be in the sudoers file, without having any  ability to make changes to the system?

I am really at wits end here and I've been staring at this screen for days.  I can't find any threads that have a solution which leads me to believe I'm the only one in the world who hasn't figured this out.

---

### Post by milton1 on 2010-01-31
Can you boot to recovery mode? That should give you root access to the system.

---

### Post by wojox on 2010-01-31
> **milton1 said:**
> Can you boot to recovery mode? That should give you root access to the system.

That'll work

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Tdonohue on 2010-01-31
> **milton1 said:**
> Can you boot to recovery mode? That should give you root access to the system.



Yep, that worked.  I knew it was right there too.


I'm playing around with adding myself to the sudo group.

"useradd -G sudo tim" is not working.  I'll keep looking for ways to do this.  if you can help me with that too, you'd be my hero today...

---

### Post by milton1 on 2010-01-31
any user in the admin group should have sudo rights. try:
```
sudo adduser <yourname> admin
```

---

### Post by Tdonohue on 2010-01-31
> **milton1 said:**
> any user in the admin group should have sudo rights. try:
```
sudo adduser <yourname> admin
```


That actually didn't work (No admin group!!??)

visudo, and adding myself to the bottom worked.

Thanks to everyone for responding so quickly.

---

