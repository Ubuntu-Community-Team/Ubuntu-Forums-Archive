---
title: "A Big Thank You"
date: 2009-02-18
forum: Testimonials &amp; Experiences
---

### Post by humbug01 on 2009-02-18
Friends,

I've dabbled with Linux for a couple of months now (but I'm not new to computers) and have decided to stick with Ubuntu and gnome (although I do like XFCE too).

With help from a couple of books and mags (e.g., Linux Format) and this forum, I've successfully got grub set up in its own partition for multi-booting, the current Nvidia driver installed in Ubuntu, I've exorcised a few demons and bashed around a little in Ubuntu and the end result is that GNU/Linux and Ubuntu seem like an incredibly elegant, sophisticated OS. It's even more incredible to think that it's free and volunteer work! WOW!

Someday, maybe I can contribute, but until then, A Big THANK YOU to all Ubuntu-ians!

Best,

Steve
humbug01
San Diego, California USA area

Asus P5Q Pro MB
Intel E8400 CPU
Nvidia 9800 GTX+
(I built this system for myself for Xmas)

---

### Post by humbug01 on 2009-02-18
P.S. The next thing on my "to do list" is to swap the Control and ALT keys. I've just never gotten used to them moving them way back when. I still use a Northgate 102 clicky keyboard at work where the CTRL key is where it belongs! :)

S

---

### Post by barney_1 on 2009-02-18
Wow, switching CTRL with ALT is a new one to me.  No offense, but wouldn't is it that hard to learn a new way?  You must have to use computers other than your own that have a standard keyboard?

But, if you must, I think you need to look into the command: xmodmap.  Keycodes would be 11 for CTRL and 12 for ALT so you should be able to try this out:

**[COLOR="Red"]USE AT YOUR OWN RISK, I HAVEN'T TRIED THIS!![/COLOR]**
```
xmodmap -e "keycode 11 = 12"
```
To set CTRL to do ALT's job.... you need to run another command to get ALT to do CTRL's job.

I'd be interested in hearing if this worked... I'm not going to try it out myself, sorry.

**edit:** I just noticed that there is an entry for the Northgate Omnikey 101 in Ubuntu's X keyboard selection.  Have you tried that configuration out yet to see if it works with your 102?

---

### Post by bapoumba on 2009-02-18
Moved to Ubuntu Testimonials.

---

### Post by stchman on 2009-02-18
> **humbug01 said:**
> P.S. The next thing on my "to do list" is to swap the Control and ALT keys. I've just never gotten used to them moving them way back when. I still use a Northgate 102 clicky keyboard at work where the CTRL key is where it belongs! :)

S

I have been using PCs for over 10 years and have never seen a keyboard in such an arrangement.  I did have a SUN workststation that had a somewhat funky keyboard, but not as funky as that.

To each their own.

---

### Post by solwic on 2009-02-18
> **stchman said:**
> I have been using PCs for over 10 years and have never seen a keyboard in such an arrangement.  I did have a SUN workststation that had a somewhat funky keyboard, but not as funky as that.

To each their own.

+1.  I've never seen that, either.  But hey, whatever works....  

:biggrin:

---

### Post by humbug01 on 2009-02-18
First, sorry about mis-placement of this thread. Silly me.

Well, the CTRL-ALT swap thing sort of dates me. My first home computer saved data to a cassette tape player (1985), then we moved up to "super-fast" 5 1/4" floppies; I still remember reading about an article on futuristic things called CDs and wondering how in the world one could possibly fill such a huge storage medium. (I was heavy into assembler at the time and working on optimizing programs to be as small and fast as possible....)

So, yes, I *could* re-learn the keyboard but I figure that a computer should adapt to me and not vice versa. "HAL: 'Please don't touch that button, Dave.'" So I've always swapped CTRL-ALT keys on all my computers over the years to match the gold standard of keyboards, the Northgate OmniKey 102 which I still use at work after 20+ years of service:

[http://www.northgate-keyboard-repair.com/](http://www.northgate-keyboard-repair.com/)

:)

I did, by the way, do this key swap very easily in an x.org kbd config file in Puppy Linux running XFCE, but Ubuntu doesn't seem to use that kbd setup.

Sorry to ramble on. I do appreciate the help and I'll give xmodmap a try.

Best,

Steve

---

