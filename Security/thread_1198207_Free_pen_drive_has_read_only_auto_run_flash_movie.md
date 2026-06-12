---
title: "Free pen drive has read only auto run flash movie"
date: 2009-06-27
forum: Security
---

### Post by dopple on 2009-06-27
I recently received a free pen drive and there is an annoying autorun flash movie that opens whenever it is plugged into a windows machine. The pen drive seems to be partitioned so that 2 directories are mounted in /media/ when it's plugged in.

Not a problem when I'm at home using linux but when I'm at work it gets on my nerves. Here's the history and output of some commands I have tried.

```
sudo chmod 777 20090506_1947
[sudo] password for graham: 
chmod: changing permissions of `20090506_1947': Read-only file system

sudo rm -rf 20090506_1947
rm: cannot remove `20090506_1947/autorun.inf': Read-only file system

```
After the last command it lists all of the other files in the directory as well but I didn't think listing it all would help.
 Any ideas of how to get rid of this directory?

---

### Post by kixome on 2009-06-27
format the hell out of it? That the only thing that i think would work

sudo gparted, install it if it isnt already by 
sudo apt-get install gparted

---

### Post by dopple on 2009-06-27
As it has a partition, and one of those seems to auto mount a cd, how would I do this? I have used gparted to format the drive to fat32 but I don't seem to be able to "get at" the virtual cd.

---

### Post by bobince on 2009-06-27
It may be read-only at a hardware level? That is, it might be deliberately blocking you from doing anything with the other partition.

Either way, if it runs automatically on Windows that's an extreme security risk which **will** get your machines infected with one of the many pen-drive viruses going round at the moment. You'll want to [disable autorun](http://www.publicsafety.gc.ca/prg/em/ccirc/2008/tr08-004-eng.aspx).

---

### Post by dopple on 2009-06-28
Thanks. I'll do that. It may mean there's a few mb I can't use on the drive but I don't mind that.

---

### Post by mezba_ua on 2009-07-26
please post this Pen Drive to my address
My address is
Salam Manjil (2nd Floor), House: 111, Road: 08, Shantibag R/A, P.O: Bondor, P.S: Double Mooring, N. Agrabad, Chittagong, Bangladesh.

---

### Post by dopple on 2009-07-26
Ummmm. Yeah. Sure. I'll nip down to the post office right now and do that.
Muppet.):P

---

### Post by Whiffle on 2009-07-26
After you've plugged in the pen drive, what is the output of "sudo fdisk -l" in the terminal?

---

