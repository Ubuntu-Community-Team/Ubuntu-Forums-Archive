---
title: "Good Travel Computer"
date: 2016-01-21
forum: The Cafe
---

### Post by branau on 2016-01-21
I do a lot of travelling. In fact, I don't really have a home, because I move around so much. I'm looking for a decent computer that would be suitable for doing web development, but that is also light and easy to transport. I currently have a 15.6 in MSI gaming laptop that I run Ubuntu 14.04 on, but it's a little big and a little heavier than I'd like. I was considering getting a Chromebook, but they seem too limited for what I need. Some common technologies I work with are:


[LIST]
[*]PHP (Laravel, CLI, WordPress, Magento, Cake)
[*]JavaScript (Node, Angular, jQuery)
[*]Python
[*]Ruby
[*]git
[*]SSH
[*]FTP
[/LIST]

I'm also transitioning into more DevOps type work, so I'll need to be able to run Docker, and work with Puppet and Chef.

From what I've seen, Chromebooks can be "hacked" to boot Ubuntu alongside them, and even have Ubuntu replace ChromeOS, but I'm wondering if it's worth the trouble, or if I should just grab a small Windows laptop and upgrade the RAM and hard drive. I'm looking for at least 4GB of RAM, and a SSD because speed is important to me. I'm also hoping to keep the total under $300, if possible. Something like [this]("http://www.amazon.com/gp/product/B0197WF5BA?psc=1&redirect=true&ref_=ox_sc_sfl_title_1&smid=ARKFFGMZRYG2X") looks promising, but I'm not sure. I was also considering buying a used laptop and switching out the hard drive and RAM. Smaller 11.6" laptops run for around $150 used on eBay, and for another $100 or so I could upgrade it to be capable of what I need. Any suggestions on particular makes/models? Anyone have experience doing web development on a Chromebook?

---

### Post by khelben1979 on 2016-01-22
I would say that the computer you linked to there seems like a decent choice considering the price tag. It will also work good with Ubuntu, that's for certain. Personally I'm much more for other brands such as HP, but the prices are higher. Be prepared that you might haveto scrap the Windows signatures from BIOS to be able do the Linux install, you loose the Windows licence, but that's the way some of the vendors have chosen to do it, like HP for instance. I'm not sure about Lenovo, but could be the same thing with that.

---

### Post by branau on 2016-01-22
> **khelben1979 said:**
> Be prepared that you might haveto scrap the Windows signatures from BIOS to be able do the Linux install

Is this something new with Windows 10? I'm not too concerned with losing the Windows license because I don't have any need for it, and I have a spare Windows 10 Activation Key lying around in case I change my mind, but would a complete hard drive wipe not suffice?

---

### Post by 1clue on 2016-01-22
First thing, I'd like to point out that EVERY time I've bought a cheap computer in order to make money with it I regretted it.  My definition of cheap has changed over the years, but I've learned that you get what you pay for.  If your income depends on this thing working well, then get something that will work well.  The last time I bought a computer in the price range of what you linked to, I literally gave it away it was so useless.

Second thing, I'd recommend that you buy a second ssd or hard drive, pull the original out and install Ubuntu on the new one.  That way you have a completely pristine original drive that you can revert to when you want to sell the box.

I've never heard of this Windows signatures thing, if you can find a way to back that up I'd store it with your Windows drive.

---

