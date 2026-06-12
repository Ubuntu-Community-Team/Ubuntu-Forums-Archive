---
title: "What's broken in AMD64?"
date: 2012-01-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by teh603 on 2012-01-03
Anyone got a manifest of what does and doesn't work in 64-bit Precise Pinecone? I'm thinking about trying it on my Inspiron Duo now that it got back from the factory and everything's actually working like its supposed to, and the Duo has issues with 32-bit software from time to time.

---

### Post by collisionystm on 2012-01-03
pinecone?

---

### Post by teh603 on 2012-01-03
> **collisionystm said:**
> pinecone?A lame attempt at a joke since pangolins look a bit like pinecones.

---

### Post by collisionystm on 2012-01-03
> **teh603 said:**
> A lame attempt at a joke since pangolins look a bit like pinecones.

Ah gotcha. I see you add the prefix Precise.

---

### Post by teh603 on 2012-01-03
Yup. That'll hopefully make it actually funny. Although I don't want to derail this too much; I'd kinda like some help figuring out just what's safe to install and what's borked to hell and back.

---

### Post by scradock on 2012-01-03
> **teh603 said:**
> Yup. That'll hopefully make it actually funny. Although I don't want to derail this too much; I'd kinda like some help figuring out just what's safe to install and what's borked to hell and back.

What do you want to install? Everything I use is working fine on an old Athlon, and on a Core 2 Duo T5800 from Intel for that matter.

---

### Post by ronacc on 2012-01-03
everthing is ok here on my amd64x2 sys .

---

### Post by sammiev on 2012-01-03
With all the updates the last day or two has been given me a few errors. They are there one min and gone 4 hours later. Over all it's been very good but the network manager. The network manager has been causing a lot of problems on shut down.

---

### Post by teh603 on 2012-01-03
Ok, so nothing to worry about anymore? Cause last I'd heard, there was a problem with the ia32lib or something close to that name, and it was making trouble or stuff that wasn't natively 64-bit.

---

### Post by ronacc on 2012-01-03
I believe a few non default apps like wine  have problems with it but the normal stuff I have tried has all been ok .

---

### Post by cariboo on 2012-01-03
> **teh603 said:**
> Ok, so nothing to worry about anymore? Cause last I'd heard, there was a problem with the ia32lib or something close to that name, and it was making trouble or stuff that wasn't natively 64-bit.

There are problems with mutliarch still, but if you don't need any 32-bit apps, or wine, you shouldn't have any problems.

---

### Post by ventrical on 2012-01-04
I still can't get ATI Radeon Express1250 driver to be installed on that 64AX2.

---

### Post by rajeev1204 on 2012-01-04
There was a problem the ia32 libs package and its dependencies but it seems to be fixed now. I have wine installed and running fine.

---

### Post by fjgaude on 2012-01-04
For me it's been slightly more stable than 11.10... thus let's say it is solid at the moment. Can't tell what is going to happen tomorrow! <smile>

---

### Post by P-I H on 2012-01-04
I Installed the daily build from today January 4 and had some problems. I use an Nvidia card, GTS250.
I had to use nomodeset to boot the Desktop CD, which is copied to a USB stick with the dd command.
After installation I had to boot with recovery mode and then select normal boot, to start the system.
After installation of the proprietary Nvidia driver (version current), the system works OK.
I haven't tried to install Wine yet.

---

### Post by MacUntu on 2012-01-04
> **rajeev1204 said:**
> There was a problem the ia32 libs package and its dependencies but it seems to be fixed now. I have wine installed and running fine.
IMO it depends on what software you have installed whether it's fixed or not. With Skype, Adobe Reader, and Google Earth it's still not fixed here. I have all installed, because I upgraded from Oneiric, but that's why I cannot update the ia32libs package. :KS

---

### Post by rajeev1204 on 2012-01-05
> **MacUntu said:**
> IMO it depends on what software you have installed whether it's fixed or not. With Skype, Adobe Reader, and Google Earth it's still not fixed here. I have all installed, because I upgraded from Oneiric, but that's why I cannot update the ia32libs package. :KS

I have skype installed yesterday too. But you are right. It magically pulled in the ia32 libs package yesterday after many tries so iam not sure what exactly happened there. But it is surely working.

This is a good read.

[http://ubuntu.5.n6.nabble.com/multiarch-in-12-04-the-home-stretch-for-ia32-libs-help-requested-td725119.html](http://ubuntu.5.n6.nabble.com/multiarch-in-12-04-the-home-stretch-for-ia32-libs-help-requested-td725119.html)

---

### Post by QIII on 2012-01-05
If it's stable today, don't fret.  There's always unborking to do tomorrow!

---

### Post by 1roxtar on 2012-01-05
I have Dell Dimension E521, AMD64 Athlon X2, 5 Gigs of RAM, Nvidia Geforce 9500 GT video card and everything seems to be working great.  It feels faster than 11.10 and despite being an Alpha 1, Precise feels pretty stable.  I have been running it for several hours now and I had only one crash alert with the Software Center, but nothing froze or shut down.  So far this has been the best Ubuntu Alpha 1 that I have ever used.  I can't wait to see how it gets by the time the first beta comes out.  Precise Pangolin FTW!!!

---

### Post by rajeev1204 on 2012-01-06
> **1roxtar said:**
> I have Dell Dimension E521, AMD64 Athlon X2, 5 Gigs of RAM, Nvidia Geforce 9500 GT video card and everything seems to be working great.  It feels faster than 11.10 and despite being an Alpha 1, Precise feels pretty stable.  I have been running it for several hours now and I had only one crash alert with the Software Center, but nothing froze or shut down.  So far this has been the best Ubuntu Alpha 1 that I have ever used.  I can't wait to see how it gets by the time the first beta comes out.  Precise Pangolin FTW!!!


You are spot on. I often forget iam using an early alpha, precise is so stable. Or maybe the risky updates are yet to come on.

But if memory serves me correct, i used to start a new version from alpha 3 onwards and that too used to crash often, but this alpha is something quite different.

---

### Post by 1roxtar on 2012-01-06
I have a Dell Dimension E521, AMD64 Athlon X2, 5 Gigs of RAM, Nvidia Geforce 9500 GT video card and everything seems to be working great.

> **rajeev1204 said:**
> You are spot on. I often forget iam using an early alpha, precise is so stable. Or maybe the risky updates are yet to come on.

But if memory serves me correct, i used to start a new version from alpha 3 onwards and that too used to crash often, but this alpha is something quite different.

This has been my primary testing computer since 11.04 and with this same machine, Alphas were completely unusable until at least the first Beta came out.  I am completely impressed with Precise. It gives me so much to look forward to in April.  Ubuntu 12.04 is the version I really intend to push for my home-based computer tech/repair business because of the new 5 year desktop support, it's LTS stability and a more refined Unity.  (Another plus, my fans and hard drive don't seem to run as loud as they did with 11.04 and 11.10)

---

### Post by thedarkdonut on 2012-01-07
The only problem I came across so was Skype because of the multiarch problem.

---

### Post by TDK800 on 2012-01-07
+1 Skype not working because softwar center "Cannot install 'ia32-libs'"

---

### Post by rajeev1204 on 2012-01-08
Hi

Can you try installing wine 1.3 and then skype after. I have skype running on my system and i remember either skype or wine pulling in the ia 32 libs package.

Also, make sure your repositories are set to the main server.

---

