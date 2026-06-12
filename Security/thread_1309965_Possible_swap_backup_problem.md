---
title: "Possible swap backup problem?"
date: 2009-11-01
forum: Security
---

### Post by pedja_portugalac on 2009-11-01
Hi there

Today, I have installed new version of Ubuntu (9.10) from alternate i386 CD. 
After download, the hash matched and check disc for defects also give no error. But, while installing, it freeze installation close to the end. Exactly while writing passwords and user account. After more then 5 minutes waiting I decided to "hard way" restart. After restarting, there was a problem mounting sdb5 (my installation is on sdb disk), everything else looked OK so I have done my costume settings and decided to make a backup image of whole disk using clonezilla live CD. 
My Ubuntu is installed on one entire disk of 320GB. Two partitions, sdb1 and sdb5 (swap). Creating backup image of HDD with just fresh installed Ubuntu takes no more then 6-7 minutes and it was so till it come to the sdb5 part. Then it warned me, partimage doesn't recognised file system and it will be cloned with dd. Whole partition no matter if written or empty sectors will be copied bit to bit, one by one. My sdb5 (swap) is about 9GB and I was waiting all the way till it was done. I was imagining it will take 9GB on my external HDD but after I have checked it takes only 68kb for sdb5.dd-img.aa and the whole image was under 800MB. 
I am wondering if someone else had similar problem, and even if this is a problem? Never happened to me before with ext3 file system.
Now I will try to restore from that image, it takes 4 minutes on my laptop, and I'll try to install again from ubuntu9.10-alternate-i386 CD to see if it'll freeze again by the end. I'll let you know what happened and would like to hear if you to had some of this problems.

---

### Post by pedja_portugalac on 2009-11-01
Trying to restore the image give the same result. Slow dd restoring of sdb5. So I reinstalled Ubuntu from CD but this time I chose not to encrypt home directory. And what happened, no problems, installation goes normally till the end. Creating backup image with clonezilla 1.22.31 also was without problem.

Conclusion, there may exist a bug with encryption of home directory when we install from alternate i386 CD?

---

