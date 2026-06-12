---
title: "I think my Linux experiment is...  Over."
date: 2021-01-05
forum: Ubuntu, Linux and OS Chat
---

### Post by phuzzyday on 2021-01-05
Looong time Windows Power user here.  Now one might think a computer techhie might be the ideal guy to try moving to Linux, right?  The problem with that, is that this very type of person is also doing a lot of perhaps interestingly off the wall things with their computer.  These things often CAN be done in Linux, but success depends on the amount of time and determination the person has to find all the workarounds.

In fact, I would say that Linux might be better suited, in it's current form, to light, average users.

Ok, here's my deal.  Ryzen 5 3600 on an x570 board.  GTX 1060 3GB.  16 GB.  Several drives, but booting Linux off of a 500g SATA Samsung SSD.  (Kubuntu.)

There are many interesting things in Kubuntu that I really like!  Not the least of which was pulling 20W less from the wall...  for some reason...   all the time.  Liked the interface.

Here are the things that led me to going.. BACK to Windows!!! I WAS gonna duel boot, but I HATE rebooting.  Anyway, perhaps this information will help the community.  


[LIST]
[*]Used VMWare Player to run Win10 to do the stuff I couldn't do in Linux.  (The Zoom Linux app has fewer features.  Sucks.)Also, Fusion 360 for 3D modelling.  I know there are Linux alternatives, but they all seem SO different, unlike, for example, video editors, which all follow a generally common principle.  Now VMWare is GREAT, Better than Virtualbox by MILES if you want to pass through USB devices, but I seemed to often get a **total system hang** when shutting down or saving the state of VM's.  Even the mouse would freeze.  At times I thought it was a video driver thing, based on log peeking, but still not sure.
[*]Sound.  It's rather confusing.  Pulse?  Jack? Alsa?  Not sure how these all relate to each other, but I muddled along, but one settings seemed to be tucked away in a config file.  The sample rate!  And if I changed it, I couldn't tell if it was any different on the screen anywhere.  I use several audio devices.  Frustrating.  Just a guessing game, but I got tired of guessing.  Again, if comes back to the time and determination of the user...  I must say, the pulseaudio setup seemed pretty dang advanced.  Still nothing like EqualizerAPO on Win though.
[*]Multi-Monitor stuff... Even for the same app, one dialog would be on the far left edge of the left screen, then the next would be on the far right of the right one....  Windows apps struggle with this too sometimes, but it's nearly like Linux developers are trolling the users.
[*]The 'Discover' software installer in Kubutu has a search algorithm that is screwier than steel wool.  I can type an exact title for something I need, and the right one will be 10 or 15 down on the list.  What the heck?
[*]I love that a lot of games are working via Steam now, that's pretty cool.  TONS don't though.  And like I said, I hate rebooting..  This is scraping the bottom I guess..
[*]I like to play with SDR.  The software for Win is all open source or free, but there sure seems to be a lot less for Linux!
[*]Seems like there are so many broken dialog boxes with fonts that don't show properly...  And I am sure there are other things...
[/LIST]

