---
title: "encrypting the /tmp folder."
date: 2009-06-07
forum: Security
---

### Post by solitaire on 2009-06-07
Is their any problems with using a "random pass-phrase" encrypted /tmp partition?

An encrypted partition that is recreated at every boot (like the set up for the swapfile)?

Then i can point all the temp directories (and things like thumbnails etc...) in my /home folder to the /tmp partition so that every time the computer is rebooted all the temp files are wiped.

It's just in idea for now. I've got a spare machine that i cna do some testing on but wanted to find out if it's technicaly possible before i start.

---

### Post by Jekshadow on 2009-06-08
Just a question, but why do you need to encrypt the /tmp folder, wouldn't it be easier just to create a script that shreds your /tmp folder on shutdown?


shred_tmp.sh
```

shred -f -v -u -z /tmp

```

---

### Post by solitaire on 2009-06-08
It's just an experiment in security. 

Having all the temp files in a single location and having it encrypted (with a one time key) makes it a bit more secure.

Just want to see if it's possible...

---

### Post by cdenley on 2009-06-08
Assuming you don't write much to /tmp, and have a little RAM to spare, you could mount /tmp with tmpfs instead, which writes to memory instead of disk. This will result in an increase in performance instead of a decrease, and nothing will be stored on disk, if you're paranoid about recovery.

---

### Post by solitaire on 2009-06-08
I'm doing a test on an old laptop with 756Mb of ram I'll try the tmpfs but might be a bit tight for room.

---

### Post by Agent ME on 2009-06-08
> **Jekshadow said:**
> Just a question, but why do you need to encrypt the /tmp folder, wouldn't it be easier just to create a script that shreds your /tmp folder on shutdown?


shred_tmp.sh
```

shred -f -v -u -z /tmp

```
Many programs delete the files that they write to /tmp, so those would be missed by the shredder.

---

### Post by solitaire on 2009-06-08
> **Agent ME said:**
> Many programs delete the files that they write to /tmp, so those would be missed by the shredder.


That's what I thought!

That's the main reason i'm looking into the one time encryption key setup for /tmp

Also it has the benefit of you never knowing the key to decrypt it, so anything on it can't be recovered.

---

### Post by HermanAB on 2009-06-08
Uhmmm, if you did the default ubuntu install, then /tmp will be configured as tmpfs which is a RAM disk.  So the moment you turn the machine off, it should be gone.

---

### Post by Dr Small on 2009-06-08
> **HermanAB said:**
> Uhmmm, if you did the default ubuntu install, then /tmp will be configured as tmpfs which is a RAM disk.  So the moment you turn the machine off, it should be gone.
Yeah, I thought that's what /tmp was for anyhow. Nothing ever stays in it permanently. When I reboot, all of the data in /tmp is always gone.

---

### Post by lavinog on 2009-06-09
Technically it is possible to retrive data from ram from a shutdown machine. (although with little success I would imagine)

I actually saw something similar on my moms laptop. I booted into windows, shutdown and rebooted with a ubuntu live cd. For a brief second during a video mode change, I saw the windows shutdown screen.

---

### Post by Agent ME on 2009-06-10
> **HermanAB said:**
> Uhmmm, if you did the default ubuntu install, then /tmp will be configured as tmpfs which is a RAM disk.  So the moment you turn the machine off, it should be gone.
On my system, which is just a default 9.04 install, typing 'mount' shows that the only tempfs filesystem is /dev/shm. /tmp is on the main filesystem, for me at least.

---

### Post by lavinog on 2009-06-10
> **Agent ME said:**
> On my system, which is just a default 9.04 install, typing 'mount' shows that the only tempfs filesystem is /dev/shm. /tmp is on the main filesystem, for me at least.

Same here

---

### Post by solitaire on 2009-06-10
> **Dr Small said:**
> Yeah, I thought that's what /tmp was for anyhow. Nothing ever stays in it permanently. When I reboot, all of the data in /tmp is always gone.

The /tmp is cleared at every boot but it's still recoverable, also the data is only cleared on boot (I think) so if it was booted off of a USB drive or on another machine the /tmp data will still be there.

By encrypting the /tmp partition with a single use key, then once the power is turned off all the data is non-recoverable, unless they find a flaw in the encryption that let's people decrypt it!!

---

### Post by lavinog on 2009-06-10
Wait, what is the point of securing tmp anyway?
There should not be any sensitive data in /tmp for any reason since any logged in user would be able to access it.

