---
title: "MB &amp; CPU recommendations"
date: 2011-01-01
forum: Ubuntu Studio
---

### Post by garyed on 2011-01-01
I'm planning on putting together another box just for a DAW with U-studio 10.04. I'm not trying to go top of the line but just something moderately priced that will do a good job. The last box I built quite a few years ago still does everything I need running Windows w/ Sonar & Gigastudio  & it only has AMD64 3700+ cpu w/ 2 gig of ram. It just hasn't worked well with the last few versions of U-studio so in order to ween myself off Windows I want to build a new box. If anyone would like to fill in any of the blanks with their ideas I would appreciate it:

Existing PCI Sound card - M-Audio Audiophile 2496 

1 - Motherboard

2 -CPU

3 - Ram 

4 - Hard drives

---

### Post by gordintoronto on 2011-01-01
First, I suggest you confirm that your sound card will work with Ubuntu. Most people use the audio on the motherboard, so sound cards are not well tested.

Here are some components you could consider:
motherboard: [http://www.newegg.ca/Product/Product.aspx?Item=N82E16813128455](http://www.newegg.ca/Product/Product.aspx?Item=N82E16813128455)
CPU: [http://www.newegg.ca/Product/Product.aspx?Item=N82E16819103817](http://www.newegg.ca/Product/Product.aspx?Item=N82E16819103817)
Hard drive: [http://www.newegg.ca/Product/Product.aspx?Item=N82E16822136319](http://www.newegg.ca/Product/Product.aspx?Item=N82E16822136319)
and a really good power supply, such as:
[http://www.newegg.ca/Product/Product.aspx?Item=N82E16817371023](http://www.newegg.ca/Product/Product.aspx?Item=N82E16817371023)
(unless you are going with a high-end video card, which will need much more power.)
Memory: 2 GB from the motherboard's certified list.

I am happy with my Gigabyte motherboard, but it's not that one. I do have that hard drive, and an AMD Phenom II processor.

You could also try the PCMech web site for suggestions.

---

### Post by gordintoronto on 2011-01-01
Here's some interesting reading:
[http://dev.modmancer.com/index.php/2010/05/15/m-audio-audiophile-2496-on-ubuntu-9-10-no-sound/](http://dev.modmancer.com/index.php/2010/05/15/m-audio-audiophile-2496-on-ubuntu-9-10-no-sound/)

I found it by Googling: audiophile 2496 ubuntu

---

### Post by cchhrriiss121212 on 2011-01-01
What I would recommend first is that you try a lightweight OS. Ubuntu uses Gnome, but you can always swicth to LDXE or IceWM. Maybe try out [AVLinux]("http://www.bandshed.net/AVLinux.html").

Your specs are good enough to multitrack audio, and I don't like to see people buying new hardware when their old stuff still works.

---

### Post by garyed on 2011-01-01
Thanks for the ideas so far.
I probably should have explained where I am a little better.
I've got U-studio 7.10 working perfectly on my existing system.
I've tried every version since then except for 10.04 but I had latency problems will all the others so I'm stuck with 7.10 right now. I did try 64 Studio with the same latency problems. The audiophile 2496 is supposedly supported but I've heard of some reported problems with that card & Linux. 
I'm not opposed to going with another sound card if thats what I need. I'd also like to hear some specs from those who have a good working Linux DAW. I've been using Ubuntu for about 3 years so I'm very comfortable with the OS but I'm not locked in if there's a better alternative. The bottom line is I want a complete Linux DAW system where I don't have to rely on Windows for any type of recording or editing.

---

### Post by cchhrriiss121212 on 2011-01-02
You don't need a new card, the delta series just has a bug with pulse audio that is easily fixed once you know how (see post 3). 

Newer versions of Ubuntu should actually perform better than 7.10 since they have more efficient kernels and now use jack2 by default which makes use of dual core cpus. 64studio is ancient now and does not appear to be under development. I'd recommend you try out 10.04 with a light DE.

Linux does not have DAWs like windows does, it is all designed to be modular. I use:
qtractor - for multitrack audio/MIDI/plugins
audacity - occasional edits
rakarrack - guitar fx
hydrogen - drum sequencing
jamin - mastering

---

