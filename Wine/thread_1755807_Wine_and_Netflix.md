---
title: "Wine and Netflix"
date: 2011-05-11
forum: Wine
---

### Post by irv on 2011-05-11
Has anybody gotten Netflix to run in a Browser under Wine?

---

### Post by doas777 on 2011-05-11
nope. at this point, Netflix on linux is close to impossible. we can probably write the code to do it, but to do so would be highly illegal.

---

### Post by irv on 2011-05-11
> **doas777 said:**
> nope. at this point, Netflix on linux is close to impossible. we can probably write the code to do it, but to do so would be highly illegal.

The problem is  with Sliverlight from MS. It will not load under Wine. I really feel MS has something in the install code to prevent this from happening. Of course it is not open source so we will never know.

---

### Post by _outlawed_ on 2011-05-11
> **irv said:**
> The problem is  with Sliverlight from MS. It will not load under Wine. I really feel MS has something in the install code to prevent this from happening. Of course it is not open source so we will never know.

Most likely because Silverlight needs functions of the Windows API of which Wine can't do, but that is just my guess.

---

### Post by irv on 2011-05-11
> **_outlawed_ said:**
> Most likely because Silverlight needs functions of the Windows API of which Wine can't do, but that is just my guess.
And probably a very good guess.
Windows programmer have been known to do this. I played around with windows program developing for awhile, (but never got to serious with it). Using Windows API does cut down on code and it is a practice to do this.

---

