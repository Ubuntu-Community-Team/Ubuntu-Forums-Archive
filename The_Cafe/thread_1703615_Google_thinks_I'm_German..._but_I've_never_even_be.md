---
title: "Google thinks I'm German... but I've never even *been* to the place!"
date: 2011-03-09
forum: The Cafe
---

### Post by t0p on 2011-03-09
This has been going on for !a couple of weeks now: I use Google to do a search, and it serves up results in English *and in German*!  Could this be due to some weird geolocation glitch?  I don't think so... my ISP uses servers located in various British cities (London, Bristol, Birmingham and Manchester are the ones that spring to mind).  Is it the search settings?  Well, yes - but I don't know why!  I go to the settings page, and the language boxes ticked are English *and German*!  So, I uncheck the German box, save my changes... but when I do another search I get a bunch of German results, and when I go back to the settings page the German box has been mysteriously ticked again!

This happens whether I'm signed into Google or not (ie if I'm checking my Gmail in one tab, then go to do a search in another tab I'm automagically signed in there too).  I have more than one Google account, and this happens with all my accounts!  It's got so annoying, I've started to use dogpile.com to do searches now.

One interesting thing I just thought of: this all started happening at about the same time that I chose to use Google's new https service - I type "google.com" or "google.co.uk" or whatever into the url box, but I'm taken to [https://encrypted.google.com](https://encrypted.google.com) instead.  This also happens no matter if I'm signed in as an account holder or not.  Am I to conclude from this that using Google's "super-secure" service channels my traffic through Germany - one of the most anti online security countries in Europe?

**EDIT:** Interestingly, I can't opt out of the SSL service now.  There's a link on the search page to go to "classic Google", but when I click on it I'm taken to [https://encrypted.google.com](https://encrypted.google.com) regardless.  What's happening??  Why *meeee*???

**RE-EDIT:** I decided to do a whois enquiry on "encrypted.google.com", but it wouldn't/couldn't tell me anything:

```

t0p@deimos:~$ whois encrypted.google.com

Whois Server Version 2.0

Domain names in the .com and .net domains can now be registered
with many different competing registrars. Go to http://www.internic.net
for detailed information.

No match for "ENCRYPTED.GOOGLE.COM".
>>> Last update of whois database: Wed, 09 Mar 2011 19:44:10 UTC <<<

```

*?????!!*

---

### Post by dionysius on 2011-03-09
Perhaps Google is encouraging you to take up a foreign language?;)

---

### Post by Lucradia on 2011-03-09
I want it to take me to https even though I type in google.com; but it just takes me to the normal google.com.

---

### Post by sisco311 on 2011-03-09
Did you clear the browser's cache? Did you try a different browser? 

Are you sure that you are not German? :P

---

### Post by teward on 2011-03-09
> **sisco311 said:**
> Did you clear the browser's cache? Did you try a different browser?

All joking aside, you should definitely erase your browser's cache.  If its still doing it after that, you should probably contact Google about it.

---

### Post by aschwerin.moses on 2011-03-09
> **dionysius said:**
> Perhaps Google is encouraging you to take up a foreign language?;)

haha.. good one


well... open google.com, to the top right check Search Settings. Make sure to select only english. give it a try and let us know

---

### Post by bufsabre666 on 2011-03-09
Mine was reset to Afrikaans, I just had to set it once back to english. Also had to do it on every PC I use but it's simple enough. 

If you're searching for something it's the second thing over from the top corner, that's the "My Account" page. It's the thing in the drop down menu.

---

### Post by barbedsaber on 2011-03-09
just tell them that nein, you are not germam

---

### Post by lisati on 2011-03-09
> **t0p said:**
> Could this be due to some weird geolocation glitch?  I don't think so... my ISP uses servers located in various British cities (London, Bristol, Birmingham and Manchester are the ones that spring to mind). 
Interesting thought. The [whatismyip]("http://whatismyipaddress.com") website can give you and idea of what servers might perceive as your current location. Doing a gelocation on my IP address usually gives a location 600km or so away from where I'm really located.

---

### Post by ki4jgt on 2011-03-09
Try going into the search settings and remove German as the returned results.

---

### Post by MisterGaribaldi on 2011-03-10
@ t0p:

Wenn Sie plötzlich lesen können, ohne einen Online-Übersetzer benutzen, sollten Sie vielleicht Sorgen machen.

(Just sayin'...)

---

### Post by mips on 2011-03-10
> **bufsabre666 said:**
> Mine was reset to **Afrikaans**, I just had to set it once back to english.

I could provide you with some free lessons if you are interested :D

---

### Post by 3rdalbum on 2011-03-10
Maybe it's because you have been to the Cafe, which has such threads as:

Foss not going so well in Germany
Seeking German penpal
Das Keyboard

---

### Post by Zero2Nine on 2011-03-10
Google knows you better than you know yourself :p Who should we believe, one guy who claims he is not German or GOOGLE? I guess you are German, you just have to accept it.

---

### Post by Plumtreed on 2011-03-10
....OP is clearly German....once Google has decided it is final!

---

### Post by gnomeuser on 2011-03-10
Google tends to be confused with regards to locations. E.g. right now my Android phone claims that my location is.. well.. in the middle of the lake next to my house, which given that it is winter I assure them is not true.

---

### Post by Lucradia on 2011-03-10
> **gnomeuser said:**
> Google tends to be confused with regards to locations. E.g. right now my Android phone claims that my location is.. well.. in the middle of the lake next to my house, which given that it is winter I assure them is not true.

Turn off all my location settings, GPS; and specify location manually each time. (Town name + region/state)

---

### Post by nothingspecial on 2011-03-11
I remember upgrading firefox once and choosing "uk" for my location, should have chosen "gb", everything was in Ukranian.

---

### Post by t0p on 2011-03-11
Thanks for the suggestions.  I have cleared the cache, checked English (and unchecked German) in my Google preferences... and it's still giving me German results along with the English.

I'm using dogpile.com for the moment.  Either Google is really stupid, or I am.  I don't particularly want to know which is true.

---

### Post by matt_symes on 2011-03-11
Hi

Your not going through some proxy server somewhere on the net are you. 

I have been messing around with Tor for the last couple of months and it can dump me at a Google site pretty much anywhere. 

Netherlands, Germany, Philippines. You get the picture. That can give mixed language results.

Just a thought.

Kind regards

---

### Post by Blutkoete on 2011-03-11
I've got a quick (depending on the postal system) & dirty solution: Let's exchange computers. I'm German, but many sites (including Google) identify me as English.

How long have you been experiencing this problem? Maybe your Internet provider just gave you a dynamic IP used by a German the last time and Google stored the IP as "German user".

---

### Post by ki4jgt on 2011-03-11
> **Blutkoete said:**
> I've got a quick (depending on the postal system) & dirty solution: Let's exchange computers. I'm German, but many sites (including Google) identify me as English.

How long have you been experiencing this problem? Maybe your Internet provider just gave you a dynamic IP used by a German the last time and Google stored the IP as "German user".

Yeah, but he told Google not to return German results to him.

---

### Post by Blutkoete on 2011-03-11
Yes, sorry, you're right. But I know that Google's language selection is not perfect - if I google from a university computer and tell it to only display results that are in English language, I still get some results in German as well. So maybe that's a Google problem.

I think (never really tested it) that it happens with pages that contain both languages.

---

### Post by jmore9 on 2011-03-11
Ha ! google made me chinese i had a heck of a time getting back to english.  Had to go reset all my google settings in my account.

---

