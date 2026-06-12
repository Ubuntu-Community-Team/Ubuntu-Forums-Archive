---
title: "New forum software: Lookin' for some beta testers"
date: 2009-01-18
forum: The Cafe
---

### Post by Toby2 on 2009-01-18
Hey ^_^

So I've been working on this web app for a couple of years and I'm looking for some extra feedback before I launch it. It's an open-source web forum called esoTalk. Kinda takes a different approach to vBulletin and the others - [this screencast](http://www.vimeo.com/2867330) (2 mins) probably explains it better that I can write.

Anyway, if you're interested in this kinda thing (or if you're bored) then [have a play around with it](http://forum.esotalk.com/) and please let me know if you can find any bugs that have slipped through. It should work in Firefox 3, Safari 3, IE7, and IE6. And maybe Opera 9, though I haven't checked that recently.

[Source code is available here](http://get.esotalk.com/) if you're able to check that out or install it on your own server (PHP4/5, MySQL5).

---

### Post by fatality_uk on 2009-01-18
Initially, looks good. Nice features. I'll have a look when I get more time but v interesting.!

---

### Post by Sprut1 on 2009-01-18
This looks insanely nice! Beats everything I ever tried to make online! Keep up the good work :KS

---

### Post by oasmar1 on 2009-01-18
WOW! very nice, I am going to try it in a bit, I hope it can be easily themed too, because that would make it terrific.
Have you made sure that the code is also secure though?

---

### Post by Toby2 on 2009-01-18
Thanks for the feedback so far. :)

Yep, the code is secured from SQL injections, cross-site scripting, session hijacking, unvalidated input errors, etc.

If you want to try making an esoTalk skin for yourself, download the source code and install it. Then go into the skins directory and make a copy of the "Plastic" folder. Rename that folder to, say, MySkin, and then go into MySkin/skin.php and replace all instances of Plastic with MySkin. You can then skin with CSS/images - do a bit of experimenting and you'll be able to work it out. When we launch we're planning on creating tutorial screencasts for skins and plugins.

---

### Post by e_torano on 2009-01-18
Wow! Very interesting. I'm going to check this out now! Thanks.

---

### Post by Barrucadu on 2009-01-18
Looks nice, I'll have a play around with it on my local server.

---

### Post by Chokkan on 2009-01-18
This looks fab! Great work.

---

### Post by powell on 2009-01-18
I declare that those forums are hawt

---

### Post by binbash on 2009-01-18
a good piece of work!

---

### Post by Changturkey on 2009-01-18
Is this as easy to use as InvisionFree/Zeta Boards? I've only ever had experience with those two pieces of software.

---

### Post by Thirtysixway on 2009-01-18
Looks very nice.  I'm downloading now to test.  Is there a feature like in phpbb that will alert you if there's an updated version of the forum software?

edit:
looking inside the .zip I see a .htaccess file.  This means it only work on Apache servers?  I use lighttpd on my dev server..

---

### Post by Toby2 on 2009-01-18
Thanks everyone for the feedback so far!

Currently, esoTalk doesn't notify you if there's a new version available - but it sounds like a good idea, so we'll look into adding that in.

It will work on lighttpd (the support forums are, in fact, running on lighttpd!); the .htaccess is only for mod_rewrite rules in Apache. And, of course, the software does work without mod_rewrite.

---

### Post by chamber on 2009-01-18
Looks excessively awesome. Kudos.

---

### Post by kernelhaxor on 2009-01-18
Very innovative and intuitive!
Awesome work!
I'll try to install and test sometime!

---

### Post by Polygon on 2009-01-19
very nice forum!

but the avatars/usernames should not switch from left to right, it makes it kinda annoying when its like that

---

### Post by Toby2 on 2009-01-24
Hey, just posting back to say we've integrated some new features, fixed some bugs, and released alpha 3. Here's a brief list of changes.

- Fixed some RSS bugs, couple of Opera/IE6/IE7 rendering issues, some issues with the installer, plugin system bugs, and a couple of other minor things.
- Updated the emoticon set, added a version update notifier, made some changes to "currently online", added a user preference to control avatar positioning (left, right, or alternating), made the AJAX auto-refresh thing more efficient, and some other small stuff.

Thanks for the feedback and testing so far! It's been a great help. :)

A [complete list of changes is available here](http://forum.esotalk.com/conversation/15/esotalk-1-0-0-alpha-3-released/), and [alpha 3 is available here](http://get.esotalk.com).

---

### Post by Ub1476 on 2009-01-24
This looks really nice, at least from an end-user view. When is it stable and safe to use this software?

---

### Post by Toby2 on 2009-01-24
Thanks! We're working pretty hard to get a stable release, but the timeframe mainly depends on how many people help us with beta testing and how many bugs are found.

---

