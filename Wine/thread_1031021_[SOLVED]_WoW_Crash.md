---
title: "[SOLVED] WoW Crash"
date: 2009-01-04
forum: Wine
---

### Post by baudday on 2009-01-04
So I have a ATI Radeon X850XT Platinum Graphics Card and I get the following problem.

I will be playing WoW and my computer will, what seems like, just randomly, crash. The game runs extremely smooth on my system, and there will be no signs of it slowing up or struggling before it crashes. I can't Alt+Tab out of the game or anything. The only thing I can do is hard reset my computer. Just to be clear, I don't get any sort of crash message as some may be used to. I followed the very helpful How To on installing the game, and everything works wonderfully. This is really the only problem I have, although it is a pretty big problem. Sometimes I can play until I decide to log off, and sometimes it will freeze 20 minutes into play. If anyone knows a solution to this problem, I would greatly appreciate any help.
Thanks

---

### Post by semtec04 on 2009-01-04
This forum is difficult to navigate, I cannot find my answer anywhere, I'm having an issue with my audio in wow, i dont have any of these ubuntu, ac whatever, or any other acronym that I see in these forums, it's simply a clicking , annoying, and my sound card is up to date, audio set a million different ways, resources on comp at more than operational levels for wow to run...don't know where else to go, if you can direct me to the answer please do, I'm pretty frustrated with looking through forums and googling to no avail, want to play wow asap.

---

### Post by baudday on 2009-01-05
You can go here [ [http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334) ] and click "New Thread" and post your problem there. I do actually have a problem with clicking with my video card too on one of my older computers, and I can't really figure it out. I figure it's just old and a connection somewhere is messed up. I would say check that it's connected properly and all that. Can't really help you, but if you post there, maybe someone can.

Now back to my problem ;)

---

### Post by aesis05401 on 2009-01-05
> **baudday said:**
> ... I can't Alt+Tab out of the game or anything. The only thing I can do is hard reset my computer. ...

Ctrl+Alt+Backspace is supposed to kill any frozen graphics session, but I have never had to use it.   

Figured I would post before I tried for the first time :)

Edit: I should mention it kills *all* graphics sessions - but you probably knew that.

---

### Post by baudday on 2009-01-05
Yeah I know, and that's what I thought. But even that doesn't work. I can't imagine what the problem is.

---

### Post by aesis05401 on 2009-01-05
I haven't hit this crash, but if playing WoW is one of the more resource intensive things you do on this box you might want to run a memory test for a good long while.   

Either that or put a different type of heavy load on the box and see if you can reproduce the crash without WoW running.

These steps could help rule a few obvious things that cause freezes like you describe.

---

### Post by baudday on 2009-01-05
It is probably the most resource intensive thing I do. I know my graphics card can handle the load, but fear it may be overheating. I really have no idea what's failing. Could you tell me how to run a memory test?

---

### Post by aesis05401 on 2009-01-05
> **baudday said:**
> ... Could you tell me how to run a memory test?

It is easy.  Most livecds have a memory test utility onboard.  Your Ubuntu install media should have memtest86 as an option when you boot from the disc.

The problem is the wait.  A thorough RAM check can run for quite a while. 

The good news is that bad RAM is easy and relatively cheap to fix.  If your hard freeze is due to something more complex I can't help you.

As for the overheating.. your bios should have at least a CPU temp reading.  My old overclocking rig had all sorts of temp information accessible through bios screens.

To get a solid reading you should reboot your machine following a resource intensive session, opt into the bios screen on boot, and check out how hot you are running.  Your components should have desired operating temperatures that are published somewhere on the webs... though it has been years since I needed to look anything like that up.

Now that I think about it.. I had a machine that used to freeze due to the CPU temp, but a new CPU fan fixed it right up.  You might be onto something.

---

### Post by baudday on 2009-01-05
Thank you, I will try the memory test, and check the temp of my graphics card and cpu the next time the game freezes up. I really appreciate your insight into my problem

---

### Post by aesis05401 on 2009-01-05
Heh, thanks.  I'm just giving you the optimistic troubleshooting advice ;)

If whatever it is about the execution of WoW that is completely locking your environment is not a known issue, and is not hardware related the troubleshooting could get gnarly. 

Best of luck.

---

### Post by ndefontenay on 2009-01-05
My current PC has been failing for a while now in exactly the way you describe it with no resource intensive actions at all. It was temperature.

I'm in Thailand and room temperature is pretty hot already. After looking around I found at my graphic card fan was not working.

I changed the graphic card and now it fails less x) It's still too hot. I need a bigger than for my cpu. It works like a charm otherwise if I open the case on both sides.

AMD are hotter than intels too it seems (I got an AMD)

Nico

---

### Post by Eviljim on 2009-01-05
A spring clean of the PC may well be in order.

I would remove the components such as the graphics card individually and clean with compressed air, or even by dusting it off with a rag. As with all things PC, do this very carefully and ensure any cables that are removed are put back in the same place.

Worth also checking the vent ports on the case itself, any internal cooling fans (including CPU and PSU).

---

### Post by baudday on 2009-01-05
Well thank you for the replies. I am now getting more confident that it is, in fact, temperature. My graphics card and other fans all work. But I think the card is still getting too hot. It has this little metal plate that's supposed to divert heat away from the components, and that gets extremely hot. The system was crashing far more than normal last night after I moved the computer upstairs and had it resting on the carpeted floor. I think this was insulating the heat and making it even hotter. I think a good clean out is a good idea as well. What extra can I do to cool down my card?

---

### Post by baudday on 2009-01-05
Well, I cleaned out the entire system, and there was a lot of dust in the cooling unit of the graphics card. Hopefully that solves the problem. I will run the game and see how it turns out.

---

### Post by baudday on 2009-01-05
So my graphics card runs a lot quieter than it did  before I cleaned it. Which is an indication to me that the fan doesn't have to work too hard, which means the temperature of the card is definitely lower than it used to be. I was just able to play around an hour without any crash. Which I've done a few time before, but I think it's a good sign. Hopefully I found the problem.

---

### Post by Eviljim on 2009-01-06
I know it seems silly, but have you checked the airflow whilst the Pc is running?

It has been known for fans to be incorrectly installed and the airflow be totally disrupted.

With the side of the case off, any fans at the front of the PC should be blowing air over the motherboard, graphics, memory etc, with the rear fans blowing the warm air out the back as an exhaust. Any fans mounted on the side door would probably be beneficial to be blowing air into the PC.

With the PC switched off, make sure that any hard drive cables are pushed/grouped/tied out of the way as ribbon cables can really muck up your airflow.

You can also buy replacement fans (the bigger the better as they are also quieter) and a even a replacement graphics card cooler if you want to.

---

### Post by baudday on 2009-01-06
I can happily say I played for a long while last night with no crashes. So it was definitely the dust that was causing the card to overheat.

---

