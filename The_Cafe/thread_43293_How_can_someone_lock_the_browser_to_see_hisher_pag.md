---
title: "How can someone lock the browser to see his/her page?"
date: 2005-06-21
forum: The Cafe
---

### Post by sonny on 2005-06-21
Hi, the other day I installed Linux on my grilfriend's box, she had XP but she has grow tired of viruses, malware, and the like, her mother uses the PC with only ONE porpuse, to par TAXES, she does that through the bank's web-page ([www.banamex.com)](www.banamex.com)), but the page where is the tax-payments ([www.bancanet.com](www.bancanet.com)) doesn't support firefox; at least in Linux cuz my girlfriend had firefox with windows and had no problems whatsoever, my question to the community is, HOW can someone block the web-page to only work with IE or Netscape? and what would they win with this?, is there a way to make this problem dissapear?. I have sent an e-mail to the bank because I find this outrageous.

PS: I manage to make it work, by installing Netscape Browser with CrossOver, and then downloading the Java plugin for Windows and installing it through CrossOver, but it took me ages to make it work, cuz it's not THAT quite easy, cuz IE won't open the tax-payment page; it would open the bank's page. though. I though that installing Opera under Linux would be enough, but the browser doesn't display the page either. I'm furious with the bank, cuz it's suppose to be one of the biggest in Mexico, I have never had this problem before, I heard of this, but I just never had it.

Ok, this was just like going to the psychologist...  :razz:

---

### Post by Nu-Buntu on 2005-06-21
Sonny,

Perhaps the bank uses a Java applet. Have you tried installing any Java plugins?

---

### Post by sonny on 2005-06-21
[QUOTE=sonny]I manage to make it work, by installing Netscape Browser with CrossOver, and then downloading the Java plugin for Windows and installing it through CrossOver,[/QUOTE]
I did... but thats not the point, the point is that you should be able to see it through firefox or konqueror, or whatever browser you use...

---

### Post by Nu-Buntu on 2005-06-21
I was thinking more of native Java plugins for Firefox in Linux. I am just speculating, and you know where that can lead!  :???:

---

### Post by sonny on 2005-06-21
If you have firefox under Linux, go to [www.bancanet.com](www.bancanet.com), and tell me what you get..

---

### Post by compmodder26 on 2005-06-21
Just about every web programming language has browser sniffing capabilities.  Just download the User Agent Switcher extension for firefox and make the site think that your using IE or Netscape.

---

### Post by poofyhairguy on 2005-06-21
[QUOTE=sonny]If you have firefox under Linux, go to [www.bancanet.com](www.bancanet.com), and tell me what you get..[/QUOTE]


A site that says:

you must use IE or netscape (I guess, I can't read that language)..


It will work with this firefox pluggin:

[http://extensionroom.mozdev.org/more-info/useragentswitcher](http://extensionroom.mozdev.org/more-info/useragentswitcher)

---

### Post by sonny on 2005-06-21
Nice... I didn't know there was something like this... sweet.... I'll try this as soon as I get home, and install it in my box... does it work for ALL pages like this? or just with some??

---

### Post by jeremy on 2005-06-22
The plugin should work fine, but I suggest you contact the bank and complain that their website does not work with firefox on linux, even threaten to take your business elsewhere unless they fix it.

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=sonny]Nice... I didn't know there was something like this... sweet.... I'll try this as soon as I get home, and install it in my box... does it work for ALL pages like this? or just with some??[/QUOTE]

It will make ALL pages think you are using IE if you want.

---

### Post by TravisNewman on 2005-06-22
[QUOTE=poofyhairguy]It will make ALL pages think you are using IE if you want.[/QUOTE]
 however, if there is IE only code there, it still won't work, even if it thinks you are using IE. Essentially, IE has a lot of broken implementations of standards that people have essentially started writing FOR instead of against. It's an annoying problem with no easy fix.

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=panickedthumb]however, if there is IE only code there, it still won't work, 
[/QUOTE]

Or a site that wants ActiveX (shudders). I recently installed Internet Explorer on my Ubuntu box because I need activex to register for summer school.

---

### Post by phen on 2005-06-22
does that make sense? can netscape display activex? netscape=mozilla=firefox, i think it could work (allthough my equal signs are not 100% true :-)

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=phen]does that make sense? can netscape display activex? [/QUOTE]

I think so...

---

### Post by TravisNewman on 2005-06-22
you have to have the activex plugin, or use the netscape browser for windows that lets you use IE's rendering engine

---

