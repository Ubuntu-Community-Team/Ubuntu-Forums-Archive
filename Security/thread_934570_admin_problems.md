---
title: "admin problems"
date: 2008-09-30
forum: Security
---

### Post by cannox on 2008-09-30
i have being using ubuntu for some time, and like last week or so i updated my packages and after doin so

i type

sudo apt-get update
this is wad they always give me 
sudo: /etc/sudoers is owned by gid 1001, should be 0

i have been trying to solve the problem but i couldnt i even went to recovery mode and typed 

chgrp root /etc/sudoers

but nothing happened. pls someone help me. this happens everywhere even in root.

---

### Post by Nepherte on 2008-09-30
You probably edited this file without visudo which guarantees permission and ownership of this important file. To restore the correct permissions and permission. Reboot and choose the recovery mode. This will leave you into a terminal as root. Type the following:
```
cd /etc
chown root:root sudoers
chmod 0440 sudoers
```

---

### Post by cannox on 2008-09-30
hey!

i tried it but it would not work.

it would be like 

home@laptop:~$chown root:root sudoers
home@laptop:~$

yeah it would just be like tat no changes taking place.

---

### Post by cariboo on 2008-09-30
When you make changes using the command line it usually only echos back if you do something wrong. You command may have worked and you don't know it. THe way to check permissions and ownership of a file is to use:

```
ls -la
```

You should get an output something like this:

```
ls -la sudoers
-r--r----- 1 root root 557 2008-09-30 16:49 sudoers
```

Jim

---

### Post by cannox on 2008-10-01
hi i dont really understand how izit presented. i cant seem to find the problem.

---

### Post by iponeverything on 2008-10-01
you can't change the perms on the file because your not root and your not root because of perms on are mucked. humm..

easy enough to fix:

boot into single user as shown here:
[http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

remount / read/write like so:
mount -o remount,rw /

Then cd /etc and fix the file as described earlier.

then type: sync; sync; sync; reboot 

(for those of you wondering about the last sync's.. its just old-school paranoia. -- )

---

### Post by Nepherte on 2008-10-01
> **cannox said:**
> hey!

i tried it but it would not work.

it would be like 

home@laptop:~$chown root:root sudoers
home@laptop:~$

yeah it would just be like tat no changes taking place.
Just boot into recovery mode and type the commands I gave you. It is perfectly normal behaviour that you don't get any output for that command. If you run ls -l sudoers afterwards, you should get an output like cariboo907 showed.

---

### Post by cannox on 2008-10-01
yeah i tried it again but its not working. 
i find that ubuntu is getting more and more unstable man.
even sometimes my compiz has problems. didnt have these kind of problems in
gusty man. 
sad sad:(

come on anybody! help!

---

### Post by cannox on 2008-10-01
ok i typed in 
ls -al /etc/sudoers

it came out with
-r--r----- 1 root root 470 2008-05-08 17:18 /etc/sudoers

but nothing changes. i stil get the 

sudo: /etc/sudoers is owned by gid 1001, should be 0

when i use Sudo.

---

### Post by AndyCee on 2008-10-01
Interesting one.

So file is owned by root, but the owner has a gid of 1001. Perhaps your root has changed gid?

Perhpas try:
```
id root
```

?

---

### Post by cannox on 2008-10-01
it came out like this

nerdkid@nerdkid-laptop:~$ id root
uid=0(root) gid=100(users) groups=100(users),1001(root),3(sys),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),27(sudo),29(audio),30(dip),46(plugdev),105(scanner),107(fuse),109(lpadmin),115(admin)

hope you could help!

---

### Post by Nepherte on 2008-10-02
Go to system > administration > users and groups. Then click on the button manage groups and double click on the root group. Change the group id to 0 if it isn't.

---

### Post by cannox on 2008-10-02
sorry not working

---

### Post by Nepherte on 2008-10-02
Did you restart? I believe the changes made to user/group have effect from the next login.

---

### Post by cannox on 2008-10-03
yes i did. i think i have no choice but to like reformat it. 

i give it like 1 week. if no solution. bye bye ubuntu.

---

