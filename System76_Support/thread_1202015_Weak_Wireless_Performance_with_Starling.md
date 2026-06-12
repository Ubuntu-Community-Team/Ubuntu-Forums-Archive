---
title: "Weak Wireless Performance with Starling"
date: 2009-07-01
forum: System76 Support
---

### Post by Georgesl on 2009-07-01
I started to discuss this on another thread, but it became apparent that this is a different problem than the one being discussed there so I started a new thread for it.

I have been using my new Starling for a few days now and I'm having problems making wireless connections.  If the signal bar in the network list is completely full it will connect, but it won't connect with anything less than that.  The Starling has to be within 15 feet or so of the access point for this to happen.  If a connection is established and I move away from the access point the Starling will not communicate if the signal is less than 100%.

For example, I'm currently sitting about 10 feet from my wireless access and the connection is fine.  If I hover over the wireless signal strength icon it reads "100%".

If I take the Starling ten steps down the hall to a bedroom the wireless no longer communicates.  It remains connected and if I hover over the wireless signal strength icon it reads "92%" to "95%."  There is nothing between the wireless access point and the computer other than sheet-rock walls.  If I walk back toward the access point the connection begins to work again.

Repeating the exercise with my Dell 1501 laptop on XP results in no degradation of wireless performance.  The signal strength indicator goes from "Excellent" to "Very Good" and the connection continues to work perfectly.  In fact, I can take the Dell outside to the far corners of my yard, with wire-reinforced stucco walls in between, and the signal never drops below "good" and communications remain flawless.

The Starling has also experienced this same lack of performance at the two public access locations I've tried.  Unless I am within less than 15 feet of the actual access point a connection cannot be established.  The network  appears on the list of available networks, the bar graph shows 75% or more, but the connection fails to establish.  Those around me, with a variety of laptops and netbooks have no problem establishing and maintaining good connections at these locations.  

I'm a Ubuntu novice, but I've dealt with radio and data for years.  It seems to me that the Starling's hardware is able to receive the signal well enough to interpret its strength, but for some reason the software won't accept anything less than a perfect connection.  My experience with other computers is that as the signal strength drops the connection gets slower.  With the Starling it just stops, and quickly.

I'm hoping that a fix is available for this.  My wife bought the Starling so that I could stay in touch with her on the road without carrying the big laptop, but if the wireless performance is this poor it isn't going to work for me.

---

### Post by thomasaaron on 2009-07-02
Run your System76 Driver...

Administration > System76 Driver > Install (tab) > Install (button). If that doesn't increase your range, please email me at [email]support@system76.com[/email].

---

### Post by Georgesl on 2009-07-02
> **thomasaaron said:**
> Run your System76 Driver...

Administration > System76 Driver > Install (tab) > Install (button). If that doesn't increase your range, please email me at [EMAIL="support@system76.com"]support@system76.com[/EMAIL].

I did as you said, the installation finished within a few seconds.

I rebooted and tried the same experiments as before.  The range may be slightly improved but it might be my wishful thinking.  It's still not close to standard.

Thanks for the quick response.  I'll take it to email as instructed.

---

### Post by cdysthe on 2009-07-14
Hi,

I noticed the same thing with my Starling. I can't even move to another room without wireless going out. A netbook with weak wireless performance is not exactly optimal (to say the least!). 

I've been in contact with system76 about this and recenty I got this answer:

Hi,
 
We've recently learned that the range kimitation on the Starling is an issue with the driver for the RTL8187 wireless card. It is being actively worked on (it didn't work at all under Intrepid). We expect the range to increase as the driver is improved. One customer I recently spoke to purchased a wifi relay and placed it on the other side of his house, and he now has a strong signal throughout.

Regards,
system76

I do not know what to say about this really. When you purchase a computer from a company which delivers Ubunty based only you would expect and essential feature like wireless to work normally. I hope the update comes around soon since it's a drag having to ask people for the table at my favorite coffee house closest to the access point.

//C

---

### Post by jml on 2009-07-14
I have to agree with you, cdysthe.  The Starling is the third computer I have purchased from System 76 and its the first one where something as important as wireless did not work well out of the box.  According to Tom, they needed to use a driver from the backports repository to get the wireless working!  Support for the Starling's wireless card is not yet widespread in the Linux community.  It interesting to note that when I "Googled" the wireless card, this is the first reference I found:

