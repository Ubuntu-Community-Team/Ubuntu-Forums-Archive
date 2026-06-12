---
title: "What would you recommend for these &quot;needs&quot;?  (Audio)"
date: 2008-05-30
forum: Ubuntu Studio
---

### Post by T4_ on 2008-05-30
Switching to Linux completely is dependent on one thing, and that's music production software. I don't even need something big! ;)

Basically, I was wondering what the recommendations here would be for someone (me) who would need the following:

- ladspa instruments
- ladspa effects/plugins
- a host, with sequencer/tracks, also capable of inserting audio files in a new track (and a piano roll, please)

I think that's about it (I'm easy). Now, I've played with Audacity, Ardour, AMS, and Rosegarden, but they're all so... big. Audacity wouldn't let me load instruments, Ardour crashed (earlier version wouldn't let me load instruments/effects), AMS was plain scary (not enough technical knowledge on my part) and Rosegarden tells me it cannot load plugins, plus it does not output any audio.
Now, I'm sure that over time and with plenty of posts on forums, googling, and more posts these issues can be resolved - but these applications are too feature-full anyway, so that's why I'm asking if there's a "smaller" solution that anyone knows of.

Any ideas and suggestions are appreciated :)

Thanks in advance,

T4_

---

### Post by Dougie187 on 2008-05-30
I would say check out Ubuntu Studio.

---

### Post by T4_ on 2008-05-30
> **Dougie187 said:**
> I would say check out Ubuntu Studio.When I first came across it, I made a note of it, but I haven't tried it out so far.  I assume Ubuntu Studio already includes a load of libraries/settings?

---

### Post by Dougie187 on 2008-05-30
Yeah. And it has a lot of programs people use for media composition and such. I believe it has stuff for making music, movies, and images. I have never used it but I look at it for software when I need. 

Here is a link:
[http://ubuntustudio.org/](http://ubuntustudio.org/)

and a snippet that they say about audio composition using it.
"For instance, Ardour 2 - A multitrack recorder/editor geared toward people familiar with Pro-Tools."

Here is a link for Ardour:
[http://ardour.org/](http://ardour.org/)

It might have something you can use. Personally I don't know what ladspa is, but you might be able to find something on there. Keep in mind too, if you like that program, but dont need all the other stuff Ubuntustudio comes with, you can add the ubuntu studio repos to your normal ubuntu installation and get the software without having to install all the other stuff.

EDI: Sorry, I just read your original post again, and how you had issues with Ardour. If ardour can do what you are looking for and you just have issues running it, you might ask questions about how to fix that in particular.

Just an idea.

---

### Post by Dougie187 on 2008-05-30
Here is another site that I found.
[http://users.ecs.soton.ac.uk/njl98r/code/audio/](http://users.ecs.soton.ac.uk/njl98r/code/audio/)

I hope this helps some. If I find anything else I will let you know. Also, ubuntu studio might have some other audio software rather then Ardour, you might check out its repo.

---

### Post by Stochastic on 2008-05-31
You may want to try LMMS, it has all the features you're looking for.  I would have suggested rosegarden, but it seems you've been put off it.  There are other alternatives too, such as Wired, and Jokosher, though both are in early development stages and aren't really ready for production use just yet.

Edit: I'm quite surprised ardour crashed on you, if you'd like I could help trouble shoot that with you, but then again ardour is only an audio editor, not a midi editor...  ...yet.

---

### Post by thorgal on 2008-05-31
ardour 2.5 is about to be released.
Being a daily user of this multitrack audio software, I can only recommend, it is really full of features, but you can also use it for simpler tasks.
The 2.4 serie was plagued by serious bugs that I considered showstoppers but Paul Davis and his team have fixed most of them and 2.5 represents the achievement of that bugfix round. 

What I dislike in ardour's development is this habit of mixing bug fixes and new features in each release. It is a very unstable way to do software development. You do need a process scheme that can give you some sort of control on bug occurences. each new feature introduces a new bug. Ardour's development has shown me that there's no such thing as regression testing or very little, e.g. deleting a track in the 2.4 serie makes ardour crash. This is, in my view, unacceptable when this sort of things worked in prior versions. But on the other hand, we're talking about open source and these things tend to be solved quickly. But newbies can find it hard or tedious to follow up. Personaly, I'd rather cope with a non optimal development scheme but extremely active community than a monolithic software evolution process, centralized to such an extreme that the user is relegated to a simple and dumb consumer role.

Wow, what did I say ? I am OT ... sorry :lol:

Yeah, ardour 2.x does not have MIDI editing capabilities. But rosegarden has both audio and MIDI, although its strength is MIDI (the audio part is rather limited, dixit rosegarden's main author). It has a good plugin support when it comes to soft instruments (VSTi, DSSI). I don't know about ladspa though. Maybe it has ladspa support too but I am not aware of it.

---

### Post by T4_ on 2008-06-12
Hi,

thanks for all your replies, they've been very helpful! I've been running Ubuntu Studio and apart from liking it, the whole default "made to work with audio"-thing seems to help quite a bit!

The application advice will be taken to heart, I'll try everything out :)

---

### Post by dewski on 2008-06-14
Along the same lines as the OP, but I definitely don't have the hardware capabilities to use Ardour effectively.  I know it has a lot that I'd like to go into, but with the laptop I have, I have no idea what I should turn off to get a decent playback (my comp is too slow to run it essentially). 


Does anyone have any ideas on what might be good to just play around with music composition?  I have used Sony's Acid Pro and I loved it, but all I really need is something to put loops together.  This is just a hobby and I'd like to create some basic, basic stuff.  I'm having a hard time finding anything that isn't trying to be professional.

I do have a copy of Ubuntustudio, but because of some problems with soundcard issues on a toshiba laptop I'm wary of trying a new flavor of the OS.

Much love, I appreciate all the help the forum has and will provide.

---

### Post by ad_267 on 2008-06-14
> **dewski said:**
> Along the same lines as the OP, but I definitely don't have the hardware capabilities to use Ardour effectively.  I know it has a lot that I'd like to go into, but with the laptop I have, I have no idea what I should turn off to get a decent playback (my comp is too slow to run it essentially). 


Does anyone have any ideas on what might be good to just play around with music composition?  I have used Sony's Acid Pro and I loved it, but all I really need is something to put loops together.  This is just a hobby and I'd like to create some basic, basic stuff.  I'm having a hard time finding anything that isn't trying to be professional.

I do have a copy of Ubuntustudio, but because of some problems with soundcard issues on a toshiba laptop I'm wary of trying a new flavor of the OS.

Much love, I appreciate all the help the forum has and will provide.

You might want to check out Jokosher: [http://www.jokosher.org/](http://www.jokosher.org/)
and Hydrogen is a good drum machine program: [http://hydrogen-music.org/](http://hydrogen-music.org/)
Also LMMS: [http://lmms.sourceforge.net/](http://lmms.sourceforge.net/)

---

