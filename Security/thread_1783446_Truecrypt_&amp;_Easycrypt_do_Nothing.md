---
title: "Truecrypt &amp; Easycrypt do Nothing"
date: 2011-06-15
forum: Security
---

### Post by Ichido on 2011-06-15
I have repeatedly installed Truecrypt and Easy Crypt but they do not "See" each other nor do they Encrypt Any Folder or File.

Easycrypt keeps telling me that I do not have Truecrypt installed!?

I cannot get help from the Truecrypt Forum.

Can anyone help me here?

---

### Post by Dave_L on 2011-06-15
Since the current version of Truecrypt includes a GUI, why do you need EasyCrypt?

I installed Truecrypt 7.0a (in Ubuntu 10.04) by downloading truecrypt-7.0a-linux-x86.tar.gz from [http://truecrypt.org/](http://truecrypt.org/), extracting its contents truecrypt-7.0a-setup-x86, and running the command:
```
sudo sh ./truecrypt-7.0a-setup-x86
```

I think TrueCrypt gets added to the Applications >> Accessories menu. Or you can launch it with the command:
```
truecrypt
```

---

### Post by BkkBonanza on 2011-06-15
I used Synaptics to install Truecrypt from the repos. That worked fine. It adds an item to the menus that calls up the Truecrypt GUI and you can use it from there. I haven't used EasyCrypt so it's probably not needed now.

Truecrypt is not for encrypting specific files on demand but for creating encrypted volumes or devices that you can use as containers for storing files. After creating a volume you would need to mount it and then you can store files in the volume. You can create/mount/dismount volumes from the Truecrypt GUI interface.

If you simply want to encrypt a file by itself to send / protect it then you can use gpg for that. Normally that's done at the command prompt but it is possible to add a Nautilus menu item to make it easier to do with a right-click.

---

### Post by Soul-Sing on 2011-06-16
[https://bugs.launchpad.net/easycrypt/+bug/374113](https://bugs.launchpad.net/easycrypt/+bug/374113)

---

### Post by Ichido on 2011-06-17
> **leoquant said:**
> [https://bugs.launchpad.net/easycrypt/+bug/374113](https://bugs.launchpad.net/easycrypt/+bug/374113)

Thanks, I have removed Easy Crypt.

---

### Post by Ichido on 2011-06-17
> **Dave_L said:**
> Since the current version of Truecrypt includes a GUI, why do you need EasyCrypt?

I installed Truecrypt 7.0a (in Ubuntu 10.04) by downloading truecrypt-7.0a-linux-x86.tar.gz from [http://truecrypt.org/](http://truecrypt.org/), extracting its contents truecrypt-7.0a-setup-x86, and running the command:
```
sudo sh ./truecrypt-7.0a-setup-x86
```

I think TrueCrypt gets added to the Applications >> Accessories menu. Or you can launch it with the command:
```
truecrypt
```

Thanks, I have done that.
Truecrypt is in my menu, but it doesn't encrypt anything.

---

### Post by Ichido on 2011-06-17
> **BkkBonanza said:**
> 
Truecrypt is not for encrypting specific files on demand but for creating encrypted volumes or devices that you can use as containers for storing files. After creating a volume you would need to mount it and then you can store files in the volume. You can create/mount/dismount volumes from the Truecrypt GUI interface.

I have created a "Container" but none of the files in it are encrypted.
The container is visible and so are the files in it.
When I double-click a file inside the "Container" it opens and is Readable/Viewable.
No password is ever asked for?
What am I doing wrong?

---

### Post by aeronutt on 2011-06-17
The container will be open and readable as long as you have the truecrypt 'partition' mounted. using the Truecrypt GUI, dismount all partitions, then try to read that container. You can't. Then, using the Truecrypt GUI, mount the container...it will ask you for your password.

So, basic principle:
Use Truecrypt GUI to mount container/partition, which is when you'll be asked for your password.
Use container: copy files, edits files, etc. Paste files into/out, etc. Acts like a regular folder.
Use Truecrypt GUI, to close/dismount container/partition, and it'll be secure.

There's a 'basics' section in the Truecrypt documentation, recommend you read it.

---

### Post by Ichido on 2011-06-18
My error message reads:

Unable to unmount truecrypt7
umount: /media/truecrypt7 is not in the fstab (and you are not root)

If I cannot Unmount, then it is NOt Protected?!

---

### Post by aeronutt on 2011-06-18
Are you using truecrypt to unmount, or the umount command?

---

### Post by Ichido on 2011-06-18
I think I figured it out :-\

Thanks for the reply.

---

### Post by Soul-Sing on 2011-06-19
> **aeronutt said:**
> Are you using truecrypt to unmount, or the umount command?

command? its a guide with one option.
truecrypt isn't a commandline product anymore.

---

### Post by aeronutt on 2011-06-19
> **leoquant said:**
> command? its a guide with one option.
truecrypt isn't a commandline product anymore.

From his posts, it wasn't clear he wasn't trying to unmount the truecrypt partition with the linux 'umount' command, hence, my question.

---

### Post by gordintoronto on 2011-06-19
> **BkkBonanza said:**
> I used Synaptics to install Truecrypt from the repos...

What repo?

---

### Post by BkkBonanza on 2011-06-20
I just checked in Synaptics and it shows up in the Base System section. That has no tag for Universe or Multiverse so I don't know what they call that - base maybe? Anyway if you type truecrypt into the search it should show up.

---

### Post by gordintoronto on 2011-06-20
In 10.10, when I search for truecrypt, it finds gdecrypt and easycrypt, but not truecrypt. I think I got similar results in 11.04.

Hmmm. I also don't have a Base System section.

---

### Post by slooksterpsv on 2011-06-20
> **gordintoronto said:**
> In 10.10, when I search for truecrypt, it finds gdecrypt and easycrypt, but not truecrypt. I think I got similar results in 11.04.

Hmmm. I also don't have a Base System section.

Honestly, it's just as easy to download it from the internet and install it. I mean if you know how to run files in terminal using sudo, or gksudo, you're good.

There's probably a PPA for it somewhere, I just don't know where.

---

### Post by aeronutt on 2011-06-20
google truecrypt.
go to download section.
select linux debian.
download.
uncompress.
run & install.
done. 

:)

(Yea, would love to find a PPA for it, but it doesn't get updated very often, it's pretty stable.)

---

### Post by gordintoronto on 2011-06-22
That's exactly what I did. However, it turns out that Truecrypt is "the long way round" for what I want to do.

---

