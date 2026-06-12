---
title: "My new frustration - laptops with whitelisted wireless cards."
date: 2013-06-30
forum: The Cafe
---

### Post by Roasted on 2013-06-30
After dealing with some Broadcom STA issues, I decided to swap wireless chips with an available Intel card I had on the shelf. To my surprise, the system locked on boot and said an unauthorized network card was detected and must be removed to boot. I thought this was a fluke, so I called tech support. Nope, definitely no mistake. I was unable to swap wireless cards in the particular unit I was working on.

Tonight I got a hold of another laptop, different model, but same brand. I swapped wireless cards in it just for kicks and sure enough, it locked up as well. 

I can understand from a business standpoint to ensure the compatibility between your hardware platforms you fire out, but I'm having a little difficulty understanding how this makes sense to the end user. So when a new wireless standard comes out, you're just unable to upgrade it because the manufacturer says so? Am I understanding this properly? Or perhaps can you buy a new wireless card with their brand and upgrade accordingly? Based on the conversation I had over the phone, it sounded like I was indefinitely locked into using this wireless card with no upgradability on the table. That was just one phone tech support though, so perhaps there is more information to the story than what I initially received.

At any rate, I am growing increasingly disappointed with how Lenovo (yes, Lenovo) locks these units into specific wireless chipsets. I understand HP does the same thing, but HP hasn't really been my go-to brand for laptops and other pieces of hardware. I'm thankful that I learned this newfound information on work issued systems I had available, as I cannot possibly fathom purchasing a Lenovo for personal use after finding this out. System 76 is looking so dang nice these days.

Has anybody else ran into this? Is there any way around it without risking a BIOS hack and ultimately a potential BIOS crash, rendering the system useless?

---

### Post by kurt18947 on 2013-07-01
I believe you have to install a 'whitelisted' hardware device or do a BIOS hack/replacement.  Personally I just use a USB wifi network adapter.

---

### Post by ssam on 2013-07-01
yes, its annoying. if you search ebay you can usually find a card will work with your lenovo model.

---

### Post by Roasted on 2013-07-01
> **ssam said:**
> yes, its annoying. if you search ebay you can usually find a card will work with your lenovo model.

This is what I started to gather. Three Lenovo techs over the phone told me it's a no-go and the wireless card that came with your model is the one it'll die with. But another discussion with an escalated supervisor through Lenovo said you can look up a PS-REF sheet on your unit and it'll list all of the compatible hardware for it - wireless cards included. I did dig it up but it's quite long and so far, I only see what configurations the model came in... not what hardware is compatible with it. Unless she's telling me that whatever hardware that the unit COULD have came with is effectively what's compatible with it??

Also, a quick Ebay scan showed up literally nothing for my exact model besides the identical Broadcom that came with it. I can say with absolute certainty I won't be buying a Lenovo in the future if these kind of tactics are things I'll need to avoid. It's a real shame because Lenovo has some sweet hardware, but dang, these kind of decisions are so fail it's difficult to comprehend.

---

### Post by tgalati4 on 2013-07-01
In order for the laptop to put the wireless to sleep and wake it properly, the BIOS needs to know exactly what kind of wireless card is installed.  Changing the card to a different model means the BIOS will be sending commands that may or may not work.  The same thing happens when you change hard disks on thinkpads--you get an error message on boot saying "This is not an authorized hard disk."  but it works and boots with the annoying BIOS message each time.  So going from a stock 80 GB IBM-brand hard disk to a WD 320 GB disk will give you the error message and there is no fix, other than modifying the BIOS.

I imagine the wireless check is a similar situation and not a master conspiracy.  How often would one replace a wireless card in a laptop?  Or a hard disk?  Most laptops fall apart long before the wireless card wears out. 

If you can turn the wireless off in BIOS, install the new, non-OEM, wireless card, then boot.  See if the wired/cable networking still works.  Then try turning on the wireless card using a software switch in linux (*rfkill*).  It's an annoying work around, but it may work.  If that is the case, then put the *rfkill* command in a bootup script to wake the wireless through software, bypassing the BIOS check.

An alternative is to complain to Lenovo and get them to issue a BIOS upgrade with a patch that is less annoying.

---

### Post by mips on 2013-07-01
I had a similar issue on my old HP. There were two fixes for it, hacked wireless card firmware identifying the device as another brand or a hacked bios. I did both :biggrin:

---

