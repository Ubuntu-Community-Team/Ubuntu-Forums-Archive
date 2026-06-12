---
title: "Dead CPU?"
date: 2007-11-13
forum: The Cafe
---

### Post by xinix on 2007-11-13
I think I may have confirmed this in IRC but there was so much other chatter going on that responses would fly off screen before I could read them.  But, i think my CPU is fried and wanted to confirm this diagnosis.
I came home on Sunday to find my rig was off.  When I hit the power buttons the fans would come on for a second and then shutoff.  I stripped the system down to the basics, CPU, mem and vid.  Same results.  If I take the CPU out and power it on the fans run until I kill the power either by unplugging or holding the power button.  I get the same results if I simply disconnect the CPU power supply (square 4 pin plug).  It doesn't post at all.  The mobo manual doesn't list any beep code for missing/dead CPU, but I figure this is a component that the mobo needs in order to get as far as beeping errors.  Any thoughts?

Edit:
Tested with a working PSU and had the same results.

---

### Post by Dixon Bainbridge on 2007-11-13
Look on the underside of the CPU. If its brown, its fried :)

---

### Post by xinix on 2007-11-13
It looks fine.

---

### Post by ddrichardson on 2007-11-13
It doesn't need to have been something as catastrophic as a burn out. Static damage to integrated circuits can often not affect systems until later in their life span.

Have you looked at the motherboard support site? There's usually some good post mortem advice.

I'm no expert with i386 hardware but as far as I know the CPU is required for all but the most fundamental built in test functions.

---

### Post by xinix on 2007-11-13
I've tried the motherboards support advice from the knowledge base question that describes my symptoms.  Basically it says to reset the CMOS but I've tried this and it doesn't work.

---

### Post by ddrichardson on 2007-11-13
Reset the CMOS is the hardware support equivalent of an ISP telling you to restart Windows.

---

### Post by koleoptero on 2007-11-13
I've had the same problem and it was the power supply. Try a different one from aanother pc and see if it works.

---

### Post by jflaker on 2007-11-13
> **xinix said:**
> I think I may have confirmed this in IRC but there was so much other chatter going on that responses would fly off screen before I could read them.  But, i think my CPU is fried and wanted to confirm this diagnosis.
I came home on Sunday to find my rig was off.  When I hit the power buttons the fans would come on for a second and then shutoff.  I stripped the system down to the basics, CPU, mem and vid.  Same results.  If I take the CPU out and power it on the fans run until I kill the power either by unplugging or holding the power button.  I get the same results if I simply disconnect the CPU power supply (square 4 pin plug).  It doesn't post at all.  The mobo manual doesn't list any beep code for missing/dead cpu, but I figure this is a component that the mobo needs in order to get as far as beeping errors.  Any thoughts?

I am suspecting a powersupply rather than the system board

the PSU will commit suicide in favor of saving all other electronics.  It is basically an expendable part.  Since you are saying it comes on momentarily then shuts off, almost certain it is the PSU

(almost 19 years IT)

---

### Post by -grubby on 2007-11-13
> **jflaker said:**
> I am suspecting a powersupply rather than the system board

the PSU will commit suicide in favor of saving all other electronics.  It is basically an expendable part.  Since you are saying it comes on momentarily then shuts off, almost certain it is the PSU

(almost 19 years IT)

so you're saying the PSU cares about the other hardware components and sacrifices itself in favor of saving the other hardware components?what a hero

---

### Post by jflaker on 2007-11-13
> **nathangrubb said:**
> so you're saying the PSU cares about the other hardware components and sacrifices itself?what a hero

It is a selfless PSU!

---

### Post by nutz on 2007-11-13
Sounds like your PSU took a crap. CPUs don't just die like that and these days they all cope with overheating pretty well. Sounds to me like your PSU took a crap or you have a bad capacitor on your mainboard.

---

### Post by ddrichardson on 2007-11-14
Sorry, I'm not sure why people are suggesting the PSU - the OP said it functions when CPU is disconnected, voltage regulation is carried out by the PSU and as for sacrificing itself - only insofar as there are fuses in good PSUs and cheap toroidal transformers in cheap ones that burn out.

But I could be wrong and PSU are cheaper so why not try it first.

---

### Post by rustybronco on 2007-11-14
psu...

---

### Post by xinix on 2007-11-14
I just tested with a working PSU (the one from this computer) and I got the same results.   If it were the mobo, wouldn't it short out without the CPU too?

---

### Post by ddrichardson on 2007-11-14
Do you mean is it a problem with the motherboard?

---

### Post by xinix on 2007-11-14
Yes, could the problem be a faulty motherboard?  Removing the CPU (or CPU power plug) results in the fans staying on, but does this necessarily mean that it's the cause of the problem?  If it is the motherboard shorting out, would removing the CPU stop this from happening or would the board continue to fail without this component?  Replacing the CPU won't upset me too much since I've been considering upgrading it to the best option i can plug into a 939 socket.  On the other hand, I'm not too keen on any of the motherboards I've found with 939 sockets.

---

### Post by ddrichardson on 2007-11-14
When you say the CPU power plug are you referring to the motherboard power connector or the CPU cooling fan connector?

---

### Post by xinix on 2007-11-14
The square 4 pin connector.  Not the fan or the 20 pin connector.

---

### Post by ddrichardson on 2007-11-14
Generally I'd swap out the mainboard before the processor. If you can get hold of a known working one to test with, otherwise its down to making an educated guess, my gut feeling with your symptoms is the processor.

---

### Post by Zero Prime on 2007-11-14
Dude, you have the same exact problem I had.  I had to replace my motherboard and everything worked fine after that.  I replaced my power supply as well and I would recommend doing the same if you have an old OEM PSU.

---

### Post by xinix on 2007-11-20
> **Zero Prime said:**
> Dude, you have the same exact problem I had.  I had to replace my motherboard and everything worked fine after that.  I replaced my power supply as well and I would recommend doing the same if you have an old OEM PSU.

Yep that would seem to be the problem.  I'm still waiting on a new board but after taking out the old one I spotted a vented capacitor.  I had looked for this while the board was in the case but this one was hidden by cables and such.

---

### Post by ddrichardson on 2007-11-20
Replace the capacitor, it'll say on it what value it is.

---

### Post by xinix on 2007-11-20
Unfortunately, replacing the capacitor is out of my area of expertise.  Is this worth sending off to a shop to do?

---

### Post by aimran on 2007-11-20
Don't they teach kids nowadays to solder :|

:lolflag:

---

### Post by Lostincyberspace on 2007-11-20
hey no will teach. they say just get a new one its less hassle.

---

### Post by xinix on 2007-11-20
Heh, I was taught how to solder, only it was for metal smithing and not electronics.  Something tells me that the tools I have aren't the right ones for this job. :twisted:

---

### Post by ddrichardson on 2007-11-21
You can pick up a kit from radio shack or whatever, even in the UK they're only around £10, capacitors are cheap as chips - all you need is a de-solderer and an iron. Heat the current solder and suck it off then fit the new capacitor, flay the pins out a little and then solder it back in. Just make sure you don't apply to much heat or you'll lift the tracks off the PCB. A little letoxane to clean off any flux and you'll have spent around £15 rather than at least three times that on a new motherboard - if it's borked anyway then what have you got to lose?

---

