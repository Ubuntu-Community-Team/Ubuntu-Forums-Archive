---
title: "Protect from Google Data mining of personal Info"
date: 2010-07-11
forum: Security
---

### Post by Nbala on 2010-07-11
Hi,
So, I've been doing so net-research on the whole Google/Privacy issue.
And, honestly- I do NOT like what I am hearing.
#1: That Google places a cookie (unique identifier for you) which sends all searches performed to Google & links with your google ID. With Chrome this goes for even starting to type it in the search bar. EG: A "How to Cheat Insurance" search using Wireshark it displays that ' How / How to / How to Cheat / How to Cheat Insurance ' are each sent as cookie info to Google, and there (probably) associated with your Google ID or with whatever Infocloud they have made from you- whether or not you perform the search.
Then theres the issues of Google Docs etc mining data. ( Eg, your resume.. ) Even a project to use the microphone to define what tv you are watching to target you further.
Anyways tangent aside- my question is:

[LIST]
[*]**    In Ubuntu WHERE are the cookies located (and any other deletable internet data / personal information) so I can delete them. **
[/LIST]
The Google cookie which relays each aspect of your life has a 2 year lifespan and renews at each use of a google app...:frown:
I am realllllllly easy going- I didn't care about them recording information even when I should have, but now it is so pervasive and data-deep that I am concerned.

[LIST]
[*]**How do I remove any Google data-mining cookies, etc? In my windows days, things like Hijack this would delete ALL ( sometimes too much ) personal data from the registry down, but in Ubuntu...?**
[/LIST]
Thank you very much- I really do appreciate any ideas on this!
Nbala

---

### Post by michaelzap on 2010-07-11
First, I suggest that you be a bit more skeptical in your "research" instead of just accepting the most exaggerated critiques as fact (which your post strongly suggests to me).

