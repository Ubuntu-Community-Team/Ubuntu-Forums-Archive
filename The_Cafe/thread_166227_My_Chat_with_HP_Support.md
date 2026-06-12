---
title: "My Chat with HP Support"
date: 2006-04-26
forum: The Cafe
---

### Post by trent dillman on 2006-04-26
EDIT: There was a bit more here at the beginning, mostly me asking about the processor and then being asked for product/serial numbers...

jeff c: sorry i'm taking so long...i am feeding a baby right now...
Sarah: No worries.
Sarah: that's fine.
Sarah: Please take your time. I'll be here.
jeff c: s/n #######
jeff c: p/n #######
Sarah: Thank you for the information.
jeff c: while you're looking that up, let me just give my 2 cents about this product:

It's a nice laptop, but I had to get a thermal pad to keep it from overheating. Also, I cannot get drivers for the digital media reader.
Sarah: Okay.
jeff c: But neither of those are my concern right now. :-)
Sarah: Not a problem,I'll assist you further.
Sarah: Please spare a couple of minutes.
jeff c: OK. My main concern is the frequency scaling, though...
jeff c: Oh, another thing...the DSDT that shipped with this machine was a bit buggy...I had to fix it myself.
Sarah: Okay.
Sarah: Jeff, can you please tell me what is DSDT?
jeff c: I was starting to think you left...
jeff c: Differentiated System Description Table
Sarah: :-)
Sarah: Okay.
Sarah: Please give me a few minutes so that I can research on the issue and provide you with the relevant information.
jeff c: My main concern tonight is the CPU frequency scaling...can I change the CPU speed dynamically? For example, if I'm running on battery power, I would want a lower frequency...
Sarah: To do this please follow the steps below.
Sarah: 1.Click Start.
2.Selet Control panel.
3.Now double click Power options Icon.
4.Now under Power schemes option please select Max Battery from the Drop down Box and click Apply and Ok.
jeff c: So it is supported? Excellent
Sarah: You're welcome.
Sarah: Is there any thing else I can assist you with?
jeff c: Just so you know, and I didn't mention it before
Sarah: Sorry I didn't get you.
jeff c: I'm running Ubuntu Linux on this machine. The Windows instructions won't help me much, I just wanted to know if the processor did in fact support this feature. I figured if I mentioned 'Linux' you'd tell me, "Sorry, we don't support that."
Sarah: Jeff, let me provide you with the media card driver as well.
jeff c: For Linux?
jeff c: I thought ENE wouldn't touch Linux?
Sarah: Yes, you are correct.
Sarah: However the Dynamic frequency scaling is not supported by Intel Pentium Processor 4.
jeff c: OK. Thanks for that.
Sarah: You're welcome.
Sarah: Is there any thing else I can assist you with?
jeff c: Um, other than HP supporting Linux 100%, I can't think of anything...
jeff c: :-)
Sarah: Sure.
Sarah: It was a pleasure assisting you today.
Sarah: Bye take care.
jeff c: Thank you. Good bye.
Sarah: In closing, let me add that we appreciate your business and support. I take great pleasure in helping an esteemed customer like you.
Sarah: Thank you for using HP Total Care and giving us an opportunity to serve you through Real-Time Chat.

---

### Post by briancurtin on 2006-04-26
HP support has been great to me in the few questions ive had. im looking into getting a new computer (desktop, have a laptop now) and am leaning towards an HP

---

### Post by _simon_ on 2006-04-26
I used to work in support. Just because something isn't "officially" supported doesn't mean that you won't be lucky enough to speak to someone who can help you with it anyway!

What I hate about online support and was demonstrated above is the "okay" responses. Ok so they aren't supposed to get drawn into chit chat but they seem so 'bot like' sometimes.

---

### Post by trent dillman on 2006-04-26
Take note: dynamic cpu frequency scaling was 'supported' until I mentioned Linux...

wtf...

---

### Post by trent dillman on 2006-04-26
...and, for the record:

```
cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 9
cpu MHz         : 3192.638
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 6388.38

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 9
cpu MHz         : 3192.638
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 6383.55
```

Is that a 'stepping : 9' I see? So I should have 9 speeds I can use? Or am I wrong?

---

### Post by briancurtin on 2006-04-26
[QUOTE=trent dillman]Take note: dynamic cpu frequency scaling was 'supported' until I mentioned Linux...

wtf...[/QUOTE]
she never actually came out and said that it was supported, she just went into explaining something

---

### Post by trent dillman on 2006-04-26
```
jeff c: My main concern tonight is the CPU frequency scaling...can I change the CPU speed dynamically? For example, if I'm running on battery power, I would want a lower frequency...
Sarah: To do this please follow the steps below.
Sarah: 1.Click Start.
2.Selet Control panel.
3.Now double click Power options Icon.
4.Now under Power schemes option please select Max Battery from the Drop down Box and click Apply and Ok.
jeff c: So it is supported? Excellent
Sarah: You're welcome.
Sarah: Is there any thing else I can assist you with?
```

then

```
Sarah: However the Dynamic frequency scaling is not supported by Intel Pentium Processor 4.
```

Just left me to think it was for a minute.

---

### Post by briancurtin on 2006-04-26
i read it the first time...

is what she told you to do even considered CPU frequency scaling? i was not sure, i dont know anything about CPU freq. scaling, and she did not tell you that it specifically is supported, which is where my doubt came from. you asked, and she just went into explaining something that is copied and pasted right off of a list. she probably later on read into it more and found out its not actually supported.

---

### Post by mjg59 on 2006-04-26
[QUOTE=trent dillman]
Is that a 'stepping : 9' I see? So I should have 9 speeds I can use? Or am I wrong?[/QUOTE]

I'm afraid you're wrong. "Stepping: 9" refers to this being the 9th version of the core rather than anything about cpu scaling. Frequency scaling is only supported on P4s if they have the "est" flag, so it looks like yours may not have it.

---

### Post by prizrak on 2006-04-26
AFAIK only the mobile versions of P4 scale. Your readout seems to suggest it's not a mobile CPU. Also Ubuntu has a frequency scaling monitor that will tell you if it supports scaling or not. The directions she gave you were for power saving, it means it's gonna do a # of things one is lower the brightness and turn off the monitor earlier and such, doesn't necessarily mean the CPU will be scaled :)
Edit:
Yeah you definetly don't have a mobile one.
```
 cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Mobile Intel(R) Pentium(R) 4 - M CPU 2.20GHz
stepping        : 9
cpu MHz         : 1197.088
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 2368.23

```

---

### Post by briancurtin on 2006-04-26
thats what i thought. power saving != frequency scaling, at all

---

### Post by trent dillman on 2006-04-28
I'm an ***, I know.

I'd asked about the frequency scaling in particular, not power saving in general. But anyways, I'm not trying to start anything. All I was trying to stress is that, had I been using Windows and followed instructions, yes I would have saved power, but I might have been falsely led to believe my processor had this feature.

And shouldn't a laptop have a mobile processor? :-P

Edit: I can't use a derogatory name for a donkey or one's rear end? I can understand 'f***' and whatnot, but that? Shucks...

---

### Post by prizrak on 2006-04-28
Some of the higher end laptops come with desktop CPU's as power is more important in those than battery life.

---

