---
title: "Firefox hogging bandwidth"
date: 2012-04-05
forum: Security
---

### Post by SVWander on 2012-04-05
I don't know which forum to write to but I believe it is a security issue. Opening Firefox within a few moments a site qwest.net hogs all my bandwidth. I close Firefox and open another browser and my bandwidth returns to normal. I have tried to figure out what the problem is but don't know what I am doing. I have used etherape to local the site but don't know where to go from there. Can anyone help me with this problem?

---

### Post by CharlesA on 2012-04-05
Does it try to load qwest.net? That's the site of an ISP.

Check your startup page settings.

---

### Post by SVWander on 2012-04-05
No, I am not navigating to or trying to load qwest.net. A minute ago I started etherape, closed Chrome and opened Firefox. Within seconds my bandwidth was soaked up as you can see in the attacked jpg. This time I couldn't determine whether it was qwest.net and I didn't want to leave Firefox on long. After closing Firefox I reopened Chrome and etherape showed normal operation. 


> **CharlesA said:**
> Does it try to load qwest.net? That's the site of an ISP.

Check your startup page settings.

---

### Post by CharlesA on 2012-04-05
Try loading qwest.net in chrome and see what happens.

Also, check the startup page in firefox. It's likely that it is trying to load that when it starts up.

---

### Post by SVWander on 2012-04-05
Loaded qwest.net in Chrome and it operated normally. Dropping off the graph when I closed the site. 

Startup page was listed as . . . damn I forgot but it wasn't a website. It starts with a blank page. However I have it to load my previously pages when opening. None being qwest.net. Again opening Firefox ate up all my bandwidth. All going to:
63-235-20-209.dia.static.qwest.ne
I change the startup page to [www.weather.gov](www.weather.gov) and see what will happen with that. Could this be a security threat? It has me a little paranoid!  


> **CharlesA said:**
> Try loading qwest.net in chrome and see what happens.

Also, check the startup page in firefox. It's likely that it is trying to load that when it starts up.

---

### Post by CharlesA on 2012-04-05
I doubt it's a security issue. Does it still do the same thing with the new site?

---

### Post by QIII on 2012-04-05
That's not .net, it's .ne, which is the domain for Nigeria.

---

### Post by CharlesA on 2012-04-05
I'm pretty sure it's qwest.net. I couldn't find any reference to qwest.ne.

---

### Post by SVWander on 2012-04-05
my mistake . . . when I copied and pasted I missed the "t".
I went back to check and now for the first time in a couple of days qwest.net isn't listed in etherape but now this site is taking over. 90.84.51.80 I can only keep Firefox open a few minutes because my cpu usage goes way up and I am afraid I'm going to damage this poor netbook. However the same problem existed on my desktop before reinstalling Ubuntu and reinstalling on another hard drive just in case.

> **QIII said:**
> That's not .net, it's .ne, which is the domain for Nigeria.

---

### Post by lisati on 2012-04-05
Is there any flash content (or similar) on the site?

---

### Post by QIII on 2012-04-05
Whew!  Glad it's .net and not some Nigerian Prince scam making your machine a zombie.

Can you stop the behavior by creating a new Firefox profile?

---

### Post by CharlesA on 2012-04-05
> **lisati said:**
> Is there any flash content (or similar) on the site?
That would be my thought, but I just checked qwest.net and there doesn't appear to be any flash content on it.

+1 to creating a new profile and see what happens.

---

### Post by SVWander on 2012-04-05
Which site? When I had Firefox open the last time it was on [www.weather.gov](www.weather.gov). I viewed the source code for weather.gov and didn't see any flash content listed. 

> **lisati said:**
> Is there any flash content (or similar) on the site?

---

### Post by CharlesA on 2012-04-05
> **SVWander said:**
> Which site? When I had Firefox open the last time it was on [www.weather.gov](www.weather.gov). I viewed the source code for weather.gov and didn't see any flash content listed.
The original site -qwest.net

---

### Post by SVWander on 2012-04-05
ME TOO! Actually that was my fear. Not the Nigerians but that someone was trying to take control of my machine.

I will try a new profile and let you know.


> **QIII said:**
> Whew!  Glad it's .net and not some Nigerian Prince scam making your machine a zombie.

Can you stop the behavior by creating a new Firefox profile?

---

### Post by SVWander on 2012-04-05
Expect for trouble shooting I never went to qwest.net.
I started firefox in safe mode. This time 90.84.52.192 sucked the life out of my machine. In whois it is listed as:
"AKAMAI-FT-US descr: Akamai Technologies - US machines Chicago connected to FT AS5511"
However Firefox was still on [www.weather.gov](www.weather.gov)!



> **CharlesA said:**
> The original site -qwest.net

---

### Post by QIII on 2012-04-05
Akamai is legit.  They serve up a lot of content for a lot of sites.

But they may have something gone rogue.

Try installing NoScript and see if it is a java script gone mad.

(Might even be something like an XSS attack)

---

### Post by SVWander on 2012-04-05
Installed noscript. Firefox is still on a rampage when opened. I have attached a jpg of the etherape while Firefox is running. This time it is back to the qwest.net site. Again once Firefox is closed all returns to normal. At the point the screenshot was taken the load had reduces slightly.



> **QIII said:**
> Akamai is legit.  They serve up a lot of content for a lot of sites.

But they may have something gone rogue.

Try installing NoScript and see if it is a java script gone mad.

(Might even be something like an XSS attack)

---

### Post by QIII on 2012-04-05
I didn't see whether you had created a new profile.

Did I miss that?

---

### Post by OpSecShellshock on 2012-04-06
Largely what I think is happening is that Firefox is checking for updates to add-ons immediately when it starts up. If there are a large number of add-ons and plugins it could cause quite a strain. Also if one of the extensions is a feed reader of some kind then it will tend to check for updates to all feeds. My suggestion would be to disable all add-ons (extensions and plugins) and then start Firefox again and see what happens.

---

### Post by SVWander on 2012-04-06
Nope I missed that step. That did the trick! Thanks so much for your help.

> **QIII said:**
> I didn't see whether you had created a new profile.

Did I miss that?

---

### Post by SVWander on 2012-04-06
When I started firefox in safe mode with all add-ons disabled it didn't help. For some reason changing the profile help and ended the problem.


> **OpSecShellshock said:**
> Largely what I think is happening is that Firefox is checking for updates to add-ons immediately when it starts up. If there are a large number of add-ons and plugins it could cause quite a strain. Also if one of the extensions is a feed reader of some kind then it will tend to check for updates to all feeds. My suggestion would be to disable all add-ons (extensions and plugins) and then start Firefox again and see what happens.

---

