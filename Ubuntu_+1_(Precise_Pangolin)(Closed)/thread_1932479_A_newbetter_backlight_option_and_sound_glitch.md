---
title: "A new/better backlight option and sound glitch"
date: 2012-02-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by t1497f35 on 2012-02-27
Hi,
Where should I ask to add a backlight mode that only draws the background rectangle for launched apps. Currently the background rectangle is drawn no matter what and no option to disable it. Btw, what I'm asking is enabled on win7 by default and I find this backlight mode/option superior as it allows me to detect a lot easier which apps are launched and which ones are not (and please don't start the "it's not windows" bs).

In sound settings despite checking "alter volume - mute" it still plays a sound when logging out, feature or bug?

---

### Post by snkiz on 2012-02-27
ccsm >> unity plugin >> experimental tab. I believe you'll find the option there, at least until Canonical rips out the code.

---

### Post by t1497f35 on 2012-02-27
Thanks, neither ccsm nor myunity provide any option to disable (i.e. to not draw) the background rectangle for non-launched apps.

---

### Post by snkiz on 2012-02-27
> **t1497f35 said:**
> Thanks, neither ccsm nor myunity provides an option to disable the background rectangle for non-launched apps.

Oh you mean turn it off completely? I misunderstood. There are several options there however that better define running/non-running apps. Or you could go with the nuclear option, and switch out the background images. They aren't hard coded yet, unlike the BFB.

---

### Post by t1497f35 on 2012-02-27
Here's what I mean (though I think I already made myself clear):
a) Don't draw the background rectangle for non-running apps
b) Draw the background rectangle for running apps
nothing new, if you use win7 you know what I mean.

If you think there's such an option please be more specific or post a screenshot. The nuclear option - disabling the icons - doesn't solve the problem but only worsens it. It's not about icons/images, it's about the background rectangle.

---

### Post by snkiz on 2012-02-27
Ya no don't think you can do that. But the launcher uses several images to draw for different sates. Change the ones you want changed. They can be found in /usr/share/unity/5. If you can't get what you want there, I know it can be done with the 2-d launcher, change a few images hack some qml files. Volia you can do pretty much whatever you want. It can still be used with compiz as well. Here's mine, not what your looking for, but certainly not stock.

---

### Post by t1497f35 on 2012-02-27
To achieve what I want I changed the source code of IconRenderer::RenderIcon(..) in plugins/unityshell/src/IconRenderer.cpp

The code that always draws the background rectangle is called "draw overlay shine", there's no GUI option to configure how it should run, so I changed the code so that it gets drawn only for running apps and here's what I get (see screenshot), as you can see 2 apps are running (one is minimized), same look as in window$ 7.

Also, there's now only one side arrow - only for the currently selected app.

I used Unity 5.4 from Ubuntu 12.04, I'll see if I can do the same for my Ubuntu 11.10 and use my own compiled version from now on since I'm skeptical about upstream approval.

---

### Post by snkiz on 2012-02-28
I was skeptical, (hate the backlight, it just looks bad with monochromatic icons.) But that actually looks pretty good. How does it handle multiple windows of the same app? Does it still show the "pips" on the left side? 
Seeing as you have some C skills, I'd suggest patching it into the options and filing a bug with the patch. The only thing set in stone about Unity is the attitude that everything they do is perfect, until its not. The worst they could say is "won't fix" And even then someone could stumble across it latter and think it is a good idea.

---

### Post by t1497f35 on 2012-02-28
When more than 1 window of the same app is running I'll probably draw a tiny number (e.g. to the bottom right, not to interfere with the icon's progress bar when it's displayed etc) corresponding to the number of windows of the app. From this perspective we can be slightly better than window$ 7 cause window$ only says there are > 1 windows but doesn't say how many.

I've slightly refined my code/view since there are 3 main types of icons: not running, running and the one which is active.

The active one is now **clearly** highlighted (which you can see on the screenshot how firefox is in front and its icon is highlighted most), hence now we don't need a side arrow anymore.

The rest of the running apps are highlighted less to be clearly distinct from the active one.

