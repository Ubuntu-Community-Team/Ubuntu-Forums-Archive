---
title: "Passphrase-encrypt entire partition"
date: 2010-02-17
forum: Security
---

### Post by adamatan on 2010-02-17
Hi,

In older versions of Ubuntu, mainly 8.04, I could encrypt en entire partition using LUKS, and mount it as /. the /boot directory was mounted on another partition.

At boot time, I had to enter my password to enable any access to anything other than /boot.

In Kuuntu 9.10, I only have the option to encrypt my /home/adam directory, which is a bit of a problem for me because I have sensitive data located in other directories.

Any ideas how to set up LUKS for the entire disk, preferably during installation?

Thanks in advance,

Adam

---

### Post by bodhi.zazen on 2010-02-17
Same as previous, you install Ubuntu from the Alternate CD, not the desktop CD.

[http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml)

yes that is written for 8.04, but applies to 8.10, 9.x, and 10.04 as well.

---

### Post by adamatan on 2010-02-18
> 

 				 				**Re: Passphrase-encrypt entire partition** 			
 			 			 		   		 		 		Same as previous, you install Ubuntu from the Alternate CD, not the desktop CD.

[http://news.softpedia.com/news/Encry...04-85271.shtml]("http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml")

yes that is written for 8.04, but applies to 8.10, 9.x, and 10.04 as well.




Thanks!  I think this should work.

[http://releases.ubuntu.com/kubuntu/9.10/](http://releases.ubuntu.com/kubuntu/9.10/)

---

