---
title: "More Ram"
date: 2007-06-27
forum: System76 Support
---

### Post by Rowan187 on 2007-06-27
Ok, I have the System 76 Pangolin Value.

When building the laptop i noticed it supported 2 GB Ram (2 1GB Sticks)

at the time of purchase I could only afford 1GB, 1 Stick.

I get a paycheck on the 30th and noticed i still have that extra slot empty.. so my question is.. will System76 let me buy any type of RAM and it will be supported, or should I buy the same stuff they use? I noticed RAM has gotten really cheap this past year and am looking at stuff like this

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231066](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231066)

Is this one or any other one related to it supported by the Pangolin?

---

### Post by moore.bryan on 2007-06-27
[I]no need to go with the one from system 76, just make sure you're looking for DDR 667mhz memory.
[tigerdirect]("http://www.tigerdirect.com/") also has some ([http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2217057&CatId=1726](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2217057&CatId=1726))
[/I]

---

### Post by thomasaaron on 2007-06-27
We don't sell the RAM separately.

But if you go to the customize page, you will see what we recommend for your computer.
We use Kingston RAM, so I'd recommend you stick with that.

---

### Post by jml on 2007-06-28
Adding ram to your laptop should be pretty easy.  Bumping up the ram can really improve the performance of your computer.  Once you determine precisely what type of RAM to buy, you can buy it from a number of sources.  Most RAM is manufactured by a small number of Pacific Rim companies, and then labled by the company you purchase it from.  Just be sure to buy from a reputable company that has a good return policy if you need it.  Kingston RAM has a good reputation for reliabilty and quality, so if its reasonably priced, I would go for it.  Just my two cents worth.

Joe

---

### Post by Rowan187 on 2007-06-28
> **thomasaaron said:**
> We don't sell the RAM separately.

But if you go to the customize page, you will see what we recommend for your computer.
We use Kingston RAM, so I'd recommend you stick with that.

Thank a bunch guys, all your information helped out, I'll definately stick with Kingston, I found one with nice reviews here
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820134129](http://www.newegg.com/Product/Product.aspx?Item=N82E16820134129)
and it's in my budget

On a side-note Thomasaaron, I just thought I'd tell you that Windows XP and Windows Vista both run great on a Pangolin Value even with only 1gb ram (and the Core 2 Duo T5500 1.66GHz 2MB 667FSB).. Just thought I'd tell you that in case anyone ever asks if XP or Vista will dual-boot good...
Although I wouldn't recommend anyone go to Vista, stick with Ubuntu, it's simply the best!

Thanks again for your help, I'm going to buy the ram on saturday when I get my paycheck!

---

### Post by thomasaaron on 2007-06-29
Thanks for the info.

Is there a particular tutorial you used to dual-boot Vista?
I've read that there are some quirks, and I've not had the chance, (or desire [-( ) to give it a try.

Best,
Tom

---

### Post by Rowan187 on 2007-06-30
> **thomasaaron said:**
> Thanks for the info.

Is there a particular tutorial you used to dual-boot Vista?
I've read that there are some quirks, and I've not had the chance, (or desire [-( ) to give it a try.

Best,
Tom

Well, Here's the situation. I installed Vista completely over Ubuntu, so my Hard Drive only had one partition, and that was an NTFS partition with Vista. Then I tried to reinstall ubuntu again, but Vista wouldn't allow it for some reason, It just pretty much corrupted everything. So I formatted again and put in a Gparted Live cd, I made two empty partitions, an NTFS and an EXT3. Then installed Vista.

After vista was installed I installed Ubuntu, I went into manual partiton and made a 2GB swap file (double my current RAM). Then Ubuntu installed correctly.

So basically you have to setup the hard drive in preparation for both beforehand, and install Vista first, because if you install Ubuntu first, Vista won't accept the other partition, it makes sure it is first, as in dev/hda1 or sda1.

This was kind of unorganized but if you don't understand I can do a step by step, this is how i did it atleast, i'm sure there's a much simpler way.

---

### Post by joe.turion64x2 on 2007-06-30
> **Rowan187 said:**
> Well, Here's the situation. I installed Vista completely over Ubuntu, so my Hard Drive only had one partition, and that was an NTFS partition with Vista. Then I tried to reinstall ubuntu again, but Vista wouldn't allow it for some reason, It just pretty much corrupted everything. So I formatted again and put in a Gparted Live cd, I made two empty partitions, an NTFS and an EXT3. Then installed Vista.

After vista was installed I installed Ubuntu, I went into manual partiton and made a 2GB swap file (double my current RAM). Then Ubuntu installed correctly.

So basically you have to setup the hard drive in preparation for both beforehand, and install Vista first, because if you install Ubuntu first, Vista won't accept the other partition, it makes sure it is first, as in dev/hda1 or sda1.

This was kind of unorganized but if you don't understand I can do a step by step, this is how i did it atleast, i'm sure there's a much simpler way.
I think you could have saved some time by using the 'shrink partition' option of Windows Vista.

---

### Post by thomasaaron on 2007-07-02
Rowan187,

I would like to have a "Dual Booting Vista" tutorial on our wiki (knowledge76.com).
If you've got it all figured out and can spare the time, I'd love to have some instructions.

If you want to email them to me, I'll edit and post them. (Heck, I'll even give you a byline!).

Best,
Tom

---

### Post by Rowan187 on 2007-07-06
> **thomasaaron said:**
> Rowan187,

I would like to have a "Dual Booting Vista" tutorial on our wiki (knowledge76.com).
If you've got it all figured out and can spare the time, I'd love to have some instructions.

If you want to email them to me, I'll edit and post them. (Heck, I'll even give you a byline!).

Best,
Tom

Hmm, Yes in fact, after I get my 2GB RAM I decided to just reinstall everything again so i'll write down all my steps from there, ill even try a few things to see if i can get there faster, but I've definitely tried and the best way is to set up the hard drive beforehand, but ill try an ubuntu-first installation, because that would be the most common scenario.

by the way, that wiki really needs to be updated, so much obsolete information/news :P

---

### Post by thomasaaron on 2007-07-06
Yes, the Ubuntu-first scenario would be optimum for the wiki, as many customers buy our systems because they don't want to install it themselves.  Let me know what you find.

After the new product releases in mid- to late-July (and our new *awesome* website) the wiki will become a priority. Right now, we're doing too much development work to focus on it. But, you're right...

Best,
Tom

---

