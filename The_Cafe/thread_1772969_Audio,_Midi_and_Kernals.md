---
title: "Audio, Midi and Kernals"
date: 2011-06-01
forum: The Cafe
---

### Post by Ken UK on 2011-06-01
Hi,

Can some audio/kernal mastermind explain to me in simple terms what all this talk about audio/midi and different kernals is?

I've tried to read about it from different sources but they say different things so as far as I know there is a 'real time' kernal used in Ubuntu studio which can be installed on a normal Ubuntu installtion for responsive audio recording.

My question is why isn't one kernal adequate of doing all multimedia tasks developed? Maybe its in the pipe line? Why does this not even seem to be a factor in Windows and Mac?

I read somewhere that using a real time kernal can have stability probelsm etc. and that theres two different types, one allowing abit of a delay on tasks before termination and one that allows none.

Thanks,

Ken

---

### Post by mcduck on 2011-06-01
The real time kernel is configured to allow a single program to take as much system resources as it wants, even at the expense of everything else running on that system.

This is great for audio production as it makes sure nothing interrupts the audio server or recording program so you'll get as good quality recordings and low latency for your MIDI applications etc.

For desktop use you'd usually want better balancing between all running programs instead of focusing on a single program.

As Windows and OSX lack the ability to switch between different kernels like Linux does, it's not possible to do this kind of task-specific optimization of the operating system. On those platforms you'll just have to do the best you can to avoid running other applications while working with such tasks, and buy more powerful hardware to keep things working smoothly.

---

### Post by Ken UK on 2011-06-02
Thank you that was as clear as day.

Although I haven't done much myself I have heard that you need the real time kernel to do real audio and get acceptable results, this is why I wondered why that would be the case for Linux and not other OS's.

Also I read that getting above certain latency values in JACK means you are likely to get poor results and with my standard setup I was indeed getting much higher numbers.

I will give it a good go and see if its true or not.

---

### Post by ErikNJ on 2011-06-02
I suggest trying to work without the RT kernel first and see if it's acceptable for you.  Ultimately, the RT kernel may yield lower latency for you (by allowing smaller buffer sizes without dropouts) but if you don't have too many services running, the regular kernel may do just fine.

---

