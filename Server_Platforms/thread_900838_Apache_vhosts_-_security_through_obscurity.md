---
title: "Apache vhosts - security through obscurity"
date: 2008-08-25
forum: Server Platforms
---

### Post by munwin on 2008-08-25
I have a question for the masses.
 It's apache (with vhosts) specific.
 It's a little hack I was thinking about, and it is security through obscurity. Yes, I know that is not the best approach, but I figure, combine this with the other usual things (hhtps, validated input, yadda, yadda) and it couldn't hurt. What I am wondering is if my thoughts are correct, hence the email.....

 I want a website online, with access restricted to a handful of people with known IP Addressses.

 You have an apache server running vhosts.
 One of the vhosts was the usual [http://www.mydomain.com](http://www.mydomain.com) - a _valid_ domain name.
 The other (obscured) domain was [http://uiefnuiebnfvuienvioen.com](http://uiefnuiebnfvuienvioen.com) - some nonsense name that does not exist on the internet - or maybe even [http://www.google.com](http://www.google.com) - a well known host that _does_ exist.
 Now, if you put [http://uiefnuiebnfvuienvioen.com](http://uiefnuiebnfvuienvioen.com) in your bookmarks, and your hosts file (with the matching IP address), you could contact the second website.
 This may be an issue if you used google.com. Maybe you could use [http://www.google.com.au](http://www.google.com.au) for your "real" we searches.... so you could still use google.
 For a bit more STO, you could restrict it to your known IP address (using dyndns, or somesuch).

 Port scanner would see apache, and a probe would reveal website #1.
 Would "bad guys" have a way to detect website #2 ???

 I realise if someone did request [http://uiefnuiebnfvuienvioen.com](http://uiefnuiebnfvuienvioen.com) (or [http://www.google.com](http://www.google.com)) from your site, they would receive the pages.
 I wouldn't think the chance of someone doing that would be very likely, at all.
 So, this would just be a bit of security through obscurity "icing on the cake" as such.

 Your input and thoughts would be most appreciated.

---

### Post by mbeach on 2008-08-25
not sure about security, but I do all my testing prior to going live (or while a client umms and ahhhs about a domain name) in this fashion and have never seen a request outside my ip's in an access log - and I don't have it restricted to my ip's only.

---

### Post by y@w on 2008-08-25
While that works.. you could just use a .htaccess file and put in a username/password for your users ;)

---