The non-running apps show just their icons without any highlight at all which also makes their view clearly distinct from all the others.

The current Ubuntu Unity highlight/backlight model is a total mess since it's basically a carousel of random colors based on the icon's colors (and not on its running/active state) - this approach has little to nothing to do with user's needs. Just pointless bling.

I appended a short video whose quality is slightly glitchy (probably the recording tool is slightly broken, no wonder since Ubuntu is in alpha) but in reality there were no visual glitches.

---

### Post by snkiz on 2012-02-28
Hmm.. so you made the backlight a single colour? and the BFB isn't pulling the colour from your background (That bit I know they won't like, see: [bug 938916]("https://bugs.launchpad.net/bugs/938916").) 
I like the standard background colour, maybe read from the selection colour and use a shade of that instead though. (little bling but still functional.) Also, the fade for inactive running apps is a nice touch, it is however very dull. I'd suggest you use a hilight border for the active apps instead. (from selection colour or from icon colour.) Its a small thing but appearances are important, and you'd like to see them adopt this. (At least I do now. ;-) )
As for your idea about the numbers, I see where your going, just not sure it will work. A launcher displaying other information, (progress bar, number of updates, mail count, etc.) isn't going to leave a lot a room for a number representing the number of windows for an app, especially if its already showing a couple things. The "pips" solved this, and if I remember correctly they only show a maximum of three pips. (Seems to be enough for most cases.) Since you've eliminated the need for arrows entirely, might I suggest continuing to use the "pips" but on the right side of the launcher. Where they'd be more visible.

All in all good work! don't suffer in silence. I'm tempted to ask you to put dodge back in! :lolflag:

---

### Post by t1497f35 on 2012-02-28
You're right, that was slightly dull, does it look better now?

The back-light of active window's icon is now based on the icon's image colors, hence on the screenshot because Firefox's window is the active one and since its icon is reddish - the back-light is also reddish.

The running, non-active icons have edges and a slight shine at the top of the icon.

In fact, we're emulating almost 100% the Windows 7 back-lighting model, have a look at both screenshots, so I'll probably call it "Windows 7 back-light style" or so and suggest it upstream. But not for 12.04 since it's LTS and they don't want changes.

As to multiple windows of the same app, I'm thinking about it and I guess the number won't interfere, we'll see. I'm also thinking about icon mouse-hover (mouse over/out) effect, since it's found on windows 7 and I find it handy.

---

### Post by snkiz on 2012-02-28
Ya that's pretty good. I see the similarity with win7, thou this one is nicer :D. The BFB needs to keep a background I think, makes it stupid obvious that's the "start" button. Besides they'd never go for removing it upstream. The more I think about it, the more I dislike pulling colours from the icon. You never really know what your going to get so it causes unnecessary distraction. pulling from the background like the BFB does or the selection  colour is consistent, regardless of icon colours. 

A pop up for number of windows? Now there is a thought. I do you one better. Put it in the tooltip for the icon. So it would show *"window name (n)"* Its clean and gets out of the way til you need that info.

---

### Post by t1497f35 on 2012-02-28
The BFB look is a side effect, gonna get fixed.

