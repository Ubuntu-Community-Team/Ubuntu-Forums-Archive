---
title: "Firefox really needs &quot;Electrolysis&quot; - lack of stability makes it tough to use"
date: 2011-03-27
forum: The Cafe
---

### Post by nrundy on 2011-03-27
I really like Firefox 4 but man does it slow down the computer when you have a dozen or more tabs open and have been browsing for a while. The only solution is to have to close Firefox and restart. This blows when you're browsing in Private mode cause you lose everything. Major PITA!

I always end up switching to Chromium so everything stays stable while I'm browsing and I can finish what I'm doing without having to restart the browser. I prefer Firefox overall but its lack of stability makes it tough to use. If it had multi-process like Chromium it would be the Best. I cannot wait for Firefox to get multi-process capabilities for Tabs etc.

---

### Post by lovinglinux on 2011-03-27
Firefox is pretty much stable for me and I don't experience any problems.

Perhaps you have some extensions leaking memory or you are opening too many pages with flash content.

See my tutorials on how to optimize and troubleshoot Firefox problems.

[http://www.webgapps.org/blogs/firefox-tutorials](http://www.webgapps.org/blogs/firefox-tutorials)

---

### Post by An Sanct on 2011-03-27
Firefox is "multiprocess capable", take a look at [this article]("http://blog.mozilla.com/cjones/2009/06/21/multi-process-firefox-coming-to-an-internets-near-you/") or at [this one]("http://techie-buzz.com/browsers/mozilla-firefox-multiprocess.html").

PS. kudos to lovinglinux for flash aid!

---

### Post by lovinglinux on 2011-03-27
> **An Sanct said:**
> PS. kudos to lovinglinux for flash aid!

Thanks :-)

---

### Post by dh04000 on 2011-03-27
> **An Sanct said:**
> Firefox is "multiprocess capable", take a look at [this article]("http://blog.mozilla.com/cjones/2009/06/21/multi-process-firefox-coming-to-an-internets-near-you/") or at [this one]("http://techie-buzz.com/browsers/mozilla-firefox-multiprocess.html").

PS. kudos to lovinglinux for flash aid!

The newest firefox 4 already has this as true.

---

### Post by nrundy on 2011-03-27
> **An Sanct said:**
>  
PS. kudos to lovinglinux for flash aid!

 Yeah, I agree. Kudos! It is awesome and saves me much headache.  PS: I only run 3 extensions: adblock, noscript, and flash-aid

---

### Post by nrundy on 2011-03-27
> **An Sanct said:**
> Firefox is &quot;multiprocess capable&quot;, take a look at [this article]("http://blog.mozilla.com/cjones/2009/06/21/multi-process-firefox-coming-to-an-internets-near-you/") or at [this one]("http://techie-buzz.com/browsers/mozilla-firefox-multiprocess.html").

PS. kudos to lovinglinux for flash aid!

 they were able to multi the flash plugin etc. they still haven't implemented chrome like multi-process that allows the os to reclaim memory when tabs are closed. use firefox for a long time and open a lot of tabs and things get bogged down cause closing tabs won't reclaim memory. Only way to reclaim is to restart browser.

---

### Post by Dustin2128 on 2011-03-27
I don't use much flash, but I almost always have about 12 tabs open and it performs well for me. And thanks for the tutorials site lovinglinux.

---

### Post by lovinglinux on 2011-03-27
> **nrundy said:**
> Yeah, I agree. Kudos! It is awesome and saves me much headache.  PS: I only run 3 extensions: adblock, noscript, and flash-aid

Cool 8-)

> **Dustin2128 said:**
> I don't use much flash, but I almost always have about 12 tabs open and it performs well for me. And thanks for the tutorials site lovinglinux.

You are welcome.

