---
title: "Idea: Ubuntu Install Advisor"
date: 2006-03-18
forum: The Cafe
---

### Post by SSTwinrova on 2006-03-18
As mentioned [here]("http://www.downloadsquad.com/2006/03/16/windows-performance-rating-says-your-pc-sucks/"), Vista will have an application that rates your computer on how well it will be able to run the OS. The other tool being provided is an "Upgrade Advisor" for XP saying how your specs should be increased in order to improve performance. Well, I think both of these ideas could be taken and made as an app for the Live CD called "Ubuntu Install Advisor" with the following characteristics:
[LIST]
[*]Places an icon on the desktop of the Live CD that will rate a computer based on CPU, HD Space, and RAM and also on compatibility (video card, wireless card, etc.)
[*]Make this same application available on the Windows side of the Live CD so people could see this rating before even booting into Ubuntu
[*]After rating is determined, suggest ways to improve performance
[/LIST]
If stuff like Xgl/Compiz ever makes it to main and becomes an installation option, this would be a neat way for people to immediately see if their specs would allow them to use the additional eye candy or if they would be better off just sticking with Xorg.

If there appears to be enough people interested in an idea list this (especially since Dapper+1 will supposedly hit around the same time as Vista), I'll start learning the "Linux way" to go about doing this (I've done programming in Java before, but I figure this is much more a Python-type application). Leave whatever feedback you wish  :)

---

### Post by briancurtin on 2006-03-18
other than seeing if XGL/Compiz will work, i dont see much of a reason for this.

ubuntu works on basically anything. i dont think hard drives are even made that are too small for an install, and you can run ubuntu on very low amounts of ram.

---

### Post by towsonu2003 on 2006-03-18
This is a nice idea to me. A tool that will tell you whether ubuntu's hardware recognition mechanism will be able to configure your hardware correctly, and to what degree. Debian has a very preliminary type of this here: [http://kmuto.jp/debian/hcl/index.cgi](http://kmuto.jp/debian/hcl/index.cgi)

---

### Post by s|k on 2006-03-18
Yeah, good idea. The program should also include how many attempts it will take to make sound work, how many lines written and hours spent on #ubuntu it will take to get their nVidia graphic driver working, estimated number of times they will kill gnome and have to restart from scratch. This program should be able to tell this by taking a look at how much spyware the user has installed on windows, how many times they've visted My Space, and how many short cuts are placed on their desktop. People with AOL installed will just get a big red X that says beneath in blinking bold letters: "DO NOT ATTEMPT."


;|

---

### Post by SSTwinrova on 2006-03-18
[QUOTE=briancurtin]ubuntu works on basically anything. i dont think hard drives are even made that are too small for an install, and you can run ubuntu on very low amounts of ram.[/QUOTE]
I agree, it's hardware detection is pretty good. I think this could solve/assist two situations however:

1. User has peripheral that for whatever reason is not supported (too obscure, no vendor support, etc.); this can notify them that "Hey, this may or may not work under Ubuntu, so if this is mission-critical for you, either hold off until support becomes available or look into alternatives which are already supported"

2. If this is a lower spec computer, it can say "Gnome/KDE may not be the best for you because of reasons X/Y/Z (although probably only RAM). Xfce is a lighter interface that will run better on your computer." That way, they can get the best Ubuntu experience immediately  :)

---

### Post by Stormy Eyes on 2006-03-18
[QUOTE=briancurtin]other than seeing if XGL/Compiz will work, i dont see much of a reason for this.

ubuntu works on basically anything. i dont think hard drives are even made that are too small for an install, and you can run ubuntu on very low amounts of ram.[/QUOTE]

I'm sure people with wireless network gear would appreciate knowing if they're going to have problems *before* they install. Also, GNOME works better if you've got more than 256MB of RAM; running a barebones Linux with X and a minimal window manager like Openbox needs 64MB plus swap.

---

### Post by towsonu2003 on 2006-03-18
[QUOTE=s|k]This program should be able to tell this by taking a look at how much spyware the user has installed on windows[/QUOTE]
a good idea emerging from that rant: check installed software and inform the user which programs are available in Linux for the same job.

---

### Post by Stormy Eyes on 2006-03-18
[QUOTE=towsonu2003]a good idea emerging from that rant: check installed software and inform the user which programs are available in Linux for the same job.[/QUOTE]

I think there are more important things to do, like **GETTING RID OF ESD!**

---

### Post by s|k on 2006-03-18
[QUOTE=Stormy Eyes]I think there are more important things to do, like **GETTING RID OF ESD!**[/QUOTE]
Amen to that.

---

### Post by SSTwinrova on 2006-03-18
[QUOTE=s|k]Yeah, good idea. The program should also include how many attempts it will take to make sound work, how many lines written and hours spent on #ubuntu it will take to get their nVidia graphic driver working, estimated number of times they will kill gnome and have to restart from scratch. This program should be able to tell this by taking a look at how much spyware the user has installed on windows, how many times they've visted My Space, and how many short cuts are placed on their desktop. People with AOL installed will just get a big red X that says beneath in blinking bold letters: "DO NOT ATTEMPT."[/QUOTE]
Lol, I love that last part about AOL  :rolleyes: 

You do point out a good fact, however, which is that regardless of however much work is put into trying to make everything work "out of the box", some people are bound to experience less than perfect installs, and the less technologically inclined they are, the lower the chance they will be able to solve their problems on their own. Then again, are these the kind of people who are going to try to install Ubuntu on their own anyway? (Not meant as derogatory, but a valid statement -- they'd probably get their techie friends to do it for them).

---

### Post by SSTwinrova on 2006-03-18
Wow, posts coming in faster than I can reply  :)

Stormy and tows, I like all of those ideas, especially for the version of this designed to be run inside Windows. Wireless (as I pointed out) was one of my initial considerations for this program, but I love the pointing out alternatives (and Firefox/OpenOffice are already there for people to experiment with). Looks like this is just the next logical step  ;)

---

### Post by towsonu2003 on 2006-03-18
what's esd?

---

### Post by SSTwinrova on 2006-03-18
[QUOTE=towsonu2003]what's esd?[/QUOTE]
Enhanced Sound Daemon? Enlightened Sound Daemon??

Some alternative to ALSA that apparently causes problems  :)

---

### Post by briancurtin on 2006-03-18
enlightened sound daemon

---

### Post by towsonu2003 on 2006-03-19
Hmm, I thought of that, but couldn't get the relation btw an installation advisor tool and removing esd from ubuntu. still can't :confused: 

I like this project. Hope it will come true... I'd love to check out systems I come accross with that tool.

---

### Post by SSTwinrova on 2006-03-19
[QUOTE=towsonu2003]Hmm, I thought of that, but couldn't get the relation btw an installation advisor tool and removing esd from ubuntu. still can't :confused:[/QUOTE]
Just my guess, but I think that ESD is a main cause of people having issues with sound. So, get rid of that, and you lose a bunch of the problems people might have (which would then in turn make one less thing for this to have to take into consideration).

---

