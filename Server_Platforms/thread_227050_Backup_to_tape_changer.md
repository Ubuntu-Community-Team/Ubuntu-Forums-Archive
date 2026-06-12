---
title: "Backup to tape changer"
date: 2006-08-01
forum: Server Platforms
---

### Post by neufena on 2006-08-01
I’ve recently acquired an old server with a HP 6 tape changer in it.  I want to do a simple backup of just the data on the sever.  I’ll want to run this weekly.  The tapes are 12/24/gb and I have around 80gb to back up so I need something that will switch tapes.

Can anyone suggest how to do this?  I’ve looked at AMANDA and it looks a little to complicated for such a simple backup job.  However things like tar and dump don’t support multiple tapes.  Any links to a good Howto would be a start.

Thanks,
Neufena

---

### Post by Randomskk on 2006-08-01
I'm betting you've got DDS-3 tapes (because of the capacity).
I've got a 4-tape changer, and also use it for my server.

If you're willing to write a small script to change tapes, the basic commands to work with tape drives are:
[PHP]
## Load up a root console. Just use this for the tape stuff, type "exit" to quit it after.
sudo -i

## Then, link the actual devices to where the tools expect them to be
ln /dev/st0 /dev/tape
ln /dev/sg1 /dev/changer

## Checking status..
# to check what tapes are present etc:
mtx status
# which outputs this:
root@x:~$ mtx status
  Storage Changer /dev/changer:1 Drives, 4 Slots ( 0 Import/Export )
Data Transfer Element 0:Empty
      Storage Element 1:Full
      Storage Element 2:Full
      Storage Element 3:Full
      Storage Element 4:Full
# This means that no tapes are loaded, and all the storage drives are full

# check status of loaded tape
mt status

# this outputs basic info, is most useful to check there is definitely a tape / whether it's rewound or not

## To load a tape for use:
mtx load 1 OR mtx load 2 OR mtx load 3 ETC
# in other words, mtx load x, where x is the tape number you want loaded.
# you can also use "mtx load first", "mtx load last" and "mtx load next"
# which do what it sounds like they do.

#then, erase the tape and rewind to the start for writing
mt erase
mt rewind

## to actually write to it, using tar:
tar zcf /dev/tape /folder/you/want/written

## to read back:
#rewind tape
mt rewind
#change to where you want to write the data
cd /folder/for/data
#read from tape
tar xcvf /dev/tape
#verify data wrote correctly
ls
[/PHP]

It should be easy enough to make a simple script that will run the commands as you need.

---

### Post by neufena on 2006-08-01
Thanks, I’d found the commands you've listed but the bit I can't work out is how to tell when a tape is full then switch to the next tape.

My situation is I have a data directory with various subdirectories for movies, mp3's documents etc.  Overall they take up more than 60-80gb so I need to be able to fill the first tape, change to the next then resume writing.

Thanks,

---

### Post by Randomskk on 2006-08-02
Hrm. You'll have to experiment, but tar will probabaly stop when it runs out of space, perhaps you could work out a way to continue from where it left off?

---

### Post by Glut on 2006-08-03
Please consider amanda, it's relatively easy to setup and can handle tape libraries without a problem.

---

