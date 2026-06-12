---
title: "big chrome display bug , click this page and compare in firefox"
date: 2009-12-15
forum: The Cafe
---

### Post by sdowney717 on 2009-12-15
[http://feeds.pbs.org/pbs/wgbh/nova-video/](http://feeds.pbs.org/pbs/wgbh/nova-video/)

just a bunch of text smeared across the screen.

---

### Post by NoaHall on 2009-12-15
It's because it's a feeds page.

---

### Post by Psumi on 2009-12-15
> **NoaHall said:**
> It's because it's a feeds page.

It still should look nice in chrome.

---

### Post by Marlonsm on 2009-12-15
> **Psumi said:**
> It still should look nice in chrome.

I'm not sure if Chrome has a built-in feed reader like Firefox do...

Maybe that's the problem.

---

### Post by Xbehave on 2009-12-15
> **Marlonsm said:**
> I'm not sure if Chrome has a built-in feed reader like Firefox do...
> **NoaHall said:**
> It's because it's a feeds page.And?
Chrome should either render the page or pass it of to a program that can.

Oh and before somebody says firefox is bloated because it has an embeded rss reader, XML is pretty similar to HTML so it doesn't take much to handle something like rss (a specific XML format)

---

### Post by Grenage on 2009-12-15
> Chrome should either render the page or pass it of to a program that can.

That depends very much on what the developers wanted.

---

### Post by Tibuda on 2009-12-15
> **Xbehave said:**
> And?
Chrome should either render the page or pass it of to a program that can.

Thats not a page. Firefox treats it as a page, but it is not.

---

### Post by Xbehave on 2009-12-15
> **Grenage said:**
> That depends very much on what the developers wanted.Huh? The developers wanted to fail at parsing the XML then display that to the users? This is a bug you guys need to stop bumming chrome so hard.
> **danielrmt said:**
> Thats not a page. Firefox treats it as a page, but it is not.
it's a page of XML (specifically RSS)
```
<?xml version="1.0" encoding="UTF-8"?>
<rss xmlns:itunes="http://www.itunes.com/dtds/podcast-1.0.dtd" xmlns:feedburner="http://rssnamespace.org/feedburner/ext/1.0" version="2.0">
```

---

### Post by madnessjack on 2009-12-15
XML files should have XSLT stylesheets attached to them. Not sure if Chrome implements even this but it's a start.

And before people start bitching and moaning because a critical feature hasn't been implemented
[http://www.google.com/reader/](http://www.google.com/reader/)

There, fixed it for you

---

### Post by howefield on 2009-12-15
> **Xbehave said:**
> Huh? The developers wanted to fail at parsing the XML then display that to the users? This is a bug you guys need to stop bumming chrome so hard.

:lolflag::lolflag:

It's in Beta, go report the bug if you care and it will be fixed if the developers care or can.

---

### Post by Grenage on 2009-12-15
> **Xbehave said:**
> Huh? The developers wanted to fail at parsing the XML then display that to the users? This is a bug you guys need to stop bumming chrome so hard.

it's a page of XML (specifically RSS)
```
<?xml version="1.0" encoding="UTF-8"?>
<rss xmlns:itunes="http://www.itunes.com/dtds/podcast-1.0.dtd" xmlns:feedburner="http://rssnamespace.org/feedburner/ext/1.0" version="2.0">
```

I don't use Chrome, and it's not your place to say what it should be doing.  Unless you're one of it's developers, which you aren't.

Ta ta.

---

### Post by Tibuda on 2009-12-15
> **Xbehave said:**
> it's a page of XML (specifically RSS)
```
<?xml version="1.0" encoding="UTF-8"?>
<rss xmlns:itunes="http://www.itunes.com/dtds/podcast-1.0.dtd" xmlns:feedburner="http://rssnamespace.org/feedburner/ext/1.0" version="2.0">
```

No, it is not a page. RSS feeds are only meta data. There's nothing on the file about how it should be displayed, unless there's a link to a XSLT sheet. Firefox only have a default XSLT sheet for RSS.

---

### Post by madnessjack on 2009-12-15
Internet Explorer does a good job of rendering XML :P

---

### Post by sdowney717 on 2009-12-15
I cant report it as a bug because bug reports in linux are diabled.
[http://www.google.com/support/forum/p/Chrome/thread?tid=2a2135b6f50fd524&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=2a2135b6f50fd524&hl=en)

opera shows the feeds in a usable format

---

### Post by Xbehave on 2009-12-15
> **danielrmt said:**
> No, it is not a page. RSS feeds are only meta data. There's nothing on the file about how it should be displayed, unless there's a link to a XSLT sheet. Firefox only have a default XSLT sheet for RSS.
Fine replace the word page with file, when a web browser sees a file it should either render the page correctly according to w/e specification is relevant OR push the file out to a program/website that can. If I point my webbrowser at a pdf I don't expect it to push out the raw text of the file, hence it is a bug.

---

### Post by madnessjack on 2009-12-15
[http://lifehacker.com/5134224/ramisp-grabs-rss-feeds-for-google-chrome-users](http://lifehacker.com/5134224/ramisp-grabs-rss-feeds-for-google-chrome-users)

---

### Post by pwnst*r on 2009-12-15
hardly a bug.  nice try though.

---

### Post by Tibuda on 2009-12-15
> **Xbehave said:**
> Fine replace the word page with file, when a web browser sees a file it should either render the page correctly according to w/e specification is relevant OR push the file out to a program/website that can. If I point my webbrowser at a pdf I don't expect it to push out the raw text of the file, hence it is a bug.

yeah, it should try to open the rss in a feed reader if installed, or ask the user what to do.

---

### Post by madnessjack on 2009-12-16
> **danielrmt said:**
> yeah, it should try to open the rss in a feed reader if installed, or ask the user what to do.
Actually this is dealt with by the server. If a server gives it to you as a download, you download the file. It's in the headers, not the browsers.

Enough FUD please

---

### Post by Keyper7 on 2009-12-16
> **Xbehave said:**
> Fine replace the word page with file, when a web browser sees a file it should either render the page correctly according to w/e specification is relevant OR push the file out to a program/website that can. If I point my webbrowser at a pdf I don't expect it to push out the raw text of the file, hence it is a bug.

Apples and oranges. A PDF file has content information and layout information. You don't expect the raw text of a PDF because that would represent loss of the layout information. A RSS file has ONLY content information and NO layout information whatsoever. There's no relevant specification on how a RSS should be rendered. It's entirely up to the application, and that includes simply not caring about it.

---

### Post by Xbehave on 2009-12-16
> **madnessjack said:**
> Actually this is dealt with by the server. If a server gives it to you as a download, you download the file. It's in the headers, not the browsers.

Enough FUD please
A server doesn't give you anything as a download, your browsers requests a file and it is served for an XML file the browsers will be told it is "[text/xml]" that and the length, the server does not say download/display/etc, so please don't accuse me of spreading FUD when
1) It's just a misunderstanding
2) It is you who has miss understood how things work

> There's no relevant specification on how a RSS should be rendered. It's entirely up to the application, and that includes simply not caring about it.
I suppose that's true, but it's pretty poor for chrome to mess up the page instead of just ask you to open it in an external viewer. This particular page also listed 2 style sheets > <rss xmlns:itunes="http://www.itunes.com/dtds/podcast-1.0.dtd" xmlns:feedburner="http://rssnamespace.org/feedburner/ext/1.0" version="2.0"> but you are correct they didn't do anything technically wrong, but that doesn't make it suck any less for the user.

---

### Post by kahumba on 2009-12-17
> **sdowney717 said:**
> 
just a bunch of text smeared across the screen.

They did it to save space and resources, remember Chrome is about being fast and minimalistic, by removing the "\n" characters they save about 50 bytes per page.

---

### Post by madnessjack on 2009-12-17
> **Xbehave said:**
> A server doesn't give you anything as a download, your browsers requests a file and it is served for an XML file the browsers will be told it is "[text/xml]" that and the length, the server does not say download/display/etc, so please don't accuse me of spreading FUD when...

[http://en.wikipedia.org/wiki/List_of_HTTP_headers](http://en.wikipedia.org/wiki/List_of_HTTP_headers)

Check the responses section. Servers can be in control of who gets to download what. Either way, an XML RSS feed should never be considered an essential part of a browser. If you think you so badly need to add such functionality, check the extensions and leave the rest of us alone. I more than like it just the way it is.

---

### Post by Xbehave on 2009-12-17
> **madnessjack said:**
> [http://en.wikipedia.org/wiki/List_of_HTTP_headers](http://en.wikipedia.org/wiki/List_of_HTTP_headers)

Check the responses section. Servers can be in control of who gets to download what. 
Nothing in the response headers seams to dictate weather content should be downloaded or displayed.
I don't think Content-Disposition is applicable as you would want the file to be passed to another program or a plugin not saved.

> If you think you so badly need to add such functionality, check the extensions and leave the rest of us alone. I more than like it just the way it is.
The point is, if the browser can't handle the mime type it should be passed to a program that can handle that mime time. I find it hard to believe that you want to see the garbled raw text of an rss feed, perhaps you do but most users don't, so the format should either be handled well by chrome or passed out to a program that can, it is a bug not a feature.

---

### Post by Marvin666 on 2009-12-17
IE6 just show's the page's html, with a bunch of weird spacing and coloring added to it.

---

### Post by madnessjack on 2009-12-17
> **Xbehave said:**
> Nothing in the response headers seams to dictate weather content should be downloaded or displayed.
I don't think Content-Disposition is applicable as you would want the file to be passed to another program or a plugin not saved.
> **Wikipedia]Content-Disposition     An opportunity to raise a "File Download" dialogue box for a known MIME type     Content-Disposition: attachment said:**
> 

[quote]I find it hard to believe that you want to see the garbled raw text of an rss feed, perhaps you do but most users don't, so the format should either be handled well by chrome or passed out to a program that can, it is a bug not a feature.
I find it hard to believe you care so much. Right click, save as?

---

### Post by sdowney717 on 2009-12-17
at the site
[http://feeds2.feedburner.com/cnet/loaded/?tag=contentMain;contentBody/](http://feeds2.feedburner.com/cnet/loaded/?tag=contentMain;contentBody/)

compare playing video between firefox and chrome.

firefox is using gecko media player
chrome is using ? html5?, tiny (but it could have been scaled up)

anyway compare the sizes.
One plus for chrome is it will start playing right away
whereas firefox gecko has to catch to 100% before playing
it will only play some of these if you have the improved gecko player
[http://ubuntuforums.org/showthread.php?t=1346092&highlight=gecko](http://ubuntuforums.org/showthread.php?t=1346092&highlight=gecko)
otherwise it will endlessly cache

[http://rss.cnn.com/services/podcasting/amanpour_video/rss/?format=](http://rss.cnn.com/services/podcasting/amanpour_video/rss/?format=)

to see them in chrome you might have to install an extension called fruitrss
example is here - [http://www.pbs.org/wgbh/nova/rss/nova.xml](http://www.pbs.org/wgbh/nova/rss/nova.xml)
(I have an extended desktop, so the screen capture shows the green leaf of the other monitor)

---

### Post by Xbehave on 2009-12-17
> **madnessjack said:**
> I find it hard to believe you care so much. Right click, save as?
Did you read past the first line:
"I don't think Content-Disposition is applicable as you would want the file to be passed to another program or a plugin not saved."

A website can try and raise an a save as dialog but that isn't what is needed here, if you click on a file that the browser can't handle the browser should pass it to one that can, because there are many browser that can handle rss (firefox,konqueror,ie?,etc) it would be stupid for a site to prompt them to dl the file because chrome can't

---

