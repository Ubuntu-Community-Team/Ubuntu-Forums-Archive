---
title: "Jack - xruns again"
date: 2011-02-07
forum: Ubuntu Studio
---

### Post by metalkrapo on 2011-02-07
Hi everyone,

I've been using Ubuntu Studio for some time now, with a M-Audio Fast Track USB soundcard. I've been upgrading for several versions.

Lately I wanted to do a fresh install to get rid of several problems, so I formatted my disk and installed 10.10.

Unfortunately jack produces many more xruns than it used to. I have searched these forums and found out that realtime kernel was no longer supported.

What are the options in order to get jack running as smoothly as before?

Thanks for your help.

---

### Post by AutoStatic on 2011-02-07
Hello metalkrapo, what JACK settings are you using?
Those settings are in the ~/.jackdrc file.
And with which release did it work well?

Best,

Jeremy

---

### Post by metalkrapo on 2011-02-07
Hi Jeremy, thanks for trying to help.

Here is the content of ~/.jackdrc:

/usr/bin/jackd -r -dalsa -r44100 -p512 -n2 -D -Chw:1,1 -Phw:1,1 -i2 -o2

And here is the Settings window: [http://img831.imageshack.us/img831/6534/jackmi.png](http://img831.imageshack.us/img831/6534/jackmi.png) although I unchecked 'Realtime' when I understood there is no longer a realtime kernel.

It worked fine with the realtime kernel on Ubuntu 10.04 and several previous versions.

Thanks again!

---

### Post by AutoStatic on 2011-02-07
Salut metalkrapo, encore un autre LinuxMAOiste!

You don't need a real-time kernel in order to be able to run JACK in Realtime mode. And an USB card will perform better with a Periods/Buffer setting of 3 instead of 2. I would also lower your JACK priority, 89 is too high, try something around 70.
I think in your case it's the Realtime setting that is the bottleneck. Try enabling it and see if that works better.

Ciao,

Jeremy

---

### Post by metalkrapo on 2011-02-07
En effet :)

Unfortunately it didn't help, i still get almost 1 xrun per second while playing back an empty Ardour session.

Any more ideas?

---

