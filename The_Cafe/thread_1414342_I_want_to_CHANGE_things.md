---
title: "I want to CHANGE things"
date: 2010-02-23
forum: The Cafe
---

### Post by Woolio1 on 2010-02-23
I want to change things. I've seen so many interesting things in Ubuntu, but I'm still using a slightly modified Default.

I need some recommendations, instructions, anything you can throw at me. I want to know how to do these interesting things you see in the Art subforum and other places. I want to try out different window managers, different compositors, different desktop environments, etcetera. 

I want to make my Ubuntu look better.

Currently, I'm using Metacity as my Compositing manager and the GTK-Window-Decorator as my... Window decorator. Metacity's also my Window Manager. 

I don't like Compiz, it was bloaty and buggy when I used it. And don't try telling me I'm wrong, because that's not possible. So I want to get away from Compiz, I want to try other things. 

Any and all recommendations are appreciated. 

-Henry Ericson

---

### Post by NoaHall on 2010-02-23
Gnome is not the only DE. Try KDE, that's pretty.

---

### Post by BrokenKingpin on 2010-02-23
KDE is indeed pretty, but it is also a bit bloated in my opinion. I would look at XFCE as a DE. It has it's own compositor, and with the right theme it can look pretty nice.

You could also looking into docks. Gnome-Do + Docky looks quite nice.

---

### Post by piousp on 2010-02-23
Well, you should take a look at KDE or E17, both of em are pretty.
You could go the way of xfce, but i feel you are trying to get away from the gnomish apereance.

---

### Post by Satoru-san on 2010-02-23
> **piousp said:**
> Well, you should take a look at KDE or E17, both of em are pretty.


Another vote for e17

---

### Post by litemirrors on 2010-02-23
But you are wrong, Compiz is not buggy it's merely that your drivers for your system aren't correctly implimented with Linux. Goto anyones computer that has drivers which aren't buggy and tell me Compiz is flawed, indeed Compiz is so advanced not even the Kwin developers thought they could understand it and use the code without trashing their KDE alltogether [http://techbase.kde.org/Projects/KWin/4.0-release-notes#Why_not_Compiz.3F](http://techbase.kde.org/Projects/KWin/4.0-release-notes#Why_not_Compiz.3F)

---

### Post by Pablo Pablovski on 2010-02-23
Wow....:confused:

FWIW, I agree with litemirrors - Compiz works a treat on systems that have good, stable graphic drivers AND enough GPU oomph to do it justice. I use Compiz extensively (AMD 3500+ with Nvidia 8800GTS / 640MB video) and it runs perfectly.

If it doesn't play well with your netbook - and a Dell Mini 10 is a pretty low power machine - it's very probably down to the limited power of the graphics card, and less likely to be driver-related. 

Oh, and this is me leaving you alone, 'k?

---

### Post by Woolio1 on 2010-02-23
Okay, now I have another question. Once I've got my window manager and everything, how would I change the default window manager to the new one?

---

### Post by BrokenKingpin on 2010-02-23
On the login screen select the session button, this will give you a list of desktop environments to log into. When you select the new one it will ask if you want to keep it as the default.

---

### Post by Tristam Green on 2010-02-23
> **Woolio1 said:**
> Okay, now I have another question. Once I've got my window manager and everything, how would I change the default window manager to the new one?

at the login screen, select "session", and select the new DE.  you'll have the option of making it the default upon the next login.

---

### Post by Woolio1 on 2010-02-23
Ah, okay, thanks.

---

### Post by Frak on 2010-02-23
> **litemirrors said:**
> But you are wrong, Compiz is not buggy it's merely that your drivers for your system aren't correctly implimented with Linux. Goto anyones computer that has drivers which aren't buggy and tell me Compiz is flawed, indeed Compiz is so advanced not even the Kwin developers thought they could understand it and use the code without trashing their KDE alltogether [http://techbase.kde.org/Projects/KWin/4.0-release-notes#Why_not_Compiz.3F](http://techbase.kde.org/Projects/KWin/4.0-release-notes#Why_not_Compiz.3F)
Pfft... stable Compiz. That's hilarious.

---

### Post by litemirrors on 2010-02-23
> **Frak said:**
> Pfft... stable Compiz. That's hilarious.

But it is..... it is.... why do you think otherwise? The code works universally as long as hardware is correctly implimented through linux.

