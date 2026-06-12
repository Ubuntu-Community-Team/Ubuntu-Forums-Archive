---
title: "Unity"
date: 2012-12-28
forum: Testimonials &amp; Experiences
---

### Post by kuvanito on 2012-12-28
I Love Unity and Ubuntu BUT I wish Unity Lenses Gone!
There is no need for the Lenses when you have a BIG Search Bar with the HUD.
I would love to click on my Dash Home and see all APPS installed.Well,that's my wish...):P

---

### Post by pompel9 on 2012-12-28
You have a lense already for apps installed.
There you have 3 rows. Recently used, installed and available for download. Just click on installed, there is a option to show all installed.

---

### Post by Yougo on 2012-12-28
you can pres Super+a to go to the applications lens directly.
there's a letter like that for every lens. if you hold Super down, you get a shortcut list :)

also right-click the dash button to see a list of lenses to pick from

----------------------------
what i did was set the top-left corner to open the applications lens!
here's how:

1) install xdotool
in terminal:
```
sudo apt-get install xdotool
```
or install it from the Software center or Synaptic.
this little program lets you simulate keystrokes and more with commands.

2) test the desired effect
in terminal
```
xdotool key Super_L
``` this command tells the system the left super key has been pressed. dash should open, like you pressed the actual button.
```
xdotool key Super_L+a
``` this command tells the system the left super key and "a" has been pressed. the applications lens should open like you pressed the key combo yourselves.

3) if you haven't already, install compizconfig-settings-manager. 
it is an extensive tool for setting all kinds of compiz effects. be careful with this as you can screw up things with it. 

4) open compizconfig-settings-manager, or CCSM for short, by typing "ccsm" in the dash
find the section called "Commands" (right at the top) and open it.

5) in the "commands" tab, write your desired xdotool command. remember what command line # you wrote it behind. 

6) go to the "edge bindings" tab. press the "none" button behind the command line # you remembered from step 5. click on the desired corner in the miniature screen. it turns green. then click OK. 

7) now click "back" on the CCSM main screen. your new settings are stored now. 

8) check the box before "commands" button to activate this plugin

9) i made further tweaks by setting a 500 ms delay for edge triggers (general options) so i won't accidentally open the dash, and set the 'commands' plugin to load after the unity plugin (preferences>plugin-list), to make sure it works

you may need to log out and in, but now you can slam your mouse in the corner/edge you chose, and the Dash will open :D

---

