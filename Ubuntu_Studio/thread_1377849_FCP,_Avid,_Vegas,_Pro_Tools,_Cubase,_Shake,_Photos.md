---
title: "FCP, Avid, Vegas, Pro Tools, Cubase, Shake, Photoshop etc."
date: 2010-01-10
forum: Ubuntu Studio
---

### Post by tdcooler on 2010-01-10
I've been watching Linux post production software development for about five years now.  Five years ago I thought "Wow in five years there will be a video editor."  Well it's been five years and it seems that there isn't a lot of improvement, or at least I'm not aware of it.  This is not a criticism as Open Source is built on the backs of the working man/woman.  I decided to change careers and am currently back in school studying computer engineering.  I would really like to develop open source multimedia hardware for the linux platform.  To do this I will need to find the most stable software applications possible that are comparable to the industry standard.  What video and audio programs seem the most solid or seem to have the most potential for the prosumer/professional multimedia production specialists in your opinion on the Linux Platform and what would you compare them to?

I would like to get involved, especially in the video editing, in helping the programs that really show promise.  I think the idea of having the FCP Studio + Photoshop + 3D studio package that would really shake up the industry.  What do you all think?

---

### Post by staf0048 on 2010-01-10
> **tdcooler said:**
> I've been watching Linux post production software development for about five years now.  Five years ago I thought "Wow in five years there will be a video editor."  Well it's been five years and it seems that there isn't a lot of improvement, or at least I'm not aware of it.  This is not a criticism as Open Source is built on the backs of the working man/woman.  I decided to change careers and am currently back in school studying computer engineering.  I would really like to develop open source multimedia hardware for the linux platform.  To do this I will need to find the most stable software applications possible that are comparable to the industry standard.  What video and audio programs seem the most solid or seem to have the most potential for the prosumer/professional multimedia production specialists in your opinion on the Linux Platform and what would you compare them to?