### Post by Roasted on 2013-07-01
> **tgalati4 said:**
> In order for the laptop to put the wireless to sleep and wake it properly, the BIOS needs to know exactly what kind of wireless card is installed.  Changing the card to a different model means the BIOS will be sending commands that may or may not work.  The same thing happens when you change hard disks on thinkpads--you get an error message on boot saying "This is not an authorized hard disk."  but it works and boots with the annoying BIOS message each time.  So going from a stock 80 GB IBM-brand hard disk to a WD 320 GB disk will give you the error message and there is no fix, other than modifying the BIOS.

I imagine the wireless check is a similar situation and not a master conspiracy.  How often would one replace a wireless card in a laptop?  Or a hard disk?  Most laptops fall apart long before the wireless card wears out. 

If you can turn the wireless off in BIOS, install the new, non-OEM, wireless card, then boot.  See if the wired/cable networking still works.  Then try turning on the wireless card using a software switch in linux (*rfkill*).  It's an annoying work around, but it may work.  If that is the case, then put the *rfkill* command in a bootup script to wake the wireless through software, bypassing the BIOS check.

An alternative is to complain to Lenovo and get them to issue a BIOS upgrade with a patch that is less annoying.

I can understand some of these technical items you mention. I think what bothers me is so far it looks like you are literally stuck with the exact chip it came with. So consider a business that upgrades wireless from N to AC, and then they want to swoop in and install SSD's and new wireless cards on each unit? From a cost-saving standpoint with trying to squeeze every dollar out of the machine and prolong their use, this makes a lot of sense. It's something that a lot of organizations (largely school districts) do to maximize each dollar. But, hey! If you bought a Lenovo, too bad. THAT is where this entire situation is an epic and, to be frank, inexcusable failure.

On one hand, I find myself saying, well give them some credit. You CAN customize the system, just get Intel or Atheros wireless cards when you purchase it. But as I mentioned above, the need to swap out wireless cards can easily arise as standards change or something like that. I would even welcome a BIOS switch to override the setting with a disclaimer that your laptop might not suspend properly or do whatever if you proceed. But nope, just lock them all out cold turkey.

EDIT - I found on the PS REF sheet the Intel Centrino 2230 was an available wireless card for this model. I found a used-but-working one on ebay for 7 bucks. I ordered it. I'm curious to see if that chip will be whitelisted for this unit as well. My hope and expectation would be that it would work, because I would think to custom-flash each BIOS for your specific hardware profile would be obnoxious. I would think that it would make more sense to flash the BIOS to accept any of the available chips that were part of the possible choice list, but Lenovo has surprised me in unfortunate ways before, so we'll see.

Did I mention System 76 is looking incredibly, incredibly attractive these days?

---

### Post by mastablasta on 2013-07-02
Large organisaitons wouldn't just switch wi-fi networks withouth htinking it through first. furthermore they would use rented mashcines and replacing those is not an issue or big cost anyway.

