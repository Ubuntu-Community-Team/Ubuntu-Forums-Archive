---
title: "[SOLVED] how to steal the content of the web site?"
date: 2008-07-13
forum: The Cafe
---

### Post by hechizera on 2008-07-13
hi guys!

Is there any way to, so to say, "steal"( :) )  the content of the web site? mainly I need to "steal" text and pictures.. saving every page on my comp isn't a good thing, because it takes a lot of time.. I'd like to do that somehow automatically, if that's possible.. 

So.. please, please somebody help me..

---

### Post by bapoumba on 2008-07-13
> **hechizera said:**
> hi guys!

Is there any way to, so to say, "steal"( :) )  the content of the web site? mainly I need to "steal" text and pictures.. saving every page on my comp isn't a good thing, because it takes a lot of time.. I'd like to do that somehow automatically, if that's possible.. 

So.. please, please somebody help me..

What website, any copyrights, do they allow it :confused:
These tools exit and could drain a server..

---

### Post by hechizera on 2008-07-13
> **bapoumba said:**
> What website, any copyrights, do they allow it :confused:
These tools exit and could drain a server..

it is an online cookbook, which has very good recipes.. I want it to be on my computer, because it would be very bad if one day this web site would crash or something.. 
I am not sure if they allow it, probably not, but who knows.. could you please tell me what are these tools like? I mean names and so..

---

### Post by ssam on 2008-07-13
wget can recursively download stuff.

---

### Post by Masoris on 2008-07-13
What do you mean? Do mean you want to download all component from a web site?

Then, HTTrack could do that.
[http://www.httrack.com/](http://www.httrack.com/)

---

### Post by bapoumba on 2008-07-13
> **hechizera said:**
> it is an online cookbook, which has very good recipes.. I want it to be on my computer, because it would be very bad if one day this web site would crash or something.. 
I am not sure if they allow it, probably not, but who knows.. 
If they do not allow it, then you should not do it. May be this recipe site has some user space where you could ask, edit books or something ?

---

### Post by hechizera on 2008-07-13
ssam, thank you I will try it! :)

Masoris, I don't really want everything from the site, just the recipes with pictures :)

---

### Post by hechizera on 2008-07-13
bapoumba, I will read more about their site and also will look at the wget.. if it is not too illegal thing than I will use it.. 

they have links to the original books, but unfortunately they are in the languages which I am not too good in plus there are no pictures.. so I want exactly that site :)

---

### Post by roaldz on 2008-07-13
It probably is allowed if you just download the website and use it to browse it offline. If you publish the contents anywhere else, you´re (probably) doing illegal stuff.

```
wget -r www.specificwebsite.com
```

this downloads all links recursively

maybe there are better tools to do this, but I know this works:)

---

### Post by laxmanb on 2008-07-13
I remember Internet Explorer allowing you to save pages for offline viewing, and it could also get all pages that were a certain number of levels down from the current page. So you could get an entire website offline if you wanted

Does IE still have that? Does Firefox have something equivalent as an extension?

PS: Does mentioning IE get you in trouble here?

---

### Post by Samhain13 on 2008-07-13
I agree with Roaldz. Every page you visit gets cached by your browser anyway, so you have a copy of visited web pages and their content in your computer whether the owner allows copying or not. But to republish that content without permission is another story.

---

### Post by bapoumba on 2008-07-13
> **laxmanb said:**
> PS: Does mentioning IE get you in trouble here?
No, it should not :D

hechizera, thanks to respect their copyrights, and as roaldz mentioned, not to re-publish anywhere :)

---

### Post by Polygon on 2008-07-13
if your gonna use wget, make SURE you use a delay argument (check the man page, i think its -w )

but be sure to do this, cause if you dont put a delay, the server might actually ban you because it will think you are trying to ddos it from all the rapid download requests from you coming from wget

so do like wget -mirror -np -w 5 url or something

---

### Post by Mr. Picklesworth on 2008-07-13
No need to be concerned about this stuff. Archive.org has a nice backup of everything.

---

### Post by hechizera on 2008-07-13
roaldz, I need it for personal use only, so probably it is not illegal :)

laxmanb, it's ok about IE.. it has this saving thing, also it is possible to save a web page in firefox, but the method I know is very slow.. maybe there's some other, which I have no clue about..

so.. thanks to everyone for your answers and for help! I finally have the whole 22mb of recipes on my computer! thank you, guys! :)

---

### Post by hechizera on 2008-07-13
Polygon, oops.. I didn't use this argument.. but they didn't ban me anyway, so probably no worries :) anyway thanks for the answer, next time I will do as you wrote!

Mr. Picklesworth, archive. org? I have never heard about it :)

---

### Post by hechizera on 2008-07-13
I marked it as solved.. thanks once again and bye bye :)

---

### Post by intense.ego on 2008-07-13
Out of curiosity, would the wget method work for the follwing example:

the url is [www.example.com](www.example.com)

but some of what you want is on content.example.com

would using wget on [www.example.com](www.example.com) get everything, including what is one content.example.com?

---

### Post by mr.propre on 2008-07-13
> **intense.ego said:**
> Out of curiosity, would the wget method work for the follwing example:

the url is [www.example.com](www.example.com)

but some of what you want is on content.example.com

would using wget on [www.example.com](www.example.com) get everything, including what is one content.example.com?

No, www and content are both sub directories and have both separate directors where www mostly is the default folder. It' doesn't really have to.

---

### Post by gnuvistawouldbecool on 2008-07-13
edit:because I should remember to read the rest of a thread.

---

### Post by Masoris on 2008-07-14
You also can use a Firefox extension Scrapbook.
[http://amb.vis.ne.jp/mozilla/scrapbook/](http://amb.vis.ne.jp/mozilla/scrapbook/)

---

### Post by DigitalDingo on 2008-07-14
> **Masoris said:**
> You also can use a Firefox extension Scrapbook.
[http://amb.vis.ne.jp/mozilla/scrapbook/](http://amb.vis.ne.jp/mozilla/scrapbook/)
Or Google Notebook: [http://www.google.com/notebook/]("http://www.google.com/notebook/"). You'll then be able to access all your notes from any computer with internet access.

---

### Post by webcabbie on 2010-12-01
I am looking to do something similar.. There is a forum I read that uses Vbulletin but the site goes down alot and I hate reading scrowling on a screen. 

I clicked file save grabbed the relevant html doc and opened it with gedit. 

Now how do I remove all the html text? Is there a search and replace function that I can use or are there gedit plugins?

---