[http://www.bioticaindia.com/rtl-8187-wireless.html](http://www.bioticaindia.com/rtl-8187-wireless.html)

They list driver support for several versions of Windows, Unix, but not Linux.  Quite frankly, I was a bit suprised that System 76 chose a netbook design with poor driver support in Linux.  I also hope that the driver issue is resolved soon.  Except for the wireless issue, I really like the Starling.

Joe

---

### Post by cdysthe on 2009-07-14
> **jml said:**
> I have to agree with you, cdysthe.  The Starling is the third computer I have purchased from System 76 and its the first one where something as important as wireless did not work well out of the box.  According to Tom, they needed to use a driver from the backports repository to get the wireless working!  Support for the Starling's wireless card is not yet widespread in the Linux community.  It interesting to note that when I "Googled" the wireless card, this is the first reference I found:

[http://www.bioticaindia.com/rtl-8187-wireless.html](http://www.bioticaindia.com/rtl-8187-wireless.html)

They list driver support for several versions of Windows, Unix, but not Linux.  Quite frankly, I was a bit suprised that System 76 chose a netbook design with poor driver support in Linux.  I also hope that the driver issue is resolved soon.  Except for the wireless issue, I really like the Starling.

Joe


I like the Starling a lot also. I am actually more than a little surprised they chose this model as their netbook knowing the wireless driver support was lacking. Was they hoping it would be resolved, or did they simply not test the range when they evailuated it? I didn't even think of the range being a problem when I first couldn't connect from the room next to the access point! It took several e-mails to support before it dawned on me it didn't reach the 30 feet into the next room. Oh well, I hope they fix it soon since we are in the market for several netbooks in my compnay. Right now I am a little bit embarrased having tried to sell the Starling internally to my management...

UPDATE: system76 support wrote me today and told that they have a fix possible in just a few days. They are doing tests in their labs now. So there's hope! :)

//C

---

### Post by jediborger on 2009-07-14
That would be nice if they resolve the issue. It seems I might be having this issue. I already went through the process of returning my Starling thinking the wireless card was faulty. Just received the new one today and was very disappointed to be having the exact same issues. Well I already fired off a return email but I would be willing to wait another week to see if their fix works.

---

### Post by cdysthe on 2009-07-14
> **jediborger said:**
> That would be nice if they resolve the issue. It seems I might be having this issue. I already went through the process of returning my Starling thinking the wireless card was faulty. Just received the new one today and was very disappointed to be having the exact same issues. Well I already fired off a return email but I would be willing to wait another week to see if their fix works.

I will ask to return mine also unless a fix is found. A netbook with weak wireless is just not a very useful device. I got it to be able to take it everywhere. Right now I have to leave it next to my accesspoint. I spent some time getting Linux Mint on it thought. I hate to have to do that all over again! :)

//C

---

### Post by kingnerd on 2009-07-17
This is important.  Don't let it fall to the wayside.

---

### Post by cdysthe on 2009-07-17
> **kingnerd said:**
> This is important.  Don't let it fall to the wayside.

I'll ping them again tomorrow and let you know how it goes.

---

### Post by jediborger on 2009-07-17
Don't worry, at least cdsynthe and myself are actively pursuing this topic. I am waiting for a response to an email I sent.

---

### Post by thomasaaron on 2009-07-17
Still testing today. Should be done by C.O.B. Will send out email updates.

---

### Post by jml on 2009-07-17
At the risk of sounding stupid.  Precisely what do the letters C.O.B. stand for?  Also, will System 76 post a notice on this forum when the driver is ready?  so, those of us who have not contacted customer support will know as well?  Thanks.

Joe

---

### Post by jdb on 2009-07-17
> **jml said:**
> At the risk of sounding stupid.  Precisely what do the letters C.O.B. stand for?  Also, will System 76 post a notice on this forum when the driver is ready?  so, those of us who have not contacted customer support will know as well?  Thanks.

Joe

Close Of Business day

---

### Post by jml on 2009-07-17
Thanks, jdb.  Boy, I really should have taken some busines classes when I was in college.  :-)

Joe

---

### Post by gila_monster on 2009-07-17
> **jml said:**
> Thanks, jdb.  Boy, I really should have taken some busines classes when I was in college.  :-)

Joe

Now, Joe, the point of college is to get SMARTER, not DUMBER. ;)

Almost certainly System76 will post the solution here, but if not, you can always share it with the group yourself.

---

### Post by cdysthe on 2009-07-17
I will share what I learn here. I really appreciate that system76 tries to take care of customers. I've had major brand, like Dell, laptops witch flaws their support simply denied. I really like my 'lil Starling which for the moment seems to be wiithout wings to fly very far! :)

---

### Post by jml on 2009-07-17
I agree with you cdysthe, my Starling looks pretty funny with a long CAT5 cable sticking out of it.  I hope the new driver works.  Keeping fingers, eyes and toes crossed.  ;-)

Joe

---

### Post by paulbary on 2009-07-17
I'm on my Starling right now on the first nite of a two week trip ... my hotel tonite has a wired connection ... kinda old school ... it would be awesome if the "fix" came shortly as I'm sure wireless will be factoring in shortly .... I agree with the comments .... the Starling is a lovely
machine save this one weakness .... hopefully to remedied shortly!

Cheers,

Paul

---

### Post by val67 on 2009-07-18
Ok, COB is over, so what is the status Thomas, please

---

### Post by jml on 2009-07-18
While waiting for the driver update, I found a hardware workaround for the problem.  I bought a Belkin 802.11G USB network adapter on clearance from Walmart for a little under $30.00 US.  All I did was plug it in, and after boot up, I had reasonably good wireless performance.  I am writing this from my Starling about 25 feet from my access point without problems.  Its not an ideal solution, but it will hold me over until the Starling driver issue is resolved.

