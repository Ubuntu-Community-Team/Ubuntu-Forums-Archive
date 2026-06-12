---
title: "Lightbeam: a replacement for Collusion"
date: 2014-09-06
forum: The Cafe
---

### Post by vasa1 on 2014-09-06
Firefox users can try [Lightbeam]("https://addons.mozilla.org/en-US/firefox/addon/lightbeam/"), an extension aiming to show how sites you visit interact with others. I gather it's just illustrative and doesn't prevent anything (tracking, etc) currently. It's also not as pretty as Collusion, the previous avatar.

I had used Collusion to gauge how effective my custom blocking filters (Privoxy & Adblock Plus) were.

---

### Post by coldraven on 2014-09-07
I wonder if I could sue all those trackers who ignore the "Do not track" option in Firefox. It really is quite scary to see how many of them are sharing my browsing data.

---

### Post by vasa1 on 2014-09-07
> **coldraven said:**
> I wonder if I could sue all those trackers who ignore the "Do not track" option in Firefox. It really is quite scary to see how many of them are sharing my browsing data.
I'm not sure that "Do not track" has the force of law anywhere:> Companies are starting to support Do Not Track, but you may not notice any changes initially. We are actively working with companies that have started to implement Do Not Track, with others who have committed to doing so soon.
From [Do Not Track FAQ]("https://www.mozilla.org/en-US/dnt/")

---

### Post by vasa1 on 2014-09-07
Lightbeam sends data to Mozilla if you choose to **Contribute Data**:> If you do contribute Lightbeam data to us, your browser will send us your Lightbeam data (you can see a list of the kind of data involved here.). We will post your data along with data from others in an aggregated and open database in a manner which we believe minimizes your risk of being re-identified. Opening this data can help users and researchers make more informed decisions based on the collective information.And [this link]("https://github.com/mozilla/lightbeam/blob/master/doc/data_format.v1.1.md") explains what is sent and how it's formatted.
Unfortunately, the data, although it's plain text, will need quite a bit of work (parsing?) to make it intelligible (at least to me).

---

