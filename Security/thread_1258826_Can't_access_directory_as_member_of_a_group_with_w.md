---
title: "Can't access directory as member of a group with wrx permission"
date: 2009-09-05
forum: Security
---

### Post by narnie on 2009-09-05
Hello,

I _THOUGHT_ that I understood permissions in UNIX but have not needed something like this before.

I have created a directory /share/ with root as owner (doesn't matter who the owner is tho I get the same result) and changed its group to "share." The directory has wrx permissions, but I can't access it as a regular user who is in that "share" group. See the follow output (I've proven membership of "share" with the members and id listing):

```
user1@toshiba-laptop / $ ls -ldp sh*
drwxrwx--- 2 root share 4096 2009-09-05 13:52 share/

user1@toshiba-laptop / $ members share
share user1 user2

user1@toshiba-laptop / $ id -nG user1
user1 adm dialout cdrom plugdev lpadmin admin sambashare vboxusers hamachi share


user1@toshiba-laptop / $ ls share/
ls: cannot open directory share/: Permission denied
user1@toshiba-laptop / $ 

user1@toshiba-laptop / $ cd share/
bash: cd: share/: Permission denied
```

What am I missing?

With thanks,
Narnie

---

### Post by phillw on 2009-09-05
is  /share  actually from your / directory ?

I'm figuring it is the permissions of / that maybe stopping you.

```

phillw@piglet:/$ pwd
/
phillw@piglet:/$ mkdir share
mkdir: cannot create directory `share': Permission denied

```Permissions will always bite you in the bum !!

```

phillw@piglet:/$ ls -al
drwxr-xr-x  22 root root       4096 2009-09-05 19:02 .
drwxr-xr-x  22 root root       4096 2009-09-05 19:02 ..
.
.
drwxr-xr-x   6 root root       4096 2009-08-12 11:49 home


```So, how did you make the share directory ?

Phill.

---

### Post by narnie on 2009-09-05
I made it by

```
sudo mkdir /share/
```

then:
```
sudo chgrp share /share/
```

what I have also tried to do is under

/home/share/

where share is an actual user.

I'm trying to establish a place where I can share files with those in a share group (my wife and I so we can share a common place for pics, music files, etc).

I want it under the /home/ dir cuz it is on it's own partition so I want to keep it there to easily keep user files separate from the os. Since it wouldn't work under /home/share, I just tried it in the "/" directory.

Yet, I don't want it the dir to have anyone rwx, just those in the share group.

Thanks,
Narnie

---

### Post by rookcifer on 2009-09-05
Create the user share like this:

```
useradd -m -G adm,cdrom,share,sudo -s /bin/bash share
```

You can substitute the groups I listed above for the ones you want the user "share" to be in.  For a list of all groups, type: 

```
cat /etc/group | more
```

Then set a password for the new user "share":
```

passwd share
```

Now you will have a directory /home/share.

---

### Post by phillw on 2009-09-05
I do this via the GUI !!!, but, it's good to brush off the cobwebs !!!!

What I'm going to do is make a new directory, under home called share

I will use sudo to make the directory, so it will be owned and managed by root,
then I will create a group called share
then I will chgrp the directory to share
then I will add myself & an alias to the group share, who will have wrx privalidges

Is this what u want ?

Phill.

---

### Post by narnie on 2009-09-05
Sorry guys, I should have said, I already created the share group (first) and then the share user and added it to the share group (actually this can be seen from the command `members share` which as above showed that "share user1 and user2" users were all part of the share group).

Now, the funny things is that I went away for a while and slept my computer. When I tried to wake it up, it wouldn't (that is very rare, normally wakes up nicely) so I had to reboot. After the reboot, I could access the share dirs as users in those groups without difficulty. I can't explain that, but all is well.

With thanks,
Narnie

---

### Post by narnie on 2009-09-05
I think I have figured out why this has happened. I just revoked my wifes membership to the share group to test things. She, as expected, couldn't access the dir. Then I restored her share membership, but she still couldn't get in. I figured out that it was all in the same shell instance. Evidently, this is the problem. When I closed the shell and started another shell, it worked.

Cheerio,
Narnie

---

