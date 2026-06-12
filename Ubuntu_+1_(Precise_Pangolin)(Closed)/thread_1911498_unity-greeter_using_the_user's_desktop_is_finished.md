---
title: "unity-greeter using the user's desktop is finished.."
date: 2012-01-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mc4man on 2012-01-19
Seems to work oK, does retain the white-dot grid.

---

### Post by VinDSL on 2012-01-19
I noticed this in the *unity-greeter.conf* diff, when I upgraded.

```
#
# background = Background file to use, either an image path or a color (e.g. #772953)
**[COLOR="DarkRed"]# draw-grid = Whether to draw an overlay grid[/COLOR]**
# logo = Logo file to use
# theme-name = GTK+ theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (hintnone, hintslight, hintmedium, or hintfull)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
#
[greeter]
background=/usr/share/backgrounds/warty-final-ubuntu.png
**[COLOR="DarkRed"]draw-grid=true[/COLOR]**
logo=/usr/share/unity-greeter/logo.png
theme-name=Ambiance
icon-theme-name=ubuntu-mono-dark
font-name=Ubuntu 11
xft-antialias=true
xft-dpi=96
xft-hintstyle=hintslight
xft-rgba=rgb
```

I haven't tried it, but it looks like you can turn off the "dots" now...

---

### Post by ventrical on 2012-01-19
Just awesome .. it uses and changes the desktop background as set per each user.

---

### Post by ventrical on 2012-01-19
for example ..

[http://www.youtube.com/watch?v=ne293P-f_4I](http://www.youtube.com/watch?v=ne293P-f_4I)

---

### Post by mc4man on 2012-01-19
> **VinDSL said:**
> I noticed this in the *unity-greeter.conf* diff, when I upgraded.

I haven't tried it, but it looks like you can turn off the "dots" now...

You're right - can be removed if desired.

---

### Post by Double.J on 2012-01-19
Haha I changed my lightdm background to desktop 48 hours ago.. typical :) glad it's working though - not on the box at the mo... next your going to tell me the 12.04 logo's arrived too - I made mine with a netbook trackpad and pencil 'coz gimp took up the screen... :shock: well.. it's personal lol

---

### Post by kyleabaker on 2012-01-19
> **gnu/mirow said:**
> next your going to tell me the 12.04 logo's arrived too - I made mine with a netbook trackpad and pencil 'coz gimp took up the screen... :shock: well.. it's personal lol

The 12.04 logo **has** arrived. :P

---

### Post by Double.J on 2012-01-19
> **kyleabaker said:**
> The 12.04 logo **has** arrived. :P

#-o

---

### Post by fjgaude on 2012-01-19
What a blessing, to see my own background when and if I log in.

---

### Post by VinDSL on 2012-01-19
Noticed an oddity, at first boot, this morning...

The alternate DE icon (gnome shell, gnome 2d, et cetera) was missing from the corner of my User login box.

I clicked on Guest Session, and the icon was present.  I clicked it, and everything was there.  So...

I went back to the VinDSL login box, and the alternate DE icon magically reappeared.

Anyway, the new greeter is looking great!!!

---

### Post by MacUntu on 2012-01-19
Does this work for you guys with pictures NOT in the "Wallpaper" section? It also doesn't seem to work with solid colors/gradients.

---

### Post by kyleabaker on 2012-01-19
> **MacUntu said:**
> Does this work for you guys with pictures NOT in the "Wallpaper" section? It also doesn't seem to work with solid colors/gradients.

Works for me.

EDIT:
Though it doesn't seem to keep the aspect that I apply (span - for my twinview setup).

---

### Post by MacUntu on 2012-01-19
Thanks. Next milestone &#8594; reinstall. :P

Log files, log files, log files. It says permission denied, and yeah, my .cache dir is only readable by me.

Bug report: [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918934](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918934)

---

### Post by mc4man on 2012-01-19
> **MacUntu said:**
> Thanks. Next milestone &#8594; reinstall. :P

Log files, log files, log files. It says permission denied, and yeah, my .cache dir is only readable by me.

Bug report: [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918934](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918934)

