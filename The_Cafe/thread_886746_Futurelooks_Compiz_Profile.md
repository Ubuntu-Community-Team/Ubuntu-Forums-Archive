---
title: "Futurelooks Compiz Profile"
date: 2008-08-11
forum: The Cafe
---

### Post by Mazza558 on 2008-08-11
(Mods, I'd appreciate it if this didn't get moved to desktop effects/customization, as lots of people are missing out on this)

For all of you with more powerful computers and graphics cards, I've been working on a compiz profile which offers a healthy balance of effects and visuals. It provides the feeling of using an RGBA filter, but without the filter. It will come with Futurelooks 3 and it provides:

- Fading/blur effects on all windows and menus
- Unfocused windows transparency
- The normal compiz effects

**Installation**


You'll need:

1. A compatible graphics card - Open compiz settings manager and enable the "blur windows" plugin. Next, hold alt down and use a mouse wheel to make the window transparent. Does it look blurry? If it does, You're compatible. If there's no blurriness, you're out of luck. If enabling the blur plugin crashes your PC, it's definitely not compatible.

2. Development version of Compiz
   You'll need Ubuntu Tweak for this. 

> How to add the source of Ubuntu Tweak

No matter your Ubuntu is Feisty, Gutsy or Hardy, open your terminal, type the command to run gedit(or other editor in your opinion) to modify the sources.list:

sudo gedit /etc/apt/sources.list

And put the two line into it:

deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main

Then update the source and install or upgrade Ubuntu Tweak:

sudo apt-get update
sudo apt-get install ubuntu-tweak


Now, open this program and go to Applications > Third Party Software. Click to unlock and type your password in, then tick the compiz box and apply. The compiz development version source has now been added, and you should get some new updates in the notification area. If you don't, open a terminal and type "sudo apt-get update" and you'll get the updates. Apply the updates to compiz, log out and log in again. You're now using the new compiz. The next thing to do is to open the compiz settings manager, go to preferences and, where it says "profile", click "export" to save your settings just in case mine don't work on your PC. Next, download this file:

[https://dl.getdropbox.com/u/29948/FutureBlur]("https://dl.getdropbox.com/u/29948/FutureBlur")

Then, in the compiz manager, click "import", change the file type to "all files" and find the file you just downloaded. This should now apply these settings to your profile. if they don't work on your pc/you don't like them, you can simply restore your backup settings. Please note that you may have to do some poking around in the "general options" section, especially the parts about refresh rates and resolution.

I've attached a screenshot of what this all looks like. Enjoy! :)

---

### Post by Bart_D on 2008-08-11
I clicked on the Future Blur link you posted above, and a bunch of text came up....looks almost like a conky setup in gedit.

Is there some special way to download that file?

---

### Post by MadsRH on 2008-08-11
Looks really cool :)

---

### Post by Mazza558 on 2008-08-11
> **Bart_D said:**
> I clicked on the Future Blur link you posted above, and a bunch of text came up....looks almost like a conky setup in gedit.

Is there some special way to download that file?

Right click and click "save link as"

---

### Post by Canis familiaris on 2008-08-11
> **madsrh said:**
> looks really cool :)

+1

---

### Post by Mazza558 on 2008-08-11
> **MadsRH said:**
> Looks really cool :)

> **Anurag_panda said:**
> +1

Thanks!

---

### Post by miggols99 on 2008-08-11
I thought the whole reason for changing opacity was so you could see behind it...what's the point of it if it's blurred so you can't read it? I guess it's ok for the titlebar but for the actual window...that's very Vista like. They like to blur everything!

---

### Post by Mazza558 on 2008-08-11
> **miggols99 said:**
> I thought the whole reason for changing opacity was so you could see behind it...what's the point of it if it's blurred so you can't read it? I guess it's ok for the titlebar but for the actual window...that's very Vista like. They like to blur everything!

I'm using opacity just for the visual style. The only thing that looks like Vista is the blur, but who can really say Vista created the blur effect?

---

### Post by miggols99 on 2008-08-11
Looking at it again, I'd say those tabs look absolutely horrible! Personally I think that making the tab decorations disappear when they're inactive looks a lot better. And that top part of the active tab really needs to be changed...

Also, the inactive window titlebar looks like the gradient isn't smooth enough. Is it possible to make the gradient extend to the menu bar to make it more smooth?

Other than that, nice work. It looks very good. I would use it if I wasn't on KDE ;)

---

