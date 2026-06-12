---
title: "prevent accidental deletion of files?"
date: 2007-04-16
forum: Server Platforms
---

### Post by tr333 on 2007-04-16
What's the best way to prevent accidental deletion of files?
I currently have "alias rm='rm -i'" in my .bashrc, but that only works for standard "rm" and not "sudo rm".
Is it possible to convert all usage of "sudo rm" to "sudo rm -i"?
I heard that it might be possible using /etc/sudoers file but I have no idea how that would work.

---

### Post by BoneKracker on 2007-04-17
You can make a file "immutable"```

sudo chattr +i /boot/vmlinux
```See "man chattr".

You can also remove write permissions on a file:```
sudo chmod -w /boot/vmlinux
```See "man chmod".

---

### Post by MJN on 2007-04-17
> **tr333 said:**
> What's the best way to prevent accidental deletion of files?
I currently have "alias rm='rm -i'" in my .bashrc, but that only works for standard "rm" and not "sudo rm".
Is it possible to convert all usage of "sudo rm" to "sudo rm -i"?
I heard that it might be possible using /etc/sudoers file but I have no idea how that would work.
 
I don't think your strategy will work in the long run anyway....
 
To begin with the interactive prompt will make you think 'hmm... am I sure?'. That's good. However, after you get used to it, and perhaps a bit annoyed at being inconvenienced (i.e. 'are you sure you're sure?' syndrome) then you'll probably just hammer through y y y y y y y (or even 'a') to get them all deleted. Then you'll realise you deleted one you shouldn't have just as before.
 
I could be wrong, of course.
 
Might be better to rely on self-control and discipline rather than technology when it comes to using sudo rm (and sudo rm -fr in particular!)!
 
Mathew

---

### Post by johnnymac on 2007-04-17
HAHA!!  Holy cow - that is EXACTLY what I do to my Linux users that are constantly asking me to retrieve files they deleted.....

I've aliased rm for their user account to a script I created that copies the files to a tmp location....hah.  The directory is cleaned out once a week.....but works and saves me TONS of headaches...

---

### Post by tr333 on 2007-04-17
> **johnnymac said:**
> HAHA!!  Holy cow - that is EXACTLY what I do to my Linux users that are constantly asking me to retrieve files they deleted.....

I've aliased rm for their user account to a script I created that copies the files to a tmp location....hah.  The directory is cleaned out once a week.....but works and saves me TONS of headaches...

sounds like a good idea!

the problem that i face is that i'm constantly doing "sudo rm *~" to remove temp backup files in a folder and sometimes i miss out the ~ and accidentally do "sudo rm *" instead :lol:

---

### Post by thornomad on 2007-04-17
You can try using the libtrash package; once it is setup, you have a "Trash" in your user ~/Trash folder.  If you set it to run when you start your bash session, any time you rm something it will move to the trash.  You can have a script to empty the trash periodically.

I would like to see this work with sshfs though ... still working on that (netatalk isn't a problem).

---

### Post by tr333 on 2007-04-23
> **thornomad said:**
> You can try using the libtrash package; once it is setup, you have a "Trash" in your user ~/Trash folder.  If you set it to run when you start your bash session, any time you rm something it will move to the trash.  You can have a script to empty the trash periodically.

I would like to see this work with sshfs though ... still working on that (netatalk isn't a problem).

looks like what i want.  thanks.

---

