---
title: "Listen to my online radio station"
date: 2005-12-31
forum: The Cafe
---

### Post by JimmyJazz on 2005-12-31
[http://jimmyjazz.homeip.net:808/listenwavy/](http://jimmyjazz.homeip.net:808/listenwavy/)

It runs 100% on UBUNTU power even the web page was made in 100% UBUNTU.

enjoy.

---

### Post by sapo on 2005-12-31
Already playing here.

And i really loved your page, its pretty :D, and i peeked at the source code too.. just a question, why dont you use XHTML?

I ll post later if i like the songs :mrgreen:

---

### Post by JimmyJazz on 2005-12-31
[QUOTE=sapo]Already playing here.

And i really loved your page, its pretty :D, and i peeked at the source code too.. just a question, why dont you use XHTML?

I ll post later if i like the songs :mrgreen:[/QUOTE]


I usally do but I kinda rushed that page I'll probally modify it to XHTML standards sometime very soon.

---

### Post by sapo on 2005-12-31
[QUOTE=JimmyJazz]I usally do but I kinda rushed that page I'll probally modify it to XHTML standards sometime very soon.[/QUOTE]
I said it cause your code is kind clean and just a few details doesnt make it a valid xhtml page, btw your radio is nice, alredy in my bookmarks :mrgreen:

---

### Post by Cope57 on 2005-12-31
If you need some web designs check out [http://www.oswd.org/](http://www.oswd.org/)

---

### Post by bonzodog on 2005-12-31
Is that listed on shoutcast.com? - do so if it's not.

---

### Post by JimmyJazz on 2005-12-31
[QUOTE=Cope57]If you need some web designs check out [http://www.oswd.org/](http://www.oswd.org/)[/QUOTE]

thanks but web design is what I do.

---

### Post by JimmyJazz on 2005-12-31
[QUOTE=bonzodog]Is that listed on shoutcast.com? - do so if it's not.[/QUOTE]

yeah its listed on Shoutcast just search for "WAVY"

---

### Post by majikstreet on 2005-12-31
great design.. i wish i could design like that :(

---

### Post by JimmyJazz on 2005-12-31
[QUOTE=majikstreet]great design.. i wish i could design like that :([/QUOTE]

designing webpages is easy, making them work in IE is not :)

---

### Post by sapo on 2005-12-31
[QUOTE=JimmyJazz]designing webpages is easy, making them work in IE is not :)[/QUOTE]
True! But design needs talent, wich i dont have ANY, but coding is my thing :mrgreen:

[quote=majikstreet]great design.. i wish i could design like that :([/quote]

i wish the same :(

---

### Post by DaMasta on 2005-12-31
Hey, JimmyJazz (I can only assume this is a Clash reference, if so two thumbs up), I responded to your very old how to in the hoary section but I'll ask it here too. Any idea how I can get the scrobbler plugins to recognize the id3 tags? It says its a bad id3 tag or it doesn't have one. I know all my songs have them. I'd like to get my last.fm profile update when I'm listening to my station. Any idea?
Also, is there an advantage to shoutcast over icecast? The latter seems a little more difficult to set up which is why I went with shoutcast.

---

### Post by JimmyJazz on 2005-12-31
[QUOTE=DaMasta]Hey, JimmyJazz (I can only assume this is a Clash reference, if so two thumbs up), I responded to your very old how to in the hoary section but I'll ask it here too. Any idea how I can get the scrobbler plugins to recognize the id3 tags? It says its a bad id3 tag or it doesn't have one. I know all my songs have them. I'd like to get my last.fm profile update when I'm listening to my station. Any idea?
Also, is there an advantage to shoutcast over icecast? The latter seems a little more difficult to set up which is why I went with shoutcast.[/QUOTE]

I was looking into that issue a while back and found that AudioScrobbler dropped the feature allowing streams meta-data to be submitted to AS servers, appearently it was causing some problems.  Streams don't use actual ID3 data but special meta-data.  You might try requesting that they return this feature at their home page.

I use Shoutcast (to serve) mostly because its really simple and reliable.  Icecast actually seems to be better and have more features though.  I have used it for a short time but found I had stability issues with it.

---

### Post by DaMasta on 2005-12-31
Okay, thanks.

---

### Post by Gray. on 2005-12-31
Nice radio and nice station! I too wish I could make nice web pages... even the great DreamWeaver can't save me.. lol

---

### Post by JimmyJazz on 2006-01-07
I updated the page today to XHTML
[http://jimmyjazz.homeip.net:808/listenwavy/]("http://jimmyjazz.homeip.net:808/listenwavy/")

---

### Post by DaMasta on 2006-01-07
Where are you pulling the current track playing and next track from? When I run ices, I don't know whats coming up next until like 10 seconds before the previous song ends.

---

### Post by JimmyJazz on 2006-01-07
[QUOTE=DaMasta]Where are you pulling the current track playing and next track from? When I run ices, I don't know whats coming up next until like 10 seconds before the previous song ends.[/QUOTE]

I wrote my own DJing software in python that works along side of ices.
But you can generally pull the data from your playlist as long as you turn the random track feature off in ices.

---

### Post by eriqk on 2006-01-07
[QUOTE=JimmyJazz]I updated the page today to XHTML
[http://jimmyjazz.homeip.net:808/listenwavy/]("http://jimmyjazz.homeip.net:808/listenwavy/")[/QUOTE]

You shoegazer you! 
Enjoying now. Thanks!

Groet, Erik

---

### Post by DaMasta on 2006-01-07
[QUOTE=JimmyJazz]as long as you turn the random track feature off in ices.[/QUOTE]
Yeah, that's what I was thinking. Know of a good way to jumble up my playlist?

---

### Post by JimmyJazz on 2006-01-08
> Yeah, that's what I was thinking. Know of a good way to jumble up my playlist?

[http://jimmyjazz.homeip.net:808/shufflefilelines.py](http://jimmyjazz.homeip.net:808/shufflefilelines.py)

you can download the above python script (which I made just for you btw)
install it anywhere you want (/usr/local/bin) and run it like so...

shufflefilelines.py /the/path/to/your/song/list.lst

it will shuffle the file and create a new one called <yourfilename.list>.shuffled in the same directory (I force it to make a new file to avoid accidents that may ruin important files)
Anyways just point ices to that newly shuffled file and you are done.

---

### Post by JimmyJazz on 2006-01-08
also you may wanna take a look at you ices.cue file which gives you information about the current playing track (like 5 I think is the current position in your playlist ices is reading from)

---

### Post by maruchan on 2006-01-08
Very slick site! The tunes are nice too, thanks for serving 'em up. Looks like you use Bluefish, may I ask what you like about it? I haven't used it much.

---

### Post by JimmyJazz on 2006-01-08
[QUOTE=maruchan]Very slick site! The tunes are nice too, thanks for serving 'em up. Looks like you use Bluefish, may I ask what you like about it? I haven't used it much.[/QUOTE]
Bluefish is simple and lite and has a nice little reference feature.  I use Quanta sometimes too though just depends on if I am in KDE or Gnome

---

### Post by Jaygo333 on 2006-01-08
[QUOTE=JimmyJazz]designing webpages is easy, making them work in IE is not :)[/QUOTE]

What do you mean by that? I'm trying to learn how to create webpage and let's just say its a pain in the a$$.
 Now, I'm experimnting with XAMPP. 
I'm so new to this.  
Teach me if its so easy. 
PLEASE.1?1

And a Question to the owner. How did you do that. 
I want to make a webpage and want mine as "SMOOTH" as yours. 

Teach ME.1?1

:\\:D/:h34r: Jaygo333 :\\:D/:h34r:

---

### Post by quonsar on 2006-01-08
very nice. bookmarked!

---

### Post by DaMasta on 2006-01-08
[QUOTE=JimmyJazz][http://jimmyjazz.homeip.net:808/shufflefilelines.py](http://jimmyjazz.homeip.net:808/shufflefilelines.py)

you can download the above python script (which I made just for you btw)
install it anywhere you want (/usr/local/bin) and run it like so...

shufflefilelines.py /the/path/to/your/song/list.lst

it will shuffle the file and create a new one called <yourfilename.list>.shuffled in the same directory (I force it to make a new file to avoid accidents that may ruin important files)
Anyways just point ices to that newly shuffled file and you are done.[/QUOTE]
Thanks for the script. I haven't tried it yet. I had looked at ices.cue the other day. Just finished my php script to automatically refresh the now playing list. Only thing it doesn't take into account is how much the end user has buffered. Not sure how to go about calculating that, or if it is even possible. But, unless the buffering is way queued up, it's still pretty effective.

---

### Post by JimmyJazz on 2006-01-08
[QUOTE=DaMasta]Thanks for the script. I haven't tried it yet. I had looked at ices.cue the other day. Just finished my php script to automatically refresh the now playing list. Only thing it doesn't take into account is how much the end user has buffered. Not sure how to go about calculating that, or if it is even possible. But, unless the buffering is way queued up, it's still pretty effective.[/QUOTE]

yeah I wouldn't really think it would be at all possible to figure out how much they have buffered but it really shouldn't matter because most people only buffer 30 seconds or so anyway.

---

### Post by JimmyJazz on 2006-01-11
I was considering making my DJ software (for ices) available, would anyone be interested?

---

### Post by majikstreet on 2006-01-11
:)

yeah.. i may be interested :p I'd have to fiddle with ices, though.

---

