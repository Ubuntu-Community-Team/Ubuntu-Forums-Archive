---
title: "Meerkat Ion Freezes?"
date: 2011-05-29
forum: System76 Support
---

### Post by LinuxGuyInVA on 2011-05-29
My almost-two-year-old Meerkat Ion Nettop has suddenly developed a habit of "*freezing*" (though I use the word with trepidation as I think it might be heat related).  It started happening yesterday, though I suspect it might have happened very occasionally in the past.  

The symptom is fairly hard to miss: catatonic computer.  Keyboard and mouse non-responsive (yes, I tried switching to virtual consoles 1-6 and the usual three-finger salutes ctrl-alt-backspace, ctrl-alt-delete), screen frozen with clock indicating the time it occured, can't ssh in from another system, no ping responses.  Nothing obsious in the logs around the time of the crashes either.  The only cure is the 4-second-power-button-press.

I noticed the system was *very* hot after these incidents, so I got the sensors going so the [FONT="Courier New"][COLOR="Navy"]sensors[/COLOR][/FONT] command worked.  

On bootup, the two cores are a pleasant 23°C or so.  I started an rsync job to back up critical content to another system, and watched the temperatures climb steadily as the job progressed.  They got up to 77°C at one point, which was a bit unnerving given the "critical" temp as indicated in the [FONT="Courier New"][COLOR="Navy"]sensors[/COLOR][/FONT] output.  They settled down after the rsync was done to:

```

[INDENT]
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +71.0°C  (crit = +90.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +72.0°C  (crit = +90.0°C)
[/INDENT]

```

which is way hotter than my (Dell) laptop.

The Meerkat model I got has no fans, just some giant heat sinks on the processors.  Several months ago I upgraded it to Ubuntu 10.04 as the release it came with was no longer getting updates.  What I'm wondering now is perhaps I missed some setting or module tweak to prevent the thing from overheating during this update.  The box certainly had no problems dealing with the heat in the summer of 2010 (and we have A/C this year so it's not even particularly hot in here).

If any of this rings a bell with others here, this Linux geek would sure appreciate a heads up.  Things I'm specifically looking for would include:

[LIST]
[*] CPU Frequency Scaling options
[*] ACPI Settings
[*] Module changes (already have coretemp, lm90)
[*] BIOS tweaks
[/LIST]

and anything else that might help.

 - Pat (Ubuntu since 2006; Linux since 1993)

---

### Post by LinuxGuyInVA on 2011-08-03
Some additional information.  After some advice from a System 76 staffer (thanks!) I powered down the box, took it outside, opened it up and had at it with the air compressor.  Lots of dust.  Putting it back in one piece, and firing it up **seemed** to show a slight improvement in the temperature it typically ran.

After this, I put in a cron job to dump some of the output of the [FONT=Courier New]sensors[/FONT] command into syslog (via [FONT=Courier New]logger[/FONT])  every 5 minutes, to get an idea of how hot the processors really are.  Plotting this shows a nice asymptotic curve for the first few hours the system is turned on.  The system starts at ambient temp (mid 20's Centigrade) and then it likes to cruise around 70-80 degrees Centigrade, but the kernel thinks the critical temperature is 90.  Any serious computational load, or if the room gets a little warm (it is air conditioned) and it gets REALLY close (mid 80's):

[IMG]http://chien-noir.com/meerkat-temp.png[/IMG]

In the last few days I see a couple of times where there were several warnings such as:

```
Aug  3 19:32:25 blackwolf kernel: [99228.287181] CPU1: Temperature above threshold, cpu clock throttled (total events = 24008)
```Followed very quickly by:

```
Aug  3 19:32:25 blackwolf kernel: [99228.288131] CPU1: Temperature/speed normal
```As far as I know, this was not happening right after I cleaned it.  And as I write, it's down to 78 degrees again.  What's weird is those throttling events occured while nobody was actively using the system, just the screen saver (and I have it in turn toned down: it's the f-spot favourites one, but it pauses 15 seconds between images, not the default 2-3 seconds).

Think I'm going to have to look at adding a fan to this thang :-?

 - Pat

---

