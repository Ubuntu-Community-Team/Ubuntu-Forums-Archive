---
title: "Volts and Amps for power supply"
date: 2011-07-08
forum: The Cafe
---

### Post by CoreyB. on 2011-07-08
I am looking at a video card, [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814133356") one.  It says that the power supply must be "A minimum 300W or greater system power supply (with a minimum 12V current rating of 22A)".

I have a 250 watt stock psu in a Dell Inspiron 531S.  How do I know if I meet the "(with a minimum 12V current rating of 22A)" requirement?

Thanks!

---

### Post by CharlesA on 2011-07-08
There should be a sticker on the side of the PSU with the wattage.

A stock PSU would probably not provide enough power for a Fermi.

---

### Post by Bandit on 2011-07-08
> **CoreyB. said:**
> I am looking at a video card, [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814133356") one.  It says that the power supply must be "A minimum 300W or greater system power supply (with a minimum 12V current rating of 22A)".

I have a 250 watt stock psu in a Dell Inspiron 531S.  How do I know if I meet the "(with a minimum 12V current rating of 22A)" requirement?

Thanks!

Thats the recommend specs, this however is just a recommendation. A 250w may run. Then again it may not. Also if it does run, the higher power pull on the weaker power supply can cause hardware and the entire PC in general to run hotter. Best bet is to spend 30 or 40 more bucks and get you a decent 400 to 450w and forget about it.

---

### Post by CoreyB. on 2011-07-08
I know the wattage, it is 250 watts, but will it say what the volts and amps are?  I don't understand the volts and amps things.

A few people in the comments on the Newegg page say that they are running it fine with 220 watt PSUs.

---

### Post by haqking on 2011-07-08
> **CoreyB. said:**
> I know the wattage, it is 250 watts, but will it say what the volts and amps are?  I don't understand the volts and amps things.

A few people in the comments on the Newegg page say that they are running it fine with 220 watt PSUs.

dont hedge your bets, spend the money and upgrade your PSU.

Safer to have the extra wattage.

The volts and amps should be quoted somewhere on the PSU.

an example:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=419877&Sku=T925-3083](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=419877&Sku=T925-3083)

you can see the wattage and amps and voltage is quoted

---

### Post by Bandit on 2011-07-08
> **CoreyB. said:**
> I know the wattage, it is 250 watts, but will it say what the volts and amps are?  I don't understand the volts and amps things.

A few people in the comments on the Newegg page say that they are running it fine with 220 watt PSUs.

Voltages are normally the same in all AT/ATX PSUs that I know of. Unless there is a odd one or two out there.

Those folks that say its running fine, are they saying what CPU they are running, how much and how many sticks of RAM they are using, how many and what speed hard drives they are using. If they are running low wattage CPU alone say a 65watt -vs- a 125watt. Well theres your missing 60watts. Also have they tested it under full load. I am not saying not to try it, if it works and runs cool your good to go. Its not going to hurt to try. If it doesnt, then bust out another 40 bucks for another power supply. I have ran video cards that require 500w on a 450w PSU. But that was on a bare system. When I added more hard drives and RAM I upgraded to a 650w.

Its not going to hurt to take a chance in this case, if it works, it works, just run a stability test and watch your temps. If its solid and runs cool, your good to go.

If it doesnt run, just pull the card out and order a new PSU.



EDIT:  Check the RMS rating on the PSU, thats the true wattage output. Not the advertised, the advertised many times can be based on MAX output, not true output. Thus a 230watt power supply with high efficiency can produce more watts then a cheaper 300watt PSU or low efficiency.

---

### Post by LowSky on 2011-07-08
volts multiplied by amps = watts

if a video card says it recommends 500 watts then use at least 500 watts.

trying to run too much hardware on a undersized power supply  can lead to hardware failures

---

### Post by CharlesA on 2011-07-08
Yep. Also there's the whole "OEM parts" vs "brand name parts" thing..

I googled around a bit and couldn't find ANY information about how many amps that PSU can supply on the 12V rail.

---

### Post by Bandit on 2011-07-08
> **LowSky said:**
> volts multiplied by amps = watts

if a video card says it recommends 500 watts then use at least 500 watts.

trying to run too much hardware on a undersized power supply  can lead to hardware failures

Very true, if I was doing this for a friend or business I would order a slightly higher wattage PSU then required. Say like posted above if the card requires 500w, I would get a 550w. Just to make sure the system isnt stressed and will run cool.

---

### Post by Bandit on 2011-07-08
> **CharlesA said:**
> Yep. Also there's the whole "OEM parts" vs "brand name parts" thing..

I googled around a bit and couldn't find ANY information about how many amps that PSU can supply on the 12V rail.

Hmm :-k  Even my A+ cert study manual doesnt say.

---

### Post by lisati on 2011-07-08
+1 for checking out a few more watts, and be cautious to properly match the volts.

(Apologies if I can't be more specific: it has been a while since I've looked into such things.)

---

### Post by haqking on 2011-07-08
this looks like the information for his PSU

[http://www.newpowersupply.com/250w_tfx0250d5w_for_dell_inspiron_530s_531s_sff_slimline_250w_power_supply_model_tfx0250p5wb_tfx0250d5w-pr-1323-c-8-p-1.html](http://www.newpowersupply.com/250w_tfx0250d5w_for_dell_inspiron_530s_531s_sff_slimline_250w_power_supply_model_tfx0250p5wb_tfx0250d5w-pr-1323-c-8-p-1.html)

i would suggest upgrading your PSU

---

### Post by YesWeCan on 2011-07-08
12V x 22A = 264W

From haqking's link: [COLOR=Red]Output: +12v 17A[/COLOR]  (=204W)

Don't use Unity or your PC will catch fire. :P

---

### Post by CharlesA on 2011-07-08
> **haqking said:**
> this looks like the information for his PSU

[http://www.newpowersupply.com/250w_tfx0250d5w_for_dell_inspiron_530s_531s_sff_slimline_250w_power_supply_model_tfx0250p5wb_tfx0250d5w-pr-1323-c-8-p-1.html](http://www.newpowersupply.com/250w_tfx0250d5w_for_dell_inspiron_530s_531s_sff_slimline_250w_power_supply_model_tfx0250p5wb_tfx0250d5w-pr-1323-c-8-p-1.html)

i would suggest upgrading your PSU
Nice find.

@OP: Get a better PSU first. :)

---

### Post by haqking on 2011-07-08
> **YesWeCan said:**
> 12V x 22A = 264W

From haqking's link: [COLOR=Red]Output: +12v 17A[/COLOR]  (=204W)

Don't use Unity or your PC will catch fire. :P

ha ha ha ;-)

---

### Post by tgalati4 on 2011-07-08
It will work until you let the Magic Smoke out.  Then it won't work anymore.

---

### Post by CharlesA on 2011-07-08
> **tgalati4 said:**
> It will work until you let the Magic Smoke out.  Then it won't work anymore.

So true. :KS

---

### Post by grahammechanical on 2011-07-08
Think of this, if Volts X Amps = Watts, then 12 volts x 22 amps = 264 Watts. Your PSU is going up in smoke. The link that someone gave to your PSU shows that it is rated at +12V 17A. This would use 204 Watts.

I would recommend getting a new PSU with plenty of power to spare. The heavier the unit is, the better the quality of manufacture. Better heat dissipation, cooler case temp, Quieter operation.

Regards.

---

### Post by Bandit on 2011-07-08
> **grahammechanical said:**
> I would recommend getting a new PSU with plenty of power to spare. The heavier the unit is, the better the quality of manufacture. Better heat dissipation, cooler case temp, Quieter operation.

Regards.

I concur. :)

