---
title: "How do I install Netbeans in Ubuntu?"
date: 2009-09-09
forum: Ubuntu Dev Link Forum
---

### Post by gabimbola on 2009-09-09
Hi:

My question is, I have downloaded Netbeans IDE, that ended with .sh extension. I would like to install this on Ubuntu. I thought what I need to do is to chmod +x and then, the file. Thereafter, I thought I would execute thus: ./Nebeans... Please advise.

I welcome any response to my email (gabimbola@gmail.com).

Your immediate response to the above request would be greatly appreciated.

BTW, I think the "New Thread" button should be at the top, and not at the bottom. My reason is that the latest thread discussion is always at the top. My opinion though.

Sincerely:

Gbenga

---

### Post by mehaga on 2009-09-09
<InstallDir>/bin/netbeans

Do you get any error messages when trying to run that?

---

### Post by kashyap_ankur on 2009-09-11
CD to the directory where you have downloaded the netbeans installer - netbeansXYZABCD.sh

$ chmod +x <file name>
$ sudo ./<file name>

Ankur

---

### Post by mehaga on 2009-09-11
Oh, you can't install :oops:

---

### Post by qamelian on 2009-09-11
Netbeans is in the Ubuntu repos. is there some reason you need to download it instead?

---

### Post by mehaga on 2009-09-11
Yes. 6.5 is in the repos, while 6.7.1 is the latest and greatest :)

---

### Post by roystons on 2009-11-24
If you want to install netbeans, make sure that JDK had already installed on your system and make the Netbeans file executeable. Then you may install Netbeans using this command :
 ./netbeans-6.7.1-ml-linux.sh --javahome /usr/local/bin/jdk1.6.0_17

*Javahome direct to directory where you install your JDK

For more information you may visit [http://rstons.wordpress.com/2009/11/25/instalasi-jdk-dan-netbeans-pada-ubuntu/](http://rstons.wordpress.com/2009/11/25/instalasi-jdk-dan-netbeans-pada-ubuntu/)

Thanks and Regard,
Roystons

---

### Post by ajaykumr on 2010-02-15
Please go for Net Beans 6.7.1 unless you have high end system else you can go for 6.5 or 6.1. They are stable versions. But 6.7.1 supports Java FX too. So it really awesome version from the Net Beans developers.

---

### Post by thunderbox on 2010-02-16
I installed 6.5 from the repos, once booted into netbeans it offers you the upgrade to 6.7.1. much easier than doing it any other way.

---

