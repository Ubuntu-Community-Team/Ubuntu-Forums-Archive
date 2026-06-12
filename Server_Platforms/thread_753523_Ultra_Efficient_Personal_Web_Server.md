---
title: "Ultra Efficient Personal Web Server?"
date: 2008-04-12
forum: Server Platforms
---

### Post by hizaguchi on 2008-04-12
I'm toying with the idea of setting up a community web site for my neighborhood (per a request at a recent meeting).  I looked at some hosting options, but I really like the idea of having everything running on my own equipment so I can tinker with it freely in anyway I want.  The downside there though is that the only machine I have other than my personal laptop is an old Pentium III 733Mhz desktop.  It is loud, runs hot, needs alot of space, and eats up way more electricity than is acceptable for something I'm going to run 24/7.  So my question is, if I just want to run a Drupal-based site and maybe a few email accounts, what is the cheapest, most energy efficient, smallest footprint machine I can get that will meet my needs?

---

### Post by tamoneya on 2008-04-12
well you could get a mcro atx motherboard with a dual core AMD or intel at 1.5 GHz or so.  Then add 2 GB and small harddrive.  It really depends on the size of your neighborhood but that would be about all you need.  I bet you can get it for $500 when you include a case and powersupply as well and since it is micro atx it will be very manageable in terms of size.

---

### Post by Dr Small on 2008-04-12
I would build a new machine and use it as a headless server.
Install Xampp, Postfix, and SSH on it, and buy a domain.

---

