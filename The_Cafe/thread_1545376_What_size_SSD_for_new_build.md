---
title: "What size SSD for new build?"
date: 2010-08-03
forum: The Cafe
---

### Post by toyoracer on 2010-08-03
Hello, I am building a new computer that will run Ubuntu. 
GA 790xta ud4
Athlon II x635
XFX Radeon 5770
Mushkin DDR3 1600
Seasonic x650 psu
WD Green 1 & 2 TB for storage
WD Black for working

So I am thinking about SSD for OS maybe try KVM. I use my computer for Cad, Gimp, Blender  NO Gaming.

First would I benefit from SSD and what size would be good? OR would Two SSD's if using KVM ? 

I am very new but would like to learn and explore Linux. I will try to wait till 10.10 releases for a stable start. Kindly inform me, thank you for your time.

---

### Post by cariboo on 2010-08-04
Moved to the cafe.

---

### Post by cascade9 on 2010-08-04
@cariboo907- I dont know why you moved this to the cafe....well, I can sort of see with the description of the "Hardware & Laptops" subforum, but IMO that description creates a conflict with the "Installation & Upgrades" subfoum. 

There really should be a redefinition of the forums here,. but I doubt that is going to happen. 

> **toyoracer said:**
> Hello, I am building a new computer that will run Ubuntu. 
GA 790xta ud4
Athlon II x635
XFX Radeon 5770
Mushkin DDR3 1600
Seasonic x650 psu
WD Green 1 & 2 TB for storage
WD Black for working

So I am thinking about SSD for OS maybe try KVM. I use my computer for Cad, Gimp, Blender  NO Gaming.

First would I benefit from SSD and what size would be good? OR would Two SSD's if using KVM ? 


A SSD should speed up your boot times, and might have a meaningful impact of program loading times, but apart from that you wont get much out of a SSD. They are nice things, but I'm still wary of them- the cheaper versions can be dodgy, the faster less dodgy versions are still very expensive. 

Why a 5770? You would be better off with a lower level ATI card, or an nVidia card if you play a few videos (VDPAU) and spending the saved money on a faster CPU. I dont know how much GIMP or Blender use a GPU though.... 

GA790XTA? Not a bad board, but the newer version (GA-890XA-UD3) is the same price at newegg, has better features than the 790XTA, like USB3.0 and SATAIII. Already some of the faster SSDs can saturate SATAII bandwidth, and over time they are just going to get faster, and cheaper. I'd probably go for a 870, the 790/890 has extra stuff you will never use with linux (stupid cheap hardware RAID controllers, extra PCIe x16 slots for crossfire, etc).  

[http://www.gigabyte-usa.com/Products/Motherboard/Products_Spec.aspx?ProductID=3430](http://www.gigabyte-usa.com/Products/Motherboard/Products_Spec.aspx?ProductID=3430)

[http://www.gigabyte-usa.com/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=3385&ProductName=GA-890XA-UD3](http://www.gigabyte-usa.com/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=3385&ProductName=GA-890XA-UD3)

Be careful with the WD 'green' drives, the newer models (EARS) are a pain to setup with linux....

---

### Post by toyoracer on 2010-08-04
Well thank you cascade9, first off I asked for the move I agree on the confusing sub-forum titles. 
 The hardware listed is already bought so I will live with that and try to make it work in Ubuntu for time being. Just looking for opinions on SSD or Not.

I really like using Ubuntu and have not booted into XP since getting up and running, and do Not want to go back. Live and Learn ;)

---

### Post by handy on 2010-08-04
Fill up the drives you have first, then see how much an SSD drive costs & how their performance/reliability has changed in the meantime.

Don't spend the money on an SSD unless you have made too much money in the current financial year & need to lose some for tax purposes.

& if you do need to lose some, there are much better ways than buying an SSD. :)

---

### Post by papangul on 2010-08-04
There is a seagate hdd with integrated 4gb ssd. It monitors usage patterns and moves the most accessed files to the ssd. 

