---
title: "Simple scan and scanning:"
date: 2012-02-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bash321 on 2012-02-05
Ubuntu 12.04:
scanning with samsung clx 3175fn works with [http://www.bchemnet.com/suldr/index.html](http://www.bchemnet.com/suldr/index.html) driver.
i am network scanning with simple scan and it is really slow. it feels as if the settings are not sent to the printer to scan at a lower resolution.
Is there a way to fix this issue?
If this is in the wrong place, could you please redirect me to where i should be posting.
this has been happening since ubuntu 10.10.
bash321

---

### Post by bash321 on 2012-02-05
I do remember scanning with xsane, in 11.10, and that seems to scan faster than simple scan. at the required lower resolution rates.

---

### Post by VMC on 2012-02-05
There's quite a lot of bug reports on Simple scan from Precise downward. The problem I am having is if I scan several pages it just quits and crashes. I emailed the 6meg crash report only to find my issue has been active since 2009. I don't have the bug report off-hand.

you might try searching launchpad for your problem.

I have since used VueScan. It works flawlessly.

---

### Post by bash321 on 2012-02-07
I have filed a bug report on this issue in launchpad.
But I have since changed my stance on the default scanning application in ubuntu to gscan2pdf.

---

### Post by bash321 on 2012-02-07
> **VMC said:**
> There's quite a lot of bug reports on Simple scan from Precise downward. The problem I am having is if I scan several pages it just quits and crashes. I emailed the 6meg crash report only to find my issue has been active since 2009. I don't have the bug report off-hand.

you might try searching launchpad for your problem.

I have since used VueScan. It works flawlessly.
by the way thanks vmc for your input into this issue with scanning on ubuntu with simple scan. Vuescan I believe is an application which you have to pay for.. I think to use all of its features.. I'm sure it is a great scanning solution for you, but I was looking for a free open sourced solution. which I believe I have found called gscan2pdf.

---

### Post by VMC on 2012-02-07
> **bash321 said:**
> by the way thanks vmc for your input into this issue with scanning on ubuntu with simple scan. Vuescan I believe is an application which you have to pay for.. I think to use all of its features.. I'm sure it is a great scanning solution for you, but I was looking for a free open sourced solution. which I believe I have found called gscan2pdf.

Your right, but since I had it - and forgot I had it, I will use that instead. I was hoping the default simplescan worked.

Thanks for the free scan 'gscan2pdf'. I will try that one out.

---

### Post by VMC on 2012-02-14
Simple Scan now works for me using the latest AMD64 ISO(02/14/2012).

One of Simple Scan developers told me to install and try Xsane. If it works and Simple Scan didn't then the problem is with Simple Scan.
Xsane works, but the resolution is bad at the text 150 level. Simple Scan works very well at that level.

[bug report]("https://bugs.launchpad.net/ubuntu/+source/simple-scan/+bug/843361")

---

