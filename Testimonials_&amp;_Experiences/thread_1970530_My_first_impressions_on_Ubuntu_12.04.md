---
title: "My first impressions on Ubuntu 12.04"
date: 2012-05-01
forum: Testimonials &amp; Experiences
---

### Post by luvr on 2012-05-01
A few of my observations and notes on Ubuntu 12.04--in no particular order.

**LightDM** is great. I particularly appreciate how easy it is to automatically activate NumLock (with the NumLock LED showing the correct status) even before logging in: Just install the *"numlockx"* package and add the following line to *"/etc/lightdm/lightdm.conf"*:
```
greeter-setup-script=/usr/bin/numlockx on
```
A few other lines that you can add to the file and that I found particularly useful:
[LIST][*]To hide the user list:
```
greeter-hide-users=true
```[/LIST]
[LIST][*]To disable the guest session:
```
allow-guest=false
```[/LIST]
One little inconvenience with the **Dash**: When I open Dash Home, the screen contents under it is *blurred,* which I find somewhat uncomfortable. Is there a way to *dim* the background contents instead?

Something about **Unity** that I cannot seem to figure out without help: When I open *Rhythmbox* and let it play some music, I can close its window and it will keep running (the music continues). That's all fine, but how am I supposed to reopen its window?

Then something about the **GNOME classic** panel: When I add the Clock applet to it, the text (i.e., date and time) is dimmed so much that it's hardly readable. Is there any way to make the text appear brighter?

I must say I appreciate the presence of the **GNOME Classic** option; so far, I cannot really see the advantage that Unity is supposed to deliver--at least not for me, on a traditional desktop type of system.

I'm also no fan of the global menu; I have never even liked it on the Mac either, so I'm quite happy that Ubuntu lets me remove it with relative ease.

Generally speaking, Ubuntu 12.04 looks OK so far. I have recently begun to search for a replacement for Ubuntu 10.04 (which currently remains my main system), and Ubuntu 12.04 seems a more likely candidate than I had thought. Not sure about Unity, though; I'll play a little more with it, but it seems to me like I will end up with GNOME Classic instead (assuming I stick with Ubuntu in the first place).

---

### Post by ubuntu27 on 2012-05-04
> **luvr said:**
> 
Something about **Unity** that I cannot seem to figure out without help: When I open *Rhythmbox* and let it play some music, I can close its window and it will keep running (the music continues). That's all fine, but how am I supposed to reopen its window?


Rythmbox is running in the background, and you can open it from the 
**Volume Indicator** which is on the upper right hand corner. 

The volume indicator should be next to the Date/Time

[What's the right terminology for Unity's UI elements?]("http://askubuntu.com/questions/10228/whats-the-right-terminology-for-unitys-ui-elements")

---

### Post by luvr on 2012-05-06
> **ubuntu27 said:**
> Rythmbox is running in the background, and you can open it from the **Volume Indicator** which is on the upper right hand corner.
Thanks... I had noticed the presence of a *Rhythmbox* icon on the ***Volume Indicator,*** but I hadn't really considered *doing* anything with it.

---

### Post by luvr on 2012-05-06
Sigh... I'm afraid I'll have to give up on Ubuntu 12.04 for now.

No hard feelings, but no matter how hard I try, I cannot seem to get myself to like Unity. If *you **do*** like it--more power to you, but it simply isn't my cup of tea.

I would have liked to switch to GNOME Classic instead, but that presents me with its own set of problems.
For instance, the menu text in the top panel is too dark to be comfortably readable; the same is true of the text in the clock applet. The *Weather* applet, on the other hand, displays fine.
The ***<Alt>+<Tab>*** keys no longer work to switch between windows; *very* inconvenient, especially since I cannot seem to find a new key combination to perform this action.
To reconfigure the panel, I have to hold down ***<Option>+<Alt>*** while I press the right mouse button. Mind you, I could get used to this, so I wouldn't even have mentioned it if this were the only surprise that I experienced with GNOME Classic (I might even have found it a good idea in the end), but now it just adds to the frustration.

I will keep Ubuntu 10.04 as my main desktop system for now. I did make a backup of my Ubuntu 12.04 system partition, so I can easily restore it without having to reinstall from scratch; perhaps, in a few months' time, after testing a few other options, I may decide that Ubuntu is the least frustrating option after all... :-? And, perhaps, it may have evolved by then, or some smart people may have found all the answers to the questions that keep bugging me at this time.

Having said that, whether or not I ever come back, I will keep fond memories of Ubuntu; it was the Linux distribution that actually enabled me to dump Windows completely. Not every Ubuntu release worked well for me, but I found 10.04 in particular simply great.

---

### Post by shuttleworthwannabe on 2012-05-06
@luvr--how about Gnome Shell in Ubuntu--works like a charm, imho. Give it a try.

---

### Post by Myrddin Emrys on 2012-05-06
> **luvr said:**
> I would have liked to switch to GNOME Classic instead, but that presents me with its own set of problems.

You might want to give Xfce a shot instead, but if you want a complete Gnome 2 experience that works exactly the way it does in 10.04, try MATE:

[http://www.howtogeek.com/110052/how-to-install-the-mate-desktop-go-back-to-gnome-2-on-ubuntu/](http://www.howtogeek.com/110052/how-to-install-the-mate-desktop-go-back-to-gnome-2-on-ubuntu/)

[http://mate-desktop.org/install/#ubuntu](http://mate-desktop.org/install/#ubuntu)

---

### Post by luvr on 2012-05-06
> **Myrddin Emrys said:**
> You might want to give Xfce a shot instead, but if you want a complete Gnome 2 experience that works exactly the way it does in 10.04, try MATE
Did you read my mind??? :confused:

I have already given XFCE a test run under Debian 6.0, and my first impressions are fairly positive indeed. It takes a bit of work to find out how to customise it to my wishes, but everything that I wanted to do turned out to be doable, and not particularly complicated once I discovered how to approach the question.

Furthermore, I have just downloaded Linux Mint Debian Edition 201204 (both the *"MATE + Cinnamon"* and the *"XFCE"* releases), and I'm planning on trying out MATE, and perhaps also Cinnamon, next. (By the way, even though I have no immediate plans to try out the *XFCE* release, I did the downloads through BitTorrent, so I decided to help seed the torrents for both releases, for both the 32-bit and the 64-bit architectures. In fact, I'm also seeding Ubuntu 12.04 desktop, server and alternate images for both architectures.)

Anyway, thank you so much for the links about installing MATE under Ubuntu; I'll keep them handy in case I decide that I like MATE, but prefer Ubuntu over Mint.

---

### Post by luvr on 2012-05-06
> **shuttleworthwannabe said:**
> how about Gnome Shell in Ubuntu
Admittedly, I haven't really paid much attention to GNOME Shell so far--just a quick look.

After my experience with Unity, GNOME Shell didn't seem all that convincing to me; it gave me the feeling that, just as with Unity, I could *try* and like it, but would likely be unsuccessful. Perhaps after I try MATE for a while, with Unity no longer this fresh in memory, I may be in a position to try something new with a more open mind again.

---

### Post by Tamlynmac on 2012-05-07
> luvr

If you like XFCE the you might wish to try [Xubuntu]("http://xubuntu.org/"). I've found it rock stable and simple to configure.

Good Luck

---

