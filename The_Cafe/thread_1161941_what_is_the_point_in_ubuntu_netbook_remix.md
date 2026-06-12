---
title: "what is the point in ubuntu netbook remix?"
date: 2009-05-17
forum: The Cafe
---

### Post by NTpspE on 2009-05-17
Hi all,
Just wondering, im interested to know, what are the actual advantages of having UNR on a netbook instead of normal ubuntu?
To me it just looks like a mobile phone style interface, on a computer... which would put me down serverely :(

Is there any point to it over ubuntu?

---

### Post by issih on 2009-05-17
Not actually played with it myself, but the point would seem to be to optimise the OS for use on a small screen, so yes it will borrow some ideas from the handheld device arena and some from normal OS metaphors. It is a hybrid designed for use on machines that do indeed fall between a laptop and a mobile phone.

The small relatively low resolution screen, relatively cramped keyboard and small trackpad all mean that full blown OS behaviour is not enitely ideal, and changing the interface to minimise the need for precise positioning of the pointer and increase the font size/decrease high resolution usage seems a sensible compromise.

Hope that helps

---

### Post by NTpspE on 2009-05-17
I see where you are coming from, but wouldn't it make sense to just make ubuntu's fonts smaller, and keep it the same OS?
I mean, my netbook (advent 4221) has fully blown XP (boo) on it. I got used to the size of the keyboard, and as for mouse movement, the pad seems fine. 
I cant really think why anyone would want to use netbook remix as an operating system on a machine, instead of regular ubuntu

---

### Post by ugm6hr on 2009-05-17
> **NTpspE said:**
> To me it just looks like a mobile phone style interface, on a computer... 
That's it. Simplicity.  All the functions are still there though.  It is a question of whether you view the netbook as a computer or as an appliance.  Ease of use is more important in the latter.

Additionally, it comes with maximus which ensures all windows are opened full size to make full use of the small screen area.  It also shrinks Gnome to one panel only.

> which would put me down serverely :(
Not everyone agrees.  But I do; I installed NBR and then switched back to the standard interface.

---

### Post by NTpspE on 2009-05-17
I suppose maybe it's allright for people who want an interface like that, or for low spec machines. 
Ah well, i heard it's also bad to boot from USB all the time, as the constant too-and-fro of data can break the usb drive.
I'll stick with ubuntu for now :D as it does all i need, i only have windows on my netbook for office, but (usual tale) i got a virus on it and had to re-install XP... loosing office...
another reason why i love ubuntu so much :D

---

### Post by Fingers &amp; Thumbs on 2009-05-17
I use NBR on my Tosh NB100, and I find the tweaked interface useful, but I sure wouldn't want it on my bigger machine.

 I remember reading somewhere before I installed it, that it is optimised for the atom chip also.

 You don't have to boot from usb all the time, it can be installed onto your HD as I have done.

---

### Post by V-600 on 2009-05-17
I have the netbook remix on my aspire one. I prefer the remix desktop it to the standard gnome look one.

My netbook just that, it wasn't bought with the intention of being a laptop or second computer. I use it mainly for surfing the web and chatting to friends.The small screen means that far from dropping the font size, I have upped firefox's default to make websites a bit easier to view.

Everything that gives me more usable screen area is a welcome addition. Added to that, at some point I intend to fit a touch screen to the aspire one, so having large icons in a default favourite's section will be a huge benefit over navigating a smaller menu system.

---

### Post by NTpspE on 2009-05-17
good point, gnome would be fiddly with a touch screen. 
Now that you mention it, why isn't it called "ubuntu touch"? 
Haha that would be a better name, and better reason for the different desktop.
I didn't know you could fit touch screens into laptops, unless you buy one... might research into that :p

---

### Post by jparkerri on 2009-05-17
I made the mistake of loading the UNR on top of ubuntu 9.04 installed with wubi.  The desktop was confused and displayed both the old gnome and new UNR and flashed back and forth.  The reason I was looking for the UNR was because I'm running on a Lenovo s10 and some dialogs extend below the 1024v600 screen and I haven't been successful setting up a virtual screen resolution.  If I could do that, I'd stick with gnome.  Has anyone been able to set up a virtual 1024x768 on a Lenovo S10 or ther netbook?

---

### Post by snowpine on 2009-05-17
> **jparkerri said:**
> I made the mistake of loading the UNR on top of ubuntu 9.04 installed with wubi.  The desktop was confused and displayed both the old gnome and new UNR and flashed back and forth.  The reason I was looking for the UNR was because I'm running on a Lenovo s10 and some dialogs extend below the 1024v600 screen and I haven't been successful setting up a virtual screen resolution.  If I could do that, I'd stick with gnome.  Has anyone been able to set up a virtual 1024x768 on a Lenovo S10 or ther netbook?

UNR will not help 1024x768 dialogs fit onto a 1024x600 screen.

What I do is to hold down the Alt key, click anywhere on the window, and drag it around so I can see the part I need.

---

### Post by jparkerri on 2009-05-17
After experimenting with xrandr, I was able to set the desktop size to 1024x1024 on my Lenovo S10 netbook by using the following command line that I modified from one found at the bottom of the man page.

xrandr --fb 1024x1024 --output LVDS --scale 1.0x1.0 --output LVDS --pos 0x0 --panning 1024x1024+0+0/1024x1024+0+0/64/64/64/64

I can't make it any larger than the size described as maximum when you run:
xrandr -q.

At least I can now see the bottom of any dialogs displayed by just moving the cursor to the bottom edge.

---

### Post by TjankMjaster on 2009-05-18
> **ugm6hr said:**
> Not everyone agrees.  But I do; I installed NBR and then switched back to the standard interface.


ugm6hr,  you running standard jaunty on a netbook??  which netbook if so?  
________________________________


I've been shopping netbooks for my next mobile device,.. I'm liking the Ideapad, but to be honest,.. it's the only one I've seen in person.   Anyone have other suggests that run Ubuntu pretty seamlessly??

(currently running Mint6 on my presario M2000)

---

### Post by V-600 on 2009-05-18
The aspire one works with only a few tweeks to get the SD card slot working

---

### Post by jcoles on 2009-05-18
The netbook interface is clearly meant to deal with the severely limited screen space. That's why everything runs full screen, which might seem annoyingly dumbed-down at first. Although the display is quite sharp, the tiny fonts require an up-to-date glasses prescription! 

It would be good to have some documentation explaining all of the new GUI conventions. How can users simply discover everything that they need to know? The Alt-drag trick for oversize dialog boxes rescues several applications that would otherwise be unusable.

I hope the forum moderators will create a separate section for Netbook Remix. It will certainly have many unique problems.

---

### Post by jespdj on 2009-05-18
I like Netbook Remix on my Dell Mini 9.

See this: [Ubuntu Netbook Remix 9.04 hands-on](http://tuxradar.com/content/ubuntu-netbook-remix-904-hands)

---

### Post by NTpspE on 2009-05-18
> **jespdj said:**
> I like Netbook Remix on my Dell Mini 9.
[]("http://tuxradar.com/content/ubuntu-netbook-remix-904-hands")

You say you like it... but why?
What do you like about it over standard ubuntu?

---

