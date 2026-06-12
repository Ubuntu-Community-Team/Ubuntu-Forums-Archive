---
title: "A decision on hardware: ATI or nVidia?"
date: 2006-10-20
forum: The Cafe
---

### Post by chaosgeisterchen on 2006-10-20
Hi folks,

at the moment I'm thinking hard about changing the GPU of my box in order to use **Beryl** in future - and I dunnot want to have reoccuring performance lacks as well as other problems just like that one. 

At the moment my box is containing a ATI Radon X300 PCIE graphics card but I think about replacing it with an nVidia one as I heard that the drivers would be better.

The question is: Are the R300-opensource-drivers capable of bringing me enough power to let my box using me Beryl without problems or should I go for a nVidia board in order to achieve that?

I am thinking about using a nVidia GeForce 6200 as I think this board is enough to run Beryl.

Opinions please or, even better, clear answers.

Thanks in advance,

cg

---

### Post by dbott67 on 2006-10-20
From everything that I've read, nVidia is the way to go.

I've got a laptop with an ATI Radeon x1400 and Beryl looks and runs great.  I had a bit of an issue getting rid of the Mesa drivers, but I found the answer in the forums and now I'm a very happy camper.  My ATI setup walk-through is here:

[http://www.ubuntuforums.org/showthread.php?t=274915](http://www.ubuntuforums.org/showthread.php?t=274915)

-Dave

---

### Post by jsandys on 2006-10-20
I'm a Ubuntu newbie, I just built a computer for my father in law.  I originally used the ATI 9600 64meg (R300).  It ran FlightGear at about 15fps with the mesa drivers and 30fps with the fglxr drivers, both the Ubuntu distribution and ATI's.  But I wanted to display on a TV, and spent two weeks trying to configure the system, but the opnegl and TV out seem incompatable on the ATI, either 1fps with FlightGear or bad dvd playback.  

I switched to an nVidia FX5500 and in a day had dvd's playing and 45+fps on FlightGear, on the TV and the Monitor.  I'll use the ATI 9600 on another computer without the TV.

What is Beryl.

---

### Post by NoTiG on 2006-10-20
well if you plan on gaming go nvidia.... otherwise The open source ATI drivers are about 1/4th as powerful as their windows counter parts. But for something like beryl.... that is actually probably enough. In a way it might even be easier to use ATI opensource drivers because they are installed by default, and will not break your distro when you upgrade... there is also some rumor about ATI drivers going open source or something in the future which also seems interesting.

I would say nvidia though, just to support them because they have been more pro linux

---

### Post by chaosgeisterchen on 2006-10-20
As the R300 drivers are about 1/4 as powerful as the catalyst under Windows, how is the relation concerning nVidia?

Is it worth spending 35 Euros on that :) ?

---

### Post by teet on 2006-10-20
> **chaosgeisterchen said:**
> Hi folks,

at the moment I'm thinking hard about changing the GPU of my box in order to use **Beryl** in future - and I dunnot want to have reoccuring performance lacks as well as other problems just like that one. 

At the moment my box is containing a ATI Radon X300 PCIE graphics card but I think about replacing it with an nVidia one as I heard that the drivers would be better.

The question is: Are the R300-opensource-drivers capable of bringing me enough power to let my box using me Beryl without problems or should I go for a nVidia board in order to achieve that?

I am thinking about using a nVidia GeForce 6200 as I think this board is enough to run Beryl.

Opinions please or, even better, clear answers.

Thanks in advance,

cg

Save yourself the hassle...go with Nvidia.

I have a Nvidia Geforce 6200 in my (Celeron D 3.06 Ghz, 512 mb DDR 400 Ram, 7200 RPM Western Digital PATA hard drive) machine.  I tried out Beryl a few weeks ago and it ran fine.

The 6200 is a very cheap card, but you get a lot of bang for the buck. I think tigerdirect sells them for $45-55 depending on the week.  

For what it's worth, here's my glxgears output:

alex@htpc:~$ glxgears -printfps
7137 frames in 5.0 seconds = 1427.239 FPS
7135 frames in 5.0 seconds = 1426.921 FPS
7150 frames in 5.0 seconds = 1429.921 FPS

Nothing great, but not too shabby for a $50 card.

-teet

---

### Post by dbott67 on 2006-10-20
Here's my glxgears output on my P4 1.8 Ghz with nVidia GeForce2 MX400:
```
 *-display
                description: VGA compatible controller
                product: NV11 [GeForce2 MX/MX 400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: b2
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia
                resources: iomemory:ee000000-eeffffff iomemory:f0000000-f7ffffff irq:201

```
```
dbott@thedrake:~$ glxgears
7393 frames in 5.0 seconds = 1478.458 FPS
7808 frames in 5.0 seconds = 1561.507 FPS
7918 frames in 5.0 seconds = 1583.475 FPS
7516 frames in 5.0 seconds = 1503.026 FPS
7312 frames in 5.0 seconds = 1462.295 FPS

```

And on my Dell Inspiron 6400 laptop with ATI Radeon X1400:
```
dbott@dapper:~$ glxgears -printfps
21957 frames in 5.0 seconds = 4375.044 FPS
22707 frames in 5.0 seconds = 4520.361 FPS
21344 frames in 5.0 seconds = 4247.785 FPS
22838 frames in 5.0 seconds = 4548.444 FPS
21426 frames in 5.0 seconds = 4283.787 FPS
21680 frames in 5.0 seconds = 4323.934 FPS
22799 frames in 5.0 seconds = 4543.157 FPS

```

-Dave

---

