---
title: "Case in-sensitive?"
date: 2011-01-15
forum: Server Platforms
---

### Post by rysliv on 2011-01-15
I looked all over, nothing works

I can't find the file were speling.conf is so I can't even turn on checkspeling at all.

What the heck am I suppose to do with this LAMPP stuff? Case Sensetive URL's are a pain in the *** to work with, when your a developer that constantly makes mistakes on leaving some links with caps and some without, making half the website not work with linux's stupid file system.


Can anyone help me out here? Before I go berserk with anger throwing my server out the window.

---

### Post by spynappels on 2011-01-15
File and username are case sensitive, URLs are not. What problem are you having?

Maybe you can explain a little better?

---

### Post by sj1410 on 2011-01-16
> **rysliv said:**
> I looked all over, nothing works

I can't find the file were speling.conf is so I can't even turn on checkspeling at all.

What the heck am I suppose to do with this LAMPP stuff? Case Sensetive URL's are a pain in the *** to work with, when your a developer that constantly makes mistakes on leaving some links with caps and some without, making half the website not work with linux's stupid file system.


Can anyone help me out here? Before I go berserk with anger throwing my server out the window.

Its very easy to blame others for your wrong doings. domain names are never case sensitive. but keeping the virtual directory, files case-sensitive is the right way. windows IIS does it the wrong way. you make a mistake, type the wrong URL, and say " linux's stupid file system". You know the difference between the windows and linux file system.

---

### Post by CharlesA on 2011-01-16
It is usually best practice to make OS independent filenames. I use all lowercase file/folder names on my site, that way I don't have to worry about OS the server hosting the site runs.

---

### Post by The Cog on 2011-01-16
Actually, I think it makes sense for a filesystem to be case sensitive. I don't think we should expect non-english speakers to know that "HANKEY" and "hankey" are the same filename, any more than we should expect english speakers to know that "&#919;&#913;&#925;&#922;&#917;&#933;" and "&#951;&#945;&#957;&#954;&#949;&#965;" or "&#915;&#937;&#925;&#933;&#931;" and "&#947;&#969;&#957;&#965;&#963;" are the same filename. Actually, I can imagine that there might be pairs of filenames that are the same in some countries but not others - it just doesn't make sense to be like that.

---