Works here from Pictures as long as the image is actually in Pictures
(the image may be duped/backed up  in ~/.cache/wallpapers

(maybe some backwash from whatever that issue was people had with images in ~/.cache/wallpapers?, details have slipped away here.

---

### Post by Bowmore on 2012-01-19
Yes, there are backgrounds that do work as a desktop background but not for lightdm which then chooses the default one. Some of my private backgrounds work ok other not. Maybe it's a resolution issue.

I've haven't checked it yet but there should be a way to disable this on a per user basis, e.g for privacy/integrity as I know that this privacy/integrity issue has been discussed earlier. Another nice option could be that you are given the choice to select a specific (static) personal background per user for the lightdm login screen. But I guess that's not in the scope for Precise as it also affects other packages such as e.g gnome-control-center plugin Appearance I guess. Maybe it's possible to hack but I prefer a UX user-friendly solution in the future ;)

---

### Post by mc4man on 2012-01-19
As far as the "privacy" deal, if there isn't an option which there doesn't appear to be,  then just stick the image where it can't be retrieved 
(which atm is just about anywhere in $HOME except ~/Pictures

---

### Post by Bowmore on 2012-01-19
Well, I don't bother about privacy but others do, Then I don't believe that the path itself to the background "solves" this as I don't have my private backgrounds in the Picture folder and most of them work anyway.

---

### Post by Bowmore on 2012-01-19
@mc4man; Sorry, I think you're right after a quick test. Just wonder from where I got that :confused:

---

### Post by effenberg0x0 on 2012-01-19
Maybe [Greeter].background could be set to /usr/share/backgrounds/dynamic.png

When JohnDoe is logged in, /usr/share/backgrounds/dynamic.png would be a soft-link to /usr/share/backgrounds/NotPr0n.png (default @ $ANYONE/.bashrc)

When $YOU log in, ~/.bashrc (640) resets the link to /usr/share/backgrounds/Pr0n.png
Actually ~/.bashrc could just sed the config anyway, no links.

[FONT=monospace]
[/FONT]

---

### Post by mc4man on 2012-01-19
I've no clue (don't quite care either), what the intention is as to where images can or can not be. You'd think they could be anywhere readable/useable.

Obviously solutions will arise for those that choose to use 'private' backgrounds if the current 'restrictions' are fixed

(though I'm sure some will complain they shouldn't have to do anything, it should be provided for them ect.

---

### Post by effenberg0x0 on 2012-01-19
> **mc4man said:**
> I've no clue (don't quite care either), what the intention is as to where images can or can not be. You'd think they could be anywhere readable/useable.

Obviously solutions will arise for those that choose to use 'private' backgrounds if the current 'restrictions' are fixed

(though I'm sure some will complain they shouldn't have to do anything, it should be provided for them ect.

True... Maybe there was some initial idea to deal with happy-kappy.jpg vs 2g1c.jpg on multi-user PCs that hasn't developed entirely.

---

### Post by MacUntu on 2012-01-19
Not sure, I have a couple of images in the "Pictures" tab that set the gsettings key to ~/Pictures/..., but ALL new ones (even if they are in ~/Pictures) cause the key to point to ~/.cache/... and therefore fail to show.

Does setting a solid background work for you (I mean, does the setting get reflected in the greeter)? If not, please confirm [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918941](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918941)

---

### Post by grahammechanical on 2012-01-19
I have deleted the contents as I clicked submit instead of Go Advanced. Sorry.

---

### Post by grahammechanical on 2012-01-19
I have been able to add the old Holes background/wallpaper as a background that appears in the User Interface (to use its new name) by putting the image file in /usr/share/backgrounds and then editing /usr/share/gnome-background-properties/ubuntu-wallpapers.xml.

You need to add additional lines before the </wallpapers> markup. such as

```
  <wallpaper>
    <name>Holes</name>
 <filename>/usr/share/backgrounds/Holes_by_FireCobold.jpg</filename>
    <options>zoom</options>
    <pcolor>#000000</pcolor>
    <scolor>#000000</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>
```

Do this and you can set both the desktop background and the LightDM background without using the Pictures folder.

Regards.

P.S. I have just found out something else. You can use Simple LightDM Manager to set a background image and logo for one user and it does not over-ride the LightDM background of another user if they are using a static background image.

---

### Post by mc4man on 2012-01-19
> **MacUntu said:**
> Not sure, I have a couple of images in the "Pictures" tab that set the gsettings key to ~/Pictures/..., but ALL new ones (even if they are in ~/Pictures) cause the key to point to ~/.cache/... and therefore fail to show.

Does setting a solid background work for you (I mean, does the setting get reflected in the greeter)? If not, please confirm [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918941](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918941)

Solid colors do not work here. If I remove my current image from Pictures & switch to the XXXXXXXXX back up in ~/.cache/wallpapers then it also won't be used in the greeter. Same goes for if using an image in Documents & probably other locations

My gsetting is pointing to the actual used location, (~/Pictures) unless I specify ~/.cache/.. though I've more than once deleted the images in ~/.cache/.. (well actually because I 'lost' my preferred image at some point from Pictures, I copied the backup from .cache..  , renamed it, placed back in Pictures & deleted the images in .cache..  

One additional oddity
This setup has a 2nd user for testing when needed. Now when getting to the greeter my main user does not have the session chooser cog shown, I can only log in to last used (unity-3d
To get the cog to show I have to switch to the other user, then back to main user. The cog then appears. 
I'd assume single user setups always show the cog?

Edit: - 
thru a little bit of round robin manged to get something similar - even if picked from Pictures would show in gsettings as /home/doug/.cache/gnome-control-center/backgrounds/xxxxxx...
At that point the only way to reset & get back in the greeeter was to delete the contents of both ~/.cache/gnome-control/center/... & ~/.cache/wallpaper/

Seems a bit convoluted - picking an image in Pictures backs it up to ~/.cache/wallpaper/ as xxxxxxx.. & places it in ~/.cache/gnome-control-center/.. as a different xxxxxxxx..

---

### Post by sammiev on 2012-01-19
I add my wallpaper I want to use to /usr/share/backgrounds. Then I use ubuntu tweak to select it. It works on all 3 of my laptops and all with different wallpaper and I change my log-in screen often and never had one not load or work yet.

---

### Post by nariub on 2012-01-20
I turn off the name browser,
to make anyone logging in know both a valid username and it's associated password..

is this new feature optional, such that I can turn it off as well?
I would rather not 'give away' that the alphanumeric sequence just entered as the username is valid or not by changing the background of the greeter..

call it a personal preference.

---

### Post by cariboo on 2012-01-20
> **nariub said:**
> I turn off the name browser,
to make anyone logging in know both a valid username and it's associated password..

is this new feature optional, such that I can turn it off as well?
I would rather not 'give away' that the alphanumeric sequence just entered as the username is valid or not by changing the background of the greeter..

call it a personal preference.

You should be able to hide user names by adding them to hidden-users in /etc/lightdm/users.conf eg:

```
hidden-users=nobody nobody4 noaccess **nariub**
```

---

### Post by VinDSL on 2012-01-21
> **Bowmore said:**
> Yes, there are backgrounds that do work as a desktop background but not for lightdm which then chooses the default one. Some of my private backgrounds work ok other not. 

Maybe it's a resolution issue.[...]
That rings a bell...  :)

When I manually set a wall in LightDM,via the conf file, the resolution has to be exactly the same as my desktop size, e.g. 1280x1024(5:4).  

If I choose a wall that isn't native res, LightDM will use the default wall.

AFAIK, LightDM won't tile, zoom, center, scale, fill, et cetera.

---

### Post by mc4man on 2012-01-21
> **VinDSL said:**
> That rings a bell...  :)

When I manually set a wall in LightDM,via the conf file, the resolution has to be exactly the same as my desktop size, e.g. 1280x1024(5:4).  

If I choose a wall that isn't native res, LightDM will use the default wall.

AFAIK, LightDM won't tile, zoom, center, scale, fill, et cetera.
While my current BG & res is 1200x800 I just switched to a 1600x1200 BG & it show in greeter fine..

---

### Post by VinDSL on 2012-01-21
> **mc4man said:**
> While my current BG & res is 1200x800 I just switched to a 1600x1200 BG & it show in greeter fine..
~Cool

I'll give it a shot on this machine.

BBL

---

### Post by VinDSL on 2012-01-21
Yep!  You're right.

I used a 1680x1050 wall (on my 1280x1024 desktop) and LightDM displayed it just fine.

Good to know.  Thanks!  ;)

---

### Post by mc4man on 2012-01-21
I guess one other thing to look at though at this I've stopped trying to figure out -
 
When you use a custom BG from  Pictures & maybe elsewhere it will then show up in ~/.cache/wallpaper resized to your screen if the orig. was different.
(So the 1600x1200 I just used is 1200x800 in the cache

Additionally under some circumstances this (these) images can also show up in ~/.cache/gnome-control-center/backgrounds, probably resized though atm I don't have any, deleted them all the other day

(- if one saw images in the Change Desktop Background > Pictures dropdown that were no longer  in the Pictures folder or the ~/.cache/wallpaper folder, then they'll be in the ~/.cache/gnome-control-center/backgrounds folder

---

### Post by kyleabaker on 2012-01-21
As you guys have mentioned, the greeter doesn't seem to follow the aspect selected for a particular wallpaper. I have a dual screen setup and a wallpaper that spans both screens, but it seems to center on the greeter screen so it jumps between the greeter and desktop.

---

### Post by forcecore on 2012-01-24
Most of people like that dot grid when i demostrated 12.04.

---

### Post by fjgaude on 2012-01-24
> **forcecore said:**
> Most of people like that dot grid when i demostrated 12.04.

I did and do! <smile>

---

