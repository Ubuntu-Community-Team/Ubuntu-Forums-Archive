---
title: "Window Decorations"
date: 2009-12-30
forum: The Cafe
---

### Post by TheNessus on 2009-12-30
Disabled.

Wow, the difference... I mean, all the programs are a lot nicer now in fullscreen, and nice too when not maximized as well. Takes a while to get used to it honestly, but the feel is totally different, new, and better.

They should find a way to make the maximize/minimize/menu/exit buttons be INSIDE the window somewhere on the corners instead of having window decorations just for 4 little buttons...

---

### Post by markp1989 on 2009-12-30
> **TheNessus said:**
> Disabled.

Wow, the difference... I mean, all the programs are a lot nicer now in fullscreen, and nice too when not maximized as well. Takes a while to get used to it honestly, but the feel is totally different, new, and better.

They should find a way to make the maximize/minimize/menu/exit buttons be INSIDE the window somewhere on the corners instead of having window decorations just for 4 little buttons...

i would like that aswell, having the close etc buttons inline with the menu bar  on firefox  would rock.

---

### Post by hessiess on 2009-12-30
Just use a window manager like Xmonad/DWM instead of a full desktop environment. The GUI imeadeatly becomes redundant because you can do everything relating to window management completely with the keyboard.

---

### Post by markp1989 on 2009-12-30
> **hessiess said:**
> Just use a window manager like Xmonad/DWM instead of a full desktop environment. The GUI imeadeatly becomes redundant because you can do everything relating to window management completely with the keyboard.

i been using xmonad for a while now, its cool, takes a while getting used to the short cuts, but after a few days its like 2nd nature :D

---

### Post by TheNessus on 2009-12-30
> **hessiess said:**
> Just use a window manager like Xmonad/DWM instead of a full desktop environment. The GUI imeadeatly becomes redundant because you can do everything relating to window management completely with the keyboard.
I like my gnome+compiz that I modified heavily too much :)

---

### Post by Xbehave on 2009-12-30
> **markp1989 said:**
> i would like that aswell, having the close etc buttons inline with the menu bar  on firefox  would rock.
I think people are trying to do the opposite in kde4 put the menubar in the window decoration.

---

### Post by TheNessus on 2009-12-30
> **Xbehave said:**
> I think people are trying to do the opposite in kde4 put the menubar in the window decoration.
That might work, but I reckon it would take a lot of reprogramming in nearly all programs?

---

### Post by Xbehave on 2009-12-30
> **TheNessus said:**
> That might work, but I reckon it would take a lot of reprogramming in nearly all programs?
Well it only works in kde for now, because the kmenubar object/class is used by all kde programs so you can already hide it in most programs and kde3 had a mac like mode, i think all gnome programs use a common menubar class so adding support for them shouldn't be too hard (would need an experienced gnome programmer though), support for stuff like firefox would be next to impossible though.

---

### Post by pelle.k on 2009-12-30
> **Xbehave said:**
> I think people are trying to do the opposite in kde4 put the menubar in the window decoration.

That is _**so**_ cool! Is there any example you can point to?
This has been a dream of mine for quite some time. Didn't expect someone to implement it though. That solves the old "mac menubar" saves precious space problem, while being more usable (IMHO). As with everything, some people would certainly think this idea stinks, so having it optional would probably be the way to go.

> **TheNessus said:**
> That might work, but I reckon it would take a lot of reprogramming in nearly all programs?
No, just take a look at gnome-globalmenu. It's doable, but would require some metacity (or kwin) modifications though. It would probably me helpful if the gtk guys could do some work as well. But it wouldn't have to be supported at application level, only toolkit/WM level.

---

### Post by chucky chuckaluck on 2009-12-30
evilwm would be best if you don't want everything maximized but still without windec.

---

### Post by RiceMonster on 2009-12-30
> **hessiess said:**
> Just use a window manager like Xmonad/DWM instead of a full desktop environment. The GUI imeadeatly becomes redundant because you can do everything relating to window management completely with the keyboard.

Yeah agreed, especially about dwm.

> **chucky chuckaluck said:**
> evilwm would be best if you don't want everything maximized but still without windec.

Well, you could always just use float all the time in dwm as well, then you still have the option of tiling, as well. Plus, I find evilwm a bit of a pain since there's no config file or anything and you have to use different flags when you launch it to configure it.

---

### Post by Xbehave on 2009-12-30
the kde4 stuff i was talking about is [here]("http://www.sharpley.org.uk/page/blog/21") (from [here]("http://forum.kde.org/brainstorm.php#idea61999")) not sure if it went anywhere though.

