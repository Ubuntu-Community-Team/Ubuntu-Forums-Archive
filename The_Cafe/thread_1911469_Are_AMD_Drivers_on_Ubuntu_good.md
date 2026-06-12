---
title: "Are AMD Drivers on Ubuntu good?"
date: 2012-01-18
forum: The Cafe
---

### Post by TheNerdAL on 2012-01-18
I'm getting a new graphics card and it's my first AMD card and I'm wondering how are drivers for Ubuntu?

---

### Post by wolfen69 on 2012-01-18
> **TheNerdAL said:**
> I'm getting a new graphics card and it's my first AMD card and I'm wondering how are drivers for Ubuntu?

Did you ask anyone's opinion, or check reviews first? <raises eyebrow like sheldon cooper>

---

### Post by TheNerdAL on 2012-01-18
> **wolfen69 said:**
> Did you ask anyone's opinion, or check reviews first? <raises eyebrow like sheldon cooper>

Checked reviews first.

---

### Post by wolfen69 on 2012-01-19
> **TheNerdAL said:**
> Checked reviews first.

Then it should work, right?

---

### Post by TheNerdAL on 2012-01-19
> **wolfen69 said:**
> Then it should work, right?

Yeah, just making sure. :P

---

### Post by 3Miro on 2012-01-19
Default driver is sufficient for work on a desktop. For laptop (battery life) or heavy desktop work, you will need the proprietary ATI drivers, but they should work well enough.

For gaming and really heavy work on Linux, Nvidia + proprietary drivers is still a better choice than ATI. Unless you want to play wine games, you should be fine.

PS: I am assuming that you are using at least 4xxx card or newer, older ATI models will have lots and lots of trouble.

---

### Post by false truths on 2012-01-19
I'm running an AMD graphics card right now on Ubuntu, and my advice is, if you plan to play a game at all, other than solitaire or sudoku, get yourself a Nvidia. The AMD proprietary Linux drivers SUCK. And when you use them and decide they suck too bad to use, you pretty much have to wipe your system to put the default drivers (which will NOT handle gaming), because the proprietary drivers integrate themselves that deeply into the system.

---

### Post by BlinkinCat on 2012-01-19
This bug presently exists for Gnome Shell with fglrx driver -

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/838577](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/838577)

---

### Post by TheNerdAL on 2012-01-19
> **false truths said:**
> I'm running an AMD graphics card right now on Ubuntu, and my advice is, if you plan to play a game at all, other than solitaire or sudoku, get yourself a Nvidia. The AMD proprietary Linux drivers SUCK. And when you use them and decide they suck too bad to use, you pretty much have to wipe your system to put the default drivers (which will NOT handle gaming), because the proprietary drivers integrate themselves that deeply into the system.

Too late. :( Already ordered the gpu.

---

### Post by TheNerdAL on 2012-01-19
This is my GPU that I'm getting btw: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814161387](http://www.newegg.com/Product/Product.aspx?Item=N82E16814161387)

I'm not planning to use Wine for gaming. Just Linux gaming like Minecraft, etc.

---

### Post by mips on 2012-01-19
> **TheNerdAL said:**
> Too late. :( Already ordered the gpu.

Cancel the order & change it.

---

### Post by Roasted on 2012-01-19
AMD still has some decent workings with Linux, but when I'm ordering stuff I tend to sway to the Nvidia side. I just feel like they have their act together a bit better than AMD. That's not to say your GPU won't work absolutely fine for you, I just find Nvidia to be less headache prone.

---

### Post by TheNerdAL on 2012-01-19
> **mips said:**
> Cancel the order & change it.

It's already been shipped. :(

I'm going to dualboot with Windows for my gaming though.

Edit: Trying to cancel it via live chat. Hopefully I can.

Edit 2: Need to wait for it to ship so I can return it. 

Idk, Should I just keep the AMD card and play games on Windows?

---

### Post by BlinkinCat on 2012-01-19
I am very happy using Gnome shell with open source driver for now  - may change to fglrx if a fix comes along.

If you do your gaming in Windows you should not have any problems - just be aware that fglrx driver may cause problems if you choose it and Gnome shell. I have not heard of any problems with Unity.

Good luck - :)

---

### Post by TheNerdAL on 2012-01-19
> **BlinkinCat said:**
> I am very happy using Gnome shell with open source driver for now  - may change to fglrx if a fix comes along.

If you do your gaming in Windows you should not have any problems - just be aware that fglrx driver may cause problems if you choose it and Gnome shell. I have not heard of any problems with Unity.

Good luck - :)

Yeah, I'm thinking of doing my gaming on Windows and using open source drivers for Gnome Shell. Does it run smoothly? And can it run Youtube videos well in fullscreen? 

Also, Question: Was fglrx working well before? Like could you play games well on it? I'm thinking of keeping the AMD GPU and waiting it out while playing games on Windows until fglrx gets better.

---

### Post by BlinkinCat on 2012-01-19
> **TheNerdAL said:**
> Yeah, I'm thinking of doing my gaming on Windows and using open source drivers for Gnome Shell. Does it run smoothly? And can it run Youtube videos well in fullscreen? 

