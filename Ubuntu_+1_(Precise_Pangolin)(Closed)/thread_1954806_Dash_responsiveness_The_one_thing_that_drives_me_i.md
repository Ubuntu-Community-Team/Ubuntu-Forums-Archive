---
title: "Dash responsiveness: The one thing that drives me insane with Unity"
date: 2012-04-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kaldor on 2012-04-08
This is mainly toward people familiar with Unity (any developers or anyone who happens to know this).

I type fast. I'm a touch typist, and I tend to use a UI "quickly"; fast mouse movements, fast keyboarding, etc. With GNOME Shell, this is absolutely seamless. I love Unity and GNOME Shell for their keyboard-driven features.

Unity is not so efficient. If I invoke the Dash (Super) and type a program name and then press enter, then by the time I hit enter the Dash has only opened and registered a single letter.

For example, I will try to launch Terminal by type "ter" and pressing enter. It goes like this:

1) Press Super
2) Type "ter"
3) Press enter

So, what happens? Nothing. The Dash hasn't popped up yet. If the dash has popped up, it only recognized the r. It's beyond slow.

I have to keep waiting every time I want to launch a program, so I just keep using the keyboard shortcut on the launcher in order to launch it (Super + a number). This is not optimal.

So, my question is this: Will Unity's Dash become as responsive as Shell by the end of the Precise cycle? I keep using Shell simply because I can multitask instantly and not have to wait due to delayed response time.

---

### Post by r-senior on 2012-04-08
Does this sound like the same issue?

[https://bugs.launchpad.net/unity/+bug/966417](https://bugs.launchpad.net/unity/+bug/966417)

I agree that Gnome Shell is very good at this, hit the super key, type a few letters, hit return and even when you think it won't catch up it does.

---

### Post by Basher101 on 2012-04-08
> **r-senior said:**
> Does this sound like the same issue?

[https://bugs.launchpad.net/unity/+bug/966417](https://bugs.launchpad.net/unity/+bug/966417)

I agree that Gnome Shell is very good at this, hit the super key, type a few letters, hit return and even when you think it won't catch up it does.

I think my hardware is overkill for Ubuntu anyways, I myself have not noticed much of a difference in speed and responsiveness of Unity compared to Gnome Shell.

I have AVN for the most basic apps and use the terminal for the rest..guess i do not use the whole potential then

---

### Post by kaldor on 2012-04-08
> **r-senior said:**
> Does this sound like the same issue?

[https://bugs.launchpad.net/unity/+bug/966417](https://bugs.launchpad.net/unity/+bug/966417)

I agree that Gnome Shell is very good at this, hit the super key, type a few letters, hit return and even when you think it won't catch up it does.

It does, except I've always had this issue. I +1'd it anyway though, because it fits well enough.

My hardware is definitely more than enough for this. My 6 core CPU and 8 GB of RAM shouldn't have a delay when I'm trying to launch programs :)

---

### Post by mc4man on 2012-04-08
> **kaldor said:**
> 
I type fast. It goes like this:

1) Press Super
2) Type "ter"
3) Press enter

So, what happens? Nothing. The Dash hasn't popped up yet. .
That sounds different then the bug (which is fix committed & should show up in the next release
You must type really fast, I'd say the Dash here pops up in about 50ms or less (slightly before the super key has returned to up position

---

### Post by bdarb on 2012-04-14
I'm currently using gnome-shell, initially as I was having this same problem with the dash that seems to be fixed with it missing the first few characters, however it still fails to launch the desired program by typing a few letters then hitting enter eg.
<super>fire<enter>
even though Firefox is presented immediately the enter fails to register while dash is still searching for other matches and requires a second enter press to actually launch it. Shell handles this perfectly.
Seems like a small thing but is highly annoying and enough to keep me from giving it a fair shot.

---

### Post by keithpeter on 2012-04-14
> **kaldor said:**
> My hardware is definitely more than enough for this. My 6 core CPU and 8 GB of RAM shouldn't have a delay when I'm trying to launch programs :)

