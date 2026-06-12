---
title: "Changing the UUID of a FAT32 or NTFS Partition"
date: 2009-08-14
forum: Tutorials
---

### Post by clubsoda on 2009-08-14
I'm used to finding the answers to all my technical questions with a couple of 'net searches but information in this area seems a bit scarce.  

The typical scenario is that a partition has been backed up using a cloning tool like parted, then various problems appear due to the duplicated UUID.  The accepted solution is to alter the volume label on the backup partition using mlabel [mtools] and then edit /etc/fstab to have the backup partition identified using LABEL="WinWhatever" instead of UUID=89C9589FC4162F5.  That's not necessarily the end of the story though.  A live CD or reinstaller will again trip over the duplicate UUID.

A more robust solution is to alter the UUID on the backup partition and create a record of the original UUID at the same time, in case the master partition crashes and is unrecoverable.  First let's see what we've got:-```
sudo blkid
```Make a note of the partition number X of the backup partition.  Use that number instead of X in all the comands below.

Now let's grab the superblock:-```
sudo dd if=/dev/sdaX of=~/superblockX bs=512 count=1
```And edit it using hexeditor [ncurses-hexedit]:-```
sudo hexeditor ~/superblockX
```The UUID shown by blkid earlier will match the volume serial number which you should see at 0x43-0x46 for VFAT or 0x48-0x4f for NTFS.  Change it somehow and save. 

[Optional sanity check: "ls -l ~/superblockX"  The file should still be exactly 512 bytes].

Copy the modified file back to the superblock.  I don't need to mention how risky this part is.  Be sure you know what you're doing.```
sudo dd if=~/superblockX of=/dev/sdaX bs=512 count=1
```Next edit /etc/fstab with a line identifying the backup partition via its new UUID.  You might want to add noauto to the options if you don't want it mounted automatically all the time.  Finally, I suggest mounting the backup partition and adding a tag file to its root directory.  The file name should indicate the original UUID prior to editing, eg. 540C-0199.vol, as this will be needed if the master partition ever crashes catastrophically or needs to be restored.

I hope this process will all be automated one day.  See [this bug report](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/148743).

Please post back if you spot errors or if there are just better ways to do the above.  I haven't tested this on an NTFS partition yet.

References: 
How [FAT32 volume serial numbers](http://www.digital-detective.co.uk/documents/Volume%20Serial%20Numbers.pdf) are calculated.
[Some info on NTFS](http://hijack9.googlepages.com/ntfsdoc.html).

---

### Post by say2sky on 2009-08-14
Thank you for this very useful howto.

I also have partition with xfs, ext3, can I use the same solution as this one.  is there any other thing need to make change?

Anyway this is a good solution.

---

### Post by clubsoda on 2009-08-15
I'm sure you could use this method on xfs or ext3 if you're feeling adventurous. :)  Thankfully, those file systems are better supported so no need for open-block surgery.  Have a look at xfs_admin [xfstools] and tune2fs.

---

### Post by dcstar on 2010-09-07
This should patch the NTFS UUID with 8 random bytes (substitute the obvious with your actual NTFS partition designation, and **all** those spaces are required):

```
sudo dd if=/dev/urandom bs=80 count=1 | xxd -l 80 -c 8 | tail -1 | xxd -r - /dev/sd-NTFS-Partition
```

---

### Post by GMHilltop on 2010-09-07
> **dcstar said:**
> This should patch the NTFS UUID with 8 random bytes (substitute the obvious with your actual NTFS partition designation, and **all** those spaces are required):

```
sudo dd if=/dev/urandom bs=80 count=1 | xxd -l 80 -c 8 | tail -1 | xxd -r - /dev/sd-NTFS-Partition
```

Can you clarify the code for me please? Ones ( 1 ) and L's ( l ) can look very similar.

Also, could you clarify the ".... sd-NTFS-Partition" part?  is that supposed to be:
".... sdx-NTFS-Partition" where 'x' is the partition you'd like the uuid change on?

Are there any other parts of the code that we should be inserting the 'appropriate' value that is currently holding an 'x' place holder (ie the xxd part of the code)?

Thanks again for the help

---

### Post by GMHilltop on 2010-09-07
Ok, I gave this a try from a Live CD 10.04.1 LTS

I imaged a windows 7 OS to the first and 2nd partition of the hard drive and checked that they both have the same UUID by typing in ===>  sudo blkid

I assumed that: 
the count=1 was a "One" 
--- and that the xxd -l was an "L"
--- and that the   /dev/sd-NTFS-Partition   was supposed to be  .... /dev/sda1-NTFS-Partition  (assuming that it was the 1st partition on the drive that I was trying to change the UUID on.

When I ran it I got this message:
[COLOR=DarkRed]xxd:  /dev/sda1-NTFS-Partition:  Permission denied
1+0 records in
1+0 records out
80 bytes (80 B) copied, 0.000107521 s, 744 kB/s[/COLOR]

[COLOR=Black]Does anyone here have a suggestion as to how to make this work as it would be VERY VERY handy to be able to change the UUID with a single line like this![/COLOR]

---

### Post by dcstar on 2010-09-12
> **GMHilltop said:**
> Ok, I gave this a try from a Live CD 10.04.1 LTS

I imaged a windows 7 OS to the first and 2nd partition of the hard drive and checked that they both have the same UUID by typing in ===>  sudo blkid

I assumed that: 
the count=1 was a "One" 
--- and that the xxd -l was an "L"
--- and that the   /dev/sd-NTFS-Partition   was supposed to be  .... /dev/sda1-NTFS-Partition  (assuming that it was the 1st partition on the drive that I was trying to change the UUID on.

When I ran it I got this message:
[COLOR=DarkRed]xxd:  /dev/sda1-NTFS-Partition:  Permission denied
1+0 records in
1+0 records out
80 bytes (80 B) copied, 0.000107521 s, 744 kB/s[/COLOR]

[COLOR=Black]Does anyone here have a suggestion as to how to make this work as it would be VERY VERY handy to be able to change the UUID with a single line like this![/COLOR]

Why do I have to explain the bloody obvious?

I do not know what **YOUR** NTFS partition is, REPLACE that with the actual designation of your NTFS partition.

If you are not able to identify what partition you are supposed to be working on that I strongly advise you not to use commands like this until your Linux skills significantly improve.

---

### Post by GMHilltop on 2010-09-12
> **dcstar said:**
> Why do I have to explain the bloody obvious?
Because OBVIOUSLY there was room in _**YOUR POST**_ for 'misinterpretation'.

> **dcstar said:**
> I do not know what **YOUR** NTFS partition is, REPLACE that with the actual designation of your NTFS partition.

Yeah, that part too was "bloody obvious", and counter productive.

For  future reference when giving advice, most times, an example (just to be  absolutely clear) goes a long long way towards helping others _completely_ understand what it is you are saying.

That too should have been "bloody obvious" to you.
You choose to ignore that however (and the other OBVIOUS questions), and instead decided to be snippy.

> **dcstar said:**
> If you are not able to identify what partition you are supposed to be working on ...

I would have thought:
[COLOR=DarkRed]"...         /dev/sda1  ....  (_assuming_ that it was the 1st partition on the drive that I was trying to change the UUID on."[/COLOR]
was "bloody obvious" that I knew which partition it was that I was trying to change the UUID on.  No?  >>>>_sda1_<<<<

> **dcstar said:**
> .  . . that I strongly advise you not to use commands like this until your  Linux skills significantly improve.

Completely irrelevant, totally useless, and utterly pompous advise. 
Seriously, how is anything like that helpful to anyone.  WOW!
I  think that this community and forum have been amazing at helping people  learn the "bloody obvious" without being condescending.

dcstar, I  strongly advise that you be "crystal clear" with your code by "giving  examples", AND when questions are asked about the code that you have  given, that you answer ALL of them (even if to you it is 'bloody  obvious') in order to help others "improve their Linux skills  significantly".

Your last post does linux, ubuntu, and this forum a huge disservice IMHO.

===========

Now that those pleasantries are out of the way,
and,
after looking at it again and giving my head a smack for missing the *bloody obvious*,
AND at the risk of misunderstanding dcstar again,
I'll attempt to answer my queries for the _benefit of others_

The Code dcstar posted was:

```
sudo dd if=/dev/urandom bs=80 count=1 | xxd -l 80 -c 8 | tail -1 | xxd -r - /dev/sd-NTFS-Partition
```I, *by mistake*  left the "-NTFS-Partition" in when I ran the command.  Yeah that was  kinda dumb, but if I made the mistake it's possible others could too.

I'd like, for the benefit of others, to provide an _*example*_ of what _I think_ dcstar was trying to say (please dcstar correct me if I have still got it wrong):

If I was trying to change the UUID of the _first partition_ on the _first hard drive_ the code should have been this:

```
sudo dd if=/dev/urandom bs=80 count=1 | xxd -l 80 -c 8 | tail -1 | xxd -r - /dev/**sda1**
```I had:    ...... /dev/sda1_**-NTFS-Partition**_    mistakenly at the end of the code.

I have seen some posts say things like:  replace xx with ..... *(some value where the x's are representing something else)*
hence my query about the 'xxd' part of the code.

I  know, I know - dcstar didn't say anything about changing anything with  the "x's" - clearly my Linux (& reading comprehension) skills need  improving, but that is why I (and many others) are here :D, and it is not going to stop me from tinkering while I learn :biggrin:.

also, I believe the -l in the xxd -l is a lower case "L"
the count=1 is a "ONE"  ===>not sure if that was supposed to be "bloody obvious" . . . '*_count_=*1' :roll:
and in 'tail -1' . . . that I am pretty sure is a "ONE"

To Repeat dcstar's comment - ... **all** the spaces are required.

_Hopefully_ I have this right, and I haven't mislead anyone while trying to clear this up.

---

### Post by GMHilltop on 2010-10-08
Well I finally had an opportunity to sit down and tinker a little with this again.

The Code that I used in terminal was:

```
sudo dd if=/dev/urandom bs=80 count=1 | xxd -l 80 -c 8 | tail -1 | xxd -r - /dev/sda1
```

Now the result is this:
[INDENT]xxd: /dev/sda1: Permission denied
1+0 records in
1+0 records out
80 bytes (80 B) copied, 4.9104e-05 s, 1.6 MB/s
ubuntu@ubuntu:~$
[/INDENT]Can anyone clarify for me what it is that I am missing with this code?

Thanks again for the help. :)

---

### Post by GMHilltop on 2010-10-28
Ok, THIS I got to work for me - Hopefully it helps others as well.

First credit where credit is due - I got the help I was looking for here:

[Changing / Modifying an NTFS partitions UUID using dd]("http://www.linux.com/community/blogs/howto-modify-uuid-for-an-ntfs-partition.html#comment-3322")

Thank You very much to Simon Williams for taking the time to respond (See the comments to Adam's original post there).  I hope everyone here finds this as useful.

Here is The Code used:

```
sudo dd if=/dev/urandom of=/dev/[ntfspartition] bs=8 count=1 seek=9
```[COLOR=Red]**!!!!!!!!!!!!!!! WARNING WARNING WARNING !!!!!!!!!!!**[/COLOR]
For [ntfspartition] YOU MUST make sure you Identify the PROPER partition!!
ie:  sda1   or   sda2   or  sdb1  or  sdb2  or  sdc1  or sdc2   etc etc etc.
**DO NOT** put sda in there or you will SCREW your MBR !
Also you will want to run:  sudo blkid to make SURE you are modifying the proper partition.
DO NOT miss any part of the code above or you'll risk modifying more than just the UUID
**also posted at the above link with regard to the above code:**
Be warned that you can cause data loss ON ANY DISK CONNECTED TO YOUR MACHINE if you specify the wrong disk or partition, or if the partition you specify turns out to not be the one you were expecting. Disks of the "new" form /dev/sda (rather than the old /dev/hda, etc) have unpredictable ordering. Running this on a non-NTFS partition, or worse, the entire disk (e.g. /dev/sda rather than /dev/sda1) will mess things up very badly._** YOU HAVE BEEN WARNED. **_
[COLOR=Red]!!!!!!!!!!!!!!! END OF WARNING !!!!!!!!!!!!!!!![/COLOR]

as an example of the the code to be used --- if I wanted to modify the UUID of the 1st partition of the first hard drive _**IN MY SYSTEM**_ this is what I would type:

sudo dd if=/dev/urandom of=/dev/sda1 bs=8 count=1 seek=9

to do the 2nd partition of the first hard drive it would be:

sudo dd if=/dev/urandom of=/dev/sda2 bs=8 count=1 seek=9

**(Again - best verify what the system sees _IN YOUR SYSTEM_ by typing in Sudo blkid)**

Simon Williams gives a very nice breakdown as to what each piece of the code does for those who are interested (Again - it is in the comments to the original post there).
I think it is the 11th comment that starts off with "dd explained"
Comment 14 by Simon Williams that starts off with "written by Simon Williams, October 13, 2010
Yey, now that I can login again... :S "
gives even further detail to this part of the code:
/dev/urandom

Again Thanks again to Simon Williams for the assistance.  He was very professional and courteous!

---

### Post by Bouki on 2011-04-18
i want change my usb disk uuid. but i dont understand the risk!
it means if i changed , it may not working?

---

### Post by clubsoda on 2011-05-02
> **Bouki said:**
> i want change my usb disk uuid. but i dont understand the risk!
it means if i changed , it may not working?Changing the UUID won't break the disk or make it unreadable. Some software might check UUIDs to try and detect unauthorised copying.

The risk I was referring to was the risk of making a mistake when running 'sudo dd' to read or write the superblock. That could definitely make the disk unreadable.

If it's that important, I suggest you backup the usb disk using gparted before changing the UUID. Please also read the dd manual page so you know what you're doing.```
man dd
```


PS: To the thread moderator, my thanks.

---

### Post by strudel on 2011-09-09
Thank you!  It worked perfectly for me on ubuntu 11.04
-strudel

---

### Post by vkr on 2012-05-04
I wrote a script to automate this process for NTFS partitions and to avoid overwriting anything that isn't NTFS (or at least reduce the risks). I'm sure one could modify it to work with FAT as well, but it's a starting point.

```
#!/bin/dash
IFS=""

# echo with exit for error termination
exho(){
    echo "error: $1"
    exit 1
}

# convert hexidecimal UUID to binary characters
uuid2bin(){
    STBF="$1"
    while [ -n "$STBF" ]; do
        BYTE="${STBF%??}"
        BYTE="${STBF#$BYTE}"
        STBF="${STBF%$BYTE}"
        BYTE="$(printf "%u\n" "0x$BYTE")"
        echo -n "$BYTE" | awk '{printf("%c",$0)}'
    done
    return 0
}

# usage help
if [ $# != 2 ]; then
    echo "$0 <UUID> <device>"
    exit 1
fi

# test the input UUID for validity
UUID_NEW="$(echo -n "$1" | tr [a-f] [A-F])"
STBF="${UUID_NEW#[0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F][0-9A-F]}"
if [ -n "$STBF" ]; then
    exho "invalid UUID format"
fi
if [ "$UUID_NEW" = 0000000000000000 ]; then
    exho "UUID cannot be empty"
fi

# get current/old UUID value via system tool
UUID_OLD="$(blkid -c /dev/null -s UUID -o value "$2" 2>/dev/null)"
if [ -z "$UUID_OLD" ]; then
    exho "could not read old UUID using blkid on $2"
fi

# get current/old UUID value via raw read
STBF="$(dd bs=1 skip=72 count=8 if="$2" 2>/dev/null | hexdump -ve '1/1  "%02X"')"
if [ ${#STBF} != 16 ]; then
    exho "could not read old UUID using dd on $2"
fi

# reorder the hex digits since they are reversed
UUID_RAW=""
while [ -n "$STBF" ]; do
    BYTE="${STBF%??}"
    BYTE="${STBF#$BYTE}"
    STBF="${STBF%$BYTE}"
    UUID_RAW="$UUID_RAW$BYTE"
done

# matching UUIDs confirm NTFS structure
if [ "X$UUID_RAW" != "X$UUID_OLD" ]; then
    exho "$2 invalid NTFS device"
fi

# write UUID to device
if ! uuid2bin "$UUID_NEW" | dd bs=1 seek=72 count=8 of="$2" 2>/dev/null && sync; then
    exho "could not write UUID to $2"
fi

# verify UUID
UUID_RAW="$(blkid -c /dev/null -s UUID -o value "$2" 2>/dev/null)"
if [ "X$UUID_RAW" != "X$UUID_NEW" ]; then
    exho "verification of new UUID failed"
fi

# status information
echo "DEVICE:\t\t$2"
echo "OLD UUID:\t$UUID_OLD"
echo "NEW UUID:\t$UUID_NEW"
```

---

### Post by GMHilltop on 2012-05-08
I have used this many times now and it works perfectly: 
[http://ubuntuforums.org/showpost.php?p=10041428&postcount=10](http://ubuntuforums.org/showpost.php?p=10041428&postcount=10)

---

### Post by wbloos on 2013-02-18
> **dcstar said:**
> This should patch the NTFS UUID with 8 random bytes (substitute the obvious with your actual NTFS partition designation, and **all** those spaces are required):

```
sudo dd if=/dev/urandom bs=80 count=1 | xxd -l 80 -c 8 | tail -1 | xxd -r - /dev/sd-NTFS-Partition
```

This works great. Thanks.

---

