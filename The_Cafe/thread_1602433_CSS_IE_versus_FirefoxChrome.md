---
title: "CSS: IE versus Firefox/Chrome"
date: 2010-10-21
forum: The Cafe
---

### Post by sdlynx on 2010-10-21
Hello everyone,

I'm working on a website for my robotics team and I made it look just how I wanted on Firefox.  However, the CSS completely fails on Internet Explorer.  Does anyone have a better way to make this work on both Firefox and IE?  Here's the site: [http://powerhawks.org/derp2](http://powerhawks.org/derp2)

Thanks

---

### Post by kaldor on 2010-10-21
Not sure, but it looks awesome on OS X with Safari 5. There's your Mac testing done. :)

---

### Post by Spr0k3t on 2010-10-21
The best way to make it work on IE is to use the CSS hacks.  Design for everything else, then use a javascript if{} to import the IE "fixes".  If you code it for IE, then you will spend time on each other browser... it's best to just target everything but IE, then go back in and correct the industry-nonstandard browser.  There's a reason why the marketshare of IE is falling as fast as it is.

Also, put on your site: "This site works best in every internet browser with the exception of Internet Explorer".  Then provide links to comparisons of IE vs everyone else.

---

### Post by sdlynx on 2010-10-21
> **Spr0k3t said:**
> The best way to make it work on IE is to use the CSS hacks.  Design for everything else, then use a javascript if{} to import the IE "fixes".  If you code it for IE, then you will spend time on each other browser... it's best to just target everything but IE, then go back in and correct the industry-nonstandard browser.  There's a reason why the marketshare of IE is falling as fast as it is.

Also, put on your site: "This site works best in every internet browser with the exception of Internet Explorer".  Then provide links to comparisons of IE vs everyone else.

I think that sounds like a good idea, but nonetheless, I can't understand why my widths for divs are differen't in IE.  And, for that matter, it seems to have handled "top" and "left" wrong as well.  The biggest problem is that since I have javascript that alters CSS, if IE doesn't respond the same to a certain change in, say, "left" the layout will be messed up.

---

### Post by Darth Penguin on 2010-10-21
You can use [.htaccess](.htaccess) to detect the user agent and redirect people using Internet Explorer to a page designed for Internet Explorer.

[http://doctype.com/redirect-ie-browsers-htaccess](http://doctype.com/redirect-ie-browsers-htaccess)

Also, there are various Javascript and PHP browser detection and redirection scripts. Javascript being the least effective if the browser has Javascript disable, PHP and .htaccess are preferable. You can also redirect IE users to a page telling them to get Firefox if you want to skip the whole having to recode everything for IE.

---

### Post by Merk42 on 2010-10-21
> **sdlynx said:**
> I think that sounds like a good idea, but nonetheless, I can't understand why my widths for divs are differen't in IE.  And, for that matter, it seems to have handled "top" and "left" wrong as well.  The biggest problem is that since I have javascript that alters CSS, if IE doesn't respond the same to a certain change in, say, "left" the layout will be messed up.

[Fix your errors](http://validator.w3.org/check?uri=http://mylifeisnerdy.co.cc/Tests/derp.php&charset=(detect+automatically)&doctype=Inline&group=0)
Most notibly, your lack of a doctype.
This is making IE render in "quirks mode" which is why [the boxes are a different size](http://www.quirksmode.org/css/box.html)

Fix the code, IE will render in standards mode, and you won't have problems (well you may still have some).

---

### Post by Untitled_No4 on 2010-10-22
I'm with Merk42. Install the firefox HTML Validator ([http://users.skynet.be/mgueury/mozilla/](http://users.skynet.be/mgueury/mozilla/)) and fix your errors. It's likely that it will fix most of your problems. 
For all other IE-specific problems I then still have I use a condition as such:
```
<!--[if lt IE 8]>
<link type="text/css" rel="stylesheet" href="/styles/IE7.css" />
<![endif]-->

```
This means that if the browser is less than IE8, it will load another css file which has the specific fixes for IE7. It doesn't need to be the complete css file, just the elements that need fixing. This should be inserted under your <link> to your main css file.
I don't go as far as fixing everything for IE6. I've stopped supporting it about a year ago and my customers all understand that.

---

### Post by sdlynx on 2010-10-22
Wow, I just realized I hadn't put my doctype in, and some meta tags.

Nonetheless, thanks guys.  I ended up making a little ternary statement whenever I needed a different CSS value for IE and it works pretty well.

---

### Post by devondashla on 2010-10-23
> **sdlynx said:**
> Hello everyone,

I'm working on a website for my robotics team and I made it look just how I wanted on Firefox.  However, the CSS completely fails on Internet Explorer.  Does anyone have a better way to make this work on both Firefox and IE?  Here's the site: [http://powerhawks.org/derp2](http://powerhawks.org/derp2)

Thanks

I can't help you with IE, but it looks fantastic in Midori.

---

### Post by Strategist01 on 2010-10-23
That site looks very good! BTW, there's no apostrophe in "Chaiman's", as it's plural, not possessive. Sorry. Had to point that out. Works great under FF. But I think a link to direct people to a page to encourage them to get FF would be best...

---

### Post by Dr. C on 2010-10-23
Looks great on Firefox 3.6.11 on Ubuntu 10.04, but IE 6 on Windows 2000 mangles it badly.

---

### Post by MisterGaribaldi on 2010-10-23
> **Strategist01 said:**
> That site looks very good! BTW, there's no apostrophe in "Chaiman's", as it's plural, not possessive. Sorry. Had to point that out. Works great under FF. But I think a link to direct people to a page to encourage them to get FF would be best...

Not quite.

"Chairman's" is possessive. Like, for instance, "This is the Chairman's parking space."

Chairmen would be plural. Otherwise, it's a bit like saying "How many waters are in this glass?" It doesn't make proper grammatical sense.

Other than that, I really like the site's design. I've never seen anything done that way, and I have to admit I think it's a very novel approach to multiple pages. I'm not into coding or anything like that, but if I were to design a web site, I would strongly consider doing something similar. Very, very nice!

---

### Post by phrostbyte on 2010-10-23
Looks great! Can't wait to see the robot. :)

---

### Post by dionysius on 2010-10-23
I don't know about IE8, but it used to be the case that divs, especially divs with a border, would be calculated in a different way by IE. Whereas every other browser used to stick to the idea that if a div is say 100px wide, and you add a border of 2px, the total width of that div would be 104px. IE on the other hand would calculate a total width of 100px, leaving you effectively with only 96px of content, because it didn't add the border px but subtracted them from the overall width. 

This used to be, and probably still is, one of the most common 'quirks' of IE that requires a seperate stylesheet. So for IE (like I said, it may have been fixed in IE8 ) add the size of borders, the total size (so if it's a 2px border all round, add 4px) to the width and/or height of the divs you already got and ithat should correct IE's pigheaded obstinacy.

Site looks good in Opera 10.63 here :)

---

### Post by sdlynx on 2010-10-23
> **dionysius said:**
> I don't know about IE8, but it used to be the case that divs, especially divs with a border, would be calculated in a different way by IE. Whereas every other browser used to stick to the idea that if a div is say 100px wide, and you add a border of 2px, the total width of that div would be 104px. IE on the other hand would calculate a total width of 100px, leaving you effectively with only 96px of content, because it didn't add the border px but subtracted them from the overall width. 

This used to be, and probably still is, one of the most common 'quirks' of IE that requires a seperate stylesheet. So for IE (like I said, it may have been fixed in IE8 ) add the size of borders, the total size (so if it's a 2px border all round, add 4px) to the width and/or height of the divs you already got and ithat should correct IE's pigheaded obstinacy.

Site looks good in Opera 10.63 here :)

Yeah, that's still how IE does it.  I just decided to make ternary statements that set the height/width values to a little bit larger for IE.

> **Strategist01 said:**
> That site looks very good! BTW, there's no apostrophe in "Chaiman's", as it's plural, not possessive. Sorry. Had to point that out. Works great under FF. But I think a link to direct people to a page to encourage them to get FF would be best...


A quick google showed that Chairman's is the way FIRST spelled it.

Anyway, thanks guys, at least I know the design is a hit.

---

