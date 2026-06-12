---
title: "Securely erase HDD"
date: 2011-09-06
forum: Security
---

### Post by Jonker on 2011-09-06
Hi all,

I have an old computer with a 80 GB HDD. Now there is a new computer und I would like to throw the old one out. Do you have any recommendations how to securely erase the HDD?

Thanks in advance!

Jonker

---

### Post by 2F4U on 2011-09-06
You could use the shred utility from, for example, the Knoppix liveCD.

[http://www.ehow.com/how_6246449_use-knoppix-wipe-hard-drive.html](http://www.ehow.com/how_6246449_use-knoppix-wipe-hard-drive.html)

---

### Post by Jonker on 2011-09-06
Thanks, I have Ubuntu installed on a USB-Drive. Is it also possible from Ubuntu? Will the command "Shred" also write "00000" to the HDD?

---

### Post by CharlesA on 2011-09-06
Degauss the drive. If that's not possible run dban (or dd) on it a few times, or physically smash the platters.

---

### Post by Lars Noodén on 2011-09-06
> **CharlesA said:**
> Degauss the drive. If that's not possible run dban (or dd) on it a few times, or physically smash the platters.

It's been many, many years since I've seen a degausser.  A quick search shows that they are still available for sale, sometimes called bulk erasers, but the question is where to borrow or rent one for a one-off activity like clearing a hard drive.

---

### Post by tubbygweilo on 2011-09-06
Jonker, Post [#41]("http://ubuntuforums.org/showpost.php?p=11216503&postcount=41") of thread [Securely Wipes Hard Drive]("http://ubuntuforums.org/showthread.php?t=1834924") may well answer your question.

---

### Post by Lars Noodén on 2011-09-06
> **tubbygweilo said:**
> Jonker, Post [#41]("http://ubuntuforums.org/showpost.php?p=11216503&postcount=41") of thread [Securely Wipes Hard Drive]("http://ubuntuforums.org/showthread.php?t=1834924") may well answer your question.

The program is misspelled as **d** in comment #41.  The correct spelling is **[dd](http://manpages.ubuntu.com/manpages/natty/en/man1/dd.1.html)**

---

### Post by CharlesA on 2011-09-06
> **Lars Noodén said:**
> It's been many, many years since I've seen a degausser.  A quick search shows that they are still available for sale, sometimes called bulk erasers, but the question is where to borrow or rent one for a one-off activity like clearing a hard drive.

They are really too expensive/hard to get for a home user, which is why I suggested dban or dd. ;)

---

### Post by Jonker on 2011-09-06
So, the computer has 2 internal HDDs. But I am booting from an external HDD. So lets say  the first one is /dev/sda, the second /dev/sdb and the boot one /dev/sdc. So the command should be:```
dd if=/dev/zero of=/dev/sda bs=1M
``` To wipe my first hdd. The second would be /dev/sdb. 
Can I have a screen output, to show the progress?
Is the command correct, sudo rights required?
thx
Jonker

---

### Post by sakthidaran on 2011-09-07
I have Ubuntu 10.04 LTS in a lab. Many students (in 100's) use these computers. Occasionally,  some students while learning or trying commands damage the HDD. Recently, a few SATA HDDs have been thoroughly cleaned/erased by some one. I suspect that some one has used "shred" command.

Is there a way to protect the HDD against such activities. I mean, is it possible to disable the command? Or is there any other way to protect against such operation.

---

### Post by CharlesA on 2011-09-07
> **sakthidaran said:**
> I have Ubuntu 10.04 LTS in a lab. Many students (in 100's) use these computers. Occasionally,  some students while learning or trying commands damage the HDD. Recently, a few SATA HDDs have been thoroughly cleaned/erased by some one. I suspect that some one has used "shred" command.

Is there a way to protect the HDD against such activities. I mean, is it possible to disable the command? Or is there any other way to protect against such operation.
Don't give them root access and/or image the drives before they use them.

---

### Post by Lars Noodén on 2011-09-07
One way of imaging the drives is to use [radmind](http://rsug.itd.umich.edu/software/radmind/) to remove extra stuff and restore the settings.

---

### Post by Jonker on 2011-09-07
So could one also use the shred command to erase a hdd?

---

### Post by CharlesA on 2011-09-07
> **Jonker said:**
> So could one also use the shred command to erase a hdd?
As far as I know, you just use shred to overwrite a file. If you wanted to do that to the whole drive, you'd need root permission to do so.

dd would probably be the easier/simpler way to do it.

---

### Post by Jonker on 2011-09-07
Well,I'm the admin from that OS and PC. 
dd just copies the content from /dev/zero (which is what ever) to /dev/sda, right?

---

### Post by CharlesA on 2011-09-07
> **Jonker said:**
> Well,I'm the admin from that OS and PC. 
dd just copies the content from /dev/zero (which is what ever) to /dev/sda, right?
Pretty much. You can tell it what to use - /dev/urandom, /dev/zero, etc.

---

### Post by The Cog on 2011-09-07
> **Jonker said:**
> Well,I'm the admin from that OS and PC. 
dd just copies the content from /dev/zero (which is what ever) to /dev/sda, right?

Yes. /dev/zero is a device that provides an infinite number of zero bytes for as long as you keep reading from it. /dev/random is a source of random byte values. /dev/urandom is a source of random bytes that (I gather) is statistically more random than /dev/random, but uses a more CPU intensive algorithm for calculating the next value.

---

### Post by Jonker on 2011-09-07
Thanks u guys a lot. How long would it take to fill a 80GB drive with zeros? Intel Pentium 4; 2GHerz is my prozessor. Do I need to format the drive first?

Jonker

---

### Post by CharlesA on 2011-09-07
> **Jonker said:**
> Thanks u guys a lot. How long would it take to fill a 80GB drive with zeros? Intel Pentium 4; 2GHerz is my prozessor. Do I need to format the drive first?

Jonker
It shouldn't matter if you format or not. It will probably take a few hours to finish.

---

### Post by Jonker on 2011-09-07
Ok. Thanks very much. Ill mark this Thread as solved.

Thx and Bye

Jonker

---