### Post by robsoles on 2011-05-11
Hey, I haven't checked out netflix but if it relies on Silverlight can you guys confirm it won't work using [http://www.mono-project.com/Moonlight](http://www.mono-project.com/Moonlight) directly in a Linux based browser?

---

### Post by irv on 2011-05-11
> **robsoles said:**
> Hey, I haven't checked out netflix but if it relies on Silverlight can you guys confirm it won't work using [http://www.mono-project.com/Moonlight](http://www.mono-project.com/Moonlight) directly in a Linux based browser?

No matter what browser you use in Linux you will get this message even with moonlight installed.
[ATTACH]191885[/ATTACH]

---

### Post by irv on 2011-05-11
I have a Roko box running Linux and they are licensed to use code to run Netflix. There has been many articles out on this problem with Netflix. I guess the only what we can get Netflix to support us Linux users is to boycott them. The only problem is I like Netflix and so do many others.

---

### Post by doas777 on 2011-05-11
> **irv said:**
> I have a Roko box running Linux and they are licensed to use code to run Netflix. There has been many articles out on this problem with Netflix. I guess the only what we can get Netflix to support us Linux users is to boycott them. The only problem is I like Netflix and so do many others.
the issue at hand is the licensing on the DRM layer. moonlight has the ability to implement most of the silverlight runtime, because MS licensed it (and the associated patents) freely, but the components that silverlight uses to decrypt a protected stream are closed-source, and restrictively licensed. Roku and Boxee both purchase a hardware decoder from a licensed manufacture, or so I have been lead to believe.

---

### Post by robsoles on 2011-05-11
> **irv said:**
> No matter what browser you use in Linux you will get this message even with moonlight installed.
[ATTACH]191885[/ATTACH]

That could be netflix rather than Microsoft doing that. Please post me a link to a netflix video (seriously, don't make me google for it :)) and I will have a look at changing my user-agent string in Firefox and see if I can trick their system into starting the stream for me - if I can I will describe how I do it.

Ps: I understand that the original topic and intent of this thread is to do it in WINE using Silverlight etc but I see this as a more likely alternative :)

---

### Post by irv on 2011-05-11
> **robsoles said:**
> That could be netflix rather than Microsoft doing that. Please post me a link to a netflix video (seriously, don't make me google for it :)) and I will have a look at changing my user-agent string in Firefox and see if I can trick their system into starting the stream for me - if I can I will describe how I do it.

Ps: I understand that the original topic and intent of this thread is to do it in WINE using Silverlight etc but I see this as a more likely alternative :)

I doubt it will let you run the video because it is my account and i can't give you my login and password; but here is the link:
[http://movies.netflix.com/WiMovie/Judgment/70027100?trkid=3953044#height1866]("http://movies.netflix.com/WiMovie/Judgment/70027100?trkid=3953044#height1866") I have a coupon for one month free netflix, if you send me your email address I will send it to you. That way you will have a month to play around with this. Just send me a private message and I will send it to you.

---

### Post by robsoles on 2011-05-11
OK, now I've been reminded why 'netflix' is something I would ask for a link to, rather than hunting down for myself.

I am in Australia and the operators of that website have a message for people outside of the US that it basically isn't for them :roll:


Anyway, what I was going to do was use either of the following firefox addons to give myself a Windows based user agent (in Firefox on my Ubuntu installation at home) string and then try the link anybody might provide me.

[https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/)

[https://addons.mozilla.org/en-us/firefox/addon/user-agent-rg/](https://addons.mozilla.org/en-us/firefox/addon/user-agent-rg/)


I was going to try practically any generic user-agent string with Windows indicated as the operating system```
Mozilla/5.0 (Windows NT 6.0; rv:2.0b7) Gecko/20100101 Firefox/4.0b7
```**(Actually: Very likely need to get the user-agent string being used by copies of Windows based firefox with Silverlight installed!)**


I imagine that this will stop the website from blocking you (your GEOIP location being in US or Canada and your browser claiming to be running in Windows) and then you can find out if moonlight can manage their movie stream or not.

---

### Post by directhex on 2011-05-12
> **robsoles said:**
> OK, now I've been reminded why 'netflix' is something I would ask for a link to, rather than hunting down for myself.

I am in Australia and the operators of that website have a message for people outside of the US that it basically isn't for them :roll:


Anyway, what I was going to do was use either of the following firefox addons to give myself a Windows based user agent (in Firefox on my Ubuntu installation at home) string and then try the link anybody might provide me.

[https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/)

[https://addons.mozilla.org/en-us/firefox/addon/user-agent-rg/](https://addons.mozilla.org/en-us/firefox/addon/user-agent-rg/)


I was going to try practically any generic user-agent string with Windows indicated as the operating system```
Mozilla/5.0 (Windows NT 6.0; rv:2.0b7) Gecko/20100101 Firefox/4.0b7
```**(Actually: Very likely need to get the user-agent string being used by copies of Windows based firefox with Silverlight installed!)**


I imagine that this will stop the website from blocking you (your GEOIP location being in US or Canada and your browser claiming to be running in Windows) and then you can find out if moonlight can manage their movie stream or not.

Without DRM support, this is a futile path.

---

### Post by robsoles on 2011-05-12
> **directhex said:**
> Without DRM support, this is a futile path.

This is dated 2007 but appears to have had updates since then: [http://www.wine-reviews.net/microsoft/windows-media-player-9-aamp-10-on-linux-with-wine.html](http://www.wine-reviews.net/microsoft/windows-media-player-9-aamp-10-on-linux-with-wine.html)

Not quite there but the nearest I found for 15 minutes of trying to Google as if I really wanted to play DRM protected stuff.

---

### Post by irv on 2011-05-12
Just found this link in another thread:  [http://www.droiddog.com/android-blog/2011/05/google-bringing-netflix-to-chrome-chrome-os-and-linux-via-html5/]("http://www.droiddog.com/android-blog/2011/05/google-bringing-netflix-to-chrome-chrome-os-and-linux-via-html5/")
[ATTACH]191955[/ATTACH]

---

### Post by doas777 on 2011-05-12
> **irv said:**
> Just found this link in another thread:  [http://www.droiddog.com/android-blog/2011/05/google-bringing-netflix-to-chrome-chrome-os-and-linux-via-html5/](http://www.droiddog.com/android-blog/2011/05/google-bringing-netflix-to-chrome-chrome-os-and-linux-via-html5/)
[ATTACH]191955[/ATTACH]
I've heard promises before, but I hope this one is for real. if chromeOS takes off, linux will be much less of a second class citizen.

---

### Post by irv on 2011-05-12
> **doas777 said:**
> I've heard promises before, but I hope this one is for real. if chromeOS takes off, linux will be much less of a second class citizen.
We will never be second class in my book.
If every Linux user who has a account with Netflix would organize a one month boycott again Netflix all in the same month maybe they would sit up and take notice.

---

### Post by Derringer81 on 2011-05-13
[http://getchrome.eu/download.php](http://getchrome.eu/download.php)

...I'm giving it a shot....

---