Also, Question: Was fglrx working well before? Like could you play games well on it? I'm thinking of keeping the AMD GPU and waiting it out while playing games on Windows until fglrx gets better.

As far as my usage goes, I don't do any gaming - Full screen youtube runs perfectly and I am generally very happy using Gnome shell as my OS. My card is HD 5770 so I can't really comment on how yours would work, however I would be optimistic if I was you.
That is unless you pull the plug on your present order.

---

### Post by Buntumatic on 2012-01-19
Native Linux gaming might work.
However, for those stumbling across this thread looking for media center needs, even Intel with VA API leaves AMD in dust, not to mention nVidia VDPAU.

---

### Post by TheNerdAL on 2012-01-19
> **BlinkinCat said:**
> As far as my usage goes, I don't do any gaming - Full screen youtube runs perfectly and I am generally very happy using Gnome shell as my OS. My card is HD 5770 so I can't really comment on how yours would work, however I would be optimistic if I was you.
That is unless you pull the plug on your present order.

Nah, going to keep the gpu then and game on Windows. Only games I play on Linux is Minecraft and Assaultcube anyways. :P

---

### Post by mips on 2012-01-19
> **TheNerdAL said:**
> It's already been shipped. :(

I'm going to dualboot with Windows for my gaming though.

Edit: Trying to cancel it via live chat. Hopefully I can.

Edit 2: Need to wait for it to ship so I can return it. 

Idk, Should I just keep the AMD card and play games on Windows?

I also game in Windows but always stick with nvidia as their linux drivers are much better. I wont buy AMD until their drivers are on par in linux.

If I just used windows I would buy AMD in the blink of an eye.

---

### Post by TheNerdAL on 2012-01-19
> **mips said:**
> I also game in Windows but always stick with nvidia as their linux drivers are much better. I wont buy AMD until their drivers are on par in linux.

If I just used windows I would buy AMD in the blink of an eye.

I thought about it for a while, and I decided to get an nVidia card instead. Decided to get this card: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814130679](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130679)

If I was using Windows only, then I'd stick with AMD, but Linux is what I mainly use.

---

### Post by TheNerdAL on 2012-01-19
delete

---

### Post by mips on 2012-01-19
How does it compare to the AMD you picked performance wise?

---

### Post by TheNerdAL on 2012-01-19
> **mips said:**
> How does it compare to the AMD you picked performance wise?

It's way better. Runs Crysis 2 and it's on sale for $95 with rebate. There is only 1 left in stock! :O

---

### Post by Buntumatic on 2012-01-19
The trouble with Newegg is they ship too fast. :P
I made my last purchase Sunday night and it was in my car porch before Tuesday noon. And it wasn't rush delivery or something.

---

### Post by TheNerdAL on 2012-01-19
Decided to go for this one, is this a good card?: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814125409&RandomID=189401081991822420120119133035](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125409&RandomID=189401081991822420120119133035)

---

### Post by Buntumatic on 2012-01-19
Seems fine, but do not blame me if it blows up your box or does not  bring beer to your chair. Can do feature set C for multimedia, that's good. [http://en.wikipedia.org/wiki/Nvidia_PureVideo](http://en.wikipedia.org/wiki/Nvidia_PureVideo)

---

### Post by TheNerdAL on 2012-01-19
> **Buntumatic said:**
> Seems fine, but do not blame me if it blows up your box or does not  bring beer to your chair. Can do feature set C for multimedia, that's good. [http://en.wikipedia.org/wiki/Nvidia_PureVideo](http://en.wikipedia.org/wiki/Nvidia_PureVideo)

Blows up my box? :S Is a 500w PSU fine for that gpu?

---

### Post by Buntumatic on 2012-01-19
500 W should do, they require 400 W minimum. BTW, all units in metric system that are derived from names are uppercase, watt - W as a SI unit - is named after the Scottish engineer James Watt.

---

### Post by TheNerdAL on 2012-01-19
> **Buntumatic said:**
> 500 W should do, they require 400 W minimum. BTW, all units in metric system that are derived from names are uppercase, watt - W as a SI unit - is named after the Scottish engineer James Watt.

Thanks! Only thing I'm worried about now is if it will fit in my case well.

---

### Post by forrestcupp on 2012-01-19
> **TheNerdAL said:**
> I'm thinking of keeping the AMD GPU and waiting it out while playing games on Windows until fglrx gets better.We've been waiting on that for a long, long, long time. I don't think it's going to happen. Maybe the year after "The Year of the Desktop Linux". ;)

> **TheNerdAL said:**
> I thought about it for a while, and I decided to get an nVidia card instead. Decided to get this card: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814130679](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130679)

If I was using Windows only, then I'd stick with AMD, but Linux is what I mainly use.Great choice on switching your choice to nVidia. You'll be very glad you did. Of course you won't go through all of the AMD headaches to really know to be glad, though.

_The only reason_ to wrestle with AMD drivers is if you have a laptop or an onboard chip, and you just don't have any other choice. If you actually have a choice, there's no way you should choose AMD graphics for Linux.

