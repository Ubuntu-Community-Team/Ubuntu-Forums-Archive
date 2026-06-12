---
title: "Disable automatic mounting of ecryptfs of Private at Gnome startup"
date: 2009-09-28
forum: Security
---

### Post by narnie on 2009-09-28
Hello,

I have been searching and searching for a way disable the initial mounting of my ecryptfs Private folder on login.

I have run ecryptfs-umount-private at the beginning of the Gnome session, but that is an after-the-fact solution. It also doesn't clear the tokens from the keyring for some reason, as all I have to do is click on the Access your Private..." and it will mount it decrypted without asking me for the login passphrase. If I run ecryptfs-umount-private from a command line, it will dismount it and clear the keyring as it should, but doesn't do this at initial logon. Hence, my desire to prevent it's mounting in the first place (plus I just wanna know, hehe). I don't want to walk away from the computer and have another user with root privileges look at my "Privates" while it is mounted when I didn't want it mounted really in the first place.

Does anyone know how ecryptfs is automounted (and hopefully how to prevent it)? If so, please, please share this mystical knowledge.

Thanks,
Narnie

---

### Post by Lars Noodén on 2009-09-28
What does /etc/fstab say, if anything, about it?

---

### Post by Soul-Sing on 2009-09-28
> Does anyone know how ecryptfs is automounted (and hopefully how to prevent it)? If so, please, please share this mystical knowledge.

ecrypt decrypt automag. your .private with your login password.

---

### Post by Soul-Sing on 2009-09-28
> Does anyone know how ecryptfs is automounted (and hopefully how to prevent it)? If so, please, please share this mystical knowledge.

ecryptfs decrypt automag. your .private with your login password.
that process can be changed....
(: [http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/))

---

### Post by narnie on 2009-09-28
> **Lars Noodén said:**
> What does /etc/fstab say, if anything, about it?

/etc/fstab 

is quite about ecryptfs. There are just the linux os, home, and swap partitions as the only entries in my fstab.

---

### Post by narnie on 2009-09-28
> **leoquant said:**
> ecryptfs decrypt automag. your .private with your login password.
that process can be changed....
(: [http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/))

Hmm. Interesting. I saw that file in ~/.ecryptfs and tried renaming it to bak.auto-mount.bak and rebooted the system. I could no longer login via gdm. I COULD log in via a vtty, which I did and renamed it back. Gotta go for a sec and when I get home, this will be the first thing I try.

In the mean time, I would like to know (just to increase my knowledge base) what is checking for this auto-mount (empty) file and when and from what is it called to do so?

Thanks,
Narnie

---

### Post by narnie on 2009-09-28
> **narnie said:**
> Hmm. Interesting. I saw that file in ~/.ecryptfs and tried renaming it to bak.auto-mount.bak and rebooted the system. I could no longer login via gdm. I COULD log in via a vtty, which I did and renamed it back. Gotta go for a sec and when I get home, this will be the first thing I try.

In the mean time, I would like to know (just to increase my knowledge base) what is checking for this auto-mount (empty) file and when and from what is it called to do so?

Thanks,
Narnie

As I feared, completely removing auto-mount from ~/.ecryptfs DOES result in a strange gdm hang in that it never seems to take my password but doesn't time out in the normal fashion as if one mistypes the password. It hangs the gdm and which then reboots itself as if CTRL-ALT-BKSP is hit. I restored the auto-mount file and I got back in fine.

As I feared, no dice, at least on my system, for this trick. Hence, again, my strong desire to know what calls ecryptfs-mount-private in the first place. I think it happens due to tight integration in with PAM so it is somewhere with that handoff of a validated gdm call to login and the actual transfer to Gnome in some manner (but then again I could be way off and probably am )

Narnie

---

### Post by narnie on 2009-09-28
In the meantime, I have just written a simple script rather than calling ecryptfs-umount-private directly using the startup application under the preferences menu which just unmounts the ecryptfs Private dir, remounts it (it DOES NOT ask for the login passphrase, at least on my system), and then turns around and unmounts it again. A nasty quick-fix band-aid-type fix for this problem until I find out how to go to the source with it to prevent mounting in the first place.

I put the code below in ~/bin/privatize where privatize is the file.

```
#! /bin/bash
#unmount private folder - ecryptfs-unmount-private is run twice to ensure keyring is cleared
ecryptfs-umount-private
ecryptfs-mount-private
ecryptfs-umount-private
exit

```

then make it runnable with:
```
chmod +x ~/bin/privatize
```

I then used Menu->Preferences->startup applications to add this file to the startup processes.

It works like a charm. Now, just for the source of the mounting in the first place.

Narnie

---

### Post by narnie on 2009-09-28
OK Folks, here is the true fix.

