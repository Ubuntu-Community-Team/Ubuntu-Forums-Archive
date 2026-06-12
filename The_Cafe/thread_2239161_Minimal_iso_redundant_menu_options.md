---
title: "Minimal iso redundant menu options?"
date: 2014-08-12
forum: The Cafe
---

### Post by user1397 on 2014-08-12
Out of curiosity, I booted up the ubuntu mini iso in virtualbox (I was gonna mess around with installing the minimal kde packages to see how complete a system I would have).

I noticed in the first menu, it gives you the options of:

1. Install
2. Command-line install
3. Advanced
   a. Expert install
   b. Expert command-line install

So basically 4 ways to install ubuntu minimal.  However, if you actually select any of the 4, they all seem to take you to the same text-mode install program (I cannot for the life of me see any difference between them)

Anyone know why there are 4 choices and what their differences are?

I haven't actually tried installing it through all 4 ways, I've just selected each, and seen the install menus for all 4, then just pressed back to get back to main menu.

---

### Post by buzzingrobot on 2014-08-12
I seem to recall choices 1 and 2 offer different routes through the install.  I.e., you are presented different options. It's been some time, though.

---

### Post by user1397 on 2014-08-12
> **buzzingrobot said:**
> I seem to recall choices 1 and 2 offer different routes through the install.  I.e., you are presented different options. It's been some time, though.
Yea, I can't remember how it used to be on the older images (although it should be pretty easy to test that out just by quickly downloading an older iso and installing through virtualbox) but I can assure you that no matter what method you choose on the current mini.iso, they're all text-mode and all have the same options.  I guess one difference is that the normal install skips through some of the dialogs that the expert one doesn't skip, but either way, if you select back at any point ad return to the main installation menu, all 4 methods show the same steps to install (like configure internet, edit mirrors, install bootloader, etc)

Odd indeed.

And you would think command-line only means actual command line or terminal, and not an ncurses-like text-mode install...

---

### Post by grahammechanical on 2014-08-13
I have only done 1 mini ISO install and I chose the Install option. I so I have not tested all the options. But I think that you will find that whatever option we choose we first need to go through the Who are you? Where are you? what partition? What internet connection? Etc. All that stuff has to be entered before the install can begin and no matter what option we chose.

If we choose Install we eventually get to a list of software selection. It is section 27 in this tutorial.

[http://amjjawad.blogspot.co.uk/2013/07/ubuntu-mini-iso-installation-process.html](http://amjjawad.blogspot.co.uk/2013/07/ubuntu-mini-iso-installation-process.html)

If we choose command-line then I expect that only installs Linux. And we have to take it from there. The other options give more user control. But every option will require us to complete sections 1 to 26 and then section 28.

Regards.

---

### Post by user1397 on 2014-08-14
Yea, I think I'm just going to try installing all 4 ways through virtualbox and then report my findings here ;)

EDIT:  Okay so I did exactly that, and there is definitely a difference between the expert ones and the regular installs, but I found absolutely no difference between the regular install and command line regular install, and also no difference between the expert install and command-line expert install.

So, at least 2 out of the 4 seem redundant and I have no idea why they are included.  They seem like remnants from older minimal images where the "command-line" argument actually meant through a command-line or terminal, and not text-mode.  Maybe these were overridden with the text-mode for some reason.

Interesting nonetheless (at least to a guy like me :))

---

