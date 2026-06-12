---
title: "Sudden, unexpected freezes"
date: 2012-12-08
forum: Ubuntu Studio
---

### Post by Inoki on 2012-12-08
Hi guys,

lately I'm experiencing these unexpected, randomly, from time to time occurring freezes when using Chrome. Any ideas why this happens?

I'm on Ubuntu Studio 12.10 x64 bit with kernel pinned to version 3.5.17 (base kernel) but get all the other updates.

As mentioned, this only occurred while using Chrome so far, thus am unable to provide any logs.

It seems odd to me as I couldn't experience any higher CPU usage.

---

### Post by 2F4U on 2012-12-08
Are you able to detect a pattern behind the freezing, for example, always happens when application X is also running, or always happens when visiting a particular website?

---

### Post by Inoki on 2012-12-08
> **2F4U said:**
> Are you able to detect a pattern behind the freezing, for example, always happens when application X is also running, or always happens when visiting a particular website?
Mostly this occurs on Facebook. I think I didn't observe such behaviour when visiting other sites.

---

### Post by irv on 2012-12-08
I had the same problem back in Oct. I had an ongoing thread on this. here is the link: [http://ubuntuforums.org/showthread.php?t=2008813]("http://ubuntuforums.org/showthread.php?t=2008813")
If you read through the tread, you will see some of the things that were happen to me. Maybe it might help to fine out what is going on.

---

### Post by Inoki on 2012-12-08
Ok, correction, this does not happen on Facebook only. I monitored the memory usage of Chrome and I've got 4 GB of RAM, Chrome eating 1.5k of it, that could be the problem I guess.

I know alternatively I could use Firefox, but that's an even greater resource eater.

Any suggestion on how to optimize Chrome possibly (I know removing a few addons could do)? I am well aware what people say, that Chrome eats a lot of CPU and RAM due to it opening every tab as a new window.

Is there a big difference between Chromium and Chrome when it comes to memory usage? Although I highly doubt it.

Alternatively, can someone recommend a good, lightweight web browser with excellent web support and somewhat support for addons? I'd highly appreciate, if that particular browser had prepense bookmark handling (great export features for backup and restore) and possibly Greasemonkey and an Adblocker.

Thanks to all in advance.

---

### Post by irv on 2012-12-08
> **Anathaen said:**
> Ok, correction, this does not happen on Facebook only. I monitored the memory usage of Chrome and I've got 4 GB of RAM, Chrome eating 1.5k of it, that could be the problem I guess.

I know alternatively I could use Firefox, but that's an even greater resource eater.

Any suggestion on how to optimize Chrome possibly (I know removing a few addons could do)? I am well aware what people say, that Chrome eats a lot of CPU and RAM due to it opening every tab as a new window.

Is there a big difference between Chromium and Chrome when it comes to memory usage? Although I highly doubt it.

Alternatively, can someone recommend a good, lightweight web browser with excellent web support and somewhat support for addons? I'd highly appreciate, if that particular browser had prepense bookmark handling (great export features for backup and restore) and possibly Greasemonkey and an Adblocker.

Thanks to all in advance.
A couple of point, 4 GB is more then enough RAM to run both Chrome and Fire Fox together.
[ATTACH]228388[/ATTACH]
And if Chrome is only using 1.5k that nothing. I use all three browser from time to time, Chrome, FF, and Chromium. I use different browser for different things. Overall memory usage I believe is not an issue. Now temperature could be. If your CPU runs to hot it could cause a lockup.

---

### Post by Inoki on 2012-12-08
Heya,

temperature definitely ain't the issue. It's 47° Celsius. I've also had my laptop cleaned a while ago.

I strongly believe this is browser related, but wasn't occurring 'till I didn't have a Fakebook account :D And since I don't run any browser no freezes, only when I run the browser.

It could also be related to Google's latest update of the browser, who knows.

I've also had a look at the thread posted before, but from that I could only identify browser issues.

Both Firefox and Chrome are very much demanding. I am not aware whether Chromium is lighter than Chrome, but I've had syncing issues with it in the past, since it's not supported on Windows and Google Chrome syncs better with Google servers than Chromium and I heavily rely on that.

Even my Android phone has Chrome built in and syncing is a wonderful feature, having all the stuff I need on the go.

**Summary:**

This definitely only occurs when using a browser, in my case Chrome.

---

### Post by irv on 2012-12-08
I know that I had those problem with Chrome so I mostly use FF now. But I still use Chrome once in awhile but it hasn't locked up lately. There are other browsers you can try. In the software center there is a long list of light weight browsers you could try.
What I would do is stay away from Chrome for a day or two and see if your problem goes away. if it dose, then wait for a update to come out. Like I said, there is a issue with it. At lease it's true with me also.
I think I will go back to using it full time and see if I lockup again. will let you know if that happens.

---

### Post by Inoki on 2012-12-09
> **irv said:**
> I know that I had those problem with Chrome so I mostly use FF now. But I still use Chrome once in awhile but it hasn't locked up lately. There are other browsers you can try. In the software center there is a long list of light weight browsers you could try.
What I would do is stay away from Chrome for a day or two and see if your problem goes away. if it dose, then wait for a update to come out. Like I said, there is a issue with it. At lease it's true with me also.
I think I will go back to using it full time and see if I lockup again. will let you know if that happens.
Thank you. I'll mark this as solved for now, since we know where the problem resides. I only cannot comprehend why have these browsers become so demanding. I mean, Firefox e.g. 'till version 2 was so light, beginning with version 3 it has become a disaster and has been ever since.

Chrome opens every new tab as a new window in its own sandbox, I mean, what for? Why are these programs so hungry on resources?

Well, Ubuntu Studio is a hybrid between XFCE and Gnome, but most parts of it are XFCE and the default web browser for XFCE is Midori. If Midori had good extensions support, at least for bookmark syncing, Adblock and Lastpass or similar and Greasemonkey then I'd definitely use it.

---

### Post by irv on 2012-12-09
Well, first, I have been running Chrome since my last post yesterday and it's been running good. No lockups. Also I have been watching CPU usage and it been low. I have six tabs open and this is my CPU usage.
[ATTACH]228454[/ATTACH]
I have Ubuntu Studio installed on a laptop I use on a sound system, but I don't use  Midori. I use FF and Chrome on there also. But to be honest I don't use them to often. I mostly use it for recording sound.

---

