---
title: "MagicSysRq keys for assistance with Ubuntu troubles"
date: 2007-11-19
forum: Tutorials
---

### Post by PmDematagoda on 2007-11-19
[COLOR="Navy"]**_[SIZE="2"]This guide consists of four parts:-[/SIZE]_**
[B]1) Introduction
2) Restarting Ubuntu safely when it is frozen.
3) Shutting down Ubuntu safely when it is frozen.
4) Brief descriptions about the keys you can use in magic SysRq sequences.
5) Controlling the use of SysRq keys.[/B][/COLOR]

[COLOR="Sienna"]**_1) Introduction_**[/COLOR]

First off I would like to thank the creators of the different Linux Kernel documentation, tutorials and how-tos that made this possible, I would also like to thank pauper and Vadi for their help in this(in someway:)).

The magic SysRq keys are key combinations within the Linux kernel that allows the user to perform various low level commands regardless of the system's state, except during kernel panics or freezes. It is often used to recover from X-Server freezes, or to reboot a computer without corrupting the filesystem.


[COLOR="Sienna"][SIZE="2"]**_2) Restarting Ubuntu safely when it is frozen_**[/SIZE][/COLOR]

If anyone faces a freeze with Ubuntu where you cannot do anything, then this will certainly be helpful if you want to reboot the OS as cleanly as possible without damaging their HDD's or losing their data.

In case of a freeze where you cannot do anything, simply press [SIZE="3"]_Alt+SysRq_+R+S+E+I+U+B[/SIZE], keep in mind that the underlined keys must be kept pressed through the rest of the sequence AND that you will need to keep holding the sequence keys for a small period of time before going to the next one so that their actions can be carried out properly (For example, hold the R key for about 1-2 seconds before moving on to S). If the sequence does not work at first, then increase the time period between each sequence key press and try again.

If anyone requires a good way of remembering the sequence R+S+E+I+U+B, just remember "**R**aising **S**kinny **E**lephants **I**s **U**tterly **B**oring":).

**If someone requires a good description on what each keystroke does, here is something rather good:-**

[COLOR="DarkGreen"]**R**[/COLOR]aw (take control of keyboard back from X), t[COLOR="DarkGreen"]**E**[/COLOR]rminate (kill -15 programs, allowing them to terminate gracefully), k[COLOR="DarkGreen"]**I**[/COLOR]ll (kill -9 unterminated programs), [COLOR="DarkGreen"]**S**[/COLOR]ync (flush data to disk), [COLOR="DarkGreen"]**U**[/COLOR]nmount (remount everything read-only), re[COLOR="DarkGreen"]**B**[/COLOR]oot.

**_NOTE:- This keystroke does not work in the event of a kernel freeze as the keystroke sequence depends on the kernel in order to unmount and make the required steps before the restart._**


[COLOR="Sienna"][SIZE="2"]_**3) Safely shutting down Ubuntu when it is frozen**_[/SIZE][/COLOR]

The key sequence to achieve this does not differ from the one used to restart Ubuntu safely except for the last key. So here it is as follows:-
[SIZE="3"]_Alt+SysRq_+R+S+E+I+U+O[/SIZE], keep in mind that as in the previous sequence, the underlined keys must be kept pressed through the rest of the sequence AND that you will need to keep holding the sequence keys for a small period of time before going to the next one so that their actions can be carried out properly.

**If someone requires a good description on what each keystroke here does, there is not much of a difference from the last one, except(Once again:)), the final key:-**

[COLOR="DarkGreen"]**R**[/COLOR]aw (take control of keyboard back from X), t[COLOR="DarkGreen"]**E**[/COLOR]rminate (kill -15 programs, allowing them to terminate gracefully), k[COLOR="DarkGreen"]**I**[/COLOR]ll (kill -9 unterminated programs), [COLOR="DarkGreen"]**S**[/COLOR]ync (flush data to disk), [COLOR="DarkGreen"]**U**[/COLOR]nmount (remount everything read-only), shutd**[COLOR="DarkGreen"]O[/COLOR]**wn.

**_NOTE:- This keystroke does not work in the event of a kernel freeze as the keystroke sequence depends on the kernel in order to unmount and make the required steps before the shutdown._**


[COLOR="Sienna"]_[SIZE="2"]**4) Brief descriptions about the keys you can use in magic SysRq sequences**[/SIZE]_[/COLOR]

