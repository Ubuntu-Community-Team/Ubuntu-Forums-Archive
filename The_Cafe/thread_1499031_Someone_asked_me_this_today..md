---
title: "Someone asked me this today."
date: 2010-06-01
forum: The Cafe
---

### Post by Random_Dude on 2010-06-01
In windows when the system crashes you get the famous Blue Screen of Death.

Is there an equivalent for Ubuntu or for Linux Distros in general?

Someone asked me this out of curiosity, and I got curious myself. I'm still a newcomer to Ubuntu so I've never had any major crash.

Can anyone post a picture?

Cheers :cool:

---

### Post by dzon65 on 2010-06-01
Can't help you there,never crashed.

---

### Post by razorboy5 on 2010-06-01
i got a blank screen once ...
not sure how it got there but i went to the bathroom came back it was just locked/frozen

never happened again

---

### Post by blueturtl on 2010-06-01
The Linux equivalent is called a 'Kernel Panic'.

You can tell you're having a kernel panic when your system completely freezes and/or your keyboard lights all flash. It should never ever happen, but you do run in to it sometimes with poor device drivers or failing hardware.

---

### Post by undecim on 2010-06-01
Well, a crash at the very core of the OS would cause what's called a kernel panic. If you are in console mode, you will get text explaining it. In graphical mode, the computer will just lock up.

In both cases, the caps lock light will flash (or is it another lock light? I forget...)

But that is only for errors at the very core of the OS and is most common when booting the system or with faulty core hardware.

You don't have the same kind of BSOD crash in Linux because Linux is modular. If your GUI fails, you will fall back to console mode and Ubuntu and similar distros will try to restart it. If that continually fails, you get a blue screen with a gray box explaining that there is a problem starting GDM.

You could consider that a BSOD to some extent, but you can still log into the console and fix the problem.

---

### Post by Penguin Guy on 2010-06-01
[Google it.]("http://www.google.com/images?q=linux+kernel+panic")

---

### Post by m4tic on 2010-06-01
Kernel Panic. Install mandriva 2010 first and dual boot ubuntu 10.04. You'll get one. I don't get why ubuntu blocked mandriva, fishy.

---

### Post by gnomeuser on 2010-06-01
Interestingly it isn't till now that we have KMS we even have the technical capability available to do a BSOD for Linux.

Normally a problem is resulting in things such as hanging the UI unrecoverably or a kernel oops.

---

### Post by Dragonbite on 2010-06-01
I've managed to get in a situation where the Cap, Num and Scroll lock buttons were flashing and the system was completely unresponsive!

---

### Post by new_tolinux on 2010-06-01
> **Random_Dude said:**
> Is there an equivalent for Ubuntu or for Linux Distros in general?
.......
Can anyone post a picture?

There is, it's called "kernel panic" and produces mostly text that is about as uninformative as the BSOD in Windows.

I don't have a picture of it, white text on a black background.

---

### Post by 98cwitr on 2010-06-01
> **Random_Dude said:**
> In windows when the system crashes you get the famous Blue Screen of Death.

Is there an equivalent for Ubuntu or for Linux Distros in general?

Someone asked me this out of curiosity, and I got curious myself. I'm still a newcomer to Ubuntu so I've never had any major crash.

Can anyone post a picture?

Cheers :cool:

yeah...NOTHING works...the mouse doesn't move, no more I/O at all...this is Linux's BSOD.

---

### Post by Stancel on 2010-06-01
The "gray window of death" when the window you have open freezes up and turns gray. Very annoying.

---

### Post by chessnerd on 2010-06-01
> **blueturtl said:**
> The Linux equivalent is called a 'Kernel Panic'.

You can tell you're having a kernel panic when your system completely freezes and/or your keyboard lights all flash. It should never ever happen, but you do run in to it sometimes with poor device drivers or failing hardware.

So that's what a kernel panic is like.

