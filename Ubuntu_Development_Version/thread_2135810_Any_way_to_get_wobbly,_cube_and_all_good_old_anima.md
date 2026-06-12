---
title: "Any way to get wobbly, cube and all good old animations back?"
date: 2013-04-15
forum: Ubuntu Development Version
---

### Post by vikkyhacks on 2013-04-15
Is is possible ??? I know this has been asked before, but is there any way to use the compiz-plugins-extra set of the tools in the upcoming versions of the ubuntu. ???? I'am ready to change any desktop environment .... just need to get a stable OS with all burn, mac like minimize maximize, cylindrical workspace switching and wobbly windows all the more ... !!!

---

### Post by grahammechanical on 2013-04-15
> [COLOR=#000000] is there any way to use the compiz-plugins-extra set of the tools in the upcoming versions of the ubuntu.[/COLOR]

Short answer - NO.  I lost wobbly windows halfway through the development cycle of 12.10. Compiz Configuration Settings Manager has been changed to reflect the modifications that are available. I still have wobbly windows on my 12.04 install but nothing like that in 13.04.

Besides, if all the work being done on developing MIR into a display driver is completed up to the standard required and desired we will not be using Compiz as the compositing window manager on desktop Ubuntu when 14.04 is released. Those of us using the development branch may see that change slightly sooner.

And I can tell you this, at the moment no one (developers) is even considering bringing in fancy effects. This is the age of Ubuntu convergence. One user interface across different form factors.

Watch the video discussion.

[http://www.youtube.com/watch?v=Cpqhof7Elgs](http://www.youtube.com/watch?v=Cpqhof7Elgs)

Regards.

---

### Post by monkeybrain2012 on 2013-04-15
Yes, as far as 13.04 is concerned.Just check the boxes in ccsm.

---

### Post by JOHNNYG713 on 2013-04-15
Oh Ya  ! Google is your friend ! [http://askubuntu.com/questions/86977/how-to-correctly-enable-desktop-cube-in-unity-3d](http://askubuntu.com/questions/86977/how-to-correctly-enable-desktop-cube-in-unity-3d)
And As an added precaution, for **when** compiz crashes!!! . . . . . . . .  and it will !  Make a launcher on your desktop, command ' compiz --replace '** Keep it on your desktop** !! This will come in very handy !! :) Be careful ! and as always back up your important data !! before attempting any modifications to 'Ubuntu's', ! Unity desktop ! Remember your playing with something as unstable as Charles Manson on crack ! IT ! can and WILL turn on you, without notice !

---

### Post by mc4man on 2013-04-15
Yes you can have cube & wobbly windows if you wish. I use cube/rotate here, works fine. Hate wobbly windows but just enabled, they work fine
(when enabling these plugins I'd 1st disable the unity plugin in ccsm, make your changes, then re-enable. Compiz may hang for a little when enabling wobblywindows, just wait.

To get these plugins you must install compiz-plugins package & I'd install compizconfig-settings-manager to make the changes.
(there is ongoing work by a few to fix some of the previous unusable plugins..

If for some reason compiz hangs too long after enabling wobbly then just hit power button. If you end up logging out or restarting no big deal. When back just open a terminal > ccsm & re-enable unity plugin.

---

### Post by sudodus on 2013-04-15
> **vikkyhacks said:**
> Is is possible ??? I know this has been asked before, but is there any way to use the compiz-plugins-extra set of the tools in the upcoming versions of the ubuntu. ???? I'am ready to change any desktop environment .... just need to get a stable OS with all burn, mac like minimize maximize, cylindrical workspace switching and wobbly windows all the more ... !!!

Download Knoppix if you want to play or impress on Windows users ;-) Wobbly windows, the cube and more fancy stuff come as default and work beautifully in my old IBM Thinkpad T42 with a Pentium M cpu without pae and Radeon 7500 graphics. Of course these effects work in new computers too.

---

### Post by philinux on 2013-04-15
Wobbly windows activated but i had to tick it twice. First time compiz reset I think and then ccssm came back with option unticked. Ticked it again and instant wobble.

---

### Post by ryanvade on 2013-04-15
I don't understand.  The fancy effects is why l switched  from Windows to Ubuntu.  It is more work for the developers I am sure, but it is a great first impression.

---

### Post by alphacrucis2 on 2013-04-15
Yeah cube and wobbly are still available but the one I miss is the one that you could use to burn windows on close. That was cool but appears there is no one maintaining it so it was dropped. Longer term it looks like compiz is a goner unless someone forks it and converts it into a Wayland compositor. Ubuntu wont use it as they are rewriting unity using qt with a mir compositor.

---

### Post by VinDSL on 2013-04-15
> **grahammechanical said:**
> Short answer - NO.  I lost wobbly windows halfway through the development cycle of 12.10.
Still working, here...  ;)

[http://youtu.be/rdHMs2NTS0g]("http://youtu.be/rdHMs2NTS0g")

---

### Post by VinDSL on 2013-04-15
> **mc4man said:**
> Yes you can have cube & wobbly windows if you wish. I use cube/rotate here, works fine.[...]
Yep, works here, too.

[http://youtu.be/CmbbiZj3EP8](http://youtu.be/CmbbiZj3EP8)

Looks better in real life, of course...

---

### Post by mc4man on 2013-04-15
> **VinDSL said:**
> Yep, works here, too.

[http://youtu.be/CmbbiZj3EP8](http://youtu.be/CmbbiZj3EP8)

Looks better in real life, of course...
What will be nice is if MC Return gets this bug fixed, I use a slightly varied version of the command & dbus workaround that works fine, especially with a custom launcher in plank. (click on launcher icon, all windows of currently focused app are picked from all Ws's
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/774059](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/774059)

He (MC Return) has also taken looking & fixing some off the so-called "unsupported" plugins...

---

### Post by VinDSL on 2013-04-15
> **mc4man said:**
> He (MC Return) has also taken looking & fixing some off the so-called "unsupported" plugins...
Heh!

Compiz Milestone 0.9.10.0 should be interesting!

---

### Post by tad1073 on 2013-04-16
Has anyone gotten "3D Windows" working again?

---

### Post by ventrical on 2013-04-16
> **tad1073 said:**
> Has anyone gotten "3D Windows" working again?

Compiz is working great here. Never better. 3D windows is like a scene from the Matrix :)

Oh well.

---

### Post by ventrical on 2013-04-16
ok.. 3D windows is now back to it's inverted carousell wheel with cylinder turned on. Everything else works ok.

---

### Post by tad1073 on 2013-04-17
> **ventrical said:**
> Compiz is working great here. Never better. 3D windows is like a scene from the Matrix :)

Oh well.

It was like that for me too, WHEN it was working.

---

### Post by vikkyhacks on 2013-04-17
well that sounds a lot promising, has anyone got the cylinder kinda of cube with burn and those extra effects working under the package compiz-extra-plugins .... Those extra set of plugins were removed from 12.10's repo ...

---

### Post by stinkeye on 2013-04-17
> **vikkyhacks said:**
> well that sounds a lot promising, has anyone got the cylinder kinda of cube with burn and those extra effects working under the package compiz-extra-plugins .... Those extra set of plugins were removed from 12.10's repo ...

The cylinder and cube are working in 13.04 after installing the compiz-plugins package.
The cubeaddons plugin is missing in the 12.10 compiz-plugins.

---

### Post by tad1073 on 2013-04-17
I'm also having an issue with multiple desktops. When I set 4 desktops in ccsm I get 8, changing # of desktops in unity tweak tool doesn't work.

---

### Post by mc4man on 2013-04-17
> **tad1073 said:**
> I'm also having an issue with multiple desktops. When I set 4 desktops in ccsm I get 8, changing # of desktops in unity tweak tool doesn't work.

Number of workspaces (virtual size) = #horiz x #vert
There is only 1 Desktop, that setting is irrelevant

---

### Post by tad1073 on 2013-04-17
> **mc4man said:**
> Number of workspaces (virtual size) = #horiz x #vert
There is only 1 Desktop, that setting is irrelevant

That's what I meant.

---

### Post by mc4man on 2013-04-17
> **tad1073 said:**
> That's what I meant.
Unfortunately you lost me here - There are 3 ways to get 4 Ws's.
2x2
1x4
4x1
So for 4 Ws's use one of those 3, typical for cube/rotate is 4 horiz,1 vert.

There are 2 ways to get 8
2x4
4x2

If you are using one of the top 3 & getting 8 that would be interesting though unlikely

---

### Post by tad1073 on 2013-04-17
> **mc4man said:**
> Unfortunately you lost me here - There are 3 ways to get 4 Ws's.
2x2
1x4
4x1
So for 4 Ws's use one of those 3, typical for cube/rotate is 4 horiz,1 vert.

There are 2 ways to get 8
2x4
4x2

If you are using one of the top 3 & getting 8 that would be interesting though unlikely

In ccsm H=4 & V=1 and in unity tweak tool H=4 & V=1 which produces 8 (octogon) virtual desktops but when I set H=1 in unity tweak tool it also sets it to 1 in ccsm. Reason being is I was using key bindings alt+1, alt+2 etc. to switch between work spaces and it produced 1&3 and 2&4 being the same work spaces.

---

