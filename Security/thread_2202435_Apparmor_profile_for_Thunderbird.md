---
title: "Apparmor profile for Thunderbird?"
date: 2014-01-29
forum: Security
---

### Post by cogset on 2014-01-29
Hi there,having been using Apparmor for a while,I was wondering if specific profiles for Thunderbird do exist:given the possible exploits served via email (come to that,here's the last I've read about : [http://thehackernews.com/2014/01/mozilla-thunderbird-vulnerability.html](http://thehackernews.com/2014/01/mozilla-thunderbird-vulnerability.html) ),to curb some possible exploit attempts it would look logical to me to also enforce some policies for Thunderbird.

---

### Post by DuckHook on 2014-01-30
I've looked high and low for such a preconfigured profile but could only find ones that were years old. Afraid you'll have to spin your own.

---

### Post by Habitual on 2014-01-30
The vulnerability is fixed in the latest versions (24.2.0) of [Thunderbird]("http://www.mozilla.org/en-US/thunderbird/all.html"), and users are highly recommended to upgrade as soon as possible.

---

### Post by cogset on 2014-01-31
Alright,still my original question remains:are there any already made apparmor profiles for Thunderbird that you can grab,if nothing just to have an idea of what you need to put in a custom profile?

I wouldn't mind having a look even at old stuff,again just to get the hang of it:writing my own profile isn't going to be easy,on the other hand I've once tried to use  aa-genprof for a non-standard Firefox installation and there was almost nothing in that profile.

---

### Post by Dave_L on 2014-01-31
There are some old (2009) ones here: [http://bodhizazen.net/Tutorials/aa](http://bodhizazen.net/Tutorials/aa)

---