I was reading an article on ecryptfs ([http://ecryptfs.sourceforge.net/ecryptfs-pam-doc.txt]("http://ecryptfs.sourceforge.net/ecryptfs-pam-doc.txt")) and found that PAM is involved and thus started looking in /etc/pam.d/ and found 2 files that need to be modified:

/etc/pam.d/common-auth
/etc/pam.d/common-session

Do the following as root, but make a backup copy first in a directory OUT OF this directory like ~/ or it will possibly run the backup which is unmodified.

In /etc/pam.d/common-session look for a line that says:

```
auth	optional	pam_ecryptfs.so unwrap
```
and comment it out like:
```
#auth	optional	pam_ecryptfs.so unwrap
```

In /etc/pam.d/common-auth look for a line that says:

```
session	optional	pam_ecryptfs.so unwrap
```
and comment it out like
```
#session	optional	pam_ecryptfs.so unwrap
```

Both files must be modified. The common-session file is what cause the actually mounting and the common-auth unwraps the passphrase.

If just common-session is commented out (as I tried first), all one has to do is type ecrypt-mount-private and it will mount without the login passphrase. This is NOT GOOD. So the common-auth must be modified to prevent the loading of the unwrapped passphrase into the kernel.

The caveat to this is that THIS AFFECTS ALL USERS. I have just discovered the above by rooting around myself and it satisfies my needs. However, it will make it more difficult on a multiuser system for novices as the Private will not be automatically mounted. There may be a way to prevent this on a user-level (not system level) but I don't know how to do that.

Hope this helps someone in the future.

Yours,
Narnie

---

### Post by undecim on 2009-09-28
rm ~/.ecryptfs/auto-mount

Note: If you encrypt your entire home directory with ecryptfs (as i do) you need to umount it first

---

### Post by narnie on 2009-09-29
> **undecim said:**
> rm ~/.ecryptfs/auto-mount

Note: If you encrypt your entire home directory with ecryptfs (as i do) you need to umount it first

This resulted in a complete inability to login via GDM on my system. Please see the posts where I explained this above.

Narnie.

---

### Post by bodhi.zazen on 2009-09-29
Just some information ...

First if you log in via say ssh, your $HOME will be encrytped and you will see this :

```
ufbt% ls
Access-Your-Private-Data.desktop  README.txt
```

now 

```
ufbt% cat README.txt
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 $ ecryptfs-mount-private
```

And so ....

```
ufbt% ecryptfs-mount-private
Enter your login passphrase:

Warning: Using default salt value (undefined in ~/.ecryptfsrc)
Inserted auth tok with sig [10a46f5185226394] into the user session keyring

INFO: Your private directory has been mounted.
INFO: To see this change in your current shell:
  cd /home/bodhi

ufbt% cd

. ./.zshrc #This command loads .zshrc (I use zhs)
```

Which results in 

```
    August 2009          September 2009         October 2009
Su Mo Tu We Th Fr Sa  Su Mo Tu We Th Fr Sa  Su Mo Tu We Th Fr Sa
                   1         1  2  3  4  5               1  2  3
 2  3  4  5  6  7  8   6  7  8  9 10 11 12   4  5  6  7  8  9 10
 9 10 11 12 13 14 15  13 14 15 16 17 18 19  11 12 13 14 15 16 17
16 17 18 19 20 21 22  20 21 22 23 24 25 26  18 19 20 21 22 23 24
23 24 25 26 27 28 29  27 28 29 30           25 26 27 28 29 30 31
30 31

  09:59:35 up 2 days, 34 min, 1 user, load average: 0.00, 0.01, 0.00


  After enjoying the taste of solitude and the taste of peace, one is
  freed from distress and evil, as one enjoys the taste of spiritual joy.
  205


  Today is Boomtime, the 53rd day of Bureaucracy in the YOLD 3175

  Peace be with you bodhi

bodhi@ufbt:~$ 
```

You can re-encrypt your $Home if you wish

```
cd /home
ecryptfs-umount-private
cd

ls

Access-Your-Private-Data.desktop  README.txt
```

====

I find it is often easier to simply make a separate encrypted directory rather then encrypting everything in $HOME.

---

### Post by psychok7 on 2012-07-06
> **narnie said:**
> In the meantime, I have just written a simple script rather than calling ecryptfs-umount-private directly using the startup application under the preferences menu which just unmounts the ecryptfs Private dir, remounts it (it DOES NOT ask for the login passphrase, at least on my system), and then turns around and unmounts it again. A nasty quick-fix band-aid-type fix for this problem until I find out how to go to the source with it to prevent mounting in the first place.

I put the code below in ~/bin/privatize where privatize is the file.

```
#! /bin/bash
#unmount private folder - ecryptfs-unmount-private is run twice to ensure keyring is cleared
ecryptfs-umount-private
ecryptfs-mount-private
ecryptfs-umount-private
exit

```

then make it runnable with:
```
chmod +x ~/bin/privatize
```

I then used Menu->Preferences->startup applications to add this file to the startup processes.

It works like a charm. Now, just for the source of the mounting in the first place.

Narnie

this works for me like a charm. even wrote a decrypt :

```
 #! /bin/bash
#mount private folder
ecryptfs-mount-private
exit


```

---

### Post by wildmanne39 on 2012-07-08
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

