---
title: "Precise - activie dodge re-enable"
date: 2012-03-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bpb101 on 2012-03-07
amigos/amigoas 

using 12.04 beta and i found out active dodge is gone! It nor installed or avable to install.

anybody know where i how i can get it working .
i downloaded ubuntu tweak and that had the option but when i went to change it to active dodge it changed but never change 

anybody any help


__________________________________________________________
this was one of / if not  the best things in unity , since i have only have  notebooks.

---

### Post by kazztan0325 on 2012-03-07
Hi bpb101,

It seems the function was removed from 12.04.

Sadly I don't know how to re-enable it, and it seems there is no workaround at present.

---

### Post by squilookle on 2012-03-07
Does this refer to the launcher hiding itself when you have a full screen window open? 

If not, ignore me. If so, I read that it is gone in 12.04. Personally, I think that is a shame though because I quite liked it... 

I haven't tried 12.04 yet, so I'm not sure how it behaves instead.

---

### Post by oldos2er on 2012-03-07
Thread moved to Ubuntu +1 (Precise Pangolin).

---

### Post by bpb101 on 2012-03-07
> **squilookle said:**
> Does this refer to the launcher hiding itself when you have a full screen window open? 

If not, ignore me. If so, I read that it is gone in 12.04. Personally, I think that is a shame though because I quite liked it... 

I haven't tried 12.04 yet, so I'm not sure how it behaves instead.

yes , that what im talking about , i thought i heard somebody calling it that , i thought the feature was quite good and now i cant work with the laucher on the side when i have even firefox open

anybody, i dont care what, but this will p*** me off when 12.04 hits 
i only have it on a old un used netbook. but i plan to update my netbook that i use on a daily basic on the release date , but now will i have to reconsider

---

### Post by philinux on 2012-03-07
> **bpb101 said:**
> amigos/amigoas 

using 12.04 beta and i found out active dodge is gone! It nor installed or avable to install.

anybody know where i how i can get it working .
i downloaded ubuntu tweak and that had the option but when i went to change it to active dodge it changed but never change 

anybody any help


__________________________________________________________
this was one of / if not  the best things in unity , since i have only have  notebooks.

 [http://ubuntuforums.org/showpost.php?p=11676275&postcount=35](http://ubuntuforums.org/showpost.php?p=11676275&postcount=35)

---

### Post by x-shaney-x on 2012-03-07
It still works in Unity 2D and can be enabled via dconf-editor (for now, not sure how long before that goes too).

---

### Post by EgoGratis on 2012-03-07
I use [this script]("http://ubuntuforums.org/showpost.php?p=11743771&postcount=6") for now (single screen/workspace). I hope this behavior will remain a part of Unity Shell too but i don't know how this will end. It looks like developers are strongly against this feature but we can only hope in the end something that will make developers and users happy will emerge.

P.S. Pretty much everything was said about this topic and don't use "bad language" it won't change anything if something will change then probably it would be solution that would make both developers and users happy.

---

### Post by x-shaney-x on 2012-03-07
How would such a script be used?  Startup application?

---

### Post by EgoGratis on 2012-03-07
Yes i have it in startup applications. 

For now it's quite "robust" and "reliable" at doing the job but this is suboptimal solution and works only for single screen/workspace and somebody with more skills could probably do it better or the best solution would be if mode like this would still be part of Unity Shell!

---

### Post by x-shaney-x on 2012-03-07
> **EgoGratis said:**
> It looks like developers are strongly against this feature but we can only hope in the end something that will make developers and users happy will emerge.


Well according to Mr S, the developers AREN'T against it and neither is he, he even said he liked it and clearly so do the 100 or so people subscribed to the discussion.
The "user tests" suggest it is confusing and that is why it is gone.

---

### Post by x-shaney-x on 2012-03-07
I can't seem to get the script to do it's job.
I assume I am meant to manually add the X/Y values in the script (which I have)?
It runs without any errors but the launcher doesn't move when maximizing.

<EDIT>

Silly me, I was trying it in Unity 2D :)
After switching to standard Unity it is indeed working well and looks like being the only way I will get dodge back.

