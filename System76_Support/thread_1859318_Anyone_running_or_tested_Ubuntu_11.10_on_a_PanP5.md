---
title: "Anyone running or tested Ubuntu 11.10 on a PanP5?"
date: 2011-10-13
forum: System76 Support
---

### Post by samalex on 2011-10-13
Hey Guys --

My PanP5 is still working great with Ubuntu 10.04, and though I generally don't reinstall except for when an LTS edition is released every two years I'm seriously thinking of jumping the gun to get 11.10 since I've heard some nice things about it.

So just curious, has anyone tested 11.10 on an older PanP laptop, maybe a 4 or 5?  Mine's a PanP5 that's over two years old now, but that thing still runs like a champ.  Also to the S76 folks, do you guys have 11.10 drivers for the PanP5 if I decided to move up to it?  The Knowledge76 site - [http://knowledge76.com/index.php/PanP4/PanP5](http://knowledge76.com/index.php/PanP4/PanP5) - only goes up to 10.10 so am I stuck with the drivers that come with Ubuntu if I move past 10.10?  

Thanks --

Sam

---

### Post by japhyr on 2011-10-16
I'm still running 10.04 on my panp5 as well.  I think I will upgrade to 11.04 soon, but I'm also curious to watch this thread and hear how 11.10 runs on the panp5.

---

### Post by Eldera on 2011-10-17
Upfront: I am only a hobbyist. I have no computer tech background. My only experience with Linux has been reading the forums and using the Pangolin I bought a little less than 3 years ago.

[quote=samalex]has anyone tested 11.10 on an older PanP laptop, maybe a 4 or 5?[/quote] 

I have successfully installed Oneiric 11.10 on my Panp4n, specs in sig.
With a couple of exceptions listed below everything seems to be working rather well.

I did not activate the proprietary nVidia drivers because everything seems to be working with whatever was shipped with the download.

I do not use WIFI, my webcam, or the fingerprint reader, so have not tested them. Also, I do not download my email to my computer. I just read it on my ISP's site and delete it. So, I have not tested any of the email programs in Oneiric or any of the social networking.

I don't know how much detail you people are interested in, but here is exactly what I did and why. 

I have been so satisfied with 10.04LTS Lucid that I intend to use it for my serious work until end of life or when I find something as good for my individual needs. However, I want to understand the new things in Ubuntu as they happen. To do both, I kept Lucid's partition untouched and installed Oneiric on a separate partition.

I made a live USB stick from the desktop 32bit download. I have run both 64 and 32 bit OS's on the Pangolin with no problems, but wanted to try the same stick   on a couple of other computers.

Install was fast and had no errors. 

I added my bookmarks to Firefox from a backup USB. No problem.

Downloaded the following from the Ubuntu Software Center:
	Ubuntu Restricted Extras
	Xsane
	HPLIP Toolbox
	Startup Manager
	GIMP
	Synapic (Could not find the GIMP user manual in the Software Center and knew it was in Synapic)

	Downloaded Gimp manual from Synapic.

All downloads were fast. Almost everything seems to be working. Have not had time to do much with GIMP.

The printing and scanner functions of my HP OfficejetJ6400 All-in-one are working.

I can play video from my favourite websites and DVD's.

The only things that haven't worked so far:

The screen for the System 76 driver did not close after running restore. I had to force quit to close it. The same thing has happened in Lucid and Natty.

After playing a DVD, I could not eject from the launcher. I had to eject it from within the Movie player program.

I downloaded over 500 mp3 files from a USB backup into Music and played a few of them in Banshee. They played very nicely. However when I went to quit the program, the window closed without the music stopping. I finally used REISUB to close the program. I need to Google the problem and don't have time right now.

Overall, I would say I had a very good install.

Unfortunately, Oneiric 11.10 is not a good fit for my working habits. I do as much as I can with the mouse. I do not like to type, never use keyboard shortcuts, and am just learning a few things with the terminal. 

The deal breaker for me is the workplace switcher. I like to open 8 or 10 workplaces and switch between them with one click, which one can do in Lucid.

I plan to read up on Gnome 3, and Gnome Shell and find out how to get into them from Oneiric, but for the time being I did the right thing for myself by keeping my Lucid 10.04 LTS partition.

Hope this helps someone. Eldera

Edit: I downloaded Rhythmbox, which played and quit correctly. I have no plans to troubleshoot Banshee.

---

### Post by samalex on 2011-10-17
Thanks Eldera for the review.  I might try the live CD and see how that fairs, but my main question at this point to the System76 folks is to see if they will offer driver support for the PanP5.  I do depend solely on Wifi for connectivity, but my webcam went out a year ago and though it was still under warranty I just never bothered sending it in for repair so I'm not concerned with it or the fingerprint scanner.

As for Unity I'm still up in the air on that, though I do want to check it out.  But in the end I'm glad they've made Gnome 3 available as an option if Unity doesn't pan out.

Sam

---

### Post by samalex on 2011-10-18
Honestly after reading more and more reviews about Oneiric I think I'll just keep running 10.04 LTS for a bit longer and see what 12.04 brings to the table granted that'll hopefully be the next LTS version.  And then I'll decide whether or not to jump ship to another distro or not.  I have't heard whether or not S76 will offer driver support for 11.10 and forward, which if not then there's no real reason to keep Ubuntu since the driver support through S76 was one reason I went with the PanP5 -- well that and because it's just an amazing system :)  

But honestly for now my system works great with little to no problems, so I guess I should leave well enough alone.  Maybe when 12.04 comes out, granted that has LTS, I'll peak my head into the Ubuntu cloud and give it a whirl, that or jump ship to Mint or OpenSuSE.  Not sure...

---

### Post by isantop on 2011-10-18
> **Eldera said:**
> 
I downloaded over 500 mp3 files from a USB backup into Music and played a few of them in Banshee. They played very nicely. However when I went to quit the program, the window closed without the music stopping. I finally used REISUB to close the program. I need to Google the problem and don't have time right now.


This is actually a feature. Banshee will continue to run after the window has been closed so that the player can be controlled through the sound menu. In the menu with the volume controls are a second set of player controls and a quick playlist selector that you can use to queue up songs and control the playback.

---

### Post by Eldera on 2011-10-19
[quote=samalex]Also to the S76 folks, do you guys have 11.10 drivers for the PanP5 if I decided to move up to it? The Knowledge76 site - [http://knowledge76.com/index.php/PanP4/PanP5](http://knowledge76.com/index.php/PanP4/PanP5) - only goes up to 10.10 so am I stuck with the drivers that come with Ubuntu if I move past 10.10? [/quote]

[quote=samalex]my main question at this point to the System76 folks is to see if they will offer driver support for the PanP5.[/quote]

Isantop, you missed the question samalex is asking and he is the OP of this thread. I was just commenting on my experience.

---

### Post by isantop on 2011-10-20
The Driver will work fine in Ubuntu 11.10, but it won't actually install any drivers, since there aren't any needed for the PanP5 anymore. All of the driver support is provided natively by Ubuntu.

---