### Post by Mazza558 on 2008-08-11
> **miggols99 said:**
> Looking at it again, I'd say those tabs look absolutely horrible! Personally I think that making the tab decorations disappear when they're inactive looks a lot better. And that top part of the active tab really needs to be changed...

Also, the inactive window titlebar looks like the gradient isn't smooth enough. Is it possible to make the gradient extend to the menu bar to make it more smooth?

Other than that, nice work. It looks very good. I would use it if I wasn't on KDE ;)

Which bit of the tabs? Do you mean the blue lines? I'm tryig to get that fixed at the moment. The gradient is another thing to get rid of. Eventually I'll be able to get a completely flat bar.

---

### Post by saratchandra on 2008-08-11
Apologies to hijack yur thread, but what is the gtk theme you're using? I'm using futurelooks murrina right now, since none of the gtk themes match with the standard emerald theme

---

### Post by speedemonV12 on 2008-08-11
hey guys, im trying to get this to work, but whenever i start ubuntu-tweak and go to unlock the third party apps section, it freezes, any idea why?

---

### Post by Mazza558 on 2008-08-12
> **saratchandra said:**
> Apologies to hijack yur thread, but what is the gtk theme you're using? I'm using futurelooks murrina right now, since none of the gtk themes match with the standard emerald theme

This is my mod of the "glow" theme. I'm not finished with it yet ;)

> hey guys, im trying to get this to work, but whenever i start ubuntu-tweak and go to unlock the third party apps section, it freezes, any idea why?

Are you using Hardy?

---

### Post by mrgnash on 2008-08-12
This is very cool :D Thankyou.

---

### Post by brunovecchi on 2008-08-12
Strange... focus blur works fine (it blurs whatever is not focues), but active blur (blurring behind transparent windows) doesn't... does that mean that my graphics card is not comptabile?

---

### Post by narselon on 2008-08-12
I tried reverting back to my old settings, but can't get the animations to change back even when I manually set them. I'm now using animations plus to get some of them to work but that plugin still has a few bugs. The cube has a jerkier motion too. Also, I don't recommend setting a default skydome as the path on your computer doesn't apply to others.

---

### Post by Parp on 2008-08-12
Nice one mate..

---

### Post by Mazza558 on 2008-08-12
> **narselon said:**
> I tried reverting back to my old settings, but can't get the animations to change back even when I manually set them. I'm now using animations plus to get some of them to work but that plugin still has a few bugs. The cube has a jerkier motion too. Also, I don't recommend setting a default skydome as the path on your computer doesn't apply to others.

What happens when you "reset to defaults" and then try to loads your profile? Does this fix your problems?

---

### Post by Mazza558 on 2008-08-23
Anyone else care to try this out? I'm hoping I can include it in FutureLooks 3 but I'm not quite convinced.

---

### Post by Woormy on 2008-08-23
> **Mazza558 said:**
> Anyone else care to try this out? I'm hoping I can include it in FutureLooks 3 but I'm not quite convinced.

Everything looks great but moves slowly. It isn't eating memory sothat's not the problem. Do I need to make another setting?

---

### Post by Mazza558 on 2008-08-23
> **Woormy said:**
> Everything looks great but moves slowly. It isn't eating memory sothat's not the problem. Do I need to make another setting?

It's probably one of the most cpu/graphics-intensive settings for Compiz as a whole, so it's likely to be your PC.

---

### Post by PRGUY85 on 2008-09-18
Hmm, I can't get it to work like it used to.  I had it all working great yet I had to reinstall hardy and now its not the same.  I don't get menu transparencies or much blur overall.  Do I have to select FutureBlur on General once I import it?  I'm asking because it doens't how on the profile selector after importing it.

---

### Post by Exsecrabilus on 2008-10-02
Wait, I just noticed. Why is this telling me to install Ubuntu Tweak? All you have to do is get the direct Launchpad PPA repo and post it, just like you did with the Ubuntu Tweak repo. >_>

---

### Post by waldenasta on 2008-10-09
> **Mazza558 said:**
> Anyone else care to try this out? I'm hoping I can include it in FutureLooks 3 but I'm not quite convinced.


I am new to ubuntu and truth be told, I thought I would have to give on some of the eye candy that I enjoyed with vista ultimate. But, not only is my dual video card working with sli but this is the cherry on top.  You did a stellar job. This is absolutely beautiful. I have no reason to go back to windoze.  You definitely made a fan.  Keep up the good work and much blessing. By the way, when I update to 8.10 I won't lose anything will I. I just love the way my system is setup and running right now.  Cheers.

---

