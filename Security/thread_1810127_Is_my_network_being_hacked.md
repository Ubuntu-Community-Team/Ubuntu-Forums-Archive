---
title: "Is my network being hacked?"
date: 2011-07-22
forum: Security
---

### Post by luismgl on 2011-07-22
Up to recently I never had problems with wireless internet connection on any computer of the house until now, every time I enable wireless on my router, the speed and ping go from the usual 9Mb/s 30ms to 1Mb/s 120ms, the upload remains 1Mb/s in both cases. These speed tests were done with full wireless signal and with cable while with only one computer on-line, and of course, the referred computer didn't have any P2P or any application of sorts on.

I already called my ISP's costumer support and according to them I'm receiving the speed I'm paying for, which is 8Mb/s.

to sum it up, when wireless is on, speed is low, so I'm wondering if some undesired individual may have discovered my wireless lan key and is using my internet for free. 

My router is a Kozumi KM-410WG and the tests have been done on a Windows 7 32 bit computer.

Thank you.

---

### Post by 3Miro on 2011-07-22
Doesn't your router have a log about who's going on-line? I had messed up my router settings once and the result was that some jerk went on-line and started downloading who-knows-what slowing down my traffic big time. Check your logs, they will tell you if someone else is on.

---

### Post by Dangertux on 2011-07-22
It's possible.

Things you can do to find out.

- Change your WPA Key (you should be using WPA not WEP). 
- Check your wireless AP's logs, they should show who authenticated to the AP.
- Watch your network traffic with a program like wireshark, kismet, tcpdump etc (note doing this after changing your WPA key will likely yield nothing)

Personally, I think it's more likely an issue with your wireless. Usually wireless will get poorer performance then wired networking.

---

### Post by Dustin2128 on 2011-07-22
Wpa2>wpa.

---

### Post by ZarathustraDK on 2011-07-22
Seconding/thirding the "someone is piggy-backing" off of your router, theory.

Try (unless you have customized your router settings, in which case you have to remember those) to do a full reset just for safety (the intruder may have changed the settings on your wireless router through the ol' look-up-the-factory-default-password routine, and if you're not used to mingling about with your router, you might miss those modified settings).

Next, if possible, whitelist the MAC-adresses of your internet-connected devices on your router configuration-page. Other devices, other than the ones you've whitelisted, will not be able to use your router to download "stuff". If you can not whitelist, then blacklist all the MAC-adresses in your log (also on the router-configuration-page) that you don't recognize

On the other hand, if you wish to download "stuff" there are nice online services available to provide that anonymity for you, TOR being one, your own neighboors wifi, for sweet revenge, being another ;)

---

### Post by luismgl on 2011-07-25
First of all thank you for all your answers.

I have ruled out the possibility of being hacked since after more testing with the wireless signal disabled on the router, my connection was still slow, also because there were no devices showing on my router besides one, which was obviously the computer that was on.

Since the problem was presistant I decided to call on my ISP costumer service yet again (27 min call :@ ) and it seems that my router is to blame for the lack of speed and big ping. From what they told me, services of 8 or more Mb/s require ADSL2+ and even though my router has it, they seems like its connecting to them through ADSL2. Now, ever since configuring my router for the first time about 10 months ago, I have never changed any configuration and have never had problems with slow speed up until recently, so could it really be my routers fault, or have I just been hit with sand on my eyes?

This is my current ADSL configuration:
[[IMG]http://img811.imageshack.us/img811/8300/shotz.th.jpg[/IMG]]("http://imageshack.us/photo/my-images/811/shotz.jpg/")

Thank you.

---

### Post by Dangertux on 2011-07-25
> **Dustin2128 said:**
> Wpa2>wpa.

WPA2 is cracked in exactly the same method as WPA...

Meaning the real difference between WPA and WPA2 is simply the use of CCMP vs TKIP, which increases the number of operations required to brute force a pass phrase. However, as long as the passphrase is not weak TKIP can still be considered secure.

Both WPA/2 if set to use PSK will be vulnerable to dictionary and brute force attacks, as opposed to the statistical attacks that WEP is vulnerable to.

Also to the TS, did you try disabling the router from connecting via any method other than ADSL2+?

---

### Post by luismgl on 2011-07-25
> **Dangertux said:**
> 
Also to the TS, did you try disabling the router from connecting via any method other than ADSL2+?

I did, this resulted in no interenet connection whatsoever. I tried combinations like ADSL2+ and T1.413 and had really slow speeds

---

