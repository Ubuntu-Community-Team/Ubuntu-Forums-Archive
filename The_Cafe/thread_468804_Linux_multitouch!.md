---
title: "Linux multitouch?!"
date: 2007-06-09
forum: The Cafe
---

### Post by dlai on 2007-06-09
Well you have all seen the previous work of Jeff Han, and recently the Microsoft Surface which shows how a multitouch surface can be used to do various tasks. Though Microsoft Surface is not new, they have achieved to bring alot of attention to themselves, though not really being that inventive.
I think we have to show the world that what they have done is nothing in comparison to what our community can develop!
I have started out a small project in order to make this come true. Building on MacSlow's magnificent unfinished (but hopefully finished at some time) lowfat, I have managed to create an interface to lowfat using the output from one of these multitouch tables. Just want to see where this could go! If anyone would be interested in continuing development on this together with me, they are most welcome. Most of the work will probably be in the backend, making it stable, creating support for other inputs than fingers and so on. Anyway if anyone is interested please say so, the code done so far is primarily a proof of concept, and a complete code rewrite will probably be needed, it won't take long though!

Well let's see what happens!

Here is some of the information, just post if you feel something is missing!

[dlai.jafu.dk]("http://dlai.jafu.dk")

---

### Post by Feba on 2007-06-10
The problem is the hardware. Most people just can't afford it. Other than that, this could actually infringe on MS patents if you aren't careful. I don't see how this is much more complex than getting the program to recognize and use two mouse inputs at once though.

---

### Post by dlai on 2007-06-10
Well ok, this is really cheap to create, so I don't believe hardware is the biggest problem. I'm not afraid that this will infringe any software patents, I'm in europe anyway so that should not matter. The hardware side; I don't know if Microsoft filed any patents on these technologies, anyway these technologies has been around quite some time before they showed off Microsoft Surface. By the way, you are welcome to try and implement it with two mice, I am sure it could help development. What is fantastic about this interface, is the fact that it is tangible in another way than just two mice, and can support alot of other input forms than just two x and y's. For example pattern recognition, like the guys with the Reactable have done.

---

### Post by Druke on 2007-06-11
This all goes down to the x server project. basically one needs to understand how the mouse devices is configured and howto setup another one.