Joe

---

### Post by mrchuc on 2009-07-19
Do I understand that it worked right out of the box. No configuration or installs?

Chuc

---

### Post by jml on 2009-07-19
That's right, Chuc.  Here are the steps.  
1.  Turned on Starling with the USB wireless adaptor plugged in.
2.  After boot up and log in at the desktop, a dialogue box opens stating that "Authentication required for wireless network." (I use WPA encryption on my network,) clicked on the connect button.  
3.  Wait about 30 seconds, during that time the dialog box pops up again, presumably for the internal card.  I clicked cancel this time.
4.  After about 30 seconds the network manager applet announces that I am connected to my wireless network.
5.  I am now on the net, able to view web pages, watch Youtube videos, check e-mail.

I confirmed that this does not harm the internal wireless card.  I booted the Starling right next to my wireless AP without the USB device plugged in and as long as I maintained 100% signal strength, it worked fine.  With my set-up, I get about 10-15 foot range on the internal card.  With the USB device plugged in, I can connect out past 40 feet with a signal strength reported as 30%.

My Starling is stock, with only the published updates and a few other apps installed.

The device that I am using is the Belkin G Wireless USB Network Adapter.  Version 4122.

That's it.  If I were to give up on the internal card for good, I'm sure that there is a way to turn it off in the bios. That would eliminate the second dialog box.  But I am still hoping that S76 will come through on the driver.  The USB device is a little ungainly given the small size of the Starling.

---

### Post by unutbu on 2009-07-19
Belkin wireless adapters usually come with a part or model number like "F5D7050". Could you tell us which particular model you have, jml?

---

### Post by jml on 2009-07-19
Sorry for the omission.  It is model number F5D7050.  Boy, Belkin really does a good job of making the model number hard to read.  I needed a loupe to read it!  Maybe I need stronger bifocals.  :-)

Joe

---

### Post by unutbu on 2009-07-19
Thanks for the info, jml! :)

---

### Post by Talon2 on 2009-07-19
> **mrchuc said:**
> Do I understand that it worked right out of the box. No configuration or installs?

mrchuc,

If you are looking for a readily available usb wifi adapter that "just works" you might look at this one:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833166022](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166022)

I use this cable with it:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812339023](http://www.newegg.com/Product/Product.aspx?Item=N82E16812339023)

This setup works very well for me and is plug and play with Ubuntu since at least v8.04.

---

### Post by mrchuc on 2009-07-20
Hi Everyone,

How is it going on the fix for the wireless driver? Any news yet, Thomas? 

Chuc

---

### Post by thomasaaron on 2009-07-20
Well, I put Karmic Koala on the machine, hoping that it would have the fix. So far, it doesn't. I also tried ndiswrapper on it. That didn't work either. I've handed it off to another tech who has some ideas, and he's going to give it a whirl.

Will follow up again shortly.

---

### Post by cdysthe on 2009-07-20
> **thomasaaron said:**
> Well, I put Karmic Koala on the machine, hoping that it would have the fix. So far, it doesn't. I also tried ndiswrapper on it. That didn't work either. I've handed it off to another tech who has some ideas, and he's going to give it a whirl.

Will follow up again shortly.

Is it possible that this is hardware related? Has anyone tried Windows on the Starling to see if the wireless problems go away? Not that I would ever run Windows, but it's a good way of identifying problems like this one since you then would be running the proprietary driver.

---

### Post by mrchuc on 2009-07-21
> **jml said:**
> That's right, Chuc.  Here are the steps.  
1.  Turned on Starling with the USB wireless adaptor plugged in.
2.  After boot up and log in at the desktop, a dialogue box opens stating that "Authentication required for wireless network." (I use WPA encryption on my network,) clicked on the connect button.  
3.  Wait about 30 seconds, during that time the dialog box pops up again, presumably for the internal card.  I clicked cancel this time.
4.  After about 30 seconds the network manager applet announces that I am connected to my wireless network.
5.  I am now on the net, able to view web pages, watch Youtube videos, check e-mail.


It just happened that I have an Ativa wireless usb plugged into a desktop machine. I tried it on the Starling and it worked. In fact, the Starling reported that it was the same Belkin model you used. 

The signal strength reported was much lower than that reported by the internal card (30% vs. 100%), but the connection seems to be MUCH more reliable. With the internal card I often have to wait and wait for Firefox to connect to a URL. It reports that it is waiting on the site or connecting or loading, but nothing happens for quite a while. With the usb adapter, that has yet to happen to me. Connections are very snappy. 

I have only used it at home. I need to test it at my local diner where I was unable to connect with the Starling. I will go there soon and verify that the internal card won't connect. Then I will try with the usb adapter. If that is the case, I will know I have a usable work-around. 

Maybe that will be useful information for System76 as well.

All the best...

Chuc

---

### Post by jml on 2009-07-21
You are welcome Chuc.  I'm glad it worked for you.  Since we now have two successes using the same chipset on a USB device, Tom may want to make this message thread "sticky" and relabel to something like "Starling Wireless Workaround"  And leave it as a sticky until the driver issue is fixed.  Tom, what do you think?

Joe

---

### Post by mrchuc on 2009-07-22
Hi Everyone,

I took my Starling to the local diner. It is located beside a Panera Bread Company which has wi-fi. I often connect to the Panera wi-fi while I have breakfast at their competition. :)

