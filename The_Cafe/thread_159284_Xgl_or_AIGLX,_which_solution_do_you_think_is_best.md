---
title: "Xgl or AIGLX, which solution do you think is best?"
date: 2006-04-12
forum: The Cafe
---

### Post by jarocooke on 2006-04-12
I have just been reading my copy of Linux Format and it had a couple of articles which talked about Xgl on it.  

They also mentioned AIGLX as an alternative (a competing one) and I was wondering which solution Ubuntu users and developers thought was best?


Personally, I think Xgl takes it by a mile, though I have heard that AIGLX is a much more incremental step up (rather than a leap), for me at the moment Xgl seems almost ready fly.  Granted it is running nested in an ordinary xerver, but that doesn't change the fact that it is stable enough to use, fast, I can watch movies, and works with a quite large range of graphics cards.

So anyway, enough of what I think, what do you think AIGLX or Xgl, which is the best option?

---

### Post by mstlyevil on 2006-04-12
As of right now XGL simply because it is in a much more advanced state of development and both ATI and Nvidia supports it. I could change my mind when Nvidia adds support for AIGLX.

---

### Post by ComplexNumber on 2006-04-12
apparently, AIGLX is more for those with nvidia cards whereas xgl is largely graphic card independent. i seem to remember nVidia mentioning something about they are much more in favour of AIGXL. AIGLX is more of a plugin to xorg whereas XGL is more integrated.

---

