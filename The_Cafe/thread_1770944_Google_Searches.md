---
title: "Google Searches"
date: 2011-05-29
forum: The Cafe
---

### Post by P=NP on 2011-05-29
I was reading about the [Casey Anthony]("http://www.google.com/#hl=en&sugexp=ldymls&xhr=t&q=casey+anthony+internet+searches&cp=20&pq=casey%20anthony&pf=p&sclient=psy&source=hp&aq=0&aqi=&aql=&oq=casey+anthony+intern&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=a34f7f1872f21971&biw=1280&bih=889") murder trial and how she searched the Internet for various seemingly incriminating things, and it got me thinking.

Where are those search records stored? On her computer? Google's servers? The ISP?

Would something like tor have obfuscated those searches?

Is there anything that can be done so that I may remain anonymous?

Is Google our all-seeing, all-remembering overlord?

---

### Post by jtarin on 2011-05-29
The story if you will read more diligently, states it was found on the computer. Do you have something to hide?

---

### Post by P=NP on 2011-05-29
Just guessing here, but she was probably using a Windows machine.

How does this apply to Ubuntu? 

Will turning off FF's cache be enough? Encrypted home directory?

Does Google or the ISP have this information?

---

### Post by _0R10N on 2011-05-29
I don't know whether google keeps log of all the searches made by an IP for a given period of time, but I can tell you for sure that ISPs keep logs of all of the traffic comming through them. Also the searches made by an user are stored in his/her local machine, to help search engines autocomplete entries, based on previous searches made by the user.

regards!

---

### Post by drs305 on 2011-05-29
Moved to the Cafe.

---

### Post by P=NP on 2011-05-29
> **_0R10N said:**
> I don't know whether google keeps log of all the searches made by an IP for a given period of time, but I can tell you for sure that ISPs keep logs of all of the traffic comming through them. Also the searches made by an user are stored in his/her local machine, to help search engines autocomplete entries, based on previous searches made by the user.

regards!

So would tor make it impossible for Google to keep track of your Internet searches? 

The ISP knows about traffic, would tor make it seem to come from a random machine? Do they sniff traffic for searches?

---

### Post by undecim on 2011-05-29
> **P=NP said:**
> So would tor make it impossible for Google to keep track of your Internet searches? 

Only if done correctly. There are a lot of mistakes you can make that render Tor worthless.

> **P=NP said:**
> The ISP knows about traffic, would tor make it seem to come from a random machine? Do they sniff traffic for searches?

The ISP would see that the user is using Tor, but not what is being done with that traffic. Google would see it coming from a Tor exit node, assuming that the user has taken care to clear cookies, cache, and takes measures to avoid [browser fingerprinting]("https://panopticlick.eff.org/"), and uses Tor properly.

Theoretically, Google and the ISP could work together to determine that you are the one performing the searches, but that is highly unlikely.

---

### Post by scouser73 on 2011-05-29
All searches performed using Google are held on their servers, they go to helping refine search in general.  Could you be identified by it?, well that's an interesting question; there was a case of a woman from America having been traced by using a number (not an IP address).  She was identified as being related to that number via her online activities.

---

### Post by jtarin on 2011-05-29
Any connection between you and a cached IP number could only be used as circumstantial evidence.

---

### Post by Aquix on 2011-05-30
ISP won't see your google search if you use ssl. [https://encrypted.google.com/](https://encrypted.google.com/)

---

### Post by ubuntu27 on 2011-05-30
Use [Duck Duck Go]("https://duckduckgo.com/"), [Ixquick]("https://ixquick.com/"), [StartPage]("https://www.startpage.com/"), or [Scroogle]("http://www.scroogle.org/")

---

### Post by tgalati4 on 2011-05-30
All your searches are belong to us.

---

### Post by jtarin on 2011-05-30
> **Aquix said:**
> ISP won't see your google search if you use ssl. [https://encrypted.google.com/](https://encrypted.google.com/)
From their page
> Note that SSL search does not reduce the data that Google receives and logs when you search, or change the listing of these terms in your Web History New window icon.

---

### Post by handy on 2011-05-30
The following is courtesy of tjwoosta from this thread:

