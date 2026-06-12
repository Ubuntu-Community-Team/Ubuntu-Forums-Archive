---
title: "Best Way to Encrypt Data on VPS.... HELP"
date: 2010-11-20
forum: Security
---

### Post by steven.smith on 2010-11-20
Hey there all. I have a linux VPS with Ubuntu 10.04. I would like to create an encrypted file container on my VPS but I have no clue what program to use. Before responding, please know that I am very well aware of the downfalls of encrypting a folder, etc... but still wish to do so. 

I wanted something exactly like Truecrypt. It allows us to make an encrypted file container and requires the password and keyfiles to access it. The problem is, when I tried installing it on my VPS, the installation went through, but when i tried created a volume it kept on giving me the error "fuse: permission denied". I've tried everything I could to get around it, but no luck. The only thing that actually worked was creating a "fat32" filesystem. It created the volume successfully after that. Then when I try to mount it, it gives me a kernel error and a "fuse: permission denied" message and will not let me mount the volume. I tried compiling the kernels on the VPS and chmod the folder with full write access, but it didn't seem to make a difference. So after trying for awhile (and asking for help on these forums with no luck), I basically gave up on getting Truecrypt to work.
--- If you know the solution, please tell.

Anyways.... So I looked on the internet for another possible way to encrypt the data. The best i could find was "EncFS". However, after reading more about it, I learned that the passkey is stored ON the server and could be easily read by anyone who has access to the VPS. 

So the question comes down to... is there a program like Truecrypt that I can use on my linux VPS that is secure and doesn't have big security risks such as EncFS? And can this program be installed successfully on a VPS - Openvz?

Thanks for anyone who can help. All [relevant] advice is welcome :D

---

### Post by Fafler on 2010-11-22
dm-crypt can be used on pretty much everything. Files, partitions etc.

Do you have a link to the EncFS issue? I haven't heard about that before and actually thought EncFS was quite safe.

---

