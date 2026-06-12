---
title: "Why do no browsers seem to have the ability to do a REAL force refresh?"
date: 2009-11-28
forum: The Cafe
---

### Post by hoppipolla on 2009-11-28
This is annoying me soooo much ._.

I make a change to my site (something small), switch to Chrome and refresh... no change. I press F5... no change. I press Ctrl+F5 or Shift+F5 or Shift/Ctrl+Refresh button... no change :(

I open a new browser which hasn't viewed the page before and suddenly I can see my change(s)!

So why can't I just force Chrome or Firefox or whatever to completely reload the page without checking it's cache or anything? It would save me so much time!

Thanks all!

Hoppi :)

---

### Post by Islington on 2009-11-28
holding down the Shift key while clicking on the refresh button works for me. ctrl f5 seems to be a windows specific thing.

---

### Post by Islington on 2009-11-28
Edit: I was wrong ctrl+f5 should work: [http://support.mozilla.com/en-US/kb/Keyboard+shortcuts](http://support.mozilla.com/en-US/kb/Keyboard+shortcuts)

---

### Post by hoppipolla on 2009-11-28
I know they SHOULD it's just... they never seem to ._.

Not when doing loads of changes to your site, I just find that it might refresh the images but it doesn't grab the html from the server again, which is what I need it to do ._.

---

### Post by dragos240 on 2009-11-28
CTRL + R usually works for all browsers.

---

### Post by BuffaloX on 2009-11-28
> **dragos240 said:**
> CTRL + R usually works for all browsers.

Thanx I'll try that next time, usually I have to purge my cache, then refresh.

Can anyone confirm this really works. It seems to work, but I don't have anything to test on right now.

---

### Post by jpmelos on 2009-11-28
Weird, for me it always worked with a simple CTRL+F5... Even if I change a single character on the page. I'm using Firefox 3.5.5.

---

### Post by Hells_Dark on 2009-11-28
Maybe your server doesnt refresh as fast :D

(I mean it's not always browser fault&#8230; servers, routers, etc)

---

### Post by v8YKxgHe on 2009-11-28
This is why it's quite common to append a number query string to things like JavaScript files etc, to force the browser to download the new version, e.g. assets/js/foobar.js?1234

---

### Post by Ylon on 2009-11-28
Looks like an issue relative to .css file.. wich were usually treated differently than other page elements.

---

### Post by hoppipolla on 2009-11-28
> **dragos240 said:**
> CTRL + R usually works for all browsers.

I'll give that one a go :)

> **AlexC_ said:**
> This is why it's quite common to append a number query string to things like JavaScript files etc, to force the browser to download the new version, e.g. assets/js/foobar.js?1234

I don't fully understand this, do you mean just renaming the file?

---

### Post by v8YKxgHe on 2009-11-29
> I don't fully understand this, do you mean just renaming the file? 

Renaming the file *would* work, yes. However what I mean is to just append a query string to the URL, because to the browser this is a different URL now and so downloads the 'new' copy. It's a very common thing to do on production sites (and large development teams) since it ensures that end-users wont get a half-broken site if you example, you change the CSS but keep the same name.

---

### Post by spupy on 2009-11-29
It's not always the browser. I think some proxies do caching as well. The remedy in that case is the mentioned method of appending some nonsense to the url.

---

### Post by SunnyRabbiera on 2009-11-29
Clearing cache is the only real way to keep pages 100% refresh.
I use no cache personally, I always set mine to 0MB in firefox/opera.

---

### Post by betrunkenaffe on 2009-11-29
Kill the cache when doing testing on your own work. You will save yourself alot of pain.

That being said, a master refresh only forces the browser to grab the latest of the target page (not every page that the target links to). Hence the css and js files will all be out of date. I've never tried the suggestion to append "?version" but looks like it will work. Does that work for css files as well because that will save me alot of grief at work where I can't turn off cache. :)

---

### Post by v8YKxgHe on 2009-11-29
> **betrunkenaffe said:**
> Kill the cache when doing testing on your own work. You will save yourself alot of pain.

That being said, a master refresh only forces the browser to grab the latest of the target page (not every page that the target links to). Hence the css and js files will all be out of date. I've never tried the suggestion to append "?version" but looks like it will work. Does that work for css files as well because that will save me alot of grief at work where I can't turn off cache. :)

It works for anything, it's just a URL.

---

### Post by chucky chuckaluck on 2009-11-29
does setting cache at 0 hurt the back button's functioning?

---

### Post by v8YKxgHe on 2009-11-29
You really shouldn't set your browser to not cache, if anything but to help take load of peoples servers.

---

### Post by hoppipolla on 2009-11-29
> **AlexC_ said:**
> Renaming the file *would* work, yes. However what I mean is to just append a query string to the URL, because to the browser this is a different URL now and so downloads the 'new' copy. It's a very common thing to do on production sites (and large development teams) since it ensures that end-users wont get a half-broken site if you example, you change the CSS but keep the same name.

oh ok, so... any URL? So like let's say we have one of my sites:

[http://www.twitteractivism.com/index.php](http://www.twitteractivism.com/index.php) ... what comes after? *?12345* ?

Sorry, I'm not too hot on this stuff! And then I just change the string of numbers to make it reload? 

oh and my other one is html... same deal?

Sorry, excuse my ignorance on this one! :)

---

### Post by v8YKxgHe on 2009-11-29
> oh ok, so... any URL? So like let's say we have one of my sites:

[http://www.twitteractivism.com/index.php](http://www.twitteractivism.com/index.php) ... what comes after? ?12345 ?

Sorry, I'm not too hot on this stuff! And then I just change the string of numbers to make it reload? 

oh and my other one is html... same deal?

Sorry, excuse my ignorance on this one! 

No, it would come after your CSS/JavaScript files. For example:

```
<script type="text/javascript" src="assets/js/foo.js?v=2"></script>
```

When ever you alter the JavaScript file, simply change the 'v=2' for 'v=3' or, 4, 5, 6 etc etc. All you're doing is appending what is called a query string to the URL, GET arguments in the HTTP request.

How do you mean with HTML?

---

### Post by hoppipolla on 2009-11-29
> **AlexC_ said:**
> No, it would come after your CSS/JavaScript files. For example:

```
<script type="text/javascript" src="assets/js/foo.js?v=2"></script>
```

When ever you alter the JavaScript file, simply change the 'v=2' for 'v=3' or, 4, 5, 6 etc etc. All you're doing is appending what is called a query string to the URL, GET arguments in the HTTP request.

How do you mean with HTML?

oh ok i think I understand now!

Although MEGA weirdly, when I just bunged in the equivalent of:

[http://www.twitteractivism.com/index.php?1234](http://www.twitteractivism.com/index.php?1234)

it refreshed perfectly! Weird no? Is it just because that's a query being passed to the browser about the page? O.O

It even worked without me having to change the string each time, so I just F5'd the page the 1234 on the end and it did it fine!

Weeeeeiiiird! ^_^

I hope it keeps working as this is SO easy!

---

### Post by ssam on 2009-11-29
surely there is a firefox extension to disable all caching or something similar.

---

