---
title: "X randomly restarting (I think)"
date: 2009-07-03
forum: System76 Support
---

### Post by gila_monster on 2009-07-03
A while back, I reported that X had restarted suddenly in the middle of a session. The gist of the responses was that I might have accidentally done something like hit ctrl-alt-backspace. I didn't think I did, but I had my hands on the keyboard at the time, so it was possible. It didn't happen again, so I ignored it and went on.

In the past three days, however, X has restarted suddenly TWICE. I had my hands on the keyboard neither time. The first time, I was swapping to another workspace. Tonight, I was doing nothing, just reading a web page, and off it went. 

I don't know where to start with this. The temps on the GPU and CPU seem fine, nothing else out of the ordinary was going on, and I really only had Evolution, Firefox, and a terminal window open at the time of the events. I don't mind spending some time debugging this, but if someone can give suggestions on where to start, I would appreciate it.

Other information that may be relevant: Compiz is running, and I used the Compiz settings manager to set up some custom stuff (wallpapers, cube, some extra effects). I suppose there could be an interaction between X and Compiz, as I set "Force synchronization between X and GLX" true in the Workarounds to help with the NVIDIA problem (where it didn't refresh the screen properly on scrolling and whatnot). Is that workaround still required?

Given what I do with the machine during the day, reliability and uptime are incredibly important to me. I can't have this happen in the middle of one of our emergency response calls. Any help welcome.

---

### Post by 3Miro on 2009-07-03
System 76 driver has the option to create a crash log option. I suspect Tomas would ask you for such a log from right after a crash.

My two cents on the subject: if you need reliability, don't use compiz. Use metacity instead. Metacity has no 3D effects, but it is way (and I mean WAY) more stable than compiz.

I myself have experienced several bugs with compiz. For example TexMaker (which is a program of extreme importance to me) wouldn't sometimes refresh properly. I would delete some text and then it will not show as deleted. Also the blinker cursor will not show correctly on which place of the text I am. All of those are compiz + TexMaker bugs.

Compiz also takes more resources, so turning it off will make things work faster (somewhat, if you are not running anything resource demanding then it will not make a difference).

I tend to believe that nothing as complicated as graphical environment can be 100% bug free. The extreme measure in this case would be to move over to a terminal only mode. Depending on what you need to run and how important it is, this may or may not be a good idea.

---

### Post by gila_monster on 2009-07-04
> **3Miro said:**
> System 76 driver has the option to create a crash log option. I suspect Tomas would ask you for such a log from right after a crash.

Oh, I know he would. And I will when it happens again. (I was called away by bickering kids right when it happened and didn't get a chance to play with it.)

> My two cents on the subject: if you need reliability, don't use compiz. Use metacity instead. Metacity has no 3D effects, but it is way (and I mean WAY) more stable than compiz.

Have been considering that. In fact, I'm using Metacity for the window decorations already anyway. I'll miss the shiny, but if it's compiz causing the problem, I'll jettison it in a heartbeat.

Thanks, 3Miro. Much appreciated.

---

### Post by thomasaaron on 2009-07-06
Yes, next time it happens go to System > Administration > System76 Driver > Support > Create. Attach the logs.tar file created in your home directory.

How long was the computer up before the crash happened (i.e. hours? days?)?

---

### Post by gila_monster on 2009-07-06
> **thomasaaron said:**
> Yes, next time it happens go to System > Administration > System76 Driver > Support > Create. Attach the logs.tar file created in your home directory.

How long was the computer up before the crash happened (i.e. hours? days?)?

Between six and ten hours...wasn't really tracking it. I shut down every night. It wasn't an unusual amount of time for how I use the box. Pretty happy with the Pangolin overall, but these things....

I had compiz turned off over the weekend. I'll fire it back up (and try to restore the custom settings I had) and see if I can catch it in the act. We might learn something.

---

### Post by gila_monster on 2009-07-11
> **thomasaaron said:**
> Yes, next time it happens go to System > Administration > System76 Driver > Support > Create. Attach the logs.tar file created in your home directory.

Got one! Attached.

I was about to say, "Woo hoo! Got one!" and then realized I'm cheering about my system crashing.

So I may now go turn compiz off, and see if I get a crash later.

This crash, incidentally, happened as I was exiting Kompozer after editing some web pages. Firefox 3.5 was up, and Evolution. Not a lot else in use at that point. Previous two crashes happened when closing Firefox, and once when doing nothing at all. So I am thinking that turning compiz off won't help a lot.

Tom, I can send to you via direct email if you prefer. And of course everyone else is free to poke around. About to do so myself.

EDIT: looking at the log file, it seems really unhappy about a screensaver. I'm going to go turn that off and set it to just turn off the screen, just in case.

---

### Post by thomasaaron on 2009-07-13
OK, a couple of things.

1. I'm not sure if that screensaver message is indicating that the screensaver crashed x, or that screensaver was going offline because x was crashing. Chicken-or-the-egg kind of thing. However, if you have your screensaver set to "Random," then set it to a particular screensaver. I use ant spotlight. I've seen Flying Toasters, cool though it is, segfault and crash X. However, I didn't see a screensaver segfault, so I'm leaning toward this being a red herring. If you have it set to a particular screensaver, change it. Let's see what happens.

2. Second, what are you using nullmailer for? If you don't know... have you set up any servers on your system? There are a lot of nullmailer messages, and if you're not using it, you may want to uninstall it. Your logs indicate it's trying to send email but failing. It's doing this every few minutes. To delete it, run...

sudo apt-get remove nullmailer

Make those changes and see what happens. If it crashes again, post more logs.

---

### Post by gila_monster on 2009-07-13
> **thomasaaron said:**
> OK, a couple of things.

1. I'm not sure if that screensaver message is indicating that the screensaver crashed x, or that screensaver was going offline because x was crashing. Chicken-or-the-egg kind of thing. However, if you have your screensaver set to "Random," then set it to a particular screensaver. I use ant spotlight. I've seen Flying Toasters, cool though it is, segfault and crash X. However, I didn't see a screensaver segfault, so I'm leaning toward this being a red herring. If you have it set to a particular screensaver, change it. Let's see what happens.

I had the same thought. I had it set to glmatrix rather than random, and now it's set to "blank screen."  No problems since then, but it's not a regular occurrence.

> 2. Second, what are you using nullmailer for? If you don't know... have you set up any servers on your system? There are a lot of nullmailer messages, and if you're not using it, you may want to uninstall it. Your logs indicate it's trying to send email but failing. It's doing this every few minutes. To delete it, run...

sudo apt-get remove nullmailer

Make those changes and see what happens. If it crashes again, post more logs.

I am not using nullmailer for anything, but it didn't seem relevant to the crash, so I ignored it. I think it may have been installed when I tried to set up an alert system for weather events (long story. Optimal solution is to inherit the current, non-functional server from my friend and fix it). I will gladly remove it if it doesn't serve a purpose.

Thanks for your time.

---

### Post by gila_monster on 2009-07-16
> **thomasaaron said:**
> 
Make those changes and see what happens. If it crashes again, post more logs.

Crashed twice more, spectacularly. Logs sent by email.

---

### Post by thomasaaron on 2009-07-17
Geesh! OK, I'll have a look at them.

---

