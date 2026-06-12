---
title: "amd microcode?"
date: 2012-06-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Gregory Lee on 2012-06-28
Should I have some AMD microcode from somewhere?  I'm getting complaints during boot:
```
boot-errors:Jun 25 06:14:41 greg-p7-1220 kernel: [   10.943864] microcode: CPU3: patch_level=0x03000014
boot-errors:Jun 25 06:14:41 greg-p7-1220 kernel: [   10.945191] microcode: failed to load file amd-ucode/microcode_amd.bin

```
Also, I've had to revert to kernel version 3.4, because 3.5 just won't boot up, though I don't know whether there is any connection to the error messages about missing microcode.

---

### Post by dino99 on 2012-06-28
do you get it with both 3.5.0-1 & 2 ? Maybe simply purge the kernels headers & images then reinstall them.

---

### Post by Gregory Lee on 2012-06-28
> **dino99 said:**
> do you get it with both 3.5.0-1 & 2 ? Maybe simply purge the kernels headers & images then reinstall them.
I don't know, because 3.5 doesn't get far enough in booting to leave behind any messages.  I'm using 3.4 now, and I do get the error message as it boots up.  3.4 seems to be working okay still.

All the kernels I have now on my disk, starting with 3.2, have some header files mentioning microcode in their names or subdirectories, and all those files are empty.

I don't mind the error messages -- I don't think of them as being a problem.  I'd like to know whether there is some AMD microcode that I should have.  Sometimes there are good reasons for error messages.

---

### Post by dino99 on 2012-06-28
you might have seen recent kernel images change: now it have been splitted into "image" AND "image-extra", so both are needed as "extra" has most of the modules.

---

### Post by zika on 2012-06-28
[http://ubuntuforums.org/archive/index.php/t-1945481.html](http://ubuntuforums.org/archive/index.php/t-1945481.html)

---

### Post by Gregory Lee on 2012-06-28
So there is.  Thanks, zika.

---

### Post by Gregory Lee on 2012-06-28
> **dino99 said:**
> you might have seen recent kernel images change: now it have been splitted into "image" AND "image-extra", so both are needed as "extra" has most of the modules.
I found a list of modules in the image-extra parts, and I do have those in my system.  I don't see anything there about amd microcode.

I downloaded the amd firmware that zika pointed out and installed it.  I got these kernel messages:
```
Jun 28 05:49:51 greg-p7-1220 kernel: [82197.326248] microcode: Microcode Update Driver: v2.00 removed.
Jun 28 05:49:57 greg-p7-1220 kernel: [82203.821692] microcode: CPU0: patch_level=0x03000014
Jun 28 05:49:57 greg-p7-1220 kernel: [82203.825815] microcode: CPU0: new patch_level=0x03000027
Jun 28 05:49:57 greg-p7-1220 kernel: [82203.825835] microcode: CPU1: patch_level=0x03000014
Jun 28 05:49:57 greg-p7-1220 kernel: [82203.828926] microcode: CPU1: new patch_level=0x03000027
Jun 28 05:49:57 greg-p7-1220 kernel: [82203.828953] microcode: CPU2: patch_level=0x03000014
Jun 28 05:49:57 greg-p7-1220 kernel: [82203.830992] microcode: CPU2: new patch_level=0x03000027
Jun 28 05:49:57 greg-p7-1220 kernel: [82203.831016] microcode: CPU3: patch_level=0x03000014
Jun 28 05:49:57 greg-p7-1220 kernel: [82203.834500] microcode: CPU3: new patch_level=0x03000027
Jun 28 05:49:57 greg-p7-1220 kernel: [82203.834600] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet
.co.uk>, Peter Oruba
```

No noticeable effect, so far.

---

### Post by zika on 2012-06-28
> **Gregory Lee said:**
> I found a list of modules in the image-extra parts, and I do have those in my system.  I don't see anything there about amd microcode.

I downloaded the amd firmware that zika pointed out and installed it.  I got these kernel messages:
```
Jun 28 05:49:51 greg-p7-1220 kernel: [82197.326248] microcode: Microcode Update Driver: v2.00 removed.
Jun 28 05:49:57 greg-p7-1220 kernel: [82203.821692] microcode: CPU0: patch_level=0x03000014
Jun 28 05:49:57 greg-p7-1220 kernel: [82203.825815] microcode: CPU0: new patch_level=0x03000027
Jun 28 05:49:57 greg-p7-1220 kernel: [82203.825835] microcode: CPU1: patch_level=0x03000014
Jun 28 05:49:57 greg-p7-1220 kernel: [82203.828926] microcode: CPU1: new patch_level=0x03000027
Jun 28 05:49:57 greg-p7-1220 kernel: [82203.828953] microcode: CPU2: patch_level=0x03000014
Jun 28 05:49:57 greg-p7-1220 kernel: [82203.830992] microcode: CPU2: new patch_level=0x03000027
Jun 28 05:49:57 greg-p7-1220 kernel: [82203.831016] microcode: CPU3: patch_level=0x03000014
Jun 28 05:49:57 greg-p7-1220 kernel: [82203.834500] microcode: CPU3: new patch_level=0x03000027
Jun 28 05:49:57 greg-p7-1220 kernel: [82203.834600] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet
.co.uk>, Peter Oruba
```No noticeable effect, so far.What effect did You expect? It looks OK...

---

### Post by Gregory Lee on 2012-06-28
> **zika said:**
> What effect did You expect? It looks OK...
I expected my life to become better.

---

### Post by zika on 2012-06-29
> **Gregory Lee said:**
> I expected my life to become better.It might get only micro-better, this is microcode... ;)

---

### Post by cariboo on 2012-06-29
Shouldn't there at least be puppies? I don't have any problems, but I loaded the microcode as per zika, and all I got was the same output as Gregory Lee. :) :) :)

---

### Post by zika on 2012-06-29
> **cariboo907 said:**
> Shouldn't there at least be puppies? Here You are:
[img]http://cdn-www.dailypuppy.com/dog-images/rhea-the-poodle-mix_65827_2012-06-28_w450.jpg[/img]
[IMG]http://www.dailypuppy.com/puppies/rhea-the-poodle-mix_2012-06-28[/IMG]

---

