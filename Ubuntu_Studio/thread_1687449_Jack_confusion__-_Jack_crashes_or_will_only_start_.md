---
title: "Jack confusion  - Jack crashes or will only start after Ardour starts"
date: 2011-02-13
forum: Ubuntu Studio
---

### Post by windeguy on 2011-02-13
Hello Again all. A little background.  I had my laptop up and running Ubuntu Studio 10.10 with either a generic kernel or the 2.6.33-29-realtime kernel after very good advice given here. 

I had a system problem after what I expected to be a routine upgrade of packages and I could no longer boot. So I started over with a clean hard drive and decided to install Ubuntu Studio 10.04 LTS in the hopes of more stability.  I retraced my steps as best I could to get everything running as I had before.  I now have generic kernel 2.6.32-21 and the 2.6.33.29-realtime kernel.   I am using what were stable settings in Jack before. 

When I try to start JACK it crashes.  I get the following Messages from Jack:

20:35:58.338 Patchbay deactivated.
20:35:58.392 Statistics reset.
20:35:58.411 ALSA connection graph change.
20:35:58.614 ALSA connection change.
20:36:09.491 Startup script...
20:36:09.492 artsshell -q terminate
sh: artsshell: not found
20:36:09.894 Startup script terminated with exit status=32512.
20:36:09.894 JACK is starting...
20:36:09.895 /bin /usr/bin/jackd -t5000 -dalsa -dhw:0 -r48000 -p32 -n3 -s
20:36:09.898 Could not start JACK. Sorry.
20:36:11.630 JACK was stopped successfully.
20:36:11.631 Post-shutdown script...
20:36:11.632 killall jackd
jackd: no process found
20:36:12.061 Post-shutdown script terminated with exit status=256.

If I first start Ardour, JACK will run. I certainly did not have to start any programs before I started Jack before, in fact quite the opposite, I needed to start Jack before starting some programs. The behavior is the same if I use the generic or realtime kernels.

As I mentioned,  Jack will run if I start Ardour first and I just discovered that Jack will run if I enter the following command in the terminal window:

$sudo jackd -R -d alsa

Any ideas what I missed or what I can check to debug this problem?

---

### Post by Pablo_F on 2011-02-14
Hi, 

So far, you know three different ways of starting the jack server (or the jack daemon, or jackd or "jack").

1) qjackctl -> Start button
2) ardour 
3) command line

What happens here is that you are using different parameters and options, depending on how you start the server, which is a bad idea.

When you start from the command line, with "sudo jackd -R -d alsa", in adition to realtime mode (although you don't really need -R because this is the default) and alsa driver, you are implying the following:

audio card: hw:0
1024 frames per period 
sample rate: 48000 Hz
2 periods per buffer

because these are defaults. 


With regards to qjackctl's failure:

"/bin /usr/bin/jackd -t5000 -dalsa -dhw:0 -r48000 -p32 -n3 -s"
is incorrect. 

Write "/usr/bin/jackd" or simply "jackd" in the "server path field". Normally, 2 periods per buffer (-n option) is better and 32 frames per period (-p option) is extremely low. Be more conservative. 

You can check the complete jackd command in the message window and also (for example if you set the jackd command via ardour's audio configuration) you can always use the following informative command when jackd is up and running:

ps -eo command | grep jackd

(ignore the grep line in the output, of course)

You have a reference on every jackd option, by typing *man jackd* in a terminal. 

Cheers, Pablo

---

### Post by windeguy on 2011-02-15
Hi Pablo, 

Once again Pablo, a very insightful reply. Thank you. Knowing the full details of what Jack does and its settings is better than "not knowing JACK" ;)

What I found that seemed to be causing my problem was that in qjackctl there was a startup script enabled to run after I re-installed Ubuntu Studio.  I unchecked the box for the startup script and now Jack starts without a problem using qjackctl and hitting the start button. 

I will experiment with the frames/buffer and periods per buffer settings for both the built in RealTek HD audio chip and my Lexicon Omega USB interface. 

And I was getting latencies under 10 ms for both the internal audio and the Lexicon Omega that seemed to be pretty stable using the -realtime kernel.


Anxiously awaiting Ardour 3 to be released. Any behind the scenes news on when the Beta will be available?

---