Hello kaldor

What graphics card have you in that monster PC?

I use an nvidia GeForce GT520 with proprietary drivers and I can *just* beat the Dash when typing *really* fast. That's on an old quad core HP workstation.

---

### Post by kansasnoob on 2012-04-14
I find that Unity-2d is much more responsive on my weak (but not old) hardware.

I tend to just blame compiz although that may be total nonsense.

---

### Post by santosh83 on 2012-04-14
> **kansasnoob said:**
> I find that Unity-2d is much more responsive on my weak (but not old) hardware.

I tend to just blame compiz although that may be total nonsense.

After reading this and other threads I'm starting to have misgivings about replacing my old Maverick setup with Precise. If Dash exhibits noticeable latency on kaldor's powerful rig, I wonder if it'll be usable at all on my relatively puny hardware...

Intel Pentium Dual-core E2140 (1.6 GHz) + 988 Mib RAM + 40 Gb HDD
Not even a separate graphics adapter; just the built-in crappy one by Intel.

---

### Post by georgelappies on 2012-04-14
Yeah, this sure happens. Very frustrating having to wait for the UI to catch up when you're trying to launch an app. Also why does it take that long to search the dash anyway. Isn't it indexed?

If I would like to give shell a bash, how would I install that?

---

### Post by bdarb on 2012-04-14
> **georgelappies said:**
> 
If I would like to give shell a bash, how would I install that?

sudo apt-get install gnome-shell

---

### Post by keithpeter on 2012-04-14
Hello All

I think this is slightly more complex than raw processor power or graphics card spec.

Unity2d dash appears *more slowly* than the unity dash on my recycled quad core PC with nvidia, and prop. drivers.

On little Asus EeePC the dash seems only a little bit less responsive than the quad core with unity.

---

### Post by jerrylamos on 2012-04-14
Dash "responsiveness?"  Simple.  There isn't any.  Not a design goal.
Unity is all about "eye candy" so responsiveness and efficiency went out the window.  
Unity is all about fuzzy borders, foggy windows, huge icons.  Not speed.
Classic Microsoft answer that seems to be coming from ubuntu: "Buy a faster computer".
By the way, are you running unity-2D?  Fractionally faster.

Jerry

---

### Post by keithpeter on 2012-04-14
> **jerrylamos said:**
> 
By the way, are you running unity-2D?  Fractionally faster.
Jerry

Hello Jerry and all

That's my point, *you* find unity2d fractionally faster, *I* find unity2d a tad slower on both my test machines (Xeon quad core room heater/Asus EeePC vertebrae saver).

I might ask a question on unity-design about what the 'rate determining step' is for invoking the dash on the two packages.

---

### Post by kaldor on 2012-04-14
> **keithpeter said:**
> Hello Jerry and all

That's my point, *you* find unity2d fractionally faster, *I* find unity2d a tad slower on both my test machines (Xeon quad core room heater/Asus EeePC vertebrae saver).

I might ask a question on unity-design about what the 'rate determining step' is for invoking the dash on the two packages.

Same here. Unity 2d takes up to 5 seconds to load the dash every time. Shell is instant. Unity 3d is better, but not by enough to be non-distracting.

---

### Post by x-shaney-x on 2012-04-14
I do find Dash feels sluggish on my Core i5 hardware but I have just been trying the suggestion mentioned here:

<Super> couple of letters <Enter> and stuff does launch instantly.

---

### Post by JRV on 2012-04-14
The code listed below will put the pre-unity menu system in the upper panel.
It is the Ubuntu icon on the right side.
I find this much faster, and I never need to use the dash.
You will probably want to install alacarte so you can modify the menus.

```

sudo add-apt-repository -y ppa:diesch/testing
sudo apt-get update
sudo apt-get -y install classicmenu-indicator

```

---

### Post by keithpeter on 2012-04-14
@kaldor

> **kaldor said:**
> Same here. Unity 2d takes up to 5 seconds to load the dash every time. Shell is instant. Unity 3d is better, but not by enough to be non-distracting.

