---
title: "Unable to run Internet explorer 7 on Wine 1.2, ubuntu 8.04"
date: 2010-11-28
forum: Wine
---

### Post by lpub on 2010-11-28
Following the instructions here: [http://www.wine-reviews.net/wine-reviews/applications/ie-7-on-linux-with-wine.html](http://www.wine-reviews.net/wine-reviews/applications/ie-7-on-linux-with-wine.html)
  I installed IE7. But when I run it with Wine 1.2 with: wine iexplore.exe&
  I get a bunch of fixme messages, seen here (Ubuntu forums sees "15 images" in my message and won't let me post it i.e. BB code & HTML tags, even though there are none, it's just the error message format):

[http://stackoverflow.com/questions/4296613/unable-to-run-internet-explorer-7-on-wine-1-2-ubuntu-8-04](http://stackoverflow.com/questions/4296613/unable-to-run-internet-explorer-7-on-wine-1-2-ubuntu-8-04)

  And I am unable to open any webpages. How can I fix this?

---

### Post by WienerWuerstel on 2010-11-28
I have a few Questions of my own for you.

1. Why do you run Ubuntu 8.04? It's almost 3 Years old. You can get the newest Ubuntu [here]("http://www.ubuntu.com/")

2. Why would you want to use the Internet Explorer when there are native Browsers like Firefox, Opera, Chrome/Chromium, Midori that are newer and several Times better.

---

### Post by lpub on 2010-11-28
> **WienerWuerstel said:**
> I have a few Questions of my own for you.

1. Why do you run Ubuntu 8.04? It's almost 3 Years old. You can get the newest Ubuntu [here]("http://www.ubuntu.com/")


I am well aware of the latest version of Ubuntu for some time & have read the reviews. I am using an older computer, 8.04 is LTS and has been upgraded over time. I am using 8.04.03 & willing to give time for 10.10 to improve.

> **WienerWuerstel said:**
> 
 2. Why would you want to use the Internet Explorer when there are native  Browsers like Firefox, Opera, Chrome/Chromium, Midori that are newer  and several Times better.

I use Firefox regularly. Do you know what Wine is?  Wine exists for the reason of testing Windows programs in Linux. I need to check that my page works in IE as a majority of views have been with that browser.

I remember asking about using IE on Wine on another forum few years ago and someone automatically assumed, just like the person above, that I don't know of the native browsers on Linux. Just because I am new to a forum does not mean I am that ignorant.

---

### Post by lpub on 2010-11-28
Anyways, reinstalled Wine 1.2 and was able to run IE7 by clicking the icon in the Program Files folder. But it does not work that well, e.g. there are some javascript errors when running certain pages e.g. no post buttons on blogger. 

Tried out PlayOnLinux as I saw this on another thread in this forum, which uses Wine 1.3.6. This works. Although I had to lower the security settings to a risky level at the Adobe flash website to get the latest version of their player (otherwise, IE7 would not show the Active X controls on the website). Then raised the security settings again before going to another website. Adjustments to Security settings may have to be made if you're testing out a webpage with Active X controls to allow the controls to be used.

---

