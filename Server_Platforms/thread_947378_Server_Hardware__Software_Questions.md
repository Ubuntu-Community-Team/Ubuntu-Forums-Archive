---
title: "Server Hardware / Software Questions"
date: 2008-10-14
forum: Server Platforms
---

### Post by jcr1 on 2008-10-14
Hi all,

I am thinking of trying out the Server Edition on a pc that I have been using as a home server which currently just has Hardy desktop on it.

There are a few things that I don't understand when using the server edition.

1) how would I set up a wireless card? On a desktop install, it comes up as a restricted driver i have to enable. What is the equivilent on the command line?

2) what about graphics cards? Is there any requirement to get it working right if it is a headless server? There is a card in there at the mo I have been having problems getting to work correctly, but if it becomes headless will it be irrelevant?

3) Running programs...that is to say, running a program on the server but thru a remote computer via ssh. I know its possible but what I don't understand is where the program runs? Is it on the server and all you are seeing on the remote client is an image of the program running? What about the graphical capabilities of running a program this way? Linked to my question above, if the server is powerful enough to run HD video, does the graphics card on the server need to be working to display it via ssh on a remote screen (as it isn't going via the GFX card)??

4) Will graphical programs work on the remote client even though there is no grpachical interface installed on the server? e.g. can I launch VLC and watch a video on my laptop that is running on the server? Which computer needs the ability to play the video...the laptop or the server? 

All along the same lines...any demanding program, if run via ssh on the laptop, where is the processing done and does the gfx card need to be working or not? Is the laptop merely a 'viewer'?

5) Any hardware that requires restricted drivers to be enabled... how would I know? on a desktop it pops up and tells you... or you can go into the menu and check... how do you 'check' on the server?

There must be more questions but i can't think right now.

Thanks in advance!

---

### Post by lykwydchykyn on 2008-10-14
> **jcr1 said:**
> Hi all,

I am thinking of trying out the Server Edition on a pc that I have been using as a home server which currently just has Hardy desktop on it.

It's worth pointing out that you don't really have to reinstall "server edition" on it, you could just add and remove the packages necessary to convert your install to a server.  Unless you just want the experience...

> 
There are a few things that I don't understand when using the server edition.

1) how would I set up a wireless card? On a desktop install, it comes up as a restricted driver i have to enable. What is the equivilent on the command line?

Honestly not sure about that, what model is the card?

> 
2) what about graphics cards? Is there any requirement to get it working right if it is a headless server? There is a card in there at the mo I have been having problems getting to work correctly, but if it becomes headless will it be irrelevant?

If it's headless, it doesn't matter.  As long as it will show console output for setup and in case you have problems with it's networking, you're good. 
> 
3) Running programs...that is to say, running a program on the server but thru a remote computer via ssh. I know its possible but what I don't understand is where the program runs? Is it on the server and all you are seeing on the remote client is an image of the program running? What about the graphical capabilities of running a program this way? Linked to my question above, if the server is powerful enough to run HD video, does the graphics card on the server need to be working to display it via ssh on a remote screen (as it isn't going via the GFX card)??

It is running on the server.  It's kind of hard to explain, but the [wikipedia article on X windows](http://en.wikipedia.org/wiki/X_Window_System) does a decent job.  Just read the "design" section.  What you're doing is attaching a remote X11 client to your local X11 server.

Not sure about the HD video question, though you have to keep network bandwidth in mind as a limiting factor.  Especially if this thing is going over a wireless.  But the server's graphics card shouldn't matter.
> 
4) Will graphical programs work on the remote client even though there is no grpachical interface installed on the server? e.g. can I launch VLC and watch a video on my laptop that is running on the server? Which computer needs the ability to play the video...the laptop or the server? 

I'm not entirely sure that you can do it without any graphics card, but the capabilities of the server's card are irrelevant.  To answer the second question, the server would need VLC and relevant codecs installed.  The laptop would not.
> 
All along the same lines...any demanding program, if run via ssh on the laptop, where is the processing done and does the gfx card need to be working or not? Is the laptop merely a 'viewer'?

Yes, the "normal" processing demands are on the server, but the graphics processing is done by the laptop.
> 
5) Any hardware that requires restricted drivers to be enabled... how would I know? on a desktop it pops up and tells you... or you can go into the menu and check... how do you 'check' on the server?

You'd know because they wouldn't be working, at least not if  you uninstalled the restricted-modules package for your kernel.

> 
There must be more questions but i can't think right now.

Thanks in advance!

We'll be here to attempt an answer.

---