### Post by pauljw on 2016-01-22
I bought one of the these for my daughter, although hers has a hdd instead of an ssd.  It seems to be a very nice machine and she loves it.  Ubuntu 14.04 LTS runs just fine on it.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16834299726](http://www.newegg.com/Product/Product.aspx?Item=N82E16834299726)

---

### Post by kurt18947 on 2016-01-23
Thinkpads have worked very well with Ubuntu historically. I'd be a little concerned with the one you linked to in that an A4 processor might be limiting for processsor intensive work. My wife's desktop is an A6 and it works very well but she just uses it for web browsing and basic office tasks, nothing demanding. I haven't used an A4 machine, it may be perfectly adequate for your purposes but if this is a work machine you would want enough power. An SSD is certainly the way to go if you want responsiveness in a portable machine. I have an Ebay refurb Thinkpad X201 Core i5 upgraded with a 256 GB OCZ Vector 180. PC & SSD together were < $200 U.S. Very portable and responsive.

Edit: A Thinkpad without trackpoint? HERESY!!! :D  I prefer Thinkpads for 2 reasons. One is *buntu compatibility, the other is the Ultranav trackpoint/touchpad. I've never used a touchpad only machine where I didn't soon connect a mouse.

---

### Post by khelben1979 on 2016-01-23
> **branau said:**
> Is this something new with Windows 10? I'm not too concerned with losing the Windows license because I don't have any need for it, and I have a spare Windows 10 Activation Key lying around in case I change my mind, but would a complete hard drive wipe not suffice?

No, it's one the features which came along as they released Windows 8. I got a so called OEM license with my new laptop, but even if I replaced the hard disc, the license of Windows 8 will still be invalid, since it does look up the valid Windows signature file which is stored in the computer BIOS. There is no way to be able to run Windows 8 on it again, unless purchasing a new full license of Windows. I tried to install linux myself, but the installer didn't allow me to install anything, it was all buggy and no options worked. So once the signatures were erased, the install went through without any problems! This was a Debian install, but the same thing goes for Ubuntu.

It's up to the Vendors if they decide to ship computers with Windows 8 or 10. There's a few vendors where you can skip that as an alternative, but very few offers this.

---

### Post by branau on 2016-01-23
Thank you all for your input. Based on your combined advice, I think I found a winning combination:

[Lenovo Thinkpad X220]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834319687&cm_re=lenovo_thinkpad_x220-_-34-319-687-_-Product") - It's a refurbished model, but I'm not too concerned with that. I've had good experiences with Newegg in the past and they have a pretty good warranty/return policy. This particular computer looks to have good base specs and is upgradeable, so I could always add on. And at 12", it should be fairly easy to lug around with me wherever I go. $240 to start

[240 GB SSD]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820156066") I don't need a ton of space, as I don't work much with media files, just a bunch of code. Everything I do is on git anyways, so if I find that I don't have enough space, I can always delete some of the repositories that I don't use very often from my local machine. I'd need to check to make sure this particular SSD would fit/be compatible with the laptop but I think anything I find will be around the same price range of ~$65, which brings my total to $305. I never use windows, so I could just leave the hard drive alone and stick it back in when I'm ready to sell this computer.

Finally, [8 GB RAM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820191523") Again, I'd need to confirm that this particular set of memory would be compatible with the machine, but I'd say ~$40 would be reasonable, which brings my total up to $345, and that's not unreasonable for me. 8GB should be more than enough, as at most I have a few tabs open, a terminal, a text editor, and possibly a Node/Rails/Laravel development server running. Running a lightweight DE should provide me with adequate speeds and prevent me from hitting swap space too often. 

Thoughts/opinions on this build for a budget?

---

### Post by Christopher_Stayne on 2016-01-23
I use a Dell Latitude E4310 that runs Kubuntu 15.10 rather excellently.  Its 13.3" and is lightweight thanks to its aluminum and megnesium-alloy casing.  Most come with a 1st gen Core i5 that runs at up to 3.06 Ghz and 4GB RAM.  They are easily upgradeable to 8GB RAM which is what I have done and threw a 180GB Intel 330 SSD in it.  Extemely responsive and stable.  Love it.  These laptops can be bought for between $150-$200 on eBay and can be upgraded to the state mine is in for another $100 (give or take.)  Im very happy with it.

---

### Post by 1clue on 2016-01-23
I just upgraded my dev box from 12g to 24g RAM. I use a couple vms for testing so that makes a difference. If you don't positively know 8g is enough for your dev box I would try to find something that can be expanded.

---

### Post by branau on 2016-01-24
> **Christopher_Stayne said:**
> I use a Dell Latitude E4310 that runs Kubuntu 15.10 rather excellently.

I'll have to check those out too, thanks!

> **1clue said:**
> I just upgraded my dev box from 12g to 24g RAM. I use a couple vms for testing so that makes a difference. If you don't positively know 8g is enough for your dev box I would try to find something that can be expanded.

I'm quite certain 8GB would be enough, and if not then I could shoot for 16GB. The ThinkPad I linked to can unofficially support up to 16GB but officially 8GB. I'd be amazed if 8 weren't enough for my use though

---

### Post by Sandy_Cal on 2016-01-26
Hi, for a travel computer I'll go for a Dell or a Macbook laptop for me. However, in picking a good one you should also consider the usage.

---

### Post by fkkroundabout on 2016-01-31
mmm personally i would absolutely go with a thinkpad.

i had heard alot about thinkpads and their linux compatibility, and for the first time yesterday i used a friend's - and installed ubuntu on it - and was surprised by how fast and smooth it was as it was just an X200, but also because of the zero friction when installing ubuntu on it as everything worked straight away. after the headaches of past experiences of installing linux on the myriad of hardware in the wild, i would absolutely save the trouble if i need a laptop and just buy a thinkpad. even saw some i5 thinkpads for $140 when i checked briefly, today

unless you want OSX then you'll have to get a macbook, as there is no laptop equivalent to the feasibility of the desktop hackintosh world. and you'd definitely get less processor power for your money as macs retain their value for quite a while

---

### Post by speedwell68 on 2016-02-01
A Chromebook.  I can do most stuff with ours.  If not just dual boot Ubuntu.

---

### Post by branau on 2016-02-05
Yeah, I'm not a huge fan of OSX or anything Apple for that matter. Too much propietary BS for me. I like my devices to work well together without having to buy them all from the same vendor. I originally got into Linux because I started learning programming, and had read that Linux and Macs were THE operating systems to use for it. Since I didn't have the money at the time for a Mac, I went with Linux and when I finally had the money for a Mac, I didn't like it so I installed Xubuntu on it haha. 

 I've been doing a lot of research and looking at these particular brands that you all have recommended, and I've found some solid options that are cheap too. I think my final choice is going to be this [laptop]("http://www.newegg.com/Product/Product.aspx?Item=9SIA6AB3GX9464") from Dell. It's a little over my preferred limit of $300 but not by much, so it shouldn't be a big deal. The specs look good on it too, so I should be able to work just fine with it.

---

