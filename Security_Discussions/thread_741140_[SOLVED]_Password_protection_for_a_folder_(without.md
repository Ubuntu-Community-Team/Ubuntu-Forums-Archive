---
title: "[SOLVED] Password protection for a folder (without encryption)"
date: 2008-03-31
forum: Security Discussions
---

### Post by MountainX on 2008-03-31
I would be interested in this too. Is there any way to do it?

---

### Post by MountainX on 2008-03-31
Is there a simple way to just put a password on a folder? I don't need the folder contents encrypted. I want something really simple - just a one-time password for seeing the folder contents in Nautilus might be enough. Can that be done?

---

### Post by lespaul_rentals on 2008-03-31
You could always archive the folder in RAR and encrypt it with a password.

---

### Post by MountainX on 2008-03-31
Thank you, but I'm looking for something even simpler. I don't want to encrypt or compress the contents because that requires time and it also requires *altering* the content. I just want to stop casual browsing but I don't want to touch the content. (I'm not concerned about real security either.)

---

### Post by MountainX on 2008-03-31
EDIT: now that this has been moved to a new thread, my question is this:
How can I password protect a folder? I want a very simple solution that doesnt' change the contents (no compression or archiving) and doesn't take any time. I simply want to put a password on a folder.

Old comment (before thread was split):
I need to do something exactly like that, but for just one application. I want to continue working in other applications. 

Or maybe I just move that app to another desktop and blank/lock just one of my four desktops...

Any ideas about that?

---

### Post by pietjanjaap on 2008-03-31
Maybe truecrypt, is a little different but very good.

---

### Post by MountainX on 2008-03-31
I'm already using TrueCrypt. What I'm looking for is a simple, quick, easy way to just specify that someone cannot causally browse into a folder I have already decrypted/mounted. 

That's also why I don't want to rar it or anything else that changes the content. I'm just looking for one more layer of protection on top of TrueCrypt.

Like the OP said, "wondering if there is a way to password protect certain folders on my desktop" but in my case, the folders are stuff that has been mounted with TrueCrypt.

I'm just trying to avoid unmounting when I will be using the stuff again very soon -- and in fact, I'll be sitting at my computer during this time, but I may be working on another task before I get back to using that TrueCypt mounted folder. (Unmounting and remounting is something I only want to do at the start and end of the work day because it is very time consuming.)

---

### Post by markjensen on 2008-03-31
> **MountainX said:**
> I would be interested in this too. Is there any way to do it?
This gets asked every now and then, but I am of the mind that user account separation takes care of file access.   Not sure what advantage there is in protecting your file from.. well.. you.

There are ways to completely encrypt your volume, if that is something you are interested, but I have never done so, so don't know of any specific apps.  Here is a link:
[http://www.debianadmin.com/filesystem-encryption-tools-for-linux.html](http://www.debianadmin.com/filesystem-encryption-tools-for-linux.html)

---

### Post by cdenley on 2008-03-31
There is no way that I know of to force yourself to enter a password for a directory you own which is on a mounted filesystem. You can make root the owner of the directory and remove access for anyone else. Then the only way to access the directory would be
```

gksu nautilus ~/mydir

```
Then, you would not be able to copy from that nautilus window to another unless it was also running as root. Programs would not be able to access the directory unless they were running as root. It would be more secure to create a new user as the owner of your directory, since running things as root is not a good idea unless you are changing system settings. Also, unix permissions can easily be defeated by local users by booting with recovery mode or a livecd, which is why encryption is used.

Basically, that's not the way that unix filesystems (or ntfs) work.

---

### Post by MountainX on 2008-03-31
> **cdenley said:**
> There is no way that I know of to force yourself to enter a password for a directory you own which is on a mounted filesystem. You can make root the owner of the directory and remove access for anyone else. Then the only way to access the directory would be
```

gksu nautilus ~/mydir

```
Then, you would not be able to copy from that nautilus window to another unless it was also running as root. Programs would not be able to access the directory unless they were running as root. It would be more secure to create a new user as the owner of your directory, since running things as root is not a good idea unless you are changing system settings.
.

Those are very helpful ideas. Thank you very much!

If I use another user account instead of root, is there a "run as" command that would be similar to gksudo but would invoke the command for the new non-root account?

---

### Post by cdenley on 2008-03-31
```

gksudo -u notroot nautilus

```

---

### Post by MountainX on 2008-03-31
I think this is a great solution for my needs. Thanks!

---

### Post by lespaul_rentals on 2008-04-02
To my knowledge, there isn't such a way to do this (there isn't in Windows either).  Any form of "password protection" would require some encryption, no matter how minimal.  Otherwise, someone could simply hexdump the contents of the folder or file and get all your personal information, which is not secure at all.  Any password protection solution thus involves a form of encryption.

