---
title: "Google now has Google Chrome in a .deb file"
date: 2009-12-09
forum: The Cafe
---

### Post by RJ12 on 2009-12-09
Hey guys I just found out google has released there Linux version of Chrome:D. You can now get it in a .deb file for 32bit and 64bit. I am downloading it right now and will post back after install.

Oh and they even have .rpm for Fedora and openSuse

Here is the link

[http://www.google.com/chrome/eula.html?brand=CHFH&utm_source=en-et-yt-ftr-lx&utm_medium=et&utm_campaign=en](http://www.google.com/chrome/eula.html?brand=CHFH&utm_source=en-et-yt-ftr-lx&utm_medium=et&utm_campaign=en)

---

### Post by jbrown96 on 2009-12-09
One thing to note is that installing this .deb also installs an automatic updater. Check /etc/cron.daily/google-chrome. It doesn't bother me, but some people may want to delete it.

I tried it out. Rendering is very fast! I've really come to like the Awesome Bar in Firefox, so it was difficult using Chrome initially. I also wasn't impressed with the font rendering (something that has never bothered me before), although it may be a Kubuntu quirk. 

I recommend trying it at least. I've found that Arora (KDE webkit browser) offers similar performance with better location bar and font rendering (again, that may be because I use KDE).

---

### Post by t0p on 2009-12-09
> **RJ12 said:**
> Hey guys I just found out google has released there Linux version of Chrome:D. 

But are you aware that Google Chrome is chock-full of spyware?  That the browser is really just another way for Google to keep tabs on you?

The open source version of the browser - Chromium - is apparently the same thing but with a lot of the spyware removed.  I've been testing it for a short while now.  I still prefer Firefox.  But Chromium's just a beta at the moment, maybe it'll improve enough to steal me away from the 'Fox...

**EDIT:** Instructions on how to install Chromium daily builds [here]("http://www.psychocats.net/ubuntucat/chromium/").

---

### Post by RJ12 on 2009-12-09
Well yeah but I have always wanted to see a Ubuntu version though. I really never tried Chromium (I couldnt find a deb file and I didnt know if the one where adding the PPA is safe) but I have a error with it. It is looking for a old file in the repos. (the version in the repos is something2_i386.deb when its looking for a something1_i386.deb). Hey at least they dont hide the spying though (Its in the EULA)

---

### Post by RiceMonster on 2009-12-09
> **t0p said:**
> But are you aware that Google Chrome is chock-full of spyware?  That the browser is really just another way for Google to keep tabs on you?

Thank God someone has to point that out everytime there's a thread about Chrome! I'm saved from the evil empire!

---

### Post by crimesaucer on 2009-12-09
> **t0p said:**
> But are you aware that Google Chrome is chock-full of spyware?  That the browser is really just another way for Google to keep tabs on you?

The open source version of the browser - Chromium - is apparently the same thing but with a lot of the spyware removed.  I've been testing it for a short while now.  I still prefer Firefox.  But Chromium's just a beta at the moment, maybe it'll improve enough to steal me away from the 'Fox...

**EDIT:** Instructions on how to install Chromium daily builds [here]("http://www.psychocats.net/ubuntucat/chromium/").

I think the browser that removes all of the tracking is called "Iron".

The Iron Browser: [http://maketecheasier.com/iron-browser-a-secure-alternative-to-google-chrome/2009/07/08](http://maketecheasier.com/iron-browser-a-secure-alternative-to-google-chrome/2009/07/08)

---

### Post by RJ12 on 2009-12-09
Thanks for the instructions I will try them out now

I dont want spyware *shivers*

---

### Post by ElSlunko on 2009-12-09
Installed the .rpm in opensuse but flash didn't work out of the box. It did in Ubuntu, however.

---

### Post by beastrace91 on 2009-12-09
> **t0p said:**
> But are you aware that Google Chrome is chock-full of spyware?  That the browser is really just another way for Google to keep tabs on you?

Can you provide a link to the source of this information?... As far as I'm aware Chrome browser is Open Source correct? Meaning even if they are tracking stuff through it (which I really don't doubt/mind) odds are people have ripped it out already...

Also Google Chrome having a .deb installer is super old news - I've been using it for over a month at least now ;)

~Jeff

---

### Post by pwnst*r on 2009-12-09
old.

and, lol @ spyware.

---

### Post by RiceMonster on 2009-12-09
> **beastrace91 said:**
> Also Google Chrome having a .deb installer is super old news - I've been using it for over a month at least now ;)

Chrome, not Chromium.

Chromium, the open source development version has been available for a while. Chrome, the branded proprietary version was just made available for Linux yesterday. Not old news.

---

### Post by Linuxforall on 2009-12-09
Well I needed a alternate to Opera when I would get the occasional stumble with it, FF just doesn't work for me so plunged into Google's spyware, gotta admit, they did a heck of a job, browser opens in flash, renders quite a few sites faster than Opera but on some sites its slow so its a toss up. The extensions work, adblocking works, one of the most interesting extensions is the HTML5 redirect for sites like youtube and that is a real catcher, the videos even in full screen mode hardly uses any CPU. It has run stable with heavy surfing, no strange issues and very few if any incompatibilites with websites. So yes, let Google spy on me for all they want, thats their reward for offering a great browser. I got nothing to hide anyways and when one uses Google search engine, they are spying on you as well ;)

Btw, during install you have the choice to check or uncheck the send anonymous statistics to google tab, at least they are admitting and giving one a choice. Just because of the so called perception on Google shouldn't prevent people from trying this browser out and prejudging it.

Flash x64 works well but I don't need it as I use the HTML5 extension. Java works but not the Open JDK, you need to install Sun Java either the older one from repos or the latest one via .bin file. I have done the later, its installed over Open JDK and selected via update-alternatives and it works wonderfully. All three browsers pass the Java tests thrown at them.

---

