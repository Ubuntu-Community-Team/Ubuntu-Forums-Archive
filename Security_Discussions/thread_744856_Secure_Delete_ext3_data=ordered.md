---
title: "Secure Delete ext3 data=ordered"
date: 2008-04-04
forum: Security Discussions
---

### Post by Ostien on 2008-04-04
I've gotten a bit of conflicting opinions on the effectiveness of the secure delete utilities (srm, sfill etc) on ext3.  I have heard that in data=ordered mode that sfill will work fine.  

So is this true will sfill (wipes free space) work on a ext3 data=ordered filesystem?

also how would one check if the ext3 partition is data=ordered.  I heard that that is the default.

---

### Post by cdenley on 2008-04-04
Reading "man mount", it looks like data=ordered is the default. It also looks like the only difference is whether it forces the system to write the metadata after the actual data. This would only be a problem if you were using data=writeback and you didn't unmount properly. Then the write operation you were in the middle of would leave your old data where your new data was going to be written. If the meta-data was already written, your system would see all the data as being part of the new file. In this case, sfill wouldn't erase your previously unused data since it is now part of a file which never finished being written.

As far as I know sfill works fine on ext3 filesystems and overwrites all available data on a filesystem. If it is a partially written file as described above, it will not be overwritten even though the file may contain data from a previous file.

If the data=writeback mount option isn't specified in /etc/fstab or set in the superblock (sudo tune2fs -l /path/to/ext3|grep Default\ mount), then I think data=ordered is used.

---

### Post by HermanAB on 2008-04-04
It depends on the threat level.  If you are worried about your little kid sister reading your files, then any delete or overwrite scheme will work.

However, if you are worried about people with special equipment, then you have only two options:
a. Activate the secure delete utility in the drive controller to erase the whole disk. (This is very good, but still not good for military use).
b. Use a very big hammer.

Special equipment can read data off a disk platter, more than 20 layers deep - think about that before wasting your time on delete utilities.

The only good solution is to use a new disk and encrypt the /swap, /tmp and /home partitions.  To delete the data, forget the key.

Cheers,

Herman

---

### Post by cdenley on 2008-04-04
> 
Special equipment can read data off a disk platter, more than 20 layers deep - think about that before wasting your time on delete utilities.

Are you sure about that? I couldn't find anything on the internet about this actually being done on a modern drive.

---

### Post by HermanAB on 2008-04-04
You won't find detailed information about it anywhere, but I'm an ex-army signals officer.

Nowadays, you can actually buy disk drives with encryption built into the drive controller made by Seagate and others.  For financial or medical use, those things are the best.  Even the military use them, but the military still use strict procedures and destroy all media at end of life, regardless.

Cheers,

H.

---

### Post by cdenley on 2008-04-04
I know it is possible to read some noise from the track edges, but as far as I know you can't recover actual data on modern drives. It was my understanding that security precautions taken by government and military were just in case somebody developed a method for using this noise to determine what the original data used to be. As far as I know, there is no method. I was curious if this possibility was only theoretical, or if you know otherwise. The more passes you make overwriting the disk with random data, the more distorted this noise becomes, the more difficult the theoretical method becomes. Is my understanding correct? It sounds like you're the person to ask, since I won't find anything on the net.

---

### Post by niteshifter on 2008-04-04
Hi folks,

> Special equipment can read data off a disk platter, more than 20 layers deep - think about that before wasting your time on delete utilities.

Yes, it's "doable" - but at great cost (time and money). Another under-appreciated item is the error rate on bits recovered, this comes into play as well. There's a distinct difference in "knowledge" and "evidence". Your local district attorney is not likely to approve the expenditure of 1000's or tens of 1000's of dollars to acquire knowledge that can't be used reliably as evidence in court. That's US/UK/Euro/Asia-centric-ish, btw, there are other places in the world where they may just cut to the chase and get out the rubber hose (and worse). It's cheaper.

The venerable shred tool works well, perfectly so against any but top tier "attackers", by that I mean an entity like government/military or large corporations that can afford the multi-kilo-dollars equipment and the many man-hours needed. There's not all that many players on that bench (your local police aren't in this group) - and if they do elect to examine you, they already know something, and have known it for some time. IOW you're already screwed, it's now a question of how bad.

Also, the default behavior of shred is 25 passes. Feel free to spec more :)

If you're worried about what can accumulate via temporary files do this: Make a separate partition for /tmp, ensure the software you use uses /tmp for temp files. Shutdown, boot from a Live CD and shred /dev/hdaX (where /tmp is mounted), then create a fresh file system on that partition.

If the "material" you're working with is really that sensitive, don't put in /home/<user>. Create a partition just for that and treat it as above. Or use truecrypt on a usb thumb drive / SD card.

