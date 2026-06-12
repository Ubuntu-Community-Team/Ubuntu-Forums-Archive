---
title: "Scale effect stopped working"
date: 2012-03-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by geovino on 2012-03-17
In 12.04 I set up Scale effect in Compiz, it worked until I rebooted and then it stopped working. I guess since is a beta it is expected.

---

### Post by neu5eeCh on 2012-03-17
> **geovino said:**
> In 12.04 I set up Scale effect in Compiz, it worked until I rebooted and then it stopped working. I guess since is a beta it is expected.

Still working on *my* system. I bound this function to the middle mouse button of my wireless mouse. Have you updated?

---

### Post by geovino on 2012-03-17
> **VTPoet said:**
> Still working on *my* system. I bound this function to the middle mouse button of my wireless mouse. Have you updated?

yes I updated. Another thing... why is the boot up so slow? it's been like that for that past two versions!

---

### Post by neu5eeCh on 2012-03-17
> **geovino said:**
> yes I updated. Another thing... why is the boot up so slow? it's been like that for that past two versions!

Boot up time hasn't changed here - so far so good. Sounds like these troubles might be related to your system?

---

### Post by geovino on 2012-03-17
> **VTPoet said:**
> Boot up time hasn't changed her - so far so good. Sounds like these troubles might be related to your system?

I've got Fedora LXDE on another hdd on the same pc and it's faster. And Mint 12 on my main pc and its a bit faster, but becasue its based on Ubuntu its about the same.

---

### Post by x-shaney-x on 2012-03-17
Scale has been a bit iffy for me ever since I installed the beta.

I have it bound to the bottom-right screen corner and sometimes it works and other times it doesn't.

---

### Post by neu5eeCh on 2012-03-17
> **x-shaney-x said:**
> Scale has been a bit iffy for me ever since I installed the beta.

I have it bound to the bottom-right screen corner and sometimes it works and other times it doesn't.

I bound workspace overview (expo) to the bottom right (using Ubuntu Tweak). I haven't been able to bind scale to the top right. Something is buggy somewhere -- either Ubuntu Tweak or Unity. I've had no problems with scale when bound to the mouse.

---

### Post by stinkeye on 2012-03-17
For me it no longer picks up all windows in the same group if they are on another workspace.
"Initiate for all windows" only shows windows for the current desktop.

---

### Post by mc4man on 2012-03-17
> **stinkeye said:**
> For me it no longer picks up all windows in the same group if they are on another workspace.
"Initiate for all windows" only shows windows for the current desktop.

