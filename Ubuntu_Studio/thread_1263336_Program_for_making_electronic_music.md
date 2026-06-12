---
title: "Program for making electronic music"
date: 2009-09-10
forum: Ubuntu Studio
---

### Post by stenshorne on 2009-09-10
Was wondering if there is any program out there for making electronica (electronic music) on xubuntu. I`ve tried out one program called Sonic Foundry many years ago, but it seemed a bit complicated.

Any suggestions anyone? Pros and cons of the various programs you list would also be nice, if there are any that is. 

-s

---

### Post by modemsutra on 2009-09-10
Ubuntu studio includes many are you familiar with ubuntu?

---

### Post by stenshorne on 2009-09-10
Not pretty good with it, think I got some basics down.

So, just find ubuntu studios in synaptic package manager and install? Will it work for for jaunty?

Think you will have to explain to me what ubuntu studios is.

Thanks for helping.

---

### Post by mcduck on 2009-09-11
Ubuntu Studio is Ubuntu-based distribution thta includes all kinds of audio, video and graphics-related tools. And it's also available as metapackages through Ubuntu's repositories. But if you found Sonic Foundry confusing I really doubt that the complete Ubuntu Studio, or even only it's audio-related parts, are what you are looking for.

I'd suggest trying [LMMS]("http://lmms.sourceforge.net/"), it's pretty much the easiest software studio app available for Linux.

---

### Post by luctor on 2009-09-12
Check out this : [http://www.rebirthmuseum.com/](http://www.rebirthmuseum.com/)

It's a windows program, but you can run it on ubuntu with wine.

---

### Post by shae on 2009-09-12
Maybe Ardour is what you are looking for?

[http://ardour.org/](http://ardour.org/)

---

### Post by Bucky Ball on 2009-09-12
I actually have a Xubuntu install with all the packages for Ubuntu Studio installed in that. (Except the artwork and desktop cos I'm not keen.) This allows me to boot Xubuntu using the RT kernel and have access to all the Studio apps. Perfect.

This would do it; just leave out the bits you don't want (for instance I left out ubuntustudio-theme and a few other bits), if you open a terminal (Applications->Accessories) and paste this in:

```
sudo apt-get install ubuntustudio-desktop ubuntustudio-gdm-theme ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-default-settings ubuntustudio-icon-theme ubuntustudiolauncher ubuntustudio-graphics ubuntustudio-look ubuntustudio-menu ubuntustudio-screensaver ubuntustudio-sounds ubuntustudio-wallpapers ubuntustudio-video usplash-theme-ubuntustudio ubuntustudio-theme
```

---

### Post by paulmerchant on 2009-09-12
Try Renoise. It's outstanding.

---

