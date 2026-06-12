---
title: "ssh-copy-id not working on one box"
date: 2010-10-31
forum: Security
---

### Post by holiday on 2010-10-31
I have three computers on my lan. I have installed authorized_keys entries to enable no password between two of these machines, but the third will not go there. 

The sshd_config is identical for all machines.

Where else can I look for the trouble?

---

### Post by luvshines on 2010-10-31
You may want to have a look at the id_....pub key of the base machine and see if it is actually dumped in the .ssh/authorized_keys on that remote box or not ( you can compare the entry with other machine)

Also, do check the permission for the file and directory and compare it with other working machines

---

### Post by holiday on 2010-10-31
> **luvshines said:**
> You may want to have a look at the id_....pub key of the base machine and see if it is actually dumped in the .ssh/authorized_keys on that remote box or not ( you can compare the entry with other machine)

Also, do check the permission for the file and directory and compare it with other working machines

Good suggestions. Thanks. 

The keys are there for both machines, and the permissions on all directories are the same. 

I've been doing this for years and I've never had this problem. The only change is that I upgraded all of them to 10.04 - the Best Ubuntu release ever - and I haven't felt that way since my first install. 

Perhaps my best bet - though the least interesting - is to re-install ssh on the problem box?

---

### Post by mainerror on 2010-10-31
Is the no password directive active on the server when you try to copy your key to it?

---

### Post by holiday on 2010-10-31
> **mainerror said:**
> Is the no password directive active on the server when you try to copy your key to it?


The sshd_config is identical on all machines. Where else should I look?

---

### Post by luvshines on 2010-10-31
> **holiday said:**
> The sshd_config is identical on all machines. Where else should I look?

Try looking into ssh -vv logs. Maybe that can point to something useful. Also auth.log on the server may help

---

### Post by holiday on 2010-11-01
> **luvshines said:**
> Try looking into ssh -vv logs. Maybe that can point to something useful. Also auth.log on the server may help

The auth.log had it - "bad ownership or modes"

So it was permissions, as you'd suggested at first. But! My permissions were the same for the .ssh directory on all accounts - when viewed from outside the directory. However when inside the .ssh directory and 

$ ls -la

I noticed this

drwxrwxrwx 38 srephen srephen 32768 2010-10-30 15:55 ..

Whereas if I did the same from the other machines, the permissions for the .. directory were 755. 

I chmod 755 on .. and now it's working. 

That is interesting. I assume it means that I had misconfigured my home directory for universal access - some late night desperate hacking no doubt. 

Does it look like that to you, or am I missing something. 

Thanks for your help, by the way.

---

### Post by luvshines on 2010-11-02
> **holiday said:**
> The auth.log had it - "bad ownership or modes"

So it was permissions, as you'd suggested at first. But! My permissions were the same for the .ssh directory on all accounts - when viewed from outside the directory. However when inside the .ssh directory and 

$ ls -la

I noticed this

drwxrwxrwx 38 srephen srephen 32768 2010-10-30 15:55 ..

Whereas if I did the same from the other machines, the permissions for the .. directory were 755. 

I chmod 755 on .. and now it's working. 

That is interesting. I assume it means that I had misconfigured my home directory for universal access - some late night desperate hacking no doubt. 

Does it look like that to you, or am I missing something. 

Thanks for your help, by the way.

Gud to know that it is finally (re)**SOLVED** :D
Maybe 777 for /home messed it.

I really hate apps which fail to run due to file permissions.

Recently someone unknowingly changed 777 perms for /etc/sudoers file and sudo stopped working :mad:

---