### Post by Stormy Eyes on 2006-04-12
I'm not familiar with AIGLX, since I don't use (and won't touch) Fedora. I've used Xgl for the last three weeks, however, and am pleased with it thus far.

---

### Post by mstlyevil on 2006-04-12
[QUOTE=ComplexNumber]apparently, AIGLX is more for those with nvidia cards whereas xgl is largely graphic card independent. i seem to remember nVidia mentioning something about they are much more in favour of AIGXL. AIGLX is more of a plugin to xorg whereas XGL is more integrated.[/QUOTE]

Nvidia has failed to supply that support thus far. Maybe they will include it in the next version of the drivers. Intel chipsets work better with AIGLX.

---

### Post by ComplexNumber on 2006-04-12
[quote=mstlyevil]Nvidia has failed to supply that support thus far. Maybe they will include it in the next version of the drivers. Intel chipsets work better with AIGLX.[/quote]
thats very true - they have failed to thus far. apparently, they're waiting until AIGXL reaches a certain level of completeness.

---

### Post by Lovechild on 2006-04-12
I'm sorry, you are factually incorrect and uninformed on the topic.

It's not a competition, both solutions work together towards a solution that will work in all cases.

AIGLX is work that we need even if the unlikely scenerio that XGL works 100%, and it's a much more evolutionary approach to the problem. Now AIGLX is already in the X tree and it should be ready for 7.1.

---

### Post by poofyhairguy on 2006-04-12
[QUOTE=jarocooke]
They also mentioned AIGLX as an alternative (a competing one) and I was wondering which solution Ubuntu users and developers thought was best?

So anyway, enough of what I think, what do you think AIGLX or Xgl, which is the best option?[/QUOTE]

Its not really a competition. I picked the third option, because of this fact.

XGL allows for development on an OpenGL Linux desktop to happen NOW. Not months or years later. Now. So that means that work on OpenGL effects can go on and we can figure out what is needed to be done to have a non render accerated composited desktop.

But make no mistake. XGL is a "bandaid" solution. Or as I have called it- a kludge. Don't get me wrong, its a great kludge. But its not something that is a final solution.

AIGLX is a little closer to a final solution, and some would say it is one. I personally don't believe that it will be the "way that a stable OpenGL composited desktop gets shipped by default in the major Linux distros" but thats because I don't believe in ATI. I don't see them supporting the extensions needed for AIGLX (and the hard work needed to get composite and Opengl to work well together) for a long time in their closed driver. I don't see the switch being left on. One advantage of XGL is it gets ATI's support without asking- any long term solution that does not work on modern ATI hardware will end up as a dead end. But AIGLX is more of a solution than XGL (as its not a kludge) and will lead to the final solution.

What is the final solution? Some future Xserver that incorporates the advantages of both approaches. Some call this Xegl, but what has been done on a Xegl server up until this point might not be used. Instead I'll just call it what it is- lots of future hard work. But each approach (XGL and AIGLX) brings something to the table not there otherwise.

Personally I LOVE XGL now to the point I defend it (in often a stupid manor). Why? Because I'm sick of waiting for the frameworks and whatever to settle before I can have an OpenGL composited desktop. I wanted such a desktop two years ago when OSX showed it was possible. XGL allows for development of the stuff I actually care about (the compositors and effects) to go on while the boring stuff that has just been in my way until this point (the framework) keeps getting worked on. But I am not loyal to XGL till its death. Maybe Compiz, but not XGL. In fact, when the extensions that AIGLX needs gets into the Nvidia driver I will probably switch to get Twinview support back.

The real questions are:

What do you think are best- OpenGL compositors or Render Compositors? For me the answer is obvious.

What solution do you think is best- developing the OpenGl effects in a seperate window manager (Compiz) or working them into a popular/already used window manager (Metacity)? Since I HATE the Metacity philosophy more than anything else in Linuxland I am glad that Compiz gives me this freedom from it, but some disagree.

These sorts of things are the real questions. XGL vs. AIGLX don't compete directly, they help each other a lot and neither seems to be the perfect final solution.

So just use which one works best for your hardware and get to what really matters THE EFFECTS!

---

### Post by poofyhairguy on 2006-04-12
[QUOTE=poofyhairguy]I personally don't believe that it will be the "way that a stable OpenGL composited desktop gets shipped by default in the major Linux distros" but thats because I don't believe in ATI. I don't see them supporting the extensions needed for AIGLX (and the hard work needed to get composite and Opengl to work well together) for a long time in their closed driver. One advantage of XGL is it gets ATI's support without asking- any long term solution that does not work on modern ATI hardware will end up as a dead end. [/QUOTE]

I quoted myself here to clarify something- what I think the final solution will look like. I want this horrible speculation to be seperated from my other post, as this post is trash. Please don't read it if you are offended by stupidity.

The problem with XGL is that its a hack. Its kinda clear to see its limitations. 

Yet AIGLX has a problem that is VERY hard to see- its optional. Fans of it like that you can "flip a gconf switch" to get effects. In some ways this is great because it allows for those who don't have supported hardware to just miss out, while those with can easily get involved in the fun. I see this as a major weekness though.

ATI sucks. Really bad. Their newest line of cards has been out for a VERY long while with no Linux support what so ever. Up until now they have avoided supporting many major "optional" features of the Xserver like the composite extension. I see them as the problem with the optional AIGLX solution- the will decide FOR THEIR CUSTOMERS that it is a switch that does not need to be turned on. I can pretty much promise this will be the case.

Here is where I agree with Jon Smirl- I think the final solution must break the Xserver. It must draw a line in the sand. It cannot be optional. Either you support this future Xserver, or you can't claim to support Linux. ATI- either you work 100% with a future AIGLX/XGL/Xegl or nothing will display in the screen at all. I don't see anything that is optional working in the long run.

 Of course this will take a while- this cannot happen until every open source driver is ready for the switch. That could take some time. But I can see a future where every driver works with this new age framework except the closed source ATI one (kinda like the situation in 2006 with render acceration) and the community is forced to break compatibility with the old Xserver to force ATI to play ball...

I hate freaking ATI. I will never buy another ATI product again. If all graphics cards were Nvidia and Intel, we could just all switch to AIGLX next year and have a stable composited desktop by default before Vista has 5% market penetration. But because of ATI, I see a future where it might be some time before all the effects are turned on in the same way they are turned on in OSX. 

This is kinda fine with me, as I bought a Nvidia card just to avoid this problem.  Yep- I bought a 6600 GT just for Linux eye candy. XGL and Compiz (more like Compiz's water pluggin) has made this purchase be worth at least four times what I paid for it. I recommend this to all people who have desktops and want this stuff. For laptops, I recommend getting one with an Intel card over an ATI card even if in Windowsland the ATI card is better. That way you can use one of the two solutions and have a modern desktop today......

---

### Post by jarocooke on 2006-04-12
There are some really interesting pieces of information on this thread!!!  I'm learning a lot.

However I don't want people to think that I am trying to create a competition where none exists.  There are however two approaches that could be taken, we could incrementally change the existing xserver or we could go for a big leap towards where we all want to be eventually, a desktop rendered out of OpenGL primitives.

Now you'd think that the big jump would be the most buggy and difficult to use solution wouldn't you.  To be honest I wouldn't know, because at the moment my well supported Nvidia card is a complete no go for AIGLX, which means I am not very happy with AIGLX to say the least.  The day that Open Source software relies on other parties implementing something that doesn't already exist is the day that nothing happens with open source.  So I think we might as well work on stabilising the solution that appears to be closest to fully usable at the moment.

At least that is my feeling, but obviously I think that there will always, as is the nature of open source, be cross over between the two code bases.

One thing's for sure the effects are what matters and I have them now and I find them really quite stable and usable, considering.:cool:

---

### Post by ComplexNumber on 2006-04-12
it seems that xgl is the best solution for the here and now because its just a hacked xorg. aiglx is the best solution for the future. maybe.

---

### Post by Lovechild on 2006-04-12
[QUOTE=ComplexNumber]it seems that xgl is the best solution for the here and now because its just a hacked xorg. aiglx is the best solution for the future. maybe.[/QUOTE]

I believe that the underlying solution be that AIGLX, XGL or XEGL is indifferent to the end user - what the user cares about is the effects, smooth windows and that is done by the compositing manager and only relies on X primitives (which is why Compiz works with AIGLX and XGL).

---

### Post by mrgnash on 2006-04-12
Neither of them work for me, so meh.

---

### Post by poofyhairguy on 2006-04-13
[QUOTE=jarocooke]
One thing's for sure the effects are what matters and I have them now and I find them really quite stable and usable, considering.:cool:[/QUOTE]

As I have been saying for a while: the window manager matters more.

---

### Post by helpme on 2006-04-13
[QUOTE=Lovechild]
It's not a competition, both solutions work together towards a solution that will work in all cases.

AIGLX is work that we need even if the unlikely scenerio that XGL works 100%, and it's a much more evolutionary approach to the problem. [/QUOTE]
I'm sorry, I'm probably simply uninformed, but I was under the impression that both project do implement the same thing, that is accelerated indirect rendering. So how does XGL need what AIGLX is doing and vice versa?

[QUOTE=poofyhairyguy]I personally don't believe that it will be the "way that a stable OpenGL composited desktop gets shipped by default in the major Linux distros" but thats because I don't believe in ATI. I don't see them supporting the extensions needed for AIGLX (and the hard work needed to get composite and Opengl to work well together) for a long time in their closed driver. I don't see the switch being left on. One advantage of XGL is it gets ATI's support without asking- any long term solution that does not work on modern ATI hardware will end up as a dead end.[/QUOTE]
Again, I'm probably only uninformed, but don't AIGLS and XGL rely on the very same extension? And isn't the only difference right now that XGL works with doing some of the things not yet implemented in the driver with software, that is mesa?
And if that's the case, shouldn't it be possible for AIGLX to work the same way if needed?

---

### Post by poofyhairguy on 2006-04-13
[QUOTE=helpme] And isn't the only difference right now that XGL works with doing some of the things not yet implemented in the driver with software, that is mesa?
And if that's the case, shouldn't it be possible for AIGLX to work the same way if needed?[/QUOTE]

My (bad) point was that I don't see ATI rolling out a driver to support that extension for a while. XGL allows for ATI users to get around that issue, AIGLX doesn't.

---

### Post by Cybercool on 2006-04-22
Well all the stories are very nice and all.
But one thing is for sure,

If there isn't going to be some serius action soon. vista will take the lead and wont give it away.
Not because it is so good, but because it's there!!

The problem is, every body is working on something.
And in the end they almost work on the same thing openGL rendering desktop.

Linux needs a standart voor all brands of grapicscards and all kind of renderings software.
Then ATI, NVIDIA, INTEL and lot's of more brands can focus on one system.

Of corse ATI isn't going to make all those drivers, why should day.
Nobody know with system will be used at the end.

And then ATI and other brands spended al that money for nothing on systems that aren't being used.

But making a standart in linux is a problem, it's not a big organisation.
Everybody thinks he know, and is doing it!!

I hope that everybody is letting NOVELL do what they do, and wait for the XGL to be stable and make drivers for that.
Than but maybe than linux has a change of winning more market in desktop computers!!

---

### Post by fettuohi on 2007-06-19
I wonder what people think now about XGL vs. AIGLX especially when it comes to ATI cards?

Regards

André

---

### Post by forrestcupp on 2007-06-19
Yeah, I couldn't believe what people were saying until I finally realized that this thread is over a year old.  Of course  they would say that back then when aiglx wasn't really ready.  

Now I don't think there is any doubt that aiglx is better.  The only reason people even use xgl is because they have to.  Why else use xgl when aiglx is built into xorg?

---

### Post by FuturePilot on 2007-06-19
Well since the ATI proprietary driver doesn't support the composite extension required to run Beryl or Compiz with AIGLX you almost have to use XGL. Or you could use the open source "ati" driver and run compositing with AIGLX, which a lot of people have had success with. AIGLX is much better than XGL though.

---

### Post by starcraft.man on 2007-06-19
Talk about thread necromancy... over a year.

Anyway, I use and like AIGLX. It works well and I've never had any problems with it. I might try xgl just to see the difference when I get my new computer. I'm probably saying with what I got though.

---

### Post by forrestcupp on 2007-06-19
> **starcraft.man said:**
> Talk about thread necromancy... over a year.

Anyway, I use and like AIGLX. It works well and I've never had any problems with it. I might try xgl just to see the difference when I get my new computer. I'm probably saying with what I got though.

Please don't.  The way things have involved, xgl has become something that you should only use if you have to.   I encourage you to study it out more deeply before you actually do it.  Xgl can be a nightmare.

---

### Post by starcraft.man on 2007-06-19
> **forrestcupp said:**
> Please don't.  The way things have involved, xgl has become something that you should only use if you have to.   I encourage you to study it out more deeply before you actually do it.  Xgl can be a nightmare.

No worries, its more of an experiment. I like to try lots of things since moving to Linux :D. Anyway, I will be imaging my drive before trying it, so I can always restore it if I mess up bad (I've done that enough times when "experimenting" :p) and be up and running in 10 minutes. I love imaging, I just wish I started doing it sooner...

---

### Post by FuturePilot on 2007-06-19
XGL kills video playback. It adds all kinds of horizontal breakages and artifacts. Ugghh it's a mess.

---

### Post by fettuohi on 2007-06-19
> **starcraft.man said:**
> No worries, its more of an experiment. I like to try lots of things since moving to Linux :D. Anyway, I will be imaging my drive before trying it, so I can always restore it if I mess up bad (I've done that enough times when "experimenting" :p) and be up and running in 10 minutes. I love imaging, I just wish I started doing it sooner...

How do you do that under Linux? I mean imaging a drive?

Regards

André

---

### Post by starcraft.man on 2007-06-19
> **fettuohi said:**
> How do you do that under Linux? I mean imaging a drive?

Regards

André

Me particularly? I use Acronis True Image. Had the product for a long while before I had Linux (it costs money). I've kept using it mostly because I can't be bothered to change the backups I have to a new format (would mean reimaging them all). Oh and the reason I can still use Acronis even though its a windows product is cuz I work exclusively with it off the live CD I made and it has excellent support for all file systems used by win and linux. Even though they are paid, they care a deal about their product measuring up.

Partimage seems to be the favourite, and I will give it a try when I get some spare time. Ghost 4 lin is also good I hear. Options are listed [here.]("http://linuxappfinder.com/backupandrecovery/driveimaging") This is a tutorial to use [partimage.]("http://www.psychocats.net/ubuntu/partimage")

Give it a whirl, you'll probably find it very useful. Imaging your drive is the best way to prevent against failure IMO, if you have any trouble you boot up and restore and in less than 20 minutes you have a fully functional OS that was just the way you imaged it.

I think that answers question, enjoy :).

Oh and if your using partimage, use this [system CD.]("http://www.sysresccd.org/Main_Page") Contains a lot of awesome apps all in one disk :D.

---

### Post by prizrak on 2007-06-19
Yeah this is pretty old. Is an interesting topic however and this is my view:

In theory and from a technological stand point XGL is a much better alternative. Well it doesn't really go far enough. A fully OpenGL X server does make certain sense and is a pretty cool piece of technology. Even with XGL's buginess it looks better (without effects just the server) than normal X.org interface. Another thing about it is that it would run exclusively from the video card thus completely freeing the CPU.

In practice AIGLX is a better alternative. It provides a fall back GUI that can be used when 3D fails. It also uses old way of doing thing (which is obviously very stable) and renders (AFAIK) the desktop from the CPU only using the video card for effects. 

So in the real world AIGLX is better, as a technology however XGL if properly developed might actually replace X.org at some point.

---