As far as a user set binding that's be broken for some time, now that it's also been intentionally removed from left click on launcher icon the only way it's seen in any form is from the alt-tab switcher 
(& the other switchers excluding scale

Requests (bugs) to fix 'window picker for window group' (initiate_all) have gotten nowhere

---

### Post by stinkeye on 2012-03-17
> **mc4man said:**
> As far as a user set binding that's be broken for some time, now that it's also been intentionally removed from left click on launcher icon the only way it's seen in any form is from the alt-tab switcher 
(& the other switchers excluding scale

Requests (bugs) to fix 'window picker for window group' (initiate_all) have gotten nowhere
I'm starting to regret Canonical ever got their hands on compiz.
Seems to me they're taking away a lot of the functions I like and use on the desktop
for their own multiplatform purposes.

---

### Post by x-shaney-x on 2012-03-17
Well they are working on more unity specific switching/task managing features which will no doubt depend on compiz: [https://docs.google.com/document/d/1EdrlUuZvA9P8-BZufUU2KlHGjg49p9UacF4MCL0U5uA/edit?pli=1&pli=1](https://docs.google.com/document/d/1EdrlUuZvA9P8-BZufUU2KlHGjg49p9UacF4MCL0U5uA/edit?pli=1&pli=1)

Not sure where this will head.
Since most distros are shipping either KDE with Kwin or Gnome Shell with Mutter, where does the future lie for compiz?

I imagine unity and compiz are going to become more and more entwined as time goes on so many of the plugins may well be ripped out in order to make it a more stable and streamlined unity window manager.

---

### Post by mc4man on 2012-03-17
Just to see I've restored window picker for window group all ws's in 0.9.7 initiated thru a dbus command & key binding 
(also involved building scale.cpp as the current one won't allow initiate_all in scale

Will have to see it breaks anything or unintended effects, if not will add to the cuberotate-hack thread.

As example set scale addons to display a large overlay from all, I spread one naut window from each of 4 Ws's

Also interesting is that the newish 'unfocused' element of light-themes also works in spread, with a modded ambiance is fairly clear - when mousing over, (focused), the highlights  are shown, in unfocused windows they are dimmed

---

### Post by neu5eeCh on 2012-03-17
> **mc4man said:**
>  Also interesting is that the newish 'unfocused' element of light-themes also works in spread, with a modded ambiance is fairly clear - when mousing over, (focused), the highlights  are shown, in unfocused windows they are dimmed

mc4man, what theme are you using that you get the black sidebar in Nautilus? I'm using Ambience, but the sidebar is light grey.

---

### Post by mc4man on 2012-03-17
> **VTPoet said:**
> mc4man, what theme are you using that you get the black sidebar in Nautilus? I'm using Ambience, but the sidebar is light grey.

Back in 11.10 warrioring64 put together a basic dark sidebar variation of ambiance
I liked it with a few differences like having selected go from light to dark (selected_fg), & a few other diff's

Since then I've been using & modifying in 12.04 which has been a bit of a challenge with all the gtk+3 changes & subsequent light-themes changes, some nautilus changes, especially for someone who knows nothing about theming or  how to use gimp or inkscape beyond just some basic's & trial & error

Atm I'm pausing due to currently using my son's laptop which has an awful screen, colors look different depending on angle, screen placement ect. (hope to get mine back soon.
And the easiest part of inkscape is currently broken (extensions

So atm I'm about here, using Faenza for places icons, something in that neighborhood for selected_bg, (currently :#D3B37D, not sure yet), selected_fg_color:#3c3b37" & then will go about recoloring all the action & close button icons ect. to the extent I can figure this stuff out...

I also didn't like the arrow button placement in naut, & because I use Location view alot put back the up (parent) arrow

A casualty of the 'light context menus' has affected a r. click on sidebar item, which prior would be dark, don't know yet if I can workaround..

---

### Post by snkiz on 2012-03-18
Scale is broken spectacularly in precise. My hot corner (bottom left) doesn't work at all. App scaling (via the launcher) doesn't pick up minimised windows, doesn't pickup windows on other workspaces and triggers show desktop for some reason. I've filed a couple bugs, me 2'd a few. been like this since unity 5.2. I simply don't see them fixing it any time soon, Canonical is too busy mucking with "new features" to fix the old ones, that they screwed up in the first place.

---

### Post by neu5eeCh on 2012-03-18
> **snkiz said:**
> Scale is broken spectacularly in precise. My hot corner (bottom left) doesn't work at all. App scaling (via the launcher) doesn't pick up minimised windows, doesn't pickup windows on other workspaces and triggers show desktop for some reason. I've filed a couple bugs, me 2'd a few. been like this since unity 5.2. I simply don't see them fixing it any time soon, Canonical is too busy mucking with "new features" to fix the old ones, that they screwed up in the first place.

You should provide links to the bugs so that we can second them.

---

### Post by geovino on 2012-03-18
the scale worked this morning for a while and then stopped after some updates. But you can get the same effect with this hot keys:

Windows or super key + W

---

### Post by snkiz on 2012-03-18
[https://bugs.launchpad.net/bugs/933776]("https://bugs.launchpad.net/bugs/933776")

Can't find the other ones right now

---

### Post by stinkeye on 2012-03-18
> **geovino said:**
> the scale worked this morning for a while and then stopped after some updates. But you can get the same effect with this hot keys:

Windows or super key + W
Doesn't show windows on all workspaces.

Disabled the unity switcher and went back to the old ring switcher.
At least shows all windows and can set it to a mouse button.

---

