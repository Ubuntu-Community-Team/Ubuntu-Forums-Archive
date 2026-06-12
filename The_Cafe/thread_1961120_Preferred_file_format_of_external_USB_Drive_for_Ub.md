---
title: "Preferred file format of external USB Drive for Ubuntu Server."
date: 2012-04-18
forum: The Cafe
---

### Post by donniezazen on 2012-04-18
Hi,

I am going to format a western digital 1.5TB external usb hard drive for Ubuntu server. What should be the format for this external drive to? EXT4. I rarely use windows and am looking for a format that robustly works with Linux systems.

Thanks.

PS:-Sorry, this might be a re-post. I am unable to get the right search term.

---

### Post by for.i.am.root on 2012-04-18
No windows, use EXT4. Windows use NTFS.

---

### Post by CharlesA on 2012-04-18
> **for.i.am.root said:**
> No windows, use EXT4. Windows use NTFS.

This pretty much.

I use EXT4.

---

### Post by donniezazen on 2012-04-18
> **CharlesA said:**
> This pretty much.

I use EXT4.

I was also thinking about EXT4.

What do you think of UFS or ZFS? I have FreeNAS in my mind. I used it for a while and still have the external hard drive in UFS format. I do not plan to buy another hard drive and was thinking about coming back to Ubuntu for I find I can do a lot of things on Ubuntu. FreeNAS might be better idea if I had multiple hard drives.

Thanks for replying.

---

### Post by for.i.am.root on 2012-04-19
Ext4 is journaled so data recovery is fairly easy.

I have never used UFS or ZFS so no comment on those.

My advice (FWIW) is to stick with whatever you like as long as it's journaled.

---