### Post by kerry_s on 2008-04-12
check out the dsl store->
[http://damnsmalllinux.org/store/Mini_ITX_Systems](http://damnsmalllinux.org/store/Mini_ITX_Systems)

---

### Post by FakeOutdoorsman on 2008-04-13
I use an old and very small PII 400 MHz, 384 MB RAM for a low volume site that uses an average of 35 watts with a minimal Debian Etch.  It works fine, and I bet you can get something better than that for free via Freecycle or Craigslist.

> **Dr Small said:**
> ... Install Xampp, Postfix, and SSH on it, and buy a domain.

I don't recommend XAMPP for a production server.  Apache is easy enough and I've seen way too many compromised XAMPP servers out there because they didn't read the Security section of the documentation during installation.

---

### Post by jflaker on 2008-04-13
Freecycle is a great option as I have seen in the last 2 months, 3 full systems going up for grabs......stating the system doesn't boot so they replaced it...

Thinking, load up Ubuntu or Xubuntu and you will most likely find that the system is ok, just that Windows had crashed hard!


Place a wanted on freecycle for computers, working or not.....most DO work or just need a Powersupply.

---

### Post by Metro_Dan on 2008-04-13
You can get a mini itx Intel 201GLY2A mobo with a Celeron 220 onboard for $70 from [Newegg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813121334&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-Motherboard+/+CPU+/+VGA+Sets-_-intel-_-13121334") add a gig of ram, a cheap case,  HD and Ubutnu Server 64. Then you have yourself a nice little box that costs under $150 and uses less then 50watts.

---

### Post by volkswagner on 2008-04-13
I agree with the mini ITX solutions.  There are via, amd geode, and the mentioned intel versions.  Check newegg under mobo/cpu/video combos.  There is also this unit under amd mobos.  Probably the most powerful cpu of the bunch.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813153052]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813153052")

If you have not already, verify it is possible to host from your home.  Your ISP may not allow it.  They may block ports, etc. 

Some Ideas here also.

[http://ubuntuforums.org/showthread.php?t=748095]("http://ubuntuforums.org/showthread.php?t=748095")

If the town is gonna pay, and you a volunteering your time, go new.  "There is nothing like new".

---

### Post by hizaguchi on 2008-04-13
Didn't consider my ISP blocking me from hosting a site.  I'll have to check into that.

I'm sure I could get some money to buy the equipment and domain from the HOA, but I've never done a web site before, so I can't guarantee success up front.  I'd hate to take any money and then have my idea bomb.  Plus, this is a spare time project, and footing the bill myself lets me work on my own time frame, without anyone expecting results at a certain point.  All of that has me leaning toward the Freecycle option.

Then again, I have a cable/phone connection hub in my laundry room where the CAT5 cable I'm using for phone and ethernet to all my rooms comes together and hooks into my router (har har!).  So something small and quiet, that I can hang on the wall next to the router, is tempting.  Maybe I should build a mini-itx system.

I'll check with the ISP first though.  Thanks for that info.

---

### Post by saspo on 2008-04-13
You might want to try the new Ebox 4300.  Real nice and will fit on the back of the monitor - VESA  compliant.  Very cool.  No fan noise.
[http://www.wdlsystems.com/ebox/ebox.shtml](http://www.wdlsystems.com/ebox/ebox.shtml)
[http://www.linuxdevices.com/news/NS9820651660.html](http://www.linuxdevices.com/news/NS9820651660.html)
Hope you have fun.

---

### Post by Dr Small on 2008-04-14
> **FakeOutdoorsman said:**
> I use an old and very small PII 400 MHz, 384 MB RAM for a low volume site that uses an average of 35 watts with a minimal Debian Etch.  It works fine, and I bet you can get something better than that for free via Freecycle or Craigslist.



I don't recommend XAMPP for a production server.  Apache is easy enough and I've seen way too many compromised XAMPP servers out there because they didn't read the Security section of the documentation during installation.
That simply requires running:
```
sudo /opt/lampp/lampp security
```

And choosing most of the defaults, sets it up pretty secure.
But just because user's fail to tighten security on it after installation is no excuse to say it is a bad application. But whatever floats your boat...

Dr Small

---

### Post by refdoc on 2008-04-14
I am using a Buffalo Linkstation to do a large part of what you are planning to (reflashed to Debian)

It is quiet, cheap to buy and does not eat much energy.

I used in the past a 486 with 24Mb as a webserver ruinning from my ADSL. It was mostly static HTML: pages with a bit of PHP

I doubt that you will have many vieweres competing for ressources

So i think the Linkstation's specs should be sufficient.

ARM9,266 MHz,  128MB Ram

---

### Post by Luke has no name on 2008-04-14
Why hasn't anyone discussed using the LAMP server from Ubuntu Server 7.10? I would think that would be the better option than XAMPP.

---

### Post by kerry_s on 2008-04-14
> **Luke has no name said:**
> Why hasn't anyone discussed using the LAMP server from Ubuntu Server 7.10? I would think that would be the better option than XAMPP.

cause ubuntu's not a good server, upgrades are risky. better to use debian. no problem running lamp on debian though. also the op is looking at the hardware end, not software.

---

### Post by hizaguchi on 2008-04-14
> **saspo said:**
> You might want to try the new Ebox 4300.  Real nice and will fit on the back of the monitor - VESA  compliant.  Very cool.  No fan noise.
[http://www.wdlsystems.com/ebox/ebox.shtml](http://www.wdlsystems.com/ebox/ebox.shtml)
[http://www.linuxdevices.com/news/NS9820651660.html](http://www.linuxdevices.com/news/NS9820651660.html)
Hope you have fun.

Nice.  I followed the link to the Ebox 2300 from there too, which is like $100 for a 300MHz "486-class" or slightly more for a 200MHz "Vortex86".  What's the difference?  My first computer was a 486 with Dos.  That's not what I'm getting with the 300Mhz one is it? :)

Then next step up from there looks like the Buffalo Linkstation EZ for right under $200 but with a sizable HD.  Then Ebox 4300 and 3800 for a little over $200.

Then there's this Zonbu/Ebox 4800 for around $300 buch still beefier.

So now I'm in a new kind of dilema.  These and all sorts of other little Linux boxes seem to run a whole range of speeds and prices.  Obviously, I want to get out as cheap as possible, but I wonder if there's more I'll want to do with my little setup down the road that the cheaper machines can't handle.

Can anybody give me some rough guidelines for what kind of power a server needs to host a website, possibly with forums, and an email server?  Then on top of that, what other really cool stuff I should consider when buying, and what kind of power do I need for that?

Thanks alot for all the guidance so far, by the way.  :)

---

