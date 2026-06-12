---
title: "Linux Newbie TrueCrypt Help"
date: 2007-05-14
forum: Server Platforms
---

### Post by OhioYJ on 2007-05-14
I have a 250 gig HD, that is FAT32, one 192 GB partition, one 41 GB partition

The entire 192 GB partition was encrypted using True Crypt when I was running Windows. I'm trying to access a hidden TrueCyrpt volume.

Now I've tried both Forcefield and the terminal and I'm overlooking something.

According to GParted, the 192 GB partition that I'm trying on un-encrypt is /dev/hda5.

So I use:

**truecyrpt -i**

**Enter Volume path:** /dev/hda5
**Enter Mount Directory:**      <---- What is this, what should it be? Where I want the HD to show up? I've been leaving it blank.
**Protect hidden volume?**: Y[/b]
**Enter Keyfile path**: I leave this blank because I don't have a keyfile.
**Enter Keyfile path for hidden volume**: I leave this blank because I don't have a keyfile.
**Enter Password for '/dev/hda5':**  I enter the password for my outer volume.
**Enter hidden volume password:** I enter the password for the hidden volume I'm trying to access.

After these steps, I get dumped back off at the prompt like it did something, but I can't find the drive anywhere?

---

### Post by OhioYJ on 2007-05-14
Ok I believe I figured it out, hopefully someone can verify?

I changed the mount directory to /mnt/ 

Then my drive showed up. So now I can access the data, **but I assume the Mount Directory is where you want the drive to show up, correct? **

*****EDIT*****, ok I've come across a problem. I can only view my drive, I can't write to it. Seems only root has write privleges to it.

---

### Post by pviglucci on 2007-05-15
> **OhioYJ said:**
> Ok I believe I figured it out, hopefully someone can verify?

I changed the mount directory to /mnt/ 

Then my drive showed up. So now I can access the data, **but I assume the Mount Directory is where you want the drive to show up, correct? **

*****EDIT*****, ok I've come across a problem. I can only view my drive, I can't write to it. Seems only root has write privleges to it.


HI Ohio,

You are correct, the Mount Directory is where the truecrypt volume will appear in the filesystem.

The permission problem you are encountering is very common.  How you mount the truecrypt volume will depend on what filesystem you selected when you created the volume.  I am assuming your truecrypt volume is formatted as FAT (the default in truecrypt).    FAT is convenient because you can share truecrypt volumes between Linux and Windows easily.  However, FAT does not respect UNIX access controls so you have to fake it.  Truecrypt provides the --user-mount flag to deal with this exact issue.  Try mounting your truecrypt volume like so:

 # sudo truecrypt -u /dev/hda5 /mnt

However, I think it makes more security sense to mount the volume in a sub directory of your home.  It contains your secret files after all and not intended for other users on the system as a mount in /mnt suggests. 

Make a directory you can use in your home:

# cd ~
# mkdir vault
# sudo truecrypt -u /dev/hda5 /home/<USERNAME>/vault

If you formatted your truecrypt volume as EXT3 instead of FAT, then you can use standard UNIX file permissions to ensure you have write access to the mounted volume. In other words, with an EXT3 volume you don't use the -u flag, instead, you use chmod/chown to set the permissions/owner of the mount point. 

One more point to note if you plan on sharing files between Linux and Windows using a truecrypt volume formated as FAT32.  FAT32 has a 2GB file-size limit that EXT3 does not have.  Forget about storing those large home movies, large virtual machines etc.  You'll have to split them into 2GB chunks first.  Read up on "tar", "split", and "cat".  Splitting files if fine for archiving purposes but quickly gets old when you need them for everyday use.    If you do have to deal with large files - considering formatting your truecrypt volume as EXT3 rather than FAT and look for a EXT3 driver for Windows.

Truecrypt is a great program, I have been using it for years.  Good Luck.  


Pete
 

P.S. Forcefield is *very* much beta software in my experience.  Try "man truecrypt" and browse the truecrypt forums to learn how to use truecrypt on Linux.  You'll be better off in the long run.

---

### Post by OhioYJ on 2007-05-15
Pete you are the man!

Not only did you fix my problem, you explained the why/how the problem so it made sense. Thanks a ton!

I owe you a beer if you are ever in this direction.... 

Thanks for helping this Linux newbie out.

---

### Post by pviglucci on 2007-05-15
No problem.  

Have fun learning Linux!

---

