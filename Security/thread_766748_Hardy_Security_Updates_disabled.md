---
title: "Hardy Security Updates disabled"
date: 2008-04-25
forum: Security
---

### Post by Bachstudies on 2008-04-25
Has anyone else found that Hardy 'security upates' is unticked by default after installation? Only 'recommended updates' is ticked. I did install via wubi but i doubt this would make a difference.

---

### Post by FredB on 2008-04-25
Could be a problem related to servers being overwhelmed. No problem here.

---

### Post by Oldsoldier2003 on 2008-04-25
> **FredB said:**
> Could be a problem related to servers being overwhelmed. No problem here.

+1 if you fail in connection attempts repeatedly the repo will be commented out in your sources.list

to the OP: just edit /etc/apt/sources.list and uncomment the lines and try again later. you might also want to try a different server setting in software sources, or choose the option that allows synaptic to chose the best server for you.

---

### Post by Bachstudies on 2008-04-25
Thanks for the replies - having looked at my source list, the security repos were commented out several times. After deleting the source list and selecting options again everything is working as it should.

---

### Post by windows-killer on 2008-04-28
I had the same problem and the mistake was found on my software sources. chek your server type and make sure its on main server not your local server.

---

### Post by FredB on 2008-04-28
Or another local server ;)

Just use synaptic server chooser, it could help ;)

---

### Post by Chareos on 2008-07-27
I'm having this very problem right now... and these are not commented in the file.

Any suggestion ?

---

### Post by Stunts on 2008-07-28
It's happened here too.
I think it was related to having backports enabled.
A bug has allready been filed in launchpad, tough I don't know the status right now...

---