i wonder what ever happened to PCMCIA slots. used to be omnipresent in all laptops but now these cool expansion ports are gone it seems. sticking a wi-fi card into that slow makes it far less bulky than on USB. then again they have now those mini USB wi-fi that barelly protrude out from the USB.: [https://www.google.com/search?q=USB+wifi+mini&rls=com.microsoft:sl:IE-SearchBox&tbm=isch&tbo=u&source=univ&sa=X&ei=3Y7SUc_fBcSM4ASsnYHoBQ&ved=0CD4QsAQ&biw=1280&bih=827](https://www.google.com/search?q=USB+wifi+mini&rls=com.microsoft:sl:IE-SearchBox&tbm=isch&tbo=u&source=univ&sa=X&ei=3Y7SUc_fBcSM4ASsnYHoBQ&ved=0CD4QsAQ&biw=1280&bih=827)

---

### Post by mips on 2013-07-02
> **tgalati4 said:**
> In order for the laptop to put the wireless to sleep and wake it properly, the BIOS needs to know exactly what kind of wireless card is installed.  Changing the card to a different model means the BIOS will be sending commands that may or may not work.  The same thing happens when you change hard disks on thinkpads--you get an error message on boot saying "This is not an authorized hard disk."  but it works and boots with the annoying BIOS message each time.  So going from a stock 80 GB IBM-brand hard disk to a WD 320 GB disk will give you the error message and there is no fix, other than modifying the BIOS.

I imagine the wireless check is a similar situation and not a master conspiracy.  How often would one replace a wireless card in a laptop?  Or a hard disk?  Most laptops fall apart long before the wireless card wears out. 

If you can turn the wireless off in BIOS, install the new, non-OEM, wireless card, then boot.  See if the wired/cable networking still works.  Then try turning on the wireless card using a software switch in linux (*rfkill*).  It's an annoying work around, but it may work.  If that is the case, then put the *rfkill* command in a bootup script to wake the wireless through software, bypassing the BIOS check.

An alternative is to complain to Lenovo and get them to issue a BIOS upgrade with a patch that is less annoying.

I don't really agree here. There are industry standards on how hardware should communicate. In most cases it's simply a ploy by manufacturers (Lenovo, HP etc) to buy their branded hardware at inflated costs as the off the shelf items will not work simply due to the whitelist. I hacked my wireless cards firmware, everything worked just fine afterwards, I then went one step further and flashed it with a custom/hacked bios image where the whitelist was removed, still happily working without any issues and there are thousands of people that have gone down this road before.

---

### Post by ssam on 2013-07-02
I have not seen this with disks. I used plenty of disks on my thinkpad x31 and ideapad s12 without trouble. not changed the main disk in my x230 yet, but it booted fine with a crucial mSATA ssd installed.

I though the official reason for the wifi card lock was for RF regulations. That the laptop is only guaranteed to meet is FCC with an OEM wifi card. The regulations around stray emissions and RF kill switches are quite strict. Though that does not explain why other manufactures dont include these locks.

My x230 has a intel card, so I have no need to swap it.

ps: [http://www.thinkwiki.org](http://www.thinkwiki.org) is quite a good resource for lenovo/ibm hardware

---

### Post by Roasted on 2013-07-02
> **ssam said:**
> I have not seen this with disks. I used plenty of disks on my thinkpad x31 and ideapad s12 without trouble. not changed the main disk in my x230 yet, but it booted fine with a crucial mSATA ssd installed.

I though the official reason for the wifi card lock was for RF regulations. That the laptop is only guaranteed to meet is FCC with an OEM wifi card. The regulations around stray emissions and RF kill switches are quite strict. Though that does not explain why other manufactures dont include these locks.

My x230 has a intel card, so I have no need to swap it.

ps: [http://www.thinkwiki.org](http://www.thinkwiki.org) is quite a good resource for lenovo/ibm hardware

Everything I've read suggests that this is the "excuse" that's used but that it doesn't hold any legal water. I'm no expert on the subject, but the first question that comes to mind is this... if all wireless cards must meet FCC regulations in order to be sold, why am I restricted on which FCC approved wifi chips work in my Lenovo? Furthermore, why is Lenovo bound by this "legal" restriction while other companies are not? Lenovo has been doing this as early as 2006, so this isn't new (I'm astounded I never heard of it before until recently), so if there was some sort of legality issue that's involved, I find it hard to believe that Lenovo would be playing ball while all other companies (besides HP) would have been ignoring it for the last 7 years... 

I'm calling it. It's a crock. If you look at some of the prices of Lenovo-branded wireless chips, things might come into perspective a little more. Quite the Apple move, in my opinion.

---

### Post by chili555 on 2013-07-02
[http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card](http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card)>  IBM/Lenovo's reasoning for this is that the combination of MiniPCI card and the integrated antenna in the ThinkPad needs to be certified by the US FCC (Federal Communications Commission) or similar agencies in other countries. I doubt that Lenovo will soon change its stance since they may be subject to penalties from the US FCC and I suspect the US is their largest market.

I have successfully used the 1802 hack on an IBM but not yet on either of my two Lenovos. I bought them with Intel cards for just the reasons you enumerate.>  Lenovo has been doing this as early as 2006, so this isn't newAnd IBM far earlier than that.

[http://joshuawise.com/wireless-whitelist](http://joshuawise.com/wireless-whitelist)

Have you fully exhausted all the options with respect to your Broadcom?

---

### Post by Roasted on 2013-07-02
> **chili555 said:**
> [http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card](http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card)I doubt that Lenovo will soon change its stance since they may be subject to penalties from the US FCC and I suspect the US is their largest market.

I have successfully used the 1802 hack on an IBM but not yet on either of my two Lenovos. I bought them with Intel cards for just the reasons you enumerate.And IBM far earlier than that.

[http://joshuawise.com/wireless-whitelist](http://joshuawise.com/wireless-whitelist)

Have you fully exhausted all the options with respect to your Broadcom?

Respect to Broadcom? They get none of that from me. I didn't purchase this unit, otherwise I would have undoubtedly picked an Intel card. I guess my frustration stems beyond any issues I'm having and into the realm of, what if a user wants to upgrade from N to AC? They just can't because Lenovo says so?

With all do respect, I'm still calling their nonsense reasoning out. It's a crock.

---