[http://spiralinear.org/forum/viewtopic.php?f=17&t=243](http://spiralinear.org/forum/viewtopic.php?f=17&t=243)


[i]I feel I can get pretty decent privacy when I want to.

1. Use an anonymous proxy to mask my ip

I use tor for anonymity, privoxy for filtering (i.e. ad blocking, some header stripping, deanimate gifs, etc..), and polipo for caching (helps speed tor up a bit).

2. Block all plugins and js completely (flash and js can give away an amazing amount of data that can help distinguish your individual machine, such as system fonts, screen resolution, etc..)

With uzbl this is as simple as disable_scripts = 1, disable_plugins = 1, etc.. in the config. With firefox Im sure theres a setting somewhere in about:config

3. Disable all cookies (this will break many popular websites, but if your trying to stay annonymous its essential..)

With uzbl I actually just use the whitelist which blocks all cookies accept from the sites you specify in the list.

4. Change useragent to something more common. (A rare browser like uzbl sticks out like a sore thumb.)

5. Change accept headers to match the default for whichever useragent string you went with. (If you have a IE/windows useragent with webkit/linux accept headers you could be even easier to pick out then if you hadnt changed your useragent)

Im still trying to accomplish this one in uzbl, the devs claim arbitrary header modification is something theyre working on which is good. It can already be done in firefox though.


Of course this is not my everyday browsing configuration for obvious reasons, but more of a special privacy mode configuration that I use for the .onion web. I made a script to automate everything.

Turn private mode on..

kills all uzbl instances
stops polipo daemon (I use polipo even without tor so its already running)
starts tor daemon
appends .bak to uzbl's history file
deletes polipo's cache
changes all the uzbl config settings (useragent, scripts, and plugins)
adds setting for tor as parent proxy in polipo's config
starts polipo daemon
opens uzbl again

Turn private mode off..

kills all uzbl instances
stops polipo daemon
stops tor daemon
deletes history file
moves the .bak history file back into place
deletes polipo's cache
changes all the uzbl settings back to original
removes setting for tor as parent proxy in polipo's config
starts polipo daemon
opens uzbl again


Most of the privacy plugins for firefox are obsoleted when you dont have cookies, plugins, or js. (Ghostery, BetterPrivacy, noscript, flashblock, whatever..)

Now this setup is fine for staying annonymous, but not at all for security. For example anyone can run a tor exit node, and anyone running an exit node can scan the traffic and see everything everyone using that node is doing, they just cant see where it originated beyond the next node in line, unless they get a warrant and get the full route from the tor master servers.

So basically nobody can know who you are, but dont do anything that would give you away, and dont do anything sensitive, like checking your real email, signing into places with your real username, etc.., because somebodys probably watching.[/i]

---

### Post by CraigPaleo on 2011-05-30
Yes, they found the searches on the computer. If she's guilty, I hope she gets the death penalty.

---

### Post by HappinessNow on 2011-05-30
> **P=NP said:**
> I was reading about the [Casey Anthony]("http://www.google.com/#hl=en&sugexp=ldymls&xhr=t&q=casey+anthony+internet+searches&cp=20&pq=casey%20anthony&pf=p&sclient=psy&source=hp&aq=0&aqi=&aql=&oq=casey+anthony+intern&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=a34f7f1872f21971&biw=1280&bih=889") murder trial and how she searched the Internet for various seemingly incriminating things, and it got me thinking.

Where are those search records stored? On her computer? Google's servers? The ISP?

Would something like tor have obfuscated those searches?

Is there anything that can be done so that I may remain anonymous?

Is Google our all-seeing, all-remembering overlord?Actually, you should worry more about your internet provider like Comcast, I have had on more then one occasion have a Comcast Representative brag how they can see everything I do online and to test this out I had one Representative give me passwords to accounts I told him I forgot.

The supposed big brother watching is not Google but Comcast!...

---

### Post by CraigPaleo on 2011-05-30
> **HappinessNow said:**
> Actually, you should worry more about your internet provider like Comcast, I have had on more then one occasion have a Comcast Representative brag how they can see everything I do online and to test this out I had one Representative give me passwords to accounts I told him I forgot.

The supposed big brother watching is not Google but Comcast!...

I believe it. My father received a warning from Comcast for downloading copyrighted material and they even specified the movie Avatar.

---

### Post by HappinessNow on 2011-05-30
> **CraigPaleo said:**
> I believe it. My father received a warning from Comcast for downloading copyrighted material and they even specified the movie Avatar.It's amazing how many people want to point the finger at Google when Comcast is blatantly and boldly intruding on our privacy but when you live in places where they are the only provider we have little choice in the matter except to unplug completely!

---

### Post by jtarin on 2011-05-30
I learned of the "suckyness" of Comcast in the early 90's and they have never ceased to amaze at the heights they can achieve at this.

---

### Post by CraigPaleo on 2011-05-30
> **HappinessNow said:**
> It's amazing how many people want to point the finger at Google when Comcast is blatantly and boldly intruding on our privacy but when you live in places where they are the only provider we have little choice in the matter except to unplug completely!

All ISPs should have those capabilities. I don't know how long they cache it but if there's a reason to flag it, it'll probably stay there indefinitely no matter how you try to circumvent it. 

You're right though. You may be able to fool Google but you can't fool your own ISP.

---

### Post by matthewbpt on 2011-05-30
If you're using SSL to connect to website, I don't know how the ISP is supposed to know what you're doing? SSL provides end to end encryption between you and the server, so middlemen cannot decrypt the information, this should include the ISP ... right?

---

### Post by jtarin on 2011-05-30
Maybe they don't need the information,only the address. Who is accessing?

---

### Post by jhonan on 2011-05-30
EDIT: Wrong section

---

### Post by PhillyPhil on 2011-05-30
> **matthewbpt said:**
> If you're using SSL to connect to website, I don't know how the ISP is supposed to know what you're doing? SSL provides end to end encryption between you and the server, so middlemen cannot decrypt the information, this should include the ISP ... right?

Right.

---

### Post by CraigPaleo on 2011-05-30
> **matthewbpt said:**
> If you're using SSL to connect to website, I don't know how the ISP is supposed to know what you're doing? SSL provides end to end encryption between you and the server, so middlemen cannot decrypt the information, this should include the ISP ... right?

I'm not really sure how it all works but this post makes it sound like it's other people who are doing the reporting to Comcast, sometimes even erroneously. 

[QUOTE=LoPhatPhuud]Before you go off the deep end condemning Comcast, remember they are just  the middleman in all this. Some else supplied them with the IP address. Comcast looked it up for the date and time of the supposed violation and sent the letter.

 Could the Comcast lookup make a mistake? Sure, but unlikely. Most likely the error, if  there was one, came from whoever sent Comcast the notice. [/QUOTE]
[http://forums.comcast.com/t5/Security-and-Anti-Virus/Comcast-Reporting-Erroneous-IP-Information-for-Copyright/td-p/891005]("http://forums.comcast.com/t5/Security-and-Anti-Virus/Comcast-Reporting-Erroneous-IP-Information-for-Copyright/td-p/891005")

---

