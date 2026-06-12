---
title: "What is considered to be the most Ubuntu/Linux friendly wifi card for laptops?"
date: 2007-04-22
forum: The Cafe
---

### Post by PartisanEntity on 2007-04-22
Just wonder, what is considered to be the most Ubuntu/Linux friendly wifi card for laptops?

Is there any official statement on this or is this based on user feedback?

Thanks

---

### Post by visik7 on 2007-04-22
based on my experience:
1.  prism54
2. atheros
3. all intel cards ipw
4.all the rest
5.broadcom

---

### Post by Slackpacker on 2007-04-22
Well, there's[ this list]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported").  I just wish it was sortable.  That appears to be the closest thing there is to an official compatibility list.

---

### Post by Ender Black on 2007-04-22
Quit slacking slackpacker and edit your hyperlink adding the necessary "h" in the front of https://

lol

---

### Post by aysiu on 2007-04-22
Intel Pro Wireless 2200 works for me.

---

### Post by PatrickMay16 on 2007-04-22
Ralink are friendly with linux.

---

### Post by TheMono on 2007-04-22
Ralink are actually the best for compatibility as far as releasing the specs, etc. You don't need the binary blobs for Ralink... 

Having said that, for some stupid reason the drivers are still imperfect, and they don't work nice with Network Manager.

---

### Post by jiminycricket on 2007-04-22
> **TheMono said:**
> Ralink are actually the best for compatibility as far as releasing the specs, etc. You don't need the binary blobs for Ralink... 

Having said that, for some stupid reason the drivers are still imperfect, and they don't work nice with Network Manager.

There are new drivers that support the extensions needed by network-manager in development.  I guess if one was desperate they could compile those from their site.

but yes Ralink are  basically the free-est wireless cards for Linux and highly recommended, but with network-manager there's a bit of trouble there.   However, just uninstall it and use wicd or wifiradar instead.

My Intel 2200b/g also worked great, so look for laptops with the word CENTRINO.

---

### Post by racoq on 2007-04-22
For me the best supported chipset is atheros by a far distance. The madwifi project does a great job creating drivers for this wireless chipset, and they are easy to compile / install

---

### Post by troymcdavis on 2007-04-22
Free Software Foundation, FTW:

[FSF >> Resources >> Hardware Database >> Networking >> Wireless >> Cards]("http://www.fsf.org/resources/hw/net/wireless/cards.html")

---

### Post by prizrak on 2007-04-22
Intel is best as they provide FLOSS drivers. Atheros works pretty well but requires non free firmware so might not be in some distro's. Orinoco seems to work well in just about any Linux.

---

### Post by PartisanEntity on 2007-04-23
Thanks for all the feedback. I would like to replace the broadcom wifi card in my laptop because having to constantly fiddle with it is starting to get on my nerves.

---

### Post by xyz on 2007-04-23
> **visik7 said:**
> based on my experience:
1.  prism54
2. atheros
3. all intel cards ipw
4.all the rest
5.broadcom
Hi,
I read this [HERE]("http://www.fsf.org/resources/hw/net/wireless/cards.html"):
> Atheros

These cards are not supported. The 'madwifi' driver, which is free, is not by itself sufficient to run these cards.

Did you really get it to work? I've been trying on a friend's box but no luck so far.

---

### Post by PartisanEntity on 2007-04-23
> **xyz said:**
> Did you really get it to work? I've been trying on a friend's box but no luck so far.

The Atheros worked out of the box in Dapper on a friends laptop. Didn't work in Edgy, and I have yet to try it in Feisty.

---

### Post by TheMono on 2007-04-23
To elaborate on that quote from the FSF about Atheros, what they mean is the madwifi driver, which is open source, is not enough to run the card by itself. It needs a binary blob which is not open source. That binary blob IS provided in the Linux-restricted-modules package for Ubuntu, so the cards do normally work perfectly

That is the difference with the RaLink ones though, they do not require a binary blob and are totally open.

And prizrak, are you sure about the Intel ones being completely open? I know that Intel provide drivers, but they also contain a binary section as far as I am aware. But the point still stands that Intel cards normally work well.

---

### Post by PartisanEntity on 2007-04-23
I am thinking of getting the Intel PRO/Wireless 2915ABG card for my Asus laptop.

Anyone here familiar with it? Experiences?

---

### Post by racoq on 2007-04-23
> **PartisanEntity said:**
> I am thinking of getting the Intel PRO/Wireless 2915ABG card for my Asus laptop.

Anyone here familiar with it? Experiences?

