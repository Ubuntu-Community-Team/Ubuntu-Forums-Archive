---
title: "THIS will get folks looking at linux - Live Video Game DVD"
date: 2008-09-29
forum: The Cafe
---

### Post by earthpigg on 2008-09-29
just saw this on digg :)

[http://www.linuxhaxor.net/2008/09/28/live-dvd-for-linux-games/]("http://www.linuxhaxor.net/2008/09/28/live-dvd-for-linux-games/")

> The project live.linuX-gamers.net was founded with the idea to present Linux games at the Linuxtag exhibition in a novel way. A collection of games should be shown to directly run from DVD without the user in need to know about Linux or care about his system. After some intense brainstorming sessions the team decided to create and publish this DVD as a live distribution project. Thus an additional and very difficult problem had to be solved: The dvd should run on every x86 PC out there. 

> Hardware requirementsYour PC must at least meet these requirements: 
intel x86 architecture 
512 MB ram 
videocard with 3d acceleration 
The games on the DVD have different hardware requirements, have a look on their project page. But all of them are running fine on a testsystem with this hardware configuration: AMD 1800+, 512MB ram, ATI Radeon 8500 (comparable to nvidia gf3) 

im at work now, but intend to download as soon as i get off. anyone played around with it?

once 1.0 comes out, i'm thinknig we should petition saaaaaaaaaay PC Gamer (or other similar venues) to have **this **be the free dvd that comes with one of their issues....

---

### Post by tom66 on 2008-09-29
I'd wait till it was a bit more friendly. Have a nice flashy game-menu thing with screen shots and descriptions. Might look a bit better than just a command line or simple non-antialiased menu. Just my two cents.

---

### Post by fatality_uk on 2008-09-29
Linux gaming is getting stringer and stronger. ID are leading the way, but I hear many of the larger games publishers are getting a taste for the penguin.

---

### Post by ooobuntooo on 2008-09-29
As an employee of Atari Europe, I am going to try and get some of their games ported to Linux. Can't promise anything though

This is also worth a look: [http://xeiso.com/home/](http://xeiso.com/home/)

---

### Post by jpeddicord on 2008-09-29
Ooh, competition, I like that. Makes me want to work more on getting this thing developed.

(If you have no idea what I'm talking about, take a long stare at the big blatant image in my signature. :))


Though honestly, it looks like we're going in different directions. They want to make a Live CD with games on it. I want to be able to make a standardized open game platform. Ambitious, eh?

---

### Post by earthpigg on 2008-09-29
> **jacobmp92 said:**
>  Ambitious, eh?

yeah. from my noob perspective, it appears that their live dvd will do more for **linux**, while your project aspires to do more for **linux gaming** specifically.

---

### Post by Northsider on 2008-09-30
Ooo, pretty sweet, thanks for sharing with us!

---

### Post by ModdTaco on 2008-09-30
Xeiso looks pretty cool... what does it support?

---

### Post by wolfen69 on 2008-09-30
i've been seeding it for 3 days now. great disc.

---

### Post by Mr. Picklesworth on 2008-09-30
The one downside here is that the kernel is stuck at the same version forever, so hardware support going into the future is doomed. Thus, this scheme can't really be applied in the real world. It would be interesting if the same concept worked so that the computer's normal Linux kernel loads, along with some relevant services and information, then the boot process switches to loading everything from the game disk rather than the normal rootfs (on the hard drive).

No idea how kernels really work yet, so I can come up with overcomplicated solutions like that. Maybe something nifty could be done with unionfs :P

Perhaps the disk could package its own Linux kernel just in case (for Windows users), but have the fancy / overcomplicated way as its default operation, and a fun little incentive for using Linux.

Indeed, this kind of thing could single-handedly convert all the world's game developers over to Linux and totally rejuvinate PC games. Kudos to those who are making it happen!
...Having said that, lots of good developers are married to online distribution, so maybe not.



Oh, bootable game disk idea in general aside... nice compilation!

---

### Post by wolfen69 on 2008-09-30
> **Mr. Picklesworth said:**
> The one downside here is that the kernel is stuck at the same version forever, so hardware support going into the future is doomed. 

it says [here]("http://www.linux-gamers.net/modules/news/article.php?storyid=2483") that they do kernel and driver updates. :rolleyes:

---

### Post by earthpigg on 2008-09-30
> **Mr. Picklesworth said:**
> The one downside here is that the kernel is stuck at the same version forever, so hardware support going into the future is doomed.

at which point you simply burn a new dvd with the newest version :)

~hopefully~ they will have a very streamlined end user remastering process, so people can just pick whatever games and such they want.

> **wolfen69 said:**
> i've been seeding it for 3 days now. great disc.

Thanks :)

---

### Post by earthpigg on 2008-09-30
repost of what i posted on their forums:

> subj: Feedback from a Linux Noobcake

hello,

i migrated to linux pretty recently. someone tossed me an ubuntu cd and here i am. about the only thing i can do in the command line is "sudo apt-get install whatever" and follow well written how-to's. which, excluding gaming, is enough for me to prefer linux to windows.

i have very little experience playing 3d games and such on linux... which makes me very much like your typical windows user... which ~also~ makes me very much like about 90% of computer gamers out there.

so, first of all: i love what you folks are doing. this criticism is intended to be constructive. i want this project to succeed.

my primary gripe is screen resolution.

in about 1/2 the games, i was able to adjust the display so it takes up the whole screen. Open Arena sticks out as one that, no matter what options i tweaked, i could NOT. i tried all the different desktop resolution options, and i tried manually inputting my monitor's native resolution. in Warsow, i could and it was easy as pie.

i have no idea why. i have a feeling it is very easy to do, ~once you know how~.

so,

1. i suggest you make it easy to figure out how. really easy solution is to put the most common problems in text right on the desktop background image. <big text>Open Arena</big text> to make the game fill the screen click here, here, and here.

2. how do i make the games fill the whole screen? i dont want to play in a little box taking up 1/4 of my screen :)

Minor Gripes:

1. would it hurt to include a web browser and mIRC client with an icon on the right side of the panel on the bottom? that way i can come here and on IRC and seek tech support without having to restart every time. the browser should open directly to this forum, and mIRC to yalls IRC channel.

2. dual monitor support... i'd rather use my 22 inch than my laptop's display. this is not needed by the vast majority of people, hence it is minor.

~again~, i love what you folks are doing and this is intended to be constructive.

oh yeah:

where is volume control hidden?

i know there is a CLI command that you can use to adjust that... but i couldn't get to the web to look it up ;)

---

