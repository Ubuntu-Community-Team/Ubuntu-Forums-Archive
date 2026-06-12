---
title: "[SOLVED] Backing up encfs encrypted directories, and decrypting the backups"
date: 2008-08-24
forum: Security
---

### Post by amac777 on 2008-08-24
Hello, I am currently researching a way to have an encrypted directory. So far I really like the sound of encfs because I use rsync to backup my computer to a remote server and it looks like rsync will be able to do incremental backups of only the new and changed files even for the encrypted information when using encfs. I also like that I don't have to specify in advance how much space for encrypted data I will need.

But I'm worried about getting locked out of my encrypted data if something should happen to my main computer and I'm forced to actually rely on my backups. I'm wondering if there any issues that I need to be aware of for restoring the encrypted data from my backups?

Reading the encfs home page (see [http://www.arg0.net/encfsintro](http://www.arg0.net/encfsintro)), it says:

> "Note about backups: In order to decrypt a file, two things are required (besides the encrypted file data): the password, and the “.encfs5” control file at the top level of the raw encfs filesystem." 

So in addition to that, I'm wondering if there are any differences between the various Ubuntu versions or later updates to encfs that would render my backed up data undecryptable? For example, if I backup some encrypted data (including the .encfs5 control file) now, will it be possible to access (decrypt) that data many years from now when I'm running a new Ubuntu version? What if I'm no longer running Ubuntu, or heaven forbid, Ubuntu no longer exists? Do I need to be worried about backing up the exact version of the encfs program itself to ensure I can still get to my data in the future?

Thanks for any help or comments!
Andrew

---

### Post by stimpack on 2008-08-25
The encfs directory structure works very nicely with rsync. You will have no problems backup up and restoring, even to different locations.

Lets say encfs development dies and support dies and it disappears from the repositories in future versions. You should still be able to download the source from somewhere and compile it. But lets also say a kernal change renders encfs unrunnable.. I think downloading an old version of ubuntu and running it in a virtual machine like VirtualBox would regain your access to the data letting you migrate it elsewhere.

I'm sure these are probably not the best or most elegent methods either, so I think there is plenty of safety, if the unexpected happens.

---

### Post by amac777 on 2008-08-26
Thanks for your answer. Running an old version of Ubuntu in a virtual machine would surely work if worst comes to worst. So I feel more confident now with this setup. Also I got encfs installed and working as well and it is just what I was looking for. I also tried restoring from a seperate computer using only the encrypted data from the backup and it works fine. So I'm gonna mark this thread solved. Easy.

---