Full disk encryption isn't the perfect solution many think it to be. See this:
[http://citp.princeton.edu/memory/]("http://citp.princeton.edu/memory/")
and get the pdf and have a read. Fascinating stuff.

Easy counter-measure, however: Just turn the dang thing off AND stay with the machine for a couple of minutes afterward.

---

### Post by cdenley on 2008-04-04
> 
If you're worried about what can accumulate via temporary files do this: Make a separate partition for /tmp, ensure the software you use uses /tmp for temp files. Shutdown, boot from a Live CD and shred /dev/hdaX (where /tmp is mounted), then create a fresh file system on that partition.


Better yet, if you have enough memory to spare, mount it with tmpfs. Temporary files would never get written to disk.

Do you know for a fact that it's "doable"?

---

### Post by niteshifter on 2008-04-04
Hi,

@cdenley:

See:

[http://www.cs.auckland.ac.nz/~pgut001/pubs/secure_del.html]("http://www.cs.auckland.ac.nz/~pgut001/pubs/secure_del.html")
and note the date of publication, it's a safe assumption that the state of the art has advanced ;)

[http://scitation.aip.org/getabs/servlet/GetabsServlet?prog=normal&id=JEIME5000014000001013015000001&idtype=cvips&gifs=yes]("http://scitation.aip.org/getabs/servlet/GetabsServlet?prog=normal&id=JEIME5000014000001013015000001&idtype=cvips&gifs=yes")
There was an article on this in Scientifc American a fews years back, IIRC, but I don't have access to my archives at the moment.

Encase forensics-ware: [http://www.guidancesoftware.com/products/ef_index.asp]("http://www.guidancesoftware.com/products/ef_index.asp")
One of two software tools that have legal validity (as evidence)  in the US (via settled case law). The other? Unix/Linux' dd command.

More clues can be had by examining the offerings of the various data-recovery companies about.

{Edit} I forgot this: Note that a key item in deleted and overwritten data recovery (vs just deleted) is the statistical analysis employed. Attempting to go deep (> 15 - 20 "layers") causes bit error rates to become higher and higher. So does the cost (in man-hours and dollars). I trying to illustrate the practical vs the theoretical.

---

### Post by netlogic on 2008-04-04
Today's drives are pretty good. 3 wipes should do the trick. Today's drives are a lot neater than the past. I believe USA govt standard is 3 and German is 7 wipes.  However, there are drive experts who have various physical hardware to yank out your data. If you have a multi-million dollar information, the best thing to do is drill a big hole in it. Most people don't have patiences to fill in the missing data to put one or two data together.

---

### Post by cdenley on 2008-04-04
I'll have to read the Gutmann article later. It was easier to recover data on older hard drives because the tracks weren't as dense. I think I read somewhere that Gutmann more recently said on modern hard drives, a few passes of random data would be sufficient. The data recovery technology may have improved, but so has hard drives.

I think the idea that data must be overwritten 25 times originates from the Gutmann essay you linked, which has been referenced in other articles or essays I have read. However, it is dated, and tracks are much more dense on modern drives.

I've looked up data recovery experts, but haven't found one that claims to actually recover data which has been overwritten. I haven't spent that much time looking, though.

---

### Post by netlogic on 2008-04-04
Instead of constantly worry about this subject, I always followed the simple rule.

1. desktop drives will get wiped before they go to the trash or resold
2. server drives will go to the back room. 40mm drill bits will kill it. if 1/8th of platter is bits and pieces... no way... it takes 2mins to junk it.

There is no need to buy expensive equipments. I like to keep it simple. 40mm drill bit  should like $15. I am sure most companies can afford that.
acid, water, burning, all don't work.

---

### Post by Ostien on 2008-04-04
an opinion question to people more knowledgeable then I:  What is "better" in your opinion, shred, or the tools in the "secure delete" package i.e. srm, sfill etc. ?

---

### Post by niteshifter on 2008-04-05
Hi,

@Ostein:
I have only occasional use for shred - but I do trust it. That's the nice thing about open source software - one can look at the source(s), build the program, test it and have trust in it.

Mostly I keep sensitive material in truecrypt volumes, passworded and keyfiled (keyfiles on SD card). Using truecrypt volumes solves two problems: deletion remnants and no worries if laptop gets stolen.

@netlogic:
Burning does work. An oxy-acetylene torch with a cutting tip reduces platters to ash (powder). It's overkill and time-consuming - but fun. Lots of pretty colors in the flame ;) Just stay upwind of the fumes.

---

### Post by netlogic on 2008-04-05
Unless you take the platters outside the drive, burning and acid will not work according to few disaster recovery firms I emailed few years ago. Acid probably will only reach first outer platters. Still there is a chance, it can be cleaned and rebuild into similar spec drives. One disaster recovery firm claimed they got out 95% of data from a huge fire incidents. One disaster recovery firm I chated had a huge success for few real estate firms during Katrina disaster. If I think about how drives are made, it doesn't sound far fetch at all. Only way truly kill the drive is totally crack the platters on the drive. You can't re-glue the platters once they are cracked, but they can get cleaned. However, these days, overwriting the drive three times should be sufficient. 

Dead controllers can be easily replaced.

---

### Post by netlogic on 2008-04-05
> **Ostien said:**
> an opinion question to people more knowledgeable then I:  What is "better" in your opinion, shred, or the tools in the "secure delete" package i.e. srm, sfill etc. ?

Shred should be fine. Shred is very simple to use.

---

