---
title: "New beans and mature beans - I roast both"
date: 2008-11-10
forum: Testimonials &amp; Experiences
---

### Post by Darrell Lawrence on 2008-11-10
I purchased a Dell XPS M1530 preloaded with Ubuntu 8.04 a little over a month ago. Everything on it works perfectly. Now we can't have that, so I decided to have a little fun :). Dell furnishes the 32-bit version of 8.04, but my Dell has a dual core intel processor capable of running the 64-bit version.

Since I'm studying for Ubuntu Certified Professional, and the coursework is always based on the long term releases, I need to keep 8.04 around for awhile. So I set up a dual boot system with 8.04 and 8.10 both in 64-bit versions. Well 8.04 still runs perfectly, just faster in the 64-bit version and everything in 8.10 works except the webcam. The webcam is a known issue - there are several bug reports about it over on launchpad. 

So, my plan is to keep 8.04 until the next LTS, but always run a dual boot with the regular releases. That way I can have stability, but at the same time report any issues with the newest releases over on launchpad. I figure it's a good way to contribute.

Love Ubuntu, and hope to become a developer in the future. I've attached  screenshots of my old beans (8.04) and my new beans (8.10). I'm roasting both :).

---

### Post by Crafty Kisses on 2008-11-11
Best of luck to you my friend.

---

### Post by Geekkit on 2008-11-11
Right on and good for you! It's interesting with this certification thing ... I was in the book store and saw a certification study guide for Ubuntu today and I was interested in purchasing it (too busy right now though to dive into it unfortunately).

I'll offer my experience/opinion with development in Ubuntu/Linux. First off, no matter what programming language you decide upon and what IDE you decide to go with, they all seem to be quite easy to install (apt-get is your friend :).

If you have programming experience and are completely 'cool' with diving into the deep end, doing C programming in GTK+/GNOME can be incredibly rewarding. Downside is that the GTK+ documentation is not as informative as it could be and so you may spend a lot of time scouring Google for answers (e.g., trying to load an image into memory, manipulate it using GTK/GDK calls is not very well documented). Upside is applications will be a few kilobytes (with no GUI) and only a couple of Megabytes with a GTK+/GNOME GUI (in main memory) - very tight!

If you want to start off easy, Python is a very popular programming language that comes with a supportive VM. Many Ubuntu programmers swear by it and most people will be more then willing to answer Python questions.

Mono (.NET/C# clone in Linux) is another choice although it seems to be problematic and not as mature.

Java. Java support in Linux is VERY mature and comes with the best/fastest/glitch-free (IMO) VM in Linux (better than Python, Ruby, Mono by far). There is Netbeans and Eclipse for development tools - both with literally dozens of tools. Netbeans has a great module that allows you (with great ease I might add) to create J2ME applications (mobile applications).

Ruby. I have no experience with Ruby so I won't say anything on it other than there's support for it in Linux.

Most of these environments offer GUI drag-and-drop IDE support so you'll only have to write logic to tie the GUI together with the model of your application (for the most part).

The programmer people in the programmer forums are quite nice people and are quite helpful as long as you provide specific questions requesting specific answers.

You have your choice of high level tools that will allow you to drag-and-drop and guide you through project creation or you can use the console and use Geany (for example) - whichever suits your needs. It's like what you've been studying: totally configurable. The only downside to doing development in Linux I think is that there are so many options/choices that you may loose yourself for a while just deciding what to use.

Hope this helps.

---

### Post by MrWES on 2008-11-11
What theme is that?

---

### Post by Darrell Lawrence on 2008-11-11
Geekkit,

Thank you for your very informative post. I copied and saved it as a document for future reference. If you're a developer, thanks for your hard work. I'm fairly proficient in C, and you've given me some great insights into other languages and programming in the Gnome environment.

Darrell

---

### Post by Geekkit on 2008-11-11
> **Darrell Lawrence said:**
> Geekkit,

Thank you for your very informative post. I copied and saved it as a document for future reference. If you're a developer, thanks for your hard work. I'm fairly proficient in C, and you've given me some great insights into other languages and programming in the Gnome environment.

Darrell

You're welcome. If you're proficient at C then you should have no problem with GTK+/GNOME. The libraries are all in the repositories - so is the Glade Drag-and-Drop tool (version 2 generates the code for you and version 3 uses the libglade library to dynamically generate it at run time using XML files as a guide).

If you're into graphics, Cairo is now easily integrated into your GTK+/GNOME application development. Cairo is a 2D library that GNOME recently (within the last couple of years) embraced for things such as font rendering, better/cleaner/faster graphics support. OpenGL is also easily integrated into your GTK+/GNOME application. It's all quite a lot of fun.

I do develop but these days mostly in Java and web applications. I don't get enough time to play in GTK+/GNOME and graphics ... at least not as much as I'd like to. :)

---

### Post by Darrell Lawrence on 2008-11-11
> **MrWES said:**
> What theme is that?

MrWES,

The theme I'm using on 8.04 is called GoldandBlack. It's a GTK 2.x theme over at gnome-look.org. Got the wallpaper their as well (it's not part of the theme. The icons are part of extra Gnome icons available in Synaptic.

For 8.10 I got the wallpaper over at gnome-look.org. The theme is the Dust theme which is part of a package called community themes through Synaptic. The icons are part of that extra Gnome icons pack through Synaptic.

Darrell

---