---

### Post by lavinog on 2009-06-10
Also it looks like ubuntu will mount /tmp as a tmpfs if there is not enough space on the root partition.( see /etc/init.d/mountoverflowtmp )

---

### Post by solitaire on 2009-06-10
> **lavinog said:**
> Wait, what is the point of securing tmp anyway?
There should not be any sensitive data in /tmp for any reason since any logged in user would be able to access it.

It's not other users i'm worried about.... and their is temp data in the users /home directory which *does* hold sensitive information.

This is for a single user laptop.

Most programs put some info in /tmp and in temp folders within /home
By having *all* temp data pointing to a singe secured partition any old data can't be accessed when the laptop is rebooted.

As i've said before: It's an exorcise in security, any data which is temporary in nature must be secured.

---

### Post by benj1 on 2009-06-10
> **solitaire said:**
> It's not other users i'm worried about.... and their is temp data in the users /home directory which *does* hold sensitive information.

This is for a single user laptop.

Most programs put some info in /tmp and in temp folders within /home
By having *all* temp data pointing to a singe secured partition any old data can't be accessed when the laptop is rebooted.

As i've said before: It's an exorcise in security, any data which is temporary in nature must be secured.

why don't you encrypt your home partition?

if your home partition is encrypted and /tmp is in ram what are you worried about???
or am i missing some thing?

---

### Post by solitaire on 2009-06-10
> **benj1 said:**
> why don't you encrypt your home partition?

if your home partition is encrypted and /tmp is in ram what are you worried about???
or am i missing some thing?

OK i'll explain it in a bit more detail:

I'm doing an experiment to built a "Secure" laptop.

Part of the berief is to secure all temp files.

"The temp folders in the /tmp AND the users /Home folders are to be secured in a manor which after a reboot, login (or if the drive is accessed using a Live CD or placed in another system) the old contents may NOT be recoverable."

To do this I'm trying to set up the /tmp as a partition, with the temp files in the users /home folder to point to the /tmp partition as well (a temp file is things like but not limited to logfiles, histories or thumbnails).

The /tmp partition will be re-created every boot using a "random, single use encryption key" (the same as the swap file) so that even if a user hands over his password any temp data in the old encrypted partition would have been overwritten with a new encrypted partition that uses a different key.

Is the above possible?

---

### Post by logos34 on 2009-06-10
> **Jekshadow said:**
> Just a question, but why do you need to encrypt the /tmp folder...?


> **solitaire said:**
> It's just an experiment in security. 

Having all the temp files in a single location and having it encrypted (with a one time key) makes it a bit more secure.

Just want to see if it's possible...

Yeah, *sure*...(PORN!) :razz:

---

### Post by benj1 on 2009-06-10
> **solitaire said:**
> OK i'll explain it in a bit more detail:

I'm doing an experiment to built a "Secure" laptop.

Part of the berief is to secure all temp files.

"The temp folders in the /tmp AND the users /Home folders are to be secured in a manor which after a reboot, login (or if the drive is accessed using a Live CD or placed in another system) the old contents may NOT be recoverable."

To do this I'm trying to set up the /tmp as a partition, with the temp files in the users /home folder to point to the /tmp partition as well (a temp file is things like but not limited to logfiles, histories or thumbnails).

The /tmp partition will be re-created every boot using a "random, single use encryption key" (the same as the swap file) so that even if a user hands over his password any temp data in the old encrypted partition would have been overwritten with a new encrypted partition that uses a different key.

Is the above possible?

well my suggestion of encrypting the /home folder ensuring /tmp is kept in ram, would ensure that no one could access data, i think directing all temporary files to /tmp is more likely to break your system, although im not sure on that. if youre just doing it to see if its possible and because you can then fair enough, but there are easier methods of achieving what you want to achieve.

---

### Post by Agent ME on 2009-06-10
> **lavinog said:**
> Wait, what is the point of securing tmp anyway?
There should not be any sensitive data in /tmp for any reason since any logged in user would be able to access it.
Generally programs that make temporary files in /tmp set their permissions so that they are only accessible by the owner.

