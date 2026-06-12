---
title: "Wireless router not detected"
date: 2010-02-16
forum: System76 Support
---

### Post by ranch hand on 2010-02-16
I have this new Pangolin that I got my wife set up so she just loves it.

We have dsl so it hooks up great to that.  There are a couple bars in town with a wireless connection.   It has no trouble with that either.

Bought a Linksys WRT54G router.  Figured to hook it through our router (wire only) to connect this box from where ever she wants to work.

Hooked through our router it works fine for a wired connection.

I can't detect the bugger from 5 feet away.  Is it bad (it is used)?  Am I just ignorant (a real possibility)?
```

Wireless WiFi Link 5100
vendor: Intel Corporation

```
and
```

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0

```
seem like the handiest info I have.  I can get more is needed.

Another important thing is that it does pick up signals from outside the house (the neighbors).

---

### Post by Noah0504 on 2010-02-16
I would say it's bad.  I work for a computer service company, and I can no longer count on my two hands how many routers we have pulled out of the box brand new that were defective or DOA.  Did you pick it up locally?  If so, I would go see if you can swap it out.

---

### Post by ranch hand on 2010-02-16
> **Noah0504 said:**
> I would say it's bad.  I work for a computer service company, and I can no longer count on my two hands how many routers we have pulled out of the box brand new that were defective or DOA.  Did you pick it up locally?  If so, I would go see if you can swap it out.
Thank you very much.  I was afraid of that.

I bought on line and so that is out but I will hold on to it as a spare, it works fine wired.

I want to stay with Linksys (I think) as I have used them, wired, and know they work.  Never used one, or connected with anything but dial up until March last year.

Searching for info on this problem brought up several folks opinion that this is not a real good router for wireless.

Any suggestions for a better model will be appreciated and investigated.

---

### Post by 2hot6ft2 on 2010-02-16
> **ranch hand said:**
> 
[/code]
and
```

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          [COLOR="Blue"]**Tx-Power=15 dBm   **[/COLOR]
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0

```
That's only 32 mW, I don't own an adapter that is less than 20dBm or 100mW.
If you have a usb wifi adapter try it.

I have a Linksys WRT150N with dd-wrt on it and it works great.

---

### Post by Noah0504 on 2010-02-16
I personally love Linksys.  It's what I have been buying for years, and it and Cisco (kind of one in the same) are the two name-brands we carry and sell at work.  The products are for the most part rock-solid and just as fancy as they need to be.  The WRT54G is a fine Wireless router.  However, it seems like the WRT54G2 is the replacement model.  I surprised you were able to find one of the older varieties.  It never hurts to browse online (Amazon.com or Newegg.com for instance) and see the reviewed others have posted.

I personally stick with the WRT54GL.  I know those model numbers can get confusing, but it is essentially a router with a few extra specifications that make it able to run third party firmware that is often more lean than the stock Linksys firmware.

I hope I didn't make your choice any more difficult!

---

