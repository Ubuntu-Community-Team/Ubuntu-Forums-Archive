---
title: "Firefox 3 + Windows + malicious javascript"
date: 2008-07-22
forum: Security
---

### Post by sefs on 2008-07-22
Hey I came across a website today that had malicous javascript code in it.

I've saved the script and sent it off to avast. Because I am sure some of what was being downloaded was undetected, while some were being detected as trojans and rootkits etc.

The script was pulling this stuff down from an IP different than the hosted site, so it was clear they were compromised somehow.

My question is no prompts were given ... that stuff just started to download all of its own without user intervention.  

I was on FF3 and I thought FF3 took care of that.  Had I been running noscript which i usually do it would not be a problem but i had noscript off at the time.

the javascript looks like some form of cypher, i could see the use of functions like unescape etc.

Is there somewhere to decode the script to see exactly what IP it was pulling this stuff down from?  I didnt have the mind at the time to write down the suspect IP when i saw it in the status bar.

---

### Post by calraith on 2008-07-22
> **sefs said:**
> I was on FF3 and I thought FF3 took care of that.  Had I been running noscript which i usually do it would not be a problem but i had noscript off at the time.

the javascript looks like some form of cypher, i could see the use of functions like unescape etc.

Is there somewhere to decode the script to see exactly what IP it was pulling this stuff down from?  I didnt have the mind at the time to write down the suspect IP when i saw it in the status bar.

I dunno about whether it should have been disallowed by FF3 or not; but if you'd like to decode the script, [this page looks promising]("http://code.gosu.pl/dl/JsDecoder/demo/JsDecoder.html"), or maybe [this one](http://www.netdemon.net/haywyre/). Google is just [full of good ideas](http://www.google.com/search?q=decode obfuscated javascript).  If nothing else, you could paste that javascript into a vanilla HTML file, replacing document.write / eval / location / submit() / whatever could potentially redirect your browser or do a postback, with "alert" or "document.getElementsByTagName('textarea')[0].value =" (assuming you include a textarea in your vanilla HTML).

---

### Post by kajillin on 2008-07-23
... it was probly off an anonymous proxy, if there smart.....

---

### Post by WastePotato on 2008-07-27
To prevent this from happening in the future you should use this add on for Firefox:

[NoScript :: Firefox Add-ons (Link)]("https://addons.mozilla.org/en-US/firefox/addon/722")   :)

---

