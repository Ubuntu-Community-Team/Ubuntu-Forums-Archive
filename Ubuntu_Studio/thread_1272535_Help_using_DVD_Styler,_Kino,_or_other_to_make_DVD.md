---
title: "Help using DVD Styler, Kino, or other to make DVD"
date: 2009-09-22
forum: Ubuntu Studio
---

### Post by sunwatt on 2009-09-22
When I used XP I produced seven  1 hour DVD slideshows that are showing on our local public access TV. I used Nero 7 Ultra for awhile, it has a slideshow feature, then I started using ProShow Gold, which is much better.

I switched to Ubuntu 9.04 about 3 months ago, and have a 2nd machine running Mint 7 Gloria.

DVD Styler and Kino is what I tried from synaptic so far, and I cant figure out how they work. Help!

How do I add a jpg file, & set the time I want it appear on screen, how do I add an audio narration, or mp3  that goes along with the series of pictures?  How do I add a frame with text I write? I need a program that lets me view my progress, and adjust the timing of pictures with the audio. Then it needs to burn the DVD, slideshow or produce a iso file that K3b can burn to a DVD. 

I prefer to stay with programs available in synaptic. 

I did try to run Nero 7 and ProShow with Wine Doors but it didnt go quite right, and I would rather PRODUCE this show with L:iunx. Using a Windows program is just wrong.

My next slide show will be a short documentary of a Windows PC with Blue screen, and show Liunx Mint Gloria installed, and go online.

I really like the Linux radio adv linuxad.ogg, which runs about 1 min and 13 seconds. Its really well done. It plays on some radio station somewhere, I got a copy of it from my Liunx guru Ian, in BC Canada.

OK, here is the url where you can download the Linux adv.

