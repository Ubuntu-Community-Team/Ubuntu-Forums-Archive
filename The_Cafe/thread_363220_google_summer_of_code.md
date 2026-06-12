---
title: "google summer of code"
date: 2007-02-16
forum: The Cafe
---

### Post by ssam on 2007-02-16
[Google's summer of code]("http://code.google.com/soc/") is on for 2007.

This is a project to pay a few hundred students to work on open source projects over the summer.

so does anyone here have any great ideas for projects? you can suggest ideas for any existing software, or an idea for something completely new.

Note: I am not asking this is an sort of official way. i am not from google or anything like that.  I just want to hear if any of the ubuntu forum people have good ideas.

---

### Post by FredSambo on 2007-02-16
[img]http://fredsambo.com/fred/hacking.jpg[/img]

---

### Post by ssam on 2007-02-16
if we are going to hiding in a dark room, we may as well be coding :-)

---

### Post by ssam on 2007-02-18
anyone?

---

### Post by G Morgan on 2007-02-18
A decent config tool for X which handles multiple monitors and compositing. There should be both GUI and ncurses options. Best solution would be a series of text filters which handle the actual backend then plug either frontend in. Definitely something that desperately needs work in Linux.

Preferably it should extend to some form of hardware detection which can handle blobs if needed. Individual distros can tie in their own deployment method for blobs. I.E. On Ubuntu it will drag in the appropriate packages via apt.

---

### Post by ssam on 2007-02-18
> **G Morgan said:**
> A decent config tool for X which handles multiple monitors and compositing. There should be both GUI and ncurses options.

could it be added the resolution changing tool? i think there should only be options for thing that can't be auto detected.

the auto detection in X is getting much better, there will be monitor hot plugging soon. though i dont think X could ever auto detect which side of your desk your second monitor is on :-)

---

### Post by G Morgan on 2007-02-18
Didn't say it would tell you which side of the desk only offer you a set of lists and check boxes then generates your xorg.conf file for you. It should also handle seemless changing from dual to single monitors.

//edit - I will watch monitor autodetection with interest.//

---

### Post by G Morgan on 2007-02-18
Another tool might be a GUI that reads the list of modules available for your kernel then offers a list where you can activate or de-activate each module with the changes being made in /etc/modules.

It could link into a web server (or just download the information) to provide a description of what each module does.

---

### Post by maniacmusician on 2007-02-18
Perfect timing for this thread :)

I think we sorely need PDF editing applications that are on par with those found in Windows. Now that PDF is open, it should be at least a little easier to do.

---

### Post by ssam on 2007-02-18
> **G Morgan said:**
> Didn't say it would tell you which side of the desk only offer you a set of lists and check boxes then generates your xorg.conf file for you. It should also handle seemless changing from dual to single monitors.

what i mean is that you should not need to choose any option that could be autodetected.

the only things that i can think of that the user should need to choose in the gui are:
resolution (it should default to the highest resolution, but some people might want lower resolution for some reason)
screen rotation
colour depth
maybe colour profiles, if X can support this
layout of multiple monitors (is you second/third/... above or below or left or right)
mirror or span for multiple monitors.
open source or closed source driver (should be a simple option to flick between them)

@maniacmusician
PDF editing would be good. you might want to read [http://rants.scribus.net/2006/12/10/pdf-surgery/](http://rants.scribus.net/2006/12/10/pdf-surgery/)

---

### Post by aitorch on 2007-03-23
Hi! Im looking for some feedback, I wrote an Soc Application about "GNU/DEBIAN and UBUNTU: Possibility to comment and rate packages in Synaptic" here is it [http://mysummerofcode.blogspot.com/2...-and-rate.html](http://mysummerofcode.blogspot.com/2...-and-rate.html)

What do you think? its a good Idea. Im thinking too in a web based approach or a mix.

---

### Post by bash on 2007-03-23
I think all the so far mentioned ideas are good and should get worked on. Especially a GUI front-end for xorg.conf. We can't say we want to make Linux easier and more accessable to less Teche/Geeky/Nerdy people and then expect them, if they want to change anythig bigger (meaning really anything besides the screen resolution), to edit Textfiles. You should be able to set which Driver is used in a dropdown menu in a GUI tool. You should have a box where you can check and uncheck which driver modules are loaded (glx, dri, ...), you should have a part to specifiy details about your screen, have a box where you see the current resolutions and have an option to manually add/remove resolutions and more. And all of this done in one GUI frontend (maybe using one Tab for graphics card and driver, one for the screen and so on).

Also I agree that a PDF editing tool is needed. But not only an editing tool, but also a proper PDF creation tool. Yes you can export PDFs out of OOo. But your not always using OOo when you want to create a PDF. [CUPS-PDF](http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/) is already an ok way. The basic idea is pretty clever, but it lacks basic features found in this of programs for Windows. It misses basic features, such as the option to password protect a PDF, set restrictions on what users are allowed to do with the PDF and more. 

So I think theres plenty to do for those happy Code Monkeys. :D

---

### Post by bash on 2007-03-23
For some reason it wouldn't let me edit my post above. But I think [this](http://www.xfire.com/xf/modules.php?name=Forums&file=viewtopic&t=57683&postdays=0&postorder=asc&start=75#978468) would also be a good project for Googles Summer of Code.

---

