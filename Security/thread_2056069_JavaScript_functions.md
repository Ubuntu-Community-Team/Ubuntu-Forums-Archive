---
title: "JavaScript functions"
date: 2012-09-10
forum: Security
---

### Post by mike acker on 2012-09-10
while doing a little excessive thinking :confused: I started to wonder: what all functions are available in JavaScript?

In a WebBrowser (Firefox) we can hit save page as - and Firefox will allow us to browse the user account's home libraries - and the files within

this of course is implemented by system function calls - for the directories and contents...

if that function is available to JavaScript then a "script" should be able to carry out a thorough inventory of a client PC ...

unless the Browser's "Sandbox" prevents this ...

I'll be assigning myself to JavaScript kindergarten . in the mean time any helpful hints - will be appreciated :redface:

---

### Post by wacky_sung on 2012-09-12
If the webpage you are viewing using java script, you can actually right click your mouse and view source of all html including the java script. 

This will be interesting if you went to a phishing site which you can trace the scumbag email address otherwise it is hidden through their script.

---

### Post by offgridguy on 2012-09-12
> 

This will be interesting if you went to a phishing site which you can trace the scumbag email address otherwise it is hidden through their script.

Very interesting, I must try this.

---

### Post by mike acker on 2012-09-26
I think I should be addressing Java moreso than JavaScript

There was this article [http://www.scmagazine.com.au/News/316926,new-critical-oracle-java-vulnerability-found.aspx](http://www.scmagazine.com.au/News/316926,new-critical-oracle-java-vulnerability-found.aspx)

this morning discussing more newly found problems with Java. as usual we are advised to disable the Java plug-in in our browser . Based on this I think the functions I'm worried about are more part of Java rather than JavaScript

which leads to the question: **what other "web tools" can be hazardous? **any "plug-in" obviously. or,.... has anyone bought an MP3 from Amazon lately? they immediately want to install a music player for you .   yuck, I need to try the Ubuntu music store!!

my thinking continues to be: It's most likely best to simply set up a separate ordinary user for General Surfing . this should give the needed isolation -- even when Java's sandbox fails

once this philosophy is adopted one would then give some thought to exfiltrating documents from that General Surfing area... anything in there could be packing trouble... So you would share a directory OUT of the General Browser and not allow the General Browser to share into any outside directory

---

### Post by CharlesA on 2012-09-26
Javascript can be exploited was much as java can. I saw a site where there were ads at the bottom of the page - hidden with javascript. This was a storefront site and I tried to email the webmaster, but their web form failed. Needless to say, I didn't bother buying from them.

I run noscript on my boxes, even if it can be a pain in the butt sometimes.

---

### Post by mike acker on 2012-09-28
> **CharlesA said:**
> Javascript can be exploited was much as java can. I saw a site where there were ads at the bottom of the page - hidden with javascript. This was a storefront site and I tried to email the webmaster, but their web form failed. Needless to say, I didn't bother buying from them.

I run noscript on my boxes, even if it can be a pain in the butt sometimes.

hmmmmmm,... 40 on the NoScript -- adblock+ as well & flashblock

my thinking is that the quickest way for me to deal with the security problem is to simply use a separate ordinary log-on for General Surfing.  The activity resulting from whatever is thrown at the browser will then be confined to that one account.

---

### Post by CharlesA on 2012-09-28
Apparmor/selinux work wonders for confining Firefox, as well.

---

