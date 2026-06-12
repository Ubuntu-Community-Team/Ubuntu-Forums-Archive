---
title: "oh ubuntu help me"
date: 2008-09-25
forum: Security
---

### Post by kazablnka on 2008-09-25
[COLOR="Blue"][FONT="Georgia"]i can not open my partions ntfs when i o it ubuntu requst password when enter ont open it's wrong ,i enter also
root and change it also wrong i can't open my hard
look [/FONT][/COLOR]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=86433&stc=1&d=1222387113[/IMG]

---

### Post by lisati on 2008-09-25
Is there anything running that you know of that should be accessing the NTFS partition?

Have a look h[ere]("http://https://help.ubuntu.com/community/MountingWindowsPartitions?action=show") for some information on file systems - it has a link to a section about NTFS

---

### Post by John164918a on 2008-09-25
Have you forgotten/changed your password? How did you log in?

If so you could boot into recovery mode which I think automatically gives you root (Well it did on my PCLinuxOS when I forgot the root password), then use the passwd command to change your password.

---

### Post by cariboo on 2008-09-25
Are you entering the password you set when you installed Ubuntu. What version of Ubuntu are you using, as I get the same dialogue box when opening an external drive, I'm using Intrepid alpha6.

Jim

---

### Post by kazablnka on 2008-09-26
i have tow partion with ntfs and to with fat32 im log on in system with defult user and password (ubuntu - ubuntu )ican change password root and when im log on password wrong
iwant to mount my hard 

Are you entering the password you set when you installed Ubuntu. What version of Ubuntu are you using, as I get the same dialogue box when opening an external drive, I'm using Intrepid alpha6.

Jim ?
yeas
my ver 8.4
when  useing cd live ican acssece to partions without password
im innstall new vertion user and password is ubuntu
ican't also entery to my hard ntfs or fat32

---

### Post by hyper_ch on 2008-09-26
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

### Post by cariboo on 2008-09-26
In your next post could you paste the output of:

```
sudo fdisk -l
```

One other thing to check is your /etc/hosts file and make sure it looks something like this: 

```
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	intrepid
```

If you've just installed hardy and haven't done any updates, there was a problem with the hosts file when hardy was first released, but the updates repaired the problem.

Jim

---

### Post by kazablnka on 2008-09-28
> **cariboo907 said:**
> In your next post could you paste the output of:

```
sudo fdisk -l
```

One other thing to check is your /etc/hosts file and make sure it looks something like this: 

```
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	intrepid
```

If you've just installed hardy and haven't done any updates, there was a problem with the hosts file when hardy was first released, but the updates repaired the problem.

Jim

why can i get enter on hard with cd live wihtout updat

---

### Post by hyper_ch on 2008-09-29
*edit*"

---

### Post by lisati on 2008-09-29
> **kazablnka said:**
> why can i get enter on hard with cd live wihtout updat

Are you able to go to the "terminal" (you can find it on the Applications->Accessories menu) and enter commands? If so, please type in ```
sudo fdisk -l
``` and let us know what it tells you.

---

### Post by NathanDS101 on 2009-04-17
hmmm im gunna search some stuff up ill get back to you:popcorn:

---

### Post by cariboo on 2009-04-17
This thread is from September 2008, I'm sure the OP is long gone.

Jim

---

