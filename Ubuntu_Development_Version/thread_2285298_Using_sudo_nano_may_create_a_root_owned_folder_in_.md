---
title: "Using sudo nano may create a root owned folder in user Home folder (.nano"
date: 2015-07-04
forum: Ubuntu Development Version
---

### Post by mc4man on 2015-07-04
Of no real significance I guess though don't like root owning anything in my $HOME
(- wouldn't know what source to bug..

Edit: turns out the 1st run of nano creates the folder, if done as root then root owns, otherwise it's a user owned dir. of no particular use.

---

### Post by oldfred on 2015-07-04
We normally post sudo for editing system files.

But if a file in /home, you then should not need sudo.

---

### Post by ajgreeny on 2015-07-04
What is in that root owned folder, or is it empty?

---

### Post by coffeecat on 2015-07-04
Yes, I can confirm this.

```
sudo nano /etc/hosts
```

I added a dummy line starting with #, ctrl-o to save, ctrl-x, and folder ~/.nano appeared owned by root. It's empty.

---

### Post by ajgreeny on 2015-07-06
I can also confirm this is happening in my 15.10 as well.  It is possible to avoid it, not surprisingly, by using **sudo -i nano** or **sudo H nano** but it would be good to know why this root-owned folder appears with **sudo nano**.

You do not even need to open a file for the folder to appear; simply using **sudo nano** to open nano empty as root does this.

PaulW2U from these forums has raised a launchpad bug for this
[https://bugs.launchpad.net/ubuntu/+source/nano/+bug/1471459](https://bugs.launchpad.net/ubuntu/+source/nano/+bug/1471459) but has then suggested it is an invalid bug as it does not occur if he uses **sudo nano** to open a system file.

That is not my finding where any use of sudo nano makes that .nano folder in my home

---

### Post by PaulW2U on 2015-07-06
Thanks ajgreeny, I'm not sure what planet I was testing on previously. :confused:

Anyway, I've re-opened the bug - [https://bugs.launchpad.net/bugs/1471459](https://bugs.launchpad.net/bugs/1471459) - and marked it 'Confirmed' as there are currently two of us shown as being affected.

---

### Post by ajgreeny on 2015-07-06
And now a third, v3.xx, so it is certainly still there as a bug!

---

### Post by mc4man on 2015-07-06
Typically the first time in an install I’d use nano would be as root, so decided to check otherwise.
Seems now the first use of nano creates the .nano folder. So if done as a user then it will be created & subsequent uses of 'sudo nano' will leave alone & not change permissions.

---

### Post by VMC on 2015-07-06
> **coffeecat said:**
> Yes, I can confirm this.

```
sudo nano /etc/hosts
```

I added a dummy line starting with #, ctrl-o to save, ctrl-x, and folder ~/.nano appeared owned by root. It's empty.

Since I never used 'nano', I just tried using 'vi', and no root file is left over on my home folder.

edit: is it a 'nano' problem then?

---

### Post by v3.xx on 2015-07-07
> **VMC said:**
> Since I never used 'nano', I just tried using 'vi', and no root file is left over on my home folder.
edit: is it a 'nano' problem then?
It looks so.  You could try "sudo nano" and see if you are affected and maybe add your  findings to the launchpad bug report.

---

### Post by zika on 2015-07-07
And, yet, if You've used nano first as ordinary user (I think even if You did not) You can erase whole folder without root priviledges. Even though search_history file could have root in its flags it is not owned by root.
Explore sudoedit... ;)

---

### Post by coffeecat on 2015-07-07
Following up on what zika and ajgreeny have said, and summarising what I can confirm:

```
sudo nano
``` -> root owned .nano folder appears in user's home.

```
sudo -H nano
``` -> .nano folder does not appear.

```
nano
``` -> User-owned .nano folder appears in user's home.

It looks as though nano has suddenly decided it needs what I assume is a config folder in home. I haven't gone any further yet to see what if anything causes files to be saved in this folder.

---

### Post by mc4man on 2015-07-07
As I edited in orig post yesterday & mentioned in prev. posts by ajgreeny & me this occurs on the 1st. run of nano. If done as a user then the user will own .nano, if done as root (sudo), then root will own
(- I changed the bug report to reflect this

If using sudo -H nano then a .nano will be created in /root

This appears to be a one time deal, once created ownership is not changed.

---

