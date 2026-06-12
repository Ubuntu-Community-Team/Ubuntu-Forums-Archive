---
title: "[SOLVED] Get permission"
date: 2008-11-21
forum: Security
---

### Post by johannes_h on 2008-11-21
Hello.
I want total permission to everything..
ATM I am making a homepage.. I'm running it with xampp from localhost.. Every (fu#"!ing) time I make a new file, I have to do it from my terminal, cat > new.file.php and then chmod 777 new.file bla bla bla... 

The files that I have to save are located in /opt/lampp/prosjekt/ and from my text-editor, I can't save anything there, or make new folders before arranging everything from my terminal.. it's simply driving me insane..

Thanks ;)

---

### Post by aysiu on 2008-11-21
How about this? ```
sudo chown -R $USER:$USER /opt/lampp/prosjekt/
```

---

### Post by Afkpuz on 2008-11-21
First off, is there any way that you can move your project to your home folder?  That would be ideal as you wouldn't have to mess with permissions.  But, if that's not an option, you could just give yourself permission to whatever folder you're working in without wiping the whole system of permissions.

```
sudo chown user:user /foldername
```

replace user with your username and foldername with whatever folder you want.  Then, you can right click on that folder in a file browser and set permissions to your hearts content.  Make sure you click the "apply permissions to enclosed folders/files".


*Edit***
aysiu beat me to it.  Just own the folder, not your whole drive

---

### Post by bodhi.zazen on 2008-11-21
Permissions are frustrating at first, but after a while they are quite easy (dare I say natural ?).

You should probably not use 777

[uhelp]community/FilePermissions[/uhelp]

---

### Post by johannes_h on 2008-11-21
Thanks for all the answers! Why should I not set 777? When I set owner: 7, group 5, and other 5, I still can't save the file. Am I not the owner (using text-editor to save)? Who is other, and who is group?

---

### Post by Dr Small on 2008-11-21
> **johannes_h said:**
> Thanks for all the answers! Why should I not set 777? When I set owner: 7, group 5, and other 5, I still can't save the file. Am I not the owner (using text-editor to save)? Who is other, and who is group?
Permissions are set in three different groups:
OWNER  GROUP  OTHER

For each number, you are specifing either OWNER, GROUP or OTHER.
The number 777 gives RWX-RWX-RWX (read, write, execute) to OWNER, GROUP and OTHER. Generally not a good idea. The GROUP can be set by chown'ing the file/directory:
```
chown $USER:group file
```

If you own the files, it is always best to set the files to 755 (RWX-RX-RX) to disallow the group and others to write to your files. If you are paranoid, you set it to 700 (RWX--), so only you can access your files.

---

### Post by johannes_h on 2008-11-21
When I set it to 755, I can't save my files (from text-editor)!

---

### Post by Dr Small on 2008-11-21
> **johannes_h said:**
> When I set it to 755, I can't save my files (from text-editor)!
Did you try aysiu's response? It looks to be the best option.

---

### Post by johannes_h on 2008-11-22
Now it's working, don't know what new I did..

EDIT: But thanks guys!

---