[http://linuxlock.blogspot.com/2009/09/tux-takes-to-airwve.html](http://linuxlock.blogspot.com/2009/09/tux-takes-to-airwve.html)

You want the long version.

Its a great promotion for Liunx, and I would very much like to produce a DVD for my Public Access station, using Liunx.

But I'm gunna need some help getting started please.

If you want to hear the Linux radio adv, let me know, we can work something out to get a copy to you.

Its very well done, I wish I had the name of the person who produced it! 

I'm sure its online somewhere.

Everyone should produce a DVD using this Liunx radio spot (1min 13sec) and get it played on your local public access TV station.

Or make one with your own narration. 

My documentary will mirror what happened to me with Windows, and show viewers how to save their old PC from the landfill, and give it new and better life with Linux.

Jim
Dell Mini 10V Unbuntu 9.04 120gb HHD 1GB ram
Dell Mini 9 Mint 7.0 8GB SSD 2GB ram

---

### Post by Keyper7 on 2009-09-22
I never used it myself, but I've heard that mandvd is quite good at making slideshows and very user-friendly. Try it, it's in the repositories.

Alternatively, you can do all video editing in a video editor and use DVD Styler or a similar program just to burn it. In this case, I recommend you try OpenShot.

---

### Post by sunwatt on 2009-09-22
Thanks, mandvd is downloading right now from synaptic.

I'll report back, up or down!

Thanks

Jim

---

### Post by sunwatt on 2009-09-22
Mandvd looks promising.

One problem is the size of the program window does not fit the display screen.

There is a X and a - on the upper right corner, no + sign and no way to re size the window to fit my display.

So I cannot see the bottom bit of the mandvd program window.

But this looks like it might do the job if I can fix this.

Ive noticed that most programs fit perfectly, but some are oversized for my display.

This is a Mini 9 Im using by the way.

---

### Post by Keyper7 on 2009-09-22
Hmm, yeah, I suppose some programs are not very netbook-friendly...

What's the highest resolution your display can give?

---

### Post by cotcot on 2009-09-22
SMILE is a slideshow making program (successor of Manslide). It might be a little bit shorty in features for what you want.
I think that you are better of with making an video with audio (most editors are able to do this) and then making a dvd with Devede or ManDVD.

---

### Post by sunwatt on 2009-09-22
[B] Its 1024x600. And I've seen a couple of other prgs that were "too tall" for my display.

And if there are any buttons at the bottom of mandvd, I cant see them.

I dont have any video equipment, but if I dont find a way to do this with slides, I have the option of letting the public access folks film an install.

Cotcot, thanks for the tip on SMILE, I'll check synaptic.

Thanks

Jim
[/B]

---

### Post by cotcot on 2009-09-22
It is not in synaptic. [[COLOR="Red"]Here[/COLOR]]("http://smile.tuxfamily.org/?q=node/2") are .deb packages for 32 and 64 bit.

---

### Post by sunwatt on 2009-09-22
Thanks cotcot

Did you hear the Liunx radio advertisement?

I put a link on my 1st post. Below the picture of the microphone.

It will make you want to do something with it.

Jim

---

### Post by sunwatt on 2009-09-22
I did a google search for mandvd screenshot.

[http://linux.softpedia.com/progScreenshots/ManDVD-Screenshot-12812.html](http://linux.softpedia.com/progScreenshots/ManDVD-Screenshot-12812.html)

Looks like everything I need!

But all those bottom buttons are not seen on my 1024x600 display.

Bummer, this is a very nice program.

Jim

---

### Post by FunkyRes on 2009-09-22
I've used kino in ubuntu succesfully.

kino creates the xml file for dvdauthor. You will probably want to edit the xml file, you will need to use a text editor (I use bluefish) and read the dvdauthor documentation.

Then you use dvdauthor to create the dvd structure and use mkisofs with the appropriate arguments to make the iso.

Not quite a GUI solution, but kino at least gets you started.

---

### Post by sunwatt on 2009-09-22
I got a good look at Mandvd just now. Using my old boatanchor laptop running Mint 7, I installed mandvd, and with the great 15" display I got to see all of mandvd.

(I had hoped to use my Mini 9, with 30watt power supply, the boatanchor laptop has a 150 watt PS, and I'm living with only solar power/batteries)

It looks good, I was able to add afew pictures right away, and a sound track.

It was simple to adjust the time a picture shows, and the special effects are all nice.

Problem is, I dont see any way of playing my test "creation", to edit it.

Tomorrow I'll give it a try with a DVD+R in the burner and see what comes out. But it seems there should be a "Play" button so I can check my work. Thats frustrating. Am I missing something?

A simple mp3 for a sound track, and afew jpegs to go as long as the song, that was easy. Tomorrow I see if it will burn a test DVD+R.

So, Ive come a ways, but still have to mess with mandvd to see if this is gunna work.

Thanks everyone for the suggestions.

Jim

---

### Post by sunwatt on 2009-09-24
Maybe its cuz of the external drive I have on my Dell Mini 9. But I have copied a DVD before on this same external drive, using DVD+R blanks. hmmmmmm

So, I made a slideshow with Mandvd, it saved it to a vob file I was able to watch with VLC. 

I got an error message when I tried to burn the test project to a DVD+R blank. I get as far as Generate DVD structure, I check Force ac3, and 4/3 Format defalut, the other choice is 16/9. Whatever that is.

Screenshot1 shows mandvd as it fails to burn the slideshow, and the error message.

It starts encoding video gets to the end and error message. 

Error when generating menu. Check console for details.

I attached screenshots of k3b saying insert a dvd-r blank, there was a dvd+r in the drive, whats up with that? Give it a dvd-R I guess?

But I was happy to see k3b open the vob file made by mandvd. I was happy to make a slideshow with mandvd I could watch with VLC.

Get this, Brasero opened the vob file, and created an iso! Thats what I tried to burn to a DVD+R with K3b. And yes, the iso also plays on VLC.

LOL... I'll keep trying, I'm getting close.

I just wonder if its true k3b needs dvd-r blanks???

Thanks

Jim

---

