---
title: "So I'm planning to start this open source project around VNC remote desktop"
date: 2010-03-08
forum: The Cafe
---

### Post by diablo75 on 2010-03-08
I'm not a programmer but a good buddy of mine is.  We're kicking an idea around about coming up with a little utility that anybody can customize and use to establish reverse-VNC sessions with people who need help with their computers.  It's not a new idea.  There's a way to do this with UltraVNC right now, but it looks like the way you do this with that program hasn't been modified in over a decade.  The utility looks dated, and the VNC protocol used seems to be incompatible with newer VNC viewers... or at least that the experience I had.  But I basically want to tackle the concept and try to bring it back to life so freelance techs out there can get their own remote desktop software that's easy to customize and call their own while keeping it all open-source.

We've had no problem creating little test projects that allow the user/client who needs help with their computer establish a VNC session with someone else with nothing more than a single-click.  The emphasis has always been to make things streamlined and simple for the non-tech users.  With the help of DynDNS, it's a snap to do something like this.  So the primary feature that this program will do is basically connect users to a pre-specified listening viewer using a DynDNS hostname the tech configures into this app before having the client download and install it on their machine.

Beyond that the only bells and whistles that might be integrated into this might be encryption... but I don't know the best way to go about doing that and might not really worry about that so much as perhaps other things first.

The creation/customization process that I have in mind for this app would be sort of like what you have to do with UltraVNC right now, but instead of downloading a zip file that contains a few files for you to exchange out or modify and send back to their server, we'd instead do all of the customization via a website.  You'd go to create your own quick-connect server app by browsing to a webpage and answering a few simple questions like, "What will your viewer's hostname/IP address be?"  "What is the name of your company?"  "What do you want the top title bar to say?"  "Here are a couple skins/themes you can pick from to customize the look of the program; feel free to upload your own based on this template you can download."  And so on..

This is where I'd like to find some feedback to see what other things someone might want to be able to customize during the creation process of an app like this.  So if you have suggestions, I'm all ears.

After all the questions are answered and you've basically built up your own customized VNC session launcher, you're offered a download link for a program (and it's appropriate source code) to post on your own website for customers to download and use to get in touch with you.  And, to an extent, you can say that it's your own software that you created when it's really just like an open-source template that you modified to serve your purposes.

So... that's about all I've really thought into this idea.  I want to start a project that will provide a tool to freelance techs out there who would like to incorporate remote assistance into their services.  I don't think it would be too difficult to do... but then again, I've never tried to do something like this before (develop something, open-source it, and then see what happens).  And I would imagine that once it caught the attention of a few other programmers who are smart enough to improve the source code could perhaps contribute little updates to the software from time to time...  That'd be pretty cool.

What do you think?

---

### Post by Ralob on 2010-03-08
Give this a look- [http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

I know a lot of people have given the program positive reviews. So maybe you can use it as a starting point.

---

### Post by castrojo on 2010-03-08
> **diablo75 said:**
> We've had no problem creating little test projects that allow the user/client who needs help with their computer establish a VNC session with someone else with nothing more than a single-click.  The emphasis has always been to make things streamlined and simple for the non-tech users.

Empathy's shipped with this ootb starting with Karmic. You can just right click on a person's contact and share a desktop.

EDIT: I didn't mean to come across like "too late your idea is done", just that if you'd like to improve the functionality on top of what's already built that you don't have to start from scratch!

---

### Post by diablo75 on 2010-03-08
> **whiprush said:**
> Empathy's shipped with this ootb starting with Karmic. You can just right click on a person's contact and share a desktop.

EDIT: I didn't mean to come across like "too late your idea is done", just that if you'd like to improve the functionality on top of what's already built that you don't have to start from scratch!

Not at all.  But the thing I forgot to mention is that the first version of this software will be for Windows, not Linux.  My friend has never programed for Linux so we were going to put that in the backseat on the priorities list.  It's easy enough (for now) to just have the user create a shortcut executing x11vnc in a terminal and leave it on their desktop for future use.

---

### Post by diablo75 on 2010-03-08
> **Ralob said:**
> Give this a look- [http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

I know a lot of people have given the program positive reviews. So maybe you can use it as a starting point.

This would make for a great start on the Linux side of things (since we're really not experienced with programming for Linux yet; just Windows for the most part).

---

