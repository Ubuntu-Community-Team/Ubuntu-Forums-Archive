---
title: "Darktable unable to import pictures"
date: 2012-07-09
forum: Ubuntu Studio
---

### Post by arunssha on 2012-07-09
I have installed darkroom 1.0.4-0pmjdebruijn1~natty on my ubuntu natty 11.04.
it  was working fine but suddenly one day i saw it's unable to import  pictures. Whenever I browse to an image in import window and click on  open or double click on picture, the darktable freezes. After clicking  the close button multiple times i get this prompt "The window darktable  is not responding" with 'cancel' and 'Force quit' options.

Even  for already imported pictures in lighttable, it says 'working..' when I  try to open it but the picture never opens in darkroom.


when i  run with cache i get following:

[FONT=Courier New]$ darktable -d cache
[image_cache] has 262144 entries
[mipmap_cache_init] cache has  2048 entries for mip 0 ( 156.97 MB).
[mipmap_cache_init] cache has   512 entries for mip 1 ( 156.95 MB).
[mipmap_cache_init] cache has   128 entries for mip 2 ( 156.94 MB).
[mipmap_cache_init] cache has    32 entries for mip 3 ( 156.94 MB).
[mipmap_cache_init] cache has     8 entries for mip 4 ( 156.94 MB).
[mipmap_cache] level 0 fill 97.11/141.27 MB (68.74% in 1267/2048 buffers)
[mipmap_cache] level 1 fill 0.00/141.25 MB (0.00% in 0/512 buffers)
[mipmap_cache] level 2 fill 0.00/141.25 MB (0.00% in 0/128 buffers)
[mipmap_cache] level 3 fill 0.00/141.24 MB (0.00% in 0/32 buffers)
[mipmap_cache] level 4 fill 0.00/141.24 MB (0.00% in 0/8 buffers)
[mipmap_cache] level [full] fill 1/1 slots (100.00% in 1/16 buffers)


[mipmap_cache] level 0 fill 97.11/141.27 MB (68.74% in 1267/2048 buffers)
[mipmap_cache] level 1 fill 0.00/141.25 MB (0.00% in 0/512 buffers)
[mipmap_cache] level 2 fill 0.00/141.25 MB (0.00% in 0/128 buffers)
[mipmap_cache] level 3 fill 0.00/141.24 MB (0.00% in 0/32 buffers)
[mipmap_cache] level 4 fill 0.00/141.24 MB (0.00% in 0/8 buffers)
[mipmap_cache] level [full] fill 1/1 slots (100.00% in 1/16 buffers)


[mipmap_cache] level 0 fill 97.11/141.27 MB (68.74% in 1267/2048 buffers)
[mipmap_cache] level 1 fill 0.00/141.25 MB (0.00% in 0/512 buffers)
[mipmap_cache] level 2 fill 0.00/141.25 MB (0.00% in 0/128 buffers)
[mipmap_cache] level 3 fill 0.00/141.24 MB (0.00% in 0/32 buffers)
[mipmap_cache] level 4 fill 0.00/141.24 MB (0.00% in 0/8 buffers)
[mipmap_cache] level [full] fill 1/1 slots (100.00% in 1/16 buffers)

[mipmap_cache] level 0 fill 97.11/141.27 MB (68.74% in 1267/2048 buffers)
[mipmap_cache] level 1 fill 0.00/141.25 MB (0.00% in 0/512 buffers)
[mipmap_cache] level 2 fill 0.00/141.25 MB (0.00% in 0/128 buffers)
[mipmap_cache] level 3 fill 0.00/141.24 MB (0.00% in 0/32 buffers)
[mipmap_cache] level 4 fill 0.00/141.24 MB (0.00% in 0/8 buffers)
[mipmap_cache] level [full] fill 1/1 slots (100.00% in 1/16 buffers)


[mipmap_cache] level 0 fill 97.11/141.27 MB (68.74% in 1267/2048 buffers)
[mipmap_cache] level 1 fill 0.00/141.25 MB (0.00% in 0/512 buffers)
[mipmap_cache] level 2 fill 0.00/141.25 MB (0.00% in 0/128 buffers)
[mipmap_cache] level 3 fill 0.00/141.24 MB (0.00% in 0/32 buffers)
[mipmap_cache] level 4 fill 0.00/141.24 MB (0.00% in 0/8 buffers)
[mipmap_cache] level [full] fill 1/1 slots (100.00% in 1/16 buffers)


[mipmap_cache] level 0 fill 97.11/141.27 MB (68.74% in 1267/2048 buffers)
[mipmap_cache] level 1 fill 0.00/141.25 MB (0.00% in 0/512 buffers)
[mipmap_cache] level 2 fill 0.00/141.25 MB (0.00% in 0/128 buffers)
[mipmap_cache] level 3 fill 0.00/141.24 MB (0.00% in 0/32 buffers)
[mipmap_cache] level 4 fill 0.00/141.24 MB (0.00% in 0/8 buffers)
[mipmap_cache] level [full] fill 1/1 slots (100.00% in 1/16 buffers)


Killed
[/FONT]

I do not understand these cache levels. Do i need to do something with memory settings?

Current settings:
mipmap cache : 1000000000
background threads: 1
export multiple images: 1

I  have already done complete removal and reinstallation.  It seems to me  that i was running on older version earlier may be 1.0.3 and started  facing problem once 1.0.4 got into distribution. I thought upgrading to  1.0.4 will solve the problem but it didn't.
Now there is no option to go back to 1.0.3.

Thanks.

---

### Post by arunssha on 2012-07-17
Is this really a tough question? or did I use really bad english?
i've got more than 100 views on this but no answer. :(

---

### Post by goldshirt9 on 2012-07-17
well i have always found Darktable a little glitchy 
have you posted this request on their site ?

could you not uninstall and reinstall.
wish i could be of more help.:(

---

### Post by arunssha on 2012-07-17
> **goldshirt9 said:**
> well i have always found Darktable a little glitchy 
have you posted this request on their site ?

could you not uninstall and reinstall.
wish i could be of more help.:(


thanks :)
No i didn't post there, i will do right away.
You are true, darktable is indeed glitchy but that was the only option i found to substitute my lightroom.

I have tried complete removal and installation already. :(

Do you know about any other program similar to darktable that can be used to enhance photographs? (i mean not like gimp)

---

### Post by arunssha on 2012-07-17
Ah it works now :)
My memory settings were incorrect.

old settings:
mipmap cache : 1000000000
background threads: 1
export multiple images: 1
Momory limit for tilting:1500

Current settings:
mipmap cache : 268435456
background threads: 1
export multiple images: 1
Momory limit for tilting:500

:guitar:

---

### Post by goldshirt9 on 2012-07-17
unfortunately windows is the best options for various  photo software programs.:(

at the moment i'm rebuilding my laptop and have no software at the moment on it.

Am about to play around and install  a few to see what their like.
As i have a Sony camera and the raw format can be a pain, this is the best option I find.
install and remove at a will.:D

you could try to purge darktable files to see if its possible to do a complete fresh install re-install .



sudo apt-get remove <program>

---

### Post by Jenske on 2012-09-25
I have since about 3 years been using Digikam. It is able to open RAW-camera images.

---