> **benj1 said:**
> well my suggestion of encrypting the /home folder ensuring /tmp is kept in ram, would ensure that no one could access data, i think directing all temporary files to /tmp is more likely to break your system, although im not sure on that. if youre just doing it to see if its possible and because you can then fair enough, but there are easier methods of achieving what you want to achieve.
Storing /tmp in ram isn't always an option, especially if you're working with large files there.
Temporary files already go into /tmp. There isn't any redirecting going on.

***edit; just read first post again:*** Redirecting thumbnails to /tmp shouldn't be too much of a hassle. I would write some code in the ~/.login script that would create a random folder in /tmp for storing user stuff, and create a folder in it named 'thumbnails'. At the same time, the script would create a symlink in my home directory linking ~/.thumbnails -> /tmp/random$$/thumbnails (forcibly overwriting any pre-existing symlink named .thumbnails in my home directory).


I've seen tutorials in the past for randomly encrypting the swap partition; maybe just following the same instructions can help for setting up a similar /tmp partition (just obviously with an ext3 or similar FS instead of the swap setting). Think I'm going to keep my eye on this thread in case you figure something out, and I'll probably try to take a stab at it eventually if you don't.

---

### Post by lordal on 2009-08-05
Just found this, maybe it will be of interest to you

[http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu&mode=print](http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu&mode=print)

part II Dealing with /temp

---

### Post by solitaire on 2009-08-05
> **Agent ME said:**
> 
***edit; just read first post again:*** Redirecting thumbnails to /tmp shouldn't be too much of a hassle. I would write some code in the ~/.login script that would create a random folder in /tmp for storing user stuff, and create a folder in it named 'thumbnails'. At the same time, the script would create a symlink in my home directory linking ~/.thumbnails -> /tmp/random$$/thumbnails (forcibly overwriting any pre-existing symlink named .thumbnails in my home directory).

I've seen tutorials in the past for randomly encrypting the swap partition; maybe just following the same instructions can help for setting up a similar /tmp partition (just obviously with an ext3 or similar FS instead of the swap setting). Think I'm going to keep my eye on this thread in case you figure something out, and I'll probably try to take a stab at it eventually if you don't.

Just re-reading this thread "Real Life"™ got in the way!  ^_^

I'm going to work on a script to create the folder structure just after boot (to kick in once the encrypted swap is created and accessible)

ToDo list: (for a start anyway!)

i) Going to look through most of the software on my virtual system (clean install) for a baseline for folders and structure.
ii) Need to work out a way to check for changes to folders in general use (Need to check if rsync logs can be used for this)
iii) Write a script to create /tmp/ folder structure
iv) Create symlinks for temp folders to point to /tmp/ folder structure
v) Might need to make a script to check if the symlinks exist if not create them.

Once the above is finished, will let it loose for others more skilled in scripts and programing to cater for different installed software. 
As it stands the user would have to manually edit the script every time they installed a program which has temp files they wish to encrypt.

---

### Post by jaygo on 2010-01-18
This is a late reply but hopefully it helps someone. You can create a separate encrypted partition (using the alternate install CD) and give it a random passphrase, then set its mountpoint as /tmp. You might also add /var/tmp and some of the other random places that end up with private data to the same partition. Everytime the machine reboots or powers down, that partition will be as unrecoverable as encryption can make it. I've done this in the past with my swap partitions but it has a downside: you can't hibernate. GL

---

### Post by solitaire on 2010-01-18
I'm doing something like that at the moment!

but I'm pointing /tmp/ and /var/tmp/ to a small ramdrive (256Mb) which is VERY tight or both of them but has the added advantage that once power is gone no more data (and in the UK it's a criminal offence not to give over a password when when asked, if you are ever arrersted) So I'm trying to stay clear of encryption for basic things like /tmp/ and keep if for business and personal files.

---

### Post by lavinog on 2010-01-18
> **solitaire said:**
> (and in the UK it's a criminal offence not to give over a password when when asked, if you are ever arrersted)

Really?  Wow, what happens if you forgot your password?
Does it only pertain to encrypted data, or can they require your bank password?

---

### Post by solitaire on 2010-01-18
> **lavinog said:**
> Really?  Wow, what happens if you forgot your password?
Does it only pertain to encrypted data, or can they require your bank password?
Basically if it's on your PC and requires a password to be readable you *HAVE* to give the police the password otherwise it's upto 2 years behind bars. 

As for Bank passwords, they can go direct to the bank so they don't need it.

Think only 1 person so far has been jailed in the past 10 years, but it's becoming more common to be reported for not giving over a password.

---

