---
title: "Virus?"
date: 2012-09-22
forum: Security
---

### Post by Gazucha on 2012-09-22
Hi all,

was just following some links relating to documented  evidence of Governmental knowledge and involvement in Chemtrails when my  Firefox browser froze and my cpu fan went crazy...

I have restarted, and now my Firefox won't refresh and something has definitely changed for the worse.

Have I been bugged in some way?

How can I find out?

Any help will be great.

~ Gaz

x

---

### Post by Gazucha on 2012-09-22
Just for the record...

the pages I was on were..

[http://www.infowars.com/information-for-chemtrail-skeptics/](http://www.infowars.com/information-for-chemtrail-skeptics/)

[http://www.usatoday.com/tech/science/environment/2011-02-25-geoengineering25_CV_N.htm](http://www.usatoday.com/tech/science/environment/2011-02-25-geoengineering25_CV_N.htm)

[http://www.usatoday.com/tech/science/environment/2011-02-25-geoengineering25_CV_N.htm](http://www.usatoday.com/tech/science/environment/2011-02-25-geoengineering25_CV_N.htm)

[http://www.infowarsshop.com/WHY-In-The-World-Are-They-Spraying_p_698.html](http://www.infowarsshop.com/WHY-In-The-World-Are-They-Spraying_p_698.html)

is it because I visited infowars.com?

is it even possible?

~ Gaz

---

### Post by PaulInBHC on 2012-09-22
Unless the govt is out to get you, I don't think it is a virus. Sounds more like a hardware problem. 

My wife visits infowars on occasion with a Windows computer and I just asked her if she ever got a warning from avast. Nope.

usatoday could have ads that are trying to track you but this should not have messed up your system.

---

### Post by dodo3773 on 2012-09-22
I just visited those pages without an issue. Try installing bleachbit and cleaning your firefox profile with it. It's hard to say where your problem stems from. Use something like noscript would probably not be a horrible idea though since there are probably something like 30+ scripts running on that page that you do not need to read the article.

---

### Post by akoskm on 2012-09-22
Browser freeze and CPU fan disorder according to my experiences means that something with a Flash applet went wrong.
[http://www.usatoday.com/tech/science/environment/2011-02-25-geoengineering25_CV_N.htm](http://www.usatoday.com/tech/science/environment/2011-02-25-geoengineering25_CV_N.htm) <- candidate

---

### Post by dcstar on 2012-09-22
> **akoskm said:**
> Browser freeze and CPU fan disorder according to my experiences means that something with a Flash applet went wrong.
[http://www.usatoday.com/tech/science/environment/2011-02-25-geoengineering25_CV_N.htm](http://www.usatoday.com/tech/science/environment/2011-02-25-geoengineering25_CV_N.htm) <- candidate

Page works fine on my system.

---

### Post by Bucky Ball on 2012-09-22
*Moved to **Security Discussions***

---

### Post by claracc on 2012-09-23
> 
[http://www.usatoday.com/tech/science/environment/2011-02-25-geoengineering25_CV_N.htm](http://www.usatoday.com/tech/science/environment/2011-02-25-geoengineering25_CV_N.htm) <- candidate

Using firefox 15.0.1, visited web page works well in my system, running applets without any problem.

what adobe flashplayer are you using?, and firefox version?, what is your graphics card?

---

### Post by akoskm on 2012-09-23
> **dcstar said:**
> Page works fine on my system.

Sure, here too. That was the only page using flash IIRC.
On my system happened a few times that pages using flash made my browser/CPU crazy.

---

### Post by wacky_sung on 2012-09-23
This can be malware attack which has already infested your system with any outdated plugins of your browser or browser. Otherwise use as what people has recommended.

---

### Post by Bucky Ball on 2012-09-23
Incidentally, are you using a supported release? What version?

---

### Post by Ms. Daisy on 2012-09-23
> **wacky_sung said:**
> This can be malware attack which has already infested your system with any outdated plugins of your browser or browser. Otherwise use as what people has recommended.
The OP has not provided enough information here to say if it's malware. (Yes it **could** be malware, but it **could** also be a hundred other things). Let's find out if the other solutions proposed in this thread solve the problem first.  When you leap to malware as the problem without sufficient evidence, you're just spreading FUD.

---

### Post by mike acker on 2012-09-23
re: Linux/Ubuntu browsing

I suggest using a separate, ordinary user account for browsing "in the wild"

use another ordinary user account for Secure Sites such as your Credit Union

Notes

1. take care to avoid exfiltrating documents from your Wild Account.

2. a browser -- or any program -- running in your Wild Account -- can't "see" anything other than the home directory libraries of that "Wild" account.

3. when you switch users,.... you'll get your own set of extensions to Firefox -- just as though you and your WildSide were on different boxes... 

When I tried this this morning.... when I switched user IDs Firefox had to update itself.  the isolation is pretty good.

~~
I've been playing with MySQL for the last few days; I still need to get back to my JavaScripts tests. What I expect to find is that a JavaScript, running in your browser -- can "see" everything that you -- as logged in -- can see. ie. I suspect a javascript can "inventory" your user account...   any comments ?

I've asked about this before but it would be Really Cool if the workspace tool would allow us to optionally re-logon in each "work space"

---

### Post by rookcifer on 2012-09-23
> **wacky_sung said:**
> This can be malware attack which has already infested your system with any outdated plugins of your browser or browser.

Extremely doubtful.

---

### Post by HartleyTom on 2012-09-23
I dont think that it's a virus , maybe it's problems of your firefox version ...

---

### Post by Gazucha on 2012-09-23
Thank you for all the responses and suggestions.

Fan is still running high.



What should I be looking to delete in Bleachbit?

---

### Post by Ms. Daisy on 2012-09-23
Have you read the [bleachbit documentation]("http://bleachbit.sourceforge.net/documentation/general-usage")? That would be a good place to understand what it will do. You want to delete cookies, clear history, & delete logs for Firefox (I'm assuming you're using Firefox. If not then please post what browser you're using).

Have you updated your system recently? If not do ```
sudo apt-get update && sudo apt-get upgrade
``` That will ensure you've got the latest version of Firefox. If things are funky with flash then you could give [Flash Aid]("https://addons.mozilla.org/en-us/firefox/addon/flash-aid/") a try. It doesn't always work on all hardware, but it worked for me personally.

If the fan is still running high then run ```
top
``` and see what process is eating up the CPU. If you don't understand the output of top then post it here and we can interpret it.

---

### Post by wacky_sung on 2012-09-23
> **rookcifer said:**
> Extremely doubtful.

Ah...what make you think so. If you think so, i can recommend you to go to a site for test. Any damage is not my responsibility. A simple java exploit which still out in the wild inspite patch has been release. In term of security, nothing is bullet proof but continuously improvement.

A simple [site]("http://viooz.eu/") like this seem harmless but you can find out the reason behind if you know it.:lolflag::lolflag:

Enter at your own risk.):P):P):P):P

---

### Post by rookcifer on 2012-09-23
> **wacky_sung said:**
> Ah...what make you think so. If you think so, i can recommend you to go to a site for test. Any damage is not my responsibility. A simple java exploit which still out in the wild inspite patch has been release. In term of security, nothing is bullet proof but continuously improvement.

A simple [site]("http://viooz.eu/") like this seem harmless but you can find out the reason behind if you know it.:lolflag::lolflag:

Enter at your own risk.):P):P):P):P

