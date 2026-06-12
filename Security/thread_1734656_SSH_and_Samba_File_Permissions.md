---
title: "SSH and Samba File Permissions"
date: 2011-04-20
forum: Security
---

### Post by msbealo on 2011-04-20
Hi,

Ok. Simple situation. I have a desktop and a laptop. I have set it up so I can SSH from my laptop to my desktop using a RSA key. Works well.

I also want to share files using samba between my home directories on both computers.

It seems that I can either get ssh working well, or samba. But if I get up SSH and then samba then SSH won't work (bad authorisation on home directory), or if I have ssh working, then samba is in read-only mode. 

Can someone help me get the permissions correct?

Kind regards,

Mark

---

### Post by bodhi.zazen on 2011-04-20
Well, one option would be to use sshfs =)

[http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

Other then that, what file are you sharing and what is the configuration (in samba)?

With samba, do not share your home directory, share a directory within home

ie

/home/your_user/share or /home/your_user/public

---

### Post by Doug S on 2011-04-21
It is not my intent to sidetrack this thread, but I wanted to ask bodhi.zazen about this:
> With samba, do not share your home directory, share a directory within home
Why not? That is exactly what I have done on my system, and now I am worried. I am the only one with samba access to that folder. Actually, I set up all users the same way, with a private share that is their home directory and a global share available to anyone on the internal network.

---

### Post by bodhi.zazen on 2011-04-21
If it is not causing a problem , then you are fine.

But when sharing a file with samba, often the permissions of /home/your_user_name may need to be changes, to allow others access.

Changing the permissions of your home directory are less then ideal, and you (I) really do not want sensitive data, as might be in .ssh or .gpg, shared.

So if it works for you, no problem, but in general I would advise against it.

---

### Post by Doug S on 2011-04-21
bodhi: Thanks for the reply and the increased detail. I think I am O.K. but will check everything again.
 
Original poster, msbealo: Sorry, that I have no suggestion for you, and for digressing your thread. I am able to use ssh and samba at the same time without issues.

---

