---
title: "[idea] a web cam layer/api"
date: 2007-10-28
forum: Ubuntu Brainstorm
---

### Post by lingnoi on 2007-10-28
Web cam support is limiting and the programs that support web cams in Ubuntu. I propose a new layer be added between the webcam device layer and application layer which provides the following functionality:

- The ability to use the same web cam device for multiple programs at the same time.
- Greater compatibility with applications that don't support certain web cams because the web cam displays the wrong width or height for that program.
- The ability to feed video data into this layer that can be used as an alternative to web cam data.

The features of this layer could be use in the following use cases:
- A user could use his web cam while talking to multiple users though Amsn, Gyachi, Ekiga, etc
- A user that wanted to show a large family movie could push the movie into the webcam layer and show other users via the programs listed above
- A programmer could quickly implement web cam support in their program by requesting the image size and grabbing the image to display on screen

I made [a blueprint]("https://blueprints.launchpad.net/ubuntu/+spec/webcam-layer"), please feel free to add to it based on the above ideas.

As an avid web cam user I'm dying to know what you all think. :)

---

### Post by 23meg on 2007-10-28
Have you looked into GStreamer? Maybe they're planning to implement this kind of thing, or already have.

As for the blueprint, so far you've only entered a blueprint summary; I assume the actual blueprint is yet to be written, right? And a semantic suggestion: "on top of Ubuntu" isn't really good wording to describe this if you ask me, since it shouldn't be done in Ubuntu and be Ubuntu-specific.

---

### Post by lingnoi on 2007-10-28
The website to fill out the blueprints is quite difficult to understand. I'm not sure how it's suppose to be structured at all. Any pointers would be great, or if you'd like to take what I have done please go ahead.

When I comes to the blueprints I have no idea. :D

---

### Post by 23meg on 2007-10-28
I'll soon post a thread with basic instructions on writing blueprints, among other things. I can also help you with the blueprint to some extent; what you should do first is do research to find out if this kind of work is already being done or planned somewhere. GStreamer would be a good first place to look.

---

### Post by loell on 2007-10-29
hi, I work closely with gyachi project , and the project is moving towards gstreamer webcam API. 

I think ekiga is using another high level API , OTOH amsn is written in tcl so perhaps there is a gstreamer binding for tcl? i'm not sure.

speaking of blueprint, i would also like to file a blueprint on some other package, but lacks the knowledge to do it , did file a launchpad bug but was invalidated :( , hope 23meg will update this thread with the link on how to do it ;)

---

### Post by lingnoi on 2008-02-29
I made an idea on brainstorm here: [http://brainstorm.ubuntu.com/idea/577/](http://brainstorm.ubuntu.com/idea/577/)

---

