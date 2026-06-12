---
title: "Google Error. What the hell is this?"
date: 2005-12-10
forum: The Cafe
---

### Post by MetalMusicAddict on 2005-12-10
I searched for phpbb from the searchbar in firefox and got this:

[[IMG]http://img234.imageshack.us/img234/364/untitled2xz.th.png[/IMG]](http://img234.imageshack.us/img234/364/untitled2xz.png)

WTH is that? Dosent happen if I use the Google site though.

---

### Post by KiwiNZ on 2005-12-10
Does the same for me , how rude

---

### Post by raublekick on 2005-12-10
woah, now that is weird. it's only from the bar, too. a regular google search is fine.

---

### Post by MetalMusicAddict on 2005-12-10
Is this something we should report to Google or the Mozilla/Firefox people?

---

### Post by akurashy on 2005-12-10
mostly google i think

---

### Post by gord on 2005-12-10
it could just be some virus thats doing the rounds thats targeting the url
[http://www.google.com/search?q=phpbb](http://www.google.com/search?q=phpbb)

and its varients (but allways with the q=phpbb).

---

### Post by ssam on 2005-12-10
i imagine there is a current virus that exploits a vunrability in phpbb, that is using google to search for vunerable sites.

this action by google stops that virus.

---

### Post by aysiu on 2005-12-10
I'm not getting that. Is there a particular search you're doing?

---

### Post by DoeRayMe on 2005-12-10
aysiu is shows me the error when searching for "phpbb" but not anything else, so it's right what ssam said ;)

try clicking this

[http://www.google.com/search?q=phpbb](http://www.google.com/search?q=phpbb)

---

### Post by aysiu on 2005-12-10
[QUOTE=DoeRayMe]
[http://www.google.com/search?q=phpbb](http://www.google.com/search?q=phpbb)[/QUOTE] That's weird. When I click on your link, I get that funky message, but when I just do a regular search for *phpbb*, I get a regular set of search results:

[http://www.google.com/search?hl=en&q=phpbb&btnG=Google+Search](http://www.google.com/search?hl=en&q=phpbb&btnG=Google+Search)

---

### Post by MetalMusicAddict on 2005-12-10
Very strange. Just from the bar. 

I hope its not a phpbb thing. I want to use it.

---

### Post by invalid on 2005-12-10
The problem is that when you just click the link, or use the toolbar, you are not being refered from an official google webpage. This makes google think that you are running a robot to search for a common string that is found in exploitable websites (phpbb).

This is perhaps a flaw in the way google checks for referers, they should check other things at the same time (useragent and other things could provide useful results).

Cb

---

### Post by ssam on 2005-12-10
[QUOTE=invalid]This is perhaps a flaw in the way google checks for referers, they should check other things at the same time (useragent and other things could provide useful results).
[/QUOTE]

they would need a smart way to check to stop the virus spoofing it.

---

### Post by poptones on 2005-12-10
It's not just when searching for phpbb. I have a tool I made that allows me to search the forums fron the bar - all it does is add the string "site:www.ubuntuforums.org" after the search string and I get that same message when I use the tool with ANY string.

It seems to be a bug in google - when the search string has the "&num" field set it throws up an error. I just tried it in the URL bar and the search works normally only when that field is not specified in the intial search. If you take any "normal" google search and add that field "&num=10" to the end of the URL you will again get that error message.

---

### Post by gord on 2005-12-10
it actually only happens whenever you do 
[http://www.google.com/search?q=phpbb](http://www.google.com/search?q=phpbb)...

the regular google search code has 
[http://www.google.com/search?hl=en&q=phpbb](http://www.google.com/search?hl=en&q=phpbb)...

it doesn't matter what your referre is

---

### Post by poptones on 2005-12-10
Ummm.. no.

[http://www.google.com/search?as_sitesearch=www.ubuntuforums.org&q=atheist&num=20](http://www.google.com/search?as_sitesearch=www.ubuntuforums.org&q=atheist&num=20)

Not a phpbb anywhere in that string

Get rid of the "num" field and it works just fine.

---

### Post by linbetwin on 2005-12-10
I searched for **phpbb** from the address bar and it took me to: [http://www.phpbb.com/](http://www.phpbb.com/)

---

### Post by gord on 2005-12-10
[QUOTE=poptones]Ummm.. no.

[http://www.google.com/search?as_sitesearch=www.ubuntuforums.org&q=atheist&num=20](http://www.google.com/search?as_sitesearch=www.ubuntuforums.org&q=atheist&num=20)

Not a phpbb anywhere in that string

Get rid of the "num" field and it works just fine.[/QUOTE]


yea sorry, i wasn't refering to what you said, i think thats a diffirent bug :)

---

### Post by Dr. Nick on 2005-12-10
[quote=linbetwin]I searched for **phpbb** from the address bar and it took me to: [http://www.phpbb.com/]("http://www.phpbb.com/")[/quote]

The address bar is different I believe, Try it from the google box in the corner of Firefox, not the bar where you also type in urls

---

### Post by sapo on 2005-12-10
I think that is the virus stuff.. and if you DONT send a referer it give you the error, when you search for the site you send a referer as being from google.. so it allows your search :razz:

---

### Post by linbetwin on 2005-12-11
[quote=Dr. Nick]The address bar is different I believe, Try it from the google box in the corner of Firefox, not the bar where you also type in urls[/quote]

Yeah, no I got that message too. It doesn't happen when you search on Yahoo from the "engine" box.

---

### Post by earobinson on 2005-12-12
[QUOTE=KiwiNZ]Does the same for me , how rude[/QUOTE]
lol oh starwars I, lol

---

### Post by flurdy on 2005-12-13
Seem I cross posted a [similar bug]("http://www.ubuntuforums.org/showthread.php?t=102545")

Basically I narrowed it down to searching within any sites containing forum and requesting 20 rows per page. 

However as it seems from this thread the problem is for other type of strings and combinations as well.

---

### Post by unkemptwolf on 2005-12-13
Perhaps related to [this]("http://news.netcraft.com/archives/2004/12/21/santy_worm_spreads_through_phpbb_forums.html")?

---

