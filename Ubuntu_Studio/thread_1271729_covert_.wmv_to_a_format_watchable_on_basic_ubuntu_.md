---
title: "covert .wmv to a format watchable on basic ubuntu install"
date: 2009-09-21
forum: Ubuntu Studio
---

### Post by izak on 2009-09-21
Hi all,

I want to show a small .wmv video to my class on my laptop, which has a the standard CD installation of Jaunty (in other words no extra video codecs intalled). I cannot connect the laptop to the internet to easily update the codecs, so I want to convert the .wmv to a different format using my desktop (which is connected). 

After browsing some threads I installed Mencoder, which seems as though it might be the right tool for the job.

Which video format should I output to so it is playable by a standard CD installation of Jaunty? Will mencoder be able to do this? Any pointers on what such a command might look like will be much appreciated. 

Thanks

---

### Post by bumanie on 2009-09-21
vlc player should play .wmv format without the need of extra codecs. > sudo apt-get install vlcFind it under Applications --> Sound & video --> vlc player

---

### Post by izak on 2009-09-21
the laptop I want to play the video on is not connected, so unless VLC and all its dependencies are on the standard installation CD, I cannot easily install it. It only has the standard media player installed. 

What I want to do is convert the video on my desktop, where I can easily install whatever software is needed for the task.

---

### Post by trulan on 2009-09-21
I use WinFF for converting videos.  It's a nice open source program, does a great job (uses the ffmpeg libraries) and you can convert to pretty much whatever you want.  There are windows and linux versions of WinFF.

---

### Post by Stochastic on 2009-09-21
Unfortunately, you just can't do it unless you have the codec installed.

In order to convert it to a different format, you first need to decode the wmv, then re-encode to the desired format (this is usually seen by the user as one step rather than two, but the algorithm has two steps).  The first step requires the same libraries one would use to play it.

---

### Post by izak on 2009-09-22
That is not a problem since I want to do the conversion on my **desktop (with internet connection)** then copy and play the converted video on my **laptop (without connection)**. So I can install codecs and programs on my desktop, if I only knew which ones...

---

### Post by izak on 2009-09-22
@Trulan,

thanks for the tip, I see winFF is in the repos. 

Does anyone know which output video formats are supported by a standard ubuntu installation?

---

### Post by alphacrucis2 on 2009-09-22
> **izak said:**
> @Trulan,

thanks for the tip, I see winFF is in the repos. 

Does anyone know which output video formats are supported by a standard ubuntu installation?

mpg (mpeg2) should work. If you have no joy with winFF then try avidemux.

---

### Post by trulan on 2009-09-22
> **izak said:**
> Does anyone know which output video formats are supported by a standard ubuntu installation?
Why not go with true open source and use Ogg Theora?

---

### Post by izak on 2009-09-23
Urgh, this is taking more time than I am willing to devote to it. Installing packages (with their dependancies) to a machine without internet is always troublesome, but it seems video conversion is not easier.

avidemux gives: "Trouble initializing audio device" upon loading the .wmv

winFF gives: "Unknown encoder 'mpeg2video'" upon trying to convert wmv to mpg, which (as I found out after I googled it) is apparently a bug.

Thank you all for your help, but I am just going to give this up as a lost cause.

---

### Post by etnlIcarus on 2009-09-23
Christ, you should be trying to convert it to Ogg Theora, not mpeg.

Install ffmpeg2theora, make sure you've got all of ffmpeg's dependencies installed and it should be a piece of piss. If graphical tools fail, get to know ffmpeg via the command line.

---

### Post by izak on 2009-09-23
@etnlIcarus: 

ffmpeg2theora worked like a charm and was exactly what I was looking for. (I was slightly suspicious whether mpg would work on the standard install...)

simply typing ffmpeg2theora myMovie.wmv did the trick.

Thanks!

---

### Post by etnlIcarus on 2009-09-23
Only wish I'd seen this thread sooner.

---