---

### Post by Buntumatic on 2012-01-19
> **forrestcupp said:**
> Great choice on switching your choice to nVidia. You'll be very glad you did. [COLOR="RoyalBlue"]Of course you won't go through all of the AMD headaches to really know to be glad, though.
[/COLOR]
Well said! :guitar:

---

### Post by TheNerdAL on 2012-01-19
> **forrestcupp said:**
> We've been waiting on that for a long, long, long time. I don't think it's going to happen. Maybe the year after "The Year of the Desktop Linux". ;)


Guess I'll stick with nVidia all the time then until they drivers for Linux get better. Thanks!

---

### Post by Buntumatic on 2012-01-19
As a side note, I work for a casino. All newer slot machines are running Linux of course, unmatched reliability and flexibility. Newest ones are really demanding on graphics. Guess what graphics cards they use.

---

### Post by TheNerdAL on 2012-01-19
> **Buntumatic said:**
> As a side note, I work for a casino. All newer slot machines are running Linux of course, unmatched reliability and flexibility. Newest ones are really demanding on graphics. Guess what graphics cards they use.

nVidia?

---

### Post by Buntumatic on 2012-01-19
TheNerdAL, you just hit the jackpot. :D

---

### Post by mips on 2012-01-20
> **TheNerdAL said:**
> Decided to go for this one, is this a good card?: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814125409&RandomID=189401081991822420120119133035](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125409&RandomID=189401081991822420120119133035)

Gigabyte is a good brand. Good pick.

If you ever want to quickly compare specs/performance between two cards have a look at [http://www.gpureview.com/show_cards.php](http://www.gpureview.com/show_cards.php) for more info read in depth reviews.

---

### Post by mips on 2012-01-20
> **TheNerdAL said:**
> Thanks! Only thing I'm worried about now is if it will fit in my case well.

Dimensions (LxHxW):
239mm x 138mm x 41mm (9.4" x 5.4" x 1.6")

---

### Post by DeadSuperHero on 2012-01-20
My laptop has an ATI Vision Mobility card in it, and I'd just like to say: the FOSS Radeon driver that ships with Oneric with it is fantastic. Unity and Gnome-Shell are both pretty fast in it, and the whole system feels very responsive.

The only downside with the Radeon driver is Wine gaming. Specifically, games that work with the proprietary driver sometimes won't work with the free one. (A prime example is anything made with Adventure Game Studio, in my situation. When I click out of a game window, the game turns into a black screen and that effect lingers when I start up new games for some reason.

You could try the proprietary driver. KDE works well on it, but I don't particularly like the feel of KDE most of the time. Unity runs horribly on it, though, and Gnome Shell barely works at all (lots of broken visuals in Clutter and Mutter libraries)

So, it's a toss-up. Like I said, FOSS driver is great, save for the Wine problems. Hopefully that situation will improve in the future.

---

### Post by Perfect Storm on 2012-01-20
Also +1 for Nvidia card. Nvidia vdpau is genius when watching movies and alike.

---

### Post by forrestcupp on 2012-01-20
> **TheNerdAL said:**
> Guess I'll stick with nVidia all the time then until they drivers for Linux get better. Thanks!

My thoughts have always been that even if I use Windows or a console most of the time for gaming, I still don't want to feel like my Linux experience is limited, especially when I have the option for it to not be limited.

---

### Post by TheNerdAL on 2012-01-20
> **mips said:**
> Dimensions (LxHxW):
239mm x 138mm x 41mm (9.4" x 5.4" x 1.6")

Will it fit in this case? [http://www.newegg.com/Product/Product.aspx?Item=N82E16811147099](http://www.newegg.com/Product/Product.aspx?Item=N82E16811147099)

I bought it because it was cheap and I needed a new case fast because my old one was OEM and I couldn't connect the connectors to the motherboard since it was proprietary. 

Don't worry, I'm not using the case's PSU.

---

### Post by Chame_Wizard on 2012-01-20
I have some problems atm,can't install fglrx.

---

### Post by mips on 2012-01-20
> **TheNerdAL said:**
> Will it fit in this case? [http://www.newegg.com/Product/Product.aspx?Item=N82E16811147099](http://www.newegg.com/Product/Product.aspx?Item=N82E16811147099)

I bought it because it was cheap and I needed a new case fast because my old one was OEM and I couldn't connect the connectors to the motherboard since it was proprietary. 

Don't worry, I'm not using the case's PSU.

That case is extremely small seing it's a microatx case. I have no idea if it will fit. best to check the manufacturers site.

---

### Post by TheNerdAL on 2012-01-20
> **mips said:**
> That case is extremely small seing it's a microatx case. I have no idea if it will fit. best to check the manufacturers site.

The dimensions of the case are bigger than the gpu. Is that good enough?

---

### Post by silverhaze06 on 2012-01-20
If you're having issues with the drivers, I would suggest reading this thread to get things working better. I've tried it and things are running smoother for me. [http://ubuntuforums.org/showthread.php?t=1857911]("http://ubuntuforums.org/showthread.php?t=1857911")

---

