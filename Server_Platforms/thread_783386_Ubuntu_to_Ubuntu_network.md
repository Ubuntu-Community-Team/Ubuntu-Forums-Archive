---
title: "Ubuntu to Ubuntu network?"
date: 2008-05-05
forum: Server Platforms
---

### Post by joplass on 2008-05-05
If you have to have a network of Linux to Linux machines, Ubuntu to Debian machines would you use Samba?  
I am using samba because I have one windows box, one debian box, and one Ubuntu notebook.  The windows box has no issues connecting to the Linux machines but both Linux machines are not playing nice with each other.  I see the other machine's home but I get the message "can't mount home" when trying to access it.
Any idea?
Thank you,

---

### Post by chewearn on 2008-05-06
I would prefer to use NFS if there are only linux involved.

---

### Post by Archmage on 2008-05-06
> **joplass said:**
> I see the other machine's home but I get the message "can't mount home" when trying to access it.
Any idea?

Wild guess: If you want to mount the home-partition of another machine you need to mount it on a different place than your own home folder and use this mount-point.

But honestly Samba isn't a good idea for Linux to Linux-connections, but it should still work.

---

### Post by DrNick on 2008-05-06
> **AstalaVista said:**
> I would prefer to use NFS if there are only linux involved.

Ew, NFS *shudder*

Does anyone ever use that for new installations anymore??  CIFS/Samba might be ugly, but at least it has some security and doesn't require NIS.

My advice - stick with samba.

---

### Post by joplass on 2008-05-06
> **Archmage said:**
> Wild guess: If you want to mount the home-partition of another machine you need to mount it on a different place than your own home folder and use this mount-point.

But honestly Samba isn't a good idea for Linux to Linux-connections, but it should still work.
Now I am curious.
When you navigate your network I believe you don't mount in /home.  If you don't, and I could be wrong, how do you tell samba not to mount in /home?

---

### Post by Archmage on 2008-05-07
> **DrNick said:**
> CIFS/Samba might be ugly, but at least it has some security and doesn't require NIS.

You can install NFS without NIS, but than the only secruity is over the IP-adresse. But that work if you only use it in your network.


> **joplass said:**
> Now I am curious.
When you navigate your network I believe you don't mount in /home.  If you don't, and I could be wrong, how do you tell samba not to mount in /home?

I got the impression that he wasn't navigating over my computer and try to mount the sambe folder directly on the /home directly.

---

### Post by hyper_ch on 2008-05-07
for remote networks you can use sshfs

---

