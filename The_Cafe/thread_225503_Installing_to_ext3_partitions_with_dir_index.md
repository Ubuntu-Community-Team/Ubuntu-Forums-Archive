---
title: "Installing to ext3 partitions with dir_index"
date: 2006-07-29
forum: The Cafe
---

### Post by K.Mandla on 2006-07-29
While cruising the Arch linux forums, I found [a thread]("http://bbs.archlinux.org/viewtopic.php?t=16501") that described a striking speed difference when using ext3 partitions with dir_index enabled. 

This looked like something that I could use -- I work with 1Ghz and lower machines a lot, and as I understand it, the speed of some file systems is influenced by your [processor speed]("http://fsbench.netnation.com/"). 

At present I'm more inclined to work with Ubuntu than Arch, but the actual grunt work of using dir_index proved a bit tricky. I could see that my drives weren't using the dir_index option, which I take to mean that it isn't installed by default.

Furthermore, using the commands in the [dir_index howto]("http://www.ubuntuforums.org/showthread.php?t=37806") didn't work in my case. This one 

```
sudo tune2fs -O dir_index /dev/hda1
``` 
yielded error messages, and this one 

```
sudo e2fsck -D /dev/hda1
``` 
did not seem to have an effect. (I was checking with *sudo tune2fs -l | grep dir_index*, and got no results. ;) )

Far as I know, you can't (or perhaps just *shouldn't*) directly convert file systems without removing the information that's there already. That wouldn't be so much of a problem for a home directory, but what about the root? I suppose you could *chroot* somehow, but I'm not real good with that.

Since I was hankering to reinstall anyway (I get that way sometimes), I thought I might start from scratch and repartition like this.

```
/dev/hda1 100Mb boot
/dev/hda2 2Gb root
/dev/hda3 512Mb swap
/dev/hda4 (remainder) home
```
I wanted ext2 for the boot and, of course, swap for the swap, but root and home would both be ext3 with dir_index.

The only flaw in my plan at this point was getting that file system in place before the installer took over. 

I tried expert installations as well as normal installations off the Xubuntu alternate (install) CD, but you're not given the opportunity to work with the filesystems in the partitioner, and even if you were, it seems the alternate CD installer automagically formats those partitions with or without your consent.

So my solution was to boot to the Xubuntu desktop (live) CD, set my partitions with cfdisk, make the file systems with *sudo mke2fs -j -O dir_index /dev/hda2* and *sudo mke2fs -j -O dir_index /dev/hda4*, then start the integrated installer.

The live CD installer lets you mount partition by partition, and has the option of reformatting or not. Which means I could quickly set up my partitions as I wanted, then start installing without blanking the partitions and (I suspect) losing the dir_index option.

(One quirk I should mention at this point: cfdisk will ask for a partition size in Mb, but giving it 2048Mb for the root partition resulted in a partition that was actually slightly smaller -- 1910Mb or something like that. It's probably the whole multiply-by-1024 thing coming back to haunt us again. Either way,  the live CD installer balks at mounting the root partition to anything smaller than 2Gb. So ... if you try this at home, make sure you partition your root to be just slightly larger than 2048Mb, just to keep the installer happy.)

From there, everything went exactly as planned. I can check for the dir_index option on the root and home drives and it shows up exactly how I wanted it. Boot times are a little faster, and drive access seems ... perkier. :rolleyes: 

But of course, after it was all said and done, I wondered if anyone else might have an easier way to do it ... perhaps without needing to reinstall. Suggestions? 

P.S.: I considered posting this in the Installation section, but I wasn't sure it was really best there. If someone wants to move it, I won't be offended. ;-) 

And thanks for reading to the end. :)

NOTE: I might recast this as a how-to, even though the topic is a little obscure and the procedure will appeal to a slim audience. Still, if you're working with an older machine, it could be useful. If you have any suggestions, I'd be happy to hear them.:smile:

---

### Post by briancurtin on 2006-07-29
since i post on those forums, when i read your thread title i was going to link you to that thread...but you clearly found that on your own haha.

---

### Post by K.Mandla on 2006-07-30
Yeah, I learn a lot of neat stuff at the Arch forums. But I mostly lurk over there.

---

