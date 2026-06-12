---
title: "Firefox ipfuk proxy"
date: 2010-07-16
forum: Security
---

### Post by yeleek on 2010-07-16
Interesting article - rude name.

[http://pentestit.com/2010/07/15/ipfuk-ip-address-personnal-data/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+PenTestIT+%28PenTestIT%29](http://pentestit.com/2010/07/15/ipfuk-ip-address-personnal-data/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+PenTestIT+%28PenTestIT%29)

---

### Post by HermanAB on 2010-07-16
Hmm, it only adds an X-forwarded-for header.  Each packet still has the real IP address.  So this is quite useless.

---

### Post by yeleek on 2010-07-16
Not aimed at being a Tor replacement...  as it says 

'This is a proof-of-concept to show that IP addresses can easily be spoofed and no taken as an evidence.'

I see that as an easy quick example to show non-techy management.

---

### Post by OpSecShellshock on 2010-07-16
Wait, so this is spoofing-spoofing? Fantastic! Although in most cases the Plaintiffs in US civil trials don't care as much whether they've got the right person--they just want someone who'll settle in order to save what it would cost to challenge the complaint.

---

### Post by bodhi.zazen on 2010-07-16
> **yeleek said:**
> Interesting article - rude name.

[http://pentestit.com/2010/07/15/ipfuk-ip-address-personnal-data/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+PenTestIT+%28PenTestIT%29](http://pentestit.com/2010/07/15/ipfuk-ip-address-personnal-data/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+PenTestIT+%28PenTestIT%29)

Just curious, did you click the download link ?

---

### Post by cariboo on 2010-07-16
I'm not sure I would trust this addon, as it isn't in mozilla's addon repository, and the link leads to a spam site.

---

### Post by lovinglinux on 2010-07-17
> **cariboo907 said:**
> I'm not sure I would trust this addon, as it isn't in mozilla's addon repository, and the link leads to a spam site.

In fact it is at [https://addons.mozilla.org/en-US/firefox/addon/176007/](https://addons.mozilla.org/en-US/firefox/addon/176007/)

But I wouldn't trust it, since it hasn't been reviewed by Mozilla editors.

---

### Post by bodhi.zazen on 2010-07-17
> **lovinglinux said:**
> In fact it is at [https://addons.mozilla.org/en-US/firefox/addon/176007/](https://addons.mozilla.org/en-US/firefox/addon/176007/)

But I wouldn't trust it, since it hasn't been reviewed by Mozilla editors.

That extension has a similar function, but different name (ipFlood vs ipfu*k).

I would not trust either one.

---

### Post by lovinglinux on 2010-07-17
> **bodhi.zazen said:**
> That extension has a similar function, but different name (ipFlood vs ipfu*k).

I would not trust either one.

Despite having different names, they both link to the same site.

I would not trust either one either.

---

### Post by bodhi.zazen on 2010-07-17
> **lovinglinux said:**
> Despite having different names, they both link to the same site.

I would not trust either one either.

Oh, OK , thanks for that.

My interest in this extension is low, I think it should be "reported" to mozilla as suspect.

---

### Post by lovinglinux on 2010-07-17
> **bodhi.zazen said:**
> My interest in this extension is low, I think it should be "reported" to mozilla as suspect.

I disagree. Unless you inspect the code and find something harmful there. Then you should definitely report it. 

I took a look into the code and I couldn't find anything suspicious. In fact is a very simple extension.

---

### Post by yeleek on 2010-07-19
I don't disagree re suspicious sites/extension.

I personally found this article interesting because increasingly irl I am hitting political barriers as decision makers accept the need to lockdown a users machine (to stop the installation of malicious software) but stop short of locking down the browser (because it needs access to unsigned dev box 'x' and lockdowns may break it).  

To my mind the browser itself can become a malicious tool, extensions like this, groundspeed, tamperdata, xss me, etc take your simple web browser to a whole other level....  and all this quite possibly within your LAN and out of site of any perimeter IDS/IPS.

---

