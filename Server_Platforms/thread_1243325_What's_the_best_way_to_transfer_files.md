---
title: "What's the best way to transfer files?"
date: 2009-08-18
forum: Server Platforms
---

### Post by mag1 on 2009-08-18
I setup a simple test web server to play around with, i can see it works if i browser to the ip but i've not done anything with it yet, i want to move files across from my desktop pc to test out some web page designs, what's the best way to do this?

I did try browsing to it using nautilus but strangely even though i used the right admin name and password i can't change any of the existing files, i did look at the server guide and im guessing it has something to do with permissions but i used admin so im not sure what's going on, could someone guide me in exactly what i need to do to fix this, thanks.

---

### Post by wojox on 2009-08-18
ssh:
```
scp file-to-send user@host:/path/to/place/file
```

[http://www.debian-administration.org/article/Transferring_files_with_OpenSSH](http://www.debian-administration.org/article/Transferring_files_with_OpenSSH)

---

### Post by mag1 on 2009-08-18
Lol very funny, i had a feeling someone might post some kind of command line way to do this but seriously do people really go through the tedious process of typing out every single file to transfer by command line like that?

Seems pretty crazy if its more than the odd file occasionally, tools are made to make life easier, im guessing nautilus is the best way then, so how do i go about sorting this file permission issue?

---

### Post by fjgaude on 2009-08-18
Nautilus is fine... permissions... right click on the folder or file and then click on Properties, then on Permissions in the next little window. You likely need to be root to do all this if you are working with other than your own folders and files. That should do it... lots to learn, eh?

---

### Post by wojox on 2009-08-18
Oh sorry I thought the old drag and drop method wasn't working for you.
As far as editing what error is it giving you?

---

### Post by bear24rw on 2009-08-18
use ssh but use FileZilla as the gui, i use it all the time and it never fails, even transfered over 100GB halfway across the country once lol

sudo aptitude install filezilla

---

### Post by BDNiner on 2009-08-18
I use fireftp to transfer files to and from my computers. it is a simple ftp client add on for firefox. I just downloaded filezilla but haven't played with it much

---

### Post by mag1 on 2009-08-18
Thanks guys, also thanks wojox, i thought you might have been messing with me as i've seen an over use of the command line around here for some tasks that should have a gui, anyway i just tried logging in as root and it looks like i can but the password i used with my name when setting up the server doesn't work, yet thats the only password i've used, i don't remember being asked to make a root password either so how do i go about changing that?

I thought most stuff was done by sudo in ubuntu, if so how do you use sudo in nautilus to change a files permission or should i log in as root?

---

### Post by mag1 on 2009-08-18
After some searching i found out how to changed myself to the owner of /var/www but im a little concerned if i've done the right thing, i read the owner of that is meant to be www-data or something, it was an older thread so im not sure, is it ok, i could edit and view index.html and it worked when i browsed to it in firefox?

---

### Post by BDNiner on 2009-08-18
you could always run a nautilus window as root by typing 
```

gksu nautilus

```
and then your password.

you can either run this from a terminal but i normally run it from the run box which is accessed by pressing Alt+F2

---

### Post by kangyu29 on 2009-08-18
if you have ssh and you prefer nautilus, you can just type
sftp://address:/home/username/folder 
in your address bar.

otherwise use some kind of gui for ssh is good too

I normally use rsync to copy files.

---

### Post by hessiess on 2009-08-18
> **kangyu29 said:**
> if you have ssh and you prefer nautilus, you can just type
sftp://address:/home/username/folder 
in your address bar.

otherwise use some kind of gui for ssh is good too

I normally use rsync to copy files.

+1 for rsync, it does delta uploading so has much less network overhead for frequently edited files, so is a lot faster.

---

### Post by stinger30au on 2009-08-18
giver

in 9.04

sudo apt-get install giver

---

### Post by mag1 on 2009-08-19
Thanks, i seem to be doing ok with sftp in nautilus now with the owner change i made, still not sure if it's the right/best thing to do but everything seems to work ok and it's only a test web server anyway, still if there's a proper way to go about it might be best to know.

> **mag1 said:**
> After some searching i found out how to changed myself to the owner of /var/www but im a little concerned if i've done the right thing, i read the owner of that is meant to be www-data or something, it was an older thread so im not sure, is it ok, i could edit and view index.html and it worked when i browsed to it in firefox?

:confused:

---