---

### Post by halibaitor on 2011-07-08
> **Bandit said:**
> I concur. :)

+1   ;)

Your current PSU is hopelessly under powered.

---

### Post by psusi on 2011-07-08
As others have pointed out, watts = volts x amps.  PSUs supply 3 different voltages: 12v, 5v, 3.3v.  Their wattage rating is the maximum it can handle on all 3 voltage rails combined.  That video card wants 264 watts just on the 12v rail, which is more than your current psu can handle all together, so you certainly need a new one, or it will randomly shut down whenever the load gets high.

You will need to read the fine print to see the specific amperage ratings on each rail of the PSU.  Many of them have split 12v rails, which can be a problem since some of both can be consumed by other things in the computer, and neither could be left with the 22A that card needs.  Either get a PSU with a single 12v rail, or make sure that the second one is rated for at least 22A.

---

### Post by CoreyB. on 2011-07-09
Since this computer is a slim-case, would I be looking at what they call "micro-atx" power supplies?

Thanks everybody for all the advice, btw!

---

### Post by Bandit on 2011-07-09
> **CoreyB. said:**
> Since this computer is a slim-case, would I be looking at what they call "micro-atx" power supplies?

Thanks everybody for all the advice, btw!

Possibly, but hard to say without a pic of the computer and how the PSU is positioned in it.

---

### Post by CharlesA on 2011-07-09
Speaking from experience, but with the form factor of those ATX power supply, it is probably going to be a royal pain in the butt finding a better one that will fit the case.