What about programs like LiVES ([http://lives.sourceforge.net/](http://lives.sourceforge.net/)) or Cinelerra ([http://cinelerra.org/getting_cinelerra.php)?](http://cinelerra.org/getting_cinelerra.php)?)

I've not used either one too much, but they certainly look like they have plenty of features for casual to advanced film editing.

---

### Post by tdcooler on 2010-01-10
Yes I'm looking at both of those.  It would be great to know how other people feel about their development community if a programmer.  If a user which one do you like and why?  I read on this site that the cinerella creator was difficult to work with but I've also heard about a fork Lumiera project that seems to not be ready yet.  For those of you that have used FCP which one seems to be going in the right direction?

---

### Post by staf0048 on 2010-01-10
> **tdcooler said:**
> Yes I'm looking at both of those.  It would be great to know how other people feel about their development community if a programmer.  If a user which one do you like and why?  I read on this site that the cinerella creator was difficult to work with but I've also heard about a fork Lumiera project that seems to not be ready yet.  For those of you that have used FCP which one seems to be going in the right direction?

I will say that I totally agree that Cinelerra is WAY too complicated for an "introductory" video editor.  I'm just now getting familiar with LiVES and have not formed an opinion on it yet, but so far so good.

I've not heard of Lumiera, but interested to see how it develops.  All in all though, I agree with your stance that video editing in Linux is still in its infancy for home users.  From what I recall a lot of Pixar movies are created using Linux, I just don't know what software they use, but I'd venture to geuss that its something proprietary and _very_ expensive.

---

### Post by kayosiii on 2010-01-10
There are a number of industry leading packages available on Linux.... They aren't necessarily cheap (in fact most of really big content creation shops are Linux based).

One of the packages you mention in your headline (Shake) is and always has been available for Linux (as much as I am sure Apple would prefer not to offer it). Along the same vein you can look at nuke. For 3D you can look at Maya, Houdini & SoftImage. These are all industry heavy weight packages that have a long history of working with Linux.

Linux currently doesn't have native industry heavyweight packages for sound,video (as opposed to compositing) or Image editing.

For Audio you can either side with one of the smaller products that has bean ported recently (eg reaper) or you could look at the flagship OS digital audio workstation Ardour. Ardour's development is currently funded and very healthy. 

For video and image editing things are a little less favourable. Cinelerra works if you are prepared to bend over a bit to accommodate it.
There are other tools on the way (they have been on the way for a very long time). If Lumiera lives up to the hype I shall be very happy. With Photo editing It's a similar situation the gimp is by far the most complete native tool. But it falls short on some functionality and has very little active development happening at the moment. Krita currently has a very healthy developer base and some funding to do the necessary but boring bits. In general I would look for projects with healthy community and many developers. I would look for projects that have some how managed to figure out how to fund part of their development. If pressed today I would go for.

Video: Blender 
Compositing: Blender, Nuke or Houdini.
3D: Blender, Maya, XSI and or Houdini and Wings3d
Realtime 3D: Unigine or Blender Game Engine 
Sound: Ardour, Hydrogen, Zynaddsubfx.
Images: Photoshop + wine, Krita, Mypaint, Inkscape.

It would depend a large degree on what my budget was and what the deliverables were.

---

### Post by tdcooler on 2010-01-10
Thanks for the reply.  It appears that Blender is the most useful tool for now.  I've heard a lot of complaints that blender isn't focusing much on the NLE.  That makes sense considering it's for compositing.  Am I right to compare Blender to Combustion and After Effects?  Though I like the concept behind Lumiera, the name, well let's just say it could be better.  I just don't think it's very catchy and I'm actually qualified to say so.  Well my previous Studio job in Burbank, CA says I am anyway.

I am currently only programming with C++ as I'll be using it for another year in college.  Is Blender and Lumiera using Python?  It appears that these two may actually have a future.  At least Blender does.

It seems that there are too many small projects.  which ones do you all think we (I) should consider supporting?  How can we get the community more focused or are the politics too great?

---

### Post by kayosiii on 2010-01-11
Blender is primarily a 3D app but it does a bit of everything. It just happens that it is one of the more stable and feature filled video editors that works on linux. Right at the moment the focus is a major UI overhaul and completing project Durian ([http://durian.blender.org](http://durian.blender.org)). So except where it is needed for Durian I don't expect to see a lot of focus on the sequence editor.

Blender is written in C (or C++?) with some parts written in Python (don't worry python is really easy to learn). Not sure about Lumiera but I am guessing that it is at least partially written in C/C++.

As for support - I say support any project which does things the way you want to do them (regardless of size). However some projects are currently healthier than others. 


Blender - really healthy at the moment. I predict that this is going to be a big year for blender.

Lumiera - Way too early to call. Doesn't seem to be moving as fast as I would hope. It seems like a release is some ways off.
 
Cinelerra - Its pretty good if you feed it the right files and are familiar with 3 point editing. Main developer is completely unresponsive to outside help. I think it would be better to go straight to Lumiera.

The GIMP - this project is really unhealthy. It has had approx 2 and a half developers for many years now.

Krita - Raised funds for a full time developer for 3 maybe four months. looks a lot more healthy going out of 2009 than they did coming into it (already has up to 32bit per channel images, layer effects, etc - needs stability, speed).

Ardour - Main developer is funding himself through donations on website is able to work full time and this shows. This is the closest thing you are going to see to Protools on Linux for quite some time.

Inkscape is going slow and steady. It is already a very usable project ditto for Scribus.

Kdenlive and Openshot might be worth a lookin. Pitivi will have fulltime programmers working on it but I doubt will be aimed at professionals.

Once a project gets above a certain size it really needs programmers working on it full time. I think that the unix "a tool for a single task philosophy" works quite well as many projects can create simple tools and those can be used together. This works particularly well for audio software under linux (thanks to jack) and while I would like to see improvements, jack is something that really makes doing sound on linux worthwhile. I would love to see something similiar for processing video.

---

