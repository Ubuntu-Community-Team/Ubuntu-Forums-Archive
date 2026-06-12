---
title: "Web based media manager"
date: 2011-03-31
forum: Server Platforms
---

### Post by nielsteekens on 2011-03-31
Hi,
I'm using Mediatomb as a media server on my server (text based only, no X) and quite happy with it.
However, Mediatomb does not do the media management.

So I'm looking for a web based solution that lets me import media in the library, automatically or manually retags (id3) and renames/moves media, does media lookup on the internet etc.
Does something like that exist?


Thanks

---

### Post by Ma®io on 2011-04-01
Hi,

I'm looking for this kind of solution as well.
I'd appreciate any suggestions.

Thanks,
Ma®io

---

### Post by robsablah on 2011-05-14
bumping

---

### Post by Ma®io on 2011-07-05
Hello,

I'm going to start creating own web based media manger and would like to ask you to provide me with list of features you would like to have (if you are interested in such solution).

I can not provide you with any estimates as I'm very busy with my current work but I will try to do my best to make it fast.

Thanks,
Ma®io

---

### Post by nielsteekens on 2011-07-05
I would be most interested! I tried adapting Subsonic myself, but found it was taking too much time.
Now for the wishlist:

General

[LIST]
[*]I don't care about a player, we have plenty of choice for that
[*]I'm only interested in music not video
[*]UPNP would be nice, but again there are many already.
[/LIST]
Library management:

[LIST]
[*]Import media into the library
[*]Edit ID3 tags, including internet lookup
[*]Rename/move media according to rules, using ID3 tags as source
[*]Adjust naming convention for files/album/
[/LIST]
Reporting

[LIST]
[*]On incomplete (adjustable) ID3 tags
[*]On files/album naming exception (against the rule defined above)
[/LIST]
On Windows I now use Helium Music Manager, which I quite like.
It does a lot of the above (except for the reporting).
Heliums  philosophy of first importing, then fixing the ID tags and only then  renaming the files, has saved me considerable time. ID3 tags can be  seriously messed up and when I was using Itunes this ruined the  structure of the library. 

Hope this helps!

Let me know if you need beta testing on Ubuntu 11.11

Regards

---

### Post by arrrghhh on 2011-07-05
I would be interested as well.

I usually look at the file names and groom them with a Bulk Rename utility, then use MP3Tag to groom the ID3 tags.

I think if there was a web-based solution to do this that would be great!  I also have to move the files around, but ajaXplorer seems to be OK at this - perhaps something extended on ajaXplorer?  I like the concept of ajaXplorer, but I have trouble with how it's implemented.

---

### Post by Ma®io on 2011-07-05
Thanks for answers!

I'd like to implement the solution starting with Library Management functions wich I need as well.

Beta testing would be great so I'll let you know as soon as I implement something.

Thanks,
Ma®io

---

### Post by cj13579 on 2011-08-20
Hey guys, you should check out Jinzora - [http://en.jinzora.com/](http://en.jinzora.com/) this does everything you have asked for I believe aswell as giving you ability to stream your music from anywhere should you so wish!

For pure tag editing can I point you in the way of puddletag [http://puddletag.sourceforge.net/](http://puddletag.sourceforge.net/) a great tag editor which can be run from your headless server so long as you have an xwindows server running on the machine you are connecting from.

Both Jinzora and Puddletag have good help pages on their sites and solid, detailed READMEs should you want to try them out.

Additionally, should you wish to do stuff for videos in the future Jinzora works with those (although not as well in my opinion). For music though - brilliant. I love it.

Hope this helps!

---

### Post by nielsteekens on 2011-09-29
Chris,
Jinzora does some ID3 tag editing, but lacks virtually all features for library management.
As most web based solution available today, it is all about streaming and presentation.

What I was looking for is back-end management: i.e. mass rename, naming convention, two-step import into library (first add songs/album, then based on corrected tags, move and rename the file/folders into library location), reporting on dupdlicates or empty tags.
A totally different approach.

---

### Post by cj13579 on 2011-09-29
> **nielsteekens said:**
> 
What I was looking for is back-end management: i.e. mass rename, naming convention, two-step import into library (first add songs/album, then based on corrected tags, move and rename the file/folders into library location), reporting on dupdlicates or empty tags.
A totally different approach.

Fair enough, Jinzora definatly wont handle that - have you found something that works for you yet?

---

### Post by nielsteekens on 2011-09-29
No, still searching. I abandoned the idea of creating/modifying something, I won't maintain it anyway..

---

### Post by cj13579 on 2011-09-29
> **yucww210 said:**
> Well done ,learn more:o

read more, or read more closely is probably the thing.

At least they both got a good plug anyhow!!

---

### Post by cj13579 on 2011-09-29
@nielsteekens Have you tried sticking your original bit of Windoze software into [Alternative To]("http://alternativeto.net")? I just stubled upon it a few days ago.I just put "Helim Media Manager" into it and it came back with a load of results. Don't know if any of them will be any good but perhaps worth a try.

---

### Post by nielsteekens on 2011-09-29
Well, it gives me all linux variants like Amarok. Which I know exists, but isn't exactly web based.
It's intended to run on a headless server.

---

