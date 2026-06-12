---
title: "Firefox vs Chrome - Download speed"
date: 2019-01-31
forum: Ubuntu, Linux and OS Chat
---

### Post by makitso on 2019-01-31
I recently upgraded my internet connection speed to 100Mbps.  After doing so I tested the download performance using speedtest.net for both Chrome and Firefox.
I was surprised to see that FF started about 75Mbps and then rose to 98Mbps.  However, Chrome started at about 75Mbps and dropped to 60Mbps.  I tested on several systems and the results are the same.
Both browsers had no extensions.  Tried a Win10 machine and the results are about the same.  

Any insight as to why Chrome is slower?

Firefox Version 65 
Chrome Version 72

---

### Post by ajgreeny on 2019-01-31
Just as a comparison, have you also tried open-source chromium, on which chrome is based, but without any google branding; it always shows me the same speeds as FF when I use speedtest though not as fast as yours.

I have a 38Mb/s connection and regularly get 37Mb/s in speedtest with both browsers.

---

### Post by yetimon_64 on 2019-02-02
> **ajgreeny said:**
> ... it always shows me the same speeds as FF when I use speedtest though not as fast as yours...
My networking is very variable in speeds being via an android mobile phone with a mobile 4G plan. I have seen the phone max out at 130 Mb/s though typical phone speeds are 60 to 75 Mb/s (network loading dependent). Generally my devices including my laptop max out at about 50 Mb/s when connecting through the phone supplied access point, usually the download speeds are much lower at about 20 to 25 Mb/s.

On my laptop Trusty 14.04 install here I have 4 browsers installed; chromium-browser, firefox quantum-esr (currently v.60.5), firefox quantum (currently v.65.0) and google chrome stable.

Using the speedtest.net site, the open source chromium browser is consistently the fastest with firefox quantum-esr  coming in second. With testing conditions the same for all browsers google chrome stable is consistently last average speed wise but also seems to show the greatest speed variation from test to test.

I tend to use chromium browser if I want the most consistently fast downloading; if I want "all the bells and whistles" (extension wise) I use firefox quantum-esr as it is also reasonably speedy with downloads. The standard firefox quantum browser here is significantly lower in speed to chromium, averaging about 60% of the speed of chromium, it and google chrome stable tend to be my least used browsers.

I only have google chrome stable here for screen casting with a google chromecast device attached to my TV, though I recently discovered the open source chromium browser can also do the same. I'll probably keep google chrome installed though it gets only occasional usage.

@ makitso,
> Chrome started at about 75Mbps and dropped to 60Mbps.  I tested on several systems and the results are the same.
I haven't noticed such a speed dip here with google chrome, it shows a very similar profile to the other browsers but tends to be slower in general. That may be as a result of the type of connection I am testing over...maybe, I don't know for certain though.

Cheers, yeti.

---

### Post by walts48 on 2019-02-03
Is Speednet really a test of the browser or the Internet connection? One browser could have better speeds due to internet traffic.

Try a real browser test. 

[https://browserbench.org/](https://browserbench.org/)

---

### Post by yetimon_64 on 2019-02-03
> **walts48 said:**
> Is Speednet really a test of the browser or the Internet connection? One browser could have better speeds due to internet traffic.

Try a real browser test. 

[https://browserbench.org/](https://browserbench.org/)

Sounds interesting, I'll have to try your link tomorrow and run all 4 browsers with it. Has me wondering but I need to get some sleep at the moment, one for checking later on :-). Cheers, yeti.

---

### Post by VMC on 2019-02-03
[COLOR=#000000]&#8203;Result using ARES. Then again I'm sure system speed comes into play as well as internet speeds. I've got basic $15 Spectrum.[/COLOR]
[COLOR=#000000][B]
Chrome:
[/B]Overall[/COLOR]
[COLOR=#000000]63.27±2.30ms

[/COLOR][B]Firefox:
[/B]Overall
170.86 ±13.05ms




[COLOR=#000000][Thank you @Walts for the link][/COLOR]

---

### Post by VMC on 2019-02-09
I couldn't believe the above results, so ran Chrome again just to be sure:
Overall
62.54 ±2.40ms

It was even faster than before.

---

