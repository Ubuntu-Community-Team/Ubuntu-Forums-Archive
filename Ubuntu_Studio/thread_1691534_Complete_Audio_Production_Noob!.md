---
title: "Complete Audio Production Noob!"
date: 2011-02-20
forum: Ubuntu Studio
---

### Post by emoguitarist06 on 2011-02-20
I have an Asus 1201N Eee PC 

and I want to run either Ubuntu Studio x86_64 or KXStudio x86_64
to get my feet wet in this whole audio production scene but I have NO CLUE what I'm doing and whenever I try to read about Jack or Ardour I get confused lol... I tried plugging in my friends M-Audio Fast Track Pro and Ardour doesn't recognize it and I'm not quite sure how to do the connections in Jack

Basically what I'm trying to say is, what video or book or website that any of you can direct me to to learn how the basics

---

### Post by Sylos on 2011-02-20
Hello and welcome to the audio production side of the moon.

As far as learning the basics is concerned it depends on what you already know about audio production. If we assume you know nothing about how music gets recorded and produced then you may be best to start with something like Tweak Headz lab

[http://www.tweakheadz.com/](http://www.tweakheadz.com/)

The author has some good intoductions to the hardware and software options and how midi can fit into the mix.

Above and beyond this Im not sure if I know of anything that will be easy to understand if jack/ardour info confuses you. In all honesty I have found that the best way to learn is to leap in and try to get it working. When you get stuck post in the forums and one of the experienced users will no doubt help you out (there are some really good users in the studio section who do some heroic work in getting us lesser mortals to obtain a working set up).

I would probably say the best way is to install Ubuntu Studio or KX alongside your exsting set up as a dual boot. Then you can set everything up and not worry about breaking things too much.

If you can stomach it, try some of the sites below:

[http://www.linuxaudio.org/](http://www.linuxaudio.org/)

[http://www.linux-sound.org/](http://www.linux-sound.org/)

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

---

### Post by Pablo_F on 2011-02-20
> I tried plugging in my friends M-Audio Fast Track Pro and Ardour doesn't recognize it and I'm not quite sure how to do the connections in Jack

Ardour will not show your audio card by name. Ardour talks to jack so the crucial thing here is that **you have to tell jack to use the m-audio**. 

After you start the jack server by means of qjackctl (Jack Control), press the connect button. You will see three tabs. By the time being, ignore MIDI and ALSA tabs (both are for midi). In the audio tab you should see a client called "system" with capture and playback ports. This "system" is the generic name that jack gives to the audio card that is using. 

Press the setup button and make sure that the "interface" is the m-audio (note the drop down list). If you have an onboard card, jack is probably using by default.

Cheers, Pablo

---

### Post by sgx on 2011-02-20
> **emoguitarist06 said:**
> I have an Asus 1201N Eee PC 

and I want to run either Ubuntu Studio x86_64 or KXStudio x86_64
to get my feet wet in this whole audio production scene but I have NO CLUE what I'm doing and whenever I try to read about Jack or Ardour I get confused lol... I tried plugging in my friends M-Audio Fast Track Pro and Ardour doesn't recognize it and I'm not quite sure how to do the connections in Jack

Basically what I'm trying to say is, what video or book or website that any of you can direct me to to learn how the basics

search youtube for ardour, hydrogen, zynaddsubfx, qjackctl, and rakarrack.

Many of these will cover the basic connections of jackd, and its gui, qjackctl, and then move on to recording or performing.
 
Check the qjackctl wiki, and google like mad, great info is available!

In qjackctl, in the connect panels, you highlight items, one on each side, then press the connect button.
A line appears indicating connection. On the setup page,

Input device >
Output device >

click the  >  widgets to see your soundcard options.

:guitar:

---

### Post by ankanlento on 2011-02-20
fast track pro wont work 24bit/96kHz in ubuntu. Even to work 16 bit it needs hours of fighting. They aren't able to do working drivers.

---

### Post by maghoxfr on 2011-02-21
In the begining I realized that most of my questions were impossible to be answered on a forum. People can help you but you have to do most of the work. So, google a lot and look for youtube videos. This forums are awesome, but they work best if the question is more specific. You'll realize that once you have a specific question results are much faster and straight forward.

The [ubuntu help documentation]("https://help.ubuntu.com/") page is very useful. The [linuxmusicians]("http://www.linuxmusicians.com/") forums are great too. At first it will be too much to handle, I had a rough time because there's so much information that it's hard to know what information is essential and waht you can let go. My advice is to focus on your immediate needs, don't start diving much into the developing aspect of things (unless you have any idea of course) because it will take tons of time from you.

The learning curve is sometimes discouraging, that's when the great community helps, because noone ever said to me, RTFM, or this is not for you etc.

Be sure to read about jack configuration, the connections are pretty straight forward if you are familiar with real life mixers. I use Qtractor to record/mix, Hydrogen as a drum machine, Rakarrack for effects, Yoshimi/Phasex as synths. 

There's tons of software, so will have to try for yourself and decide.

Cheers mate!

---

