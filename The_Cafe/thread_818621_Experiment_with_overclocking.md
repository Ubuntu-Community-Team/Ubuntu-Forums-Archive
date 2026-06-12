---
title: "Experiment with overclocking"
date: 2008-06-04
forum: The Cafe
---

### Post by Raccoon1400 on 2008-06-04
I finally found the perfect machine to experiment with overclocking.
I have a pIII coppermine 600MHz compaq, 256MB of ram, and I just gave it a CLI debian install.

How would I go about overclocking it? Can I do that with software?

---

### Post by MrMatt2532 on 2008-06-04
Go into the BIOS. You should probably be able to change at least the FSB.

---

### Post by Raccoon1400 on 2008-06-04
I don't see any mention of fsb in bios.

---

### Post by MrMatt2532 on 2008-06-04
Yeah, i looked back at your post. Usually big vendors like compaq really limit the bios options. You can probably only do things like boot order, system time, and system password.

If that is the case then i don't know a good way to overclock. I'm not really familiar with software overclocking. I've done it with video cards before, but never with cpus.

edit: I did a little bit of searching and cpufsb and clockgen might work for your needs. The only problem is that they are apps for windows.

---

### Post by Raccoon1400 on 2008-06-04
I wish it was one of those motherboards you could manually overclock with switches on the motherboard.

---

### Post by tamoneya on 2008-06-04
look up your motherboard model.  A lot of the overclocking and such done with PIII processors was done with "pencil mods" and other physical modifications of the motherboard.  Basically you shade over certain resistors to change their resistance because lead/graphite conducts and this changes clock speeds and such.

---

### Post by Raccoon1400 on 2008-06-04
> **tamoneya said:**
> look up your motherboard model.  A lot of the overclocking and such done with PIII processors was done with "pencil mods" and other physical modifications of the motherboard.  Basically you shade over certain resistors to change their resistance because lead/graphite conducts and this changes clock speeds and such.
Interesting. This is a good machine to experiment with because the only other thing it is good for is throwing out the window. I picked it up today at the curb.

---

### Post by tamoneya on 2008-06-04
what is your mother board model.  I will help you do some of the research.

---

### Post by sweeneytodd on 2008-06-05
surprised u can't overclock it, no switches on motherboard? no options in bios, try upgrading bios maybe, i just haven't seen a motherboard without the switches on the  m/b, mind you, 600mhz, whats the point, if u don't have an use for it, give it to oldie wanting one, thats what i'd do

---

### Post by Raccoon1400 on 2008-06-05
It turns out I can manually clock this board. However, the switches don't allow it to be overclocked.

I will have a good look for the model number later, it proved easier said than done. It is a strange form factor too.

---

### Post by Raccoon1400 on 2008-06-05
Can't find model number anywhere. I have the year made, the serial number, system board revision, but no model number.

---

### Post by Raccoon1400 on 2008-06-05
Is there some command that will give me the motherboard model?

---

### Post by tamoneya on 2008-06-05
```
sudo lshw >hardware.txt
gksudo gedit hardware.txt
```
It should be near the top.

---

### Post by Raccoon1400 on 2008-06-05
> **tamoneya said:**
> ```
sudo lshw >hardware.txt
gksudo gedit hardware.txt
```
It should be near the top.

I had to modify this command because X is not installed, and I had to install lshw.

Model: 0440h (I think)

Here is the entire file.

---

### Post by Raccoon1400 on 2008-06-05
Does /proc/cpuinfo automatically adjust to changes in clock speed, or is there a command to refresh it?

---