The Starling has never been able to connect there, but my iPod Touch, Dell Latitude, and Powerbook all connect without problem. I thought this would be a good test of the usb adapter.

First I tried to connect with the internal card. No joy. The little comet went round and round for quite some time and finally the Starling gave up and reported no connection.

I rebooted with the usb adapter (an Ativa that the Starling identifies as a Belkin of the same model that started this thread). The connection was immediate and solid. No problems at all. The reported strength was only 25%, but the surfing was snappy.

I rebooted without the adapter and confirmed that the internal card would still not connect. On a whim, I plugged in the usb adapter without rebooting and found that I could then choose the Panera network and connect.

So, until we get a permanent fix, I will keep my usb adapter handy and plug it in whenever I need the extra range. I don't like it sticking out the side, but it is better than not being able to connect. 

Hope this is helpful.

All the best...

Chuc

---

### Post by kingnerd on 2009-07-22
We really need a status on the fix.  I'm going away soon and this is almost an emergency issue for me.  I wouldn't want to have to return my Starling before I leave.

---

### Post by jml on 2009-07-22
kingnerd, it all depends on how much you like the Starling overall.  I really like the build quality and system speed of the Starling.  So, I am willing to invest in a stop gap measure, realizing it may turn out to be a permanent solution, if the driver issue is not resolved.  Here is the USB dongle I am using right now:

[http://www.amazon.com/Belkin-Wireless-USB-Network-Adapter/dp/B0006374PK/ref=sr_1_1?ie=UTF8&s=electronics&qid=1248318583&sr=1-1](http://www.amazon.com/Belkin-Wireless-USB-Network-Adapter/dp/B0006374PK/ref=sr_1_1?ie=UTF8&s=electronics&qid=1248318583&sr=1-1)

Now, its not an elegant solution.  I hate having a "dongle" sticking out of the side of my netbook.  But it's small, relatively inexpensive,and it works well for me.  I'm willing to put up with it in exchange for being able to buy a netbook with a large hard drive without having to pay for Windows XP ,(like I did when I bought my ASUS 900HA.)

I assume that the fact that we have not heard anything suggests that the problem is turning out to be harder to solve than originally anticipated.  Only time will tell.

Joe

---

### Post by thomasaaron on 2009-07-23
It looks like we *may* have a fix in Karmic Koala...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/293946](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/293946)

...and I will be testing this today/tomorrow.

---

### Post by rrenomeron on 2009-07-24
So will this potential fix be something that's rolled into the System76 driver, or will we have to wait until Karmic is released to have a usable wireless on the Starling?

---

### Post by thomasaaron on 2009-07-24
If we can get it to work (still working on it) we will either roll it into the driver or get on the horn with Canonical and have it added to Ubuntu now.

---

### Post by gamerchick02 on 2009-07-24
Very cool.

This will help me use my starling all over the house, and take it other places.

I'm looking forward to taking it to the coffee shop and getting looks about it.  :)

Amy

---

### Post by mrchuc on 2009-07-28
Any news yet? 

Chuc

---

### Post by val67 on 2009-07-28
I just hope this issue will not have the same fate as the suspend/resume issue with daru2, which was never resolved by s76 in what, 2 years?

---

### Post by cdysthe on 2009-07-28
> **val67 said:**
> I just hope this issue will not have the same fate as the suspend/resume issue with daru2, which was never resolved by s76 in what, 2 years?

What I wonder about is how they (system76) pick their hardware. I mean, they can pick and choose from any of the white label pc-makers out there. Why not making sure the models they choose have linux proven components? I recently was in the market for a laptop. I went on-line and looked up a few good offers. Then I made a list of Linux proven components like nVidia graphics, Intel wireless and so on. I then matched my list with the offers I had found and purchased. I ended up with a laptop which it took me 30 minutes to get up on Ubuntu after I got it out of the box. Absolutely everything on it just works. It's like the thing was designed for Linux! How could system76 pick a model with obvious hurdles like the wireless is on the Starling? It just baffles me.

---

### Post by thomasaaron on 2009-07-29
Well, the area where we test our machines is fairly small, so the wireless actually works quite well in our shop. Even if we walk down the hall to the water fountain it works. 

So, for what it's worth, it slipped under the radar of our typical testing procedures. We've definitely learned a lesson from it, though.

I don't think this will go the way of the DarU2 power management issue. The wireless drive for the Starling has already seen significant improvement since Intrepid, and it's being actively worked on.

---

### Post by axel_2078 on 2009-07-30
I'm glad I came across this thread because I was contemplating ordering one of these. Having quasi-functional wireless is not acceptable to me, especially for a netbook. I won't be ordering one of these until the problem is resolved.