**0 - 9** - sets the console log level, controlling which kernel messages will be printed to your console so that you don't get flooded.

**B** - restarts the system without making steps to ensure that the conditions are good for a safe reboot, using this key alone is like doing a cold reboot.

**E** - sends SIGTERM to all processes except init. This means that an attempt is done to end the current processes except init, safely, e.g. saving a document.

**F** - call oom_kill(Out Of Memory Killer), which will kill a process that is consuming all available memory.

**H** - displays help about the SysRq keys on a terminal though in actuality you can use any key **except** for the ones specified, to display help.

**I** - sends SIGKILL to all processes except init. This means that all the processes except for init are killed, any data in processes that are killed will be lost.

**K** - kills all processes on the current terminal. It is a bad idea to do this on a console where X is running as the GUI will stop and you can't see what you type, so you will need to switch to a tty after doing the magic SysRq.

**L** - sends SIGKILL to all processes, including init. This means that **every** process including init will be killed, using this key **will** render your system non-functional and no further magicSysRq keys can be used. So in this case you will have to cold reboot it.

**M** - dumps memory info to your console.

**O** - shuts down the system via ACPI or in older systems, APM. As in key "B", using this key alone is like a cold reboot(Or in this case, a cold shutdown;)).

**P** - dumps the current registers and flags to your console.

**Q** - dumps all timers info to your console.

**R** - takes keyboard and mouse control from the X server. This can be useful if the X-Server crashed, you can change to a console and kill the X-Server or check the error log. 
NOTE:- The documentation refers to this key's task as "Turns off keyboard raw mode and sets it to XLATE", but I suppose it's safe enough to assume that it takes back control from X.

**S** - writes all data from the disc cache to the hard-discs, it is a sync and is necessary to reduce the chances of data corruption.

**T** - dumps a list of current tasks and info to your console.

**U** - remounts all mounted filesystems read-only. After using this key, you can reboot the system with Alt+SysRq+B without harming the system.

**W** - dumps uninterruptable (blocked) state tasks.


[COLOR="Sienna"]_[SIZE="2"]**5) Controlling the use of SysRq keys.**[/SIZE]_[/COLOR]

There are some ways of controlling the use of SysRq keys(i.e. what can be used, enabling or disabling them completely), two ways of doing this are:-
1) Configuring the SysRq keys during kernel compilation itself.
There isn't much here since you can only disable SysRq keys and not actually control or define what you can and can't use. The option you are looking for is:-
```
MAGIC_SYSRQ
```

2) Using proc sysrq trigger calls.
This is much more flexible than changing the configuration of the kernel but this has one downside with security which is explained after(since it is very minor). You use the echo command to achieve this for ease but you could also use any normal text editor to achieve this. Now the command is(you will need root permissions):-
```
echo * > /proc/sys/kernel/sysrq
```
where "*" is a number, which can be any one of these:-
**0** - disable sysrq keys completely

**1** - enable all functions of sysrq

**2** - enable control of console logging level

**4** - enable control of keyboard (SAK, unraw)

**8** - enable debugging dumps of processes etc.

**16** - enable sync command

**32** - enable remount read-only

**64** - enable signalling of processes (term, kill, oom-kill)

**128** - allow reboot/poweroff

**256** - allow nicing of all RT tasks(control the nice level(priority) of Real Time tasks)

So you can define what SysRq keys can be used, and also define whether they are all on or off. Also, there may be more ways of controlling the SysRq keys, but as of now the above two are the only ways I know of.

Now for the "downside". For example you disable SysRq keys when you want to stop people(local) from doing key presses and then shutting down or messing up the PC during an important task(very obscure, I know). Now with configuring the kernel, you can stop SysRq keys from being used at all from the beginning of the boot process right uptil the end, with calling the proc sysrq triggers however, your option only takes place when it is executed(i.e. after the system has booted up) so there is a certain area of vulnerability with calling the triggers whereas there is no such thing in configuring the kernel, some people are that desperate to secure their systems to care about a few seconds, however do not blame me for it;).


**Something about the magicSysRq keys is that they can be used in any sequence and in any way to achieve the required objective, for example you can just press Alt+SysRq+B to do something like a cold reboot.**

[SIZE="2"]**One more NOTE:- [COLOR="DarkRed"]Even though this guide is made for Ubuntu, the magic SysRq keys can be used on other Linux distributions with little/no alterations[/COLOR].**[/SIZE]

---

