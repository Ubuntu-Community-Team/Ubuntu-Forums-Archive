---
title: "So I have this disgusting idea, but I need some info before I try it..."
date: 2010-05-15
forum: The Cafe
---

### Post by murderslastcrow on 2010-05-15
So, I had this really fast Duo Core laptop with 2 GB of RAM that I never used even half of the processing power with, and I realized I might as well sell it and look for something more modest (I know, I'm weird- I'm trading a workhorse for something adequate- Linux does stuff to ya').

So, then I thought... hey, why not get a crazy fast desktop for gaming at home? I'm never out of town THAT often, anyway. Then my family could throw out the cable and use web-based services, and I could mess around with some nifty technology (five VirtualBoxes running simultaneously).

So, I found a really fast computer that's well within my price range. But then I thought, "well, I still want something on the go, so maybe a netbook or a UMPC." Then I realized I already have an N810.

Then it struck me- as long as I'm near a computer, I could use some sort of dedicated service to remotely control my PC at home, allowing me to utilize it from anywhere in the world! :O

However, VNC and Yuuguu are the only things I've tried, and I don't know if any of it's really fast enough to be worth accessing my computer from someone else's house.

So, my questions are this- anyone know of viable Remote-Desktop applications you can use from a 20 mile distance (in Linux, of course), and do you know any good remote applications that would work well on ANDROID?

I know I'm crazy, and I'll most likely end up with a half-baked solution, but I've just GOTTA' KNOW. Your thoughts, please.

---

### Post by DodgeV83 on 2010-05-15
Logmein.com works great on Windows hosts and Linux clients, unfortunately there is no option for a Linux host with logmein.com.  They have the best iphone application I've ever seen for remote desktop, but I'm not sure if they have an Andriod application.

[www.teamviewer.com](www.teamviewer.com) works well with Linux/Windows hosts or Linux/Windows clients and have a great iphone application, but I'm pretty sure no andriod application here.

One of the above, if not both, should work for you..  If not, you could connect to your home network through a VPN and just use VNC ;)

---

### Post by BoneKracker on 2010-05-15
Read up on NX.  It's like VNC but designed to be usable over a slow connection.

