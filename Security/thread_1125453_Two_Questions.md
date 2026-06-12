---
title: "Two Questions"
date: 2009-04-14
forum: Security
---

### Post by Regele IONESCU on 2009-04-14
Hi all!

Firstly let me share my happiness: I am the happy owner of a dual boot system: Windows XP and Ubuntu Studio. Everything works fine.


Questions:

1. When I installed Ubuntu Studio I have been asked for the passphrase and told that there will be a folder nobody could access but me. What is that folder? What is his name?

2. How could I make a similar folder, with the same rights, so I could be the only one that could open it, on an external hardrive? The last question would be better like this: could I make such a folder on an external hard drive?

Many thanks!
Long live Linux, long live Ubuntu, long live Ubuntu Studio, long live Ubuntu community!):P

---

### Post by Yvan300 on 2009-04-14
To the guy above me, don't you have to be an admin of the forums to have that animation in your signature :)

---

### Post by ninjapirate89 on 2009-04-14
Looks like spam.

---

### Post by Regele IONESCU on 2009-04-15
> **Yvan300 said:**
> To the guy above me, don't you have to be an admin of the forums to have that animation in your signature :)

Then why is an option available to non administrators? And I was waiting a response to my questions.:guitar:

---

### Post by Regele IONESCU on 2009-04-15
> **ninjapirate89 said:**
> Looks like spam.

Two questions DIRECTLY related to Ubuntu are spam? And a non-sense reply isn't spam at all?

As both of your replies do not answer my questions they are pure spam.

I was waiting for an answer to my questions and I got stones. Is that how Ubuntu community is?

---

### Post by Nepherte on 2009-04-15
The private directory is /home/<username>. The <username> has full access, others none. Creating the same situation on a external disk is somewhat more difficult as fat and ntfs, the two most common file systems found on external disks, don't have this kind of permission system.

---

### Post by Regele IONESCU on 2009-04-15
> **Nepherte said:**
> The private directory is /home/<username>. The <username> has full access, others none. Creating the same situation on a external disk is somewhat more difficult as fat and ntfs, the two most common file systems found on external disks, don't have this kind of permission system.

**Thank you for your reply!**

Couldn't I make an ext3 filesystem on the external HD? If I make that could I access it from another Linux machine, would I be able to access it using a user name and pass-phrase or sort of?

My aim is to make kind of archive that would be accessible only via a pass-phrase/password on an external HD, so that only the person knowing the pass-phrase/password would be able to access it no matter the machine.

I just started to use Ubuntu and I am a bit confused regarding difference between pass-phrase and password. I am learning.
[B]
Thanks a lot again![/B]

---

### Post by Nepherte on 2009-04-15
You can indeed create a ext3 partition. You can then access the directories if you have the same username, otherwise you simply can't.

[quote="Regele IONESCU"]My aim is to make kind of archive that would be accessible only via a pass-phrase/password on an external HD, so that only the person knowing the pass-phrase/password would be able to access it no matter the machine.[/quote]
Perhaps you're better off with encryption. Something like TrueCrypt which can be used on any filesystem and many operating systems.

To get back on your home directory, I suggest you check the permissions of that directory with:
```
ls -l /home
```
and post them here, so we can verify others can't read it.

---

### Post by Regele IONESCU on 2009-04-17
drwxr-xr-x 53 admiral admiral 4096 2009-04-17 00:48 admiral

---

### Post by Bachstelze on 2009-04-17
> **Regele IONESCU said:**
> drwxr-xr-x 53 admiral admiral 4096 2009-04-17 00:48 admiral

That means everyone can read your home directory. If you want to change this, do

```
chmod -R o= $HOME
```

To setup a private encrypted folder, see [this howto]("http://tombuntu.com/index.php/2008/08/07/create-an-encrypted-private-directory-with-ecryptfs/"). Note this is **not** the same as using UNIX permissions. If you merely [font="monospace"]chmod 700[/font] something, anyone will be able to access it by stealing your hard drive, or even just using a Live CD on the machine while you're looking away.

