---
title: "Natty driver fix."
date: 2011-05-25
forum: Testimonials &amp; Experiences
---

### Post by ventrical on 2011-05-25
Just sharing a tip/trick. 

I live on a border city in North America, right on the line between Canada and the U.S.  During alpha, beta and LTS installs I would just allow default installs to (English US). But on other occasions I would choose (English Canada).

 I was having a heck of a time getting the wireless working for Natty and Mint on a few installs. Then I went to search and found a method of re-installing Broadcomm Drivers for some wireless laptops. 

After entering the code suggested at the web-page I was able to see that my (English_Canada) UTF8 file was being reported as an error.

 So then I went and changed the language back to  (English US) and  Ta Da !!!!! Instant wireless detect of Broadcomm drivers!!!!

   I am not trying to make a bug report here but I just wanted to make note of *my* experience and how I was able to fix the wireless driver problems I have had. I am not sure if it is a bug overall all with the Natty kernel, but, perhaps, by default, some languages may not be recognized (or are excluded) during the install and I would not have discovered this if I did not use the <terminal> apt -reinstall of the broadcomm drivers.

 Thanks

---

### Post by ventrical on 2011-05-25
And this one is a sure fire fix.
[http://askubuntu.com/questions/44355/broadcom-issue-in-natty-but-not-in-maverick](http://askubuntu.com/questions/44355/broadcom-issue-in-natty-but-not-in-maverick)

thanks again!

:)

---

### Post by ventrical on 2011-05-25
Please ignore my last 2 messages.  I made a small adjustment in the Unity Plugin from Compiz, to have the tool bar dock from the bottom and now the wireless is busted again.

Everything works good as long as you don't fiddle with COmpiz.

---