### Post by tamoneya on 2008-06-05
see if either of these two threads help you in IDing the motherboard further:
[http://www.techsupportforum.com/hardware-support/other-hardware-support/56447-compaq-deskpro-model.html](http://www.techsupportforum.com/hardware-support/other-hardware-support/56447-compaq-deskpro-model.html)
[http://www.motherboardpoint.com/t37349-help-needed-in-identifying-compaq-en-series-pd1005-.html](http://www.motherboardpoint.com/t37349-help-needed-in-identifying-compaq-en-series-pd1005-.html)

btw here is the relevant section```

       *-core
       description: Motherboard
       product: 0400h
       vendor: Compaq
       physical id: 0
       serial: ************
```

---

### Post by tamoneya on 2008-06-05
i just did some more looking and it appears that you have a Dpend-P550.
This thread may help with the OCing.
[http://forums.extremeoverclocking.com/t148253.html](http://forums.extremeoverclocking.com/t148253.html)

Also could you post or link to some pictures of the motherboard.  I would like to get myself familiarized with its layout and everything.  Maybe I can find some likely places to start investigating.

---

### Post by Raccoon1400 on 2008-06-06
Here are some pictures.

---

### Post by Raccoon1400 on 2008-06-06
No, wait, here they are.

---

### Post by Raccoon1400 on 2008-06-06
No, wait, here they are here FOR REAL!!!!

---

### Post by Raccoon1400 on 2008-06-06
PLEASE tell me it worked this time!!!!!

---

### Post by tamoneya on 2008-06-06
unfortunately it wasnt very helpful since they arent great resolution and the flash was a bit off.  Did those thread links help at all?

---

### Post by Raccoon1400 on 2008-06-06
Sorry about the quality. It appeared the pictures had to be 19.6 KB or less, and 280pixles high.

The case says:

DPENM P600
it is a compaq deskpro

---

### Post by tamoneya on 2008-06-06
its best if you can upload to flickr or something and then link them.

---

### Post by Raccoon1400 on 2008-06-07
Haven't forgoten, working on uploading to picasa.

---

### Post by Raccoon1400 on 2008-06-08
[http://picasaweb.google.ca/Raccoon1400/Computers](http://picasaweb.google.ca/Raccoon1400/Computers)
here's one.

---

### Post by tamoneya on 2008-06-08
can we possibly see under the heatsink.  If you havent found anything interesting online I would be willing to help you find some replacement oscillators for the chip.  You would have to solder these into the board in place of the current oscillators.  This is a very old school method for overclocking but it could work and you would probably learn a fair amount in the process.

---

### Post by Raccoon1400 on 2008-06-08
Go to the previous linked page. There is another photo.(and I added captions to both photos)

How much would oscillators cost? I am only 16, and don't have much money.

---

### Post by tamoneya on 2008-06-08
I have attached an image where I highlighted what looks like the only oscillator on the board from the pictures so far.  Can you make out any markings on that component?  Can we get a closer pic on that one piece?

EDIT: i noticed one more oscillator.  Take a look at that one as well.  I reuploaded the picture.

---

### Post by Raccoon1400 on 2008-06-08
> **tamoneya said:**
> I have attached an image where I highlighted what looks like the only oscillator on the board from the pictures so far.  Can you make out any markings on that component?  Can we get a closer pic on that one piece?

EDIT: i noticed one more oscillator.  Take a look at that one as well.  I reuploaded the picture.

Sure. Have to wait until tomorrow afternoon though. (10:20 PM EST now)

---

### Post by s3r4phim on 2008-06-08
If you really dont care that much about it:

take out the processor (you should be able to without de-soldering or cutting wires, but they dont make it easy, especially not compaq). Look on the processor controler (its the other chip that doesn't have the processor itself on it.) This may be built into the motherboard or the chip with the CPU on it, so look there if it's not separate. On the controller there should be a little black box with wires coming out either side. This is the time crystal. It is a form of ocillator that allows the system to keep track of time. De-solder this, and go to any radio shack or modding store and buy a faster ocillator. Make sure it is designed for a computer,and not a radio. Radio crystals are far less stable, and tend to spike. Solder this onto the place of the old crystal, and you have an over clocked computer. Remember, even a .3 ghz overclock is alot. Make sure you have an adaquet cooling system to handle it. Mine is overclocked from 3.5 to 3.8, and i needed a whole new cooling chamber just for that.

good luck!

---

### Post by Raccoon1400 on 2008-06-09
> **s3r4phim said:**
> If you really dont care that much about it:

take out the processor (you should be able to without de-soldering or cutting wires, but they dont make it easy, especially not compaq). Look on the processor controler (its the other chip that doesn't have the processor itself on it.) This may be built into the motherboard or the chip with the CPU on it, so look there if it's not separate. On the controller there should be a little black box with wires coming out either side. This is the time crystal. It is a form of ocillator that allows the system to keep track of time. De-solder this, and go to any radio shack or modding store and buy a faster ocillator. Make sure it is designed for a computer,and not a radio. Radio crystals are far less stable, and tend to spike. Solder this onto the place of the old crystal, and you have an over clocked computer. Remember, even a .3 ghz overclock is alot. Make sure you have an adaquet cooling system to handle it. Mine is overclocked from 3.5 to 3.8, and i needed a whole new cooling chamber just for that.

good luck!

Would that be one of the ocsillators mentioned in post 29?

---

### Post by s3r4phim on 2008-06-09
> Would that be one of the ocsillators mentioned in post 29? 

yes.

---

### Post by Raccoon1400 on 2008-06-09
Could I just take an oscillator off another motherboard? I have a whole stack of them.

---

### Post by Raccoon1400 on 2008-06-09
[http://picasaweb.google.ca/Raccoon1400](http://picasaweb.google.ca/Raccoon1400)

more pictures, close ups of the oscilators

---

### Post by tamoneya on 2008-06-09
looking at the photos only the first one you showed is an oscillator.  The second one I thought was an oscillator from the original pics but is in fact just a heat sink.

---

### Post by Raccoon1400 on 2008-06-09
> **tamoneya said:**
> looking at the photos only the first one you showed is an oscillator.  The second one I thought was an oscillator from the original pics but is in fact just a heat sink.

The second didn't look like the first one, and I thought you confused them, but I uploaded both anyways.

Could I replace the oscillator with one from a different motherboard?
If so, how would I tell what speed each oscillator would make the processor run? numbers on side?

the oscillator on this board doesn't appear to have a number, but I checked two other boards, and their oscillators both say 'e32k'

---

### Post by tamoneya on 2008-06-09
typically you see a three digit number like 123 which means 12*10^3 which in this case would mean 12 khz.

EDIT: im guessing e32k means a 32 khz oscillator.  Not sure on the "e" i will see what i can find.

---

### Post by Raccoon1400 on 2008-06-09
maybe this one is 32K.
What speed should I use?
Hard to tell, since there is no number on the original.

---

### Post by tamoneya on 2008-06-09
well i would like to do some more investigating.  I am looking at the pics that show under the heat sink because I am hesitant about the current oscillator.  It is rather far away from the CPU.  I would have expected it to be a lot closer.  When looking at the pics I noticed a table in the upper right hand corner that says something about frequency.  Can you copy the contents of the table into the forums or take a picture of it?

Assuming it is 32Khz you would want some percentage increase on that number. You dont want to be to agressive though.  shoot for 20 percent or so.  That would make it 38-39khz.

---

### Post by s3r4phim on 2008-06-09
Just remember, motherboards are often multi-layered, so be careful when de-soldering, you might accidentally melt through and destroy it. Use an old, low power iron, or just clip it of, if that's feasible.

---

### Post by Raccoon1400 on 2008-06-09
The frequency chart is for the frequency clocking swithes. Unfortunately, the chart stops at 600MHz, the current clock speed.

EDIT: Just uploaded a pic anyway

---

### Post by Raccoon1400 on 2008-06-09
> **s3r4phim said:**
> Just remember, motherboards are often multi-layered, so be careful when de-soldering, you might accidentally melt through and destroy it. Use an old, low power iron, or just clip it of, if that's feasible.

15 Watt?

My iron does 15 and 30 watt.

---

### Post by tamoneya on 2008-06-09
15 watt is good.  Also I second the idea for clipping the old one in a way that leaves a long lead so that you can solder onto that.

The other thing that we should consider now that i am looking at the chart is that it will also increase the ram frequency.  Both the CPU and the RAM will get a frequency bump so you want to make sure they dont over heat either.

---

### Post by Raccoon1400 on 2008-06-09
> **tamoneya said:**
> 15 watt is good.  Also I second the idea for clipping the old one in a way that leaves a long lead so that you can solder onto that.

The other thing that we should consider now that i am looking at the chart is that it will also increase the ram frequency.  Both the CPU and the RAM will get a frequency bump so you want to make sure they dont over heat either.


Will the frequency of the RAM increase when I change oscillator, or just the switches?

---

### Post by tamoneya on 2008-06-09
well since so far the only oscillator i see is that one everything else is probably based off that one frequency so everything is based upon a multiple of that frequency.  The other possibility is a RLC circuit being run at its fundamental frequency is in there somewhere but typically clocks are controlled somewhere by oscillators.

---

### Post by Raccoon1400 on 2008-06-09
I may have been unclear earlier. The 32k oscillator was on a different motherboard, and could be moved to this board.

The oscillator on the board in the pictures has no numbers whatsoever.

---