I understand that the *foundation* under the distros, The Kernal, gets "honed to a fine edge" by a LARGE community of developers united in that direction, and that foundation certainly seems very awesome, but a big part of me wishes a similar thing was happening with the Distros & Window Managers.  If that many minds were focused on honing *these* areas to as sharp of an edge, (Less distros, or maybe a tiny number), Linux would be a seriously reasonable option for new PC buyers!  AS it is, it seems like there are too many bad ideas in some windows managers, for example, that just don't show the same amount of thought or refinement.  There just doesn't seem to be enough in common between them.  An experienced tech in one distro could be put in another, and just not know where ANYTHING is, or how ANYTHING is organized.  (I guess the command like can make up for that a lot of the time, but that doesn't help newer users..  the example still stands.)

Now don't get me wrong, I LOVE that Linux is there.  I am AMAZED by the hard work done by SO many, and I would definitely recommend it to some users! But I am pretty sure the market share is important, so this information might help get more, even if I don't move.  (My Octoprint instance on my Pi 3B rocks, and I will continue to learn on my 8G Pi 4..  once my health starts allowing for it!)

Open Source in General?  I think of all these developers as the cream of humanity.  

Interesting to hear comments..

---

### Post by malspa on 2021-01-05
> **phuzzyday said:**
> and I would definitely recommend it to some users

That sums things up for me. But for the most part I don't go around recommending Linux to anyone. I figure the ones who'll take to it will probably find out about it and come around to it on their own. The others will use something else, everybody's happy, Life goes on.

---

### Post by QIII on 2021-01-05
> **phuzzyday said:**
> In fact, I would say that Linux might be better suited, in it's current form, to light, average users.


Like virtually 100% of supercomputers, the lion's share of the internet backbone (95% of the top million web servers), 50% + or corporate servers, most of the world's cell phones, automobile electronics, the IoT, most routers, automation controls, smart TVs, DVRs, private space vehicle avionics, smart homes - and users ranging from grandmothers to super-tech guys like me.  The number of the world's devices using Linux out strips by at least an order of magnitude anything coming out of Redmond or Cupertino.

If I had a dime for every post like yours on these forums ...

But use what works for you.  That's what is important.

---

### Post by TheFu on 2021-01-05
You gave it a shot!  Linux isn't for everyone.  At least you know now.

I just hope you didn't bring too many ideas from Windows expecting those to transfer to a Unix-like OS.  There are very different philosophies.  Power Users, if they have the flexibility, generally love Linux for all the capabilities that you can create yourself, without waiting for some SW developer who doesn't have the same itch to solve.

The people with the most problems switching are those who use point-n-click for nearly everything.  I suspect there are too many Windows-converts programming on Linux these days. They never read [https://en.wikipedia.org/wiki/Unix_philosophy](https://en.wikipedia.org/wiki/Unix_philosophy)  and have brought more and more and more and more and move bloat.  

WM likes and dislikes is very personal.  There's no accounting for taste, right?

People with decades of time spent learning all the weirdness that is MS-Windows forget all that time spent doing it. Linux needs that same level of time commitment to get to a similar skill level.  People using only the GUI are getting only about 20% of the power that computers offer.  It is all the non-GUI things where Linux/Unix shines, especially automation.  But OS-tourists will never get to that level. Nothing wrong with tourists. Their money spends too.

When I'm forced to use Windows (I was a "power user" for a long time), I find it very frustrating.  There's just so much is doesn't do.
I don't hate rebooting, but it isn't usually necessary.  Here's 3 different systems, two are storage servers and run stuff like Calibre, Plex, NFS, and a few VMs.  The last system is pretty busy

```
$ uptime 
 11:07:25 **up 44 days, 18:09**,  2 users,

$ uptime
 11:06:52 up 30 days, 23:41,  1 user,

$ uptime 
 11:18:22 up 23 days, 16:27,  4 users,  **load average: 12.29, 12.06, 8.41**

```

And a raspberry Pi running OSMC (Kodi) connected to the Plex Server:
```
$ uptime
 11:10:35 up 21 days, 15:59
```

These systems are from 2010, 2015, and 2019, so a mix of hardware. One was $45 all in.  The NFS/Plex/Calibre server was $126 (MB+CPU+RAM) + storage. Everything else was reused from an old machine.  The busy system is a Ryzen 2600 w/ 32GB RAM running 10 VMs and batch transcoding some video processing.  About 50% of the RAM isn't being used.  Because I don't game on normal computers, the most expensive GPU is a fanless nvidia 1030.

A newer Ryzen will have some bleeding edge issues, based on my research.  Many motherboards have moved the 2.5Gbps networking, which have really bad drivers at this point, included the Intel NIC drivers. I've been looking to replace 2 of those older systems with a newer Ryzen, but decided against using any Realtek NICs. I prefer Intel for a number of reasons. Been pretty happy with the i211 and i210 NICs, but those don't seem to be in the newer Ryzen motherboards, unfortunately. I'll probably end up with a B450 or X470. Generally, I have 3 NICs in a system for physical network separation and risk management.  For people new to Linux, they will likely learn that vendor support is spotty for any hardware that isn't hugely popular, mainstream, and loved by Linux people.  That can be scanners, printers, and sometimes even USB storage. This can be extremely frustrating. Even if you buy something marketed with "Supports Linux", that doesn't necessarily mean it works with a current kernel.  I was burned by a HW-RAID card with that claim. The Linux kernel the card's drivers supported was 4 yrs old. Same for many video recording devices - like a Haupauge 1212 and 1515.

If you will only have 1 box and are tied to multiple Windows programs still, I can see where Linux could cause a hardship. At this point, I use 3 Windows programs.  One is a video editor and the other 2 are financial software related.  The video editor use has dropped drastically this year - now it is used maybe 30% of the time. I don't see the financial tools ever being gone completely, but at least I don't need Windows running, which drastically reduces all sorts of security risks.

Again, at least now you know that KDE isn't for you.  Have you tried Mate or Cinnamon or being completely crazy - fvwm?  These really aren't something for a Ryzen 5, unless you just prefer cleaner desktops, like me.  Then your system should fly. Windows open before you bring you fingers up for many non-bloated applications.

---

### Post by CatKiller on 2021-01-05
> **phuzzyday said:**
> Looong time Windows Power user here.  Now one might think a computer techhie might be the ideal guy to try moving to Linux, right?  

Nope. Absolutely not. Windows power users have **by far** the hardest time. All their instincts are completely wrong, and finding out that you know very little about computers, even if you know quite a lot about Windows, is very uncomfortable for the ego.

---

### Post by TheFu on 2021-01-05
One more thing - lots of users are running into problems with Canonical's Snaps, though many people are not.  There are lots of distros that don't use Snaps which might remove that pain-point.  Linux Mint is very Ubuntu-like, but without snaps, for example.  You can add snaps, if/when you decide that's a good idea, but the GUI software installer won't trick you.  

I think Debian is the same, but they really want to remove brands - so there isn't a "Firefox" browser. The different names for things are almost Apple-like where Apple changes the names of common things for reasons only they know. This can be frustrating to some users, like me.

SuSE is a nice distro too. Worth checking out.

I wouldn't suggest Fedora, Arch, or Slackware to anyone new, unless you have a close friend willing to help get over the multiple humps.

People often forget that the GUI isn't the OS.  There are 20 popular GUIs for Linux. Try some out. Check out a few youtube videos of each.  Remember the Next computer?  You can run that GUI on Linux.

---

### Post by GhX6GZMB on 2021-01-05
> **TheFu said:**
> 
People often forget that the GUI isn't the OS. 


Except that in Windows it is. First you build a GUI and then try to kludge together an OS under it.

---

### Post by grahammechanical on 2021-01-05
If Linux is suitable for light, average users, how is that suppliers when they sell their laptops with Linux pre-installed it is expensive developer version laptops that they offer and not cheap machines for the light and average users? They market Linux machines for the power user.

 I wish they did sell less powerful machines for the average user with Linux pre-installed. I might be tempted to purchase one. More ordinary users might purchase them to avoid the stresses of dual booting with an OS that does not play nice.

By the way, what is the latest Zoom version? Some sites say 5.4.7. That is exactly the version of Zoom client that is presently installed on my Ubuntu 20.04. Funny that. Is it not?

Regards

---

### Post by TheFu on 2021-01-05
Cough ... Chromebooks running ChromeOS (linux) and MS-DOS as a MSFT non-GUI OS that Windows is built onto.

---

### Post by phuzzyday on 2021-01-05
All i know is that In Linux, Zoom has no background replacement feature.

---

### Post by QIII on 2021-01-05
That is not the fault of Linux.  The Zoom developers have not provided that for their Linux version.

---

### Post by phuzzyday on 2021-01-05
I have to ask..  Do you actually think I don't KNOW the extent of Linux use in areas other than in the home computer area?  Do you think I am throwing crap at Linux in general?  I thought in this forum one might be able to assume workstation use was the primary subject.  Perhaps I was wrong about *that*, but not in the other respects. (I HAVE been working with computers for a solid 40 years, but I guess I should have stated that to protect myself from assumptions.)  I thought I did a pretty good job of balancing my appreciation for what Linux has accomplished, and what I am still learning, against my day to day needs.  Like you say, the preferred choice for each person is different.  Did..  did you think I wasn't aware of that either?  

To be honest, I really LOVE Linux, and I wish it was the easiest route for me, but right now, I'm going to keep learning on my little ARM stuff.  I have an extra tower that may be destined for it also..

---

### Post by phuzzyday on 2021-01-05
I appreciate your reply.  The difference in how Unix stuff it put together is what fascinates me about it!  And this was nowhere NEAR the first time I have tried to move over, just the longest running try yet.  I'm not exactly repartitioning that drive in the foreseeable future either....

---

### Post by phuzzyday on 2021-01-05
I guess I had the advantage of having played with it in smaller capacities for the past few years.

---

### Post by phuzzyday on 2021-01-05
Pretty sure you are correct there.  I was more less explaining one of the reasons for using a VM.  MAN I wish the VM didn't freeze the system so often when shutting it down.

---

### Post by VMC on 2021-01-05
I didn't go back or forward or sideways. I use them both (Windows, Linux) ,for their strengths. To me its not either/or, its both. Whats lacking in one is the others strength.

---

### Post by phuzzyday on 2021-01-05
> **TheFu said:**
> People often forget that the GUI isn't the OS.  There are 20 popular GUIs for Linux. Try some out. Check out a few youtube videos of each.  Remember the Next computer?  You can run that GUI on Linux.

I think my post made it pretty clear that I knew that.  That's why I said I wished there were fewer GUI's, each having been given the amount of time and attention given to the Kernal.  Maybe one MAIN one?  I dunno.

---

### Post by QIII on 2021-01-05
Who chooses the "main" one?  Maybe that won't be what somebody else wants as the main  one.

---

### Post by poorguy on 2021-01-05
> **VMC said:**
> I didn't go back or forward or sideways. I use them both (Windows, Linux) ,for their strengths. To me its not either/or, its both. Whats lacking in one is the others strength.

Exactly.

I have Linux installed on a desktop.

 I have Windows installed on a desktop.

I agree Linux and Windows each have their strengths and I use both although one more than the other.

I have a dual boot Linux and Windows desktop using a separate hard drive for each OS and have no problems.

Best of both worlds.

---

### Post by TheFu on 2021-01-06
> **phuzzyday said:**
> I think my post made it pretty clear that I knew that.  That's why I said I wished there were fewer GUI's, each having been given the amount of time and attention given to the Kernal.  Maybe one MAIN one?  I dunno.

_Too many choices_ is a common complaint, but that's part of the Unix culture.  Assuming that a team working on a project they love would switch to work on some other 'meh' project just doesn't happen when volunteers are involved.  Herding cats is hard, even harder when their mortgage isn't dependent on doing what you want.

It is all about scratching a personal itch, at least for me.

---

### Post by birdman1959 on 2021-01-06
I'm here to research screen flicker in my Ubuntu 20.04 System 76 computer, and read this with interest. I have had just the opposite experience. When I used Windows I was able to do a lot of maintenance, reconfigs, driver updates/conflict fixes somewhat ably on the myriad of issues that seem to be commonplace on Windows machines. But Linux has made me lazy. Things rarely go wrong. Answers for the few things that do, are easily fixable. Its solid as a brick. After my experience, it is hard for me to understand why schools and business's spend all that time and money for Windows. It's great we have choices.

---

### Post by ajgreeny on 2021-01-06
> **phuzzyday said:**
> All i know is that In Linux, Zoom has no background replacement feature.
Mine does, (Zoom 5.4.7 downloaded from [https://zoom.us/download?os=linux](https://zoom.us/download?os=linux)) though it tells me that it needs a more powerful graphics system than I have and it also needs a plain "real" background for it to work properly, and I don't have that either.

I don't know if it's the same for Windows as I do not use Windows any more.

---

### Post by deadflowr on 2021-01-06
> **ajgreeny said:**
> Mine does, (Zoom 5.4.7 downloaded from [https://zoom.us/download?os=linux](https://zoom.us/download?os=linux)) though it tells me that it needs a more powerful graphics system than I have and it also needs a plain "real" background for it to work properly, and I don't have that either.

I don't know if it's the same for Windows as I do not use Windows any more.

Do you mean this:[https://support.zoom.us/hc/en-us/articles/210707503-Virtual-Background#:~:text=Linux,Click%20Settings.&text=Note%3A%20If%20you%20do%20not,image%20by%20clicking%20%2BAdd%20Image.]("https://support.zoom.us/hc/en-us/articles/210707503-Virtual-Background#:~:text=Linux,Click%20Settings.&text=Note%3A%20If%20you%20do%20not,image%20by%20clicking%20%2BAdd%20Image.")

---

### Post by ajgreeny on 2021-01-06
> **deadflowr said:**
> Do you mean this:[https://support.zoom.us/hc/en-us/articles/210707503-Virtual-Background#:~:text=Linux,Click%20Settings.&text=Note%3A%20If%20you%20do%20not,image%20by%20clicking%20%2BAdd%20Image.]("https://support.zoom.us/hc/en-us/articles/210707503-Virtual-Background#:~:text=Linux,Click%20Settings.&text=Note%3A%20If%20you%20do%20not,image%20by%20clicking%20%2BAdd%20Image.")
Yes, that's the one!

I was on an Android tablet when I posted so could not get that page to show the image, so thanks for finding it and posting.

---

### Post by agvantibo on 2021-01-12
> **TheFu said:**
> MS-DOS as a MSFT non-GUI OS that Windows is built onto.

Cough... Windows migrated to the NT kernel years ago. And became much worse. You can't even play DOOM on the Windows 10. And dosbox runs smoother on Ubuntu.

---

### Post by TheFu on 2021-01-12
> **agvantibo said:**
> Cough... Windows migrated to the NT kernel years ago. And became much worse. You can't even play DOOM on the Windows 10. And dosbox runs smoother on Ubuntu.

And yet MS-Dos bugs are still being found from the pre-NT days, cough.
Not that Linux is better on the bugs. Long-time bugs (and short-time bugs) are always going to be found.  

I have a little direct history with extremely high-quality, non-trivial, coding. Even when we (and every one else) thought there were zero SEV-1 bugs in the software, history of that project showed in 2011 that over 100 more were yet to be uncovered which existed at the time that belief was there.  Commercial software has thousands and thousands of bugs that can crash the program. Some have over 50K, like Windows always had. I'm fairly sure I can find a reference for my claims, but it is thick reading, meant only for software people with decades of experience tracking bugs and their root causes. On that program, **every** bug was analyzed for root cause AND actions were taken to ensure that type of bug never happened again. It was a very expensive program.

---

### Post by mastablasta on 2021-01-13
> **phuzzyday said:**
> 
[LIST]
[*]The 'Discover' software installer in Kubutu has a search algorithm that is screwier than steel wool.  I can type an exact title for something I need, and the right one will be 10 or 15 down on the list.  What the heck?
[/LIST]


Yes it's messed up. Muon found them correctly. I am not sure what went wrong in the development. they will iron it out. until then apt is faster anyway... :P

> 

[LIST]
[*]I love that a lot of games are working via Steam now, that's pretty cool.  TONS don't though.  And like I said, I hate rebooting..  This is scraping the bottom I guess..
[/LIST]

OK so first i installed a bunch of games using Play on linux. i have old Pc so these are old games. but still - wow. so easy and so many just work. many of them better than in windows. Far Cry 2 is the one that stuck with me. performance is so much better on linux i could increase the GPU settings. Rome total War also performs better, just for some reason i can't get the videos showing.

But then the kids wanted some windows games they saw and it was winter sale, so we gave it a go. just a few clicks of next button on Steam and we had Doom 2016 running, they play Subnautica now, we have a bunch of linux native games... i was watching with eyes wide open. this is really a giant leap. no more messing what libraries to install and which ones not, which should be native, which should be built in. they just work. then i checked a few new titles and they also work with gold or platinum rating. this is just awesome.

games that have issues running are mostly multiplayer games that use anticheat (rootkit). i think that with help of Valve and others they might solve that one as well. on the other hand they have hardware cheats now (completely undetectable), so i wonder what is the point of client side anticheat software.

anyway aside from this major shift in games working on linux, there is another one to consider. and that is the emergence and fast development of services such as Stadia and Nvidia Prime. They are OS agnostic and as we did some calculations here, they seem to cost less than an investment in real gaming PC, while providing similar experience. very tempting. 

at the moment windows 10 seems unnecessary to me. Sure we could have a bit more games working. more multiplayer games with plenty of cheaters with spinbots, wall hacks.... but since we are more oriented into having fun with familiy and friends, the current choice of games works for now. the only thing i miss is the MS Office suite. i know 365 works in browser, but it's just not the same. i wish they made it at least fully compatible with wine. libre office is good in some thins but not in most. 

and if we really needed something that runs only on win10, we could always use vbox for it.

---

### Post by grahammechanical on 2021-01-14
I gave up experimenting with Linux more than 12 years ago when I installed my first version of Ubuntu. That was Ubuntu 7.04. I am still using Ubuntu. I do have a couple of other distributions of Linux. I sometimes get curious. 

My wife sometimes says that she wants a laptop. I am dreading having to buy one because it will surely come with Windows on it and my wife will expect me to instruct her on how to use it and to fix things when it breaks. And I have no idea on how to do that. Such is life with a wife.

Regards

---

### Post by CatKiller on 2021-01-14
> **grahammechanical said:**
> My wife sometimes says that she wants a laptop. I am dreading having to buy one because it will surely come with Windows on it and my wife will expect me to instruct her on how to use it and to fix things when it breaks. And I have no idea on how to do that. 
There are plenty of laptops that come with Linux pre-installed. Get one of those.

---

### Post by mastablasta on 2021-01-14
> **CatKiller said:**
> There are plenty of laptops that come with Linux pre-installed. Get one of those.

or one without OS. it's what we did. 411 EUR for Ryzen 5 laptop is a good price for where i live. maybe screen could be a bit better, but meh... it's good enough. Dell was 600 EUR with slightly better configuration (i5+nvidia).

Lenovo Thinkpads can come without OS preloaded and support linux.

Many HP that are sold with no OS loaded also have good linux support.
They even had some gaming laptops with linux preloaded. or was that Asus?!?! hmmm... i saw it at local store about a year ago.

Dells have some good Ubutnu preloaded laptops. lower or medium range. also "business class" Vostro.

and ofcourse smaller vendors. looks like there is more and more of them.

---

