---
title: "SFTP through FileZilla - mkdir permission denied"
date: 2015-07-15
forum: Server Platforms
---

### Post by ryan170 on 2015-07-15
Hi all,

I just started using Ubuntu Server today to setup a Moodle installation. I have everything running great, Moodle is setup, there's plenty of documentation to help me along the way, but I recently ran into a problem.

I've setup a moodle git repository in /opt/moodle according to the installation instructions ([https://docs.moodle.org/27/en/Step-by-step_Installation_Guide_for_Ubuntu](https://docs.moodle.org/27/en/Step-by-step_Installation_Guide_for_Ubuntu)).

Now I want to download some themes and plugins and transfer them to the repository via FileZilla (so that when I update, they won't be overwritten; it is explained here, and I *think* that's the way it is supposed to work: [https://docs.moodle.org/27/en/Step-by-step_Installation_Guide_for_Ubuntu#Step_5:_Copy_local_repository_to_.2Fvar.2Fwww.2Fhtml.2F](https://docs.moodle.org/27/en/Step-by-step_Installation_Guide_for_Ubuntu#Step_5:_Copy_local_repository_to_.2Fvar.2Fwww.2Fhtml.2F)).

I can use FileZilla to access the server via SFTP no problem, but when I try to copy files over to /opt/moodle/, all I get is "mkdir /opt/moodle/theme/XXX: permission denied", so I can't create any directories or transfer any files.

I've been googling for a while, but I haven't quite found anything to walk me through solving this just yet.

Could someone point me in the right direction? Thanks.

---

### Post by Anakondarh on 2015-07-15
Can you SSH into the server and check the permissions of /opt/moodle? ssh and do ```
ls -la /opt
```, and check the moodle line. Post it here if you're not too sure of what the output means...

---

### Post by ryan170 on 2015-07-15
Here is the output:

```
total 12
drwxr-xr-x  3 root root 4096 Jul 15 19:34 .
drwxr-xr-x 22 root root 4096 Jul 16 07:59 ..
drwxr-xr-x 46 root root 4096 Jul 15 19:45 moodle
```

So it appears that it belongs to root.

I'm trying to use SFTP with the same user that I use for SSH. I only have one user on this server so far - the admin user "ryan".

---

### Post by Lars Noodén on 2015-07-15
If you are the only user, then a simple [chown](http://manpages.ubuntu.com/manpages/trusty/en/man1/chown.1.html) will work.  If you plan to have other users sharing the same directory then you will have to use a group:

```

sudo addgroup moodlers

sudo gpasswd --add ryan180 moodlers

sudo chgrp -R moodlers /opt/moodle

sudo find /opt/moodle -type d -exec chmod g=rwxs "{}" \;

sudo find /opt/moodle -type f -exec chmod g=rws "{}" \;

```

---

### Post by ryan170 on 2015-07-15
EDIT:

That got it working. Thanks!

If I wanted to reverse the changes, could I just 

```
sudo chgrp -R root /opt/moodle
```?

---

### Post by Lars Noodén on 2015-07-16
Sorry.  I meant to write 'moodlers'.  You're in that group so you will then get write permission.  So will any others in that group.

---

### Post by ryan170 on 2015-07-16
Thanks, that got it sorted.

If in the future, if I wanted to reverse the changes, could I just give the command

```
sudo chgrp -R root /opt/moodle
```

?

Thanks again.

---

### Post by Lars Noodén on 2015-07-16
No worries.  

Yep.  Using chgrp to change it back to root would undo the changes, except for the +s (setguid) bit.  To clear that you would need chmod.  

```

sudo chmod g=rx /opt/moodle/

```

---

