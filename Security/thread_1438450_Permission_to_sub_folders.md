---
title: "Permission to sub folders"
date: 2010-03-25
forum: Security
---

### Post by whalogreg on 2010-03-25
Not sure if this is the right category, but here goes...

I gave the Lucid Beta a try by way of upgrading from 9.10, and decided to go back to Karmic until the final release. With this being said, I copied my Home folder to a different partition to keep and copy back after a clean install of 9.10. My problem now, is every folder/sub-folder and file in that copy of my Home folder has permission set to root. So when I copied it back to my Karmic install, I'm having trouble accessing everything. What would the best way to change permission of the folders I want? I could do them one by one, but with thousands of folders in my Picures/Music/Videos/Documents ect, it could take weeks.. Am I just in for a lot of leg work?

---

### Post by ldouble_e on 2010-03-25
Did you try to change the ownership of the entire home directory?
```
sudo -s
chown owner Home
```
Owner would be your user name. This should give you access to all of your home directory.

---

### Post by the yawner on 2010-03-25
assuming the folders are now inside your new Home folder, open a terminal and type the following commands:

```

cd ~

```
To go to your user home directory.

```

sudo chown *user*:*user* -hR *

```
sudo - run as superuser
chown - change owner with option R to also affect files and directories
* - will change ownership of all files and folder inside the current directory. alternative option is to specify the folder/s

---

### Post by whalogreg on 2010-03-25
> **ldouble_e said:**
> Did you try to change the ownership of the entire home directory?
```
sudo -s
chown owner Home
```
Owner would be your user name. This should give you access to all of your home directory.
I gave this a shot and got this in response...

"chown: cannot access `home': No such file or directory"

> **the yawner said:**
> assuming the folders are now inside your new Home folder, open a terminal and type the following commands:

```

cd ~

```
To go to your user home directory.

```

sudo chown *user*:[i]user[/] -hR *

```
sudo - run as superuser
chown - change owner with option R to also affect files and directories
* - will change ownership of all files and folder inside the current directory. alternative option is to specify the folder/s

and I tried this as well and got this...

"chown: invalid user"

---

### Post by HermanAB on 2010-03-25
Hmmm, Id do something like this:

$ sudo chown -R herman:herman /whereveritnowis/herman

---

### Post by the yawner on 2010-03-26
@OP
I didn't notice there was a typo in my post. Also, I forgot to point out that the *user* on command:
```

sudo chown *user*:*user* -hR *

```
should be your actual username on your system.

---

### Post by Francewhoa on 2010-10-22
Another way of doing this with a visual interface [http://ubuntuforums.org/showthread.php?t=1454684](http://ubuntuforums.org/showthread.php?t=1454684)

---

