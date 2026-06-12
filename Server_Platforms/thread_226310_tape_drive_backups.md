---
title: "tape drive backups?"
date: 2006-07-31
forum: Server Platforms
---

### Post by mrweirdo on 2006-07-31
Hello I have a dell poweredge system runing ubuntu server 6.06 which happens to have a dat72 tape drive in it. I also have a bunch of unused tapes siting around for it and since its my fileserver I have though hrmm it might be a good idea to backup some of my more important files i wish to keep ;)

Well my questiong is how can this be done via the shell where I can manualy select a few files i wish to keep namely mp3s and a few documents in different areas on the hard disks?

Sorry for sounding so n00bish here but hte fact is I have never usedd a tape drive before in my life lol. Hope someone can point me into the right direction.

---

### Post by mrweirdo on 2006-07-31
forgot to mention the drive i have is a HP StorageWorks DAT72
or HP C7438A

---

### Post by Randomskk on 2006-07-31
Look into the commands mt and tar.
mt is used to rewind / erase / manipulate the tape itself, and tar is used to write to it.
If your drive has a tape changer as well, that can usually be controlled using mtx.

A quick tutorial to write some files to tape, then read them back:
```

##prepare the tape
sudo ln /dev/st0 /dev/tape #this sets up a symlink from the tape device to /dev/tape, which simplifies mt usage
sudo mt status # check status of a loaded tape
sudo mt erase #wipe the tape
sudo mt rewind #go to the start of the tape

##write to the tape
tar zcf /dev/tape /home/username #write /home/username to the tape (compressed)

##read from the tape
mt rewind #rewind tape to start
cd /location/you/want/to/write/to #change to where you want data to be saved to
tar zxvf /dev/tape #read from
ls #check files were read OK

```

Try that out for starters, also look into "man mt" and "man tar"

---

