---
title: "http://http"
date: 2005-11-29
forum: The Cafe
---

### Post by jamesford on 2005-11-29
it pissed me off that whenever i click a malformed url (common in forums where http:// is automaticly added as a prefix) like [http://http](http://http) brings me to micro**ft.com

id like to go anywhere else

anyone know a fix?

---

### Post by uberlinux on 2005-11-29
That's weird!
I bet you can do some sort of DNS thing,  or stop screwing up ;)

---

### Post by oddabe19 on 2005-11-29
mine does it too

---

### Post by gingermark on 2005-11-29
Using Opera, when I click that it goes to [www.http.com](www.http.com) - which doesn't seem much better, but maybe it's browser dependent?

---

### Post by kvidell on 2005-11-29
Googling for it gets you an interesting result set...

The first one is a UC Berkeley result for Artificial Intelligence!

My guess is it's some kind of... crappy easter-egg built in to the browser... for lord only knows what reason.
- K

---

### Post by dtfinch on 2005-11-29
To fix this:
Go to url "about:config"
browser.fixup.alternate.enabled = false
keyword.enabled = false

Fixing another annoyance related to middle clicking when the mouse isn't over a link:
middlemouse.ContentLoadURL = false
middlemouse.paste = false

With all those changes, Firefox becomes reasonably deterministic.

---

### Post by Qrk on 2005-11-29
It is because microsoft is the "I'm feeling lucky" google result for http. (at least I think so) I use epiphany, which google searches for the url by default.

---

### Post by dtfinch on 2005-11-29
Features like that are probably why Google took browser rankings out of their zeitgeist.

---

### Post by matthew on 2005-11-29
[quote=jamesford]it pissed me off that whenever i click a malformed url (common in forums where http:// is automaticly added as a prefix) like [http://http]("http://http") brings me to micro**ft.com

id like to go anywhere else

anyone know a fix?[/quote] My gut feeling is that search engines probably connect [http://http]("http://http/") with Microsoft so that it forwards to their site. There isn't anything you can do about that except try to be more watchful as you input urls.

---

### Post by nemik on 2005-11-29
you could change the name of your ubuntu group to http. :) 

when i do [http://ubuntu](http://ubuntu) (ubuntu being my group/domain name thing) i get my index from my www folder. :D

---

### Post by etc on 2005-11-29
Nope, my squid proxy doesn't redirect improper urls.

---

### Post by benplaut on 2005-11-30
that's not the scariest... if you accidentally replace the : with a ; ...

---

### Post by Kvark on 2005-11-30
If you change keyword.URL to [http://www.google.com/search?lr=&ie=UTF-8&oe=UTF-8&q=](http://www.google.com/search?lr=&ie=UTF-8&oe=UTF-8&q=) in about:config then it will take you to a list of Google search results instead of to the stupid "I'm feeling lucky" search when you click malformed urls or type search keywords in the address field.

---

### Post by egon spengler on 2005-11-30
[QUOTE=Qrk]It is because microsoft is the "I'm feeling lucky" google result for http. (at least I think so) [/QUOTE]

Yeah Microsoft is the first result in a [google search for http]("http://www.google.co.uk/search?q=http"), whenever you enter a term into the firefox address bar without a search engine keyword to tell it which engine to use the default function is to do a google "I'm feeling lucky" search on the term. Hence entering http will take you to microsoft.com

As someone said, you can change this default behaviour though. Personally I find it useful, it's easier to me to type "bbc news" and get to the BBC like that (though just setting a bookmark with a keyword would be quicker) then typing the correct url, but I can see how it would be annoying to some people

---

### Post by dtfinch on 2005-11-30
It's annoying when you type in the name of a computer on the local network, and you get sent somewhere you didn't want to go because for some reason the name didn't resolve. You could wind up just about anywhere. I'd imagine it'd be embarrasing if one of your local intranet servers went down and Firefox decided to send all your coworkers to a porn site instead, but I can't say I've heard of that ever happening.

---

### Post by newbie2 on 2005-11-30
[http://ubuntuforums.org/showthread.php?t=87256](http://ubuntuforums.org/showthread.php?t=87256)
:rolleyes:

---