### Post by 2hot6ft2 on 2010-02-16
Don't trash the router without first at least trying dd-wrt on it if it's a supported version. [http://www.dd-wrt.com/site/support/router-database](http://www.dd-wrt.com/site/support/router-database)
Of course you may have got one that someone already had it on and they cranked up the TX power until they fried the transmitter. It's supposed to be a real good router.

---

### Post by ranch hand on 2010-02-16
I am not going to trash the router.  It works fine wired and my wired router may crater.

@2hot6ft2
What is this "32 mW" that you mention and where did you get it?  I have not got a clue.

If it has to do with range, I think it is enough for us.  It does fine at the bar and one router i am picking up from the neighborhood is using a last name as the device name so I know where it is.  There is a house between us.

It it has to do with speed, my wife has used it at the bar (tends bar there in the daytime) and found the speed just fine with her.

@Noah0504
I will check out the buggers a little more and run a search for the numbers you gave.  This by no means makes things harder.  I got that one blind.  Absolutely no clue.  Now I have a clue.  A few more and I may start to learn something about this.

It may help folks to understand better to know that the last ranch I was on did have phone service (land line).  Cell phones would work in a few, very small places for about a 40 mile radius of the place.  We never bothered as they just are of no use.  DSL service only needed to come another 46 miles to get to us.  Dial up is the only affordable answer there and many places.

Now I need to learn this stuff too.

If you need help with your internal modem on Hardy for dialup let me know.  That I can do in my sleep.

---

### Post by jdb on 2010-02-16
> **ranch hand said:**
> 
What is this "32 mW" that you mention and where did you get it?  I have not got a clue.


mW is milliWatt or .001 Watt which is a measure of power.

15 dBm is 15 decibel from a milliWatt

A decibel is .1 bel so 15 dB is 1.5 B

bel is a logarithmic scale so:

10^1.5 = 10 to the 1.5 exponent = 31.62

and

31.62 x 1 mW = 32 mW

jdb

---

### Post by 2hot6ft2 on 2010-02-16
> **ranch hand said:**
> 
@2hot6ft2
What is this "32 mW" that you mention and where did you get it?  I have not got a clue.

If it has to do with range, I think it is enough for us.  It does fine at the bar and one router i am picking up from the neighborhood is using a last name as the device name so I know where it is.  There is a house between us.

It it has to do with speed, my wife has used it at the bar (tends bar there in the daytime) and found the speed just fine with her.

I got it from the ifconfig info in your first post 15dBm = 32mW. Like the previous post explained (perhaps too in depth)...;)
It just means that it doesn't have a s much power as one that is higher. This can be both good and bad.
Good for battery life.
Bad for receiption

If you're getting the neighbour 2 doors down then it's doing real good so no problem there you got a good one.

No you don't need to know all this stuff we were just looking for possible reasons why you were unable to connect to your router by wifi.

---

### Post by ranch hand on 2010-02-16
Hey jdb & 2hot6ft2

Thanks a bunch.  This is not to in depth.  I do need to know this stuff.  I have come to know the way I learn is not quite the same as for every one else but I have figured it out over the years.

It has been a long time but math is one thing I was real good at in school.  Not bad at physics either.  Both handy when trying to get some old piece of agricultural equipment going or making parts in the ranch shop.

Also handy with the computers.

For some reason I was misreading dB as B as in baud.  What a moron.  I really am a noob.  I am trying to get over it.  Really.

---

### Post by 2hot6ft2 on 2010-02-16
You're welcome. If you get a chance or get bored sometime you might check the routers configuration. If it has dd-wrt firmware on it there is an adjustment for the TX power. The default is usually around 70 but it may have been changed by the previous owner.

You can log in to the router by going to 192.168.1.1 in your browser.
In dd-wrt it's under Wireless > Advanced Management > TX Power.
If it has the linksys firmware on it I'm not sure if the option to change it is there or not.

Going higher only increases it's transmit power and does nothing for the RX receive power. Still people will get them and run them as high as they can go which is usually around 250 which can burn out the transmitter due to overheating.

---

### Post by ranch hand on 2010-02-16
I actually just put the bugger in storage for now.  I am going to search for another one.

I have a Linksys wired router and I figured that was the way to get to this on too.

Right now I have little time as I am testing 10.04 (looking good except for plymouth problems right now).  Have a kernel update waiting and need to get it up on a couple installs before trying it on my "production" installation.  A3 comes out the 25th and I hope this kernel update fixes the boot problem with plymouth but I think we need a new version of that too and maybe ureadahead.  Booting to recovery every time is getting old.

Other than that it is really great.  9.10-testing was a rough ride.  This one is pretty nice, I like it a lot and look forward to upgrading the wifes laptop to it from 9.10.

---

### Post by ranch hand on 2010-02-17
Ordered one of the GL buggers.  Coming from Washington (state) so doesn't have far to go.  New.

Hope it is in better shape.

---

### Post by Noah0504 on 2010-02-17
> **ranch hand said:**
> Ordered one of the GL buggers.  Coming from Washington (state) so doesn't have far to go.  New.

Hope it is in better shape.

I don't want to jinx you, but I think you'll like the router.  I have one in my apartment serving all of my needs and my parents have one that I installed.  It's been running great for a few years now.

---

### Post by ranch hand on 2010-02-17
That is good to hear.

Linux on routers!  What is the world coming to.

---

