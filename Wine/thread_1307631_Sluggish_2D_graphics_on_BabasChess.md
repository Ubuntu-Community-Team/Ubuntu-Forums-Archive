---
title: "Sluggish 2D graphics on BabasChess"
date: 2009-10-31
forum: Wine
---

### Post by MrNatewood on 2009-10-31
This has only strated happening after upgrading to ubuntu 9.10 "karmic koala".

Making moves is incredibly sluggish, everything is very slow.

From the official website support:
> Why is the piece movement slow? Why is there a delay when I make a move on the board?

    BabasChess uses a double-buffering technique to draw the board without flickering; unfortunately, on a few video cards this technique determines a slow board redraw (delays when moving a piece or between the end of the piece movement and the subsequent board update). This problem can be usually fixed as follows: 1) open the Windows Display Properties (right click on your desktop and select "Properties"), 2) select the "Settings" tab (where you can change the screen resolution, color quality, ...), 3) press the "Advanced" button, 4) select the "Troubleshoot" (or "Performance") tab and 5) decrease the hardware acceleration by one step.

What similar action can I do on wine/ubuntu?

Edit: Solved by changing the wine audio driver to Alsa from Esound.

---

### Post by beastrace91 on 2009-10-31
What type of graphics card are you using? Also I do not have my Ubuntu system in front of me at the moment but I am pretty sure there is a setting in the winecfg to toggle your level of hardware acceleration.

Regards,
~Jeff

---

### Post by myromance123 on 2009-11-01
May I ask, are your hardware drivers installed?
 I would think after upgrading or doing a fresh install of Karmic, naturally your graphics drivers would not be installed.

Have you tried installing the drivers from System->Administration->Hardware Drivers?

If those are installed but you still have this sluggish performance you may need to install the binary driver for your graphics card instead.

Please let us know what card you are using (what brand) and possibly if you are using any graphics drivers.

---

### Post by MrNatewood on 2009-11-01
I have an nvidia geforce FX5600 ultra and installed the binary drivers.

[ATTACH]134046[/ATTACH]

---

### Post by myromance123 on 2009-11-01
Hmm it would seem you have the right driver installed (according to Ubuntu and Nvidia's site for your card).

Is Compiz enabled? I mean the special-effects/desktop-effects ?
That could be a reason why your game is running sluggishly.
To disable desktop effects, right-click anywhere on your desktop and choose Change Desktop Background then go to the Visual Effects tab and select None.
Try and run the game again.

If the results are the same, then please run the game via a terminal and post the output here.

To run the game from a terminal, type the following:
```
wine game.exe
```
where game is replaced with the name of your game's exe file.
If it doesn't work at first, you may need to change to the directory of your game using cd.

EDIT: You may want to give Nvidia's latest driver a shot too. It says it has support for you card. The version is 190.42 and I myself have tested it on a lot of games with maximum graphics. It works far better than previous drivers from them. I can try and help you install it if you do not know how to.

---

### Post by MrNatewood on 2009-11-01
Desktop effects are disabled.

Terminal output:
```
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -120, std (d/m/y): 27/09/2009, dlt (d/m/y): 27/03/2009
fixme:richedit:ME_HandleMessage ECO_NOHIDESEL not implemented yet!
fixme:richedit:ME_HandleMessage ECO_NOHIDESEL not implemented yet!
fixme:richedit:ME_HandleMessage ECO_NOHIDESEL not implemented yet!
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -120, std (d/m/y): 27/09/2009, dlt (d/m/y): 27/03/2009
fixme:richedit:ME_HandleMessage ECO_NOHIDESEL not implemented yet!
fixme:richedit:ME_HandleMessage ECO_NOHIDESEL not implemented yet!
fixme:richedit:ME_HandleMessage ECO_NOHIDESEL not implemented yet!
fixme:richedit:ME_HandleMessage ECO_NOHIDESEL not implemented yet!
fixme:richedit:ME_HandleMessage ECO_NOHIDESEL not implemented yet!






```

---

### Post by myromance123 on 2009-11-01
I forgot to ask!
What version of wine are you using?

 to check either go to Applications->Wine->Configure Wine and open the tab About or open up Synaptic Package Manager and type in wine in the search bar.

---

### Post by beastrace91 on 2009-11-01
EDIT - Your card is a legacy card - do not upgrade past the 173 drivers. Sorry about that.

Also regarding finding your wine version quickest way is to open terminal and run ```
wine --version
```

~Jeff

---

### Post by myromance123 on 2009-11-02
@beastrace,
 
 If I'm not wrong the graphics card he is using is already considered a legacy card no?
I did a check on Nvidia and they suggest the version 173.xx for his card.

I have personally tried Nvidia's 190.42 driver and it works way better than 185.xx versions I used. My computers have become quiet and take up less processing power during gameplay after installing it, so yes I agree you might want to truly consider Nvidia's latest driver or at least something newer than what you have!

Bare in mind, know how to revert to the 173.xx driver in case things should fail. Better safe than sorry. :D

---

### Post by beastrace91 on 2009-11-02
Ahh you are correct myromance, I though the legacy cards started with the geforce 4 series but it is 5 series and older. Stick with the 173 drivers with that card.

Also regarding the 185 vs 190 driver for non-legacy cards it is important to remember that while you personally have good luck with the beta driver others may not. I know for instance certain beta drivers cause massive stability issues on my 260m.

~Jeff

---

### Post by MrNatewood on 2009-11-04
> **myromance123 said:**
> I forgot to ask!
What version of wine are you using?

 to check either go to Applications->Wine->Configure Wine and open the tab About or open up Synaptic Package Manager and type in wine in the search bar.

Wine vesrion is 1.1.31
It worked fine with same version on 9.04.

---