Just wondering how that script could be adapted to Unity 2D?
I have tried changing the lines to point to the Unity 2D settings in gconf and it DOES change them but doesn't have any affect on the launcher.  I assume it would have to be done through dconf?

---

### Post by EgoGratis on 2012-03-07
I tried to do it for Unity 2D too through dconf but it didn't work. Maybe this will become problem for Unity 3D too when settings get migrated to dconf?

---

### Post by x-shaney-x on 2012-03-07
I have managed to modify the script and it partially works :(
When I maximize a window it simply changes the behaviour to autohide globally.

Here is what I have so far if anyone knows where I'm going wrong:

```
#!/bin/bash
# Install wmctrl before using: sudo apt-get install wmctrl

while true; do
sleep 2 # Set delay

SHOW_LAUNCHER=$(wmctrl -lpG | grep -c "1301 744") # Use wmctrl -lpG and find max value when Launcher is in neverhide mode
HIDE_LAUNCHER=$(wmctrl -lpG | grep -c "1366 744") # Use wmctrl -lpG and find max value when Launcher is in autohide mode

if [ $SHOW_LAUNCHER -eq 0 -a $HIDE_LAUNCHER -eq 0 ]
then
    CURRENT=$(gsettings get com.canonical.Unity2d.Launcher hide-mode)
    if [ $CURRENT -ne 0 ]
    then
        gsettings set com.canonical.Unity2d.Launcher hide-mode 0
    fi
else
    CURRENT=$(gsettings get com.canonical.Unity2d.Launcher hide-mode)
    if [ $CURRENT -ne 1 ]
    then
        gsettings set com.canonical.Unity2d.Launcher hide-mode 1
    fi
fi
done
```

Though as I mentioned before, dodge windows DOES still work in unity 2D so a script isn't needed, I am just looking into future possibilities for when they do remove it in 2D as well.

---

### Post by EgoGratis on 2012-03-07
Dconf should be used and i had solution that should work but there is one problem with Unity 2D.  If u test it manually with dconf you will notice when Unity 2D launcher is set to never hide mode and strut is enabled it does not appear automatically. User has to log out/ log in or press Super Key.

Until this gets fixed the same approach from Unity 3D can't be used or if somebody knows workaround or better solution.

---

### Post by EgoGratis on 2012-03-07
I tested on fully updated Ubuntu 12.04 install and it works better. I will look in to it tomorrow.

---

### Post by snkiz on 2012-03-07
Why use a script in 2D? dodge is still there, they've made no mention of removing it from 2D. I'd be surprised if they did, dodge might be unexpected and confusing on a desktop (to idiots and morons.) But the other form factors that 2D is targeted for, its kinda a must have isn't it?

---

### Post by EgoGratis on 2012-03-08
I have working solution for Unity 2D too but i agree until Unity 2D has Dodge Windows "script approach" is giant step back.

Unity 2D has one "strange bug" too if window is maximized and then minimized in launcher it still presents it self as window with max width/height.

If i would try maybe i could make Unity 2D work in a way all workspaces could be used and script would know if windows are maximized on current workspace. For more screens i don't have solution.

For Unity 3D on the other hand it would be harder to do anything more from my part than script i wrote. It's more complex to get number of workspaces and list windows on it with Compiz and more experience programmer would be needed. 

Users of Unity 2D you didn't lost anything just jet. Maybe if you are lucky you will have this by default in Ubuntu 12.04 if not i can publish my script then too if anybody will find it useful.

For us Unity 3D users i guess until somebody comes up with better solution script for one screen/workspace is all we have. I personally am using it and will continue to do so!

---

### Post by rg4w on 2012-03-08
> **x-shaney-x said:**
> The "user tests" suggest it is confusing and that is why it is gone.
Those "user tests" are curious things:  while I understand the explanation given for how the testing results compelled them to remove that feature, it seems the same principle of "where did it go?" would apply equally well to concealing the menu bar, which unfortunately remains an anti-feature in 12.04.

---

### Post by snkiz on 2012-03-08
I tried that exact same argument, logic need not apply it turns out.

@ego I've seen that bug, it doesn't happen all the time. open up an non-maximized window and that corrects it.

---

### Post by rg4w on 2012-03-08
> **snkiz said:**
> I tried that exact same argument, logic need not apply it turns out.
Was this in a venue for which you have a URL?

I want to raise the issue at UDS to see if it can be reconsidered, so it'll be helpful to get as much background on it as I can.

TIA -

---

### Post by x-shaney-x on 2012-03-08
Something that could possibly be promising if there are any coders reading:  [https://lists.launchpad.net/unity-design/msg08676.html](https://lists.launchpad.net/unity-design/msg08676.html)

As the post says, this is about the possibility of moving the launcher for maximized windows only, NOT the return of dodge windows in it's current/recent incarnation.

@ rg4w

I am unable to find the discussion that has been referenced in this thread for some reason.  I will post a URL if I manage to locate it.

---

### Post by x-shaney-x on 2012-03-09
Found it: [https://bugs.launchpad.net/unity/+bug/930148](https://bugs.launchpad.net/unity/+bug/930148)

---

### Post by snkiz on 2012-03-09
@ rg4w Sorry I b*tched and moaned everywhere, read a lot of others b*tching and moaning. It was mostly late at night, its all a blur. I know I thought that line, if I didn't write it, someone did.

---

### Post by x-shaney-x on 2012-03-10
@ EgoGratis

Just wanted to add a hugBeen using it the past couple of days and works great.  I actually much prefer this to the full on dodge :)

---

### Post by EgoGratis on 2012-03-11
I fixed some problems with the script and [added some new features]("http://ubuntuforums.org/showpost.php?p=11757499&postcount=10"). It now detects Unity 3D session and the script runs only in Unity 3D session and user will not get two or more scripts running in the same time if it logs out / logs in Unity 3D session and Hud and Dash won't interferer with the script anymore and all user settings got moved to the top of the script!

---

### Post by snkiz on 2012-03-12
Question, has anyone tried just putting the removed code back into current unity? I'd like to try but I don't have the time right now, planing a big move. I don't really know anything about C but if that works then we could look at simplifying the code so its a little more predictable. Maybe even submit a patch??

---

### Post by EgoGratis on 2012-03-13
I added [autodetection]("http://ubuntuforums.org/showpost.php?p=11761683&postcount=15") feature. 

Average user on default Ubuntu should not have hard time making it work!

---

### Post by x-shaney-x on 2012-03-13
Awesome!  You should give the guys on OMG ubuntu or WebUpd8 a heads up and get this to a wider audience.

It it gets plenty of positive responses (which I'm sure it would), it may even get the attention of the Unity devs and show how much this is wanted by many people.

---

### Post by EgoGratis on 2012-03-13
Personally i think Unity developers should made this decision by them self because they believe it should be there. Because Unity is developed "in-house" and basically windows manager too i don't see much problems if simplified and robust solution would be implemented again. Never hide mode + Hide when at least one window is maximized. 

I can't work without this anymore and because of that i made this script and shared it if anybody finds it useful but in my opinion this mode needs to stay in Unity by default and i hope it will be.

---

### Post by mc4man on 2012-03-13
> **EgoGratis said:**
>  Never hide mode + Hide when at least one window is maximized. 

If they did that as a 3rd option then it would be ok, but then again there seems to be an unwillingness to carry 3 options now.

---

### Post by x-shaney-x on 2012-03-13
They wouldn't need a third option as such.
Could simply have a checkbox next to the "Always show" option:

"Hide when windows are maximized" or something?

---

### Post by mc4man on 2012-03-13
> **x-shaney-x said:**
> They wouldn't need a third option as such.
Could simply have a checkbox next to the "Always show" option:

"Hide when windows are maximized" or something?
That's a 3rd option

While I expect no change for 12.04 if they were ever to change 'never' to 'never except with a maxed window' that would be disappointing, though I really can't imagine them doing that

---

### Post by x-shaney-x on 2012-03-13
Well I think of it more as an extension to one of the options.
2.5 options maybe :)

---

### Post by EgoGratis on 2012-03-14
I added fix/feature for [race condition]("http://ubuntuforums.org/showpost.php?p=11764663&postcount=18").

---

### Post by x-shaney-x on 2012-03-15
I have actually noticed that when using this script, I am getting around 50%-60% CPU usage on all FOUR cores all the time.

When I look at the process list, intellihide (as I called the script) and dbus-daemon appear to be the biggest culprits.

Any idea why?

---

### Post by EgoGratis on 2012-03-15
I did some test and only thing i can think off is you lowered the delay to 0? 

If u changed the delay try with default value of 2 and log out / log in again. If you will still get high CPU values end the "intellihide process" with system monitor and see if ending "intellihide process" drops dbus-daemon CPU usage too or not!

---

### Post by x-shaney-x on 2012-03-15
You got it spot on!

I don't remember changing it and can't imagine why I would have but it was indeed set to "0".
Changed it back to 2 and all is well again :)

---

### Post by EgoGratis on 2012-03-15
I have one feature left to implement that basically works for me already but i have to test it before publishing the code. I will probably test it on Saturday because i don't have time to do it before that. I will probably remove all settings because default "2" is "sane default" and it will avoid problems like this for others that will use the script!

Glad that you solve the problem!

---

### Post by x-shaney-x on 2012-03-15
Aw, you have to at least tell us what that feature is?  :D

---

### Post by EgoGratis on 2012-03-17
I added [Single Screen / Multi Workspaces]("http://ubuntuforums.org/showpost.php?p=11773397&postcount=19") support.

---

### Post by jsevi83 on 2012-03-28
I tried to simplify some things, let me know what you think:

```

#!/bin/bash
# sudo apt-get install wmctrl

ps -ef | grep "$0" | grep -v "grep\|$$\|/bin/sh" | awk '!/awk/ {print $2}' | xargs -r kill

if [ "$DESKTOP_SESSION" != "ubuntu" ]; then exit 0; fi

RACE=$(wmctrl -l | grep -c "DNDCollectionWindow\|launcher\|panel")

while [ "$RACE" -lt "3" ]; do RACE=$(wmctrl -l | grep -c "DNDCollectionWindow\|launcher\|panel"); sleep 1; done

MAX_W=$(wmctrl -lG | awk '{if ($5 > max) { max = $5;}} END {print max}')
MAX_H=$(wmctrl -lG | awk '{if ($6 > max) { max = $6;}} END {print max}')
LAUNCHER=$(wmctrl -lG | grep launcher | awk '{print $5}')
PANEL=$(wmctrl -lG | grep panel | awk '{print $6}')
WIDTH=$(expr $MAX_W - $LAUNCHER)
HEIGHT=$(expr $MAX_H - $PANEL)

while true; do sleep 1

SHOW_LAUNCHER=$(wmctrl -lG | grep -v "Hud\|Dash" | awk -v LAUNCHER=$LAUNCHER -v PANEL=$PANEL '$3==LAUNCHER && $4==PANEL' | grep -c "$WIDTH $HEIGHT")
HIDE_LAUNCHER=$(wmctrl -lG | grep -v "Hud\|Dash" | awk -v PANEL=$PANEL '$3==0 && $4==PANEL' | grep -c "$MAX_W $HEIGHT")

if [ "$SHOW_LAUNCHER" -eq "0" -a "$HIDE_LAUNCHER" -eq "0" ]; then
	CURRENT=$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")
	if [ "$CURRENT" -ne "0" ]; then gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 0; fi
else
	CURRENT=$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")
	if [ "$CURRENT" -ne "1" ]; then gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 1; fi
fi
done
```

---

### Post by EgoGratis on 2012-03-28
I added logic for majority of things i thought could cause problems for users and in the end nothing has to be setup manually by the user and it works because of that i didn't put much thought into it anymore but sure it can be optimized if anybody wants to. 

I thought i could put more autodetection in "while loop" too and user could change settings in real time but i like less operations executed in each interval and i didn't change this. Log out / log in is still required after changes are made because of that.

If i understand correctly and i didn't test much and i assume it works fine:

-Dimension autodetection was added and if this changes in the future Unity the script would still work.
-Some cleanups/optimization that remove unnecessary operations was made.

Great work!

Maybe a note on delay. Changing delay below 2 in my tests didn't make any real difference but setting value too low could create unnecessary problems for users on some hardware.

The "real goal" of this script was to demonstrate to Unity developers why this should be implemented in Unity by default and i hope this will be the final outcome!

---

