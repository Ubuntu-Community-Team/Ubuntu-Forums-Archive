---
title: "is Chromium slower than Chrome for you too?"
date: 2011-04-30
forum: The Cafe
---

### Post by nrundy on 2011-04-30
I've run dozens of tests with a stop watch of page load times: Google Chrome vs Chromium. Both browser settings are identical. Chrome consistently loads pages faster. I also ran both browsers thru the Peacekeeper benchmark ([http://clients.futuremark.com/peacekeeper/index.action](http://clients.futuremark.com/peacekeeper/index.action)) just for the heck of it. Chrome scores higher.

I was wondering if everyone experiences this performance gain for Chrome? Whatever Google is adding to Chromium is making it "faster." Thing is though, there's nothing on paper that appears different between the two performance wise. Weird.

---

### Post by matthewbpt on 2011-04-30
What builds of each are you running? Chromium in the repos isn't latest build. I have the Chromium Daily Builds ppa added. If you go on the about page of each you can see what build it is, I currently have 12.0.741.0. To properly compare the two you should be running the same version of both. I've run both and I've never noticed a performance difference between them ...

---

### Post by nrundy on 2011-04-30
I'm comparing the same versions (version 11). I have PPA-stable for both Chrome and Chromium. Interesting you haven't noticed difference. Have you benchmarked them? Chrome shows a much higher score on peacekeeper. I found this strange.

---

### Post by el_koraco on 2011-04-30
> **nrundy said:**
> I'm comparing the same versions (version 11). I have PPA-stable for both Chrome and Chromium. 

isn't chromium always one version ahead of chrome? even with the stable versions, i mean.

---

### Post by nrundy on 2011-04-30
no, the PPA-stable for Chromium matches the Google Chrome releases. The same version Chrome releases is pulled for the Chromium release.

---

### Post by P1C0 on 2011-04-30
Chrome is faster than Chromium in my system too. But only in benchmarking since I don't notice any difference with normal browsing.

Firefox 4.0.1 is waaay behind..!

---

### Post by P1C0 on 2011-05-01
I think the answer is that Google Chrome is more aggressively compiled than Chromium. Probably with a higher optimization level among other things.

---

### Post by matthewbpt on 2011-05-01
It's true that I haven't done any real benchmarking, I'm just speaking from normal use of both. @P1C0 I can't imagine how they would compile it to have such a speed increase, I would have thought they would need quite generic compiler flags to ensure compatibility across a wide variety of hardware, though I am no expert in compiler optimization. I would be very interested in finding out what tricks they use if this is indeed the case.

Matt

---

### Post by P1C0 on 2011-05-01
> **matthewbpt said:**
> It's true that I haven't done any real benchmarking, I'm just speaking from normal use of both. @P1C0 I can't imagine how they would compile it to have such a speed increase, I would have thought they would need quite generic compiler flags to ensure compatibility across a wide variety of hardware, though I am no expert in compiler optimization. I would be very interested in finding out what tricks they use if this is indeed the case.

MattJust a small pointer about optimization levels: [http://www.network-theory.co.uk/docs/gccintro/gccintro_49.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_49.html)

---

### Post by nrundy on 2011-05-01
Benchmark that shows Chromium as faster than Chrome. However it's a year old:  [http://news.softpedia.com/news/JavaScript-Benchmarking-Google-Chrome-vs-Chromium-vs-Opera-vs-Firefox-141606.shtml](http://news.softpedia.com/news/JavaScript-Benchmarking-Google-Chrome-vs-Chromium-vs-Opera-vs-Firefox-141606.shtml)

---

### Post by MountainX on 2011-05-01
> **nrundy said:**
> I've run dozens of tests with a stop watch of page load times: Google Chrome vs Chromium. Both browser settings are identical. Chrome consistently loads pages faster. I also ran both browsers thru the Peacekeeper benchmark ([http://clients.futuremark.com/peacekeeper/index.action](http://clients.futuremark.com/peacekeeper/index.action)) just for the heck of it. Chrome scores higher.

I was wondering if everyone experiences this performance gain for Chrome? Whatever Google is adding to Chromium is making it "faster." Thing is though, there's nothing on paper that appears different between the two performance wise. Weird.

Where do you get Google Chrome for Ubuntu? 

BTW, even if it is a bit faster, I'd rather use Chromium (doesn't phone home as much).

