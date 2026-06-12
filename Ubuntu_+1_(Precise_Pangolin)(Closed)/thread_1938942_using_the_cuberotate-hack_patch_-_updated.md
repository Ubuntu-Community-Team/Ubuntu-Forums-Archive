---
title: "using the cuberotate-hack patch - updated"
date: 2012-03-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mc4man on 2012-03-10
Edit:
The flashing has been fixed, hopefully will be in a compiz* upgrade before release. (have tested & am using - works fine
When this bug shows 'fix released' the packages should be available

[https://bugs.launchpad.net/compiz-core/+bug/862430](https://bugs.launchpad.net/compiz-core/+bug/862430)

(- has been merged finally - expect to see after release in compiz-0.9.8


I know there are going to be people wanting to use that hack as posted here
[http://ubuntuforums.org/showpost.php?p=11723425&postcount=77](http://ubuntuforums.org/showpost.php?p=11723425&postcount=77)
And just to again mention - this is a hack not a 100% fix, may work well, may show some issue. 
**Additionally there is no desire to represent this as a real fix, so if sharing please don't do so**.

Edit: have also added a patch for scale to allow limited window group picking from all WS's see post 15, can be built at the same time  - both of these hacks will survive upcoming compiz upgrade to compiz-0.9.7.2 (ABI-20120305), though plugins will need to be rebuilt yet again

I'm very happy with it here, get a flash once & a very rare while, ymmv

There has been an api change so using the bzr source will currently fail
So in light of that an alternate means to build the plugin, anyone feel free to suggest otherwise
(one could build a dependency package to install then remove the ton of dev packages, not today... or build as debian packages

```
sudo apt-get build-dep compiz
```

```
mkdir -p compiz && cd compiz && apt-get source compiz
```

Place the patch from post 77 directly in the compiz folder as seen in screen, adjust red to match source folder

```

cd [COLOR="Red"]compiz-0.9.7.4[/COLOR] && patch -Np0 -i ../cuberotate-hack.patch.txt
```


```
mkdir build && cd build
cmake .. 
make
```

After the make completes 
```
sudo mv /usr/lib/compiz/libcube.so{,-bak}
sudo cp plugins/cube/libcube.so /usr/lib/compiz/
```


Edit:
When compiz (compiz-core, compiz-plugins, ect. ) updates - 
let it update, this will overwrite your modified libcube.so

If the flashing returns then you may be able to use the previous libcube.so that was built, assuming you hung on to it, if the ABI matches

To tell look in synaptic under compiz-core > installed files, see screen 2

Then ck. the ABI of your modded libcube.so,
 Ex. of the current one, for the moment I've left in place, will probably save it elsewhere

```
doug@doug-XPS-M1330:~$ ldd  /home/doug/compiz/compiz-0.9.7.4/build/plugins/cube/libcube.so  |grep libcompiz_core
	libcompiz_core.so.ABI-20120216 => /usr/lib/libcompiz_core.so.ABI-20120216 (0xb764f000)

```
Notice the ABI of libcube.so matches the ABI of what's in screen 2, so they're compatable

If the ABI of  the updated libcompiz_core is different then the one of your previously built libcube.so then you'd would need to get a new source, rebuild ect.

(there may be a different way to find an ABI of an .so, I just use the 1st. that works

---

### Post by ventrical on 2012-03-10
@ mac4man,

Thanks for keeping us apprised of these changes.

---

### Post by durand on 2012-03-11
Does this patch also work when you're using the Desktop Wall instead of the Cube? The flashes are actually driving me completely insane.

Thanks!

---

### Post by mc4man on 2012-03-11
> **durand said:**
> Does this patch also work when you're using the Desktop Wall instead of the Cube? The flashes are actually driving me completely insane.

Thanks!
Not at all.

If you're getting flashing while using wall directly then file a bug on.

If you're getting flashing in the workspace switcher (expo), then I've had a bug on that for 2 months, no progress

---

### Post by durand on 2012-03-11
Ah ok, I do get the flashes with Expo as well :/ I've commented on the relevant bug report for Desktop Wall. Thanks for the heads up!

---

### Post by quequotion on 2012-03-15
> **mc4man said:**
> 
After the make completes 
```
sudo mv /usr/lib/compiz/libcube.so{,-bak}
sudo cp plugins/cube/libcube.so /usr/lib/compiz/
```
There is a better and safer way to do that (no **sudo**)!

If you put the plugin in your home directory, it will override the default one.

**Better, Safer** (and fixed!):```
mkdir -p ~/.compiz-1/plugins
cp plugins/cube/libcube.so ~/.compiz-1/plugins/
```**Restart compiz:** ```
[ALT] + [F2]
compiz --replace
```

This is safer because you don't need to make any changes to the current compiz install.

This is also better, as the file will *not* be overwritten with compiz upgrades.

Caveats:

This file will become outdated, eventually.

Since compiz seems to be going through daily ABI changes, in the future this plugin may become incompatible and may crash compiz.

In that event, or should anything else go wrong, delete the file **~/.compiz-1/plugins/libcube.so**

After that, until the bug gets fixed, rebuild from source as shown by mc4man.

---

### Post by mc4man on 2012-03-15
> **quequotion said:**
> There is a better and safer way to do that (no **sudo**)!

If you put the plugin in your home directory, it will override the default one.

**Better, Safer: **```
mkdir ~/compiz-1 && mkdir ~/compiz-1/plugins
cp plugins/cube/libcube.so ~/compiz-1/plugins/
```[B].

That sounds good, except I'd think more like
```
mkdir -p  ~/.compiz-1/plugins
cp plugins/cube/libcube.so ~/.compiz-1/plugins/
```

I usually just log out in, BwackNinja has an alternate restart command in his post that works well also
```
bash -c 'compiz --replace ccp &'
```

Anyway - how's it working out - I'm fairly pleased other than unfold is a disaster here, not because of the patch, it just is atm

---

### Post by quequotion on 2012-03-15
> **mc4man said:**
> ```
mkdir -p  ~/.compiz-1/plugins
cp plugins/cube/libcube.so ~/.compiz-1/plugins/
``` Yes, that's better and more simple. I didn't know about "-p" :)

> ```
bash -c 'compiz --replace ccp &'
```
This command definitely works, but it's overkill.

"bash" is not necessary, unless you are not using the default shell.
Ubuntu's default shell is bash.

"ccp" is the settings plugin.
Since ages ago, "compiz --replace ccp" has been copypasta'd all over the internet, but as far as I can tell it has not been necessary to manually load this plugin for quite some time.

"&" runs a process in the background, opening the terminal for another command.
This is unnecessary when using [ALT] + [F2]; Unity or Gnome's "Run a command" dialog.

> how's it working out

So far so good.

I haven't tried unfold yet, although I want to use it in place of expose which is also badly broken lately...

[S]I noticed another benefit with the cube/rotate patch:
Some animations, particularly airplane and explode, look better.
Before patching, these animations showed some kind of corruption in which certain sides of the 3d objects they generate would not be textured with the window content or would not be drawn at all.[/S]
Nevermind, still having that problem.

Just how dirty is this hack?

---

### Post by mc4man on 2012-03-15
> Just how dirty is this hack?
BwackNinja  would be the one to comment on that, I've seen no ill or unintended effects so in that regard not bad.

One thing I was 'correcting' about your command was you used compiz-1 instead of .compiz-1, you probably should edit

---

### Post by BwackNinja on 2012-03-15
> **quequotion said:**
> Yes, that's better and more simple. I didn't know about "-p" :)


This command definitely works, but it's overkill.

"bash" is not necessary, unless you are not using the default shell.
Ubuntu's default shell is bash.

"ccp" is the settings plugin.
Since ages ago, "compiz --replace ccp" has been copypasta'd all over the internet, but as far as I can tell it has not been necessary to manually load this plugin for quite some time.

"&" runs a process in the background, opening the terminal for another command.
This is unnecessary when using [ALT] + [F2]; Unity or Gnome's "Run a command" dialog.



So far so good.

I haven't tried unfold yet, although I want to use it in place of expose which is also badly broken lately...

I noticed another benefit with the cube/rotate patch:
Some animations, particularly airplane and explode, look better.
Before patching, these animations showed some kind of corruption in which certain sides of the 3d objects they generate would not be textured with the window content or would not be drawn at all.

Just how dirty is this hack?

First, on the command. For just Alt+F2, just "compiz --replace ccp" is sufficient. On the terminal, I do that so that it double-forks and is no longer tied to the terminal I run it from and I can close that terminal at any time without worrying about that also closing compiz. And I keep ccp because I'm pretty sure I've had problems with it not loading at one time, and its just habit to be safe and a few extra characters to type.


Now, on the lack of cleanliness of this hack. Without the patch, compiz displays the previous workspace's contents (for 1 - 2 frames) when rotating the cube. To mitigate this, I:
- found the place where it draws using the wrong workspace value
- stored the last workspace value when redrawing
- set it up to use the last workspace value instead of the current wrong workspace value at the point where it is done rotating

An interesting thing though is the fact that I say 1 - 2 frames, not just 1 frame. I actually always see 2 frames that were wrong but only end up compensating for 1 in my patch. This works out anyway (making this even worse of a hack) because more than 1 thread is in the draw function at the same time where I do the check and use the last workspace value.

If that made any sense to you, you can see why I have made absolutely no effort and explicitly go against any attempts to upstream a patch like this.

Oh, and while I'm happy that other things are working better for you, I find it hard to take credit for those.

Once I have a good chunk of time to devote to it again, I'll try to see if I can find and fix the actual problem and/or take a look at rotating with a window. Both with the mouse and keyboard ways of doing that don't work well at all >.<



Special thanks to mc4man for making this thread. I haven't even tested this patch on ubuntu, and I always build all of compiz from bzr for myself.

---

### Post by quequotion on 2012-03-15
> **mc4man said:**
> One thing I was 'correcting' about your command was you used compiz-1 instead of .compiz-1, you probably should editOoops! Yes, **.compiz-1** is correct.

> **BwackNinja said:**
> First, on the command. For just Alt+F2, just "compiz --replace ccp" is sufficient. On the terminal, I do that so that it double-forks and is no longer tied to the terminal I run it from and I can close that terminal at any time without worrying about that also closing compiz. And I keep ccp because I'm pretty sure I've had problems with it not loading at one time, and its just habit to be safe and a few extra characters to type. I see. I think there was a time when that plugin had to be loaded manually (like 0.7.x), but I only have trouble with compiz not getting settings when gnome-session fails, in which case a logout/login usually fixes things. Either way, yeah it's safe and your command makes sense on a terminal.

> - found the place where it draws using the wrong workspace value That's good news. At least someone knows where things are going wrong.

> An interesting thing though is the fact that I say 1 - 2 frames, not just 1 frame. I actually always see 2 frames that were wrong but only end up compensating for 1 in my patch. This works out anyway (making this even worse of a hack) because more than 1 thread is in the draw function at the same time where I do the check and use the last workspace value.I'll admit this doesn't entirely make sense to me, but do you mean that you draw the last workspace value for one frame times multiple threads which ends up stamping out the misdrawn workspace for a few frames (how many?) OR that you redraw only half of the affected frames and the others are too fast to see?

> Oh, and while I'm happy that other things are working better for you, I find it hard to take credit for those. Actually, since my post the badly drawn animations have returned. Probably they were looking better because I had restarted compiz manually.
Compiz runs differently when it is started by a user than when it is started by gnome-session.

> Once I have a good chunk of time to devote to it again, I'll try to see if I can find and fix the actual problem and/or take a look at rotating with a window. Both with the mouse and keyboard ways of doing that don't work well at all >.< Yeah, I've been practicing a mouse trick: If you drag a window over the edge of the screen and let go just before the rotation completes you get to the next desktop with half the window on it.

Perhaps you are already on to the same thing, but I think this is related to the rotation flicker.
Maybe it's not just a redrawing bug, because compiz seems to cycle the window order or active/inactive status of windows on rotation.
Somehow the mouse partially loses control of the window if you try to drag it straight across and then it goes back to where it was on the previous desktop. If you keep your grip on it, you can then enjoy dragging around a window on a different desktop than the mouse....
That would be neat if it were input redirection and not a bug.

Thanks for working on this!

I know things are going on in bzr, but lately it seems like the compiz cube has been left out of development.

---

### Post by mc4man on 2012-03-15
Here is another occurrence of a similar effect though this started not that long ago in expo. Whether there is any tie in the the issues of rotate/cube no idea other than possibly there's some flaw in rendering that now affects expo most, but not all, the time.

Only mentioning because i'd hope, (expect) the expo problem is addressed in the near future, this bug shows no activity but there could be reasons for, the least of which is that it's bugged elsewhere

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931641](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/931641)

(I attached a vd which was interesting because the default recordmydesktop option of recording in a frame 'fixed' the flashing..

---

### Post by BwackNinja on 2012-03-16
It is definitely more than a drawing bug, that's what makes this a mere hack and not even a road to a fix. The best it does is make the experience a little more bearable and help me learn how those parts of compiz work.

About moving a window with the mouse, you'll see that after rotating with the window, the window moves back to its original position (because of lazy moving and having its position updated when it shouldn't be). If you put the window all the way at the edge of the screen and then rotate with it, you'll see that there is only a small space between where the window is and where it should be, as opposed to when the window is farther from that edge to start with.

The issues are definitely in the workspace switching code, which also moves all the windows (probably so input works properly). It is all likely a problem where there are differences between where X thinks the window is and where compiz thinks the window is, probably a place where servergeometry is used instead of geometry when updating the position of the window.

Thinking about it that way, the fix is probably very simple, but it'll still be a pain to find out where it goes. I'll probably have a good chance to work on it this upcoming week.

---

### Post by mc4man on 2012-03-16
While somewhat off the track of this thread - 
it looks like in 12.10 &+ there will be some decent changes to workspace switching, spread ect. Some of it seems quite interesting, certainly wonder if it will translate from 2x2 to other configs 

[https://docs.google.com/document/d/1EdrlUuZvA9P8-BZufUU2KlHGjg49p9UacF4MCL0U5uA/edit#heading=h.ft27uqmvhjmp](https://docs.google.com/document/d/1EdrlUuZvA9P8-BZufUU2KlHGjg49p9UacF4MCL0U5uA/edit#heading=h.ft27uqmvhjmp)

Top of the doc
[https://docs.google.com/document/d/1EdrlUuZvA9P8-BZufUU2KlHGjg49p9UacF4MCL0U5uA/edit](https://docs.google.com/document/d/1EdrlUuZvA9P8-BZufUU2KlHGjg49p9UacF4MCL0U5uA/edit)

---

### Post by mc4man on 2012-03-21
A 'use at you own risk, ymmv' add on. 
If there is personal  value to having a key binding to initiate 'window picker for window group' from all WS's then when building the cube plugin one can also patch & build a scale plugin that allows all WS's

The binding can't be set directly in ccsm, instead uses a command & dbus

If inclined then dl the attached patch, place in build folder like with the cuberotate patch & patch with (this patch is good for the current compiz source - compiz-0.9.7.0~bzr3035

 ```
patch -Np0 -i ../fix_scale.txt
```

After building replace the current scale.so or use ~/.compiz-1/plugins as an override (I'm currently using that method, screen 

To set up - 
Open ccsm & if not already enable 'commands' & 'dbus' plugins. Expect compiz to stuff up a bit, if needed re-start your session

Once cool in ccsm - in the commands plugin choose a slot & paste this command in, note this is one very long command, get it all.
```
dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/scale/screen0/initiate_all_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'` string:"match" string:$(xprop -id `xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" | awk '{print $5}'` | grep "WM_CLASS" | cut -d\" -f4 | awk '{print "class=" $1 }')
```

Then under the 'key' tab choose the command # where the above was entered & set a binding, I'm currently using Shift+Alt+p

Use the binding when focus is on a window group wished to pull - I'd refrain from using the binding while focus is on the Desktop, unexpected results may occur

Enabling scale addons & the text plugin will allow a window title overlay in spread, adjusted in the scale addons plugin  -  example here, 4 nautilus from 4 WS's
[http://ubuntuforums.org/showpost.php?p=11773699&postcount=12](http://ubuntuforums.org/showpost.php?p=11773699&postcount=12)

---

### Post by BwackNinja on 2012-04-05
Apparently this will finally be fixed for real.

All will be good once an iteration of this gets through:
[https://code.launchpad.net/~smspillaz/compiz-core/compiz-core.work_923683/+merge/100796](https://code.launchpad.net/~smspillaz/compiz-core/compiz-core.work_923683/+merge/100796)

It was stated here that it fixes the issue:
[https://bugs.launchpad.net/compiz-core/+bug/862430](https://bugs.launchpad.net/compiz-core/+bug/862430)

---

### Post by BwackNinja on 2012-04-11
[https://code.launchpad.net/~smspillaz/compiz-core/compiz-core.work_923683/+merge/101483](https://code.launchpad.net/~smspillaz/compiz-core/compiz-core.work_923683/+merge/101483)

The real fix for these issues is currently resubmitted as this merge proposal.

I just tried it, and it works perfectly, fixing all the issues we've been having. No more flickering and we can drag windows between workspaces without an issues. Yay!!!

---

### Post by mc4man on 2012-04-11
> **BwackNinja said:**
> [https://code.launchpad.net/~smspillaz/compiz-core/compiz-core.work_923683/+merge/101483](https://code.launchpad.net/~smspillaz/compiz-core/compiz-core.work_923683/+merge/101483)

The real fix for these issues is currently resubmitted as this merge proposal.

I just tried it, and it works perfectly, fixing all the issues we've been having. No more flickering and we can drag windows between workspaces without an issues. Yay!!!
That's good to hear - many users will be quite pleased 
(the next unity & compiz upgrades should be interesting, some decent fixes I've seen though some new breaks that hopefully are fixed before the upgrades release.

---

### Post by ventrical on 2012-04-11
> **BwackNinja said:**
> [https://code.launchpad.net/~smspillaz/compiz-core/compiz-core.work_923683/+merge/101483]("https://code.launchpad.net/%7Esmspillaz/compiz-core/compiz-core.work_923683/+merge/101483")

The real fix for these issues is currently resubmitted as this merge proposal.

I just tried it, and it works perfectly, fixing all the issues we've been having. No more flickering and we can drag windows between workspaces without an issues. Yay!!!


Nice work you guys !

---

### Post by mc4man on 2012-04-21
The fix for this, flashing in expo & one other thing reached a nice point some time ago.
There were a few obscure issues, but instead of merging & dealing with those ect. after, it's just 'progressed' on & on (an add. 25 commits.

The current state is a bit interesting, bottom line is will not show in 12.04 release.
Whether it makes SRU-O who knows, hope so.

Current branch -  latest comments about 1/2 way down
[https://code.launchpad.net/~smspillaz/compiz-core/compiz-core.work_923683/+merge/102504](https://code.launchpad.net/~smspillaz/compiz-core/compiz-core.work_923683/+merge/102504)

Maybe next week this will get to where it can be merged & move on, maybe not

re-edit: finally merged, should show up in SRU-0 some time after release...

---

