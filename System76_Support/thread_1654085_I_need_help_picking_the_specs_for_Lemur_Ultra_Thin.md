---
title: "I need help picking the specs for Lemur Ultra Thin"
date: 2010-12-27
forum: System76 Support
---

### Post by Mindswap1 on 2010-12-27
Hi Guys! So I was messing around with the available specs for the Lemur Ultra Thin from System 76, and I can't seems to figure out whats the difference between the available stuff. 

So Far I have it configured at Ubuntu 10.10, With a i3 Processor, followed by 6 gb of ram, and a 500 GB 7200 RPM SATA II hard drive, also I have a external USB CD-RW / DVD-RW. And Intel Centrino Advanced-N 6200 - 802.11A/B/G/N Wireless LAN Module for wireless. 

However I was really confused. There is a option to get a 500GB 7200rpm SATA Hybrid Hard Drive with 4GB SSD. How does this differ from the 500 GB 7200 RPM SATA II hard drive. Should I get the hybrid hard drive instead, and downgrade the ram to 4gb instead of 6. 

Also the optical drive's name is external USB CD-RW / DVD-RW. Does this mean that the drive is not inside the laptop itself, and has to be plugged in via wire? 

And lastly whats the difference between the 802.11 B+G+N Wireless LAN Module. And Intel Centrino Advanced-N 6200 - 802.11A/B/G/N Wireless LAN Module.

I really appreciate the help! I just want to make sure I'm buying the best available specs with my budget for when I buy the laptop. You Guys ROCK!

---

### Post by jml on 2010-12-27
I am not an expert, but I do have a bit of information I can share with you.

1.  The hybrid drive combines a conventional hard drive with a small solid state (the 4 gig part) hard drive.  It theoretically speeds up data reads and writes.  Launching applications reading data, etc. Seagate (a manufacturer of hybrid drives) says that their hybrid runs at the speed equivalent to a 10,000 rpm conventional drive. If increased speed is important to you, then it might be worth the extra money.  In my opinion, a 7200 rpm drive is plenty fast for my needs.

2.  Ram, unless you plan to run multiple resource hungry applications at the same time, 4 gigs of ram should be more than adequate for your needs.  In fact, the i3 Processor will become a bottleneck before the ram will.

3.  Optical drive:  In order for the Lemur to be so small and light, it does not have a built in optical drive.  You are correct, the optical drive is a separate device that is connected to the Lemur via 2 USB cables.  If you intend to play music CD's or DVD's on the Lemur, you will need to carry the drive with you when you travel.  Many people only use the optical drive to install apps and data, loading both music and movies onto the Lemur's hard drive.

4.  Wireless:  The Intel wireless card is a bit more Linux friendly than the stock wireless card.  So, if at some time in the future, you want to load a different Linux distro on the Lemur, the Intel card should be a bit easier to get running.  The Intel card is also said to have a little better performance (speed and range,) than the stock card.

5.  Battery:  With the money you would save by not buying the hybrid drive, and settling for 4 gigs of ram, you might want to consider buying an additional battery.  According to System 76 staff, the standard battery will get between 2.5 and 3 hours of run time.  If you want longer battery life you may want to consider getting the 62.15 WH (twice the capacity of the standard) battery.

Again, I am neither a computer professional, nor a System 76 employee.  These are just my opinions for what they are worth.  Have fun shopping.

Joe

---

### Post by Mindswap1 on 2010-12-28
Thank You So Much JML! I really can't thank you enough. I was hoping u could help me with one last question. You mentioned that I should invest in getting a better battery, and I agree. I was wondering though does this mean they will give me two batteries? Or will I just be given one battery that last longer. It sounds like a stupid question, but the only reason I ask is cause its titled as Extra Battery on the website. And will the longer lasting battery make the slim factor of the laptop useless. I noticed that laptops with longer batteries tend to be thicker, and I really like the Lemur , because it was really slim. Thanks In advance I can't thank you enough.

---

### Post by isantop on 2010-12-28
It certainly won't make a form factor useless. We have some picture up on our facebook page: [urlhttp://www.facebook.com/photo.php?fbid=10150145130477729&set=a.10150145130387729.347587.38123997728[/url]. You would receive two batteries, as we can't ship the Lemur without the standard battery right now.

Also, JML's battery life estimates were our initial guesses. We're seeing that the standard battery is lasting around 1.5 to 2 hours. The extended one should get about four.

---

### Post by jml on 2010-12-28
Thanks for the clarification, isantop.  It's really a shame how these more powerful laptops suck down battery life so quickly.  Given that information, if I were buying a Lemur, I would definitely get the bigger battery in addition to the stock one that ships with the Lemur.

Joe

---

### Post by Mindswap1 on 2010-12-28
Thanks Guys! This really helped me out a lot. You guys rock! So once again thank you so much for your wisdom.

---

### Post by Eres on 2011-01-03
Another question about the 2nd battery: can one use both batteries at the same time, or the 2nd battery replaces the first one?

If I have two batteries, must I turn my laptop completely off in order to change battery or can I just suspend it?

---

### Post by Flyers2391 on 2011-01-05
> **Eres said:**
> Another question about the 2nd battery: can one use both batteries at the same time, or the 2nd battery replaces the first one?

If I have two batteries, must I turn my laptop completely off in order to change battery or can I just suspend it?

suspend requires power to RAM so you would have to plug in to swap batteries and stay powered.  Assuming the Lemur hibernates you could hibernate it and then swap batteries.

---

### Post by isantop on 2011-01-05
The Lemur hibernates just fine, so there wouldn't be any issues there. You simply hibernate, swap the batteries, then resume.

---

### Post by Eres on 2011-01-05
Thanks for the answers. So I cannot use both batteries together, but I have to swap them once the first is flat, right?

A last question: in order to ibernate the laptop one has to have a swap partition? Because I would buy a small SSD hard disk; on such a device, a swap region would require "costly" space...

---

### Post by isantop on 2011-01-07
Hibernation does require as much free swap space as you have physical RAM. However, Ubuntu also recommends this as a minimum requirement, and while you would probably be fine in operation, it really doesn't hurt to have more swap than you need. Obviously, you'll want to balance swap with storage, but it does provide a nice overhead in case you start doing something that fills the RAM up.

An alternative is to keep the system plugged in while you swap batteries. I think this defeats some of the point, but if it would work for you, you could make it without as large of a swap partition.

---

