---
title: "Can Anyone Recommend a good capture/edit application"
date: 2009-01-18
forum: Ubuntu Studio
---

### Post by Vince4Amy on 2009-01-18
There are loads of choices in the repos. Can anybody recommend a good application which can do the following:

[LIST]
[*]Capture Video
[*]Edit Video (For Example Cut Useless Parts of the video)
[*]Burn To DVD (Menu System Or Not It Doesn't Matter)
[/LIST]

Now that my video capture device works on Linux I'd like to not have to use Windows for this task any more so are there any apps which can do all of the above if not I can use one app for one thing and one for another but I'd just like some recommendations.

---

### Post by thorgal on 2009-01-18
what kind of video capture device ? you mean like cable TV and such ? I would recommened the MythTV suite (backend, frontend and modules like a file archiver, news, netflix, DVD handling, video, weather, etc, etc), it does all you mention and more :

[www.mythtv.org](www.mythtv.org)

---

### Post by Vince4Amy on 2009-01-18
Thanks for that but No it's nothing like that, just so I can occasionally capture video from my (tape) camcorder and sometimes my VCR. Both are connected via composite.

---

### Post by alegallo on 2009-01-19
I don't know any program that does all of it, but I'm not so experienced in Ubuntu.

I use Kino for DV grabbing, and it also works for basic editing.
I guess it should be able to import analogic video too, if your device is supported, but I cannot tell you for sure.

To be honest, I have been searching for months for a Nvidia VIVO driver, but no way :(

A great program for the "simple and dirty job" (cutting, de-muxing, converting, colour filtering and the like) is Avidemux, a real swiss army knife for video.

Advanced editing (for me) is called Cinelerra.

Authoring the DVD must be done with some other apps. 
I mainly use DVDStyler, sometimes ManDVD.

Then burning. Although I use Gnome, I don't like Brasero, so I installed K3B.

Just my 2 cents ;)

---

### Post by cotcot on 2009-01-20
Another 2 cents :

+1 for Kino to capture from firewire connected camcorder

Video editors : Blender VSE (comparable level as Cinelerra) is my preference. Easier to learn : Kdenlive.

DVD authoring : Devede  ; QDVDauthor

Burning : Brasero

---

### Post by RedRat on 2009-01-21
I agree that Kino is similar to Adobe Premier Elements. However, the current Ubuntu version does not capture HD DV from tape camcorders. Perhaps in another iteration it will be able to do that. The Ubuntu repos now contain 1.1 and I note that they are on 1.32 now at the Kino web site. I suggest that you take a look at that web site. 

The funny thing is, that once you get your HD video on your machine, Kino will edit it. Odd. I captured some HD video on my Windows machine and then moved it over to my Linux machine. Seems to work OK on the video.

---

### Post by cotcot on 2009-01-22
Kino does not seem to be able to capture HD. However the most recent versions of dvgrab can do (in command line) using ```
dvgrab -f hdv whatevername
```.

---

### Post by 4ebees on 2009-01-23
I'd second all the clever people ahead of me who have recommended kino :)

You may also wish to visit my new site:

[www.youcantdothatinlinux.com](www.youcantdothatinlinux.com)

It is mostly directed towards video editing in Gnu/Linux. There are some tips on the site as well as how-tos and links to other sites which have how-tos. 

I'm aiming to include what I know, what friends know and to include links to other material so I don't have to reinvent the wheel when I'm looking for information and neither to others.

It's only a new site and so has only a small amount of information; however it is growing slowly.

---

### Post by Vince4Amy on 2009-01-27
I'll give Kino a try. I don't need HD so that doesn't matter, thanks everyone:)

---

