---
title: "Test my server please"
date: 2009-08-08
forum: The Cafe
---

### Post by Krupski on 2009-08-08
(MODS if this is in the wrong spot, please accept my apology and move it appropriately)

Hi all,

I just installed Apache 2 on my file server box. What I ultimately want is to set it up so that my kids can view saved movies and videos which reside on the server, on their IPOD touch things...

I would appreciate if someone could click the following link and just tell me if it all seems to work.

Also, please try to manually get into the /images and /videos directories and (hopefully) it will deny you.

My "web site" currently only has a main page with some text, a few links to the hardware used in the server, a photo of the server and a clickable link at the bottom which should allow you to view a short video of a P51 and F15E fighter plane side by side fly-by.

All of the content is "G" rated... completely work safe and I promise there are no viruses or tricks. 

I just want to see if it works.

If you can test it for me, please email me and tell me how it worked for you:

<snip>

And, the link is:


<snip>

Thanks!

-- Roger

---

### Post by CJ Master on 2009-08-08
Yes, it forbid me from going to images or videos.

---

### Post by wojox on 2009-08-08
Tried it both images and videos got 403 Forbidden. Seems to be set right.

---

### Post by Krupski on 2009-08-08
> **CJ Master said:**
> Yes, it forbid me from going to images or videos.

Did the links to hardware websites and the video work?

---

### Post by sydbat on 2009-08-08
> **Krupski said:**
> Did the links to hardware websites and the video work?Yup.

---

### Post by Krupski on 2009-08-08
> **sydbat said:**
> Yup.

Thank you all!

-- Roger

---

### Post by chrisxuk on 2009-08-08
> **CJ Master said:**
> Yes, it forbid me from going to images or videos.

Same for me :)

---

### Post by gletob on 2009-08-08
The airplane video is downloading and it looks good from here in Firefox and IE8 on Windows 7 Ultimate RTM 64 bit.  403s on images and videos.

---

### Post by RedSingularity on 2009-08-08
Looks good to me.

---

### Post by Tipped OuT on 2009-08-08
Everything seems good to me.

Windows XP Professional
Google Chrome 2.0.172.39

---

### Post by Sporkman on 2009-08-08
Why is port 21 open?

---

### Post by Krupski on 2009-08-08
> **Sporkman said:**
> Why is port 21 open?

Anonymous FTP...

You're welcomed to try it.

Only ports that should be open are:

21 - FTP
22 - SSH
80 - HTTP

---

### Post by dragos240 on 2009-08-08
Works great.

---

### Post by lisati on 2009-08-08
So far so good!

---

### Post by slakkie on 2009-08-08
Nice ftp server dude.

---

### Post by steeleyuk on 2009-08-08
Ubuntu 9.10 Server? Is that a good idea? :p

---

### Post by P1umb3r on 2009-08-08
Downloaded the airplanes video and got 200 k/s, worked great.

---

### Post by clonne4crw on 2009-08-08
Works for me. Good job!

---

### Post by koenn on 2009-08-08
> **Krupski said:**
> 
I just installed Apache 2 on my file server box. What I ultimately want is to set it up so that my kids can view saved movies and videos which reside on the server, on their IPOD touch things...

...
Also, please try to manually get into the /images and /videos directories and (hopefully) it will deny you.


All of the content is "G" rated... completely work safe and I promise there are no viruses or tricks. 

I just want to see if it works.


You do realize that one an browse ftp just as easy as http, right ?

---

### Post by Sporkman on 2009-08-08
> **koenn said:**
> You do realize that one an browse ftp just as easy as http, right ?

...babes!! :D

---

### Post by Sporkman on 2009-08-08
> **Krupski said:**
> All of the content is "G" rated... completely work safe

Yeah right - liar! :D

Brittany01 might disagree! ;)

---

### Post by Old_Grey_Wolf on 2009-08-08
> **Krupski said:**
> 
I just installed Apache 2 on my file server box. What I ultimately want is to set it up so that my kids can view saved movies and videos which reside on the server, on their IPOD touch things...

I didn't think Time Warner (Road Runner) allowed you to run a server on their network. At least that was the case with the user agreement I had.

---

### Post by Old_Grey_Wolf on 2009-08-08
> **Krupski said:**
> 
Also, please try to manually get into the /images and /videos directories and (hopefully) it will deny you.


OK,

Index of [deleted URL] /images/babes/

Up to higher level directory
Name 	Size 	Last Modified
File:000002.jpg 	33 KB 	11/16/2006 	12:00:00 AM
File:000010.jpg 	55 KB 	11/16/2006 	12:00:00 AM
File:000011.jpg 	33 KB 	11/16/2006 	12:00:00 AM
File:000012.jpg 	32 KB 	11/16/2006 	12:00:00 AM
File:000013.jpg 	35 KB 	11/16/2006 	12:00:00 AM
File:000014.jpg 	32 KB 	11/16/2006 	12:00:00 AM
File:001.jpg 	80 KB 	06/15/2001 	12:00:00 AM
File:0014.jpg 	153 KB 	04/15/2006 	12:00:00 AM
File:002.jpg 	67 KB 	06/15/2001 	12:00:00 AM
File:003.jpg 	62 KB 	06/15/2001 	12:00:00 AM
File:004.jpg 	70 KB 	06/15/2001 	12:00:00 AM
File:005.jpg 	62 KB 	06/15/2001 	12:00:00 AM
File:006.jpg 	64 KB 	06/15/2001 	12:00:00 AM
File:007.jpg 	57 KB 	06/15/2001 	12:00:00 AM
......

You are busted!

---

### Post by Chronon on 2009-08-08
Index of %/images/magazine-pdf/

Up to higher level directory
Name 	Size 	Last Modified
. . ..

also accessible

---

### Post by Old_Grey_Wolf on 2009-08-08
> **Chronon said:**
> Index of %/images/magazine-pdf/

Up to higher level directory
Name 	Size 	Last Modified
. . ..

also accessible

Nice pictures on that site...:lolflag:

---

### Post by dragos240 on 2009-08-08
Perhaps someone should have put a NSFW warning because of these pictures.

---

### Post by Tipped OuT on 2009-08-08
> **dragos240 said:**
> Perhaps someone should have put a NSFW warning because of these pictures.

Wait, how do I access it. :P

---

### Post by Sporkman on 2009-08-08
> **Tipped OuT said:**
> Wait, how do I access it. :P

ftp in the url instead of http.

---

### Post by Tipped OuT on 2009-08-08
> **Sporkman said:**
> ftp in the url instead of http.

Oh my God. :shock:

This is [COLOR="Red"]**NSFW**[/COLOR] people, I repeat [COLOR="Red"]**NSFW**[/COLOR]!

---

### Post by Krupski on 2009-08-08
> **Sporkman said:**
> ...babes!! :D

Oh you found that directory!  :D

---

### Post by matthew on 2009-08-08
Sorry, we have kids that access our site from school and others who access our site from work. I'm going to close the thread and remove the link. There are many NSFW links...

No infractions or anything, just protecting our reputation.

---

