---
title: "Firefox 9 NOT working correctly on Medicare.Gov!"
date: 2012-01-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kevpan815 on 2012-01-15
Just 2 let you guys know today I was trying 2 modify some of my information on Medicare.Gov and Mozilla Firefox 9.0 kept giving me Java Script Errors! Anyone else getting Java Script Errors in Firefox 9.0?

---

### Post by dino99 on 2012-01-15
Are you using Precise ? thats might be FF10b4 now

---

### Post by kuvanito on 2012-01-15
it is FF problem not precise
by the way hotmail is showing the same problem

---

### Post by kevpan815 on 2012-01-15
> **dino99 said:**
> Are you using Precise ? thats might be FF10b4 now

I am using Presice, however I am using Alpha 1 with no updates installed. Due 2 my 12 GB Bandwith Limit Per Month, I do NOT install any updates.

---

### Post by kurt18947 on 2012-01-15
I've seen a problem with a few web sites using 11.10/FF 9.0.1.  Certain areas of web pages are blank.  There's no place marker or anything - it's just blank.

---

### Post by kuvanito on 2012-01-15
it is java related so i removed open jdk and installed sunjava,now all is fine..
sudo apt-get purge openjdk*
sudo apt-add-repository ppa:flexiondotorg/java
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin

---

### Post by kevpan815 on 2012-01-15
> **kevpan815 said:**
> Just 2 let you guys know today I was trying 2 modify some of my information on Medicare.Gov and Mozilla Firefox 9.0 kept giving me Java Script Errors! Anyone else getting Java Script Errors in Firefox 9.0?

Update: I just tried again with Mozilla Firefox Nightly Build 12.0 Alpha 1, Same Issue, I was still unable 2 update my Emergency Contact Information on [www.MyMedicare.Gov](www.MyMedicare.Gov)! Please note that you will be unable 2 login 2 this secure website and try it 4 yourself unless you are a Medicare Beneficiary!

---

### Post by kevpan815 on 2012-01-15
> **kuvanito said:**
> it is java related so i removed open jdk and installed sunjava,now all is fine..
sudo apt-get purge openjdk*
sudo apt-add-repository ppa:flexiondotorg/java
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin

That reminds me of the following: Recently I read on Neowin.Net that Ubuntu was going 2 start to remove Java from all of their Install Packages due 2 a Fight with Oracle over modifying Java from Oracle's Original Source Code 2 the way that Ubuntu wanted 2 modify it 2 enhance it's Out of the Box Experience.

---

### Post by kevpan815 on 2012-01-16
> **kevpan815 said:**
> That reminds me of the following: Recently I read on Neowin.Net that Ubuntu was going 2 start to remove Java from all of their Install Packages due 2 a Fight with Oracle over modifying Java from Oracle's Original Source Code 2 the way that Ubuntu wanted 2 modify it 2 enhance it's Out of the Box Experience.

Issue solved. I called Medicare, and they told me that the server was somewhat incompatible with Mozilla Firefox due to their rapid update system that they are using now. They also told me that I needed to use either a Windows Computer with Internet Explorer, or a Mac with Apple Safari. So I used my Mac OS X Lion Computer with Apple Safari, problem solved.

---