### Post by davidjmayo on 2007-11-19
Just in case anyone wants to know more about what this does
see here  [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by stinger30au on 2007-11-20
man!!!


hate to try this with small hands!!!!

ou almost need three hands to make it to press all the keys needed!

thanks for the info

---

### Post by popch on 2007-11-20
I usually use Alt+Ctrl+Backspace because it's usually the GUI which is hung. In most cases, recovery is complete enough for me to continue working.

I did not know about the method in the OP but would have needed it only once or twice in a long time. Thanks anyway for posting here.

---

### Post by wieman01 on 2007-11-20
Interesting post... I will most definitely try it out next time my system freezes (sadly just happened this morning). Thanks, man.

---

### Post by Banacek on 2007-11-20
We seem to have enough sticky threads already. Rather than make this one sticky it would be better to incorporate the posts with the key points of this thread into a thread that's already sticky. 8u)

---

### Post by MrKlean on 2007-11-20
Stinger,  only Alt-Print Screen have to be held down LOL! The rest are press and release !!  FYI ; )

---

### Post by Vadi on 2007-11-20
I was also told you should wait ~5 seconds after each command just to make sure it gets time to do it's stuff.

---

### Post by PmDematagoda on 2007-11-20
> **Vadi said:**
> I was also told you should wait ~5 seconds after each command just to make sure it gets time to do it's stuff.

Thank you very much Vadi, I forgot about that part and I included it now.

---

### Post by stchman on 2007-11-20
I have 3 machines running Ubuntu and I have only had 2 OS lockups.  It happens so rare I will forget that key combination.

---

### Post by santiagoward2000 on 2007-11-20
> **stchman said:**
> I have 3 machines running Ubuntu and I have only had 2 OS lockups.  It happens so rare I will forget that key combination.

Just try to remember how much fun you had when you were raising skinny elephants! :lolflag:

---

### Post by NIT006.5 on 2007-11-20
That is very useful information. Thanks for posting.

---

### Post by nikoPSK on 2007-11-20
lucky for me I've never had a freeze or wish for one:D...

---

### Post by PmDematagoda on 2007-11-29
I'm bumping this because it seems that there are quite a number of people for whom their Ubuntu OS keeps freezing, may be this thread could help.

---

### Post by pingpongboss on 2007-11-30
I use REISUB, but i bet it just does the exact same things.

easy to memorize since it spelled backwards is BUSIER

---

### Post by PmDematagoda on 2007-11-30
> **pingpongboss said:**
> I use REISUB, but i bet it just does the exact same things.

easy to memorize since it spelled backwards is BUSIER

Hehe, nice one pingpongboss:).

---

### Post by NT4usB on 2007-11-30
Thanks for this.
Will give it a try next time I get a lockup that I can't clear from a tty or ssh from another box... if the keyboard is still working, that is.
Unfortunately, I usually manage to bork it all the way to the keys...

---

### Post by PmDematagoda on 2007-12-23
Decided to bump this thread up since I spruced it up a little bit:).

---

### Post by Vadi on 2007-12-23
For some reason the B key never reboots for me.

I even tried it on a normally working system (well, it froze it for me, and that's about it).

---

### Post by PmDematagoda on 2007-12-23
The B key always worked for me except in circumstances where the kernel was frozen, why don't you give the O key a try?

---

### Post by jdc on 2008-01-14
Does anyone know how to type Alt Sysrq on a Macbook Pro?

---

### Post by Cannaregio on 2008-01-14
For what it is worth, and for completeness sake, there are a couple more interesting sysRq you could use in order to dump some info whenever you have been "frozen out":

'ALT+SysRq+ 0'-'9' - Sets the console log level, controlling which kernel messages   will be printed to your console., so that you don't get flooded.

'ALT+SysRq+m'    - dumps memory info to your console

'ALT+SysRq+p'     - dumps the current registers and flags to your console

'ALT+SysRq+q'    - dumps all timers info to your console

'ALT+SysRq+t'     - dumps a list of current tasks and info to your console

'ALT+SysRq+w' - dumps  uninterruptable (blocked) state tasks.

Also worth pointing out imo:

'ALT+SysRq+k' - Is the "Secure Access Key" (SAK), which kills all programs on the current virtual console. In the OP it says "*It is a bad idea to do this on a console where X is running. The GUI will stop and you cant see what you type*", but it should be pointed out that it is a VERY good idea to use it at a tty if you want to be sure there is no trojan program running at console in order to could grab your password when you  login. 
It will kill all programs on given console and make sure that the login prompt you see is actually the real init and not a trojan!

Cheers!

---

### Post by PmDematagoda on 2008-01-14
I added the magic SysRq keys mentioned by Cannaregio. Thank you Cannaregio:).

