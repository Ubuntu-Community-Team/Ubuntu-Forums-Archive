---
title: "Script, Diff, EXT and Squashfs"
date: 2007-11-22
forum: The Cafe
---

### Post by dmfield on 2007-11-22
OK, so, a bit of a challenge.

I have a situation where I have 2 ext3 files for a project i'm working on, the first i can case my base.ext3 as it has the core files i need on it, the second i will call vpn.ext3

What i have done is taken base.ext3, and installed a Secure VNC client on it. (hence the name vpn.ext3 for the 2nd file)

I can mount both of these files using 

sudo mount <filename.ext3> </some/dir> -t auto -o loop

Works fine.

What i'd like to do, is the following:

Be able to see which files were added and modified on **vpn.ext3** and "extract/lift" those files from the **vpn.ext3** directory only, and put them in a third directory **build**. 

What i'm going to do is..

1) turn **build** into a SquashFS (vpn.sfs)
2) Load my normal system using base.ext3
3) Using union, have the base.ext3 load, then the vpn.sfs load over the top.

I have the script working already for OpenOffice and Citrix client, but the secure VPN client is a bit of a bugger...

Can anyone point me in the right direction?

This is part of a bigger project, so i can't change the way i'm doing what i'm doing..

---