Evidently, my system undergoes regular kernel panics. Everything stops and the "Caps Lock" light blinks repeatedly. Great.

Anyone know how to fix this on a Gateway T-6330u?

---

### Post by Directive 4 on 2010-06-01
hit it with a hammer, 

then it's fixed, or really broke, so you can but a new one

---

### Post by Mr. Picklesworth on 2010-06-01
> **blueturtl said:**
> The Linux equivalent is called a 'Kernel Panic'.

You can tell you're having a kernel panic when your system completely freezes and/or your keyboard lights all flash. It should never ever happen, but you do run in to it sometimes with poor device drivers or failing hardware.

Fun trivia there:

[http://kerneltrap.org/node/355](http://kerneltrap.org/node/355)

There is a patch to make the keyboard lights give you an error message in morse code, instead of just blinking normally. Yes, a proper error message!

Unfortunately, with kernel mode-setting coming along, we soon won't have a use for it because Linux will be able to use graphics in its dying moments :(

---

### Post by gnomeuser on 2010-06-01
> **Mr. Picklesworth said:**
> Fun trivia there:

[http://kerneltrap.org/node/355](http://kerneltrap.org/node/355)

There is a patch to make the keyboard lights give you an error message in morse code, instead of just blinking normally. Yes, a proper error message!

Unfortunately, with kernel mode-setting coming along, we soon won't have a use for it because Linux will be able to use graphics in its dying moments :(

At least lets be pretty when we fail, also having a visual error to report is very helpful for support reasons.

[img]http://www.pajbam.com/wp-content/uploads/2007/12/mac_os_x_kernel_panic_screen.jpg[/img]

Like OS X above, but I think we can do even better.

---

### Post by ve4cib on 2010-06-01
> **Mr. Picklesworth said:**
> Fun trivia there:

[http://kerneltrap.org/node/355](http://kerneltrap.org/node/355)

There is a patch to make the keyboard lights give you an error message in morse code, instead of just blinking normally. Yes, a proper error message!

That is just freaking amazing.  I love it!

---

### Post by new_tolinux on 2010-06-01
> **gnomeuser said:**
> At least lets be pretty when we fail, also having a visual error to report is very helpful for support reasons.
...
Like OS X above, but I think we can do even better.
[img]http://www.williamrobertson.net/images/oelinux5-kernel-panic.png[/img]
As said, white text on a black background.
Not really informative, but I prefer this above something that's really giving no info like the OS X screenshot.
I have to say, most Windows BSOD's actually have a little more helpful information on (about the) fourth and sixth line on that screen.

Probably needless to say that I prefer to see it all just working as it's supposed instead of hangs and panics ;)

---

### Post by zuerston on 2010-06-01
I think you can set the color of your crash screen using terminal commands.
:popcorn:

---

### Post by Random_Dude on 2010-06-01
> **undecim said:**
> 
You don't have the same kind of BSOD crash in Linux because Linux is modular. If your GUI fails, you will fall back to console mode and Ubuntu and similar distros will try to restart it. If that continually fails, you get a blue screen with a gray box explaining that there is a problem starting GDM.

You could consider that a BSOD to some extent, but you can still log into the console and fix the problem.

[IMG]http://skepacabra.files.wordpress.com/2008/11/the-more-you-know.jpg[/IMG]

I'll keep that last one in mind in case of my Ubuntu has a major crash.


> **Mr. Picklesworth said:**
> Fun trivia there:

[http://kerneltrap.org/node/355](http://kerneltrap.org/node/355)

There is a patch to make the keyboard lights give you an error message  in morse code, instead of just blinking normally. Yes, a proper error  message!

Unfortunately, with kernel mode-setting coming along, we soon won't have  a use for it because Linux will be able to use graphics in its dying  moments :(

I'm not sure if I'm happy or sad about that kernel update.

Anyway, thanks everyone for answering the question.;)
Cheers :cool:

---