> **nrundy said:**
> they were able to multi the flash plugin etc. they still haven't implemented chrome like multi-process that allows the os to reclaim memory when tabs are closed. use firefox for a long time and open a lot of tabs and things get bogged down cause closing tabs won't reclaim memory. Only way to reclaim is to restart browser.

Try [BarTab]("https://addons.mozilla.org/en-US/firefox/addon/67651/") extension. Also try starting Firefox in safe mode and check if the problem persists.

---

### Post by Dustin2128 on 2011-03-27
> **lovinglinux said:**
> Cool 8-)



You are welcome.



Try [BarTab]("https://addons.mozilla.org/en-US/firefox/addon/67651/") extension. Also try starting Firefox in safe mode and check if the problem persists.
bartab isn't available for firefox 4...

---

### Post by beew on 2011-03-27
> **Dustin2128 said:**
> bartab isn't available for firefox 4...

It is, I am using it right now. :)

---

### Post by Dustin2128 on 2011-03-28
> **beew said:**
> It is, I am using it right now. :)
Oh?

---

### Post by lovinglinux on 2011-03-28
> **Dustin2128 said:**
> bartab isn't available for firefox 4...

Get version 2.1b2

[https://addons.mozilla.org/en-US/firefox/addon/bartab/versions/2.1b2](https://addons.mozilla.org/en-US/firefox/addon/bartab/versions/2.1b2)

---

### Post by beew on 2011-03-28
> **Dustin2128 said:**
> Oh?

Here are my screenshots. As you can see from the second one I have many tabs stored but none of them is loaded.

---

### Post by nrundy on 2011-03-28
lovinglinux, what plugin do you replace flash with when using your replace flash plugin?

---

### Post by An Sanct on 2011-03-28
As much as I understand it, it is a bash script, that downloads the newest flash plugin binaries and replaces the existing ones (they are in known locations). [The plugin is Flash Aid]("https://addons.mozilla.org/en-us/firefox/addon/flash-aid/").

---

### Post by nrundy on 2011-03-28
He has another plugin called "flashVideoReplacer"

---

### Post by An Sanct on 2011-03-28
> **nrundy said:**
> He has another plugin called "flashVideoReplacer"

[FlashVideoReplacer]("https://addons.mozilla.org/en-us/firefox/addon/flashvideoreplacer/")

---

### Post by lovinglinux on 2011-03-28
> **nrundy said:**
> lovinglinux, what plugin do you replace flash with when using your replace flash plugin?

The plugin used depends on what you have installed. The recommended is gecko-mediaplayer. Totem, which comes by default with Ubuntu needs a little trick to work.

---

### Post by nrundy on 2011-03-29
> **lovinglinux said:**
> Firefox is pretty much stable for me and I don't experience any problems.

Perhaps you have some extensions leaking memory or you are opening too many pages with flash content.

See my tutorials on how to optimize and troubleshoot Firefox problems.

[http://www.webgapps.org/blogs/firefox-tutorials](http://www.webgapps.org/blogs/firefox-tutorials)

A consistent problem I have is slow downs when I've been using it a while. The only way to fix it is to restart. So I close the program and then open it again and I get the message something to the affect that "Firefox is already running, but is not responding . . . ." So I have to wait and wait and then try to open it again. Eventually I get it open and have to start browsing best I can from where I was. But having to wait for it to "settle down" and reopen and the work/time delay the whole ordeal entails is really irksome.

Another thing that causes me trouble is having to restart firefox every time I enable or disable an extension. Sometimes I disable a couple of them, finish doing something in a Tab, and then manually close the browser. Then I'll manually open Firefox so that I can start browsing with the extensions disabled and dangit I get that "Firefox is already running, but is not responding . . . ." message again.

Firefox does crash on me from time to time--I always send the report to Mozilla. I've never had Chromium crash on me a single time. An extension crashed once. Chromium gave me a little cartoon icon saying the extension crashed and an option to reload it. Couldn't have been easier.

Really looking forward to Firefox gaining multi-process design!

---