Like I said before, a RAR archive is probably the fastest and most simple way to password-protect a directory or file.  As mentioned before, loopback encryption would also do the job, as would a solution such as TrueCrypt.

If you want to hide the folder from the very casual observer (from the sounds of it, maybe you have some personal diary entries that you don't want read, or maybe some pr0n or something) you could just put a period in front of the name of the folder and it will be hidden.  So, if you wanted to hide a folder, you'd make the name .whatever

Other than that, sorry, I don't think there's a solution if you aren't willing to use encryption.

---

### Post by jken146 on 2008-04-02
Take advantage of the wonderful file permissions system that Linux has.  Change the permissions on that file so that only your user can read it.

---

### Post by MountainX on 2008-04-02
> **lespaul_rentals said:**
> To my knowledge, there isn't such a way to do this (there isn't in Windows either).  Any form of "password protection" would require some encryption, no matter how minimal.  

For Windows see:
[http://www.freedownloadscenter.com/Search/folder_lock.html](http://www.freedownloadscenter.com/Search/folder_lock.html)
and many other sites too.

Password protection and encryption do not have to be married.

In my mind, password protection can be thought of as using a lock on the front door of your house. Encryption might be like hiding all the valuables in your house so that even if someone gets in they won't see the valuables. Of course that is a stupid analogy, but the point is that they can be used together or that either one (password protection / encryption) can be used without the other.

---

### Post by lespaul_rentals on 2008-04-02
> **MountainX said:**
> For Windows see:
[http://www.freedownloadscenter.com/Search/folder_lock.html](http://www.freedownloadscenter.com/Search/folder_lock.html)
and many other sites too.

Password protection and encryption do not have to be married.

In my mind, password protection can be thought of as using a lock on the front door of your house. Encryption might be like hiding all the valuables in your house so that even if someone gets in they won't see the valuables. Of course that is a stupid analogy, but the point is that they can be used together or that either one (password protection / encryption) can be used without the other.

All the links that I saw on that page used some form of encryption.  You have to, or else the password is worthless.  I understand you don't care about encryption, but the fact is, all of the solutions that you could use involve encryption.

I don't see what's the big hassle about encrypting the data you want to keep hidden with 64-bit encryption at most.  It will allow you to password-protect the folder, and won't take long for your system to calculate.

---

### Post by MountainX on 2008-04-02
I do appreciate all the replies. My original question was:

"Is there a simple way to just put a password on a folder?"

I stated that I don't need the folder contents encrypted and that I want something really simple.

It appears that that exact solution isn't available for Linux. (BTW, there was stuff like that for older versions of Windows and I think these latest products for Windows XP & Vista offer both encryption as well as simple password protection without encryption although I haven't tried them.)

However, I think I found a really good solution for Ubuntu: BasKet Note Pads.

It allows me to put a password on a basket (which is like a folder of notes). It is dead simple and it works exactly like I want it to work. So it isn't exactly what I had in mind when I first asked about this, but I think it will solve my needs extremely well!

BasKet is a KDE app, but it runs surprisingly well on Ubuntu. It loads up even faster than Tomboy!

---

