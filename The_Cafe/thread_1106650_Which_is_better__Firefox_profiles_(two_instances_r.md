---
title: "Which is better:  Firefox profiles (two instances running) or Firefox + Epiphany?"
date: 2009-03-25
forum: The Cafe
---

### Post by Dngrsone on 2009-03-25
Okay, I have FF 3 all loaded up with add-ons and gadgets and whatnot for my primary internet surfing pleasure.

I have a WordPress locally installed on my laptop (no internet needed), which, of course, requires me to access via web browser.

I prefer to have a minimalized browser for working in WP (because there's so little room in the Post window to begin with) since I don't need all the gadgets and whatnot for editing and publishing posts.

So, my choice is such-- create a second Firefox profile with few frills (except the Littlefox theme--> minimalized) and create a special link to open it up for my journaling pleasure, or install the Epiphany browser and use that for WP, making it an entirely separate thing.

Which would be better, and for why?

---

### Post by dmizer on 2009-03-25
Moved this to the cafe.

Carry on.

---

### Post by smartboyathome on 2009-03-26
I'd say that using two Firefox profiles would be best since Epiphany (the Gecko version) is horribly slow and Epiphany (the Webkit version) lacks many features.

---

### Post by Mr. Picklesworth on 2009-03-26
You may want to look at Prism, which provides sort of a stripped-down browser for "web apps" :)
A neat thing with it is that, since it's simpler, Prism allows the web apps more control over handlers for right clicking, keyboard shortcuts, etc. than a regular browser allows.

---

### Post by Dngrsone on 2009-03-26
Thanks, guys.  I looked at Prism; it is a little too minimalist, I think-- can't navigate back to the Dashboard once I go visit the site.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]

I suppose I will stick with the Firefox profiles.


Now all I need is a simple rich text editor that won't throw in a bunch of formatting when I cut/paste into WP... I suppose that's a different topic, though.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/rolleyes.gif[/IMG]

---

### Post by binbash on 2009-03-26
Firefox profiles is better, epiphany lacks many features

---

### Post by smartboyathome on 2009-03-26
> **Dngrsone said:**
> Now all I need is a simple rich text editor that won't throw in a bunch of formatting when I cut/paste into WP... I suppose that's a different topic, though.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/rolleyes.gif[/IMG]

I would recommend Gedit. It doesn't do formatting, but it does have syntax highlighting (very useful).

---

### Post by Dngrsone on 2009-03-26
Okay, Profiles it is... already set up.  Now if only I could find a way to make it so that the program icons in the panel could be different (so I know which profile I'm switching to between desks), life would be nearly perfect.

Only issue I have with Gedit is that it doesn't have simple formatting-- I'm writing articles and such and I need to apply the occasional italic or bold.

This is interesting-- you can call up multiple copies of the same Firefox profile in 8.10... in 8.04 and below, it throws an error saying Firefox is already running.

---

### Post by k3ttc4r on 2009-03-26
well, you could just do it in html, i suppose.. it's not that hard to add a tag for italic or bold..

---

### Post by Mr. Picklesworth on 2009-03-26
Argh, it really grinds my gears when people pass Epiphany off as "lacking many features." It doesn't lack *any* features. It's a web browser, and it isn't Firefox. (And if we're going to compare features, try opening a file in Firefox that the browser itself doesn't understand. Epiphany actually integrates with FreeDesktop specifications, so doing that is a nice, smooth process).

For what it's worth, you can run epiphany-browser -p to get a sort of temporary session alongside the existing one.

---

### Post by Dngrsone on 2009-03-26
> **Mr. Picklesworth said:**
> Argh, it really grinds my gears when people pass Epiphany off as "lacking many features." It doesn't lack *any* features. It's a web browser, and it isn't Firefox. (And if we're going to compare features, try opening a file in Firefox that the browser itself doesn't understand. Epiphany actually integrates with FreeDesktop specifications, so doing that is a nice, smooth process).

For what it's worth, you can run epiphany-browser -p to get a sort of temporary session alongside the existing one.

Actually, I didn't have any issues with Epiphany (well... I could have used a few add-ons), and it seemed to move a teeny bit faster than Firefox, but then, there's the add-ons I have running in the latter.

Some people have said in other forums that Epiphany is sluggish, though.  Care to comment on that?

---

### Post by smartboyathome on 2009-03-26
> **Mr. Picklesworth said:**
> Argh, it really grinds my gears when people pass Epiphany off as "lacking many features." It doesn't lack *any* features. It's a web browser, and it isn't Firefox. (And if we're going to compare features, try opening a file in Firefox that the browser itself doesn't understand. Epiphany actually integrates with FreeDesktop specifications, so doing that is a nice, smooth process).

For what it's worth, you can run epiphany-browser -p to get a sort of temporary session alongside the existing one.

If a web browser doesn't support simple stuff such as cookies, then I will pass it off as lacking features (epiphany webkit doesn't have cookie support as of the 2.24 release). The reason I don't use the gecko version is because it is slower compared to Firefox when it comes to loading pages.

---

### Post by Mr. Picklesworth on 2009-03-26
> **smartboyathome said:**
> If a web browser doesn't support simple stuff such as cookies, then I will pass it off as lacking features (epiphany webkit doesn't have cookie support as of the 2.24 release). The reason I don't use the gecko version is because it is slower compared to Firefox when it comes to loading pages.

That's why the supported version as of now is the gecko version ;)
Webkit is coming in 2.28, probably.

---

### Post by ssam on 2009-03-26
if you want to run two profiles at once this might help
[http://weblogs.java.net/blog/felipeal/archive/2007/02/firefox_profile.html](http://weblogs.java.net/blog/felipeal/archive/2007/02/firefox_profile.html)

an other solution is to create another user (mine is called failfox), and then run
```

ssh -X failfox@localhost firefox
```

i have flash installed in failfox's ~/.mozilla/plugins as 99% of the time its nicer to browse the web without flash.

i use ssh rather than su as i could not be bothered to trace the DISPLAY problem, and i already have openssh-server installed

---

