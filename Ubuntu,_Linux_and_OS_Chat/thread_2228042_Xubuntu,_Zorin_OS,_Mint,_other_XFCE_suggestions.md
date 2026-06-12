---
title: "Xubuntu, Zorin OS, Mint, other XFCE suggestions"
date: 2014-06-05
forum: Ubuntu, Linux and OS Chat
---

### Post by popcornchickenh4x on 2014-06-05
I appologize for the similarity of this post to some of the newbie posts around, but I have been searching for days to find some info on XFCE distrobutions for experienced linux users. Pretty much all the information/reviews I could find on any of this was geared towards the new linux user/windows/mac converts. I have used many Linux distrobutions over the years and always suffered from the "new to linux/overwhelmed" issue so I have always given up and gone back to windows like many people before me.

However for various reasons at work I have been doing a lot of penetration testing and security on our network, which is how I ended up back into linux. I currently am dual booting backbox and windows 7 and I am very comfortable with partitioning drives, installing, ect. I have also been putting in a lot of time with linux, and actually work a full time job doing development with 12.04 precise on embedded boards/micro computers. So I am extremely comfortable with git, compiling from source, make, automake, bash in general and most of terminal.

I have fallen in love with the XFCE desktop environment, however I am well aware that backbox is not a good daily use OS. I am looking for a good XFCE based distrobution for daily use with the exception of gaming, as I will always need my windows partition for that (I have an ATI HD4890 and there are simply no good drivers/ openGL support for my gfx card, its too old and ATI only supports 9x+ in linux these days). 

I really like the looks of Zorin OS but I will most likely not use a large majority of the stuff included, and I am curious if there is more to it than just the pre-installed packages and pretty desktop environment they have created. I also like the advertised boot times on their site. However I dont want to start out with something that is bloated with a bunch of useless crap. I guess my question about it, is if all the pre-installed stuff is worth it.

Next is Xubuntu. On my work laptop I am dual booting Ubuntu and windows 7 since I am a software engineer and I need access to visual studio. However I have installed XFCE on the Ubuntu and have it set up looking really nice. I have done research on Xubuntu and I like firefox, thunderbird ect. anyways so the preinstalled stuff is fine with me. I Have been seriously considering Xubuntu, but I am just trying to explore any possible better options. I can install any packages I will need.

Mint, I do not really like the look of Mint, however it seems to be extremely popular and I know any desktop environment can be built, but I am just curious if there are any advantages of Mint I am not seeing. It basically seems just like Xubuntu to me and if there is any strong reason why I should consider Mint, please let me know.

Others? I really like Voyager, A LOT.  However I do not speak French and I am 100% sure that anything that is left in french will drive me nuts as I want to have an extremely polished environment (OCD). However I am open to any suggestions, I would prefer to be on the newest Ubuntu 14.04 and I  have not been able to find/replicate anything that looks as good as the default backbox desktop environment XFCE.

Anyways, I apologize for the lengthy post, and noobish question, but there just doesnt seem to be any information on these for a somewhat experienced linux user and I really need to get on something other than backbox for daily use due to all the security vulnerabilities. Thank you for your input/opinions.

*edit* I should add that I have 16 gigs of ram on my desktop mostly for virtualbox/vmware. I have tried distro's in VM but the performance is always completely different on the whole machine, installed rather than live as most of you know. Which is why I have come here to ask for opinions instead of just trying a bunch of them. Also my internet speed is terrible so it takes litterally a day or 2 to download an iso/distro depending on size.

---

### Post by Toz on 2014-06-05
Hello and welcome to the forums.

+1 for Xubuntu.

However, you might want to consider doing an Ubuntu minimal + Xfce install if you want finer control of the packages that are installed.

Or, since you're familiar with git and compiling from source, you could do an ubuntu minimal and build Xfce from git - and stay on top of all the latest development that is happening (keep in mind that cutting edge has its benefits and its pains).

---

### Post by robin7 on 2014-06-05
A little closer to Debian if you wish, from the same team that gave us antiX, a newer "midweight" Xfce blend called MX-14.  But I actually found Xubuntu 12.04 to be faster and a lot easier to configure and manage.

---

### Post by LastDino on 2014-06-05
Well, there are one or two more I would like to mention; have you tried Fedora? It looks almost exactly like Xubuntu. I use it as my main OS. 
I've lighter version Manjaro installed on one of my test partitions. Give a shot at Manjaro, especially the Openbox edition, it also has XFCE but I've never used it. 
(Sorry in case I missed these in your post or any specific hate towards arc or Fedora or love for Debian)

Voyager is not bad tbh, and only things I see in French is that menu search bar, I've managed to change language of software centre somehow. This is also installed on my one of test partitions and although its kind of buggy when compared to Xubuntu, its not a deal breaker.

