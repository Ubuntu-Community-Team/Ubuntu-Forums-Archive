---
title: "hxsetup ?"
date: 2005-01-21
forum: The Cafe
---

### Post by ThePainter on 2005-01-21
Hi,
I use Firefox to download files from the net.
I have it set to download to a folder in /home.
In this folder is a folder named hxsetup.
It is locked up and belongs to root.
does anyone know what it is ?
Is it necessary ?
How do I remove it if it isnt necessary ?
Is it something to do with the download list that Firefox keeps ?

Thanks if you can help  :D

---

### Post by Randabis on 2005-01-21
[QUOTE=ThePainter]Hi,
I use Firefox to download files from the net.
I have it set to download to a folder in /home.
In this folder is a folder named hxsetup.
It is locked up and belongs to root.
does anyone know what it is ?
Is it necessary ?
How do I remove it if it isnt necessary ?
Is it something to do with the download list that Firefox keeps ?

Thanks if you can help  :D[/QUOTE]

That's because root owns /home. You should use /home/user/ instead. The reason it is setup like this is because *nix/linux are designed to be multiuser systems. hxsetup? I'm not sure, but it probably has something to do with setting up homes for users. I'd leave it alone.

---

### Post by az on 2005-01-21
"hxsetup? I'm not sure, but it probably has something to do with setting up homes for users. I'd leave it alone."

No.  This has nothing to do with Ubuntu or Debian.  
Did you try to install Helix Player?  If so, you probably extracted it as root.  Get rid of it.

You can do naughty things to your system as root.

---

### Post by ThePainter on 2005-01-21
Hi,
Ive been trying to remove it but it wont go.
I tried the root terminal and cd ing to that folder and then rm ing it out but it wont go ?
Ive got  afew things in the waste bin that wont go either, I get an error saying that the parent folder permissions wont allow it ?

I tried logging off then back on giving the name root then my root password but it just says wrong password ?

Ill end up booting up Mandrake Move Live cd and rip them out from there !

One more thing, is it safe to empty the /tmp folder, or is there a way to set it up to empty at log off ?

---

### Post by az on 2005-01-21
open up a terminal.

cd to the directory

cd .. (If I understand right, your file is in /home.  This makes you go up.)

sudo rm hxsetup

rm is remove.

mv is move
cp is copy
exit is exit
ln is link

logout is logout.

---

### Post by ThePainter on 2005-01-21
Hi,
This is what I did and it didnt work ?

steven@x1-6-00-07-e9-6e-a8-f3:~ $ cd /home/steven/"My Downloads"
steven@x1-6-00-07-e9-6e-a8-f3:~/My Downloads $ sudo rm hxsetup
Password:
rm: cannot remove `hxsetup': Is a directory

Any more ideas ?

---

### Post by Randabis on 2005-01-21
[QUOTE=ThePainter]Hi,
This is what I did and it didnt work ?

steven@x1-6-00-07-e9-6e-a8-f3:~ $ cd /home/steven/"My Downloads"
steven@x1-6-00-07-e9-6e-a8-f3:~/My Downloads $ sudo rm hxsetup
Password:
rm: cannot remove `hxsetup': Is a directory

Any more ideas ?[/QUOTE]

rm -rf hxsetup

---

### Post by ThePainter on 2005-01-21
Hi,
Ive got rid of it,
I tried to shange the owner with "chown" and it said it couldnt get the attributes ?
I then tried to delete the folder it was in and it went ?

strange  8-[

---

### Post by ThePainter on 2005-01-22
Hi,
Ive had a search through the help and I cant find a reference to -rf what is this command ?

Ive discovered that I was using rm to try to remove a directory, where I should have used rmdir or unlink, although the help says it can cause problems using unlink and then you should run fsck to check the file system, but this is a bit deep for me at the moment, Im just happy to be rid of the directory.

Some learning curve this Linux stuff ?
Its like a modern rubik cube, at the moment Im happy to get one row the same colour  =D>

---

### Post by az on 2005-01-22
"Ive had a search through the help and I cant find a reference to -rf what is this command ?"


Do man rm

-rf is a command line argument (two actually)


"Ive discovered that I was using rm to try to remove a directory, where I should have used rmdir or unlink, although the help says it can cause problems using unlink and then you should run fsck to check the file system, but this is a bit deep for me at the moment, Im just happy to be rid of the directory."

rmdir would be what you want.

---

### Post by ThePainter on 2005-01-22
Hi,
Im sorry about that, Im just getting to know this, I didnt realise there are a few different help methods.
So it means remove, force remove and recursive, remove all the subdirectories as well.
or rmdir- remove directory.
Is that right ?

---

### Post by jensyt on 2005-01-22
[QUOTE=ThePainter]Hi,
Im sorry about that, Im just getting to know this, I didnt realise there are a few different help methods.
So it means remove, force remove and recursive, remove all the subdirectories as well.
or rmdir- remove directory.
Is that right ?[/QUOTE]

rm -rf will do exactly as you stated: it will force remove and do it recursively.

rmdir, when used just like that, will only remove an empty directory.

---

### Post by Moinul Abrar on 2009-12-23
[SIZE=3]Hello **ThePainer**
[/SIZE][SIZE=3]I am having the same problem with my Ubuntu 9.10 Karmic Desktop PC. 
[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]After download **RealPlayer **from internet, there is a [/SIZE]                                  [B][COLOR=#ff0000][SIZE=3]hxsetup [COLOR=Black]folder on my Ubuntu desktop. 
[/COLOR][/SIZE][/COLOR][/B]
[B][COLOR=#ff0000][SIZE=3][COLOR=Black]
  [/COLOR][/SIZE][/COLOR][/B]   [COLOR=#000000][SIZE=3]It is a locked folder. Folder name is [COLOR=Red]hxsetup.[/COLOR][/SIZE][/COLOR]    [COLOR=#000000][SIZE=3] This folder can't open, delete & can't move to Trash. I think, it may be a virus.

I use a [/SIZE][/COLOR][COLOR=#000000][SIZE=3]**Avast! **Linux Home Edition Version 1.3.0 [/SIZE][/COLOR][COLOR=#000000][SIZE=3]antivirus. This antivirus can't scanned and delete it. [/SIZE][/COLOR][COLOR=#ff0000][SIZE=3][COLOR=Black]It[/COLOR] [/SIZE][/COLOR][COLOR=#000000][SIZE=3]is located in [COLOR=Black]/home/abrar/Desktop/[COLOR=Red]hxsetup[/COLOR][/COLOR][/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]
Now my pc is too slow & HD LED is continue flashing light.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]With regards,[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Moinul Abrar.
[/SIZE][/COLOR]

   [B][COLOR=#ff0000][SIZE=3]
[/SIZE][/COLOR][/B]

---

