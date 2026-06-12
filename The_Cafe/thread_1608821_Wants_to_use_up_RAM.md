---
title: "Wants to use up RAM"
date: 2010-10-29
forum: The Cafe
---

### Post by ubunterooster on 2010-10-29
I have 8GB of RAM and 33GB SWAP (on a really fast SSD) I want to fill up* 30GB* while inside Ubuntu to test SWAP. Any ideas?

---

### Post by phrostbyte on 2010-10-29
int main() {
  while (1) {
     malloc(10000000);
  }
}

---

### Post by markp1989 on 2010-10-29
from what i have herd, you shouldnt put a swap file/partition on a ssd

and with 8gb of ram, you probably dont need a swap file any way

you could use a loop to run like a million instances of a app,

> #!/bin/bash
while true; do
firefox & 
done 

---

### Post by whiskeylover on 2010-10-29
> **phrostbyte said:**
> int main() {
  while (1) {
     malloc(10000000);
  }
}

You forgot 
#include <stdlib.h>

---

### Post by lisati on 2010-10-29
> **whiskeylover said:**
> You forgot 
#include <stdlib.h>

And the [noparse]```
 and 
```[/noparse] tags.... :D

---

### Post by del_diablo on 2010-10-29
Play games, run in RAM.

---

### Post by ubunterooster on 2010-10-29
> **markp1989 said:**
> from what i have herd, you shouldnt put a swap file/partition on a ssd

and with 8gb of ram, you probably dont need a swap file any way

you could use a loop to run like a million instances of a app,
This SSD has it's own built-in OS that stops degradation that often occurs with frequent writes.

I very often use VMs and want to really stress test everything to make sure nothing is working wrong

---

### Post by ubunterooster on 2010-10-29
> **del_diablo said:**
> Play games, run in RAM.
Tried that; can't use more than 7.2 GB with games. Too many windows to keep running to do that

---

### Post by ubunterooster on 2010-10-29
> **whiskeylover said:**
> You forgot 
#include <stdlib.h>
How do I do that to use 30 GB?

---

### Post by ubunterooster on 2010-10-29
> **markp1989 said:**
> from what i have herd, you shouldnt put a swap file/partition on a ssd

and with 8gb of ram, you probably dont need a swap file any way

you could use a loop to run like a million instances of a app,
Okay, that worked to well, I think I should try only filling 30-35 GB. 

I want to stress test it not kill it ;)

---

### Post by NightwishFan on 2010-10-29
Nice! Take my joke seriously. :D Still I want that free -m. :)

---

### Post by ubunterooster on 2010-10-29
> **NightwishFan said:**
> Nice! Take my joke seriously. :D Still I want that free -m. :)
*[I]markp1989 had a good suggestion, only problem is it froze it to too much of a crawl to post free -m*
[/I]

---

### Post by markp1989 on 2010-10-29
> **ubunterooster said:**
> Okay, that worked to well, I think I should try only filling 30-35 GB. 

I want to stress test it not kill it ;)

lol, try this 

```
#!/bin/bash
for i in $(seq 100)
do
  firefox & 
done

```

this 1 should only run it 100 times :)

---

### Post by NightwishFan on 2010-10-29
Thank heavens for the OOM killer eh? :)

---

### Post by Paqman on 2010-10-29
> **ubunterooster said:**
> This SSD has it's own built-in OS that stops degradation that often occurs with frequent writes.


The IDE isn't really an OS. Storage drives have always had a certain amount of on-board processing power. That's how they do caching and handle things like bad sectors. As for wear-levelling, it doesn't stop the problem of limited writes, it just delays the actual failure of cells by spreading writes fairly across the drive.

---

### Post by ubunterooster on 2010-10-29
> **markp1989 said:**
> lol, try this 

```
#!/bin/bash
for i in $(seq 100)
do
  firefox & 
done

```

this 1 should only run it 100 times :)
Much better. However I think I should have replaced Firefox with another command, it took a good while to find this window ;)

---

### Post by user1397 on 2010-10-29
you could try to see how many times you can install an OS in another OS using a VM

---

### Post by ubunterooster on 2010-10-29
I thought that it would just take to long; Of course I also forgot to consider how long it takes to shut down 10,000 instances of firefox individually:mad: 