---

### Post by cdysthe on 2009-07-30
> **axel_2078 said:**
> I'm glad I came across this thread because I was contemplating ordering one of these. Having quasi-functional wireless is not acceptable to me, especially for a netbook. I won't be ordering one of these until the problem is resolved.

It's a great netbook at a good price. The screen is awesome and it runs Ubuntu very well. If/when this isssue is sorted out I will be the first to put the Starling on my shortlist.

---

### Post by jml on 2009-07-30
I agree with cdysthe,  I have owned several netbooks over the past two years starting with the ASUS 701.  The Starling has the best hardware and screen of any I owned.  The battery life is very good.  And though I bought my Starling before the wireless issue was known, I am glad I have it.  I am content using my Belkin USB wireless adapter until the driver issue is fixed.  I also like being able to buy hardware without the M$ tax.  Just my two cents.

Joe

---

### Post by paulbary on 2009-07-30
I've been traveling with my Starling for 2 weeks now and have seen two problem areas with wireless ... first is the inability to connect to
some wireless networks that other laptops in the room have no problem connecting to ... the second is  intermittent loss of internet connectivity after a period of use even though network manager indicates a
strong signal ... when this latter scenario happens I have found that if I disconnect from AC and remove the battery, when the unit is re-powered, everything seems to work fine ... just an observation for what it's worth. I'll likely try the Belkin USB card when I return or try loading XP, (yech) ...

Paul

---

### Post by weverjames on 2009-07-31
so you are happy buying a lemon if it does not come from Microsoft???
Any product that is sold advertising certain qualities or properties and fails to deliver them, is a lemon.... Can yo imaging the aggravating situation for somebody that trusted the product would work as advertised and instead have an expensive useless piece of hardware? How you ask somebody that just gave away big cash that he has to spend even more buying other hardware that he was not planning and for what he did not have saved money? Let me remember you, not everybody is rich....
Why continue selling a product when you know it does not deliver th advertised services? You don't buy a netbook to see how good the hardware looks or feel...you buy it looking for mobility!!! 
This is as indignant by these practices as the monopoly of MS....
People here buy pcs/laptops thinking that everything would work...thereafter they find their wireless will not connect, if it connects it will keep dropping, if it connects it will do so sitting 3 meters from the access point, the bluetooth won't work but they bough that option in their pcs, the fingerprinter won't work, but they saw the pc included a fingerprinter reader.
At the end the answer you get is: all OS have problems and linux will always have some....wireless is not a strong point in linux and so on....
Let know potential customers about this potential limitations. We need to be more honest and serious with customers so that they do informed decisions!!!!
At least cigarettes are advertised with a warning....thanks god.

---

### Post by travisoglesby on 2009-07-31
clearly you have mistaken this forum for a blog we didnt come here to complain about problems we came here to try to get answers about our problem and i dont think lumping every single operating system in the world together and saying they all suck really helps anything.....pleases migrate your comments to another post where im sure it will be warmly greeted

---

### Post by rrenomeron on 2009-08-01
So ... status on a fix for this issue?

---

### Post by paulbary on 2009-08-02
I bought the Belkin usb stick mentioned in this thread and it seems to work fine ... I resolved the dual wifi nic issue by adding the following lines to /etc/modprobe.d/blacklist.conf ....

# disable builtin wifi in favor of the belkin usb nic
blacklist rtl8187

This keeps the builtin wifi driver from loading and allows the belkin stick to be singularly detected and the appropriate driver loaded ....

Whatever ... works for me ...

P.

---

### Post by jml on 2009-08-03
Thanks for the information, Paul.  I may give it a try.

Joe

---

### Post by paulbary on 2009-08-03
Hmmm ... seems like using the belkin stick causes problems with suspend ... don't know if it is pervasive or caused by my blacklisting the rtl8187. I'll mess with it and post the results ...

Paul

---

### Post by cdysthe on 2009-08-03
Hi,

I saw something looking like a mini-pci compartment on the Starling (bottom cover). Does anyone know if it is? If so, a mini-pci wireless card could possibly be added that way. I have replaced mini-pci wireless cards on many laptops, so I know it can be done.

---

### Post by thomasaaron on 2009-08-03
It's for 3G wireless. Doesn't work with a wireless card. We already tried that.

---

### Post by showgun22 on 2009-08-03
The weak wireless issue and stability is not only with the starling I have the GU and it is far from being as good as my  old 3 + years old Dell.
It is also not stable and there is connectivity loss.

---

### Post by cdysthe on 2009-08-03
> **showgun22 said:**
> The weak wireless issue and stability is not only with the starling I have the GU and it is far from being as good as my  old 3 + years old Dell.
It is also not stable and there is connectivity loss.


Does the GU have Realtek wireless as well?

---

### Post by showgun22 on 2009-08-04
here it is

02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

### Post by cdysthe on 2009-08-04
> **showgun22 said:**
> here it is

02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02) 

I have the Intel 5100 on both my laptops (Samsung and ASUS), both running Mint 7 (built on Ubuntu) and wireless works flawlessly on both.