---

### Post by gotee12 on 2008-01-15
What's a guy to do when he's on a laptop and must use a "Function" key to access system keys such as "Print Screen" and such? Once I hold down the "Function" key, it disables all of the basic keys (such as Alt). What's the safest way to shut down a frozen laptop like mine?  

Or do I just need to pull the plug and pray? [-o<

Thanx!

---

### Post by nikoPSK on 2008-01-15
> **gotee12 said:**
> Or do I just need to pull the plug and pray? [-o<

LOL, that's windows. :popcorn:

---

### Post by Shibata on 2008-01-26
Thank you for great document.

By the way, according to Wikipedia, safe reboot is R+E+I+S+U+B.
see [http://en.wikipedia.org/wiki/Magic_SysRq_key#Raising_Elephants](http://en.wikipedia.org/wiki/Magic_SysRq_key#Raising_Elephants)

What it is difference from the key stroke in the thread?
Should I execute Sync command before Term and Kill or after Term and Kill?

---

### Post by PmDematagoda on 2008-01-26
Well, I do not know the true difference, but I think it is always better to write the data to the hard disk before terminating and killing the processes.

---

### Post by imaginal on 2008-01-29
> **gotee12 said:**
> What's a guy to do when he's on a laptop and must use a "Function" key to access system keys such as "Print Screen" and such? Once I hold down the "Function" key, it disables all of the basic keys (such as Alt). What's the safest way to shut down a frozen laptop like mine?  

Or do I just need to pull the plug and pray? [-o<

Thanx!

I second this question... holding this key combination ends up endlessly populating my printscreen dialogs... alt+fn+insert(prt sc)

---

### Post by narf y akim on 2008-02-02
I have the same problem.
Is thera a way to find out the equivalent keys in different laptos/keyboard?

---

### Post by ronocdh on 2008-02-27
> **jdc said:**
> Does anyone know how to type Alt Sysrq on a Macbook Pro?
I would love to see this answered!

---

### Post by pjstegmaier on 2008-03-10
My situation is that I'm using this MagicSysRq key all the time when either my mouse freezes on Firefox or Evolution or anything else I use or when my screensaver freezes up.  I'm talking about using it at least a dozen times per session on the pc before I just get pissed off and shut down the pc.  This started happening after Gutsy but not with Fiesty.  What gives??  I'm new at this too.

Pamela:(

---

### Post by fiprojects on 2008-03-11
I tried this sequence of characters and it just does not work for me... To clarify, I did 

ALT+PRTSCN+R
ALT+PRTSCN+S
ALT+PRTSCN+E
ALT+PRTSCN+I
ALT+PRTSCN+U
ALT+PRTSCN+B

Each of the above are done individually with about two to four seconds holding down the keys before I move on to the next series.  I'm having trouble because my laptop boots normally about 50% of the time and the other time it looks like its alive but no GUI or login prompt.  I know its not frozen because I've configured CTRL+ALT+DEL to eject the cdrom before a reboot and the eject works everytime...

I've also tried using the [fn] key, plus PRTSCN plus the letters above, and ALT+SYSRq plus the letters noted above.

Anyone have any suggestions? :(

---

### Post by pjstegmaier on 2008-03-12
I works ok if you hold down the buttons like this:

Alt & PrintscreenSysRq....Hold these down continuously and press the other keys REISUB each for a few seconds each at a time and it works.

Pamela

---

### Post by Marcolin on 2008-03-18
My system was completely locked and I tried this system. I just saw my screen get all garbled and it didn't reboot. Then I found this post:

> **Vadi said:**
> I was also told you should wait ~5 seconds after each command just to make sure it gets time to do it's stuff.

I tried that and it worked! Thanks Vadi!

EDIT: I should also note that on my laptop, "prnt scrn" is a set as a secondary use. I had to hold down ALT+FN+Prnt Scrn to get it to work.

---

### Post by tech404 on 2008-05-14
I think it is best to remember Raising Elephants Is So Utterly Boring instead. This way you sync the disk after term and kill. Seems better for the disks.

---

### Post by Scientia on 2008-06-05
Yeah, i don't think there actually is a 'prtscn' key on Apple laptops..(Using a PPC iBook)

---

### Post by vgovindan37 on 2008-06-11
Cheers for your efforts and sparing to all linux lovers especially Ubuntu. I have completely removed windows from my machine, I am fully engaged my retired life playing with linux and I am enjoying the flexibility and its openess. At this my age of 72, I wish the world is united for common pleasure with ability to live within individual's potential.
Thank you and wish you will add more tips.
V.Govindan.

---

### Post by pauper on 2008-07-24
Uploaded version of the *original* manual is [here](http://www.mjmwired.net/kernel/Documentation/sysrq.txt).

How about adding any information about
"echo ? | sudo tee /proc/sysrq-trigger" calls?

> Raw (take control of keyboard back from X)

It's actually [color=r]un[/color]'R'aw, i.e. set to XLATE.

An excerpt from manual, line #120: "Well, un'R'aw is very handy when your
X server or a svgalib program crashes."

By the way, what kind of output can you get with 8 or 9?

```
:~$ grep KERN /usr/src/linux/include/linux/kernel.h
#ifndef _LINUX_KERNEL_H
#define _LINUX_KERNEL_H
#ifdef __KERNEL__
#define KERN_EMERG      "<0>"   /* system is unusable                   */
#define KERN_ALERT      "<1>"   /* action must be taken immediately     */
#define KERN_CRIT       "<2>"   /* critical conditions                  */
#define KERN_ERR        "<3>"   /* error conditions                     */
#define KERN_WARNING    "<4>"   /* warning conditions                   */
#define KERN_NOTICE     "<5>"   /* normal but significant condition     */
#define KERN_INFO       "<6>"   /* informational                        */
#define KERN_DEBUG      "<7>"   /* debug-level messages                 */
        printk(KERN_DEBUG fmt,##arg)
        printk(KERN_INFO fmt,##arg)
#endif /* __KERNEL__ */
```

---

### Post by PmDematagoda on 2008-07-30
Thank you very much for the link to the documentation pauper, it was very useful. About the different logging levels, I never really experimented much with it since I always want as much logs as possible during problems.

I will update the information accordingly, thanks again pauper.

---

### Post by hey_ram on 2008-10-04
hey!

wonderful thread..
ubuntu has frozen quite a few times for me...
and every time i have given the system a cold boot...

now i know what alternative to key in...
thanx for the tutorial!

---

### Post by 162019444 on 2008-11-06
I've encountered this sort of problems while suing ubuntu

and got no ideas to handle the frozen system.

this have help a lot  

haven‘t finish reading;

just make a mark here;

---

### Post by SPr on 2008-11-08
Could this be made into a sticky? It may help save some hardware from becoming damaged after having the plugged pulled.

IMO the more people who know about this the better.

---

### Post by bluemm on 2008-11-25
good thread!

---

### Post by ooobooontooo on 2008-12-13
I'm sorry if this seems like a really trivial question, but does it matter if the letters in RSEIOU are capital or not? If it does matter, can I use the CAPS lock or do I have to hold down shift as well? If I do need to hold down shift, I'm going to be running out of fingers very soon...:p Thanks for the tutorial though, it will really help me out.

---

### Post by SPr on 2008-12-13
There's no need for upper case. Give it a test and see if it works :)

---

### Post by PmDematagoda on 2008-12-14
I noticed something really stupid(and really small for that matter), I had put PrintScreen where that should really be SysRq, which would have confused people(like me:-P) whose keyboards have PrintScreen and SysRq in different places.#-o

Really sorry for the silly mistake.

ooobooontooo:- I just capitalised the letters to emphasize that they are part of your keyboard, nothing more:).

Everyone else:- Glad the thread helped you:).

---

### Post by bobpaul on 2008-12-21
OP should really change this. 

"Raising Skinny Elephants Is Utterly Boring"
Sync before terminate and kill? Terminate and kill will likely cause files to be changed. You should either do SEISUB or just EISUB. Remember, this is a dirty unmount and doesn't automatically flush buffers the way the unmount command normally would. It's been mentioned a couple of times in this thread, but never really discussed, and I think this needs to be brought out in the open. So:

BUSIER backwards, "Reboot Even If System's Utterly Broken", "Raising Skinny Elephants Is So Utterly Boring", or "Raising Elephants Is So Utterly Boring" are the best ways to go about this.

As an aside, has anyone noticed this no longer working in Intrepid from within X? It works from the shell, but when I try from within X I only get the gnome-screencapture window popping up. I've tried both Alt on the left and Alt Gr on the right, hitting "Print Screen" with and without the shift key depressed, remapping Capture Window to something other than "alt+print screen", etc. Even though my laptop has a Print Scrn/Sys Req key, I've even tried using the Fn key with no results. I had done it once or twice previously, but I'm not sure if that was Gutsy or Feisty... it's not something I've needed often.

---

### Post by Reilithion on 2009-01-15
I, too, have been unable to use Magic SysRq.  I am running 8.10 on an AMD64 system.  I also have a dual-head setup.  I've never before tried to use Magic SysRq, so I don't know if it would have worked with, say, Hardy, or without the dual-head setup.  "echo h > /proc/sysrq-trigger" seems to work, and prints its helpful help message to /var/log/syslog just fine.  But the key combinations do not.  It's like the kernel never hears them.

---

### Post by The_Rebel52 on 2009-01-31
> **Reilithion said:**
> I, too, have been unable to use Magic SysRq.  I am running 8.10 on an AMD64 system.  I also have a dual-head setup.  I've never before tried to use Magic SysRq, so I don't know if it would have worked with, say, Hardy, or without the dual-head setup.  "echo h > /proc/sysrq-trigger" seems to work, and prints its helpful help message to /var/log/syslog just fine.  But the key combinations do not.  It's like the kernel never hears them.

Same here, except i am using a custom kernel and the 32bit version.

Maybe we need to reprogram a configuration to accept the printscreen key as sysreq..

I think it has something to do with our X configurations as i got the keys to work from a VT console.

---

### Post by PmDematagoda on 2009-01-31
> **The_Rebel52 said:**
> Same here, except i am using a custom kernel and the 32bit version.

Maybe we need to reprogram a configuration to accept the printscreen key as sysreq..

I think it has something to do with our X configurations as i got the keys to work from a VT console.

I'll take a look at this and see what is up.

> OP should really change this.

"Raising Skinny Elephants Is Utterly Boring"
Sync before terminate and kill? Terminate and kill will likely cause files to be changed. You should either do SEISUB or just EISUB. Remember, this is a dirty unmount and doesn't automatically flush buffers the way the unmount command normally would. It's been mentioned a couple of times in this thread, but never really discussed, and I think this needs to be brought out in the open. So:

BUSIER backwards, "Reboot Even If System's Utterly Broken", "Raising Skinny Elephants Is So Utterly Boring", or "Raising Elephants Is So Utterly Boring" are the best ways to go about this.

I'll take a look at this and get back to you as soon as possible.

Sorry if I haven't been active here for stuff I should have been, I've been very busy these days and could not find much time.

---

### Post by PmDematagoda on 2009-02-08
I have been looking into the problem, and I do think it has something to do with the X-Server, or with the evdev driver. The reason I suspect the evdev driver is because it catches all events and handles them, so the events for the SysRq keys may not be picked up by the kernel due to that and hence, no action. The X-Server may also have a hand in this, but I will need to spend some time to get the kbd and mouse drivers working before I can confirm that suspicion.

Just an FYI, SysRq keys don't work in Fedora 9 as well, which has X 1.5.2 and the evdev driver. Of course, that may be due to the keys being disabled in the kernel config, but compiling a kernel of my own with the keys turned on hasn't helped.

---

### Post by Reilithion on 2009-05-14
Since upgrading to Jaunty, I'm able to use Magic SysRq.  I believe the issue may have been fixed.  I should note that the default screenshot keyboard combination in Gnome is Alt-PrintScreen which interferes with Magic SysRq sometimes, and I noticed I can only send at least some of the commands (such as 'b') with the left Alt key on my keyboard.

---

### Post by bobpaul on 2009-05-14
> **Reilithion said:**
> I noticed I can only send at least some of the commands (such as 'b') with the left Alt key on my keyboard.

That's interesting. Generally if it only works with one Alt key, it works with the right Alt key (Alt Gr). Thanks for the heads up on the fix. It does indeed appear to be working in Jaunty.

---

### Post by -_- Joseph -_- on 2009-09-12
My ubuntu freezes when im in the middle of a game. so this was a useful thread for me

keep up the good work

                   ,Joseph

---

### Post by kevinguillorytraining on 2009-10-09
I frequent forgot my key combination. But after finding your tutorial I'll no more worried :)

---

### Post by maatuntu on 2009-12-16
Thank you for this tutorial. I am new to Linux, but have to reinstall ubuntu several times. I can only assume this is to unsafe rebooting and shutting down. Thanks for making this available, I am using years after it was first posted

---

### Post by SaintDanBert on 2010-01-21
> **gotee12 said:**
> 
What's a guy to do when he's on a laptop and must use a "Function" key to access system keys such as "Print Screen" and such?
...


My Thinkpad also has this keyboard configuration: [highlight]Fn[/highlight] activates alternate features of the keyboard shown as "blue text" on the key cap. Here is a dance that I found works.
[list=1]
[*]press and hold [highlight]ALT[/highlight] (keep holding)
[*]press and hold [highlight]Fn[/highlight]
[*]press and release [highlight]PrtSc(SysRq)[/highlight]
[indent]I get a "SysRq Help" string splashed across the console[/indent]
[*]press and release whichever command character
[indent]I get a one line announcement "SysRq command" announcing whatever the command letter does. The details go into **/var/log/syslog**[/indent]
[*]release [highlight]ALT[/highlight] when all command characters typed
[/list]

ASIDE: I don't know how to capture text during a console session or I would include an example here.

The above only works from a console [highlight]CTRL+ALT+Fx[/highlight] while running X11 or without X11 entirely. **Fx** means "F1" ... "F6" not the [highlight]Fn[/highlight] key.

If X11 is running, any use of [highlight]PrtSc(SysRq)[/highlight] activates the screen capture utility so you cannot even use the **Raw** command key to grab control. Even if I had an xterm or similar open, I kept getting the screen capture dialog.

This writer really, REALLY, **REALLY** needs a work-around so that he can use magic keys while X11 runs. 

Thanks,
~~~ 0;-Dan

---

### Post by bobpaul on 2010-01-21
> **SaintDanBert said:**
> 
If X11 is running, any use of [highlight]PrtSc(SysRq)[/highlight] activates the screen capture utility so you cannot even use the **Raw** command key to grab control. Even if I had an xterm or similar open, I kept getting the screen capture dialog.


Do you have an Alt Gr key? Use that instead of Alt. If you don't have a key labeled Alt Gr, your right Alt key is generally Alt Gr (even when not labeled). Use that instead of left Alt and you shouldn't get a print screen dialog. 

Otherwise you can remap the key Gnome uses for print in System->Administration->Keyboard Shortcuts. Change both "Take a screen shot" and "Take a screen shot of current window" to other keybindings and your problem should be solved.

---

### Post by soumoks on 2012-05-14
sorry for being a noob but which is the sysrq key?

---

### Post by bobpaul on 2012-05-14
> **soumoks said:**
> sorry for being a noob but which is the sysrq key?

It's the key on your keyboard that has "SysRq" or "SysReq" written on it. On a desktop PC, it's commonly the same as "Print Screen" or "PrtScn". On a Laptop it's often on it's own key and requires you press the Fn key to use it.

---

### Post by sazhagianambi on 2012-09-06
Hi, my system happened to freeze often and I tried this (usually I do cold reboots) and when system restarted all I saw was operating system not found...I had dual boot then used live CD and boot recovery to fix the issue...

I am just curious to understand what went wrong when I tried alt+sysreq+r+e+I+s+u+b...is it okay to use on dual boot machines?

Sony VAIO + Ubuntu 12.04

---

### Post by kiyop on 2013-03-05
> **PmDematagoda said:**
> [COLOR=Sienna][SIZE=2]**_2) Restarting Ubuntu safely when it is frozen_**[/SIZE][/COLOR]

If anyone faces a freeze with Ubuntu where you cannot do anything, then this will certainly be helpful if you want to reboot the OS as cleanly as possible without damaging their HDD's or losing their data.

In case of a freeze where you cannot do anything, simply press [SIZE=3]_Alt+SysRq_+R+S+E+I+U+B[/SIZE]
Although, many persons pointed out...
Is [Alt+SysRq]+R[COLOR=red]EIS[/COLOR]UB better than [Alt+SysRq]+R[COLOR=red]SEI[/COLOR]UB ?
[http://ubuntuforums.org/showthread.php?t=1509765](http://ubuntuforums.org/showthread.php?t=1509765)
I hope PmDematagoda edit the first post of his.

---