---

### Post by haqking on 2011-07-09
he can get plenty of differnt PSU for his machine here.

[http://www.cellularfactory.com/computer/DELL/3/424873/](http://www.cellularfactory.com/computer/DELL/3/424873/)

upto 1080W

---

### Post by CharlesA on 2011-07-09
Wow nice. I wish I was able to find a PSU that fit an old compaq that easily...

---

### Post by haqking on 2011-07-09
> **CharlesA said:**
> Wow nice. I wish I was able to find a PSU that fit an old compaq that easily...


what model ?

---

### Post by CharlesA on 2011-07-09
> **haqking said:**
> what model ?
Can't remember exactly. I think it was a presario, but in the end I found out that the PSU blew up and took the mobo with it.

Went thru two or three different PSU "sizes" and none of them fit the case right. Proprietary stuff ftw! (not)

---

### Post by haqking on 2011-07-09
> **CharlesA said:**
> Can't remember exactly. I think it was a presario, but in the end I found out that the PSU blew up and took the mobo with it.

Went thru two or three different PSU "sizes" and none of them fit the case right. Proprietary stuff ftw! (not)

[http://www.atxpowersupplies.com/250-Watt-Power-Supply-Compaq-244166-001.php](http://www.atxpowersupplies.com/250-Watt-Power-Supply-Compaq-244166-001.php) ?

---

### Post by CharlesA on 2011-07-09
Wow, that actually looks sorta like it.

Nice job!

---

### Post by haqking on 2011-07-09
> **CharlesA said:**
> Wow, that actually looks sorta like it.

Nice job!

ha well when you said presario i know from a ways back having to source one for a machine at my old job and the size and shape was proprietary. ;-)

---

### Post by CharlesA on 2011-07-09
> **haqking said:**
> ha well when you said presario i know from a ways back having to source one for a machine at my old job and the size and shape was proprietary. ;-)

Having dealt with something before makes it way easier to find parts and helps to narrow down where to look to find the cause of a problem. ;)

---

### Post by haqking on 2011-07-09
> **CharlesA said:**
> Having dealt with something before makes it way easier to find parts and helps to narrow down where to look to find the cause of a problem. ;)


well that is true, however i just went to google and typed compaq presario PSU and i liked the look of the link 6 down. ;-)

---

### Post by CharlesA on 2011-07-09
> **haqking said:**
> well that is true, however i just went to google and typed compaq presario PSU and i liked the look of the link 6 down. ;-)
Your google-fu is strong! ;)

---

### Post by haqking on 2011-07-09
> **CharlesA said:**
> Your google-fu is strong! ;)

google-fu is that a plug in for google+ ;-)

---

### Post by CharlesA on 2011-07-09
> **haqking said:**
> google-fu is that a plug in for google+ ;-)
Haha.

Anyway to stay on-topic *cough*...

@OP: Check out the links that haqking posted earlier. There are some nice PSUs there. :)

---

### Post by CoreyB. on 2011-07-09
> **haqking said:**
> he can get plenty of differnt PSU for his machine here.