---

### Post by thomasaaron on 2009-08-04
The problem is definitely the realtek wireless driver. Only the Starling has that.

---

### Post by cdysthe on 2009-08-04
> **thomasaaron said:**
> The problem is definitely the realtek wireless driver. Only the Starling has that.

Showgun22 says he has problems with the GU also which has an Intel wireless interface.

---

### Post by thomasaaron on 2009-08-04
Right, but I don't think it's the same problem. The Starling problem is now well-known and duplicable.

Not so on Gazelles.

---

### Post by showgun22 on 2009-08-04
Just to make sure we understand my wireless connection is not half as bad as what seem to be explain for the Starling.
What I am saying in my original post is when compare to my old Dell laptop the wireless is not as good and there are big drops as well as loss of connection at times.

I had problems connecting this summer to many hotels and so on so I decided to test it side by side with my 3+ years old Dell and it does not compare to my old Dell.

---

### Post by jbelmonte on 2009-08-04
What wireless controller does your old Dell have?

---

### Post by showgun22 on 2009-08-04
My old XPS has
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

I would have at least hope for my Traveling GU to be as good if not better.

---

### Post by thomasaaron on 2009-08-04
Your Gazelle has a wireless adapter that is soft of a descendant of the Intel 3945. One of the big differences is that your Gazelle's card can handle the "N" protocol, whereas the 3945 can't.

You may want to experiment with some settings in your router. What router are you using?

---

### Post by cdysthe on 2009-08-04
> **thomasaaron said:**
> Your Gazelle has a wireless adapter that is soft of a descendant of the Intel 3945. One of the big differences is that your Gazelle's card can handle the "N" protocol, whereas the 3945 can't.

You may want to experiment with some settings in your router. What router are you using?

I had to work a bit on my D-Link DIR-655 router to get it to work well with my intel 5100 interfaces, especially to get good N connections.

---

### Post by thomasaaron on 2009-08-04
Really? What did you have to tweak?

My d-link was a little weird to set up, but it works really well and is seriously fast.

---

### Post by thomasaaron on 2009-08-04
Got ahold of a newer realtek driver. Compiling it on the Starling now. Will report back with results.

---

### Post by thomasaaron on 2009-08-04
BINGO!!!!!

It worked! We just SUBSTANTIALLY increased the range and performance of the Starling wireless card. Fixed the wireless LED too!

Will be putting the fix in the System76 driver and releasing it in the next few days (if not less).

---

### Post by Vrekk on 2009-08-04
> **thomasaaron said:**
> BINGO!!!!!

It worked! We just SUBSTANTIALLY increased the range and performance of the Starling wireless card. Fixed the wireless LED too!

Will be putting the fix in the System76 driver and releasing it in the next few days (if not less).

WAHOO! Great job I will finally be able to give my dad his usb adapter back :D

Btw thanks for adding me to the mailing list about this Tom :popcorn:

---

### Post by travisoglesby on 2009-08-05
yes thank you thomas very much....btw good work on the starling i havent ever used ubuntu but it seams to work perfectly...i hope to learn alot more about it

---

### Post by kingnerd on 2009-08-05
Hey Thomas, will this be available tomorrow before around 3PM EST? I'm leaving on a three-week long trip in which I will have to rely solely on my Starling Wi-Fi to communicate, and I'd love to get this in.  Also, I upgraded to Karmic following one of the links you posted.  Will this work on Karmic also?

---

### Post by thomasaaron on 2009-08-05
We still have a couple more tests on it, but so far everything is looking fine. So, it *should* be released by tomorrow morning, if not sooner.

We are a LONG way from building Karmic support into the System76 driver. That won't happen until closer to October. We're not even testing with Karmic yet.

---

### Post by RichardK on 2009-08-05
Thanks for your work on this Thomas.  Looking forward to trying the new driver. :D

---

### Post by kingnerd on 2009-08-05
> **thomasaaron said:**
> We still have a couple more tests on it, but so far everything is looking fine. So, it *should* be released by tomorrow morning, if not sooner.

We are a LONG way from building Karmic support into the System76 driver. That won't happen until closer to October. We're not even testing with Karmic yet.

God damn it, time to downgrade.  >.<

---

### Post by kingnerd on 2009-08-06
So, I'm leaving in six hours.... What's the word?

---

