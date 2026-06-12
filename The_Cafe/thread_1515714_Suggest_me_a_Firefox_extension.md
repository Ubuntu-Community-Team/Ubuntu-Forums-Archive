---
title: "Suggest me a Firefox extension"
date: 2010-06-22
forum: The Cafe
---

### Post by Nonno Bassotto on 2010-06-22
I do not have currently much spare time, but as soon as I have some I'd like to learn XUL. I guess the best way to learn is to program a Firefox extension, but the problem is that there are too many out there. I just cannot figure out what a new useful extension would do.

So, here is the thing. Can you propose me an extension for which you feel the need, but that does not exist yet? Preferably not something too complicated, as this would be my first extension. I will then choose my favourite and write it (again, it will not be immediately since I'm short of time right now).

---

### Post by lovinglinux on 2010-06-22
You might want to check the [XUL School Tutorial](https://developer.mozilla.org/en/XUL_School).

If you need any help, please let me know. I develop a [few extensions for Firefox](http://lovinglinuxblog.blogspot.com) - 7 approved, 1 experimental, 1 not released yet and 2 for personal use only.

I don't have any ideas for a simple extension right now, but I will let you know when I have one.

---

### Post by SoFl W on 2010-06-22
To start off why don't you look at another Firefox extension that you already like and modify it for your tastes?

---

### Post by Nonno Bassotto on 2010-06-23
Uhm... Two answers and no suggestions... I guess this means that every possible extension already exists? :confused:

---

### Post by Legendary_Bibo on 2010-06-23
I have an idea! make an extension that will go through my bookmarks that I look through on a daily basis, and have it where I can hit a button and it'll load up my next bookmark. Usually I just have my bookmarks open, but I hate having to click through the list...

---

### Post by lovinglinux on 2010-06-23
> **Nonno Bassotto said:**
> Uhm... Two answers and no suggestions... I guess this means that every possible extension already exists? :confused:

No, that's not true. I have a couple of ideas, but I don't think they are good ones for someone who is starting. To be honest, I don't even know how to implement them yet, otherwise I would have started them already.

Anyway, I started one extension a few of weeks ago but stopped developing it. Perhaps you want to take over. It is a simple extension that adds a button to the toolbar that opens a popup menu with links to Ubuntu related sites. I'm not going to give you my code, because it was a mess when I stopped and it uses some advanced database stuff, but I can orient you through the first steps of creating one if you want.

BTW, do you know javascript?

---

### Post by lovinglinux on 2010-06-23
> **Legendary_Bibo said:**
> I have an idea! make an extension that will go through my bookmarks that I look through on a daily basis, and have it where I can hit a button and it'll load up my next bookmark. Usually I just have my bookmarks open, but I hate having to click through the list...

In the bookmarks sidebar, look for the "Most Visited" folder, right-click on it and select "Open All in Tabs".

---

### Post by TheNessus on 2010-06-23
.

---

### Post by madnessjack on 2010-06-23
I've got an idea!

Multiple server switcher. Like the already popular [server switcher addon](https://addons.mozilla.org/en-US/firefox/addon/2409/), but one that works with multiple development environments. It's very sought after.

---

### Post by Random_Dude on 2010-06-23
I read a lot of blogs, so I have them all in one folder on my bookmarks.
When I turn on firefox to read the recent updates I click to open all in tabs, but most of them don't have any new posts and I makes my internet connection and pc slower to open so many tabs at the same time.

Is there a way to open only the blogs which got an update since I last visited them?
Does this already exist?

---

### Post by Legendary_Bibo on 2010-06-23
> **lovinglinux said:**
> In the bookmarks sidebar, look for the "Most Visited" folder, right-click on it and select "Open All in Tabs".

I don't like having so many bookmarks open. It gets all cluttered and slow.

---

### Post by lovinglinux on 2010-06-23
> **Random_Dude said:**
> I read a lot of blogs, so I have them all in one folder on my bookmarks.
When I turn on firefox to read the recent updates I click to open all in tabs, but most of them don't have any new posts and I makes my internet connection and pc slower to open so many tabs at the same time.

Is there a way to open only the blogs which got an update since I last visited them?
Does this already exist?

You can use [Specto](apt:specto) for that. It can check web sites for modifications and launch a command when they find a certain percentage of new content.

---

### Post by Nonno Bassotto on 2010-06-23
Thank you all for your ideas!

@lovinglinux: Yes, of course I know javascript. :-)

---

### Post by lovinglinux on 2010-06-23
> **Nonno Bassotto said:**
> @lovinglinux: Yes, of course I know javascript. :-)

What I mean is, can you write javascript code? If yes, then learning how to create FF extensions will be easy.

---

### Post by Nonno Bassotto on 2010-06-23
Yes, of course I'm used to writing javascript. I wouldn't try to learn XUL otherwise.

---

### Post by lovinglinux on 2010-06-23
> **Nonno Bassotto said:**
> Yes, of course I'm used to writing javascript. I wouldn't try to learn XUL otherwise.

I didn't know javascript when I started developing Firefox extensions :)

It was hard, but I'm more or less comfortable with it now.

I have a new suggestion then. Make an extension that backup/restore Firefox search engines. Whenever you upgrade Firefox in Ubuntu, the search engines order gets completely messed up and the default search engines are added every time. It is really annoying. An extension that would allow to backup and restore the search engines would make a lot of people happy.

---

### Post by Nonno Bassotto on 2010-06-25
Ok, I got the following suggestions:

> **Legendary_Bibo said:**
> I have an idea! make an extension that will go through my bookmarks that I look through on a daily basis, and have it where I can hit a button and it'll load up my next bookmark. Usually I just have my bookmarks open, but I hate having to click through the list...

> **lovinglinux said:**
> Anyway, I started one extension a few of weeks ago but stopped developing it. Perhaps you want to take over. It is a simple extension that adds a button to the toolbar that opens a popup menu with links to Ubuntu related sites.

> **madnessjack said:**
> Multiple server switcher. Like the already popular [server switcher addon](https://addons.mozilla.org/en-US/firefox/addon/2409/), but one that works with multiple development environments. It's very sought after.

> **Random_Dude said:**
> I read a lot of blogs, so I have them all in one folder on my bookmarks.
When I turn on firefox to read the recent updates I click to open all in tabs, but most of them don't have any new posts and I makes my internet connection and pc slower to open so many tabs at the same time.

Is there a way to open only the blogs which got an update since I last visited them?
Does this already exist?

> **lovinglinux said:**
> Make an extension that backup/restore Firefox search engines. Whenever you upgrade Firefox in Ubuntu, the search engines order gets completely messed up and the default search engines are added every time. It is really annoying. An extension that would allow to backup and restore the search engines would make a lot of people happy.

Next week I may have some spare time and start learning how to make extensions. I will let you know as soon as I develop one of those.

By the way, I think I will not do the extension suggested by RandomDude, since I'd basically rewrite Specto. But a small (and simpler variant) may be worth the pain: adding a menu entry "Open unread" to the RSS feeds.

---

### Post by capink on 2010-06-25
Mozilla are developing a new extension API called jetpack. You can google for it or read more details [here]("http://news.cnet.com/8301-17939_109-10245934-2.html").

---

### Post by lovinglinux on 2010-06-25
> **capink said:**
> Mozilla are developing a new extension API called jetpack. You can google for it or read more details [here]("http://news.cnet.com/8301-17939_109-10245934-2.html").

Too soon to start working with Jetpack in my opinion.

---

### Post by mamamia88 on 2010-06-25
when i right click new tab i would like it to open to right of current one.  extensions i've tried don't work

---

### Post by mmix on 2010-06-25
multi line bookmark bar for firefox 3.7 series.

actually there is one addon for this, but 1.

[https://addons.mozilla.org/en-US/firefox/addon/6937/](https://addons.mozilla.org/en-US/firefox/addon/6937/)

---

### Post by Nonno Bassotto on 2010-06-26
> **capink said:**
> Mozilla are developing a new extension API called jetpack. You can google for it or read more details [here]("http://news.cnet.com/8301-17939_109-10245934-2.html").

Thank you, I know of JetPack. I'm not sure I want to develop with it. Actually my aim is not to develop extensions, but rather to learn XUL, in order to use it in stand-alone applications. I don't know much about Jetpack, but I think it is not based on XUL.

> **mamamia88 said:**
> when i right click new tab i would like it to open to right of current one.  extensions i've tried don't work

If I understand correctly, that is the default behaviour since Firefox 3.6.

> **mmix said:**
> multi line bookmark bar for firefox 3.7 series.

actually there is one addon for this, but 1.

[https://addons.mozilla.org/en-US/firefox/addon/6937/](https://addons.mozilla.org/en-US/firefox/addon/6937/)

I'm not sure I understand. Are you saying I should write this already existing extension?

---

### Post by lovinglinux on 2010-06-26
> **mamamia88 said:**
> when i right click new tab i would like it to open to right of current one.  extensions i've tried don't work

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **tabs.insertRelatedAfterCurrent** in the filter, then double-click the same item in the results to make it **false**.

---

### Post by mmix on 2010-06-26
> **Nonno Bassotto said:**
> 
I'm not sure I understand. Are you saying I should write this already existing extension?

Yes, it doesn't works for FF nightly version (3.7).
Anyway, it just a suggestion.

---

### Post by d3v1150m471c on 2010-06-26
streaming media recorder would be nice

---

### Post by lovinglinux on 2010-06-26
> **mmix said:**
> Yes, it doesn't works for FF nightly version (3.7).
Anyway, it just a suggestion.

That extension is under active development is already compatible with 3.7a3pre, so IMO is a waste of time doing another one. 

You can use that extension on nightly builds by disabling compatibility check. I usually recommend [Add-on Compatibility Reporter](https://addons.mozilla.org/en-US/firefox/addon/15003/), but it doesn't work with nightly builds. So you need to disable the compatibility check in Firefox preferences.  

Type **about[noparse]:[/noparse]config** in Firefox address bar, then create a new Boolean entry named **extensions.checkCompatibility.3.7a**, if you are running version 3.7a6pre or similar. You don't need to include the 6pre part. Make the value **false**. More info at [http://kb.mozillazine.org/Updating_extensions#Completely_disabling_the_compatibility_check](http://kb.mozillazine.org/Updating_extensions#Completely_disabling_the_compatibility_check)

---

### Post by d3v1150m471c on 2010-06-26
lol love the avatar lovinglinux. nicely done

---

### Post by lovinglinux on 2010-06-26
> **d3v1150m471c said:**
> lol love the avatar lovinglinux. nicely done

Thanks. It is just temporary, until the World Cup ends or Brazil gets kicked off. Then [my regular avatar](http://sites.google.com/site/lovinglinux/files/cylontux.png?attredirects=0) comes back.

---

### Post by mmix on 2010-06-26
I am using 3.7a6pre.

Another reason, i don't like the existent addon, because,
It doesn't support left-side panel.

only 1 addon for multi line bookmark bar, and it doesn't cover all.

That's my point.

---

### Post by Nonno Bassotto on 2010-07-08
Finally, here it is my first extension, Morning Bookmarks. It allows to cycle through a series of commonly used bookmarks, typically newspaper sites that you use read every morning. Thanks to Legendary_Bibo for the idea. You can find it [here]("http://www.andreaferretti.it/files/morningbookmarks.xpi"). Now that I have done it, I realize it is not very different from [Morning Coffee]("https://addons.mozilla.org/it/firefox/addon/2677/"). But, well, I didn't look very well :-)

The only thing which is missing is a set of icons suitable for MacOS. When I add that I will propose the extension to Mozilla Add-ons.

After writing it, I realize I spent most of the time not developing the features (which admittedly are very few) but trying to understand how to work with preferences, or how to put the entries where they belong, or how to do a clean uninstall. So hopefully I should be quicker next times.

Now, let's move to next extension...

---

### Post by lovinglinux on 2010-07-08
> **Nonno Bassotto said:**
> Finally, here it is my first extension, Morning Bookmarks. It allows to cycle through a series of commonly used bookmarks, typically newspaper sites that you use read every morning. Thanks to Legendary_Bibo for the idea. You can find it [here]("http://www.andreaferretti.it/files/morningbookmarks.xpi"). Now that I have done it, I realize it is not very different from [Morning Coffee]("https://addons.mozilla.org/it/firefox/addon/2677/"). But, well, I didn't look very well :-)

The only thing which is missing is a set of icons suitable for MacOS. When I add that I will propose the extension to Mozilla Add-ons.

After writing it, I realize I spent most of the time not developing the features (which admittedly are very few) but trying to understand how to work with preferences, or how to put the entries where they belong, or how to do a clean uninstall. So hopefully I should be quicker next times.

Now, let's move to next extension...

Congratulations. Your extension is really nice. 

I'm sure next time will be much easier for you. I'm currently rewriting an old extension of mine and is not only a lot easier, but the extension is way much better now.

BTW, I can't find a way to remove a bookmark from it. I guess I'm missing something. Anyway, good luck on your next project.

---

### Post by Nonno Bassotto on 2010-07-08
You can add, remove and order the bookmarks under Tools->Morning Bookmarks.

---

### Post by lovinglinux on 2010-07-08
> **Nonno Bassotto said:**
> You can add, remove and order the bookmarks under Tools->Morning Bookmarks.

Thanks. Really nice.

---