Here are some links you may find useful:
[http://www.google.com/ads/preferences/plugin/](http://www.google.com/ads/preferences/plugin/)
[http://google-anon.com/](http://google-anon.com/)
[http://www.google.com/privacy.html](http://www.google.com/privacy.html)
[http://arstechnica.com/security/news/2008/09/security-expert-google-anonymization-not-anonymous-enough.ars](http://arstechnica.com/security/news/2008/09/security-expert-google-anonymization-not-anonymous-enough.ars)
[http://en.wikipedia.org/wiki/Criticism_of_Google](http://en.wikipedia.org/wiki/Criticism_of_Google)

---

### Post by Bachstelze on 2010-07-11
> **Nbala said:**
> 
[LIST]
[*]**    In Ubuntu WHERE are the cookies located (and any other deletable internet data / personal information) so I can delete them. **
[/LIST]
[LIST]
[*]**How do I remove any Google data-mining cookies, etc? In my windows days, things like Hijack this would delete ALL ( sometimes too much ) personal data from the registry down, but in Ubuntu...?**
[/LIST]

Depends on your browser...

---

### Post by Rubi1200 on 2010-07-11
If you use Firefox:

[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

Security:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

What you should know:

Linux is not Windows; I know this has been said before, but you need to try and approach things differently.

Q. Cookies

A. Depends on your browser, but they all have an option to delete them (even IE)

Q. LSO's (you didn't even ask about them!) [http://en.wikipedia.org/wiki/Local_Shared_Object](http://en.wikipedia.org/wiki/Local_Shared_Object)

A. Firefox addon called Better Privacy

---

### Post by anomie on 2010-07-12
[QUOTE=Nbala]So, I've been doing so net-research on the whole Google/Privacy issue.
And, honestly- I do NOT like what I am hearing.[/QUOTE]

If you're sufficiently concerned, the answer is to not use their services, period (IMO). 

Don't use Google's search, gmail, DNS servers, docs, picasa, etc., etc., etc. Stay off of all social networking sites. 

As for alternatives: 
[list]
[*] Bing still mostly sucks, but it's getting better. Ixquick is not bad. 
[*] For free webmail that supports HTTPS, both Lavabit and Hushmail are OK. 
[*] OpenDNS provides free nameservers. 
[*] I know of no good, free alternative to docs. 
[*] There are lots of (variously crappy) free photo hosting services. 
[/list]

---

### Post by mikewhatever on 2010-07-12
Cookies can be disabled in all browsers. Just disable all cookies and then allow only the sites you need, like email, ubuntuforums, etc.

---

### Post by rookcifer on 2010-07-12
Use [Scroogle]("https://ssl.scroogle.org/") for search.  It is Google without any tracking whatsoever.

---

### Post by gpumalwareqs132 on 2010-07-12
-snip- nevermind.

---

### Post by cariboo on 2010-07-12
The hosts file is not the place to block ads, that may work for Windows, but can cause all sorts of problems in Linux. Privoxy is a much better solution.

---

### Post by bodhi.zazen on 2010-07-12
The best option is - do not use google. It is a two edged sword , google has a fantastic search engine because people share the search results.

If you use google, take a look at [Optimize Goolgle](https://addons.mozilla.org/en-US/firefox/addon/52498/)

Optimize google works well, so long as you do not create a google account and log in (ie no gmail, gcal, etc).

---

### Post by mikewhatever on 2010-07-12
> **cariboo907 said:**
> The hosts file is not the place to block ads, that may work for Windows, but can cause all sorts of problems in Linux. Privoxy is a much better solution.

Privoxy is cool, if you are satisfied with the default settings. Making your own configuration, however, looks incredibly complex.

---

### Post by SoFl W on 2010-07-12
If you use noscript you need to go into options and remove google from the whitelist.   Google has javascript embedded in many pages so you will need to block those scripts as well.  

But I wouldn't worry, Google motto is "don't be evil", so how could they be? ;)

---

### Post by bodhi.zazen on 2010-07-12
> **mikewhatever said:**
> Privoxy is cool, if you are satisfied with the default settings. Making your own configuration, however, looks incredibly complex.

It is not ad difficult as it first appears, try the web interface =)

---

### Post by mikewhatever on 2010-07-13
> **bodhi.zazen said:**
> It is not ad difficult as it first appears, try the web interface =)

Thanks. I'll try finding how to access web interface in the encyclopedia they call user-manual. I don't normally have reading comprehension problems, but that magnificent document is a real challenge.Can make heads nor tails of it.

---

### Post by bodhi.zazen on 2010-07-13
> **mikewhatever said:**
> Thanks. I'll try finding how to access web interface in the encyclopedia they call user-manual. I don't normally have reading comprehension problems, but that magnificent document is a real challenge.Can make heads nor tails of it.

> Privoxy's user interface can be reached  through the special   URL [http://config.privoxy.org/](http://config.privoxy.org/)  (shortcut: [http://p.p/](http://p.p/)),   which is a built-in page and works without Internet access.  You will see the following section:

[http://www.privoxy.org/user-manual/configuration.html](http://www.privoxy.org/user-manual/configuration.html)

I agree, the documentation feels a bit overwhelming. Take a look at the various files and you will probably get a feel for it fast enough.

After looking at the web interface I got it sorted in about 15 minutes.

You can also manually read the config files , they are well commented.

---

### Post by Twitch6000 on 2010-07-13
Well just to let you know all the info they gather from you is to make the ads geared toward your interests.

They never use it for anything else. If they did they would be sued so much..

The ones you need to worry about is your isp(comcast is really known to do this).

---

### Post by zerubbabel on 2011-07-18
> **anomie said:**
> If you're sufficiently concerned, the answer is to not use their services, period (IMO). 

Don't use Google's search, gmail, DNS servers, docs, picasa, etc., etc., etc. Stay off of all social networking sites. 

As for alternatives: 
[list]
[*] Bing still mostly sucks, but it's getting better. Ixquick is not bad. 
[*] For free webmail that supports HTTPS, both Lavabit and Hushmail are OK. 
[*] OpenDNS provides free nameservers. 
[*] I know of no good, free alternative to docs. 
[*] There are lots of (variously crappy) free photo hosting services. 
[/list]

Does Google scan the photographs that you organize in Picasa even if you do not use their web album feature? In other words, just using Picasa to organize your photos on your own disk?

---

### Post by uRock on 2011-07-18
NecroThread Closed.

{;ease start a new thread on this subject as the original participants are not likely to be subscribed.

---

