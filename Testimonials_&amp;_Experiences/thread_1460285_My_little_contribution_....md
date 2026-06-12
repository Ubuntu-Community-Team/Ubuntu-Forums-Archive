---
title: "My little contribution ..."
date: 2010-04-22
forum: Testimonials &amp; Experiences
---

### Post by elarrarte on 2010-04-22
Hi people ... first, sorry about my little English. I m from Argentina !

I  want to tell you my experience with Ubuntu and Linux in general ... I m  very frustrated about it.
I started using Linux with my studies  "software engineer" a few years ago. I started using it in my own home  server ... Debian ... no problems at all. The only thing i don t like is  that Debian doesn t tell u when a new release is coming ... not so good  for commercial environments or large deployments ... but WTF? It s free  !!! =D

I started to put Linux in my customers servers ... they  worked good !

Then, I wanted to replace my Windows desktop with  Linux ... I don t like Debian for a desktop, so I started to search for a  more appropiate distribution. A friend told me about Ubuntu and I gave  it a try ... 7.04 ... very good distro ... but I had some problems with  my laptop hardware so I decided to switch to a more Linux compatible  hardware laptop. I bought a Dell pre-installed with Ubuntu 7.04 LTS ...  good ... without problems!

8.04 LTS ... problems with wifi and  sound / hibernation ... it s so strange ... a newer version  (evolution?).
With a few tweaks ... things got usable again.

8.10,  9.04, 9.10 ... I see Ubuntu is working hard to boot faster, to look  nicer, but what about stability?
My Dell (with a good quality and  compatible Intel hardware) runs like a crap! .... but boots in 10  seconds!
Intel video driver problems ... DVD burning problems even  with the default Ubuntu software brasero !!!!