Lots of good movies there, but I didn't encounter a virus or an exploit of any kind.  Java didn't even run on that site.

---

### Post by Ms. Daisy on 2012-09-24
> **wacky_sung said:**
> Ah...what make you think so. If you think so, i can recommend you to go to a site for test. Any damage is not my responsibility. A simple java exploit which still out in the wild inspite patch has been release. In term of security, nothing is bullet proof but continuously improvement.

A simple site like this seem harmless but you can find out the reason behind if you know it.

Enter at your own risk. Are you seriously suggesting that the OP has been owned using a Java exploit? How do you even know that the OP has Java installed?  

Do you think that maybe it's a tad more responsible of you to find out if the OP even uses Java before you freak out about Java exploits?  Seriously dude. **Quit spreading FUD**.

---

### Post by rookcifer on 2012-09-24
> **Ms. Daisy said:**
> Are you seriously suggesting that the OP has been owned using a Java exploit? How do you even know that the OP has Java installed?  

Do you think that maybe it's a tad more responsible of you to find out if the OP even uses Java before you freak out about Java exploits?  Seriously dude. **Quit spreading FUD**.

I use Java (IcedTea) in my browser, but I have the Java plugin locked down with a custom AppArmor profile that is as restrictive as possible while still allowing the plugin to be functional.

---

### Post by Bucky Ball on 2012-09-24
***Thread Closed***

[I]**Reason: **Heresay, circular motion, at times bordering on OS bashing and original OP's issue has changed. 

* Gazucha changed to Tor browser and this rectified overheating and fan issues. [/I]


@Gazucha: Please start a new thread regarding your fan problem as that is what you are now wanting to solve and this thread title is not helpful as it has nothing to do with that. Thanks.

---