---

### Post by Zlatan on 2010-02-23
> **Woolio1 said:**
> I want to change things. I've seen so many interesting things in Ubuntu, but I'm still using a slightly modified Default.

I need some recommendations, instructions, anything you can throw at me. I want to know how to do these interesting things you see in the Art subforum and other places. I want to try out different window managers, different compositors, different desktop environments, etcetera. 

I want to make my Ubuntu look better.

Currently, I'm using Metacity as my Compositing manager and the GTK-Window-Decorator as my... Window decorator. Metacity's also my Window Manager. 

I don't like Compiz, it was bloaty and buggy when I used it. And don't try telling me I'm wrong, because that's not possible. So I want to get away from Compiz, I want to try other things. 

Any and all recommendations are appreciated. 

-Henry Ericson

```
sudo apt-get install gnome-shell
``` if I remember that correctly?:) no reason to play too much with compiez and metacities- GS will be here in the future

---

### Post by snkiz on 2010-02-23
> **Woolio1 said:**
> I want to change things. I've seen so many interesting things in Ubuntu, but I'm still using a slightly modified Default.

I need some recommendations, instructions, anything you can throw at me. I want to know how to do these interesting things you see in the Art subforum and other places. I want to try out different window managers, different compositors, different desktop environments, etcetera. 

I want to make my Ubuntu look better.

Currently, I'm using Metacity as my Compositing manager and the GTK-Window-Decorator as my... Window decorator. Metacity's also my Window Manager. 

I don't like Compiz, it was bloaty and buggy when I used it. And don't try telling me I'm wrong, because that's not possible. So I want to get away from Compiz, I want to try other things. 

Any and all recommendations are appreciated. 

-Henry Ericson

This is a fine example of how hiding features is damaging. If you turned on compositing from the appearance thingy, then I got news for you, you are using compiz. If you want to try something else than apt-get/synaptic it. and see how it works for you. In my experience however, its a little like chasing the dragon. Your always searching for that one feature (whatever it is.) that gnome/kde did so simply.

My current Desktop:
session manager = Gnome
window manager = Openbox
file manger = nautilus
desktop manager = rox
panel = cairo-dock
info = conky  :D

---

### Post by Woolio1 on 2010-02-23
> **snkiz said:**
> This is a fine example of how hiding features is damaging. If you turned on compositing from the appearance thingy, then I got news for you, you are using compiz. If you want to try something else than apt-get/synaptic it. and see how it works for you. In my experience however, its a little like chasing the dragon. Your always searching for that one feature (whatever it is.) that gnome/kde did so simply.

My current Desktop:
session manager = Gnome
window manager = Openbox
file manger = nautilus
desktop manager = rox
panel = cairo-dock
info = conky  :D

I'm not. I used the Gconf-editor to enable the Metacity Compositing, because it can do that, and completely uninstalled Compiz from my system. 

And the Metacity Compositing Manager works fine.

---

### Post by snkiz on 2010-02-23
> **Woolio1 said:**
> I'm not. I used the Gconf-editor to enable the Metacity Compositing, because it can do that, and completely uninstalled Compiz from my system. 

And the Metacity Compositing Manager works fine.

Well I stand corrected, your not as new as your original post suggested. 

I forgot to mention I use xcompmgr for compositing. I also run compiz on a acer D250 without issue. The key is to remember the power of your gfx when setting up compiz. A netbook will not handle the cube well, but shadows, transparency, wobble and other simpler effects work well, if you don't use to many.

---

### Post by Simian Man on 2010-02-23
I use xfwm as my window manager.  It has support for compositing, looks good, has a lot of handy options like snapping windows and is fairly easy to theme too.

It doesn't have the eye-candy of compiz or kwin (but is more stable).  And it totally much puts metacity to shame :).

---

### Post by cammin on 2010-02-23
> **woolio1 said:**
> and don't try telling me i'm wrong, because that's not possible.

-henry ericson

nice

---

### Post by Woolio1 on 2010-02-24
> **cammin said:**
> nice

Out of context, my friend.

I said "This deals strictly with my opinions and my personal experience. don't try telling me I'm wrong, because that's impossible."

Or something like that. Anyway, what I said is true. You cannot prove my opinions and experiences wrong, because I had my experiences, and I have my opinions. You don't.

---