10.04 ... the same  thing ... basic applications like "managing users and groups" dosen t  work anymore !!!
I created a user for my girldfriend with no  permissions ... she can still using the CDROM, USB ... :(

So  ... I think that kind of issues exist because of the direction  opensource is taking nowadays ... instead of improve a proyect and work  harder on it ... we create a new proyect and a new proyect and a new  proyect ... like a new distro, new distro, new distro .... 
It s the  case of OSS (Open Sound System) ... ALSA (Advanced Linux Sound  Architecture) ... now Pulse Audio ... i d prefer an evolution of OSS  with a cleaner code than a new Pulse Audio proyect ... my Linux desktop  ran more stable OSS days than now !

I did some proyects using  Linux and opensource software in my work ... I had to recompile my  software between Ubuntu releases ... too many changes between them !!!  ... now you have DEVFS, then you have the new UDEV ... now GRUB then  GRUB2 with the new configuration files ... ouch !!!

So (in my own  laptop) I m still using opensource software like openoffice, dia, vlc,  firefox, eclipse, mysql, java ... but in a more stable platform like  Windows ... yes, I must admit that ... and it took ages for me to accept  it !!! ... I can t spend hours in front of my computer reading bugs in  Touchpad or looking for a howto to get the newer Java running ...  anymore !

So ... I want Linux to be a great OS ... but I think  this is not the best way to get it!
I think the Linux community has  to work together ... I not so happy by telling you my experience ... I  just want to help ... in my country a lot of people is buying Windows7  Starter Edition for 50 bucks ... (my grandma too) ... and I must admit  that is a great OS, easy & fast, friendly ... and a rock solid  compared to my PC at work running Ubuntu 8.04/10.04 ... 

Look  this video
[http://www.youtube.com/watch?v=YoYL4R3Te2s](http://www.youtube.com/watch?v=YoYL4R3Te2s)

Let me  know what you think about the Linux future ... thanks in advance !!!

---

### Post by leclerc65 on 2010-04-22
Talking about speed , you must have done something wrong - because all my PC, and my relatives' PC run much faster in Linux than Windows , except one. On that one I have XP , without Firewall, Anti-virus , anti adware , anti... whatever. Yes it's suicidal to run Windows that way, but it's intentional because I use it as a ... media control center.:P

---

### Post by Jazzy_Jeff on 2010-04-22
For stability I would recommend staying with the LTS versions of Ubuntu. 10.04 is due out shortly. You might want to wait a little on it until the bugs are worked out.

---

### Post by elarrarte on 2010-04-22
Well, i don t understand what u mean when u say "much faster" ... do u mean booting??? --- I used to say those things when I was a Linux fan ... but lets accept it ... it s not important to me to boot 5 sec faster than windows ... i d prefer more stability and boot slowly ... stability prior to speed !
If we talk about the applications I use in general ... let me say that even openoffice, eclipse, netbeans run much faster and look nicer (better fonts) on windows than on linux ... dia prints my diagrams better because on windows u have better printer drivers ... and firefox ... i hate saying that ... but ... try to watch a full HD video from youtube in fullscreen ... your CPU will be at 100% and losing some frames ... on windows is less than 30% ... so i don t understand ur speed comparison at all ... i tried latest intel drivers, compiling kernel ... nothing works ... video speed in Linux is slow ... even on drawing the windows u can see a bit of lag.

Anyways ... this post is not for talking about Linux vs Windows Speed ... I dont care about that ... i know Linux is a colaborative & community OS and could have some issues ... I understand programmers have their life too ... I m only trying to say that (for me) ... they re taking the wrong way on the last years ...

Let me give a simple example ... proxy configuration ... in Ubuntu you must set ur proxy configuration in many places ... why not to set a standard configuration file like /etc/proxy.conf and all applications read that file ... even better /etc/system/proxy.xml and a simple library with a simple API that can read that file using one the good standard xml libraries around there ... that way u call a simple function within ur apps and u can get those values without any effort. =D
Instead of that ... we have many config files and each app writes his config in their own way and wastes a lot of time writing functions to read their config files.
XML should be a standard nowadays for config files on the entire system ...
Or the case of fonts ... defoma? fontconfig? ohhhh ... lets put all fonts in a directory and lets make some standard libraries so we can all take advantage of all fonts ... openoffice shows 100 fonts in my system ... eclipse shows me only 70 and looks ugly? :confused:

Look at windows ... u can call a simple API from ur apps to read a value from the registry ... that s simple, easy, fast and requires no effort ... fonts are in a default directory and all apps could take advantage of all fonts on the system.

That kinda things ll help us having a better OS ... not booting speed or to include the latest compiz with their flying windows in our distro ... or change our GTK theme to look different and modern!

If we have a standard API and a cleaner system ... commercial companies ll begin to do more things for linux and they ll do it better ... but in this scenario we must accept that it s not so cool to write a linux app and u could have to rebuild or remake some part of ur code just because a proyect dissapear or config files/libraries change all the time ...

I know that kinda things are toooo difficult to set in a community proyect, but I think Ubuntu is one of the most important Linux distros nowadays and should begin creating those things instead of waste their resources in compiz, 10 sec distro-boot ....

Another example ... Debian and their Firefox icon issue ... firefox icon have another licensing method ... and? ... they create a parallel IceWeasel or something ... that kinda things suck ... thats why I decided no to use Debian anymore ... that way Debian ll have their own packages for all apps?

So ... i u want to write a linux app ...
gnome? kde? xfce? lxde?
devfs? udev?
/proc? /sys?
oss? alsa? pulse?
kernel 2.4? 2.6? 2.6.18? 2.6.19? 2.6.20? ......................... 2.6.32?

I ll be very proud to get community feedfack on this subject ... :P

---

### Post by Tamlynmac on 2010-04-23
> elarrarte

Thank you for sharing your experiences. Since this isn't a debating section of the forum (see T&E guidelines), I will not comment on your opinions.

But rather wish you Good Luck with which ever OS meets with your expectations. It's been my experience that Ubuntu/Linux/FOSS isn't for everyone.

---

### Post by armandh on 2010-04-23
the best of any Ubuntu is the LTS a few months after release
my wife's laptop is 8.04 and works way faster than vista+AV

the OPs english is better than most MS forign customer service.

---

### Post by elarrarte on 2010-04-23
It s my first thread here ... so I really want to know where I could post this thread for people let me know their opinions ... I really want to make a debate and listen what people think about it.

Please let me know what section could I use !!!

Thanks !!

---

### Post by elarrarte on 2010-04-23
> **armandh said:**
> the best of any Ubuntu is the LTS a few months after release
my wife's laptop is 8.04 and works way faster than vista+AV

the OPs english is better than most MS forign customer service.

Please man ... read the entire thread before post anything ...

Again ... this is not a Windows vs Linux speed thread ... are linux guys gettting close that you could not see more than you want?

Please guys ... I really want to know another serius opinions ... it s not valid to say "my linux is faster than vista+AV" ... what are we saying with that? --------> nothing

Windows Vista sucks ... it was an experiment !

My girldfriend Windows XP machine with AV is really much much much faster than my Ubuntu 8.04 and my grandma Windows7 is much much faster tooooo ... but it s not the topic here !!!!

I am worry about the direction of linux distros are taking ... that s all !

Bye !

---