### Post by thomasaaron on 2009-08-06
The fix has been released. See...
[http://ubuntuforums.org/showthread.php?t=1233219](http://ubuntuforums.org/showthread.php?t=1233219)

If it's not available in your updates, you will need to install and run the System76 Driver. To install it, go to...

[http://planet76.com/repositories](http://planet76.com/repositories)

...and download the latest driver .deb package. The latest driver will always be the second link from the bottom. Save it to your Desktop.
Once it has downloaded, double-click the icon on your desktop and follow the prompts to install it. Once you are finished, it will appear at System > Administration > System76 Driver.

The first time you run the driver after a fresh installation, you will need to click the Restore System tab and the Restore button. This will modify your software sources file so that any future driver updates will be available via Update Manager.

After running the driver the first time, you no longer need to use its restore fucntionality. You can just use the Install Drivers tab and the Install button to install any necessary drivers.

If for some reason you get a GPG Key error when trying to update, open a terminal (Applications > Accessories > Terminal) and run this command to fix it.

wget -q [http://planet76.com/repositories/system76_dev.pub](http://planet76.com/repositories/system76_dev.pub) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by jediborger on 2009-08-07
Still having some issues here. So I updated the driver to the new version and rebooted. No wireless connection at all. So I run ifconfig and find a wlan2 device listed. When I try to bring it up by running `sudo ifconfig wlan2 up` I get the following:
```
SCIOIFFLAGS: Operation Not Permitted
```
Now before the internal RealTek card was wlan0. So what happend here with the driver?

---

### Post by drewbenn on 2009-08-08
> **jediborger said:**
> So I updated the driver to the new version and rebooted.

After you updated to the latest version of the System76 driver, did you go to System | Administration | System76 Driver, go to the Install Drivers tab, and click on the Install button?  If not, do that, then reboot.

---

### Post by rectagonal on 2009-08-08
Mixed results with the update. I got the improved system-76 driver via synaptic. Launched it, ran the install for the new driver and rebooted. NetworkManager did not automatically connect like usual. When I selected it, I saw a LOT of wireless access points from my neighbors. So I am sure the range has improved. However... I can not connect to any network. Network manager "spins" forever when trying to connect and finally bails with a "Disconnected from network" message. I also find myself with the same symptoms when trying to connect via Ethernet directly to my cable modem. Other PCs in my house connect fine. My immediate reaction was to try and run the update again, but I need a net connection to do it.

---

### Post by jediborger on 2009-08-08
Yes, drewbenn, I did run the System76 driver program and ran the install tab. Something else I noticed a file /etc/modprobe.d/rtl8187.conf which had the following:
```
blacklist rtl8187
```
I commented this line out in the file, rebooted and now I have the internal card being correctly recognised as wlan0 and numerous networks showing up under network-manager except I can't connect to them. I am having the same issue as rectagonal but my wired interface still connects fine.

---

### Post by rectagonal on 2009-08-08
My problem persists, even after a complete restore ( as instructed here : [http://knowledge76.com/index.php/Restoring_Your_Netbook](http://knowledge76.com/index.php/Restoring_Your_Netbook) ) . I can connect to networks on the vanilla 9.0.4 ( On incredibly reduced range.. ) but the moment I install the newest System 76 driver and hit "restore" in it. The problem returns.

---

### Post by gamerchick02 on 2009-08-09
I have done a full restore following the instructions [here]("http://knowledge76.com/index.php/Restoring_Your_Netbook").  I have a hidden wireless network (no encryption) and I cannot connect at all.  It doesn't even recognize that there is a network there.  I've ran all of the updates (on wired network) and I still do not even get close to connecting to the network.

I did what jediborger did above and still I get no connection.

I don't even get the "spins" that rectagonal gets.  It automatically tells me that the network is disconnected.

Wired works fine.

What else do I need to do to get this working?  I'm not going to reinstall Crunchbang before I get UNR working.

Amy

---

### Post by showgun22 on 2009-08-09
If I may make a suggestion
un-hide your wireless see if this will help for now.
Make sure your wifi is not turn off?

---

### Post by rectagonal on 2009-08-09
Went back to System76 Driver v2.3.6 and installed the older driver for the time being. This has restored my wireless to its previous working condition, albeit without the new and improved range...

---

### Post by gamerchick02 on 2009-08-09
> **showgun22 said:**
> If I may make a suggestion
un-hide your wireless see if this will help for now.
Make sure your wifi is not turn off?

Make as many suggestions as you want!  I'll give it a go tomorrow or the day after. I'm really tired today. :-P

Thanks for the suggestion.  I appreciate the help.

Amy

---

### Post by showgun22 on 2009-08-09
Sometimes we forget about the little things...
I know I often do...
Ps by turned off I meant disable

Good luck

---

### Post by gamerchick02 on 2009-08-09
I don't think I have it turned off.  I'll take a look tomorrow.

I don't have a problem connecting with my Pangolian.  *shrug*

Thanks!

Amy

---

### Post by thomasaaron on 2009-08-10
gamerchick,

The updated driver is working well. If you go to System > Administration > System76 Driver and click the "About" button, what version of the driver is it showing?

If you connect with a WIRED connection and go to Administration > Updates, click the "Check" button and then apply all updates, it should update your driver.

Then you will have to run your driver (Administration > System76 Driver > Install (tab) > Install (button).

Then REBOOT your computer and your wireless should be fine.

---

### Post by rectagonal on 2009-08-10
> **thomasaaron said:**
> gamerchick,

The updated driver is working well. If you go to System > Administration > System76 Driver and click the "About" button, what version of the driver is it showing?

If you connect with a WIRED connection and go to Administration > Updates, click the "Check" button and then apply all updates, it should update your driver.

Then you will have to run your driver (Administration > System76 Driver > Install (tab) > Install (button).

Then REBOOT your computer and your wireless should be fine.

Thomas,

When I use System76 Driver v2.3.7 on a vanilla Ubuntu Remix 9.04 install, and use the restore function on the restore tab, I loose the ability to connect to any wireless network after rebooting. I can see access points under Network Manager as described in previous posts, but can not connect. Connecting is fine in previous versions of the driver.

---

### Post by thomasaaron on 2009-08-10
Rectagonal,

Your particular situation appears to be an anomaly, as the driver is working for other Starlings across the board. 

I see that you have emailed me, and I'll handle your particular problem via email. Don't worry, we'll get it straightened out.

---

### Post by thomasaaron on 2009-08-10
Rectagonal,

Please verify that you've *completely* updated the system *before* running the Install functionality of the driver. It's important that the driver is run against the most current kernel. (You may have to click the "Check" button in update manager.

---

### Post by bboston7 on 2009-08-10
I seem to have a similar problem.  Before the new driver, I didn't have any problems, but afterwards, I can't see any wireless networks whatsoever and the wireless light on the bottom right of the netbook doesn't turn on.  I have followed the directions exactly, but for clarification, here is exactly what I did.

1.  Installed updates via update manager
2.  Rebooted
3.  Installed System76 driver
4.  Rebooted
5.  No WI-FI
6.  Tried to install system76 driver with Ethernet cable
7.  Rebooted
8.  Still no Wi-Fi

I have tried turning wireless on and off but it doesn't help. Internet through Ethernet works fine and I have tried re-installing the update when my netbook is plugged in via ethernet, but it doesn't seem to fix the problem.

Thanks in advanced for your help.

---

### Post by thomasaaron on 2009-08-10
OK GUYS! I think I've figured out what is going on.

On the front, right leading edge of your Starling, there is a toggle switch. It is spring loaded and always returns to center. Toggle it one time to the right, let it go. Then wait a few seconds.

Does your wireless LED come on?

How about your Internet?

---

### Post by jediborger on 2009-08-10
Rectagonal,

Try the following and see if it helps.
Open up the terminal and type
```
ifconfig -a
```
If you don't see any wlan devices then press Fn+F2 and run the command again until you see a wlan device. Now try the following:
```
sudo ifconfig wlan# up
```
Where # is the number of your device from the first command.
If you get something about Operation not permitted then slide the switch on the front of the starling to the right once and let it slide back, it's spring loaded. Now try running the above command again.

You should now see networks and be able to connect.

---

### Post by bboston7 on 2009-08-10
> **thomasaaron said:**
> OK GUYS! I think I've figured out what is going on.

On the front, right leading edge of your Starling, there is a toggle switch. It is spring loaded and always returns to center. Toggle it one time to the right, let it go. Then wait a few seconds.

Does your wireless LED come on?

How about your Internet?

It works!

And the wireless range is better!

Thanks.

---

### Post by thomasaaron on 2009-08-10
OK, here is the gig.

If (after fully updating your system and running the newest System76 driver) you turn your Starling on, and there is no wireless, do the following...

1. Locate the switch the front, right, leading edge of your machine.
2. Toggle it to the right ONE time (it will come back to center).
3. Reboot your machine.

From that point on, use Fn-F2 to turn your wireless switch on and off (not the switch on the front right edge).

---

### Post by gamerchick02 on 2009-08-11
> **thomasaaron said:**
> gamerchick,

The updated driver is working well. If you go to System > Administration > System76 Driver and click the "About" button, what version of the driver is it showing?

If you connect with a WIRED connection and go to Administration > Updates, click the "Check" button and then apply all updates, it should update your driver.

Then you will have to run your driver (Administration > System76 Driver > Install (tab) > Install (button).

Then REBOOT your computer and your wireless should be fine.

Yeah. I feel like a dumbass. I had the switch thingy off. I'm sorry for my own stupidity. I must have hit the switch when I was moving it around.  *sheepish grin*

Thanks for the help.

Amy

---

### Post by jediborger on 2009-08-22
Thought I would just post an update. While the new driver is a working improvement over not working at all. I hope someone out there is still working on the rtl driver because it is not perfect. I would say after 20-30 minutes the connection loses signal and I have to reconnect. This might just my wireless signal and other interferences but my other laptop works fine under the same conditions. Just a little encouragement to the developers out there. If I knew how to write device drivers I would gladly help out.

---

### Post by jml on 2009-08-22
jediborger, just a thought.  Do you have this problem when you are very close to your access point?  Do you have the same problem with other wireless access points.  The reason I ask, is I have a Linksys wireless router that is a bit shakey.  My Starling has less than perfect performance at home, but when I take it to work, and to coffee shops it works very well.  My larger laptops seem to handle the varying signal strength that the Linksys broadcasts, but the Starling seems to be a bit more finiky.  I will be replacing my wireless AP soon and I hope that it will help. If you have not tested your Starling at other sites, I encourage you to do so.  Hope that this helps.

Joe

---

