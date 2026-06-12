---
title: "Brand new Pangolin Performance shutting down suddenly."
date: 2011-07-21
forum: System76 Support
---

### Post by fillmont on 2011-07-21
I just received my new Pangolin Performance computer, and it arrived in a very nice package. I started it up, went through a few steps to set up Ubuntu, and everything was fine.

Until I spent about a minute on the desktop and the machine instantly turned off. This has happened about 3 times now - enough to make me worry. Upon boot up, the computer seems to take an inordinate amount of time to load. 3 or 4 minutes this last time.

I have the power cord plugged in - so it's not an issue of battery life. 

Any ideas?

The only upgrades from the base Pangolin Performance are
*Processor : 2nd Generation Intel Core i5-2520M Processor ( 3MB L3 Cache, 2.50GHz )*
* Memory : 4 GB Dual Channel DDR3 SDRAM at 1333MHz - 2 X 2GB*
[I] Hard Drive : 320 GB 7200 RPM SATA II
[/I]
Edit: So it seems that the power cord did have something to do with it - when unplugged, the machine works fine. Will report with more information as I troubleshoot.

---

### Post by fillmont on 2011-07-21
So upon further troubleshooting, it seems that the machine only shuts down suddenly when the power cord is plugged in. When running off battery, it runs wonderfully.

---

### Post by shadowtrk on 2011-07-23
I recived same machine yesterday 7/22/11 and I am having the same issue!!!!

also it shut off durning the installer and now the installer crashes. it finally droped me into a live user


Laptop works great while on battery.....

---

### Post by rotten on 2011-07-23
hmmm.  I was actually going to order a Pangolin Performance *today*.  I was just surfing around to make sure I was making the right decision.  Maybe I'll wait a few more days to see if this issue is resolved...

---

### Post by fillmont on 2011-07-24
On a whim I installed Kubuntu 11.04, and it seems to work better: i can no go about 30 before the machine shuts down on AC power

---

### Post by shadowtrk on 2011-07-25
> **fillmont said:**
> On a whim I installed Kubuntu 11.04, and it seems to work better: i can no go about 30 before the machine shuts down on AC power

Hey fillmont can u check your battle info please I'm showing 48.8 designed. Charge
But its charging to 49.9. I spoke to Eian in support at 1:30pm eat today and he said this the first reports of issues

---

### Post by fillmont on 2011-07-25
> **shadowtrk said:**
> Hey fillmont can u check your battle info please I'm showing 48.8 designed. Charge
But its charging to 49.9. I spoke to Eian in support at 1:30pm eat today and he said this the first reports of issues

Apologies, but I'm having trouble understanding your message. Could you try again? 

Further troubleshooting shows that if I attempt to boot the computer while plugged in to start, the machine will shut down within a minute of start up. If I run the machine on battery life for an amount of time, and then plug it to the wall, I can run the machine for about 30 to 40 minutes until it shuts down.

---

### Post by isantop on 2011-07-25
Hi Fillmont.

Please log in to the computer on battery power to avoid a shutdown, then click on the battery icon in the upper panel and click on the battery (It should say "estimating...")

Then look at the data in that window and compare the Energy when full to the Energy (design) fields. Can you post the values here so that we can compare them to the ones on the Pangolin in the shop and see if that's causing the problem?

---

### Post by fillmont on 2011-07-25
Here are the values: 

Energy when full: 49.2 Wh
Energy (design): 48.8 Wh

(I should note that I'm Henry, who emailed you earlier.)

---

### Post by perspectoff on 2011-07-25
Hmmm,

 Parading Pangolin?

---

### Post by isantop on 2011-07-26
@fillmont: Thanks, that's what I needed.

@perspectoff: Actually, I was thinking Phuzzy Pangolin, just for the laugh value.

---

### Post by shadowtrk on 2011-07-26
Good Morning.

Finally got home to take some screen shots this morning and low and behold its working on a/c for awhile now. so i dont know.


here is the screen shot of the batt stats.

[IMG]http://i.imgur.com/cOPPI.png[/IMG]

---

### Post by gdgilda on 2011-07-27
FWIW, I've been running on a new panp8 received this month with a very similar configuration as described in the original thread post, and have had no problems with sudden shutdowns with AC or battery power.

panp8
i5-2410
4GB ddr3
320GB

Glenn

---

### Post by luwenliang0611 on 2011-07-28
These things looked pretty good, and some that I can learn, and I hope to learn more on it!

---

### Post by shadowtrk on 2011-07-31
ok had the system a week now still powering off randomly on AC it does it on ac alone, while chargeing, fully charged. One thing I have noticed is that everytime it does shutdown like that the sound card comes up muted??? also the batt stats have changed. 

its actually matching lol. 48.8 designed 48.5 when full.


On battery system is FLAWLESS it works wonderfully!!!!! but I work from home and cant keep chargeing the battery and then useing machine till its dead then waiting 1=2 hrs for it to recharge. 


System 76 says they have units in the shop that ARE NOT doing this. looks like they would jsut cross ship us units?

System76: if you need my order number please contact me via email.

---

### Post by fillmont on 2011-08-05
So, an update:

It seems that with both Ubuntu 11.04 and Kubuntu 11.04 I had the issue with computer shut down.

However, on a whim, I decided to install the Alpha 3 release of Ubuntu  11.10. I figured I'd take a look at gnome shell before sending it back  to you all. But, as it turns out, the machine hasn't shut down on AC  power since installing 11.10. It's been around a day, and with frequent  manual shut downs while plugged into the wall, the machine has yet to  turn off unexpectedly.

I will keep using the machine with 11.10 to see if I can replicate the  instant shutting down, but it seems to work fine now. Can anyone think of  a reason why the laptop would get along better with 11.10 than 11.04?

---

### Post by fillmont on 2011-08-09
After a week or running 11.10 alpha 3, the shutdown problem has yet to recur. Success, I guess!

---

### Post by isantop on 2011-08-11
We do have reports that replacing the AC adapter seems to clear the issue right up. For anyone who is still experiencing this issue, please send us an email at support...at...system76...dot...com.

---

### Post by shadowtrk on 2011-08-12
REALLY NOW! Tom just had me send in my machine because support couldn't figure out whats wrong. so 3-4 weeks for just a power cord!?!?

---

### Post by merpius on 2011-08-26
We are experiencing this issue as well; we've tried several different power adapters and the problem occurs with all of them. Good to hear that 11.10 may fix the issue, but this is a production machine for us, so using a beta release is not very desirable. We're trying to RMA it back to System76 already.

---

