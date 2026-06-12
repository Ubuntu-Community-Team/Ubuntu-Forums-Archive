---
title: "cannot access encrypted files"
date: 2010-07-23
forum: Security
---

### Post by absurde on 2010-07-23
my friend has accidentally deleted the folder named "private" in her encrypted home folder. now she is unable to mount the folder that has her encrypted files.

i am supposed to help her on the phone but i myself has little experience in ubuntu. a few hints could save me days. is there a simple way to undelete or rebuild the emptied folder? is that deleted folder necessary to access the encrypted files?

i hope there's somebody that understands what im talking about. thanks for any help in advance.

---

### Post by Bachstelze on 2010-07-23
> **absurde said:**
> my friend has accidentally deleted the folder named "private" in her encrypted home folder. now she is unable to mount the folder that has her encrypted files.

i am supposed to help her on the phone but i myself has little experience in ubuntu. a few hints could save me days. is there a simple way to undelete or rebuild the emptied folder? is that deleted folder necessary to access the encrypted files?

i hope there's somebody that understands what im talking about. thanks for any help in advance.

Did your friend record the mount passphrase on a piece of paper or something?  If she didn't, the data is lost.

---

### Post by FuturePilot on 2010-07-23
Was this an encrypted Private directory or an encrypted home directory? There is no Private directory if the entire home directory is encrypted.

---

### Post by absurde on 2010-07-23
fortunately, she has every password that may be required. i suppose "it is an encrypted Private directory", because she told me that she emptied the folder named "private". 

we tried the "Recovering Your Data Manually" section on this thread - [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory) - but i am not sure if that is a suitable procedure since her computer does not have a "private" folder any more. i cannot think of any walkarounds.

---

### Post by Bachstelze on 2010-07-23
> **FuturePilot said:**
> Was this an encrypted Private directory or an encrypted home directory? There is no Private directory if the entire home directory is encrypted.

There is.

@absurde: the "mount with sudo" part of "Recovering your data manually" should work.  Just give me a sec, I'm going to try it on mine. *EDIT:* Yes, it works.

---

### Post by FuturePilot on 2010-07-23
> **Bachstelze said:**
> There is.


I don't have one :confused:

---

### Post by Bachstelze on 2010-07-23
> **FuturePilot said:**
> I don't have one :confused:

It is actually a symlink to /home/.ecryptfs/user/.Private, but it is there.  [font=monospace]mount[/font] should show it, or you can do a [font=monospace]ls -la /home/foo[/font] while logged is as another user.  Of course, when logged in as yourself, you won't see it, because it is mounted on /home/foo.

---

### Post by absurde on 2010-07-23
i need to install ubuntu on a virtual machine before i can instruct her about the procedure. anyway, knowing that it works, i think i can figure out how to make it work for her.

thank you for your help. it's very much appreciated.

---

### Post by absurde on 2010-07-27
it did not work. any ideas why it didn't?

---

### Post by Bachstelze on 2010-07-27
> **absurde said:**
> it did not work. any ideas why it didn't?

Could be a lot of things.  What are the error messages?

---

### Post by absurde on 2010-07-28
> **Bachstelze said:**
> Could be a lot of things.  What are the error messages?

at first, we had issues with the terminology -cipher, keyring, passphrase, etc. we got over the terminology issue and completed the procedure without any errors, only to see that the mounted folder includes solely the files that are already in the home folder. encrypted files seem to remain disappeared.

just if i knew more technical details, i would ask the perfect question. better to start with a practical one: do the encrypted files cost disk space even if the folder is not mounted? there is some free space on the disk which is not supposed to be there. and secondly, what happens basically when you delete the contents of */home/username/.Private*? i mean, are the actual files also erased?

---

### Post by Bachstelze on 2010-07-29
> **absurde said:**
> 
just if i knew more technical details, i would ask the perfect question. better to start with a practical one: do the encrypted files cost disk space even if the folder is not mounted?

Of course, they have to be stored somewhere.

> and secondly, what happens basically when you delete the contents of */home/username/.Private*? i mean, are the actual files also erased?

If you delete the files, they are deleted indeed.

*EDIT:* I guess I had a braindead, of course if you delete .Private, the files are gone.  For some reason I thought you just deleted the Private.* files (in .ecryptfs) that contain the passphrases...  Basically, yeah, the files are gone.

---

