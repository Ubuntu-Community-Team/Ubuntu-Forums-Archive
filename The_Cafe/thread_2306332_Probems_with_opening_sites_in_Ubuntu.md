---
title: "Probems with opening sites in Ubuntu"
date: 2015-12-14
forum: The Cafe
---

### Post by janeku2 on 2015-12-14
Couple of days I notice something strange: My E-republik web page wasn;t able to show normal but instead like web page where it links and pics are lost somewhere by the way and everthing looks like "the begining" (see picture).
I use 2 browsers (Firefox and Opera) running under 64bit Ubuntu 14.04.3 and both shows same problem loading Erepublik site or some other site.
To be shure I tried Live USB with Ubuntu and also I got the same problem.
Running Firefox and Opera under 32bit Ubuntu is ok, and page is opened normal.
I also tried Opera under Win 7 , to remove any suspicions about my ISP provider and everything was also fine and smooth.

Now the question is what made ubuntu and FF and Opera to act like that and to give some web sites with errors.
In attach is snapshot of this situation.

Regards,

---

### Post by Old_Grey_Wolf on 2015-12-14
I have encountered websites that have detected the OS and assumed I was using an Android phone. They offered a different format for a mobile device. It usually got corrected after a short period of time. It wasn't Ubuntu, the browser, or the ISP that was causing the problem. It was the website.

---

### Post by janeku2 on 2015-12-17
Hello,
I think I figure out what is the problem by chance. Looks like there is problem with cloudflare and it site protection rules. Personally I do not have such protection but what I did today solve my problem and point to cloudflare and it implementation in FF or even Ubuntu.
I tried to load item on my basic web site and I got same situation: blocking some links,pictures,etc. By chance I click on "open image" and i was forwarder to cloudflare security check. After completing captcha i was shown picture and voila', problem has gone. Everything was fine and web page load without problem with it all links and pics.
I tried this trick on Erepublik site and suddenly I got access to whole site and it was fully functional.
Now the question is WHY cloudflare has to block access to some site and make such a BIG problem ?
Why cloudflare is present in FF settings (about:config) on these two lines :
devtools.gcli.lodashSrc with this link: [https://cdnjs.cloudflare.com/ajax/libs/lodash.js/2.4.1/lodash.min.js](https://cdnjs.cloudflare.com/ajax/libs/lodash.js/2.4.1/lodash.min.js)
and
devtools.gcli.underscoreSrc with this link [https://cdnjs.cloudflare.com/ajax/libs/underscore.js/1.7.0/underscore-min.js](https://cdnjs.cloudflare.com/ajax/libs/underscore.js/1.7.0/underscore-min.js)
????
Intentionally it is there or somehow it comes there and make me nervous every time I see cloudflare security check captcha.
Is FF team aware of presence of these links and cloudflare problematic behaviour under Ubuntu ?

Regards,

---

### Post by Old_Grey_Wolf on 2015-12-17
I think you need to ask the FF people. This is a support forum of people that use Ubuntu. Developers rarely come here.

---

### Post by yoshii on 2015-12-18
There are free firefox addons to set a fake "user agent string" so that the website thinks you are running some common verion of windows and just lets you in instead of blocking or complaining.  

TotalSpoof is what I am using.  I have used others, but this is very easy and there's no configuration needed.  
[https://addons.mozilla.org/en-US/firefox/addon/totalspoof/?src=search](https://addons.mozilla.org/en-US/firefox/addon/totalspoof/?src=search)

---

