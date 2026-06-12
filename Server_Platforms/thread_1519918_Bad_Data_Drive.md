---
title: "Bad Data Drive"
date: 2010-06-28
forum: Server Platforms
---

### Post by tbzep on 2010-06-28
I just finished building a file server with Ubuntu Server 10.04. I used two old hard drives, one for Ubuntu Server, the other for data. After wrestling with it for several hours, I got it going and it's been running fine now for a couple of days.

I shut it down to move it into its cubby hole and fired it up again. Much to my frustration, I got a S.M.A.R.T. notification at boot saying my data drive is bad and I need to replace it immediately.

I'm not worried about any data saved on the drive because I have all the files backed up on an external drive.  Can I just swap in another one without having to change any settings or jumping through the samba hoops again? I've got another drive laying around that used to have WinXP on it.

What about formatting? Since it was a WinXP drive, it should be formatted already.

---

### Post by jbrown96 on 2010-06-28
You will need to format the drive and modify fstab.

1) The first thing to do is modify your /etc/fstab. You need to find the line that represents your data drive and put a # at the beginning using a text editor. That will prevent Ubuntu from trying to mount the drive at boot.

2) Remove the broken drive and insert the new one, then boot Ubuntu. 

3) Format the drive using fstab and mkfs, then add the entry into /etc/fstab. Generally the easiest way is to find the UUID of your newly formatted drive, then susbstitute the UUID from the entry that you commented out (#) in step 1.

---

### Post by tbzep on 2010-06-28
> **jbrown96 said:**
> You will need to format the drive and modify fstab.

1) The first thing to do is modify your /etc/fstab. You need to find the line that represents your data drive and put a # at the beginning using a text editor. That will prevent Ubuntu from trying to mount the drive at boot.

2) Remove the broken drive and insert the new one, then boot Ubuntu. 

3) Format the drive using fstab and mkfs, then add the entry into /etc/fstab. Generally the easiest way is to find the UUID of your newly formatted drive, then susbstitute the UUID from the entry that you commented out (#) in step 1.

Thanks.  I'll give it a go.

---

### Post by tbzep on 2010-06-29
That took care of it.  Thanks.

---

