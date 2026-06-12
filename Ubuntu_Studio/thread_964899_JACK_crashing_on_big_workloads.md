---
title: "JACK crashing on big workloads"
date: 2008-10-31
forum: Ubuntu Studio
---

### Post by Boneless on 2008-10-31
Hi everyone,

I have Jack 0.109.2 installed, and whenever I try the following configuration:

- JACK Keyboard
- a2j (for letting JACK keyboard communicate with...)
- QMidiArp (feeding MIDI in...)
1) ZynAddSubFX-CVS (4 different patches)
2) Sineshaper (DSSI)
3) Nekobee (DSSI)

(not everything is in the repos... for example, JACK Keyboard isn't, and so is a2j, and I REFUSE to use vkeybd since it is so crappy and outdated... I know, I should use a master keyboard and a sequencer, but I don't have a master keyboard), after working all right for a few minutes, it just crashes.
Although sometimes it's just Zyn crashing (I think its JACK implementation is kinda iffy), other times it's the entire JACK server.

I am on Ubuntu Gutsy 7.10 (hadn't had the chance to upgrade to Hardy or Ibex), and I'm using a 2.6.22-14-generic kernel. The rt kernel just freezes before even booting (it doesn't even access to the disk, and there are no error messages, I tried with noapic nolapic acpi=off but with no result). My soundcard is an Echo Indigo IO. I have to admit my PC is kinda old (it's a Compaq nx8220) but it should get along fine, I suppose. I am running JACK as realtime, anyway.

If anyone can help me about this I would greatly appreciate it.
And if anyone can sort out my realtime kernel issue, virtual beer offered :D

Here are the kernel messages before the realtime kernel (by the way, release 2.6.22-15-rt) freezes on me (no response at all by my PC, I'm forced to hard reset):

```

[9.00whatever] kernel_init+0x141/0x360
[9.00whatever] _switch_to+0xaa/0x1d0
[9.00whatever] schedule_tail+0x53/0x120
[9.00whatever] ret_from_fork+0x6/0x20
[9.00whatever] kernel_init+0x0/0x3b0
[9.00whatever] kernel_init+0x0/0x3b0
[9.00whatever] kernel_thread_helper+0x7/0x10
[9.00whatever] =============================

```

---

### Post by Boneless on 2008-11-01
bump

---

### Post by Boneless on 2008-11-01
bump again

---

### Post by Boneless on 2008-11-06
sblomp.

---

### Post by kayosiii on 2008-11-07
keep an eye on your cpu usage - also make sure that zynaddsubfx is set to use the same sample rate as jack (some zyn patches can bring even a fast system to its knees). What soundcard are you using?

---

