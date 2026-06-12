---
title: "Slide shows on a DVD, help please"
date: 2010-04-08
forum: Ubuntu Studio
---

### Post by sunwatt on 2010-04-08
Making slideshow DVD's is one of the only tasks I have not been able to do with Ubuntu/Linux Mint.

Most people doing multimedia may be doing video, but I work with jpg's and sound files, its what I do.

So I have been using XP on an old PC with Nero 7 Ultra installed, plus ProShow Gold, which I like the best of the two. These 2 Windows progs display the project very nicely, and make it quite easy.

None of the open source programs have worked for me. Maybe I could use a little help getting started, I dont know. Perhaps there is some open source software that will do what ProShow does so nicely. I dont mind learning new software, but so far Ive been stumped on this one.

Otherwise, Ubuntu/Linux has been a exciting experience, it does 90% of what I want a computer to do, with no crashes, or virus's to worry about.

My computer is a Dell Vostro 90 (Mini 9) with 2GB ram, and a 32GB SSD. Naturally I have the Dell external DVD burner that they sell with the Mini 9 and Vostro 90.

Thanks!

Jim

---

### Post by LuridCinema on 2010-04-10
You can easily drop the images into an NLE video editor such as Openshot and render for DVD.. easy. You will also be able to add titles and transitions.

Other Linux NLEs will work too. Kdenlive, Kino Lives, Cinelerra. etc

---

### Post by 23dornot23d on 2010-04-10
After down loading and having a little tryout that looks really good ..... thanks for posting the link ..... works in Lucid with the PPA great ... cheers ;)

---

### Post by sunwatt on 2010-04-11
> **LuridCinema said:**
> You can easily drop the images into an NLE video editor such as Openshot and render for DVD.. easy. You will also be able to add titles and transitions.

Other Linux NLEs will work too. Kdenlive, Kino Lives, Cinelerra. etc

Thanks for the reply, I have this Dell Vostro, a Mini 9 clone w/ 32GB SSD, and an original Mini 9, with a 16GB SSD. Both have Mint 7 distro installed right now, which is ideal for newbee's like me. 

I might try installing Studio 9.10 over Mint on my backup Mini 9, just to have a distro that includes Openshot.

Does Ubuntu Studio 9.10 come with Openshot installed? How about Ubuntu 9.10, or Kubuntu 9.10?

If they all have it, which distro boots up fastest  :)

Mint 7 does not have openshot in synaptic, I've never installed any software from a webpage since I switched from Windows. So, not sure how that works.

[http://www.openshotvideo.com/2008/04/download.html](http://www.openshotvideo.com/2008/04/download.html)

My friend who introduced me to Linux/Ubuntu told me to always download from Synaptic. Only on rare occasions do you ever download open source software from a webpage. So, I'm trying to follow these directions.

However.

The simplest way for me to try Openshot would be to install it on my backup Mini 9 with Mint 7 on it, keeping Mint.

If that will function ok. 

BTW, I just installed DVD-Slideshow from the Mint 7 synaptic. It also installed DVDAuthor. But they are not found under Applications, Sound and Video.

How do I find and run DVDAuthor? As I understand it, this is the front end of dvd - slideshow.

If I can find what I installed last night  :)  maybe they will work for me, and I'll try Openshot later.

Thanks

Jim

---

### Post by LuridCinema on 2010-04-12
You might try opening a terminal and typing in the name of the program to open it

You do not need a "studio" release to get openshot... just install it. look on the openshot site for installation instructions for your distro

You can also make a video of images using ffmpeg command line
The below code would  start w/ jpg images w/ 3 digit numbers and create an .avi file , you could the drag he avi file into a DVD creator
```

ffmpeg -f image2 -i %03d.jpeg -r 06 -sameq OUTPUT.avi

```

---

### Post by gordintoronto on 2010-04-12
Cinelerra is in Synaptic, and you can drop images and music into it to make a slideshow. Mind you, it is overkill.

If you are not afraid of the command line, there is a program called dvd-slideshow. (It might even be installed by default in Mint.)

After installing it, you can open accessories/terminal and enter the command:
man dvd-slideshow
to see how to use it.  Press "q" to exit from the manual. One advantage of this program is that it works from a text file, so if your DVD is not quite what you wanted, you just edit the text file and try again.

---