btw, I'm also upgrading and I have selected the following MSI mobo:
 [http://www.msi.com/index.php?func=proddesc&maincat_no=1&prod_no=2061](http://www.msi.com/index.php?func=proddesc&maincat_no=1&prod_no=2061)

---

### Post by Paqman on 2010-08-04
If you can afford an SSD, definitely get one, they're great. I guarantee you won't look back once you've had one for a while. I/O is a massive bottleneck on systems with magnetic drives, switching to an SSD gets the most out of all your other components.

You could easily get away with a 40GB one if it's just for the OS. Put your storage on a magnetic drive. You can get a 40GB Intel X-25M for about £100, which is well worth it for the performance IMO. If you're multibooting you might want to get an 80GB, which will cost a bit under twice as much.

Don't get a cheap SSD, they're a waste of money.

---

### Post by toyoracer on 2010-08-04
Thanks Paqman, I am wondering about KVM and SSD, would it be a help. I have a P4 now so I have no ability to try any VM. I would like to play around with that on new comp.

---

### Post by snowpine on 2010-08-04
SSD is a fantastic (if expensive) technology.

The Ubuntu operating system requires a bare minimum of about 4gb for a fresh install and 15gb is recommended:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by handy on 2010-08-05
It is really easy to spend money on technology just for technologies' sake. 

Unless someone is doing work where the (inconsequential in most cases) speed increases of upgrading whatever technology pay for themselves {one way or another (big question mark here)}, doing so is just self indulgence.

Such self indulgence is of course the cornerstone of the consumer society that most of us were born into {& therefore know no better (not that ignorance will save us)}. This is also of course how the wheels of consumption are kept incessantly revolving in the ongoing process of devouring the earth's resources.

Sounds heavy doesn't it? 

I must be lying eh?

---

### Post by Warpnow on 2010-08-05
SSDs would definitely be more worth it in a laptop imho. Power saving, don't have to worry about it being dropped or falling and the data being lost. Faster boot times because its portable...

---

### Post by markp1989 on 2010-08-05
i think the best size for ssd is 64gb, i had 32gb, and i filled it, so i moved to 64gb.

the best setup will be 64gb ssd for os + a big hard drive for media storage.

---

### Post by toyoracer on 2010-08-05
> **handy said:**
> It is really easy to spend money on technology just for technologies' sake. 

Unless someone is doing work where the (inconsequential in most cases) speed increases of upgrading whatever technology pay for themselves {one way or another (big question mark here)}, doing so is just self indulgence.

Such self indulgence is of course the cornerstone of the consumer society that most of us were born into {& therefore know no better (not that ignorance will save us)}. This is also of course how the wheels of consumption are kept incessantly revolving in the ongoing process of devouring the earth's resources.

Sounds heavy doesn't it? 

I must be lying eh?

Thanks Handy, Heavy or just reality. I fully agree that is why I am asking. At the same time, IF it will make my programs work faster then it would be worth the cost.

> **markp1989 said:**
> i think the best size for ssd is 64gb, i had 32gb, and i filled it, so i moved to 64gb.

the best setup will be 64gb ssd for os + a big hard drive for media storage.

Thanks markp, I was thinking same size. Anybody with VM knowledge and SSD?

---

### Post by mamamia88 on 2010-08-05
check slickdeals.  you can find some decent prices on ssds.  i personally bought a 30gb one for $55.  didn't work on my laptop so put it in my brothers laptop and ubuntu boots in 5 seconds.  i say if you can find one for under $100 i say go for it the performance difference should definitely be worth it imo.

---

### Post by andrewabc on 2010-08-05
I don't know what you mean by VM thing you are talking about.

Anyways, I have 2 60gb vertex. First one bought for $200 last October and 1 month ago got another for $130.

Got one in main desktop. Works great, and speeds up boot time, and application start time. Firefox is much more responsive with a large profile.

I have the other in an older model nettop that only has SATAI speed. It is faster as well for booting and some app loading. But the nettop is a bit too slow to make up for SSD speed increase.

I would say 60gb models are the least size you should get, unless you just need a 30/40gb model for laptop and only plan on using ubuntu+apps for say web surfing etc, no need for much storage/media. For life expectancy increase and maintain highest speed, I'd only keep around 1/2 full on average. My 60gb desktop SSD only has 10gb used, and usually never more than that. I have 320gb HDD inside desktop for normal data storage, and 1tb external for media storage. SSD+HDD in desktops is best and cheapest option for speed/storage mix.

Hopefully by the end of 2010 once new Intel are out, new Indilinx are out, prices should drop a lot. We've seen 60gb Indilinx last year be ~$230, and so far drop as low as $130. Maybe older Indilinx models at end of year will be very cheap as they get rid of inventory since new SSD models are much faster.

---

### Post by toyoracer on 2010-08-05
[QUOTE=andrewabc;9683338]I don't know what you mean by VM thing you are talking about.

Thanks andrewabc, VM or KVM is for virtual machine I would like to play around with. Total noob on this issue. Thought maybe even two SSD's for running VM set-up just trying to learn about and plan ahead. Very little info on this topic.

---

