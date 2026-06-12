---
title: "Lubuntu -- USB wireless adapter that works"
date: 2014-06-28
forum: Ubuntu, Linux and OS Chat
---

### Post by Mike_Berger on 2014-06-28
Please, just want to keep this SIMPLE. Have an Edimax EW-7811Un that does NOT work in my Dell c600 laptop with the latest Lubuntu. So what? I"ll just buy a new one rather than spending all day making it work.

Please, can you simply give me a model number(s) of a fool proof adapter that will work?

I like the small USB Edimax if possible but just want something that will plug and play with Lubuntu -- don't have the time for nonsense, driver downloads etc.

Thanks very much.

---

### Post by Mike_Berger on 2014-06-28
and I mean multiple downloads etc or working for an hour in terminal.

just a wifi adapter that is proven to do the job.

---

### Post by Vladlenin5000 on 2014-06-28
Any adapter based on Realtek 8191SU is "plug&play" and they usually work great.
Here's one (just an example): [http://www.dx.com/p/166678?Utm_rid=96781194&Utm_source=affiliate](http://www.dx.com/p/166678?Utm_rid=96781194&Utm_source=affiliate)

---

### Post by Mike_Berger on 2014-06-28
Thanks kindly -- I'm buying it. Should I wait till after Lubuntu loads or plug it in before I boot ? Still getting a feel for Lubuntu -- making use of an old laptop, Dell C600.

---

### Post by Vladlenin5000 on 2014-06-28
From experience I would say it doesn't matter. You may have to wait a few seconds for it to be recognized if you plug it after booting. Other than that it's the same. Mine is always plugged and it usually connects to the network even before a login.
Enjoy :p

---

### Post by Mike_Berger on 2014-06-28
is this deal extreme in the US? I need one quick -- thanks.

---

### Post by Vladlenin5000 on 2014-06-28
China, I'm afraid. Even their US Direct (or EU or AU for that matter) are sent from China. The only difference is a *supposedly* faster shipping service. 
Anyway, if you have any problem they also have a forum (plus the usual customer service) -and- you can contact me via PM (private message in this forum) with the order number and I'll give them a (serious) nudge ;).

---

### Post by kurt18947 on 2014-06-28
Mike, if you're in the U.S. you should be able to find a Trendnet TEW-649UB which uses the RTL8192SU chip last I knew. You should also be able to make your Edimax work.  I have one plugged into a Thinkpad, it's perfect.  The problem is the broken RealTek driver included in Ubuntu.  A kind and talented soul patched the driver from Realtek so it works with 13.10 and 14.04 that I know of.  Here's the page:

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

All I do is open a terminal over my web browser.  Go down to the "install" section and copy/paste each line, pressing 'enter' each time.  You would need to do this from an account with SUDO/admin. privileges. This seems to work with my RTL8188CUs (Edimax EW7811Un) and generic RTL8192CU devices.  RTL8192**SU **seems to well 'out of the box', RTL8192**CU** does not and RTL8192CU devices seem more common.

---

### Post by squakie on 2014-06-28
I've had fantastic success across releases with the Tenda W322UV2.0.  I've gotten these at Micro Center for way under $20 - usually around $12.  The've always just worked "out of the box".  It's using the RaLink RT3072.

BTW - this an B/G and N adapter.  I get full 300mps on my wireless to my router.

---

### Post by folgers on 2014-06-28
Sadly Ubuntuhcl dot org is nolonger, but give these guys a phone call.  They might be able to help you.

