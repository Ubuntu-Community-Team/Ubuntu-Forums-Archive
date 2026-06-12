---
title: "Firefox statusbar customization"
date: 2006-09-01
forum: The Cafe
---

### Post by roderikk on 2006-09-01
Hello,

Would anybody happen to know whether there is a firefox plugin/setting to let the progress bar 'progress' in the navigation bar like in Safari?

Thanks!

---

### Post by kerry_s on 2006-09-01
I've never seen Safari's one, but i'm guessing its like the one in opera. Try this one-> [https://addons.mozilla.org/firefox/1433/](https://addons.mozilla.org/firefox/1433/)

---

### Post by roderikk on 2006-09-01
Actually, I wanted to get rid of the statusbar. Safari displays the progress of downloading a page in the navigation bar (where you type a link, this slowly turns blue while loading a page). Would this be possible?

Besides this I was wondering whether the close buttons for the tabs could be positioned on the tabs themeselves (like Epiphany).

I've already found a way to put the scrollbar buttons together [here]("http://cheeaun.phoenity.com/weblog/2004/08/scrollbar-tweaks.html"). But I can't seem to get it to work. I've put the stylecode into userChrome.css ánd in userContent.css. Does anyone actually does get it to work?

---

### Post by roderikk on 2006-09-01
Ok, after some searching I have been able to solve some of my 'problems'.

Installing the TabFX extension will put the close tab button at each tab (as will be the case in FF2).

I've also installed the Stop-or-Reload Button plugin, this makes the stop and reload button into one button, displaying the reload button only when a page has loaded and the stop button while it is still loading.

I've also completely removed my vertical scrollbar by putting this line into my userChrome.css and userContent.css file (in the chrome folder of your profile, you have to create those yourself).

```
scrollbar[orient="vertical"] { display: none !important; }
```

This is just because I think it looks very sleek....

Now just for the status bar inside the navigation bar and I am all set...

EDIT: Added a screenshot... :-)

---

