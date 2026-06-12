---
title: "A question about the encrypted 'private' folder planned for Ibex"
date: 2008-08-28
forum: Security
---

### Post by jamesmcm on 2008-08-28
Ok, so I assume the encryption works by creating an encrypting version of the file and then deleting the original unencrypted version. My question is, does it overwrite the original file with a random string of the same length first? If it did this would make it impossible to 'recover' any of it from the hard drive so I strongly recommend it is implemented or else it is just a false sense of security.

Also, is it possible to have a seperate password for the folder than for the user, and does it ask you for your password every time you access it?

---

### Post by aheckler on 2008-08-28
This page may have the info you're looking for:

[https://wiki.ubuntu.com/EncryptedPrivateDirectory](https://wiki.ubuntu.com/EncryptedPrivateDirectory)

---

### Post by cariboo on 2008-08-29
The **ecrypted** folder is created when you run the script, it asks you for a passphrase that gets stored in /home/<user>/.ecryptfs. It also creates three directories in the users home directory, .Private, Private and .ecrytfs. As it stands right now these directories are set and the names can not be changed. When the Privated directory is unmounted you get the following message:

```
 THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA --  Run mount.ecryptfs_private to mount again -> /sbin/mount.ecryptfs_private
```

The permissions on the Private directory are 40500 when unmounted and 40700 when the directory is mounted.

In other words the owner has read and execute/search access when the private directory is umount and read, write and execute/search access when the private directory is mounted.

Jim

---

### Post by /etc/init.d/ on 2008-08-29
> **jamesmcm said:**
> My question is, does it overwrite the original file with a random string of the same length first? If it did this would make it impossible to 'recover' any of it from the hard drive so I strongly recommend it is implemented or else it is just a false sense of security.
Implementations like this assume or rely on the idea that any sensitive data is created and immediately saved into the encrypted file system.  Otherwise you have the issue of data remenance on the unencrypted copy.

I've demonstrated several times in this board why anything other than full file system encryption is leading people into a false sense of security, but I'll not repeat that here and suffice to say any anything that's going to provide encryption out-of-the-box has to be an improvement.

---

### Post by jamesmcm on 2008-08-29
> **/etc/init.d/ said:**
> Implementations like this assume or rely on the idea that any sensitive data is created and immediately saved into the encrypted file system.  Otherwise you have the issue of data remenance on the unencrypted copy.

I've demonstrated several times in this board why anything other than full file system encryption is leading people into a false sense of security, but I'll not repeat that here and suffice to say any anything that's going to provide encryption out-of-the-box has to be an improvement.

So implementing a system whereby it creates an encrypted version, then overwrites the original with random data before deleting it would still suffer from the data remaining on the HD unencrypted. I thought overwriting it first helped prevent this problem, or is it not that simple?

---

### Post by userundefine on 2008-08-29
I've looked through some resources on this Private folder idea but I haven't seen this answered, or perhaps I'm thick.  The guides say it's ideal to move folders there and then symlink them, i.e., .mozilla.  OK, so Firefox can still access .mozilla if it's symlinked, but how is it accessible if Private is supposed to be encrypted?  Do you enter your password each time you login?

---

### Post by MrGreen on 2008-11-01
As far as I can see it mounted as soon as your user logs in, Thing is I do not want icon on Desktop very messy... there must be a way to hide it?

Mounted is one thing but on show sort of defeats the object

Ok google is my friend

MrG

---

### Post by tubbygweilo on 2008-11-01
MrGreen,

Applications > Add/Remove > System Tools > Configuration Editor

and then selecting the Configuration Editor box will allow you to use the tool to tidy your desktop by
 
Applications > Accessories > System Tools > Configuration Editor > Apps > Nautilus > Desktop 

and then amending the volumes_visible value you should then no longer see the icon on your desktop.

Hope this helps.

---

### Post by MrGreen on 2008-11-01
Will that remove all icons? anyway will check it out thanks 

MrG

---

### Post by Sylchat on 2008-11-07
Hi 

I was trying to hide the Private folder from the desktop, as Private contains sensitive data and should not be clearly visible, especially with an empty desktop...

changing the volumes_visible option did the trick (you need to logoff/login), but it will hide any mounted volume, including usb sticks or external disks. They are still accessible in the "Places" menu in the gnome-panel.

And it won't hide regular icon.

---

### Post by bro on 2008-12-16
Related to this, if I change my password, would my Private folder still be mounted as usual when I login? (so a root could change my pass and access my data...)

---

### Post by cariboo on 2008-12-17
WHen you set up the encryted private directory, you are asked to create a passphrase, which should be different from your user password. If you change your password, it should have no effect on the passphrase you created.

Jim

---

### Post by bro on 2008-12-17
thanks, but i fail to understand then: how does it mount my private folder automatically when i log in? It has the password quasi-encrypted somewhere? 
I ask because it is quite easy to change a password once you have physical control of a computer. So I change the password (with help of a live-cd) login and still the private folder mounts... It would then only be safe if I type in the password manually after log in (so that it is in nowhere stored in de computer).

Am I wrong?

---

### Post by teddks on 2008-12-17
The unlock passphrase for the ~/Private directory is initially the same as your login passphrase, and pam hackery is used to unlock it when you log in. However, were root to change your login passphrase, it would have no impact on the unlock passphrase, so your data would still be safe as long as your password was.

---

### Post by bro on 2008-12-18
> **teddks said:**
>  However, were root to change your login passphrase, it would have no impact on the unlock passphrase

So it would just prompt me again for my password for the private folder then? Otherwise how can it mount the private folder when the password changed?

---

### Post by teddks on 2008-12-18
> **bro said:**
> So it would just prompt me again for my password for the private folder then? Otherwise how can it mount the private folder when the password changed?

It can't mount the private folder if the password changes. It'll fail silently. You'll need to mount it manually or change the password to get it to work automatically again.

---

### Post by bro on 2008-12-18
I'm going to use it :)

---