---

### Post by Welly Wu on 2011-05-01
You can get Google Chrome for Ubuntu by navigating to [http://www.google.com/chrome](http://www.google.com/chrome) and downloading the .DEB installer file for either Ubuntu 32 or 64 bit version.

I agree with the original poster that Google Chrome is faster and it performs better than Google Chromium. It also gets updates and upgrades faster too.

---

### Post by YeOK on 2011-05-01
> **MountainX said:**
> Where do you get Google Chrome for Ubuntu? 

BTW, even if it is a bit faster, I'd rather use Chromium **(doesn't phone home as much).**

I disable most of the phone home stuff in Google Chrome (it's all optional..), I leave phishing and malware protection plus predictive search enabled. 

What else does Google Chrome report that Chromium does not? 

I also find the chrome builds faster, however I think it has more to do with the way they are built by the maintainers. I also had more bugs with the chromium builds and running Chrome 12 from the dev channel (12.0.742.12 dev).

---

### Post by MountainX on 2011-05-01
> **Welly Wu said:**
> You can get Google Chrome for Ubuntu by navigating to [http://www.google.com/chrome](http://www.google.com/chrome) and downloading the .DEB installer file for either Ubuntu 32 or 64 bit version.

I agree with the original poster that Google Chrome is faster and it performs better than Google Chromium. It also gets updates and upgrades faster too.

Thanks. I appreciate the link. Where do I find the Chrome dev builds? (e.g., Chrome 12 from the dev channel (12.0.742.12 dev))?

---

### Post by YeOK on 2011-05-01
> **MountainX said:**
> Thanks. I appreciate the link. Where do I find the Chrome dev builds? (e.g., Chrome 12 from the dev channel (12.0.742.12 dev))?

I use Fedora mainly, but when I install from the link you have it also sets up the Google repo. Then I simply remove stable and install dev channel. I would think its the same for Ubuntu.

```

# yum list google-chrome*
Loaded plugins: langpacks, presto, refresh-packagekit
Installed Packages
google-chrome-unstable.x86_64          12.0.742.12-83281          @google-chrome
Available Packages
google-chrome-beta.x86_64              11.0.696.57-82915          google-chrome 
google-chrome-stable.x86_64            11.0.696.57-82915          google-chrome 

```

---

### Post by matthewbpt on 2011-05-01
> **P1C0 said:**
> Just a small pointer about optimization levels: [http://www.network-theory.co.uk/docs/gccintro/gccintro_49.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_49.html)
Thank's for the link, it's very interesting, I think I'll read up some more on this optimization business.

---

### Post by nrundy on 2011-05-02
> **Welly Wu said:**
> You can get Google Chrome for Ubuntu by navigating to [http://www.google.com/chrome](http://www.google.com/chrome) and downloading the .DEB installer file for either Ubuntu 32 or 64 bit version.

I agree with the original poster that Google Chrome is faster and it performs better than Google Chromium. It also gets updates and upgrades faster too.

If you install the Chromium-Stable PPA, it will update the same day as Google-Chrome. That is, it updates faster than the Universe one.

---

### Post by nrundy on 2011-05-02
So you guys are all running Chrome because of the performance gain? Or did you CHOOSE Chrome over Chromium for another reason?

---

### Post by P1C0 on 2011-05-02
I personally use Chromium, Google should stick with search.

---

### Post by Fedz on 2011-05-02
I avoid Google like the plague! Reason being (in a nutshell) I simply don't trust them & this reinforced my belief further by their browser ID & deceiving by small print & or omission of such!

Google are in the business of making money & getting themselves known & this will only lead to them doing it with the browser in time in my opinion so I ain't going to help them - I don't get paid to do it but, they do!

I'll stick with Chromium & SRWare Iron - they both use the same Chromium folder so no matter which you run (with both installed) they look exactly the same (theme, bookmarks, history ...) where as Google Chrome does not it uses it's own folders regardless ;-)

---