### Post by Wolki on 2006-10-20
I have a Radeon Mobility 7500 with 16 mb ram (!) on my Laptop, and if I disable the blur plugin, it runs compiz from the repos without problem. I have not tried beryl, and I currently don't plan to as I don't want additional repositories and was not impressed with compiz' usefulness aside from impressing friends.
Anyway, i was quite happy with how the free driver performed, and now plan to replace my desktop's grapics card (nvidia fx5500) with an ati that supports free drivers.

---

### Post by PriceChild on 2006-10-20
I run a 5600 xt 256mb which can run quake 4 in ultra at 1024x768 (with no more than one monster or it gets laggy)

On windows... i have to play at 800x600 on lowest.

Pricey

---

### Post by woedend on 2006-10-20
go nvidia..

---

### Post by darkhatter on 2006-10-20
the 9 series of the nvidia driver lets you run beryl with out xgl. nvidia has no open source driver.

I have a geforce 6100 go and that runs beryl perfect, the 6200 will do the job, I think that may even power vista

---

### Post by teet on 2006-10-21
> **dbott67 said:**
> Here's my glxgears output on my P4 1.8 Ghz with nVidia GeForce2 MX400:
```
 *-display
                description: VGA compatible controller
                product: NV11 [GeForce2 MX/MX 400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: b2
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia
                resources: iomemory:ee000000-eeffffff iomemory:f0000000-f7ffffff irq:201

```
```
dbott@thedrake:~$ glxgears
7393 frames in 5.0 seconds = 1478.458 FPS
7808 frames in 5.0 seconds = 1561.507 FPS
7918 frames in 5.0 seconds = 1583.475 FPS
7516 frames in 5.0 seconds = 1503.026 FPS
7312 frames in 5.0 seconds = 1462.295 FPS

```


-Dave

Off Topic:  How come you get just as many FPS on glxgears with your machine as my machine?  I have a 3.06 Celeron D and Geforce 6200.  Is there something I can tweak to get better performance or is the glxgears test just not a great indicator?

-teet

---

### Post by rocknrolf77 on 2006-10-21
For me there has nothing but trouble after I built my new computer with a ati card. Almost missing my old terrible computer with nvidia card. Getting the nvidia 7600GT in not so long. Ati quit's supporting their old cards much to early. Nvidia still makes drivers for much older cards than ati do. :)

---

### Post by sethmahoney on 2006-10-21
The 6200 can have issues with certain motherboards on linux.  Go for a 6600 (or any card that doesn't use TurboCache) for a safe bet, which you can get for about the same price if you find one on sale.

---

### Post by Anduu on 2006-10-21
I have an ATI card...go nvidia ;)

---

### Post by chaosgeisterchen on 2006-10-21
Sounds rather as if I should change the card as soon as possible, thanks for all the answers ;)

Another question: where the hell do I get a 6600 from which costs the sams as a 6200?!

---

### Post by dbott67 on 2006-10-21
> **teet said:**
> Off Topic:  How come you get just as many FPS on glxgears with your machine as my machine?  I have a 3.06 Celeron D and Geforce 6200.  Is there something I can tweak to get better performance or is the glxgears test just not a great indicator?

-teet

From my understanding, glxgears is not a great indicator.  The only thing I did was to install the nVidia drivers using '[automatix]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38")'.

-Dave

---

### Post by chaosgeisterchen on 2006-10-21
I ordered a 6200 for about 40&#8364;. My X300 gives me about 400 glxgears, which does not seem to be quite enough.

---

### Post by prizrak on 2006-10-21
On a desktop you should go with an nVidia card with the official nVidia drivers. ATI is getting better but not there yet. I would say it's a worth while upgrade and you will benefit from it. Do note however that Beryl and XGL are still beta technologies so you are likely to have issues either way

---

### Post by chaosgeisterchen on 2006-10-21
I know that they are alpha (in fact they are alpha, not even beta) - but I heard significantly better things about nVidia. So I decided to go for it - I hate to have hardware which cannot be fully used.

---

### Post by brash on 2006-10-24
> **jsandys said:**
> 
What is Beryl.

I didn't know either, and no one seemed to answer here so I poked around a little. [Wikipedia's entry]("http://en.wikipedia.org/wiki/Beryl_%28window_manager%29") seemed a little technical & hard to follow but [**this YouTube video maybe explains it best**]("http://www.youtube.com/watch?v=i0ZtcxHUSDQ"), without words.

Is Beryl or Compiz going to be packaged with Edgy, or it is something to install afterwards?

I was originally searching for a thread suggesting any performance suggestions as I am feeling that Ubuntu seems to run a trifle sluggish on my system. I'm a newb and may simply have something set up wrong; I have an AMD Geode NX 1750 (which I think may be semi equivalent to an Athlon XP 1600+), 512MB ram and a 128MB Radeon 9250. Obviously Beryl isn't a good option if I am already concerned about performance; I might swap some hardware around the house and see if I can get ram up to 756MB or 1G ram, and swap the video to a 9800pro (I also have an FX5200 and MX400 laying around the house if NVidia is that much of an imporvement, though those seem like a step backwards even from the 9250).

Anyway Beryl certainly looks downright sweet.

---

### Post by chaosgeisterchen on 2006-10-24
No, Beryl is neither part of Edgy nor will it be part of further releases (even if I think that it would fit into Feisty Fawn) as it is alpha state software.

But it's really ease to get it up and running with nVidia beta drivers. Then you just have to install them and install Beryl/Emerald. Everything's fine.

---

### Post by darkhatter on 2006-10-24
its going to be included in the version after 6.10 I read it somewhere

---

### Post by chaosgeisterchen on 2006-10-24
That was just a link to a launchpad suggestion. I do not know whether it was approved and I strongly doubt it.

---