just a little searching about and i found this -> [http://wearables.unisa.edu.au/mpx/?q=taxonomy/term/4](http://wearables.unisa.edu.au/mpx/?q=taxonomy/term/4)

and a vid on it -> [http://www.youtube.com/watch?v=0MUOn_nJmRA](http://www.youtube.com/watch?v=0MUOn_nJmRA)

we should looka t what it takes and how to get it into ubuntu in one way or another, this si truly a new step that is bound to happen in computing

edit:

a better video is [http://www.youtube.com/watch?v=AryCQ8Ybp6A](http://www.youtube.com/watch?v=AryCQ8Ybp6A)

also this only supports up to 18 inputs
live cd is [http://wearables.unisa.edu.au/mpx/?q=downloads](http://wearables.unisa.edu.au/mpx/?q=downloads), at the bottom, its a live dapper!

---

### Post by dlai on 2007-06-11
well, I have looked into the mpx project as well, and I think you are right that making a multitouch table a input device in the xserver would be desirable. But actually the biggest problem is building applications which are ready to handle several inputs, and use them constructively, or else you will just be using all your inputs doing the excact same functions as you usually do. A typical example could be resizing photos. That would be much more logical using two fingers than a one input solution. With multiple inputs there is a possibility to use more gestures, like for example rotating or resizing with two inputs.

---

### Post by dlai on 2007-06-11
and actually i just saw that the author of mpx don't think it is easy to map the multitouch to the mpx (unfortunately), It is actually in the frontpage of the mpx with the title "MS Surface"

---

### Post by Druke on 2007-06-11
so X is where it starts and you have to work your way down
.. so gnome/kde projects would have to create plug-ins and then application level things would need it, though i don't see a plug-in for gimp being that hard once gtk supports it

---

### Post by dlai on 2007-06-11
so yes I guess multiple mice represented as "fingers" would be the optimal solution? Made as an X driver... That might a bit above my skill level, but I will try and look into it

---

### Post by Tux Aubrey on 2007-06-11
dlai, I hope you are not just teasing us here.  I want one of these (full wall multitouch) so bad I would PAY for it (well, I'd actually get work to pay for it, but I would spend a lot of my valuable time writing a business case!).  I want it to work with ARCGis and Google earth and gimp and anything else I can think of!

You know, if [Jeff Han's flash video]("http://www.perceptivepixel.com/") had a shopping cart icon beside it, I'd click,

---

### Post by Druke on 2007-06-11
MPX is trying to allow multiple users which is good, but we're wanting something like surface, if everyone's in the same mindset as me. MPX is a start for the multiouch concept, by altering the x server to support it we can already design software that takes full use of the new features, problem is we now need a touch pad to support this

---

### Post by dlai on 2007-06-11
No, I'm not teasing! But I am at a very early alpha stage with this project (mostly proof of concept). Furthermore the construction of the table itself is very dependent on how well these things work. I have build two myself, one small at home (almost portable, no projector), and a bigger one at university (projector, all the bells and whistles). The work I have done is exclusively the input, MacSlow is the great man who made the lowfat pictures and document viewing platform .

---

### Post by dlai on 2007-06-11
Yes I think it would be nice to have the MPX modified to take the input from the multitouch devices!

---

### Post by Druke on 2007-06-11
think you could post more info on your project? I'm very interested.

---

### Post by dlai on 2007-06-11
Well, I have posted some info, code and video at [http://dlai.jafu.dk]("http://dlai.jafu.dk") if you want more, you are very welcome to ask.

---

### Post by Druke on 2007-06-11
ah there it is, it wasn't a hyperlink in your original and .dk soesn't stick as a web extension, sorry for looking like an idiot :p

---

### Post by dlai on 2007-06-11
All fine! :)

---

### Post by Druke on 2007-06-11
so it seems there are multiple ways to go about this, the one that your project and surface use is to actuallu look at whats on the surface. But it would seem more practical for a user to have one of those multitouch pads, and using that to do everything. 

maybe i missed it in your report but whats the addvantage to the camera and ir stuff over just the simple pad?

---

### Post by dlai on 2007-06-11
Well ok. It has not come to my attention that it is actually possible to buy a multitouch "pad". I don't know if the technology is around. Furthermore it is a very cheap way to produce a multitouch tabletop. Anyway creating a multiple input platform, but just with different backends maybe would be the best way to do this.

---

### Post by Druke on 2007-06-11
[http://fingerworks.com/](http://fingerworks.com/) is what i think we someone starts talking multitouch

like you said the backend doesn't matter, what matters is the platform, but i'm not sure where to go from there? would it be mpx?

---

### Post by dlai on 2007-06-11
Ok that is cool, but I think the feeling of having the screen right beneath your fingers is whole other experience! ;)

---

### Post by Druke on 2007-06-11
Ah ok now i understand where you are coming from, and completely agree. how small could you get one of these display boxes (I'm imagining my desk in 20 years).

also has anyone tried [http://ubuntuforums.org/showthread.php?t=470274](http://ubuntuforums.org/showthread.php?t=470274)

if thats the case then regular touch pads can be used as multitouch, i was actually wondering what it would take to make a standard touch pad accept multiple inputs and it would make sence that it all cmes down to the software

Even though this isn't the tabletop set up, it is till Linux featuring multi-touch technology and the tabletop is one application of said technology.

---

### Post by dlai on 2007-06-11
It actually depends a lot on how far away from the surface the camera and the video projector have to be in order to utilise the whole surface, i posted some photos on [http://dlai.jafu.dk]("http://dlai.jafu.dk") of the mini-table i built at home plus a demo of the video we did for the project. Maybe you can get a better idea then.

---

### Post by dlai on 2007-06-11
I actually did try to use the two input synaptics thing, but for scrolling instead (like on the mac), but it seemed to have some issues where it grabbed the mouse or something, so I could not click on anything, before I scrolled a little more up and down. Furthermore when I used the scroll it would scroll all the way to the end of the page, or to the top of the page. In short it was not really usable, but maybe i misconfigured it.

---

### Post by aktiwers on 2007-06-11
Very Interesting project you have there Dlai :)

---

### Post by dlai on 2007-06-11
Thanks! It is mostly MacSlow's work though!

---

### Post by Jay_Bee on 2007-12-09
has anyone tried touchlib from [nuigroup.com]("http://www.nuigroup.com")?
[http://youtube.com/watch?v=pY8hXu59fiE](http://youtube.com/watch?v=pY8hXu59fiE)
It is open source, and it can be installed on Ubuntu [http://nuigroup.com/wiki/Installing_Touchlib_on_Ubuntu/](http://nuigroup.com/wiki/Installing_Touchlib_on_Ubuntu/)

---

### Post by TearDownAllSigns on 2007-12-14
Glad I found this thread, building a multi touch display has been my dream since that first Jeff Han video. Thanks Jay_Bee on that touchlib on Ubuntu link, will have to look into that. 

As far as a touch screen device, that is what looks to be getting cheaper lately in the DIY area. My first trials will be to do something using a Wiimote, IR LEDs and my LCD screen similar to Johnny Chun Lee's Wii Whiteboard
[URL="http://www.youtube.com/watch?v=5s5EvhHy7eQ"]
http://www.youtube.com/watch?v=5s5EvhHy7eQ[/URL]

His [site]("http://www.cs.cmu.edu/~johnny/projects/wii/") has the code he used, but it is in C# and I am rather clueless as to how to get it running. Got mono installed but not sure where to go from there or if it will be too M$ dependent to run in ubuntu. 

Also touch screen using plexi-glass, IR LEDs, web cam, and a projector:
[http://www.instructables.com/id/Interactive-Multitouch-Display/]("http://www.instructables.com/id/Interactive-Multitouch-Display/")

In my opinion, this is one of those areas that the Linux/Free Software community needs to jump into and fast. No OS is better suited to a complete multi-touch overhall. MPX or a X.org upgrade to support multi-touch inputs for multiple users will need to be first. Then a windows manager or desktop environment with some tweaks for ease of use with touch (different scroll and sizing controls, gestures tied to app actions etc). Finally application support will complete the scene.  

No one could do it faster, cleaner, and better integrated than the free software community. I would just hate to see this technology left to proprietary software on proprietary devices, who knows how long it would take to have a usable home version that worked with your own applications. 

Imagine the option facing people when it will be between a sweet smooth afforable multi touch Linux based system or... Windows Vista. Or better yet a $10,000 Surface table. This could also open up a great small buisness market of creating multitouch displays with off the shelf tech backed by free software.  Plus with the intuitive nature of the interface, having an open and free devlopement process will be paramont for fostering UI inovations.

I'll be helping my nephew build an ubuntu based touchscreen device for his high school science fair next year, and I'll be sure that any progress made will be well shared.

---

### Post by aktiwers on 2008-01-21
Have you guys seen this?
[http://www.gearlog.com/2007/12/incredible_wiimote_hack_create.php](http://www.gearlog.com/2007/12/incredible_wiimote_hack_create.php)

Pretty cool

---

### Post by sodasound on 2008-04-30
If we're really interested in tangible interfaces, we should look outside of multitouch. the ReacTable website has some links and open-source ware and other resources which widen the field. I've just discovered this technology via my building neighbors, who are building TangiTables out of cardboard boxes, sheets of glass and webcams; and using Fiducials and pennies to control drum-sequencers and synthesiser clients. Graphics and Music are the attractor apps which lead us to ideas which are older and broader in scope. 

Tangible interfaces could be as simple as normal hand-held objects which are wirelessly addressable and give status feedback and natural gestural control. Ubuntu should be behind all of this, because it is in the ballpark of the Ubuntu philosophy. Think PLC's and microcontrollers, light and sound generators, sensors, RFID's; think autonomous calm-technology objects, which can communicate with larger systems which facilitate or control their function. Then imagine a software framework which a novice user can use to customise the behavior of these things.

I have a few concrete examples in mind, but that stuff is for when I get out of the basement. My blog [http://morleyblog.wordpress.com](http://morleyblog.wordpress.com) will soon have a new category exploring all of this. Meanwhile, here are a few links:

[http://abletable.livejournal.com/](http://abletable.livejournal.com/)
[http://www.ehornecker.de/Tangibles.html](http://www.ehornecker.de/Tangibles.html)
[http://guir.berkeley.edu/projects/papier-mache/](http://guir.berkeley.edu/projects/papier-mache/)
[http://www.electrotap.com/](http://www.electrotap.com/)
[http://www.youtube.com/watch?v=4PSBwiBUgGM](http://www.youtube.com/watch?v=4PSBwiBUgGM)
[http://www.naturalinteraction.org/images/whitepaper.pdf](http://www.naturalinteraction.org/images/whitepaper.pdf)

---

### Post by userid on 2009-06-20
[http://randomtruth.110mb.com/blog/](http://randomtruth.110mb.com/blog/)

Software-based multi-touch on linux using synaptics touchpads

---

### Post by Truefire on 2009-10-13
Hey guys, sorry for *bumping* a dead thread, but multi-touch just got a whole lot cheaper, and it may replace mice. See here:

[http://www.wacom.com/bamboo/bamboo_touch.php](http://www.wacom.com/bamboo/bamboo_touch.php)

---

### Post by markbuntu on 2009-10-13
Well, multi pointer x has finally made its way into the just released X server, too late for karmic but we will see it in the 10.4 LTS and by then it will probably have multitouch.

---

### Post by Truefire on 2009-10-13
> **markbuntu said:**
> Well, multi pointer x has finally made its way into the just released X server, too late for karmic but we will see it in the 10.4 LTS and by then it will probably have multitouch.

Thanks for the update, dude. Can't wait to see, but I'm definitely buying that multi-touch pad in the meantime.

---

### Post by AlexenderReez on 2009-10-23
i'm looking to enhance and perhaps market it in my own country..

anybody from malaysia (and neighbor )please do pm me

---

### Post by skewty on 2010-01-03
This surely must be a priority for Mark Shuttleworth and the Ubuntu team.  With Android OS invading Ubuntu territory and the recent shift to Windows 7 in the netbook world (especially tablet netbooks), it is a must.

The way we interface with our electronics is changing / shrinking and if Canonical keeps waiting for upstream to implement new technologies and software developers to write innovative new software to include they will always be trailing behind.

I realize Canonical is not focused on application development.  I realize I am not offering and solutions to the above listed problems / issues.

---

### Post by arasbm on 2010-04-03
Hi, Sorry for bumping in the old thread. 
I am really excited about multi touch support in 10.4. I am planning to build a multi touch table based on FTIR technology, which by the way many people have successfully build them, and they are surprisingly cheep. The process of building one is clean and straight forward. I want to run Ubuntu on mine.
Some of the initial links on this thread are no longer working, I was wondering how can I follow the multi-touch development in Ubuntu so at least I can help with some testing.

---

### Post by Truefire on 2010-04-03
Here ya go:

[https://launchpad.net/~multi-touch-dev](https://launchpad.net/~multi-touch-dev)

---

