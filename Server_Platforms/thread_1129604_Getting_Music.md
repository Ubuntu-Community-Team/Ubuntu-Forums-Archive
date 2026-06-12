---
title: "Getting Music"
date: 2009-04-18
forum: Server Platforms
---

### Post by ultblad1 on 2009-04-18
My friends and I have set up a server that we use to store files and stuff on. I was fooling around with some basic HTML, when I decided that it would be a good idea to have background music playing in one of my pages. However, I have tried a few tags to try to get it to play, but I hear no music. My friend (and local admin) says that there is something with the server config that I need to change, but I have no idea what that means.

Could anyone give me some information on what to do to get background music on a HTML page? Any information on the server config is appreciated! Thanks.

The music page is [here]("http://pegjudge.ath.cx:5050/toby/music.html").

---

### Post by koenn on 2009-04-19
> **ultblad1 said:**
>  ... when I decided that it would be a good idea to have background music playing in one of my pages. ...

it's usually not a good idea to have background music on web sites  :)

---

### Post by ultblad1 on 2009-04-19
I know it is not a good idea, but I want to try anyways. Besides, having a music player on the page did not work either.

The <embed> tag does not seem to work..

---

### Post by Thirtysixway on 2009-04-19
Can you post the code that you are using?

You may need to use a flash (Swf) music player.  Depending on the browser, perhaps the media player is just not kicking in to play the embeded media.

---

### Post by ultblad1 on 2009-04-19
The code I'm trying to use is:

```

<embed src="song.mp3" hidden=true autostart=true loop=true>
<noembed>
<bgsound src="song.mp3" loop=infinite>
</noembed>

```

Also, I'm viewing the page with Firefox 3.

---

### Post by Simian Man on 2009-04-19
Don't make websites that play music unless the whole point of the page is to play music (Last.FM for example).  This is the most annoying thing on the internet.

---

### Post by ultblad1 on 2009-04-19
Yeah I want to put up a music only page, but so far it's not working.

---

### Post by koenn on 2009-04-19
> **ultblad1 said:**
> The code I'm trying to use is:

```

<embed src="song.mp3" hidden=true autostart=true loop=true>
<noembed>
<bgsound src="song.mp3" loop=infinite>
</noembed>

```

Also, I'm viewing the page with Firefox 3.

bgsound is an IE-only tag, FF won't interpret it. 
the embed tag is depreciated, which may be why FF3 refuses to handle it, either because it's standards-compliant, or your doctype tells it to ignore depreciated tags.

If you have an older browser, you might use that to see if your code is correct (eg that an mp3 of that name exists in the same directory as your html)

Otherwise, this might help you out : [http://forums.mozillazine.org/viewtopic.php?f=38&t=439880&start=0&st=0&sk=t&sd=a](http://forums.mozillazine.org/viewtopic.php?f=38&t=439880&start=0&st=0&sk=t&sd=a)

If not, you'd be better off in the Programming section, people there actually know html and all that.

And if it all works out, do reconsider deleting that code anyway. You really shouldn't put background sound to web pages. :)

---

### Post by ultblad1 on 2009-04-19
Thanks, I think I will move this to the programming section.

---

### Post by Thirtysixway on 2009-04-19
> **koenn said:**
> bgsound is an IE-only tag, FF won't interpret it. 
the embed tag is depreciated, which may be why FF3 refuses to handle it, either because it's standards-compliant, or your doctype tells it to ignore depreciated tags.

If you have an older browser, you might use that to see if your code is correct (eg that an mp3 of that name exists in the same directory as your html)

Otherwise, this might help you out : [http://forums.mozillazine.org/viewtopic.php?f=38&t=439880&start=0&st=0&sk=t&sd=a](http://forums.mozillazine.org/viewtopic.php?f=38&t=439880&start=0&st=0&sk=t&sd=a)

If not, you'd be better off in the Programming section, people there actually know html and all that.

And if it all works out, do reconsider deleting that code anyway. You really shouldn't put background sound to web pages. :)

The embed tag is not deprecated.  It's still used for countless things including flash.

---

### Post by nandemonai on 2009-04-20
Working here.

I also agree about the not playing music on web pages thing. The least you can do for your users is provide the option to load it via a link or some such.

Forcing a download isn't real nice, especially to those running slow connections.

---

### Post by koenn on 2009-04-20
> **Thirtysixway said:**
> The embed tag is not deprecated.  It's still used for countless things including flash.

the blink and marquee tag is also still used ...

anyway, there seems to be some confusion :

here, 'embed' tags are depresiated : [http://www.w3schools.com/media/media_browsersounds.asp](http://www.w3schools.com/media/media_browsersounds.asp)
and here it's "new in html5" : [http://www.w3schools.com/tags/html5_embed.asp](http://www.w3schools.com/tags/html5_embed.asp)

I don't keep up with (x)html standards and browser compliance anymore, so i don't really know what's current standard and best practice, or even common web design sense :)

---

