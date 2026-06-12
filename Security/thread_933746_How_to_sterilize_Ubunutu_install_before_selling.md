---
title: "How to sterilize Ubunutu install before selling?"
date: 2008-09-29
forum: Security
---

### Post by BetterSense on 2008-09-29
I'm looking at selling a laptop with ubuntu installed on it. Very little actual files are on the SSD...I keep everything on flashdrives. But still, there is the matter of bookmarks, autocomplete, browsing history, stored passwords, etc. 

Could somebody please tell me what all I should do to make sure all my personal info is off the computer, before I just hand it to someone else? How can I change the user account name and password?

---

### Post by Biochem on 2008-09-29
one easy way is first to delete all the files in your home folder than enter (remember the .trash)

sudo dd if=/dev/random of=/tmp/temporary_random_file

this will create a file full of random bits that will expand until your disk is full. Delete /tmp/temporary_random_file and repeat to your heart or paranoias' content. This is equivalent to wiping free space on your hard drive.

---

### Post by solitaire on 2008-09-29
You have 2 options: 
I'd do option 2 if it's not too much hassle getting things to work!

1) All you need to do is remove your <username> folder from /home/ This folder hold all your settings and preferences and passwords etc..

2) Stick in the LiveCD and wipe the disk and install Ubuntu again... Clean install with NO personal info on it.

---

### Post by BetterSense on 2008-09-29
Ok I'd rather NOT have to reinstall...the eeePC requires multiple hacks to get everything working right and that was a selling point of the computer.

So I can 

```
rm -rf /home/*
```

Then do the empty space trick. That should wipe everything in /home. 
But then how will my customer be able to log on then? There will be no user account or password for him.

Is there anything else lurking elsewhere on the FS? All keyrings are in home? Where are all the trashes located? There isn't a /home/chaz/.trash.

---

### Post by solitaire on 2008-09-29
Yup "rm" the /Home drive then "dd" it 
I'm not sure about the ".Trash" folders or the keyrings,

---

### Post by Biochem on 2008-09-29
For a manual delete I would use the live cd remove the contents of the home partition and /tmp. then you can recreate the home dir of any user that would still be in use. Of course it is better to create the client's users after the sanitization or remove only your user not all of them. the .Trash-user directories are usually located on the root of partitions you have write accès.

---

