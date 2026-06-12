---
title: "Ecryptfs-mount-private"
date: 2010-03-10
forum: Security
---

### Post by Utsukushii Tsubasa on 2010-03-10
alright, so i changed my password. everything was fine, but then i logged out. my optical drive was being very... ignorant. anyway, after a simple restart, i go to log in as normal. then a couple of errors pop up. one stating something about "could not update ICEauthority" or something like that. then theres another about "configuration server error (usr/libconf2-4/gconf-sanity-check-2 exit with status 256. and the final one is about nautilus. its saying that i need to create the folders or set permisions to let nautilus create them. then i try logging in under tty4 and it says cannot mount ecryptfs-mount-private or somethin. so any help? please???? 9.04 if your wondering.

---

### Post by bodhi.zazen on 2010-03-11
ecryptfs wraps your passphrase ...

Log out

go to a terminal (ctrl-alt-f1)

log in with your new passphrase

mount your encrypted home with your OLD password

```
ecryptfs-mount-private
```Again use your OLD PASSWORD with that command.

Then cd to your home directory

```
cd
```Then run:```
ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphrase
```enter your OLD password, then your NEW password

unmount your home

```
ecryptfs-umount-private
cd
```

restart GDM

```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```You should be able to log in normally.

Next time , when your change your log in password, before you log out, simply run

```
ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphrase
```enter your current then new passphrase this time.

---

### Post by FuturePilot on 2010-03-11
> **bodhi.zazen said:**
> 
Next time , when your change your log in password, before you log out, simply run

```
ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphrase
```enter your current then new passphrase this time.

I don't think this should be necessary. Usually this problem only happens when you forcibly change a password via System > Administration > Users and Groups. If you use the "passwd" command or System > Preferences > About Me it will automatically update the ecryptfs passphrase.

---

### Post by bodhi.zazen on 2010-03-11
> **FuturePilot said:**
> I don't think this should be necessary. Usually this problem only happens when you forcibly change a password via System > Administration > Users and Groups. If you use the "passwd" command or System > Preferences > About Me it will automatically update the ecryptfs passphrase.

Your comments are spot on re: changing your log in password, but I am not sure if they will fix the OP problem or not as ~/.ecryptfs/wrapped-passphrase is encrypted.

/me goes to bork a test system ...

Update: If I change my log in password via the command line (sudo passwd bodhi) and reboot, X fails when I log in with the new password. Without X the only I know to fix my problem is as outlined.

---

### Post by Kurtber on 2010-03-13
I have got the same problem as described by Utsukushii Tsubasa in the opening post ("Could not open ICEauthority" and so on..). 


I thought I had fixed this problem a few days ago, when I followed [a guide at bodhizazen.net]("http://bodhizazen.net/Tutorials/Ecryptfs/") for updating the ecrypt password (under "Change your passphrase to mount your encrypted private directory or home"). But when I restarted my computer last night, the problem was back. I believe I did something similar to the following last time:

> **bodhi.zazen said:**
> 
Log out

go to a terminal (ctrl-alt-f1)  **Note: I used ctrl-alt-f6, but that shouldn't matter**

log in with your new passphrase

mount your encrypted home with your OLD password

```
ecryptfs-mount-private
```Again use your OLD PASSWORD with that command.

Then cd to your home directory

```
cd
```Then run:

```
ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphrase 
```enter your OLD password, then your NEW password



But none of the following, as it wasn't mentioned in the guide I followed at bodhizazen.net

This time around I've tried to follow bodi.zazhen's solution from this thread, but I'm stopped at this following point:

> **bodhi.zazen said:**
> 
Log out

go to a terminal (ctrl-alt-f1)

log in with your new passphrase

mount your encrypted home with your OLD password

```
ecryptfs-mount-private
```

At this point I get this message:

```
Inserted auth tok key with sig [******************] into the user session keyring
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'
```I am very frightened that I will not be able to access my private data.. :icon_frown: I hope someone can help me with this problem.

---

### Post by bodhi.zazen on 2010-03-13
> **Kurtber said:**
> At this point I get this message:

```
Inserted auth tok key with sig [******************] into the user session keyring
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'
```I am very frightened that I will not be able to access my private data.. :icon_frown: I hope someone can help me with this problem.

Please post the entire command you ran, not just the error message.

First, is your home currently encrypted ?

```
cd
ls
```

What do you see when you type those commands ?

If your home directory is unencrypted, proceed with :

```
ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphrase
```

if you home is still encrypted, proceed with

```
ecryptfs-mount-private
cd
ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphrase
```

post the full command and any error messages.

Also I updated this page:

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

### Post by Kurtber on 2010-03-13
Thank you very much for your quick reply!

> **bodhi.zazen said:**
> Please post the entire command you ran, not just the error message.

First I logged in and got the following notification:

```

keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'
To run a command as administrator (user "root"), use "sudo <command>" .
See "man sudo_root" for details.

```Then I ran the following command:

```
 ecryptfs-mount-private
```And the result: 

```

Inserted auth tok key with sig [******************] into the user session keyring
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'
```
> **bodhi.zazen said:**
> 
First, is your home currently encrypted ?

```
cd
ls
```What do you see when you type those commands ?

Yes, my home is encrypted.

```

$ cd
$ ls
Access-Your-Private-Data.desktop   README.txt

```> **bodhi.zazen said:**
> 
if you home is still encrypted, proceed with

```
ecryptfs-mount-private
cd
ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphrase
```post the full command and any error messages.


Here we go:

```

$ ecryptfs-mount-private
Enter your login passphrase: 
Inserted auth tok key with sig [******************] into the user session keyring
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'
$ cd
$ ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphrase
Old wrapping passphrase: 
New wrapping passphrase:
$

```

---

### Post by bodhi.zazen on 2010-03-13
I am not sure exactly, but you can try loging out and back in and / or rebooting

---

### Post by Kurtber on 2010-03-14
I have tried both, and they do not have any effect.. :|

---

