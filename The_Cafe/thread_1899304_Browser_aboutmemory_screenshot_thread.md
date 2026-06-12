---
title: "Browser about:memory screenshot thread"
date: 2011-12-23
forum: The Cafe
---

### Post by lovinglinux on 2011-12-23
I have seen many posts in the past complaining about browser memory usage. So, the idea of this thread is to compare each user browser *about:memory* page, to see where the memory is going and perhaps try to optimize it. Additionally, some users might not be aware of the existence of the *about:memory* page. I think this can be fun, educational and helpful at the same time.

I am not an expert on memory usage, but I think that together we can figure out some things. For instance, as you can see under the storage section in the screenshot below,  that *lazarus.sqlite* database is using 60Mb. 

[[IMG]http://www5.picturepush.com/photo/a/7207568/220/7207568.png[/IMG]](http://www5.picturepush.com/photo/a/7207568/img/Anonymous/about%3Amemory-2011-12-23-09-23-26.png)

Lazarus is an extension that saves what you type in forms, so in case the browser crashes you can recover the text. It is a very useful add-on, however 60Mb is too much to trade. So I opened Lazarus *Database* preferences and used the feature to *Clean The Database*, then restarted the browser. I didn't help. So I opened my FF profile and deleted the *lazarus.sqlite*. I probably could have done through Lazarus preferences as well. Anyways, I have gained 60 Mb in my Firefox RAM usage. 

[[IMG]http://www5.picturepush.com/photo/a/7207583/220/7207583.png[/IMG]](http://www5.picturepush.com/photo/a/7207583/img/Anonymous/about%3Amemory-2011-12-23-10-33-30.png)

This is a temporary solution tho. I have reduced the time lazarus keep old forms and will see if the database grows too much. If it does, I might go back to Textarea Cache extension.

So, let's see where your browser memory is going. If you have many tabs open, keep in mind that some page addresses might be revealed in the *about:memory* page. So, check the about:memory page before taking the screenshot.


**How to get the memory page?**

Simply type *about:memory* in the address bar and hit enter. It works for Chrome and Firefox. However, it doesn't work on Firefox 3.6.x, only in Firefox 4 upwards.

**How to make a screenshot?**

I recommend Awesome Screenshot, which is available for Chrome and Firefox:

[Firefox](https://addons.mozilla.org/en-US/firefox/addon/awesome-screenshot-capture-/)

[Chrome](https://chrome.google.com/webstore/detail/alelhddbbhepgpmgidjdcjakblofbmce)

**How to post?**

Please, don't post big images directly with img tags. Use a service that provides thumbnails for forums or post just the image link.

.

---

### Post by guyver_dio on 2011-12-23
1 trick I found while browsing for tweaks.

> [B]Tweak the *browser.sessionhistory.max_total_viewers* variable
[/B]This variable specifies Firefox how many pages it should keep in the memory, so when you hit *Back* and *Forward* buttons it loads pages faster. The default value is **-1**,  which means that it sets a certain number of pages depending on the  total RAM memory the system has. You can change this value to **0** (just double-click the variable), which means it won't hold into memory any pages.
Also my screenshot, using firefox 8, mines not to bad, i've got about 5 tabs open.

[URL="http://awesomescreenshot.com/0acqovscd"]http://awesomescreenshot.com/0acqovscd
[/URL]

[IMG]http://awesomescreenshot.com/0acqovscd[/IMG]

---

### Post by lovinglinux on 2011-12-23
> **guyver_dio said:**
> 1 trick I found while browsing for tweaks.

I keep mine at 5.

> **guyver_dio said:**
> Also my screenshot, using firefox 8, mines not to bad, i've got about 5 tabs open.

[URL="http://awesomescreenshot.com/0acqovscd"]http://awesomescreenshot.com/0acqovscd
[/URL]

Not bad indeed. 

Most of my memory usage comes from add-ons. They consume about 180 Mb.

---

### Post by Ms. Daisy on 2011-12-23
This is very cool and informative- thanks!
 
edit: I'm inspired to see how NoScript & Adblock affect memory use- I make heavy use of those add-ons.

---

### Post by crazy bird on 2011-12-23
about:memory gives me this --> see screenshot.

---

### Post by lovinglinux on 2011-12-23
> **crazy bird said:**
> about:memory gives me this --> see screenshot.

As mentioned in the first post, it doesn't work on Firefox 3.6.x. If you want to upgrade to Firefox 9, see [Firefox 9 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by thedarkdonut on 2011-12-24
Unfortunately the chrome extension that you linked doesn't allow screenshots of internal chrome webpages or it's the other way around.

---

### Post by lovinglinux on 2011-12-24
> **thedarkdonut said:**
> Unfortunately the chrome extension that you linked doesn't allow screenshots of internal chrome webpages or it's the other way around.

Sorry. Indeed Chrome has such limitation. I will try to figure out a way around it.

---

### Post by Shazaam on 2011-12-24
Mine (with 12 extensions running on FF 9.01)...
[http://awesomescreenshot.com/0c8qqir19](http://awesomescreenshot.com/0c8qqir19)

Off topic- Anyone try Aurora yet? Seems to be a bit faster than FF 9.

---

### Post by Zoot7 on 2011-12-24
[**Here you go...**]("http://i.imgur.com/MZVNm.png")

---

### Post by lovinglinux on 2011-12-24
> **Shazaam said:**
> Mine (with 12 extensions running on FF 9.01)...
[http://awesomescreenshot.com/0c8qqir19](http://awesomescreenshot.com/0c8qqir19)

Off topic- Anyone try Aurora yet? Seems to be a bit faster than FF 9.

Interesting that among all extensions I have, only Ghostery shows up in the report. On yours it is allocating even more memory. Not much as Lazarus tho.

I am using Aurora already and it is awesome. Add-ons are considered compatible by default now. I am not sure if there is any performance difference between the two, because Firefox 9 already incorporate the latest javascript tricks.

> **Zoot7 said:**
> [**Here you go...**]("http://i.imgur.com/MZVNm.png")

How many extensions do you have?

---

### Post by Zoot7 on 2011-12-24
> **lovinglinux said:**
> How many extensions do you have?

Counting them now, 14.

---

### Post by jjex22 on 2011-12-24
> **Shazaam said:**
> Mine (with 12 extensions running on FF 9.01)...
[http://awesomescreenshot.com/0c8qqir19](http://awesomescreenshot.com/0c8qqir19)

Off topic- Anyone try Aurora yet? Seems to be a bit faster than FF 9.

I've tried a couple of versions of it, to be honest on my hard ware the memory savings were very small compared to chromium i'd say about 5-8% and the real-time performance was just irritating - it was slow, I know chrome loads faster than firefox, but it was definitely slower than firefox, for me a silly trade off for a bit more free RAM. I managed to get it down further by disabling things, but this just made things worse and it became very unstable.

The best of the lightweight one's I've used is midori, at 5 tabs it was 30-40%% under FF6 if I remember (that gives you an idea of when I did these these last) but I wouldn't say it's full featured, and occasionally unstable - I only had it a couple of times, but there was one website... can't remember which that caused midori to exit every time. The plus side is that it uses firefox's flash, so you don't have to configure that again.

Away for the holidays atm , but when I get back I may do a more up to date test

---

### Post by lovinglinux on 2011-12-24
> **Zoot7 said:**
> Counting them now, 14.

Leave only one tab open on Google home page for example, restart the browser, open *about:memory* and take a screenshot. Close the browser, start it from command-line in safe mode:

```
firefox -safe-mode
```

Choose the option to "continue in safe mode" when prompted. Open *about:memory* and compare the previous screenshot. The difference is more or less what extensions and theme use of your memory.

---

### Post by paul_in_london on 2011-12-24
> Tweak the browser.sessionhistory.max_total_viewers variable
This variable specifies Firefox how many pages it should keep in the memory, so when you hit Back and Forward buttons it loads pages faster. The default value is -1, which means that it sets a certain number of pages depending on the total RAM memory the system has. You can change this value to 0 (just double-click the variable), which means it won't hold into memory any pages. 

Changed **browser.sessionhistory.max_total_viewers** from 8 to 0. No reduction in RAM usage for me, but that's probably because I have so many tabs open.

---

### Post by lovinglinux on 2011-12-24
> **paul_in_london said:**
> Changed **browser.sessionhistory.max_total_viewers** from 8 to 0. No reduction in RAM usage for me, but that's probably because I have so many tabs open.

Personally, I prefer to lower that value but not set as 0, because otherwise going back and forward will be slower.

---

### Post by lovinglinux on 2011-12-24
I am not sure what caused this, but there was a reduction of 36Mb on startup memory usage on my profile since yesterday. Initially, I thought it could be due to Firefox Aurora, but I have downgraded to Beta and the memory usage is the same. Perhaps they also improved 10.0b1, because I was actually using 10.0a2. But I also suspect it could be some add-ons that were updated. The memory usage difference is concentrated on the js section and heap-unclassified.

---

### Post by Lucradia on 2011-12-24
I'm going to link mine, because I don't want to use awesome screenshot, and prefer imgur out of any image host.

[http://i.imgur.com/4PkN6.jpg](http://i.imgur.com/4PkN6.jpg)

4 app tabs (Google Calendar, Twitter, a tab to help one of the boorus, and gmail)

one normal tab (vBull)

---

### Post by paul_in_london on 2011-12-24
> **lovinglinux said:**
> I am not sure what caused this, but there was a reduction of 36Mb on startup memory usage on my profile since yesterday. Initially, I thought it could be due to Firefox Aurora, but I have downgraded to Beta and the memory usage is the same. Perhaps they also improved 10.0b1, because I was actually using 10.0a2. But I also suspect it could be some add-ons that were updated. The memory usage difference is concentrated on the js section and heap-unclassified.

Hmm. I haven't noticed anything like this with the last few FF Nightly/add-on updates.

---

### Post by lovinglinux on 2011-12-24
> **Lucradia said:**
> I'm going to link mine, because I don't want to use awesome screenshot, and prefer imgur out of any image host.

[http://i.imgur.com/4PkN6.jpg](http://i.imgur.com/4PkN6.jpg)

4 app tabs (Google Calendar, Twitter, a tab to help one of the boorus, and gmail)

one normal tab (vBull)

Wow, 42Mb just for Gmail. This is interesting, to show people how different pages use different amount of memory. That "I have x tabs open" is not a good parameter when dealing with memory troubleshooting.

> **paul_in_london said:**
> Hmm. I haven't noticed anything like this with the last few FF Nightly/add-on updates.

It was probably some add-on I removed or disabled. I have tested many add-ons since yesterday. I also optimized  the profile sqlite databases.

---

### Post by lovinglinux on 2011-12-24
> **Lucradia said:**
> I'm going to link mine, because I don't want to use awesome screenshot, and prefer imgur out of any image host.

Thanks for the tip. I always like to try other services and add-ons. It is really a nice service. The [uploader add-on](https://addons.mozilla.org/en-US/firefox/addon/imgur-uploader/) is good as well.

---

### Post by cap10Ibraim on 2011-12-24
> **Shazaam said:**
> Mine (with 12 extensions running on FF 9.01)...
[http://awesomescreenshot.com/0c8qqir19](http://awesomescreenshot.com/0c8qqir19)

Off topic- Anyone try Aurora yet? Seems to be a bit faster than FF 9.
It feels faster for sure , but unstable with firebug which I use alot , but keeping it because they are adding many developer tools to it

---

### Post by cap10Ibraim on 2011-12-24
total explicit 63.49
[URL="http://picturepush.com/public/7217708"][IMG]http://www5.picturepush.com/photo/a/7217708/220/7217708.png[/IMG]not so sharp image , but just enouh 
[/URL]

---

### Post by lovinglinux on 2011-12-24
> **cap10Ibraim said:**
> not so sharp image , but just enouh

Click the image after opening and it will open the high resolution.

> **cap10Ibraim said:**
> total explicit 63.49

Awesome. I wish I could get that, but I love my extensions.

---

### Post by Lucradia on 2011-12-24
> **lovinglinux said:**
> Thanks for the tip. I always like to try other services and add-ons. It is really a nice service. The [uploader add-on](https://addons.mozilla.org/en-US/firefox/addon/imgur-uploader/) is good as well.

I've always use screengrab: [https://addons.mozilla.org/en-US/firefox/addon/screengrab/](https://addons.mozilla.org/en-US/firefox/addon/screengrab/)

I still do by installing this first: [https://addons.mozilla.org/en-US/firefox/addon/add-on-compatibility-reporter/](https://addons.mozilla.org/en-US/firefox/addon/add-on-compatibility-reporter/)

---

### Post by Lucradia on 2011-12-24
> **lovinglinux said:**
> Wow, 42Mb just for Gmail. This is interesting, to show people how different pages use different amount of memory. That "I have x tabs open" is not a good parameter when dealing with memory troubleshooting.

Same tabs, switched to google HTML for GMail instead.

[http://i.imgur.com/lxQX4.jpg](http://i.imgur.com/lxQX4.jpg)

Notice though, GMail is no longer listed, instead, there's a plus.google.com URL.

---

### Post by lovinglinux on 2011-12-24
> **Lucradia said:**
> Same tabs, switched to google HTML for GMail instead.

[http://i.imgur.com/lxQX4.jpg](http://i.imgur.com/lxQX4.jpg)

Notice though, GMail is no longer listed, instead, there's a plus.google.com URL.


Gmail - 14Mb on start. 

[IMG]http://i.imgur.com/NrIlk.png[/IMG]

Let's see what happens if I leave it open a few hours.

---

