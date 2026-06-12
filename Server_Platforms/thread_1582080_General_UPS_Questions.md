---
title: "General UPS Questions"
date: 2010-09-25
forum: Server Platforms
---

### Post by ts230 on 2010-09-25
So, I need an UPS for my server, and I was doing some looking online and got onto APC BE450G. I like it quite a bit, but before buying it, I need to know if Ubuntu supports it and is able to get the battery state. 

What I want to do is that if it goes onto battery, I want the server to update the dyndns to point to a different server, email me, and then shut itself down to prevent any damage. The UPS is called APC BE450G. 

I also would like to know if I have to install any additional drivers, or if it already works out of the box. Even if so, it would be awesome if I could have a list of required packages.

Thanks! (BTW, here's the link to the UPS: [http://www.newegg.com/Product/Product.aspx?Item=N82E16842101349](http://www.newegg.com/Product/Product.aspx?Item=N82E16842101349) )

---

### Post by SeijiSensei on 2010-09-25
sudo apt-get install apcupsd

This is a daemon process that will monitor your APC UPS and take various measures if you lose power.  I don't know if it can switch your DNS entries, though.  If you can do this by running a bash script, then you can tell apcupsd to run the script when the power fails.  See "man apcupsd" for details.

If you can't do this via scripting, but dyndns permits so-called "round-robin" DNS entries, you can build in redundancy that way by having a host name point to multiple IP addresses like this in the zone file:

```

www     IN    A    10.10.10.1
        IN    A    192.168.33.1

```
That will send requests for the www hostname to one or the other IP at random.  This is fine if the site isn't dynamic but will not work if you need things like persistent session cookies.

apcupsd will gracefully shut down your server; there's also client software that enables it to tell any other machines on the network using the UPS that they need to shut down as well.

---

### Post by HermanAB on 2010-09-26
Hmm, you should think about the power failure mode first.

In my area, long term power failures are extremely rare, but short term spikes/drops are common and happen several times a week and sometimes several times a day.  Therefore, having a machine shut down each time there is a short term problem aggravates the situation.  I found that it was better to plug the UPS in and disable the annoying beeper and not hook the UPS control interface line to anything.

In several years of use, the UPS battery ran flat once.  The rest of the time, it kept the server going successfully.

---

### Post by ts230 on 2010-09-26
Thanks for the info. But what I want to do is keep the Server running on UPS power for as long as possible, until I hava about 2 minutes of usable power left in the batteries, and only THEN shut down. I don't want the server to shut down every time a power outage happens. In my area they happened quite a few times during the last few months, about 3-4 a week, and I get pretty peeved off when that happens since it usually occurs when I am at school, and then it's like 1 minute of powerloss. So that's what I'm planning to use the UPS for.

---

### Post by BkkBonanza on 2010-09-26
The apcupsd has quite a bit of control over how it triggers your script. You should be able to set it to only run your script when a couple minutes of power are left.

**[man apsupsd]("http://linux.die.net/man/8/apcupsd")** or the [site]("http://www.apcupsd.com/").

That model seems a little under rated for a normal server but I don't know how much power yours uses. Check [here]("http://www.apc.com/resource/include/techspec_index.cfm?base_sku=BE450G") to see time vs. power graph. I'd expect about 7 minutes and as time goes by the battery will become worse, giving less time. Only you know the average power outage time in your area so consider that when deciding. (Amazon has the 750 VA model for about $20 more, which gives about 20 minutes)

Your script can [update the dyndns IP]("http://www.dyndns.com/developers/specs/syntax.html") value with a very simple wget call,

```
wget -q --user=$DYNUSER --password=$DYNPWD https://members.dyndns.org/nic/update?hostname=$DYNHOST&myip=$NEWIP&
```

You need to specify the ip if it's not the one you are updating from.

---

### Post by HermanAB on 2010-09-26
Howdy,

Predicting the power left in a battery is pretty hard.  That is why I gave up and ignored the PSU warnings.  If the battery runs flat once in a few years, it is OK.

---

### Post by CharlesA on 2010-09-26
> **HermanAB said:**
> Howdy,

Predicting the power left in a battery is pretty hard.  That is why I gave up and ignored the PSU warnings.  If the battery runs flat once in a few years, it is OK.

Indeed.

@OP: I have the same UPS and it works fine with apcupsd.

Try BkkBonanza's suggestion, since that would probably work best. :)

---

### Post by ts230 on 2010-09-26
Thanks for all the help so far, but there might be a slight change of plans from the current UPS to [this one.]("http://sfbay.craigslist.org/sby/ele/1969510655.html")

I wonder if I even need to check for the battery state on that, It'll probably run the server and modem and router for about a day.

---

### Post by BkkBonanza on 2010-09-26
You're kidding right?

Look at the label there - it's a 480V unit. You won't even be able to plugin that in unless you rent a warehouse and get an industrial 480VAC line installed.

Ha ha, that looks great though. Need a flatbed truck to take it home...

---

### Post by ts230 on 2010-09-26
> **BkkBonanza said:**
> You're kidding right?

Look at the label there - it's a 480V unit. You won't even be able to plugin that in unless you rent a warehouse and get an industrial 480VAC line installed.

Ha ha, that looks great though. Need a flatbed truck to take it home...

No, not kidding at all. I might just sell it later on for a few thousand bucks lol, but I'm gonna try to get that thing to work.

---

### Post by ts230 on 2010-09-26
> **ts230 said:**
> No, not kidding at all. I might just sell it later on for a few thousand bucks lol, but I'm gonna try to get that thing to work.

Or not. Slight change in plans - that thing is too huge to fit anywhere :P
Maybe some other time, but I'll get the small one for now. Start small.

---

### Post by CharlesA on 2010-09-26
> **ts230 said:**
> Or not. Slight change in plans - that thing is too huge to fit anywhere :P
Maybe some other time, but I'll get the small one for now. Start small.

There's no way you'd need a UPS that requires 480V AC in. That's an enterprise class UPS that needs a special power outlet.

The 450VA UPS that I have on my server lets it run for about 7 minutes before shutting down.

---

### Post by ts230 on 2010-09-26
> **CharlesA said:**
> There's no way you'd need a UPS that requires 480V AC in. That's an enterprise class UPS that needs a special power outlet.

The 450VA UPS that I have on my server lets it run for about 7 minutes before shutting down.

I was actually thinking of re-wiring the UPS's internals for it to run at 240 V, since the batteries store the whole voltage, could probably been done by removing half the batteries,
Anyways, the one I'm gonna be ordering tomorrow (along with a 2 TB hard drive and SATA cables) is 450 VA too, and hopefully, if the chart on APC's website is correct, allow my server to run for about 15 minutes until shutting down. Since there is no point in having the router and modem on, I set this in the config file:
```
# If KILLDELAY is non-zero, apcupsd will continue running after a
# shutdown has been requested, and after the specified time in
# seconds attempt to kill the power. This is for use on systems
# where apcupsd cannot regain control after a shutdown.
# KILLDELAY <seconds>  0 disables
KILLDELAY 35
```
So, now 35 seconds after a shut down was initiated, is it going to cut the power from the UPS to the server and friends? And, when the power is returned, will the UPS just click back on and the server too?

---

### Post by BkkBonanza on 2010-09-26
I think the UPS will but whether your server does depends on your BIOS settings. You can usually set it for "last-state", "no", "always" - or along those lines.

For a graceful shudown it won't normally start again with power-on unless you explicitly set it to "always power up" when power is applied. I'm not even sure that works as I've got mine set for "last-state" - good for a power cut but not for graceful shutdown as last-state is off.

I think you'll need to test out your own BIOS options.

---

### Post by SeijiSensei on 2010-09-26
I had a Dell server recently lose power, and the BIOS was set to stay off after power is restored.  I don't believe I ever changed that setting, so it came that way from the factory.  Seemed like the wrong default to me, as I had to go across town and physically restart the machine.

---

### Post by CharlesA on 2010-09-26
> **SeijiSensei said:**
> I had a Dell server recently lose power, and the BIOS was set to stay off after power is restored.  I don't believe I ever changed that setting, so it came that way from the factory.  Seemed like the wrong default to me, as I had to go across town and physically restart the machine.

It's actually a good thing to have it set that way. If the machine is on before the UPS has a chance to charge and you have another power problem, the machine could just power off without any backup power.

---

### Post by ts230 on 2010-09-27
OK, now I'm wondering if I can just hibernate the server instead of shutting it down, and then when the UPS gets power again, wake it up. Maybe some kind of interrupt from USB? 

If I remember, there was a line on the serial port (or was it the parallel port?) that you could pull high and it would simulate the press of the power button.

---

### Post by BkkBonanza on 2010-09-27
I find hibernate/suspend too finicky but you may have better luck. You just change your script to run those commands instead of poweroff. To test you don't need any signals - just pull the ups power cord (from the wall) or push the power button - that simulates losing power really well. Your UPS should notify your system via USB, which will respond correctly or not.

Assuming you config apcupsd to work with your UPS and do what you want.

---

### Post by R.Bucky on 2010-09-27
I recently purchased a 900VA unit for $99 from TigerDirect [[http://nbbl.it/j]("http://nbbl.it/j")]. This setup runs my i7, backup driver, and associated router software. The APC software does not have a Linux version, however based on the Windows GUI, I have a safe 30 minutes of power. Start small and upgrade when necessary. 110V is the way to go!

---

### Post by ts230 on 2010-09-27
> **BkkBonanza said:**
> I find hibernate/suspend too finicky but you may have better luck. You just change your script to run those commands instead of poweroff. To test you don't need any signals - just pull the ups power cord (from the wall) or push the power button - that simulates losing power really well. Your UPS should notify your system via USB, which will respond correctly or not.

Assuming you config apcupsd to work with your UPS and do what you want.

Yes - but that's not what I mean. I want to if the server was shut down because the UPS batteries were nearly empty and power comes back again, it should just turn power on the server, aka simulate a power button press on the server. Maybe I need to change wiring inside the Server so that the power button is hooked up to... something.

---

### Post by BkkBonanza on 2010-09-27
Ah, I see what you mean. You'll have to test your BIOS settings. If it boots with power-on then Ubuntu should know it was hibernated last shutdown and wake from that instead of a normal boot. It usually checks for a hibernate file during the boot up.  It's only the shutdown step that needs to be adjusted. I'm speaking from theory as I haven't set my server up that way (and my laptop is notoriously bad at this).

---

### Post by ts230 on 2010-09-27
Well, due to me needing to get more power for the server, and having to buy it off of eBay (you rule 5% rebates!) I will be getting [this UPS.]("http://cgi.ebay.com/TRIPP-LITE-1000-VA-BATTERY-BACKUP-UPS-G1000U-/370437495216?pt=LH_DefaultDomain_0&hash=item563fcb99b0#ht_3055wt_1139") Does Ubuntu have support for it?

---

### Post by CharlesA on 2010-09-27
Not a clue. I've only ever heard of the APC one.

---

### Post by BkkBonanza on 2010-09-28
Tripp-Lite is well known but I don't know about Linux support.

I found [this page]("http://www.tripplite.com/en/company/media-relations/release.cfm?txtPressID=965") saying they have support but I didn't research further to see what models may or not be covered. 

Google...  [tripp lite ubuntu]("http://manpages.ubuntu.com/manpages/dapper/man8/tripplite_usb.8.html")

[Tripp Lite docs]("http://www.tripplite.com/en/products/Specialty-Products.cfm?MDLID=4164") say it has USB and Power Alert software.

I hope that was you that just bought it... good deal, 1000VA for $39 inc. shpg. Hope that works out well for you. You may end up having to replace the battery but even so it may be an ok deal.

---

### Post by ts230 on 2010-09-28
> **BkkBonanza said:**
> Tripp-Lite is well known but I don't know about Linux support.

I found [this page]("http://www.tripplite.com/en/company/media-relations/release.cfm?txtPressID=965") saying they have support but I didn't research further to see what models may or not be covered. 

Google...  [tripp lite ubuntu]("http://manpages.ubuntu.com/manpages/dapper/man8/tripplite_usb.8.html")

[Tripp Lite docs]("http://www.tripplite.com/en/products/Specialty-Products.cfm?MDLID=4164") say it has USB and Power Alert software.

I hope that was you that just bought it... good deal, 1000VA for $39 inc. shpg. Hope that works out well for you. You may end up having to replace the battery but even so it may be an ok deal.

Well ****, someone grabbed it before me >_<
I guess it's off to spending another morning searching for another UPS tomorrow... or my dad might've just bought it without telling me.

Now, I'm probably gonna go and get [this one.]("http://cgi.ebay.com/New-Tripp-Lite-ECO550UPS-550VA-Energy-Saving-UPS-System-/180554848790?pt=PCA_UPS&hash=item2a09e85a16#ht_703wt_1139") It's not 1000 VA, mind you, but it'll be fine for what I'll need it. The server's getting a new power thingy anyways, and that new one will only be about 100 watts under full load.

---

