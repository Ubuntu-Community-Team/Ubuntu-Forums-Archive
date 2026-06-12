---
title: "With Ambiance theme - right click on desktop gives this."
date: 2012-02-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by philinux on 2012-02-19
Is this a bug or have I missed a thread on it. Black text on light grey background is just not in keeping with rest of theme. Firefox menu pull downs are white text on dark grey. Nice. And awesome bar gets the light grey and orange highlight too yuk.

And the orange highlight is not too nice.

---

### Post by mc4man on 2012-02-19
Been going on for some time now, context & sub menus have light background
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895)

---

### Post by philinux on 2012-02-19
> **mc4man said:**
> Been going on for some time now, context & sub menus have light background
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895)

Many thanks. I thought I'd seen something about it way back.

---

### Post by quequotion on 2012-02-19
I was looking into the issue discussed [here](http://ubuntuforums.org/showthread.php?p=11701055#post11701055) as I am also having it, but I decided this needs a new thread.

In Nautilus's "list" view the backround is blank.
Not blank as in filled with the default background color, but actually blank and 100% white.
This used to have alternating bands of light and dark backround colors for each line.

As for the menus, those accesible from the Unity launcher and the indicators are all Ambiance themed, but their submenus are Radiance themed.
As mentioned in the thread above, right click menus (either on the desktop or anywhere else) are also Radiance themed.

I have this feeling there was something else I wanted to add to this list but I can't remember it.
I may come back and add more later.

---

### Post by prusswan on 2012-02-19
can you put up a screenshot? I only see that the bottom panel in gedit is obviously wrong, and the application labels in the bottom panel having dark on dark

---

### Post by fjgaude on 2012-02-19
Well, soon, the time for cosmetic bug fixes will be taking place. Right now the crash-type bugs are in focus. All the subtle things will likely be where folks want them to be at release time.

Remember we are still in Alpha testing.

---

### Post by cariboo on 2012-02-19
merged similar threads.

---

### Post by philinux on 2012-02-28
Ok so a guy on IRC said the ambiance theme has changed and now right click on desktop and other places gives a light theme appearance.

I like ambiance on 11.10 so is there a theme somewhere that is similar. I'm not keen on these light menus.

---

### Post by mc4man on 2012-02-28
> **philinux said:**
> Ok so a guy on IRC said the ambiance theme has changed and now right click on desktop and other places gives a light theme appearance.

I like ambiance on 11.10 so is there a theme somewhere that is similar. I'm not keen on these light menus.

In that bug report someone implied that was the case, (comments 4 & 7) but it makes no sense to have have some dark, some light. Also comment 18 sort of confirms that this is a bug, not intended behavior, (I guess ?

---

### Post by philinux on 2012-02-28
> **mc4man said:**
> In that bug report someone implied that was the case, (comments 4 & 7) but it makes no sense to have have some dark, some light. Also comment 18 sort of confirms that this is a bug, not intended behavior, (I guess ?

I agree. It's weird.

---

### Post by kaldor on 2012-02-28
> **philinux said:**
> Ok so a guy on IRC said the ambiance theme has changed and now right click on desktop and other places gives a light theme appearance.

Seriously? It looks so out of place.

---

### Post by philinux on 2012-02-28
> **kaldor said:**
> Seriously? It looks so out of place.

Yep on #ubuntu+1 can't remember who it could be a user called daekdroom or similar.

But Yeh he said thats how its supposed to be. I need a new theme.

---

### Post by kaldor on 2012-02-28
I guess you could just copy over the 11.10 Ambiance theme, or find where to change the menus.

---

### Post by ppd on 2012-02-28
This is a bug in unity according to
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895)

---

### Post by philinux on 2012-02-29
> **ppd said:**
> This is a bug in unity according to
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895)

I subscribed to that bug a while back. You'd think it would be an easy fix but who knows.

---

### Post by ppd on 2012-02-29
Yeah, they have tons of bugs to iron out with all the changing and tweaking of unity + compiz.

Developing and maintaining a full blown desktop environment is obviously labor-intensive.

---

### Post by neu5eeCh on 2012-03-15
I cannot, for the life of me, get any real cohesiveness in themes. I use the Ambience Theme, but I notice that some menus are dark with white fonts, and some are white with dark fonts, etc...

For instance, my Firefox menus are dark grey with a white font. However, if I right click anywhere on the browser window, the menu is white with grey font. Also, if I click on the bookmark button (firefox toolbar) the menu is white. In Libre Office, my menus are white with black font. The [classic menu]("http://www.webupd8.org/2011/06/use-classic-menu-in-unity-classicmenu.html") is dark grey with white font.

So, am I dong something wrong or is this a bug?

---

### Post by grahammechanical on 2012-03-15
I do not notice this because I have taken to using the Radiance theme but it is there when I switch to Ambience. I would not call it a bug.

Have you noticed that Firefox is more integrated into Unity than Libreoffice?

The Firefox application menus go into the top panel but not the LIbreoffice application menus. The HUD seems to know about Firefox but not about Libreoffice.

Perhaps Libreoffice is holding on to its identity harder than Firefox. I think that this will happen to any program/application that keeps its application menus in a panel in the window and not let them be put in the screen top panel.

Regards.

---

### Post by neu5eeCh on 2012-03-15
> **grahammechanical said:**
>  Have you noticed that Firefox is more integrated into Unity than Libreoffice?

More, yes, but not consistently. If I right click anywhere on the FF browser window, I get a white menu. If I use the bookmark drop-down button, I also get a white menu. It seems that any menu that is not, explicitly, a "Unity Menu", doesn't mesh with the system theme? Are you sure this isn't a bug?

---

### Post by mc4man on 2012-03-15
The light menu coming from light-elements & dark menu from dark-elements is a change in ambiance that is intentional & for the most part is working as intended, there are a few areas where not quite right
(mainly with gtk2 apps & some in window menus

---

### Post by neu5eeCh on 2012-03-15
> **mc4man said:**
> The light menu coming from light-elements & dark menu from dark-elements is a change in ambiance that is intentional & for the most part is working as intended, there are a few areas where not quite right
(mainly with gtk2 apps & some in window menus

OK. That's really weird though. I don't like it, but then I suppose I can always change the theme. (And what do you mean by "light elements"?)

---

### Post by mc4man on 2012-03-15
Well when you open a context menu from inside of nautilus then that's from a light-element, from the appmenu or app indicator that's a dark-element.
Obviously this isn't a dynamic deal so all app windows fields would be treated as 'light'
There are issues with some menus from inside apps that should be dark but aren't, synaptic is a clear example.

When it comes to apps where one disables the global then it's 50 - 50. some use dark, some light. 
(I've found all the 'in window menus' here that dropdown light all use something from gtkrc where all those that dropdown dark are fully gtk3

Also the right click on the window deco, which is dark, always produces a light menu, not a big deal I guess
As does a systray icon in the unity panel

---

### Post by screaminj3sus on 2012-03-15
> **VTPoet said:**
> I cannot, for the life of me, get any real cohesiveness in themes. I use the Ambience Theme, but I notice that some menus are dark with white fonts, and some are white with dark fonts, etc...

For instance, my Firefox menus are dark grey with a white font. However, if I right click anywhere on the browser window, the menu is white with grey font. Also, if I click on the bookmark button (firefox toolbar) the menu is white. In Libre Office, my menus are white with black font. The [classic menu]("http://www.webupd8.org/2011/06/use-classic-menu-in-unity-classicmenu.html") is dark grey with white font.

So, am I dong something wrong or is this a bug?
The new light menus are intended. They changed the right non-unity menus to be light colored, because  when they were dark, it caused visual bugs in some apps (the most noticeable example is firefox's awesomebar dropdown. It was ugly as hell in older versions of ambiance, and almost unreadable. Looks great in 12.04)

I approve of all the theme changes in 12.04. Its a good combination of light and dark elements.

---

### Post by neu5eeCh on 2012-03-15
> **screaminj3sus said:**
> The new light menus are intended. They changed the right non-unity menus to be light colored, because  when they were dark, it caused visual bugs in some apps (the most noticeable example is firefox's awesomebar dropdown. It was ugly as hell in older versions of ambiance, and almost unreadable. Looks great in 12.04)

I approve of all the theme changes in 12.04. Its a good combination of light and dark elements.

Interesting. It helps to know their thinking.

---

### Post by jpeddicord on 2012-03-18
FWIW:

[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895)

---

### Post by neu5eeCh on 2012-03-18
> **jpeddicord said:**
> FWIW:

[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895)

So this **is** considered a bug? Light menus (on right clicks and the like) when dash/panel/launcher menus are dark?

So, why is the bug marked "invalid" while the importance is marked "high"?

**Edit:** Added myself to the bug list.

---

### Post by keithpeter on 2012-03-18
> **grahammechanical said:**
> Perhaps Libreoffice is holding on to its identity harder than Firefox. I think that this will happen to any program/application that keeps its application menus in a panel in the window and not let them be put in the screen top panel.

Hello grahammechanical and all

If you want LibreOffice global menu, then just install lo-menubar from software centre

The 'look and feel' of OpenOffice/LibreOffice has always been a bit different to the Gnome desktop. I suspect this is because of the cross platform nature of the package, but I can't reference that at the moment.

---

### Post by mc4man on 2012-03-18
> **VTPoet said:**
> So this **is** considered a bug? Light menus (on right clicks and the like) when dash/panel/launcher menus are dark?

So, why is the bug marked "invalid" while the importance is marked "high"?

**Edit:** Added myself to the bug list.

I'm gathering what still is a bug is that not all is following light from light, dark from dark

---

### Post by neu5eeCh on 2012-03-18
> **keithpeter said:**
> Hello grahammechanical and all

If you want LibreOffice global menu, then just install lo-menubar from software centre

The 'look and feel' of OpenOffice/LibreOffice has always been a bit different to the Gnome desktop. I suspect this is because of the cross platform nature of the package, but I can't reference that at the moment.

Thanks for that hint! :guitar:

---

### Post by jpeddicord on 2012-03-18
> **VTPoet said:**
> So this **is** considered a bug? Light menus (on right clicks and the like) when dash/panel/launcher menus are dark?

So, why is the bug marked "invalid" while the importance is marked "high"?

**Edit:** Added myself to the bug list.

Apparently it's a bug in Unity, though I'm not sure how.

I'm not entirely sure if some menus are supposed to be lighter, but some menus are still bugged out even in Radiance (the background is lighter on the context menus).

---

### Post by cariboo on 2012-03-18
> **VTPoet said:**
> So this **is** considered a bug? Light menus (on right clicks and the like) when dash/panel/launcher menus are dark?

So, why is the bug marked "invalid" while the importance is marked "high"?

**Edit:** Added myself to the bug list.

The bug is marked invalid for theming, but it is marked as a valid Unity bug.

---

### Post by neu5eeCh on 2012-03-21
Am I the only one who thinks this mish-mash of light and dark menus is the stupidest idea since renaming French Fries, Freedom Fries? Now I'm getting into an argument with the developers over this "bug", which I probably shouldn't be. It just seems willful. If users are using a dark theme, it stands to reason that they are probably using dark themes in their apps as well - like Firefox, Nautilus and Chrome for example. Andrea Climitan writes:

"Good design is having light menus coming from light-elements."

Well... ok? So why are light menus popping out of all my dark elements?:-?

---

### Post by mc4man on 2012-03-21
Myself have come to think having the context menus light when used in app windows & by extension the Desktop the better choice. Most app windows are light & it looks better.

The remaining issues here are that all gtk2 apps have light drop down menus, context menus from window borders & systray icons also are improperly light. All of these use gtkrc

What it appears is if gtk2 windows are to have light context menus then all the menus will be light or if switched to use dark menus then all inc. the 'in window' context one will be dark, (scr. 3

If that's the choice for 12.04 ambiance, then I'd opt for gtk2 to use all dark though it would be better if it did both

screens show switching gtk2 back to all dark using synaptic as an example
Screen 3 looks a bit out of place but better than having the menus in screens 1 & 2 light.

some currently common apps using gtkrc - firefox, chrome, synaptic, vlc, & I'm sure more. The window deco & systray also are influenced



(- a small add. side issue with the current gtkrc is now 'in app menu items', when selected use 'selected_fg' when the should not & just stay white.
This would only affect if there is a user mod of 'selected_fg'

---

### Post by badhorse on 2012-03-21
I am with VTPoet! This is a bad idea (if not a bug). If i choose a dark theme, i want ALL my menus dark, not light or mixed. It' simple for everyone to understand. My theme is dark, right click on desktop shows a light menu :confused::confused:

---

### Post by screaminj3sus on 2012-03-21
> **VTPoet said:**
> Am I the only one who thinks this mish-mash of light and dark menus is the stupidest idea since renaming French Fries, Freedom Fries? Now I'm getting into an argument with the developers over this "bug", which I probably shouldn't be. It just seems willful. If users are using a dark theme, it stands to reason that they are probably using dark themes in their apps as well - like Firefox, Nautilus and Chrome for example. Andrea Climitan writes:

"Good design is having light menus coming from light-elements."

Well... ok? So why are light menus popping out of all my dark elements?:-?

Most people use the default firefox theme. The previous versins of ambiance looked horrible in firefox out of the box, you could hardly read the text on the urlbar dropdown. It looks very readable now. For me its definitely better :-)

There's still some bugs to sort out as mentioned above, some menus are light that shouldn't be.

---

### Post by mc4man on 2012-03-21
> **screaminj3sus said:**
> Most people use the default firefox theme. The previous versins of ambiance looked horrible in firefox out of the box, you could hardly read the text on the urlbar dropdown. It looks very readable now. For me its definitely better :-)

That's another area where it's now done correctly & is better (the dark url dropdown never bothered me much but that's besides the point

Hopefully it's reconcilable in gtkrc to do all correctly..

---

### Post by screaminj3sus on 2012-03-21
> **badhorse said:**
> I am with VTPoet! This is a bad idea (if not a bug). If i choose a dark theme, i want ALL my menus dark, not light or mixed. It' simple for everyone to understand. My theme is dark, right click on desktop shows a light menu :confused::confused:

Ambiance has *never* been a fully dark theme. In fact its mostly a light theme. Its part of the light-themes package for a reason :)

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-22
> **VTPoet said:**
> Am I the only one who thinks this mish-mash of light and dark menus is the stupidest idea since renaming French Fries, Freedom Fries? Now I'm getting into an argument with the developers over this "bug", which I probably shouldn't be. It just seems willful. If users are using a dark theme, it stands to reason that they are probably using dark themes in their apps as well - like Firefox, Nautilus and Chrome for example. Andrea Climitan writes:

"Good design is having light menus coming from light-elements."

Well... ok? So why are light menus popping out of all my dark elements?:-?

I second that. Looks awful :shock:

---

### Post by neu5eeCh on 2012-03-22
Do any of you have a suggestion for an Ambience type theme that will flush out the "white menus"?

---

### Post by philinux on 2012-03-22
The bug report has got very heated lately.

[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895)

---

### Post by neu5eeCh on 2012-03-22
> **philinux said:**
> The bug report has got very heated lately.

[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895)

I noticed that. Makes my own posts look cool, calm and collected. I expect that when 12.04 proper is released, Launchpad is going to see a lot more "bug reports" concerning the menu-color mismatch. I'm guessing that most users will consider this a mistake, as it looks awfully amateurish.

---

### Post by screaminj3sus on 2012-03-22
> **philinux said:**
> The bug report has got very heated lately.

[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/925895)

Wow, that Jordon Bedwell guy shouldn't even be allowed on the bug tracker with behavior like that :p

---

### Post by philinux on 2012-04-01
I thought the right click was bad enough, I've got used to that for now, but Firefox awesome bar is hideous.

---

### Post by neu5eeCh on 2012-04-01
I saw your comment on at launchpad. You're wasting your bandwidth, I think. Minds are made up at Canonical. They've decided, for reasons they can't really defend other than to insinuate *that's what we think is best for you so just suck it up and we'd really like to close the comments because we're not talking to you anymore... etc.*

I quote, from Andrea: "I had all the info I need regarding this bugreport, you can stop comments."

I keep looking for a dark theme with dark menus but good themes for Unity seem few and far between. There are a lot of nice things about Unity (now that I've been using it for the last few weeks)  but I'm really looking forward to trying out Xubuntu again.

---

### Post by philinux on 2012-04-01
> **VTPoet said:**
> I saw your comment on at launchpad. You're wasting your bandwidth, I think. Minds are made up at Canonical. They've decided, for reasons they can't really defend other than to insinuate *that's what we think is best for you so just suck it up and we'd really like to close the comments because we're not talking to you anymore... etc.*

I quote, from Andrea: "I had all the info I need regarding this bugreport, you can stop comments."

I keep looking for a dark theme with dark menus but good themes for Unity seem few and far between. There are a lot of nice things about Unity (now that I've been using it for the last few weeks)  but I'm really looking forward to trying out Xubuntu again.

It made me feel better posting the comment though ;)

---

### Post by kaldor on 2012-04-01
This is the first theme decision I've hated for a long time. It really takes away from the overall feel of Ambiance. I still think it looks broken.

---

### Post by mc4man on 2012-04-01
The 'awesome bar' seems to fall in line with the current 'design' of light from light, dark from dark

Much of the remainder of gtk2 (gtkrc) doesn't, haven't seen any inclination as of yet to fix that. (if it even is possible in current design
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/961679](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/961679) (unconfirmed, ignored, ect.

If you wished to fool around a bit the attached is a decent starting point for gtk2 - basically just restores all gtk2 to dark, does produce one not so right menu though it's a bit obscure

If inclined then mv /usr/share/themes/Ambiance/gtk-2.0/gtkrc to a .bak, replace with attached after unpacking 

(making sure after replacing that the permissions are -rw-r--r--

(this obviously  has no effect on gtk3

edit - gtkrc1 attachment fixes the 'obscure' break mentioned before, (drop down menus in ccsm,

---

### Post by neu5eeCh on 2012-04-01
> **kaldor said:**
> This is the first theme decision I've hated for a long time. It really takes away from the overall feel of Ambiance. I still think it looks broken.

Theme *decision*? Have you learned _nothing_ from political discourse? We must cast this in the most negative light possible.

We shall henceforth refer to their "decision" as a "theme _edict_". ;)

---

### Post by jcm915 on 2012-04-02
Please tell me this is getting fixed eventually, everything about 12.04 screams quality except for the weird unmatched theme for the right click menu :/

---

### Post by Derek Karpinski on 2012-04-02
Yeah, this looks terrible.

Oh, and the 'from light to light......' bs doesn't hold true in all cases.

Right-click on an unmaximized FF window........'from dark to light'  The menu almost dissapears in the light background of this Ubuntu forums page.  I'd attach a screenshot................but I can't figure out how the hell to do it in 12.04.

Terrible decision, IMHO.

Also, BFB looks cheaper compared to 11.10........maybe I'm seeing things.

---

### Post by cariboo on 2012-04-02
> **Derek Karpinski said:**
> Yeah, this looks terrible.

Oh, and the 'from light to light......' bs doesn't hold true in all cases.

Right-click on an unmaximized FF window........'from dark to light'  The menu almost dissapears in the light background of this Ubuntu forums page.  I'd attach a screenshot................but I can't figure out how the hell to do it in 12.04.

Terrible decision, IMHO.

Also, BFB looks cheaper compared to 11.10........maybe I'm seeing things.

To post a screenshot it doesn't make a difference what version, or OS you are running, use the advanced editor when creating a post, and scroll down to manage attachments. The rest is self evident from there.

If you don't know how to create a screenshot in Precise, either open the dash and type **scr** or press PrtScn on your keyboard.

---

### Post by Derek Karpinski on 2012-04-02
I know how to post a screenshot here.
 
I thought I knew how to post a screenshot in 12.04, but pressing 'Alt-PrtScn', or 'PrtScn' did NOTHING.
 
It might be because I had right-clicked on the window and had a menu open.
 
Regardless, reading the bug report on launchpad, and seeing the developer's response....a screenshot isn't going to make a difference.  Minds are made up, opposing views are stuck firmly in place......we're stuck with an ugly (IMHO) theme.

---

### Post by jbicha on 2012-04-02
Yeah, GTK has a very old bug where when a menu is open, several things don't work (the screensaver won't activate, PrintScreen won't work, etc.)

You can set a delay if you need to actually take a screenshot of a menu, in the Screenshot app (same as running gnome-screenshot -i )

---

### Post by Derek Karpinski on 2012-04-02
Sounds like a potential massive security bug!

---

### Post by neu5eeCh on 2012-04-02
> **Derek Karpinski said:**
> It might be because I had right-clicked on the window and had a menu open.

Same thing here. I'd love to send ***those who refuse to take their fingers out of their ears*** a picture of my Cairo Menu with Awoken _white_ icons on a freakin' _white_ background just to see if their holinesses can even *see* the icons.

DUH.

Add my vote with those who consider this one of the dumbest 12.04 decisions. They're going to be awash with new users filing bugs on this.

---

### Post by mc4man on 2012-04-02
Light context menus inside of light windows makes sense. While I wouldn't be terribly disappointed if they were to revert I hope not, they look better & it was a good decision

Semi-example, -  in screen I've reverted gtk2 back to all dark  - the context menu looks out of place in FF. If I could keep dark gtk2 menus from dark & light from light I would. ATM only can do one or the other so am opting for all dark

As far as gtk3 all seems quite right with some obscure exceptions like from inside a terminal window, most people don't do that.

As far as the Desktop, no way to currently alter based on color

---

### Post by neu5eeCh on 2012-04-02
> **mc4man said:**
> Light context menus inside of light windows makes sense. 

Semi-example, -  in screen I've reverted gtk2 back to all dark...


Actually, your example convinced me of the opposite. I think the dark looks much better than the light on light.

But let's leave subjective aesthetics out of it. Objectively, using light context menus makes no sense whatsoever when using a "dark" icon set with the reputedly "dark" ambience theme. It's a disaster. Period. It needs to be changed. Or maybe canonical would prefer it if we just didn't mess with what is increasingly _their_ desktop experience?

---

### Post by mc4man on 2012-04-02
Well I just did a fresh install since last post so have default everything atm - 
In screen is nautilus - don't see what the big deal is, looks fine
(trust me - I wouldn't complain if reverted, just think this looks right.

Now screen 2 looks wrong, that should be fixed (or can easily be user fixed if need be

---

### Post by neu5eeCh on 2012-04-02
> **mc4man said:**
> 
In screen is nautilus - don't see what the big deal is, looks fine

The big deal is this: If the menu includes "dark theme" icons, which can be white, the user **_can not see them_**. I can **not** see my icons when using any menu that doesn't spring from the launcher or panel. Regardless of this whole memo about white from white and dark from dark, this is just objectively bad design.

---

### Post by mc4man on 2012-04-02
> **VTPoet said:**
> The big deal is this: If the menu includes "dark theme" icons, which can be white, the user **_can not see them_**. I can **not** see my icons when using any menu that doesn't spring from the launcher or panel. Regardless of this whole memo about white from white and dark from dark, this is just objectively bad design.

You have a screen on that using the default ambaince theme? Ican enable icons on menus & while a couple are light clored all are visible

---

### Post by Derek Karpinski on 2012-04-02
After really thinking about it, and looking at why I find it so objectionable, I've come to the conclusion that I liked the dark menu because it made the menu stand out.  The light menu just doesn't stand out to me.  So, I fired up Windows in a VM just to see why I don't mind it there.

The windows right click menus have a very slight border around the menu.  It's enough to make it stand out against a light background.  I'm no good with GIMP, and I don't have 12.04 installed any more, can someone please mock this up in GIMP?  I'm interested to see if I really hate it because it's light, or because the menu gets lost in the background.

EDIT: I tried in Inkscape.  I messed up the overall length of the outline, but this looks much better IMHO.

---

### Post by philinux on 2012-04-03
> **mc4man said:**
> Well I just did a fresh install since last post so have default everything atm - 
In screen is nautilus - don't see what the big deal is, looks fine
(trust me - I wouldn't complain if reverted, just think this looks right.

Now screen 2 looks wrong, that should be fixed (or can easily be user fixed if need be

I see what you mean but I prefer ambiance in 11.10 as the dark theme is uniform.

Looks like I'll have to get used to it or change theme come release.

---

### Post by neu5eeCh on 2012-04-03
> **mc4man said:**
> You have a screen on that using the default ambaince theme? Ican enable icons on menus & while a couple are light clored all are visible

For some reason I can't use "print screen" while sub-menus are open, otherwise I would send you screen shot. Like, Philinux, though, I'll switch themes once a more knowledgeable user, fed up with Ubuntu's aesthetics from on-high, decides to make a dark Ambiance theme. That way we'll have *Radiance*, the present *Radiant Ambiance Theme*, and a _dark_ *Ambiance Theme*. :popcorn:

---

### Post by philinux on 2012-04-03
> **VTPoet said:**
> For some reason I can't use "print screen" while sub-menus are open, otherwise I would send you screen shot. Like, Philinux, though, I'll switch themes once a more knowledgeable user, fed up with Ubuntu's aesthetics from on-high, decides to make a dark Ambiance theme. That way we'll have *Radiance*, the present *Radiant Ambiance Theme*, and a _dark_ *Ambiance Theme*. :popcorn:

With sub menus open select an area option in printscreen but set a time delay of say 10 seconds

---

### Post by mc4man on 2012-04-03
> **philinux said:**
> I see what you mean but I prefer ambiance in 11.10 as the dark theme is uniform.

Looks like I'll have to get used to it or change theme come release.
I've no doubt there will be some nice themes available from elsewhere, (come release or there-abouts), probably more than 'usual' because of this change. 
(ones made for 11.10 probably won't work well in 12.04 due to changes in gtk+3
I thought these were interesting though I was looking at to see how the css was written, not to actually use (& don't know spanish, ect.
[http://ubuntued.info/tema-81-blue-wave](http://ubuntued.info/tema-81-blue-wave)

Anyway I'm sure there will be a lot to choose from  

@VTPoet - 
you can also open the sceenshot tool,  pick 'Grab current window' & set the delay as needed to set up shot

(gnome-screenshot --interactive is the command - I have it as a quicklist entry under a 'Utilities' launcher icon for ease of use

---

### Post by ubuntu27 on 2012-04-06
[QUOTE=mc4man;11814691]I
I thought these were interesting though I was looking at to see how the css was written, not to actually use (& don't know **spanish**, ect.
[http://ubuntued.info/tema-81-blue-wave](http://ubuntued.info/tema-81-blue-wave)

Its Portuguese :KS

Nice find by the way. The theme looks beautiful.

Here is the [link]("http://nowerries.deviantart.com/#/d4sf29q") to the theme's author which was  mentioned at ubuntued.info

---

### Post by Greg Merchan on 2012-04-08
Just upgraded to Precise. I spent many minutes switching themes and logging out and in, because those were the things that worked when I would log in and the wrong theme would show up. Annoyed. Very annoyed that this is intended behavior. It looks awful. It's jarring, and I'm not even keeping things dark.

---

### Post by philinux on 2012-04-09
Looks like the light theme can be fixed.

 [http://iloveubuntu.net/how-fix-radiances-white-menus-ubuntu-1204](http://iloveubuntu.net/how-fix-radiances-white-menus-ubuntu-1204)

---

### Post by neu5eeCh on 2012-04-09
This thread and mine should probably be combined:

[http://ubuntuforums.org/showthread.php?t=1941302](http://ubuntuforums.org/showthread.php?t=1941302)

---

### Post by philinux on 2012-04-10
Merged

---

### Post by Cynical on 2012-04-18
> **Derek Karpinski said:**
> Yeah, this looks terrible.

Oh, and the 'from light to light......' bs doesn't hold true in all cases.

Right-click on an unmaximized FF window........'from dark to light'  The menu almost dissapears in the light background of this Ubuntu forums page.  I'd attach a screenshot................but I can't figure out how the hell to do it in 12.04.

Terrible decision, IMHO.

Also, BFB looks cheaper compared to 11.10........maybe I'm seeing things.

You aren't seeing things. BFB went "chameleonic". (so did the desktop switcher and trash icons) Personally I preferred these icons remain a neutral transparent/clear to distinguish them from app icons but unfortunately there is no option for that at the moment. 

The menu change is also bothersome, I'm definitely going to go through the theme file and fix it once 12.04 is actually released. If I wanted light menus I would use Radiance, because that is the light theme. The reason I'm using Ambiance is because I prefer dark themes. Their line of reasoning makes sense (dark from dark, light from light) but unfortunately the result in terrible in practice, less so in apps but more so on the desktop.

---

