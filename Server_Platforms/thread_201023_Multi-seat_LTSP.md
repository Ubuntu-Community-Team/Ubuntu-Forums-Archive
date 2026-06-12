---
title: "Multi-seat LTSP"
date: 2006-06-21
forum: Server Platforms
---

### Post by fnjordy on 2006-06-21
The minimum hardware requirements for a LTSP terminal in their Wiki state > 24MB / P133 is not noticeable.  This translates to me that if I had a 128MB/P3 300Mhz terminal I might be able to drive 4 multiseat terminals from one LTSP client computer.

Here is a diagram showing the three different client setups of LTSP:

[[IMG]http://img135.imageshack.us/img135/8658/ltsphead0tv.png[/IMG]](http://imageshack.us)

[LIST=1]
[*]Multi-Seat:  two or more sets of monitor/keyboard/mouse/sound devices connected to one machine.
[*]Multi-Head:  two or more monitors connected to one machine as a larger desktop for one use, known as Xinerama or TwinView for Nvidia cards.  This was supported in LTSP-4.2.
[*]Regular one monitor and computer terminal user.
[/LIST]

This allows a far larger deployment at a cheaper cost than one computer per terminal would.  But has anybody tried this, I haven't found any documentation stating work on such a configuration?  Ubuntu 5.10 has multiseat configuration out of the box (X 6.9/7.0) and there are companies selling multiseat computer systems for libraries.  So it should be a nice solution to join both setups together.

-- 
Steve-o

---

### Post by pogson on 2006-07-04
I second that. I am working on a project to install EdUbuntu on a huge server for a whole school. By using gigabit lines from the server to the multi-seat clients, I could reduce cables/switches/outlets/labour as well as CPUs. Unfortunately my school has many small offices which can barely seat more than one so we are looking at using the multi-seat thin clients in the larger spaces like classrooms, library and labs and using single seats in the offices. The savings is still huge. My multi-seat thin client (new barebones AMD64 3000 with six video cards) costs about $100 per seat, and the single-seat thin clients cost about $180 per seat, way less than the thick-client mode... I am working on a prototype now and found it interesting but doable to have both 32bit and 64bit clients running natively. Bravo LTSP and Ubuntu, a match made in heaven. 

Features I would like to see in Edgy thin client/server are multi-seat, mixed architectures (looks good, in Dapper), local devices (LTSP-4.2 lacks AMD64 throughout, but Ubuntu has some parts), and local apps. The future looks good. I may have to install i386 this summer and use LTSP-4.2 to get most of what I want this year, but that is only my backup plan. I want to wring every mips out of my expensive server (8-way Opteron).

---

### Post by fnjordy on 2006-07-05
Wow nice, how are you implementing this multi-seat?  I have put up a page on the LTSP wiki you can add some notes :)

  [http://wiki.ltsp.org/twiki/bin/view/Ltsp/MultiSeat](http://wiki.ltsp.org/twiki/bin/view/Ltsp/MultiSeat)

I found a supplier listing cheap thin clients, half the usual price but haven't heard back from my request:

> It is priced $99 to $119 per unit.

  [http://www.globalsources.com/gsol/I/Thin-client/a/9000000070390.htm](http://www.globalsources.com/gsol/I/Thin-client/a/9000000070390.htm)

---

