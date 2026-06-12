---
title: "Building a new computer to save money."
date: 2010-01-11
forum: The Cafe
---

### Post by Warpnow on 2010-01-11
So, I got to thinking. My current computer consumes about 300watts at idle, which is alot of power, and alot of money...but do I need all of that power? Is it costing me money to have this power, and if so, would I be better off having a second low power computer to use. I'd make sure to never run them both at the same time, as that would cause it to unprofitable. 

My theory is that if I build a cheap mini-itx computer, I can use it to torrent things while I sleep, for light word processing, ect, and only use my main computer when I have to, ie, when I need all of the processing power. To pull it off, I think I'd have to mostly use an external hard drive for my files, so I can access them both from both computers.

I wonder if it would be possible to share a home folder between the two computers if I was running the same version of the OS on both computers...not sure about that, but I'll worry about that later.

I've done the calculations in gnumeric, and the answer is, for me, yes, I would save money building a second computer. I've attatched the gnumeric spreadsheet I used for my calculations.

In my situation I'd save $20 the first year, and roughly $700 over the next five years.

I'd really prefer the Cortex A9 for many reasons. Its System-On-Chip style and reduced size would mean I could likely mount the motherboard in a 5.25" drive, wire a second power button to the front, cram a power supply inside, and have it boot off of an SD card. The only issue is how allow the second computer to access the main drive without turning on the main computer.

Thoughts?

---

### Post by sdowney717 on 2010-01-11
is it cold where you live?


not all that power is wasted, it heats your living space.

---

### Post by cascade9 on 2010-01-11
300 watts at idle???!!?? 

What are you running? I've never heard of anything that uses anywhere near that much power at idle. 

As for the drive access problem...I've never seen what I've about to suggest, but it should work. Just get x2 SATA data cables, and splice it so you have a 'y' setup. 1 end to plug into the drive, 2 ends for each of the motherboard SATA ports. You'll have to do the same to the power cables...and I'd guess that turning on a 2nd machine could kill the drive (or it might not, try it with a really really crap SATA drive if you build this). Then again,even if it doesnt kill the drive it might make things bit confused (either the drive or either/both the OSes confused that is).

---

### Post by kerry_s on 2010-01-11
i wish you would have put it in a format that we might all use, i'm on windows so can't read the "powersavingcomputer.gnumeric" file.

---

### Post by Warpnow on 2010-01-11
Splitting the SATA cable might work...I personally have no idea.

I have an idea for a new hardware device, but it doesn't exist, so not helpful, that would solve my problem.

I've saved the file in a 2000 excel file. Sorry, I assumed people would be using linux on the ubuntu forums...I can't confirm no errors as I don't have excel to test it with. I figure openoffice can also open excel files and is cross platform, but am unsure if excel can open openoffice files.

And...no...its not cold here, haha, I live in texas. I should actually calculate that as a cost...

Edit: I changed the values in this one just toying around, just noticed I had. Make sure to input your own specific values for b2-b7, ie, the ones with a border. The ones I have show a pretty signifigant loss because I was trying to figure out how it would end in loss.

---

### Post by cascade9 on 2010-01-11
Splitting the SATA cable _will_ work. I've seen it done with an IDE cable- and it was a 40pin/80wire version. Took the owner ages, but it work. SATA is far easier to do. 

BTW- I just noticed the hardware in your sig. If that is what you think is pulling 300watts at idle, think again...and check this 