[https://www.thinkpenguin.com/gnu-linux/penguin-wireless-g-usb-adapter](https://www.thinkpenguin.com/gnu-linux/penguin-wireless-g-usb-adapter)

---

### Post by Vladlenin5000 on 2014-06-28
$21.97 (not including S&H) for a Realtek 8187**B** ("g" only) which is older than my long dead grandma? Is this a joke or what?
*If* you still can find a similar one from other assembler it'll be worth less than $5.

---

### Post by Mike_Berger on 2014-06-29
I get to install 8192cu/1.9 and get "can't find module source directory" -- up to that line all has gone well.

Lununtu newbie.

---

### Post by Vladlenin5000 on 2014-06-29
Hummm... I think you need to cd into the cloned git directory ```
cd rtl8192cu-fixes
``` before issuing ```
sudo dkms install 8192cu/1.9
```

---

### Post by folgers on 2014-06-29
Are there any good HCL's (Hardware Compatibility Lists) for Ubuntu that really cover this subject (USB Wireless)?

---

### Post by Vladlenin5000 on 2014-06-29
> **folgers said:**
> Are there any good HCL's (Hardware Compatibility Lists) for Ubuntu that really cover this subject (USB Wireless)?

No, not really, not comprehensive and updated anyway. And definitely not "newbie-friendly"...

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by Bucky Ball on 2014-06-29
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by Mike_Berger on 2014-06-29
ok did that and now the edimax is working -- funny because I left out the last line about blacklisting -- didn't want to create a problem unless I had to buy another adapter (which I did anyway) the trendnet.  good for now it seems.  thanks.

---

### Post by kurt18947 on 2014-06-29
> **Mike_Berger said:**
> ok did that and now the edimax is working -- funny because I left out the last line about blacklisting -- didn't want to create a problem unless I had to buy another adapter (which I did anyway) the trendnet.  good for now it seems.  thanks.

I'm surprised that it worked without blacklisting the original driver.  One sure way to have wifi problems is to have two different drivers fighting to control the same device. You can tell which modules are loaded by typing 'lsmod'(list modules) in a terminal.  The broken one is rtl8192cu, the one that works is just 8192cu.  Mine is near the top of the list, I have to scroll up in the terminal.  If the Trendnet TEW-649UB is still using the RTL8192SU chipset you should be able to plug it in and it'll just work.  I don't know if having the patched 8192cu module loaded when you plug in the TrendNet device will cause a problem, I don't think it should.  One RealTek provided module drives most current production USB devices, it seems.  You just wouldn't be able to be sure the TrendNet would work 'out of the box'.  Booting a live CD/USB would tell the tale though.

---

### Post by Mike_Berger on 2014-06-30
I actually see (4) different modules and used by -- rtl8192cu(0) -- rtl8192cu_common(1) -- rtlwifi(2) -- rtl_usb(1)  ?

Anyway, it works now. This old machine (Dell C600) is actually damn peppy with Lubuntu.

---

### Post by kurt18947 on 2014-06-30
> **Mike_Berger said:**
> I actually see (4) different modules and used by -- rtl8192cu(0) -- rtl8192cu_common(1) -- rtlwifi(2) -- rtl_usb(1)  ?

Anyway, it works now. This old machine (Dell C600) is actually damn peppy with Lubuntu.

Interesting - the only wifi related modules I see on my machine are cfg80211 and 8192cu, no rtl-anything.  But step 1 of troubleshooting is "Does it work? Yes? Then don't mess with it!":D.

Yeah, it's interesting how well the lighter distros work on older machines, isn't it?  I have a tinkering box, an HP Pavilion 6735 from around 2000.  Original Celeron 667 Mhz and 13 GB. hard drive.  Came with 64 MB. RAM and WindowsME.  I upgraded it to a whopping 512 Meg.  Plugged in Nvidia MX4000 PCI video card, USB2 and ethernet PCI cards.  I'm pretty sure it wouldn't run any recent flash versions but for basic web browsing it ain't bad.  I'm thinking of making it a full time torrent box for deserving distros.

---

### Post by Mike_Berger on 2014-06-30
Someone should gather old pcs, put on Lubuntu and send them to 3rd world countries. Shame that 95% of the hardware ends up in scrap.

---

### Post by kurt18947 on 2014-07-01
> **Mike_Berger said:**
> Someone should gather old pcs, put on Lubuntu and send them to 3rd world countries. Shame that 95% of the hardware ends up in scrap.

That's not a bad idea and it wouldn't be necessary to ship 'em all to 3rd world countries.  I'll bet there's plenty of kids without home PCs in the U.S.  There'd be two issues.  One is that hard drives in retired corporate P.C.s are often shredded or otherwise destroyed.  The second would be software.  I'm guessing schools might baulk at non-Windows non-Apple educational software.  Non-North American countries might be more accepting of 'nonstandard' educational software.

---