5 seconds is worse than the old P3 laptop I installed 12.04 alpha on.

I'm seeing half a second on the recycled xeon box and worst case maybe 2 seconds on Unity2d, on the Netbook. I'm seeing a speed up on repeated invocations as well, perhaps to do with the time taken to query the zeitgeist event tables and populate the home lens?

@x-shaney-x: I agree that the dash search box 'type ahead' kicks in well before the home lens appears, but I can still hit the keys fast enough so the first letter or two end up in the program window and not the dash.

Perhaps Gnome Shell appears instant because it is triggered on the *press* of the Super, not its release after a short time?

@JRV: thanks for that link

---

### Post by jasonsmith01 on 2012-04-14
My 3d dash is super responsive fellas. I can quickly tap the super key and flash the dash it's so quick. ALT-F2 and ALT are also quick, albeit a tiny fraction slower than the dash. 

My PC Specs are nothing special:

Mem - 5.8 GiB
CPU - Intel® Core™ i7 CPU 930 @ 2.80GHz × 8 
GPU - GeForce GTX 460/PCIe/SSE2
64bit. 
With standard Platter type drives. 

It must cache or something because my first dash access after a fresh boot is noticeably slower than everything after. Also hitting ALT for the HUD after a fresh boot the HUD menu appears but I can't enter anything. I need to cycle it and then all is okay.

---

### Post by bdarb on 2012-04-14
This must have been just fixed. After an update yesterday there is no longer an issue with typing a partial name and immediately hitting enter and the program not launching.
However there still is a slight delay in the dash appearing after hitting the super key that isn't present in gnome-shell on the same machine (i7-2600, 8GB ram, SSD) where the program window appears around the same time the dash does and then disappears, but this really isn't much of an issue just not as visually smooth as shell!

---

### Post by kaldor on 2012-04-15
> **keithpeter said:**
> @kaldor



5 seconds is worse than the old P3 laptop I installed 12.04 alpha on.


Note that I am saying "up to". On my desktop PC it's pretty quick (1 second). On my laptop, it's just not usable due to the immense lag; I just use my touchpad instead.

Why is it that Shell can be so seamless, yet Unity is so delayed? It seems that Shell lets you type before the Overview loads, whereas Unity requires the Dash to load before you can type.

When I want to launch a program with GNOME Shell I usually do not even see the overview by the time I've typed and pressed enter.

---

### Post by keithpeter on 2012-04-15
> **kaldor said:**
> Why is it that Shell can be so seamless, yet Unity is so delayed? It seems that Shell lets you type before the Overview loads, whereas Unity requires the Dash to load before you can type.

Hello Kaldor

What I think is happening with Dash is this...

[LIST=1]
[*]You tap the Dash
[*]The 'input handling system' has to monitor length of the tap to see if its a tap or a press and hold
[*]On release of the Super key, the system recognises it as a tap
[*]The home lens window has to be 'built' from the current list of items - try creating a new file then press Dash - it picks up the new file instantly
[*]The system also has to 'direct' keyboard output to the search system - I find Dash will notice my typing before the home lens appears, but I can just beat it so the first letter or two of my typing goes into the current application window
[*]Finally Dash appears with an up to date list of files and registers your search text
[/LIST]

What I think happens with Gnome-Shell is this

[LIST=1]
[*]You tap, or press, or hold the Super key
[*]Nothing happens until you release the Super key so GS knows you are not going to press another key
[*]When you release the Super key, the Activities overlay appears
[*]There is no recently updated information on that first Activities overlay screen, other than the workspaces display which are in memory anyway I think - no database to query, so the Activity overlay can be rendered quickly
[*]The moment you release the Super key, GS can accept input from the keyboard - in 'parallel' with the rendering of the Activity overlay
[/LIST]

In summary: the Dash does more and tells you more but it takes a bit of time to assemble the information.

This could be complete rubbish of course :twisted:

---