Yes, one at a time!

---

### Post by SeijiSensei on 2010-10-29
> **markp1989 said:**
> 
```
#!/bin/bash
for i in $(seq 100)
do
  firefox & 
done

```

Of course I also forgot to consider how long it takes to shut down 10,000 instances of firefox individually:mad:
How about 
```
#!/bin/bash
LOG=fill_memory.log

for i in $(seq 100)
do
  firefox & 
  echo "Iteration: $i" >> $LOG
  cat /proc/meminfo >> $LOG
  echo >> $LOG
  echo >> $LOG
done
killall -9 firefox


```

---

### Post by koleoptero on 2010-10-29
```
bash :(){ :|:& };:
```

Might take a while but it will use up anything you've got.

EDIT: [read this first.]("http://www.cyberciti.biz/faq/understanding-bash-fork-bomb/")

---

### Post by ubunterooster on 2010-10-29
> **SeijiSensei said:**
> How about 
```
#!/bin/bash
for i in $(seq 100)
do
  firefox & 
done
killall -9 firefox


```
Firefox considers that an unhealthy shutdown and when it is later started, it brings back all instances. I tried that

---

### Post by SeijiSensei on 2010-10-29
> **ubunterooster said:**
> Firefox considers that an unhealthy shutdown and when it is later started, it brings back all instances. I tried that

How about "killall -15 firefox"?

By the way, I noticed that starting multiple instances of firefox manually didn't lead to separate processes each time.  I ran "firefox &" from the prompt repeatedly, but ended up with only two instances of firefox-bin.  You might want to add a few seconds of "sleep" time in any loop you write.

I tried using the GIMP instead and had similar issues.  It's hard to fill up memory when programs are written to take as small a unique slice as possible!

Maybe OpenOffice is a better choice?

---

### Post by ubunterooster on 2010-10-29
I do not know the -15 variation

---

### Post by spupy on 2010-10-29
Using 'firefox' in this loop isn't of much use for the test. Firefox is not a stupid program and doesn't start more than one process of itself if it's already running and responding. It only opens a new window. While this does use up memory, it's not a very effective wait of eating RAM.

---

### Post by SeijiSensei on 2010-10-29
Agreed.  I think manipulating VMs to have large memory footprints then running them simultaneously as others have suggested is a better test.

---

### Post by ubunterooster on 2010-10-29
> **SeijiSensei said:**
> Agreed.  I think manipulating VMs to have large memory footprints then running them simultaneously as others have suggested is a better test.
Yes, I Have realized this by now in the hours it took to shut down 10,000 instances

---

### Post by spupy on 2010-10-29
Suggestion: open a blu-ray rip several times with a text editor. Not all editor would eat memory, though - e.g. *less*, I think, doesn't read the whole file.

---

### Post by NightwishFan on 2010-10-29
Open a SVG image in gimp, and tell it to render at like 20,000 x 20,000 (10-30x size etc)

---

### Post by cammin on 2010-10-29
```
sudo mount -t tmpfs -o size=30G tmpfs /mnt

dd if=/dev/zero of=/mnt/tmp bs=10240 count=30720MB
```

creates a 30gb ramdisk and fills it with file full of zeroes.


You can then delete /mnt/tmp to free up the memory quickly.

---

### Post by ubunterooster on 2010-10-29
> **spupy said:**
> Suggestion: open a blu-ray rip several times with a text editor. Not all editor would eat memory, though - e.g. *less*, I think, doesn't read the whole file.
I don't have Blurays or a bluray drive

---

### Post by SeijiSensei on 2010-10-31
> **cammin said:**
> ```
sudo mount -t tmpfs -o size=30G tmpfs /mnt

dd if=/dev/zero of=/mnt/tmp bs=10240 count=30720MB
```

creates a 30gb ramdisk and fills it with file full of zeroes.

^This.  I knew there had to be a method using dd, I just didn't bother to go find out the details.

Does anyone think there's a palpable difference between creating a ramdisk and executing multiple instances of a large program?  I could imagine the possibility that needing to swap VMs in and out might expose programming inefficiencies in the memory manager more than creating a ramdisk.  Someone with much better credentials in the guts of the hardware and OS than me would need to answer this.

---

### Post by ubunterooster on 2010-11-01
You are correct

---