[http://www.xbitlabs.com/articles/coolers/display/system-wattage_6.html](http://www.xbitlabs.com/articles/coolers/display/system-wattage_6.html)

yes, I know its a different CPU model but its near enough. E8600/4GB/ATI4850/500GB 7200/etc etc, MAX draw from the PSU- 189watts. That would be 237watts, from the wall (assuming an 80% efficient PSU) People tend to overestimate the amount of power drawn...

BTW, you might be able to underclock your C2D and drop power use a large amount, and then restart it in 'full power' mode if you need the power.....just an idea.

---

### Post by kerry_s on 2010-01-11
thank you for saving in a more friendly format. 

not to sure about the math there, but you will save some money going with a energy efficient machine.
i recommend a external or nas for sharing.

do you have a link for this "Cortex A9" pc?

---

### Post by Warpnow on 2010-01-11
The cortex A9 isn't out yet. Its due out in a month or two.

My math is right, I am quite sure. I do these calculations alot.

And I know my computer is drawing 300 watts, I'm measuring it at the socket.

Edit: To be clear, I'm measuring what the surge protector is drawing, onto which all of my computer equipment is attatched. LCD, Computer, and Printer, versus what is consumed when the same surge protector powers a nettop with my lcd and printer.

---

### Post by starcannon on 2010-01-11
Hahaha, I come up with reasons to build new computers all the time, and when I'm lucky, I catch the wife in a rare mood, and she votes yes(damn democracy); and then I get to build one :)

Tell yourself whatever you need to, enjoy building a new machine; its one of my favorite things to do myself.

---

### Post by cascade9 on 2010-01-11
> **Warpnow said:**
> And I know my computer is drawing 300 watts, I'm measuring it at the socket.

Edit: To be clear, I'm measuring what the surge protector is drawing, onto which all of my computer equipment is attatched. LCD, Computer, and Printer, versus what is consumed when the same surge protector powers a nettop with my lcd and printer.

That makes more sense. I still think 300 is a bit high, but you may very well have a inefficient power supply. But with a LCD that draws a fair bit, a printer as well, and a surge protector (and I would assume speakers as well? please dont tell me you have no speakers! LOL) it might be a fine power supply. *shruggs* 

BTW, your maths looks fine to me.

---

### Post by tom66 on 2010-01-11
300 watts! I doubt it. Buy a Kill-A-Watt and plug it into your computer. If you're consuming 300 watts idle then your power supply will have a short life, because most PSUs you find are cheap and rated for ~300 watts. 

Here are some suggestions:
 - Get more RAM. This means you can get rid of your swap space, which means your disks are idle more often.
 - Tell your disks to spin down often, like every minute instead of every ten minutes.
 - Get a green HDD. Even if it's not your main one, put most of your files on there so it's used the most. 
 - Get an efficient power supply, at least 90% efficient. Most power supplies are 70-80% efficient, which is pretty good but not fantastic.
 - Suspend more often. Better yet, shut down.
 - Put your CPU into an underclocked configuration. If it supports PowerStep or a similar system, put it in the "Conservative" band, which will only step up the frequency when absolutely necessary.
 - If you have a dedicated graphics card, do you *really* need it? If you find it's too old to run most games, upgrade it for a newer one which is probably more efficient. 
 - Turn off your monitor when you are not using it.
 - Do you need your computer for all tasks? Example: You can check the weather on your phone, or on the TV, so you can avoid starting up your computer to browse the 'net for weather.

---

### Post by kerry_s on 2010-01-11
> The cortex A9 isn't out yet. Its due out in a month or two.

no wonder, i was googling it & only saw info on the cpu itself.

> My math is right, I am quite sure. I do these calculations alot

i meant the numbers, but you sound like you know your stuff. ;)

i can tell you when i ditched 2 full size pc's for little atom unites, are bill went down $70 dollars a month, there always on we just turn off the lcd when not using. 1 uses the 230 atom & the other is a atom 330, were using headphones instead of speakers, printers only plugged in when needed, your basic setup. we have since been cutting in more places, haven't had a bill over $300 in the last 6 months.

---

### Post by Warpnow on 2010-01-11
I found this interesting...it consumes only 5 watts...

