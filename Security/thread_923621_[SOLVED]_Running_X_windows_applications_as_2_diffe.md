---
title: "[SOLVED] Running X windows applications as 2 different users"
date: 2008-09-18
forum: Security
---

### Post by spibou on 2008-09-18
I have created an alternative account , let's call it nottrusted , which I use for running applications I don't completely trust. So I log in as my usual user name , open a terminal emulator and in that I do "su nottrusted". The idea is that everytime I want to run an application for whose security I have doubts I go to that particular terminal and run the application from there. The problem is that if I try to run an application which opens a new window I get

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
** ERROR **: Unable to open display

Is there a way around that? One idea of course would be to log in as nottrusted but I also want to be able to start X windows applications under my usual user name.

---

### Post by cariboo on 2008-09-18
Why not just user fast user switch, I'm running mint right now and not close to a computer running Ubuntu, so I'm doing this from memory, but this will start another X session and you should be able run the untrusted binary.

Jim

---

### Post by lswb on 2008-09-18
X won't let the 2nd user start a program on the 1st user's X session.

If you're intending to run X as the 2nd user, why not just login in as that user via gdm? (or kdm or whatever display manager your system is using) Select switch user from the Quit or shutdown menu. After you are logged in to the 2nd account, You can switch between the displays for your normal login and the untrusted login with <Ctrl-Alt-F7> & <Ctrl-Alt-F9> (usually F9, sometimes might be F8 or F10,11,12)

If for some reason you need to start the 2nd X session from a command line, terminal, probaly the simplest way is to switch to a vt via <Ctrl-ALt-F1> (through <Ctrl-Alt-F6>) login as the 2nd user,  and use the command "startx -- :1"

---

### Post by spibou on 2008-09-18
> **lswb said:**
> X won't let the 2nd user start a program on the 1st user's X session.

If you're intending to run X as the 2nd user, why not just login in as that user via gdm? (or kdm or whatever display manager your system is using) Select switch user from the Quit or shutdown menu.

The shutdown menu does not seem to offer a switch user option. When I click on "System" I get a menu which on the bottom has "Quit". If I click on that I will just get logged out.

> 
If for some reason you need to start the 2nd X session from a command line, terminal, probaly the simplest way is to switch to a vt via <Ctrl-ALt-F1> (through <Ctrl-Alt-F6>) login as the 2nd user,  and use the command "startx -- :1"

That worked. Actually this killed 2 birds with 1 stone because I have been wondering for quite a while how to start an X session from console. I had come across startx (and xinit) but the man pages didn't tell me how to achieve my goal.

But I still have a problem in that the alternative session does not have sound. For example if I try
```
/usr/bin/speaker-test -t pink -p 2000000000 -r 100
```
I get
```

speaker-test 1.0.11

Playback device is default
Stream parameters are 4000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Playback open error: -19,No such device
```

on stdout and

```

ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device

```

on stderr.

---

### Post by lswb on 2008-09-18
> **spibou said:**
> The shutdown menu does not seem to offer a switch user option. When I click on "System" I get a menu which on the bottom has "Quit". If I click on that I will just get logged out.


You might try adding a "Quit" button to the panel if you use the gnome desktop and don't already have one. Right-click on a panel, select Add, then look for the "Quit..." applet. If you still don't have the switch-user options there may be some configuration options available in the configuration editor. There is also a "user switcher" panel applet you can add the same way.

> **spibou said:**
> 
But I still have a problem in that the alternative session does not have sound.

I don't think I can help with that. Probably best to open a new thread for the sound problem if you can't find the answer with a forum or web search.

---

### Post by spibou on 2008-09-20
> **lswb said:**
> 
[QUOTE=spibou;5815195]But I still have a problem in that the alternative session does not have sound.
I don't think I can help with that. Probably best to open a new thread for the sound problem if you can't find the answer with a forum or web search.[/QUOTE]
As it turned out the answer was simple, I only needed to add my nottrusted account to the audio group.

---

