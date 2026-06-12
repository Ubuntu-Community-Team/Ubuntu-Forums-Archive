---
title: "*Another* jack problem"
date: 2012-04-15
forum: Ubuntu Studio
---

### Post by Overthere on 2012-04-15
Hello,
I've been playing around with using Jack on my system, but can't get it to work properly.

When I start QJackctl, I get this:
```
D-BUS: JACK server could not be started
```

and this:
  p, li { white-space: pre-wrap; } 
```

Could not connect to JACK server as client.
  - Overall operation failed.
  - Server communication error.
  Please check the messages window for more info
  
 
```


The message window gives:


```
  p, li { white-space: pre-wrap; }  
[COLOR=#ff0000]Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 JackSocketClientChannel read fail
 Cannot open qjackctl client

```


In Patchage, I try to connect JACK, but it fails. Obviously, any client using Jack also doesn't open.
Patchage also tells me that I am connected to ALSA, but I can't hear any audio coming from my web browser or Audacious.


How do I fix this?




Much thanks in advance,
brian

---

### Post by jejeman on 2012-04-15
Turn off d-bus support in qjacktl settings.

---

### Post by Overthere on 2012-04-20
I turned it off, but I still get the error:

```
  p, li { white-space: pre-wrap; }  [COLOR=#ff0000]Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 JackSocketClientChannel read fail
 Cannot open qjackctl client

```

What is the method to get jack to function correctly? Is it as simple as opening QJackCtl and clicking "start?"


Brian

---

### Post by sgx on 2012-04-21
Hi, do a quick google of your soundcard/motherboard soundchip name
with ubuntu qjackctl

there should be several discussions to read. These commands list
playback and recording devices.

aplay -l
arecord -l
aconnect -i
aconnect -o
cat /proc/asound/cards
lspci
lsusb
lsmod (lists kernel modules)

Items in brackets can be inserted in
qjackctl setup page 

Input Device >
OutputDevice >

click > widget to see your soundcards. Replace hw:0 or similar with the
soundcard name in brackets from aplay -l

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)  screenshots and configs
at links 4 and 8 on the wiki page, many videos on youtube, for
hydrogen, ardour, zynaddsubfx, rakarrack will also cover
qjackctl connections.

---

### Post by Overthere on 2012-04-24
> **sgx said:**
> Hi, do a quick google of your soundcard/motherboard soundchip name
with ubuntu qjackctl

there should be several discussions to read. These commands list
playback and recording devices.

aplay -l
arecord -l
aconnect -i
aconnect -o
cat /proc/asound/cards
lspci
lsusb
lsmod (lists kernel modules)

Items in brackets can be inserted in
qjackctl setup page 

Input Device >
OutputDevice >

click > widget to see your soundcards. Replace hw:0 or similar with the
soundcard name in brackets from aplay -l

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)  screenshots and configs
at links 4 and 8 on the wiki page, many videos on youtube, for
hydrogen, ardour, zynaddsubfx, rakarrack will also cover
qjackctl connections.

Thanks for all the suggestions, sgx.
I finally have everything working, even though I really don't know what it is that made everything fit together. I tried changing hw:0 with other options, but that didn't work.  But when I rebooted, the settings were back to their original ones, and things are working!

So for now I'm happy as a lark, with several softsynths that are all working as they should. A bit of a mystery, but QJack is working nonetheless!

hopefully your post will be of help to others, too! :)

Thanks again.
brian

---

