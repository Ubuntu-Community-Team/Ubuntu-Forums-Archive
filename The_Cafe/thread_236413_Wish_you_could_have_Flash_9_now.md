---
title: "Wish you could have Flash 9 now?"
date: 2006-08-14
forum: The Cafe
---

### Post by forrestcupp on 2006-08-14
Just make them think that you have it.  Check out this post by Malac:

> **Malac said:**
> This will make most sites think you are running version 9 in Ubuntu even if you are not.
Don't forget to copy/backup the file before editing it.

Open the file ~/.mozilla/firefox/pluginreg.dat
change
Shockwave Flash 7.0 r63:$
to
Shockwave Flash 9.0 r63:$

My boy used to love the playhouse disney website until they changed to Flash 9.  I tried this, and the disney site worked just like it always used to, games and all.

All credit goes to Malac, the ruler.

---

### Post by Rackerz on 2006-08-14
Wow, will try this out. No doubt some site's wont be viewable.

---

### Post by %hMa@?b&lt;C on 2006-08-14
nice find. flash 7 still doesnt show flash 8 perfectly though, it is a big step up!

---

### Post by jISh on 2006-08-14
Heh, nice trick!

---

### Post by GuitarHero on 2006-08-14
Didnt do anything...

---

### Post by Rackerz on 2006-08-14
Can you view Flash 9 sites?

---

### Post by GuitarHero on 2006-08-14
No I cant, not even 8.

---

### Post by dabear on 2006-08-14
Lol, this *won't* transform your flash player to version 9. This trick will only fool those sites falsly requiring flash 9 features, by bumping the version number in the pluginreg.

So if a site *really* uses features in flash 9 that doesn't work in v7, this trick won't help.

---

### Post by Rackerz on 2006-08-14
I know, just it shouldn't stop flash working altogether.

---

### Post by GuitarHero on 2006-08-14
Flash 8 never worked, flash 7 still does i think.

---

### Post by Mykewl on 2006-08-15
How do I open the file? When I try
I get "Permission denied" ](*,)

---

### Post by erikpiper on 2006-08-15
> **Mykewl said:**
> How do I open the file? When I try
I get "Permission denied" ](*,)

you have to open it as root. That will mean opening it in the terminal using "sudo" in front of the command like so:

"sudo gedit /filepathandname"

Gedit will open the file in- you guessed it- gedit.

---

### Post by Mykewl on 2006-08-15
Thanks Eric :D

---

### Post by H.E. Pennypacker on 2006-08-15
> **erikpiper said:**
> you have to open it as root. That will mean opening it in the terminal using "sudo" in front of the command like so:

"sudo gedit /filepathandname"

Gedit will open the file in- you guessed it- gedit.

Use gksudo, not sudo.

---

### Post by richbarna on 2006-08-15
> **H.E. Pennypacker said:**
> Use gksudo, not sudo.

Here's why :-
[http://www.psychocats.net/ubuntu/graphicalsudo.php](http://www.psychocats.net/ubuntu/graphicalsudo.php)

---

### Post by forrestcupp on 2006-08-15
Yeah, this doesn't magically change Flash into version 9.  It doesn't fix any of the bugs in version 7.  All it does is make a website think that you have 9 so you won't be blocked.  There are some sites that aren't using v.9 features but still require it.  Playhouse Disney is an example.  But I did notice that when my boy went to a newer area of the website that does use v.9 features, Firefox crashed.  So this helps with some things, but not all.

---

### Post by Yossarian on 2006-08-15
That's some trick.  I'll have to try it.

Edit: Added gusto

---

### Post by B0rsuk on 2006-08-15
No, I don't want flash. I used to.

It's time to move on. Flash is proprietary and closed. We should use something like svg (already partially supported by some apps like firefox and inkscape

[http://en.wikipedia.org/wiki/Scalable_Vector_Graphics](http://en.wikipedia.org/wiki/Scalable_Vector_Graphics)

With flash, you're always on mercy of Adobe. If, for example BSD systems become more popular on desktops, don't expect flash support for years. And once there is a player, everyone already uses newer versions and you can't access many sites.

---

### Post by forrestcupp on 2006-08-15
> **B0rsuk said:**
> No, I don't want flash. I used to.

It's time to move on. Flash is proprietary and closed. We should use something like svg (already partially supported by some apps like firefox and inkscape

[http://en.wikipedia.org/wiki/Scalable_Vector_Graphics](http://en.wikipedia.org/wiki/Scalable_Vector_Graphics)

With flash, you're always on mercy of Adobe. If, for example BSD systems become more popular on desktops, don't expect flash support for years. And once there is a player, everyone already uses newer versions and you can't access many sites.

That's fine, if the website you want or need to access uses svg.  Unfortunately, a lot of websites use Flash.  I would never develop a site that uses flash, but I can't help what other people do.  So if I need to access a site that refuses to use (or doesn't know about) something other than Flash, I'm automatically at the mercy of Adobe.

---

### Post by Hg80 on 2006-08-15
OMFG it works well done to you, i could almost kiss you lol

---

### Post by Brunellus on 2006-08-15
> **B0rsuk said:**
> No, I don't want flash. I used to.

It's time to move on. Flash is proprietary and closed. We should use something like svg (already partially supported by some apps like firefox and inkscape

[http://en.wikipedia.org/wiki/Scalable_Vector_Graphics](http://en.wikipedia.org/wiki/Scalable_Vector_Graphics)

With flash, you're always on mercy of Adobe. If, for example BSD systems become more popular on desktops, don't expect flash support for years. And once there is a player, everyone already uses newer versions and you can't access many sites.
All very well and good.  But tell that to the people who need to use flash to *access* certain services. 

There's also the GNASH project...but I'll wait on that for now.

---

### Post by Lord Illidan on 2006-08-15
This tactic worked well, thanks..My sister wanted to view some trailers.. All the film sites are damn flash only.

> No, I don't want flash. I used to.
 
 It's time to move on. Flash is proprietary and closed. We should use something like svg (already partially supported by some apps like firefox and inkscape
 
 [http://en.wikipedia.org/wiki/Scalable_Vector_Graphics](http://en.wikipedia.org/wiki/Scalable_Vector_Graphics)
 
 With flash, you're always on mercy of Adobe. If, for example BSD systems become more popular on desktops, don't expect flash support for years. And once there is a player, everyone already uses newer versions and you can't access many sites.

Regarding this, as much as you might hate it, flash is the de facto standard on the web not svg. It's similar to me using mp3 instead of ogg. I recognise the benefits of ogg, but my mp3 player does not support them, and I haven't the money to change players right now.

---

### Post by forrestcupp on 2006-08-15
> **Hg80 said:**
> OMFG it works well done to you, i could almost kiss you lol

Just remember, the credit goes to Malac.

My 3 year old boy thanks you, Malac.

---

### Post by deanlinkous on 2006-09-03
Strange that sounds just like my trick that I posted here....
[http://www.ubuntuforums.org/showthread.php?t=210945](http://www.ubuntuforums.org/showthread.php?t=210945)

btw- make sure you close your browser and reopen
Also depending on where and how you installed firefox the pluginreg.dat file may be located somewhere else so you can look aroudn for it or search your system for it.

---