Yep, pulling colors from the icon doesn't please anyone and in cases when it's totally red or other stark color (like in Firefox's case) it's also slightly annoying/distracting, probably that's why my former code used a single color, like windows 7 btw.

Also, in Unity the mount icons (/etc/fstab) are not listed in alphabetical order which isn't good, it also means that (often) between reboots their location is reshuffled, gonna try to fix that too.

---

### Post by snkiz on 2012-02-28
Be careful with the background colour, I'd hate to see the launcher "totaly" emulate windows, where's the fun in that? We're supposed to strive to be better. 
I think if I'm not mistaken the mounts show in the order they were mounted in. Maybe not so good for your situation, (You appear to be mounting other partitions so they are *always* there.) But alphabetical wouldn't work for removable drives. You'd have drives popping up in the middle of the stack. Keep in mind alphabetical works in windows because they are named so. eg; C:/, D:/, etc.

---

### Post by t1497f35 on 2012-02-28
Yes my partitions are always there, since, for example, I'd have to remember to mount the partition manually before listening to music or starting downloading a torrent since I have 2TB and the partitions serve for different purposes.

Of course alphabetical order would work, there's nothing wrong with "drives popping up in the middle of the stack", from a programmer's point of view it's not rocket science. And I don't mean C:, D:, I mean their labels, like in my case, "movies", "docs", "torrents", "music".

EDIT: have a look at the screenshot, the left vertical pane, how the drives are (always) listed in alphabetical order.

---

### Post by snkiz on 2012-02-28
Its a matter of opinion I guess, I use removables a lot. Not knowing where they will pop up would drive me nuts. A fair compromise would be to show fstab drives alphabetically and mtab drives **after** in the order they are mounted. That does sound complex however.

On a side note, why are you manually mounting data partitions such as those? you could permanently map them anywhere you want and simlink in your corresponding folders in your home dir. I have samba shares I do that with, saves all kinds of headaches with gfvs. My system considers them just another part of the local file system.

---

### Post by t1497f35 on 2012-02-28
They _are_ permanently mounted, through /etc/fstab. But I don't auto-mount all of them (like the partitions where window$ is installed), just the ones I use most. And a programmer typically doesn't use fstab/mtab to detected mounted/unmounted partitions, but a higher level API, such as glib.

---

### Post by snkiz on 2012-02-28
> **t1497f35 said:**
> They _are_ permanently mounted, through /etc/fstab. But I don't auto-mount all of them (like the partitions where window$ is installed), just the ones I use most. And a programmer typically doesn't use fstab/mtab to detected mounted/unmounted partitions, but a higher level API, such as glib.

I see, different strokes i guess. Every dual boot I've setup I auto mount all the win drives too, just to get rid of those icons. They take up space, (witch there is precious little of at the default launcher size.) especially if you rarely use them.

edit:
In code yes you wouldn't use fstab/mtab. However that's how the system mounts permanent vs. removable drives. I don't know how you would do it in code, I'm not there yet.

---

### Post by t1497f35 on 2012-02-29
Is this the way you wanted the BFB to look like? (i.e. it has its own background which changes according to overall color).

See the 3 screenshots with different wallpaper.

---

### Post by t1497f35 on 2012-02-29
Here's a video with Unity icons mouse over/out effects, the glitchy video is because of the recording tool, in reality there's glitches.

---

### Post by snkiz on 2012-03-01
That's really nice, I couldn't tell if you switched the icon background to pull from the selected colour or from the icon colour. IMO the former would be better. The BFB doesn't look bad either. I didn't like that change when Canonical did it because I'm just using border hilight and it looks stupid. But like this it works. Seems unique enough that they might actualy accept it, still says ubuntu to me :D Now, about dodge....

---

### Post by t1497f35 on 2012-03-01
The BFB background is based upon the desktop wallpaper average color (when you change the wallpaper it changes the bg color too).

What dodge?

---

### Post by snkiz on 2012-03-01
I know about the BFB i ment the app icons. sorry for the confusion. 

Doge? that's the killer feature that unity had, and Canonical decided to remove entirely instead of just disabling it because "new" users didn't get it in the first 5 seconds. It made the launcher hide only when a window covered it. Many people are upset. There is a post somewhere on here that has the revision number where it was ripped out. I looked at it, but its beyond me to try and patch it back in.

---

### Post by t1497f35 on 2012-03-01
I see. I'll have a look at Unity 5.6 as it lands (within the next few days) to check if the "dodge" code itself was removed or just the option, if the former then I'm not even gonna try.

---

### Post by snkiz on 2012-03-01
> **t1497f35 said:**
> I see. I'll have a look at Unity 5.6 as it lands (within the next few days) to check if the "dodge" code itself was removed or just the option, if the former then I'm not even gonna try.

No its totally gone, that's why people are so upset. I'm preparing to do a big move, I'll be offline for awhile, that's why I haven't tried. I couldn't possibly maintain it right now. Its also the reason i switched to unity 2D, dodge is still there.

---

