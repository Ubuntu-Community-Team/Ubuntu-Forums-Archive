---
title: "overwrite unused disk space with zeros"
date: 2009-08-01
forum: Security
---

### Post by Lahntaler on 2009-08-01
sfill seems to get close to my requirement to overwrite all the **unused** disk space with zeros. The FAT formatted 120 GB harddisk of my camcorder (Sony SR12) is the target. I am only mildly worried about someone trying successfully to restore the movies. Mostly I want to prevent to have the deleted files in the disk backup images which I create using dd. Zeroing the unused space from deleted files would allow much better compression, and the deleted stuff does not spread around in my backup disk images.

My concern is the time it takes for sfill to do its job on a now almost empty 120 GB harddisk. See thread 
[http://ubuntuforums.org/showthread.php?t=873332]("http://ubuntuforums.org/showthread.php?t=873332")

I haven't tried it yet because I learnt better not to interrupt sfill once it is started.

By default sfill runs 38 passes, which may take weeks on an almost empty 120 GB FAT harddisk.
The option -l makes sfill to write only one pass with random values.
The option -z makes sfill to write the last pass with zeros.

Zeroing is exactly what I want. But as far as I understand, the option -z alone would still make sfill run 38 passes. Only if I use -l together with -z, sfill would run 2 passes: one random value pass and one zeroing pass.

The -l random value pass is still useless for me. Therefore my question:
Is there an alternative for zeroing **unused** disk space, or can sfill be switched to run just one zeroing pass?

---

### Post by insane_alien on 2009-08-01
whats wrong with the random fill? it'll do the same job.

you could try using the -z option with only 1 pass. that may do it. if not try 2 passes with the -z option.

either way you're writing a LOT of data and its goign to take a few hours at least.

---

### Post by goatmonkey on 2009-08-01
If i'm not mistaken, all sfill does is create a file that fills all the available disk space and fill it with the random numbers however many times you tell it to.  What you want is to make the same file full of zeros without all the random numbers.  You could do that without sfill.  Run dd on /dev/zero maybe?  Don't know off the top of my head.

---

### Post by yabbadabbadont on 2009-08-01
```
sudo -i

dd if=/dev/zero of=/filesystem_to_be_filled/filefullofzeroes
```
**DON'T** do that on your root filesystem!

You should be ok with using it on any non-root filesystem though.  Say, for example, you wanted to fill up all the unused space on "/MySpareFilesystem".

Then you would do ```
sudo -i

dd if=/dev/zero of=/MySpareFilesystem/filefullofzeroes
```
(you can use any filename you like instead of filefullofzeroes)

When you start getting out of space errors, hit Control-C repeatedly to kill the dd process.  Then remove the file that you filled with zeros (whatever you called it).

Note: sudo -i just drops you into a root shell.

---

### Post by The Cog on 2009-08-02
Edit - Post full of rubbish deleted.

---

### Post by kg84 on 2009-08-02
What exactly does the verbose mode do with sfill?

Also, if one wants two passes using the -l swtich does one have to run sfill twice, or can it be told to utilise the -l wipe twice in one sitting (ie sfill -l -2 or whatever??)

Cheers

---

### Post by Lahntaler on 2009-08-02
> **yabbadabbadont said:**
> ```
sudo -i
dd if=/dev/zero of=/filesystem_to_be_filled/filefullofzeroes
```
**DON'T** do that on your root filesystem!


Thanks a bunch. That's exactly what I had in mind.
I will try as soon as I have a few hours.

---

### Post by Lahntaler on 2009-08-02
> **The Cog said:**
> The suggestion by yabbadabbadont will erase the entire partition or disk that you specify as the target ...

No, only the unused space will be filled because the target is not the device. The target is a file in the filesystem of the device. Therefore existing files will be preserved.

---

### Post by The Cog on 2009-08-02
> **Lahntaler said:**
> No, only the unused space will be filled because the target is not the device. The target is a file in the filesystem of the device. Therefore existing files will be preserved.

I didn't look properly, did I. I'll edit that post. Sorry.

---

### Post by MaindotC on 2009-08-03
When you say "a file full of zeroes" do you mean like a text file with "00000000000000000" in it?

---

### Post by lswb on 2009-08-03
Why not just turn the camera on to "record" and let it fill the drive up with an innocuous scene? Maybe point it at a sign that says "Nothing to see here"

---

### Post by Lahntaler on 2009-08-03
> **strAlan said:**
> When you say "a file full of zeroes" do you mean like a text file with "00000000000000000" in it?

Unfortunately, my wording "a file full of zeroes" is not correct. Correct is that the file is full of 0-bits.

---

### Post by Lahntaler on 2009-08-03
> **lswb said:**
> Why not just turn the camera on to "record" and let it fill the drive up with an innocuous scene? Maybe point it at a sign that says "Nothing to see here"

Writing 0-bits into unused sectors has the big advantage of a very high compression rate when the disk image gets gzipped.

---

### Post by lswb on 2009-08-03
> **Lahntaler said:**
> Writing 0-bits into unused sectors has the big advantage of a very high compression rate when the disk image gets gzipped.
You're right, I read your OP a little too quickly & misunderstood your reason for doing this.

---

### Post by MaindotC on 2009-08-03
> **Lahntaler said:**
> Unfortunately, my wording "a file full of zeroes" is not correct. Correct is that the file is full of 0-bits.

How do you fill a file full of 0-bits?  How many do you need?

---

### Post by yabbadabbadont on 2009-08-03
> **strAlan said:**
> How do you fill a file full of 0-bits?  How many do you need?

Re-read (or read for the first time) the entire thread from the beginning.  :D

I posted the commands to do this using the 'dd' utility.

---

### Post by MaindotC on 2009-08-04
Well, I did read your post and you mention "filefullofzeroes" but you don't specify how you create a file full of zeroes.:

> **yabbadabbadont said:**
> ```
sudo -i

dd if=/dev/zero of=/filesystem_to_be_filled/filefullofzeroes
```

How do you create that file full of zeroes?

---

### Post by shaggy999 on 2009-08-04
> **strAlan said:**
> Well, I did read your post and you mention "filefullofzeroes" but you don't specify how you create a file full of zeroes.:



How do you create that file full of zeroes?

The command he gave is the command that creates the file full of zeros. Reading from /dev/null just spits out an infinite number of zeros. Using the dd command you tell it to read from /dev/null and put the output into a file you specify:

dd if=/dev/null of=/directory/filename

---

### Post by yabbadabbadont on 2009-08-04
> **shaggy999 said:**
> The command he gave is the command that creates the file full of zeros. Reading from /dev/null just spits out an infinite number of zeros. Using the dd command you tell it to read from /dev/null and put the output into a file you specify:

dd if=/dev/null of=/directory/filename

Thanks.  I was just going to reply, "man dd", but that probably would have gotten me an infraction...  :D

---

### Post by Lahntaler on 2009-08-09
The FAT-filesystem on the 120 GB harddisk on my Sony SR12 camcorder has a file size limit of 4294967295 bytes. Therefore I wrote a small script that keeps writing zero-bit files until the harddisk is full. To whom it may concern:

```

#!/bin/bash
# Write files filled with zero-bits to the directory passed as argument.
# The script stops, when the filesystem is full.
# Don't use on your root-filesystem.

if [ $# -ne 1 ]; then
  echo "Usage: $(basename $0) directory-for-zerobit-files" 1>&2
  exit 234
fi

declare -r zeroFilename='deleteme'
declare    targetDirectory="$1"

# Remove all trailing slashes, if any.
targetDirectory=$(echo $targetDirectory | sed "s/\/*$//")

counter=0
writeResult='File size limit exceeded'

while [ -n "$(echo "$writeResult" | fgrep 'File size limit exceeded')" -o -n "$(echo "$writeResult" | fgrep 'File too large')" ]; do
  writeResult=$(dd if=/dev/zero of="${targetDirectory}/${zeroFilename}.${counter}" 2>&1)
#  echo $writeResult
  let counter=counter+1
done

echo $writeResult

exit

```

---

### Post by HermanAB on 2009-08-10
> I was just going to reply, "man dd"


The sad truth is that new users don't know about the 'man' command and really should be referred to the man pages more often.  Some man pages are totally useless, but others are very good and should be read.

---

### Post by MaindotC on 2009-08-10
If it was that simple then we wouldn't need the forums.

---

### Post by Lahntaler on 2009-08-13
The script which I posted earlier does not work if the pathname contains spaces. Two double-quotes in this line fix the problem:

```

  writeResult=$(dd if=/dev/zero of="${targetDirectory}/${zeroFilename}.${counter}" 2>&1)

```

---

### Post by Andrew.Z on 2009-08-17
> **strAlan said:**
> How do you create that file full of zeroes?

If you are not comfortable with the command line, [BleachBit 0.6.1 overwrites free disk space](http://bleachbit.blogspot.com/2009/08/bleachbit-061-released.html) with zeros (the bit 0) easily from a graphical interface (just click).  There are installation packages for Ubuntu 9.04, 8.10, and 8.04, and it should be in the Ubuntu 9.10 repo soon.


> Zeroing is exactly what I want. But as far as I understand, the option -z alone would still make sfill run 38 passes. Only if I use -l together with -z, sfill would run 2 passes: one random value pass and one zeroing pass.

BleachBit only supports a single pass: the [Gutmann 35 pass misleads people and wastes time](http://bleachbit.blogspot.com/2009/06/validating-secure-erase.html).

---

### Post by oygle on 2010-11-30
I assume I could use this **dd** command to wipe the _entire contents_ of a USB stick ?

After testing photorec on a USB stick, I'm concerned about using it to get digital photos printed, as photorec recovered heaps of confidential files.  :oops:

For the time being, I have copied heaps of audio files to the USB stick, until it was full, then deleted and reformatted with GParted. The subsequent files recovered now are at least only audio files.

But the **dd** command sounds good, using the script shown here, the USB stick is only 4Gb, so it shouldn't take long to fill the entire stick.

Oygle

---

### Post by Andrew.Z on 2010-11-30
> **oygle said:**
> I assume I could use this **dd** command to wipe the _entire contents_ of a USB stick ?

Yes, unmount the disk, run dd (not against /dev/sda!), and then re-mount it.

> For the time being, I have copied heaps of audio files to the USB stick, until it was full, then deleted and reformatted with GParted. The subsequent files recovered now are at least only audio files.

This is similar to the (overwrite) 'free disk space' feature in BleachBit, but BleachBit fills the last byte and then overwrites the inodes table where metadata (like filenames) are stored.

> But the **dd** command sounds good, using the script shown here, the USB stick is only 4Gb, so it shouldn't take long to fill the entire stick.

On my internal SATA I wipe at 25MB/s with dd or BleachBit 0.8.3 (much faster than previous versions).  I haven't benchmarked a USB disk.

---

### Post by bodhi.zazen on 2010-11-30
> **oygle said:**
> I assume I could use this **dd** command to wipe the _entire contents_ of a USB stick ?

After testing photorec on a USB stick, I'm concerned about using it to get digital photos printed, as photorec recovered heaps of confidential files.  :oops:

For the time being, I have copied heaps of audio files to the USB stick, until it was full, then deleted and reformatted with GParted. The subsequent files recovered now are at least only audio files.

But the **dd** command sounds good, using the script shown here, the USB stick is only 4Gb, so it shouldn't take long to fill the entire stick.

Oygle

You really should start a new thread rather then opening an old thread with an off topic question.

The gutmann theory has been debunked, one pass with dd is sufficient.

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

---

### Post by oygle on 2010-12-06
> **Andrew.Z said:**
> Yes, unmount the disk, run dd (not against /dev/sda!), and then re-mount it.

Thanks Andrew, for your help.  :)

Oygle

---