[http://en.wikipedia.org/wiki/NX_technology](http://en.wikipedia.org/wiki/NX_technology)

You probably want FreeNX or OpenNX.

---

### Post by murderslastcrow on 2010-05-15
Thanks for the helpful suggestions- I'll give TeamViewer and the NX stuff a go, definitely. LogMeIn never really worked for me in the past, but I may check them out if none of these seem satisfactory.

Also, I think it would be interesting, if this software could be broadcast from a server, to see what it would be like to remotely host desktops. You know, like, let my friend with a crummy computer have his own login on my super-fast hormonal death-mongering computer. :D

Again, thanks for the tips- I'll tell you how it turns out for me. :D

---

### Post by BoneKracker on 2010-05-15
If that's what you want to do, then you should look at LTSP:

[http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project](http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project)

[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

### Post by Penguin Guy on 2010-05-15
From 20 miles away there would be a lot of latency, making your computer considerably slower for most tasks. You should look into [clustering]("http://www.google.com/search?q=Clustering").

---

### Post by murderslastcrow on 2010-05-15
You can execute a LTSP over the internet, not just locally? I wonder if it's possible to combine these technologies. Also, I will definitely experiment with clustering.

So far as my testing has gone, NX has excellent performance, but although I'm connecting through WAN, not LAN, I think part of it is still the transfer rate of my router, despite being over 'the internet'. I'll have to check it out from someone else's house.

Still, this is all very interesting, and I plan to fund any projects that work exceptionally well for me, so we can get this technology more readily into peoples' hands.

I'll upload some videos of the process from several distances when I get it up and ready, which could be in a few days. :D Then we can really consider which solutions work best from a subjective standpoint.

---

### Post by BoneKracker on 2010-05-15
I've never actually used LTSP or NX, but I think LTSP can leverage NX to provide a desktop to someone remotely.  You'll have to investigate that.

Either way, I think NX may be what you're looking for.  From what I've read, it does some interesting things to reduce latency.

Also, I'm not sure "distance" per se is the issue here.  As I understand it, latency is not a direct function of distance.  It is also a function of the number of hops (a bit of handling has to occur at each hop), network congestion, and other factors.

I'm not a newtwork engineer, but I think from a raw distance perspective, you're basically dealing with electricity and the speed of light.  So you may want to tabulate / correlate your experimental results against not merely "distance" but also Round Trip Time (RTT) and Number of Hops (which you should be able to obtain from the ping and traceroute utilities).  Traceroute may also help you identify where any bottlenecks are.

---

### Post by tgalati4 on 2010-05-15
Make a list of the things that you want to do remotely.  There are web-based applications for most of those services already.  Set up a LAMP server and set up some other services and access everything through webpages.  

You can also log in via ssh with X-forwarding and run gnome-panel to get a desktop on your local machine.  This tends to be faster than VNC.

---

### Post by scouser73 on 2010-05-15
Why did I read this and think Stewie Griffin had typed it? [IMG]http://images.free-extras.com/pics/s/stewie_griffin-1144.gif[/IMG]

---

### Post by murderslastcrow on 2010-05-16
Lmao- yes, I'm going to be forwarding X through my time-machine, so dimensional distance will certainly be a factor.

Yeah, I know I can set up LAMP, but my objective here is basically to test how graphically intensive I can get (Blender, Wine games, running VirtualBox in the NXClient/VNC session, etc.). You know, just to see what else it can do. So far, it's been able to handle SNES games fairly well, and some MUGEN (this could be awesome in 2-player setups, sharing the keyboard over the internet to allow tournaments, for example).

I'm definitely learning a lot about the X server and reading a lot of documentation. There really are a lot of options, here, so I'll have a lot of OpenSSH and network modification to deal with over the next week or so.

This has gotten me really excited, to be honest. Just gotta' wait for that computer to get here, then I can really get my hands dirty.

I've even thought so far as to running the client on an AIGO with e17. I think my ultimate test would be checking the frame rate of emulating Smash Bros Brawl through the NX server on an MID.

You can guarantee I'm going to try it. This is my annual geek-out.

---

### Post by murderslastcrow on 2010-05-17
K, I've gotta' say, my favorite feature of NX so far is running applications from the console and having them render alongside my other native windows, rather than brining up an entire secondary desktop.

Just has this awesome feel to it I can't explain. The best remote desktop experience over WAN I've ever had. Unless LTSP can get much better performance than this, which is already pretty magnificent, I think I'm gonna' stick to straight NX sessions with public keys.

I can't believe I never heard of this until lately! It's awesome stuff. NoMachine is a great example of an open source company doing it right.

---

### Post by BoneKracker on 2010-05-17
Glad to hear it's working well for you. :)

Regarding LTSP: You can't really compare NX and LTSP.  LTSP might _use_ NX, but LTSP is a broader thing (practically a distro in itself).  It's really about provisioning entire remote desktops to multiple users simultaneously, which they routinely use as their desktop, probably on some kind of thin client hardware.  I only mentioned it because I thought it _might_ just fit your use case.

---

### Post by murderslastcrow on 2010-05-17
Oh, certainly. I've used LTSP before in a server/light client environment, and it works very well locally. I'm interested to see if it could perform on a wider network, or in tandem, and I'm reading a lot of documentation to see what steps I would have to take for that.

It's interesting, to say the least. I think it would be really great to GUIfy more of the process for noobs, of course, which will probably come in time.

It just amazes me that this technology is available and usable TODAY. :3 LTSP really is great for people with older computers who need multiple desktops, since they can bring in a newer PC and share the resources. I have a friend who uses it in his six member family and it actually operates very well if you have the ethernet chords for it. XD

---

### Post by BoneKracker on 2010-05-17
> **murderslastcrow said:**
> LTSP really is great for people with older computers who need multiple desktops, since they can bring in a newer PC and share the resources. I have a friend who uses it in his six member family and it actually operates very well if you have the ethernet chords for it. XD

It's _perfect_ for schools.  Not only does it save hardware money, but it keeps kids from screwing up the workstations, reduces the cost of hardware theft and damage, and makes centralized administration much easier.  I recently tried to convince a school district superintendent (in New York) to use it.  I ran some quick numbers and figured out they could avoid $300K of what they were planning to spend this year to buy new hardware.  They weren't interested, because the government reimburses them like 80% for such expenditures.  Plus, somebody on the schoolboard had a hardon about getting rid of Macs and using PCs instead (apparently the conventional wisdom from around 1997 finally trickled down to their level, even though it's no valid).

I almost sprang a hemorrhoid and had to resist the urge to yell at the guy about how "the Government" is not some magic kingdom in the sky -- that the money comes from taxpayers, and that half of what they spend on hardware ends up in China. Don't get me started. ](*,)

---

### Post by murderslastcrow on 2010-05-25
Okay guys, you have no idea...

I'm 25 miles away, playing my music, videos, editing my documents, and messing with GIMP, and printing documents, all from my super fast computer. It's all instantaneous! I feel like I'm right there. There's.... like, no difference. It's SICK!

I'm so surprised I never knew of this. So worth my time. The only thing I have yet to get working is the composite manager (so I can do 3d programs, maybe compiz, as an extra video layer). I heard that this used to be included, and the test servers have effects enabled. I just need to figure out how to get it going.

I've read up a lot on VirtualGL and the turbojpeg codec, and installed them on both the server and client computer... just not sure how to enable it. Doesn't seem like I should have to modify anything about the computer I'm connecting to the NX server from.

Anyway, I'll be including some videos soon, just to prove it to you. It's maddening. Just outrageous. Like, Flash videos, on Youtube, fullscreen- WITH NO LAG! It's so nice. Oh, I'm so excited to finally get the compositing working.

</geeky freak out session> Look forward to some extra feedback from me. This is just too cool.

---

### Post by BoneKracker on 2010-05-25
This might be a good time to insist that you owe me a beer for pointing this out out to you.

---

### Post by murderslastcrow on 2010-05-27
Haha, indeed, I must. Well, bad news and good news.

Bad news- I've been hacking away at VirtualGL, making sure my users are authorized by X, messing with restrictions levels in vglserver_config, and testing vglrun with many applications and different settings, but to no avail.

Good news is that one or two people on the internet have successfully used VirtualGL with NX without issue. I think the problem MAY be that I installed NeatX rather than FreeNX, as the Ubuntu Community Documentation suggests.

Either way, I'm putting the 3d support on hold for now as I wait for responses from a few people. However, from what I've heard the performance is pretty good in general.

If anyone here has any suggestions for who to contact or where to look for more information on this, it would be extremely helpful. I've read the Sun VirtualGL documents as well as VirtualGL's official documentation, and either way I still get an error that tells me whatever display NX is running on can't access PBuffers to do the rendering, despite having correct information, 24-bit color depth, and 3d graphics installed on the host.

But yeah, not a support thread, just wondering if any of you have had more experience in this area. Once I get this working, I'm writing a freaking tutorial with step-by-step instructions. Getting NX working is pretty simple, but I don't want anyone else to have to wrestle so hard with VirtualGL.

---

### Post by kevdog on 2010-05-28
I look forward to the tut!!!

Cheers

---

### Post by murderslastcrow on 2010-05-28
Lol- so GUESS WHAT!?

It was totally NeatX's fault. You've gotta' just use FreeNX, and then VirtualGL works great. Much better than I expected it to, for that matter.

Now all I have to do is find a way to run NX on top of VirtualGL so that I can access compiz, and see how well that runs. Blender seems to work fine for me, and I'm about to try a few Wine applications. This is totally unreal, I can't believe I can do this much. Just wow.

Oh yeah, you need to install the FreeNX available in the testing PPA, not the one provided in the Ubuntu Community Documentation. FreeNX is a lot faster than NeatX, too, it seems. It's as if the tiny jilts in refresh that used to happen every so often have vanished. It has been around quite a bit longer, after all, and it has a few more features than NeatX.

---

### Post by isotherm on 2010-07-14
Did you ever get Compiz working through NX with VirtualGL? If so, do you mind sharing how you did it? :)

---

