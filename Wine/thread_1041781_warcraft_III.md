---
title: "warcraft III"
date: 2009-01-16
forum: Wine
---

### Post by Aksha on 2009-01-16
how do i install run and play battlenet on warcraft III tft in wine?

---

### Post by hotweiss on 2009-01-17
just right click on the set-up file and select run with wine

it runs perfectly on Ubuntu

PS-ask if you have any more problems

---

### Post by Aksha on 2009-01-17
it works but its really slow how can i fix it

---

### Post by hotweiss on 2009-01-18
> **Aksha said:**
> it works but its really slow how can i fix it

add the -opengl extension at the end:

> wine .wine/drive_c/Program\ Files/Warcraft\ III/Frozen\ Throne.exe -opengl

---

### Post by Aksha on 2009-01-18
> **hotweiss said:**
> add the -opengl extension at the end:

thanks!! I test now to see the results

---

### Post by Aksha on 2009-01-18
how do i minimize once im in game

---

### Post by kyeh on 2009-01-18
alt tabbing screws up the game, so don't try it!

---

### Post by hikaricore on 2009-01-18
Minimizing it _may_ work if you run it in a WINE "desktop" window as such:

> wine explorer /desktop=WCIII,**1024x768** Frozen\ Throne.exe -opengl

Adjusting the size of the desktop (in bold) as needed.

As I said this may work, but I don't have the game to test it myself.

---

### Post by hotweiss on 2009-01-18
> **kyeh said:**
> alt tabbing screws up the game, so don't try it!

Tabbing works for me, just disable (in graphics tab) allow window manager to config and control windows (both checkmarks), and then enable virtual desktop (set your actual screen resolution). You will now be able to tab back and forward.

Here are some tweaks that will improve the video quality of Warcraft 3:

1. Type 

> regedit

2. Go to: Hkey_Current_User --> Software --> Blizzard Enterteinment --> Warcraft III --> Video

3. Edit refreshrate and enter your correct refresh rate, you now should have no more tearing

4. Edit reswidth and resheight to match your actual screen resolution, your graphic's should now be a little sharper

---

### Post by hotweiss on 2009-01-18
> **hikaricore said:**
> Minimizing it _may_ work if you run it in a WINE "desktop" window as such:



Adjusting the size of the desktop (in bold) as needed.

As I said this may work, but I don't have the game to test it myself.

Use my instructions to make life simple, don't know what the outcome of this will bring you. I have tested my instructions.

---

### Post by hikaricore on 2009-01-18
> **hotweiss said:**
> Use my instructions to make life simple, don't know what the outcome of this will bring you. I have tested my instructions.

Wow thanks, I did say that I couldn't test it so there was no need for this.
The OP can decide for themselves.

---

### Post by hotweiss on 2009-01-19
> **hikaricore said:**
> Wow thanks, I did say that I couldn't test it so there was no need for this.
The OP can decide for themselves.

LOL, no hard feelings. I just wanted the OP to have a 100% tried solution.

---

### Post by kyeh on 2009-01-19
arg, my alt stabbing still doesn't work :( however after changing the registry, the game looks a lot nicer :P

---

### Post by hotweiss on 2009-01-19
> **kyeh said:**
> arg, my alt stabbing still doesn't work :( however after changing the registry, the game looks a lot nicer :P

So compiz is enabled, and you have your wine config looking like this:

[IMG]http://img176.imageshack.us/img176/1386/winecfgeu8.png[/IMG]

---

### Post by Aksha on 2009-01-19
everything u guys said is working thanks!

---

