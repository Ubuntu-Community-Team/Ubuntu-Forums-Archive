---
title: "Ubuntu studio 8.10, rt-kernel + ALSA midi?"
date: 2008-11-27
forum: Ubuntu Studio
---

### Post by kurppa on 2008-11-27
Hello,
What I try to do is to play Hydrogen drum machine with my MIDI keyboard in 32-bit Ubuntu studio real time kernel (Linux ubuntu 2.6.27-3-rt #1 PREEMPT RT). I am using Qjackctl to connect ALSA midi to Hydrogen inputs but get no response when playing notes. However, when booting into generic kernel things work just fine and drumming is ok.

I also made a weird observation. After sending midi notes to Hydrogen in real time kernel I accidently hit backspace key at command line in terminal window. This triggered those pending midi notes in Hydrogen...so something inhibits midi communication? Whenever hitting backspace in Terminal command line, Hydrogen shows MIDI input. Any ideas or similar experiences?

my soundcard is m-audio delta 1010lt.

---

### Post by thorgal on 2008-11-27
unless someone has a better option, I'm afraid you'll have to downgrade your kernel version. I am advising an RT patched 2.6.24 kernel if your hardware is well supported by this version.

---

### Post by raboofje on 2008-11-27
Agreed. I found the non-realtime 2.6.27 kernel to perform surprisingly well as well.

LP item for MIDI performance in the RT kernel: [https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/300806](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/300806)

---

### Post by kurppa on 2008-12-02
Hi, thanks for replies. I found ubuntu studio 8.04 installation dvd and did a clean install. And it just worked out of the box. 
Now running 2.6.24-22-rt and midi ok.

---

