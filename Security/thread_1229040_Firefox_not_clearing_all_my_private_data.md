---
title: "Firefox not clearing all my private data"
date: 2009-08-01
forum: Security
---

### Post by Tantor on 2009-08-01
I am using Ubuntu 8.10, with Firefox 3.0.12. I regularlly use the "clear private data" function with all the options ticked. After hearing some rumors I've gone into the folder /home/USER/.mozilla/firefox/SOMETHING.default and found some files containing a lot of web addresses I've visited a long time ago. For example, the file "places.sqlite" contained a huge list of sites I've gone to in the past (and I believed that there was no trace of them left.)

I tried disabling all the add-ons, deleting the file "places.sqlite", going to a site I am absolutely sure I've never been to, clearing private data, closing and opening firefox, clearing private data again, closing firefox; and after that I found that the site was listed in the file "places.sqlite"!

My question is: is this a bug, is my own system compromised somehow, or this is the way it is suppose to be and I've been very naively believing this "clear private data" was doing a good job?

---

### Post by Tantor on 2009-08-02
Can someone tell me if this is also the case in your systems? Once I've cleared the private data, from Firefox everything seems to have been cleared, but the file "places.sqlite" contains a big list. For some reason, the file "places.sqlite" cannot be opened with gedit, but it can be read with nano.

---

### Post by hellmet on 2009-08-02
That is a nasty find, indeed. I can confirm the same on Windows.
I check the option that is supposed to clear all private data on close, but looks like it ain't working.
Edit: Try removing Keep History option.

---

### Post by Tantor on 2009-08-02
Apparently disabling "keep history" works. Anyway, I think there may be other items not being properly cleaned. In fact, the rumor I've heard is that the zoom preferences for individual pages where not cleaned at all, so that "somewhere" there had to be a permanent list of sites you've visited.

It is strange because when "keep history" is on, if I clean all the private data, the history list from Firefox is indeed empty. Yet everything is recorded in this file. I find this disturbing because, for example, google url's contain the strings you've entered in the search box.

---

### Post by hellmet on 2009-08-02
Disturbing indeed. Thanks for letting me (and everybody) know about this.

---

### Post by souldrinker014 on 2009-08-05
I looked at the using Ubuntu/8.04 (hardy) Firefox/3.0.12. 
For me "clear private data" seems to remove the sites I visited in "places.sqlite" but not in "places.sqlite-journal".

---