[http://www.linuxfordevices.com/c/a/News/NorhTec-Gecko-Surfboard/](http://www.linuxfordevices.com/c/a/News/NorhTec-Gecko-Surfboard/)

Also, here's a summary of an idea I've been working on.

[quote="Warpnow"]
Computer in a 5.25" Bay.

This idea is for a computer that is housed in a 5.25" computer drive bay, as a low powered alternative to booting the main computer. I believe this contains multiple original ideas, and if so, I would consider them patent pending Chase Baggett, ;).

Essentially, the computer consists of three physical components, the computer itself, the backplate accessory, and the switching unit similar to a KVM, which could be houses in a 3.5" external bay. The computer itself sits inside the 5.25" bay of a regular desktop computer. The 5.25" bay is obviously best because it has front access. This will allow buttons as well as card readers on the front. Removable and interchangable face plates would be ideal for maintaining cosmetic appeal.

Once the unit is installed in the bay, its backplate accessory is installed. This accessory consists of multiple parts. It must route audio, video, storage, ethernet access, mouse/keyboard/printer (ie, USB), and any other necessary components. Essentially all the backplate does is provide extensions from the computer in the bay to ports on the back of the computer. 

Those ports are then fed into the switching unit, which is much like a KVM, with a button to switch all things from one set of hardware to the next. Most likely many of these things would not actually have to be switched, but rather split, as they would never simultaneously be in use by both sides. 

Data storage at first seems an interesting conundrum. However, I have a proposed solution. The computer itself has a built in small SSD for the operating system, and only the operating system. The connection from the SATA hard drive to the primary one is then fed through into the 5.25" computer, and then back through another SATA cable out to the motherboard. When the 5.25" computer is off, it simply routes the connection through untouched. However, when the computer is on, it should mount the SATA hard drive as a slave and allow access to the files. The OS on the SSD could be configured to save things there, and to automount it somewhere easily accessible. A splitter would have to be provided for the SATA power to the drive, so that the drive could be powered either by the 5.25" computer or the standard ATX power supply. 
[/quote]

---

### Post by gn2 on 2010-01-11
Doubt you could build anything cheaper than an Acer Revo.

---

### Post by ssam on 2010-01-11
you could build a miniitx box from a via epia or atom board, [http://mini-itx.com/store/?c=2](http://mini-itx.com/store/?c=2) shows power consumption for quite a few boards. or you could get a beagleboard, which has very low power consumption (~1 watt), but is fairly slow.

you set up the small computer as a file server, so that the big one can access the files.

---

### Post by kerry_s on 2010-01-11
> I found this interesting...it consumes only 5 watts...

[http://www.linuxfordevices.com/c/a/N...cko-Surfboard/](http://www.linuxfordevices.com/c/a/N...cko-Surfboard/)


that would be better then arm, at least you'll have flash. :D

> Doubt you could build anything cheaper than an Acer Revo.

i bought 1 of these: [http://www.newegg.com/Product/Product.aspx?Item=N82E16856119011](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119011)
when it was on sale for $86.99, i already had ram & sata drive, so for less then a $100 bucks i was good to go. :P

---

### Post by gn2 on 2010-01-11
> **kerry_s said:**
> i bought 1 of these: [http://www.newegg.com/Product/Product.aspx?Item=N82E16856119011](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119011)
when it was on sale for $86.99, i already had ram & sata drive, so for less then a $100 bucks i was good to go. :P

Not a bad little item there, but if you had to buy new RAM and HDD, the price difference is.....?
Revo has far better graphics adapter ;)

---

### Post by cascade9 on 2010-01-11
I've been looking at those gecko surfboard machines, and hoping they come out soon. :) 

As for your idea- totally do-able. 

You'll need a nanoITX (120 × 120 mm or 4.7 × 4.7 in), pico-ITX or picoITXe (100mm x 72 mm or 3.9 x 2.8 in) motherboard. Pity that minITX wont fit in a 5.25'' drive bay, but thats the way it goes sometimes. I'm not sure you can even get pico-ITX motherboards that aren't mouthed in some form of case, but nano-ITX was around. 

[http://www.mini-box.com/Mainboards-Nano-iTX](http://www.mini-box.com/Mainboards-Nano-iTX)

That board probably isn't ideal, if only because of the VIA chrome video, but it would do the job. As for power supplies, the mini-box site has some, and I'm sure there are others around. Its also only got one SATA port which will mkae you go to IDE SSD. 

But there are others, mainly VIA, I'm sure you could find something that would do what you want. 

The biggest issue would be the cabling, but if you have any skills with a soldering iron, or are prepared to learn then it shouldnt be hard. I'm not sure I would go to a 'pass through' SATA for the 2nd (non-OS) drive, I think a y-SATA cable would be easier, but that is up to you, its maker :D

---