if you don't mind about using stuff not totally open source i still think atheros is the best choice, because of 2 factors:
- performance, my uses their Super G technology
- using it out of the box since dapper (don't know if ubuntu support it earlier)

if you do mind then maybe ralink or prism will be your best pick

---

### Post by prizrak on 2007-04-23
> And prizrak, are you sure about the Intel ones being completely open? I know that Intel provide drivers, but they also contain a binary section as far as I am aware. But the point still stands that Intel cards normally work well.
Reply With Quote
I think it might be card dependant. According to my Restricted Drivers Manager my Intel card isn't using a binary blob. I have seen a screenshot of RDM that has an Intel wi-fi driver in it. 
> I am thinking of getting the Intel PRO/Wireless 2915ABG card for my Asus laptop.

Anyone here familiar with it? Experiences?
Never used it myself but as far as I know it works with Feisty. Perhaps look at Intel website they tend to have compatibility info.

---

### Post by Anthem on 2007-04-23
My Centrino laptop has always had flawless wireless under Ubuntu.

---

### Post by jmagsho on 2007-04-23
I've had good luck with both the atheros and the prism chipsets.    I'm currently using a Netgear WGT511 and it worked out of the box with Edgy and Feisty.   I had to use the NDISWrapper drivers from Automatix with Dapper though.     

I've read that the Orinoco cards work well with most distros of Linux too...

---

### Post by PartisanEntity on 2007-04-24
Thank you for all the advice, I have gone ahead and ordered Intel PRO/Wireless 2915ABG because some friends of mine have it and have good experiences with it, however it only costs about &#8364;26 can this be right? I thought wifi cards were more expensive?

---

### Post by xyz on 2007-04-24
delete

---

### Post by xyz on 2007-04-24
I don't really know but I found this:
[http://geizhals.at/a163797.html](http://geizhals.at/a163797.html)

Might need that,too:
[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1847&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1847&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

---

### Post by PartisanEntity on 2007-04-24
> **xyz said:**
> I don't really know but I found this:
[http://geizhals.at/a163797.html](http://geizhals.at/a163797.html)

That's the website I used to search for it and I chose one of the shops in the last :)

> **xyz said:**
> Might need that,too:
[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1847&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1847&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

I am hoping the Feisty  Restricted Drivers Manager will take care of that for me, but thanks anyway.

---

### Post by xyz on 2007-04-24
Good luck then! Let us know how it goes.
I don't have WIFI but I may just be interested in it one of these days.

---

### Post by prizrak on 2007-04-24
> **PartisanEntity said:**
> Thank you for all the advice, I have gone ahead and ordered Intel PRO/Wireless 2915ABG because some friends of mine have it and have good experiences with it, however it only costs about €26 can this be right? I thought wifi cards were more expensive?
No they cards aren't that expensive anymore. It's common tech so the prices are pretty low, even when I was getting me an internal Atheros card like 3 years agot it was around $50 US (and a euro is like $1.75US right now).

---

### Post by PartisanEntity on 2007-04-26
I got my new wifi card today. Is there anything I need to do before I replace the old one in my laptop? Like removing drivers etc... ? I have never replaced hardware in either Linux or Ubuntu before.

---

### Post by TEDNUGNT on 2007-04-30
ive got the 2915 working on my ASUS W3V. works like a charm. worked with 6.10 and 7.04

---

### Post by strabes on 2007-05-01
I have full perfect support for my Intel/PRO card

---

### Post by gradedcheese on 2007-05-01
> **PartisanEntity said:**
> I got my new wifi card today. Is there anything I need to do before I replace the old one in my laptop? Like removing drivers etc... ? I have never replaced hardware in either Linux or Ubuntu before.

Nope, just plug it in.  Good choice on buying Intel, they're pretty much the best chipset maker as far as Linux wireless and graphics go.

---

### Post by awakatanka on 2007-05-01
> **TheMono said:**
> Ralink are actually the best for compatibility as far as releasing the specs, etc. You don't need the binary blobs for Ralink... 

Having said that, for some stupid reason the drivers are still imperfect, and they don't work nice with Network Manager.

I have troubles with ralink in feisty and other distro' that use the same kernel version ubuntu use. got random lockup's. Tryed to find info but only thing i find is this on vectorlinux site > Some companies chose to provide Linux support, but do it like crap.
One example of this is Ralink. I must say that it is good to see a company that does support Linux by providing GPL'd drivers, but they are of inferior quality.

If you do chose to use a Ralink based card, then you can compile the drivers provided at Ralink's website, but you can't use them with kernel that have Symetric Multi-Processing (or SMP) support enabled.
SMP is quite important nowadays, since all (or nearly all) new PC's and some high-end laptops ship with multi-core processors. SMP allows the kernel to take optimal advantage of this architecture.

Since Ralink's drivers don't have SMP support, they will crash a kernel that has SMP enabled.

There are two ways arround this:

1 - Use a SMP-disable kernel (one should be availible in the repo soon)

2- Don't buy a Ralink based card in the first place (remember in the beggining of the HowTo: make sure it works properly before buying it. And don't hesitate to ask at the forums first if you are in doubt!).



Update - 27/03/2007:

The rt2x00 project (coordinated by "serialmonkey") has made some improvements over the drivers release by Ralink.
However, these drivers (like the ones release by Ralink) do not support SMP enabled kernels.

The team is now also working on the rt2x00 project drivers which are based on chip specifications from Ralink, but aim to support SMP and follow kernel programming guide-lines, so as to one day be merged into the mainline Linux kernel releases.
If you want to test the rt2x00 drivers, then download the CVS tarball release from this page:

[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

Or just click on this link to download the tarball directly:

[http://rt2x00.serialmonkey.com/rt2x00-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2x00-cvs-daily.tar.gz)

Read the "INSTALL" file for details on compiling the right module for your card.
This is still VERY experimental stuff, so I strongly advise you not to use these drivers in an environment where stability is of utmost importance.
If you feel like a challenge and don't mind helping with the bug-squashing, then the rt2x00 release is for you.
You can post any of your debugging info at the serialmonkey forum, under the "rt2x00 BETA testing" section:

[http://rt2x00.serialmonkey.com/phpBB2/](http://rt2x00.serialmonkey.com/phpBB2/)
 Does ubuntu use SMP enabled kernels?  Because its driving me nuts. But at this point i'm not sure anymore if its my rt2500 pcmcia card our something totaly different. edgy works fine but feisty gives me random lookups if i use the rt2500 card.

---

### Post by racoq on 2007-05-01
> **gradedcheese said:**
> Nope, just plug it in.  Good choice on buying Intel, they're pretty much the best chipset maker as far as Linux wireless and graphics go.

Intel best in Graphics? i don't think so,.. they are no match to nvidia based graphic cards

---

### Post by steven8 on 2007-05-01
> **racoq said:**
> Intel best in Graphics? i don't think so,.. they are no match to nvidia based graphic cards

They meant Open Source-wise.  Intel has Open Source hardware and drivers.

---

### Post by PartisanEntity on 2007-05-01
Just to give you guys an update, I took out the old broadcom wifi card, put in the new intel one. Launched Ubuntu and everything worked. I now connect to my wifi router within seconds of logging in (before it would take ages with my broadcom card). Network strength is steady at around 70% (with the broadcom there was considerable degradation in Feisty).

---

### Post by gradedcheese on 2007-05-01
> **racoq said:**
> Intel best in Graphics? i don't think so,.. they are no match to nvidia based graphic cards

Yeah, I um... have this thing against loading proprietary drivers into kernel space.  And so do many others, for very good reason (beside the possible GPL violation when you link your driver this way).  Intel, on the other hand, not only has high-quality open source drivers, they also employ one of the main developers behind x.org.  NVidia and ATI can shove it as far as I am concerned.

---

### Post by Polygon on 2007-05-02
my d link g520 wireless card (atheros) works perfectly out of the box. The only problem is that the atheros drivers taint your kernel (just because they have a binary blob in them that controls the frequency your card uses, to follow FCC guidelines or something)....

---

### Post by LookTJ on 2007-05-02
Intel Wireless Pro 2200BG v0.5 works just fine.

---

### Post by H.E. Pennypacker on 2007-05-04
I'd really like to know more about supported wireless cards myself, and reading a forum is not exactly a great place to learn more about them.  Besides, person A will say that card X works great, but person B will say the opposite.

I am try to find a website that has a rating system, and also reviews.  Check out [www.newegg.com](www.newegg.com).  You can look up a product, check out ratings, as well as reviews by people who actually own that product.  I'd love for something like this, but specifically for Linux users.  

As far as Intel providing open source firmware, is that actually true?  I'd like to read more about this before I decide on an Intel card.  I insist on getting something completely open source, and nothing but open source.  I had been getting mixed messages about Intel and open source software.

PS:  PartisanEntity, can you talk more about how well the card works, and whether you had to follow any guides to get it to work.  I am a Broadcom card user, and every single time I am trying to setup an Internet connection, I have to follow a guide.  I'd been hoping for a thorough review.

---

### Post by gradedcheese on 2007-05-04
Open source drivers (which live in kernel space), not firmware (which lives on a small chip on the card).  If you want, take a look at my article, [Linux, Wireless, and You]("http://andrey.thedotcommune.com/wireless.html"), which explains this and gives you some buying advice.

---

### Post by PartisanEntity on 2007-05-05
> **H.E. Pennypacker said:**
> PS:  PartisanEntity, can you talk more about how well the card works, and whether you had to follow any guides to get it to work.  I am a Broadcom card user, and every single time I am trying to setup an Internet connection, I have to follow a guide.  I'd been hoping for a thorough review.

Unfortunately I don't have the experience to give you a thorough review about the card. But as I said before, I simply launched Ubuntu and the new card was working. I did not have to follow any HowTo in order to get the card to work and that is why I bought it in the first place as I have been told that the Intel drivers are open source (someone correct me if I am wrong).

I too had a Broadcom card and I too had to follow HowTo's in order to get it to work after a new installation or an upgrade, but this is obvious due to the fact that Broadcom doesn't at this moment in time make Linux drivers for their hardware.

IMO if you don't mind spending a little extra money (€26) get yourself either an Intel or an Atheros card, both work very well with Ubuntu, in the case of Atheros their drivers are not open source, but also work out of the box in many cases (in my experience the Atheros did work out of the box in Dapper and Feisty but not in Edgy).

I went for Intel due to their open source drivers.
Hope this helps.

---