There are tons of options available tbh, one might never run out of them :3
(Posted this from Ubuntu Gnome which is not bad either)

---

### Post by popcornchickenh4x on 2014-06-05
I have tried Fedora, but that was years ago, and pretty much any linux distro I have looked into recently is insanely different from how it all used to be. In a good way of course, and the support for everything is so much better I can't even put it into words.

There are a few reasons why I lean towards Debian and more specifically Ubuntu:
- first I REALLY like the package/repositories available. There is just so much available easily
- second is the extensive ammount of online help resources. Pretty much every problem I have had, I have been able to find somebody else who had the same problem, and most of the time a solution, or at least a few options to try. I know that this is true for a lot of other distributions but as one of the noob friendly distrobutions, it seems like there is a lot more documented as far as problems and fixes go.
- finally, I work in ubuntu every day at work, and I am very comfortable in it, so although I plan on exploring other kernels/distro's in the future. I am no linux god yet so I would like to stick with what I know for now.

Thank you all for your input so far, I will be sure to check out a few of the suggested options.

p.s. I hate gnome and I especially hate Unity, it just looks way too dumbed down for me. I understand that is a great approach for somebody new to linux, but for me, just not my slice of pie.

---

### Post by mikewhatever on 2014-06-06
> **popcornchickenh4x said:**
> ...

p.s. I hate gnome and I especially hate Unity, it just looks way too dumbed down for me. I understand that is a great approach for somebody new to linux, but for me, just not my slice of pie.

... and here coomes the trolling. Not sure why you'd bring this up here and now.

---

### Post by popcornchickenh4x on 2014-06-06
Not too sure what you mean by that. Was just pointing out what I don't like so it could be avoided. I like XFCE especially for the detailed "start menu". I am not a fan of the windows look alike ones, just the standard XFCE menu that lists pretty much everything I need to use. 1 thing I like about backbox that I have not been able to find anywhere else is the services catagory on that menu. It is nice to just click an easy access GUI to start/stop/restart my services like network manager without going through terminal or other methods. It also helps me keep track of which services I currently have installed.

downloaded xubuntu last night, gunna try it out today and see how I like it.

p.s. sorry if my distaste for unity is somehow considered trolling or something it is just my opinion and I don't mean to offend anybody

---

### Post by Toz on 2014-06-06
> **popcornchickenh4x said:**
> 1 thing I like about backbox that I have not been able to find anywhere else is the services catagory on that menu. It is nice to just click an easy access GUI to start/stop/restart my services like network manager without going through terminal or other methods. It also helps me keep track of which services I currently have installed.

Not exactly sure what backbox offers, but there is a gui services management tool available, but its not installed by default. It's called [Bootup Manager]("http://www.marzocca.net/linux/bum.html") (bum). To install it, look for it in the Software Centre or from the command prompt:
```
sudo apt-get install bum
```

> p.s. sorry if my distaste for unity is somehow considered trolling or something it is just my opinion and I don't mean to offend anybody 
I didn't read your comments as trolling, Unity just isn't everyone's cup of tea. I prefer Xfce but all three of my kids and wife use Unity. To each his/her own.

---

### Post by robin7 on 2014-06-06
If my computer could handle it, I think I would run Unity.  It looks gorgeous in every screenshot I've seen and looks as easy to manage as my current favorite, Xubuntu, which flies along nicely even on very old hardware. Unity looks *different* but not difficult, and I enjoy trying new things.  My next computer will be an Ubuntu box I hope.

But for Xfce distros, I keep ending back on [Xubuntu]("http://xubuntu.org") even after playing with other Xfce mixtures that are supposedly a lot faster, easier, better, etc - but they're not.  Not on my computer at least, and not in my user experience. SalixOS, Debian with Xfce, Crunchbang with Xfce, Mint Xfce, SalineOS, PCLinuxOS' unofficial Xfce spin (which I consider 2nd best to Xubuntu - even more than Mint's Xfce version), and most recently MX-14 (Debian Stable/Xfce spin from AntiX).  **Xubuntu (12.04) beats them *all*** for speed, simplicity, configurability, beauty, default software choices, community, and support. **But that's my own preferences on my own hardware.**  One user's delight is another user's disdain, so you just have to give yourself permission to wander, experiment, tweak, and evaluate for your own hardware, your own abilities and limits, and tastes.

---

### Post by SurfaceUnits on 2014-06-06
SOLYDX
[http://solydxk.com/](http://solydxk.com/)

---

### Post by SurfaceUnits on 2014-06-07
[http://www.makululinux.com/](http://www.makululinux.com/)

---