[http://www.cellularfactory.com/computer/DELL/3/424873/](http://www.cellularfactory.com/computer/DELL/3/424873/)

upto 1080W

All of those power supplies say Dell Inspiron 531, but I have the Inspiron 531s, with the s being for slim.  You can see [here]("http://www.google.com/search?q=dell+inspiron+531s&hl=en&safe=off&client=firefox-a&hs=8jE&rls=org.mozilla:en-US:official&prmd=ivns&source=lnms&tbm=isch&ei=1WQYTveCHIHr0gHMzMCXBQ&sa=X&oi=mode_link&ct=mode&cd=2&ved=0CCkQ_AUoAQ&biw=1680&bih=957") that the ones that are slimmer are the 531s, and the ones that are wider are the 530 or 531.

The PSU is located on the bottom of the case.

---

### Post by haqking on 2011-07-09
> **CoreyB. said:**
> All of those power supplies say Dell Inspiron 531, but I have the Inspiron 531s, with the s being for slim.  You can see [here]("http://www.google.com/search?q=dell+inspiron+531s&hl=en&safe=off&client=firefox-a&hs=8jE&rls=org.mozilla:en-US:official&prmd=ivns&source=lnms&tbm=isch&ei=1WQYTveCHIHr0gHMzMCXBQ&sa=X&oi=mode_link&ct=mode&cd=2&ved=0CCkQ_AUoAQ&biw=1680&bih=957") that the ones that are slimmer are the 531s, and the ones that are wider are the 530 or 531.

The PSU is located on the bottom of the case.


[http://www.cellularfactory.com/computer/DELL/40/47744/697/](http://www.cellularfactory.com/computer/DELL/40/47744/697/)

it says it is compatible with the 531s

there are many more in the list if you search it, also google.

---

### Post by CoreyB. on 2011-07-11
I googled around and from what I have seen the power supply for the Dell Inspiron 531s has to be a TFX12V type, so I don't know if the ATX ones that haqking posted would work.  [Here]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007657%20600014004&IsNodeId=1&name=TFX12V") is the Newegg page for TFX12V ones.  The Sea Sonic one has 21 amps on the 12v line.

Has anyone had any experience with Sea Sonic?

I've never upgraded a PSU before, is it pretty straight forward?  Anyone got any good tutorials?

Thanks!

---

### Post by CharlesA on 2011-07-11
Seasonic PSUs rock, however that is is just a 300W PSU.

They are easy to update, just swap it out and plug it in.

EDIT: The one I see on newegg has 2 12V rails at 18A each.

---

### Post by CoreyB. on 2011-07-11
[Here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817151090") is the one I was looking at, and [here]("http://www.seasonic.com/pdf/datasheet/NEW/Bulk/PC/TFX/SS-250%20300TFX_APFC.pdf") is the datasheet for it from their website.  It says 21 amps on the +12v rail, but I can't see if it has one or two rails.

What does it mean if it has 1 or 2 12v rails?  Is one better than the other or are there cases where one is desirable over the other?

Thanks!

---

### Post by CharlesA on 2011-07-11
> **CoreyB. said:**
> [Here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817151090") is the one I was looking at, and [here]("http://www.seasonic.com/pdf/datasheet/NEW/Bulk/PC/TFX/SS-250%20300TFX_APFC.pdf") is the datasheet for it from their website.  It says 21 amps on the +12v rail, but I can't see if it has one or two rails.

What does it mean if it has 1 or 2 12v rails?  Is one better than the other or are there cases where one is desirable over the other?

Thanks!

Ah. I was going off the label on the PSU in the picture.

See [here]("http://www.jonnyguru.com/forums/showthread.php?t=3990") for some pro/con of having single/multiple 12Vrails.

I've used PSUs with single rails and ones with multiple rails without any problems. I prefer single rail PSUs, but it's up to you and I think that Seasonic is going to be the best PSU you'll be able to get.

---

### Post by CoreyB. on 2011-07-11
There seems to be a discrepancy even on the Seasonic website.  [This]("http://www.seasonicusa.com/tfx.htm") says what you said and [the catalog]("http://www.seasonicusa.com/PDF/Catalog/NEW/Bulk/PC/TFX/SS-300TFX-APFC.pdf") says what I said.

I wonder what one Newegg sells?  I'm guessing the 21 amps with a single 12v rail because on Newegg, the type says "TFX12V v2.3", which is what it says on the catalog, and the other website I linked to above says "TFX12V (v2.1)".

Thanks for the info!

---

### Post by CoreyB. on 2011-07-11
Would a new PSU have an effect on how effectively the computer cools itself, or does a PSU not have any effect on that?

---

### Post by CharlesA on 2011-07-11
> **CoreyB. said:**
> There seems to be a discrepancy even on the Seasonic website.  [This]("http://www.seasonicusa.com/tfx.htm") says what you said and [the catalog]("http://www.seasonicusa.com/PDF/Catalog/NEW/Bulk/PC/TFX/SS-300TFX-APFC.pdf") says what I said.

I wonder what one Newegg sells?  I'm guessing the 21 amps with a single 12v rail because on Newegg, the type says "TFX12V v2.3", which is what it says on the catalog, and the other website I linked to above says "TFX12V (v2.1)".

Thanks for the info!

Hmm. I hate it when that happens. There was a phone number on the datasheet, which I would call and see which PSU is out there.

> **CoreyB. said:**
> Would a new PSU have an effect on how effectively the computer cools itself, or does a PSU not have any effect on that?

Shouldn't really have much effect.

---

### Post by psusi on 2011-07-11
Generally power supplies with split 12v rails have one that is meant to power the motherboard, and one that is meant to power everything else.  They generally don't have more than about 15 amps of capacity on the "everything else" rail, so really, you need to find a 500+ watt power supply with a single 12v rail.

It also sounds like you have an OEM case.  OEM cases tend to be custom modified and require a modified OEM PSU and sometimes motherboard as well to fit.  Given that, you should probably get a new standard ATX case to fit an ATX power supply.

A good case will come with or have slots where you can add plenty of fans to give plenty of cooling.  The PSU has a fan as well, but that is mostly for cooling itself.

---

