---
title: "Would this setup work for my work needs?"
date: 2016-03-04
forum: Ubuntu, Linux and OS Chat
---

### Post by UDroidie626 on 2016-03-04
Firstly allow me to apologize if this is in the wrong section of the  forum.

Anyways so here is my situation.
I am an IT Engineer,  we are given Windows laptops, but they suck,  battery life is way too short for our work, they are heavy to lumber around and hold  in one hand, they run  Windows, they don't have esata connections  (Would rather have native  esata over serial), and outside of Office and  IE we don't really use  much software that is Windows specific.

So one solution is this, I  have a X220 with a 9 cell battery in (Will be  getting a slice soon!), in Linux I am sure I can get  around 8hr of  battery life, maybe even more.
I want to keep my work  laptop in the office on which ever site I am  working at, when I go away  from the office to fix something I would  take my X220 (Its lighter, more  battery, better for typing on), plus  the only reason I would need the  work laptop is Citrix server access.
SO from a Linux end I would have  the system heavily secured,  GRSecurity, Encryption, SELinux/Apparmor, a  really solid system  (Although we can mostly agree Linux has this by  default over Windows).
I would remote into my Windows laptop when I  need Citrix server (Our  servers check OS versions and patches before  allowing login and there  is no known way around it with anything other  than W7), can we use something similar to RDP (Pref encrypted) I don't want to use VNC or something like that if I can avoid it.

Another solution would be to have a VM with an image of my work laptop on it, advantage of this would be snapshotting, our laptops can be unpredictable (As laptops can) and they may BSOD or something else.
I would use Virtualbox with this and possibly seamless mode (That is the one similar to unity in VMWare?) so I can simply run what I need from Windows in a windows as if it ran directly from the Linux OS.

My question is this, which solution do you recommend? on top of what distro, I know its in the ubuntu forums but, these forums seem less biased, Of course for this I need a stable distro along the lines of Debian/CentOS/Ubuntu LTS/SLED or something, personally for work I don't mind paying SLEDs entry price.

Suggestions?

Thanks!

---

### Post by grahammechanical on 2016-03-04
You are proposing solutions but you have not told us what the problems are that those solutions are to solve? How can we make that choice for you? Of, course if you have already worked out ways of doing things in Linux (and it seems that you have) you should use a Ubuntu LTS version. What do you expect from us?

A lot will depend on the hardware specification of that machine as to which of the Ubuntu family of distributions you can install. But Linux is Linux. If some method of working can be done in one Linux distribution, then it can also be done in some other Linux distributions.

There are some fundamental differences between those 4 distributions that you have mentioned. Distributions exists because the developers want differences. It gives users choice. 

I know the main difference between Debian & Ubuntu. And you have just informed me of a major difference between Ubuntu and SLED that would stop me from installing SLED. I know nothing of CentOS.

I have already made my choice and this is not my choice to make. 

Regards

---

### Post by Bucky Ball on 2016-03-04
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Seriously? I would get a big, blank piece of paper and a pencil and eraser and get to work drawing a [mind-map]("https://en.wikipedia.org/wiki/Mind_map") of what you need to do and the elements you are going to need to do it and see what works best.

Use different elements in different shaped boxes: requirements in circles, hardware in squares, operating systems in triangles. Whatever suits. In truth, this approach sounds like it could help you get all this together on some kind of conceptual framework. It sometimes helps when you have it out in front of you rather than in your head, and it looks like this is one of those times. 

Attach a plan. Might make it clearer for all of us. Just a thought. :)

---