---

### Post by Regele IONESCU on 2009-04-17
> **HymnToLife said:**
> That means everyone can read your home directory. If you want to change this, do

```
chmod -R o= $HOME
```

To setup a private encrypted folder, see [this howto]("http://tombuntu.com/index.php/2008/08/07/create-an-encrypted-private-directory-with-ecryptfs/"). Note this is **not** the same as using UNIX permissions. If you merely [font="monospace"]chmod 700[/font] something, anyone will be able to access it by stealing your hard drive, or even just using a Live CD on the machine while you're looking away.

Just got an "operation not permitted". Does it mean someone has taken over my computer?

---

### Post by Bachstelze on 2009-04-17
The directory is owned by user [font="monospace"]admiral[/font]. Is that you?

Just in case, paste the output of those commands :

```
whoami
echo $HOME
ls -ld $HOME
```

---

### Post by Regele IONESCU on 2009-04-17
The full answer to the first command is:

chmod: changing permissions of `/home/admiral/doi.mov': Operation not permitted



and for the last one is:

drwxr-x--- 55 admiral admiral 4096 2009-04-17 16:07 /home/admiral


I see that what was 53 is now 55. Does it mean anything?


Is "drwxr-xr-x 53 admiral admiral 4096 2009-04-17 00:48 admiral" kind of key to access my computer or simply states that is not protected enough?

---

### Post by Bachstelze on 2009-04-17
Okay so you have a file in your home directory that is not owned by you. Therefore, you can't change its permissions. To give yourself ownership of your home directory and everything inside it, do

```
sudo chown -R admiral /home/admiral
```


As for the permissions, [font="monospace"]drwxr-xr-x[/font] means that you (the owner) have read-write access to the directory in question, and everyone else has read-only access. As you can see, it was modified to [font="monospace"]drwxr-x---[/font] which means that you have read-write access and everyone else has no access at all (see how the last three characters changed from r-x to ---).

---

### Post by Regele IONESCU on 2009-04-17
admiral@parahod:~$ sudo chown -R admiral /home/admiral
[sudo] password for admiral: 
chown: cannot access `/home/admiral/.gvfs': Permission denied
admiral@parahod:~$ 


I created that file using **Cinelerra hi-pr(only admins)**. This is the sure reason I have no access to it or I lost the right to it.


Prior to reading your post, I saw a small window saying &#8221;Launching&#8221; but I was unable to switch to it and therefor unable to see what was launching. Does it mean that someone got into my computer?

---

### Post by Bachstelze on 2009-04-17
> **Regele IONESCU said:**
> Does it mean that someone got into my computer?

That's very unlikely, unless you have a SSH or Telnet server running. [font="monospace"]~/.gvfs[/font] is a Gnome thing so I can't help you with it. Maybe you need to be logged out to change its permissions?

---

### Post by Regele IONESCU on 2009-04-17
> **HymnToLife said:**
> That's very unlikely, unless you have a SSH or Telnet server running. [font="monospace"]~/.gvfs[/font] is a Gnome thing so I can't help you with it. Maybe you need to be logged out to change its permissions?

I have no server running. As far as I know, Ubuntu Studio does not install a server and I have not chosen to install one. Anyway, thank you very much for helping me clarify some things.

---

### Post by cariboo on 2009-04-17
.gvfs runs with a permission of 500 which means it is set to read by owner, search/execute by owner. It is needed by nautilus to mount shared folders. For instance if you have a server with shared folders, nautilus will automagically mount the folders.

> chown: cannot access `/home/admiral/.gvfs': Permission denied

that is normal.

Jim

---

### Post by Regele IONESCU on 2009-04-17
> **cariboo907 said:**
> .gvfs runs with a permission of 500 which means it is set to read by owner, search/execute by owner. It is needed by nautilus to mount shared folders. For instance if you have a server with shared folders, nautilus will automagically mount the folders.



that is normal.

Jim

Thank you Jim! I managed to see that launching screen. It says "launching http cache cleaner" so I think it is ok.

---