---

### Post by chucky chuckaluck on 2009-12-30
> **RiceMonster said:**
> Well, you could always just use float all the time in dwm as well, then you still have the option of tiling, as well. Plus, I find evilwm a bit of a pain since there's no config file or anything and you have to use different flags when you launch it to configure it.

from [http://www.6809.org.uk/evilwm/usage.shtml](http://www.6809.org.uk/evilwm/usage.shtml) ...

"evilwm will also read options, one per line, from a file called .evilwmrc in the user's home directory. Options listed in a configuration file should omit the leading dash. Options specified on the command line override those found in the configuration file."

i know i've used an .evilwmrc before, but i can't find the one i used as a starting point.

---

### Post by crimesaucer on 2009-12-30
+1 for Xmoand: [http://haskell.org/haskellwiki/Xmonad/Using_xmonad_in_XFCE](http://haskell.org/haskellwiki/Xmonad/Using_xmonad_in_XFCE)


..... although I do miss the the emerald/xfwm4 window themes that I used to use.


For anybody interested in using xfce4 with xmonad, here is my custom xmonad.hs file (using the numpad for workspaces):

```

import XMonad
import XMonad.Config.Xfce
import qualified XMonad.StackSet as W
import XMonad.Util.EZConfig
import XMonad.Hooks.ManageDocks
import XMonad.Layout.Gaps
import Control.Monad (liftM2)

-- Width of the window border in pixels.
--
myBorderWidth   = 1
 
-- modMask lets you specify which modkey you want to use. The default
-- is mod1Mask ("left alt").  You may also consider using mod3Mask
-- ("right alt"), which does not conflict with emacs keybindings. The
-- "windows key" is usually mod4Mask.
--
myModMask       = mod1Mask
-- other imports

 
myWorkspaces = ["1","2","3","4","5","6","7","8","9","0"]
 
modm = mod1Mask -- for numpad workspaces
 
myKeys = -- use with EZConfig.additionalKeys or edit to match your key binding method
    [
    ((modm .|. shiftMask, xK_KP_Add ), kill),
    ((modm .|. shiftMask, xK_KP_Enter ), spawn "/home/seventy3/firefox_start.sh"),
    ((modm .|. shiftMask, xK_KP_Delete ), spawn "killall firefox-bin"),
    ((modm .|. shiftMask, xK_KP_Divide ), spawn "ossxmix"),
    ((modm .|. shiftMask, xK_Home ), spawn "sudo shutdown -h now"),
    ((modm .|. shiftMask, xK_End ), spawn "sudo shutdown -r now"),
    ((modm,               xK_KP_Subtract ), windows W.focusDown),
    ((modm .|. shiftMask, xK_KP_Subtract ), windows W.swapDown),
    ((modm .|. shiftMask, xK_KP_Multiply ), windows W.swapUp),
    ((modm,               xK_KP_Multiply ), windows W.focusUp),
    ((modm,               xK_Page_Up ), sendMessage Shrink),
    ((modm,               xK_Page_Down ), sendMessage Expand)
    ]
    ++
    [((m .|. modm, k), windows $ f i)
        | (i, k) <- zip myWorkspaces numPadKeys
        ,  (f, m) <- [(W.greedyView, 0), (W.shift, shiftMask)]
    ]
    
 
-- Non-numeric num pad keys, sorted by number 
numPadKeys = [ xK_KP_End,  xK_KP_Down,  xK_KP_Page_Down -- 1, 2, 3
             , xK_KP_Left, xK_KP_Begin, xK_KP_Right     -- 4, 5, 6
             , xK_KP_Home, xK_KP_Up,    xK_KP_Page_Up   -- 7, 8, 9
             , xK_KP_Insert] -- 0 
 
-- The mask for the numlock key. Numlock status is "masked" from the
-- current modifier status, so the keybindings will work with numlock on or
-- off. You may need to change this on some systems.
--
-- You can find the numlock modifier by running "xmodmap" and looking for a
-- modifier with Num_Lock bound to it:
--
-- > $ xmodmap | grep Num
-- > mod2        Num_Lock (0x4d)
--
-- Set numlockMask = 0 if you don't have a numlock key, or want to treat
-- numlock status separately.
--
myNumlockMask   = mod2Mask
 
-- Border colors for unfocused and focused windows, respectively.
--
myNormalBorderColor  = "#5E98AB"
myFocusedBorderColor = "#FFB760"

-- manage hooks attempt
--
myManageHook = composeAll
   [ className =? "Gimp-2.6"                               --> (doFloat <+> viewShift "9"),
     className =? "Inkscape"                               --> viewShift "8",
     className =? "Googleearth-bin"                        --> viewShift "7",
     className =? "Stellarium"                             --> viewShift "7",
     className =? "Celestia"                               --> viewShift "7",
     className =? "Gpredict"                               --> viewShift "7",
     className =? "Mirage"                                 --> viewShift "6",
     className =? "Ristretto"                              --> viewShift "6",
     className =? "Xfce4-appearance-settings"              --> doFloat,
     className =? "Agave"                                  --> doFloat,
     className =? "Xfce4-screenshooter-plugin"             --> doFloat,
     className =? "Xfrun4"                                 --> doFloat,
     className =? "Gcalctool"                              --> doFloat,
     className =? "Xarchiver"                              --> doFloat,
     className =? "File-roller"                            --> doFloat,
     className =? "Firefox" <&&> resource =? "Dialog"      --> doFloat,
     className =? "Firefox" <&&> resource =? "Extension"   --> doFloat,
     className =? "Firefox" <&&> resource =? "Browser"     --> doFloat,
     className =? "Firefox" <&&> resource =? "Download"    --> doFloat
   ]
   where viewShift = doF . liftM2 (.) W.greedyView W.shift
------------------------------------------------------------------------

 
main = xmonad $ xfceConfig
	{
	borderWidth        = myBorderWidth,
	normalBorderColor  = myNormalBorderColor,
        modMask            = myModMask,       
        workspaces         = myWorkspaces,
        manageHook         = myManageHook <+> manageHook xfceConfig,
        layoutHook         = gaps [(D,29), (U,20)] $ Tall 1 (3/100) (1/2) ||| Full,
	focusedBorderColor = myFocusedBorderColor
	}`additionalKeys` myKeys

```

---

### Post by RiceMonster on 2009-12-30
> **chucky chuckaluck said:**
> from [http://www.6809.org.uk/evilwm/usage.shtml](http://www.6809.org.uk/evilwm/usage.shtml) ...

"evilwm will also read options, one per line, from a file called .evilwmrc in the user's home directory. Options listed in a configuration file should omit the leading dash. Options specified on the command line override those found in the configuration file."

i know i've used an .evilwmrc before, but i can't find the one i used as a starting point.

Oh cool, didn't know about that. Thanks.

---

### Post by chucky chuckaluck on 2009-12-30
> **RiceMonster said:**
> Oh cool, didn't know about that. Thanks.

and i just realized windows can be moved and resized/reshaped with the keyboard.

---

### Post by bailout on 2009-12-30
> **TheNessus said:**
> Disabled.

Wow, the difference... I mean, all the programs are a lot nicer now in fullscreen, and nice too when not maximized as well. Takes a while to get used to it honestly, but the feel is totally different, new, and better.

They should find a way to make the maximize/minimize/menu/exit buttons be INSIDE the window somewhere on the corners instead of having window decorations just for 4 little buttons...

What de are you using? I know that both kde and openbox allow turning off the win decs but I could never find a way of doing it in gnome.

On a normal sized screen it doesn't bother me but when space is limited ie netbook or even laptop it can be useful. Especially as modern wide format screens have limited height.

You can get the close max/min commands by right clicking on the taskbar.

---

### Post by TheNessus on 2009-12-30
> **bailout said:**
> What de are you using? I know that both kde and openbox allow turning off the win decs but I could never find a way of doing it in gnome.

On a normal sized screen it doesn't bother me but when space is limited ie netbook or even laptop it can be useful. Especially as modern wide format screens have limited height.

You can get the close max/min commands by right clicking on the taskbar.

In gnome you just disable it in Compiz manager. disable the 'any' command, or decide which specific progs use or don't use it.

---

### Post by chucky chuckaluck on 2009-12-31
you can run openbox, like evilwm, without decorations (using alt+mouse click to move and resize) by placing the following in your ~/.config/openbox/rc.xml file...

```
  <!-- match all windows, and remove their decorations -->
  <application class="*">
    <decor>no</decor>
  </application>
```

---

### Post by Hetor on 2009-12-31
You can disable decorations for maximized windows only, by the way. Also you can use the keyboard to maximize/minimize/close.

---

### Post by jpkotta on 2009-12-31
I still have titlebars, but they don't really have buttons and all of the bindings I have for them are replicated with the super key in the main window area.  E.g. double left click on titlebar toggles maximized, so super+double left click in the main window area also toggles maximized.

---

