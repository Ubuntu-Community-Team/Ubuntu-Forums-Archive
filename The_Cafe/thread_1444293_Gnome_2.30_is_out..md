---
title: "Gnome 2.30 is out."
date: 2010-04-01
forum: The Cafe
---

### Post by NightwishFan on 2010-04-01
[http://library.gnome.org/misc/release-notes/2.30/](http://library.gnome.org/misc/release-notes/2.30/)

Looks great. I am running Lucid so I am sure 2.30 stuff is going to hit. I could also check out my Debian Sid boxes but I am currently mobile. ;)

---

### Post by murderslastcrow on 2010-04-01
I'm really liking the list of improvements.

I really hope Gnome-Shell isn't the default, since not everyone has compositing. Like, if they just add more search integration to what we've already got and simplify some of the default interface (it's already pretty much perfect for me), then I'll love Gnome 3. And I'm seeing a lot of speed improvements here, and I hope Gnome 3 is FASTER than Gnome 2, and we don't regress and start sapping up all the new hardware coming out out of laziness.

I want Gnome 3 to be awesome and fast as Xfce. Then there will be no complaint. But I guess there's always Xubuntu if Gnome-Shell gets shoved down my pie hole XD.

---

### Post by NightwishFan on 2010-04-01
I am wary as well. The gnome shell is great but I do not want my interface to be 3d except the rare times I am bored. It is true the majority of people probably use a 3d interface on every OS now, however I still hope they keep the 2d interface for 3.2 and on..

---

### Post by symon1980 on 2010-04-02
pfffttttttttt Get with the times people
if they Polish Gnome-shell up and give it a good theme, add the functionality that is currently talked about.... Gnome-Shell should be default with the option to turn it off to make everyone happy

I love the gnomeshell concept... it just looks a bit crappy and isn't fully functional at the moment.... it will get there within 6 months

---

### Post by Psumi on 2010-04-02
> **symon1980 said:**
> pfffttttttttt Get with the times people
if they Polish Gnome-shell up and give it a good theme, add the functionality that is currently talked about.... Gnome-Shell should be default with the option to turn it off to make everyone happy

I love the gnomeshell concept... it just looks a bit crappy and isn't fully functional at the moment.... it will get there within 6 months

gnome-panel isn't receiving updates after gnome-shell is pushed through, sorry. They don't plan for you to turn it off, they want you to purge, and install panel.

It's called "legacy software," and many linux users should know what that means. Just like how GRUB turned into GRUB2.

---

### Post by weezerBo on 2010-04-02
It's beginning to get to the point where instead of looking for new features in a GNOME release I look for the features that they chopped because they weren't fitting with their lowest common denominator extremism. 

Within seconds of upgrading to 2.30 (Arch) I noticed they chopped the interface tab in gnome-appearance-properties. The lack of icons in menus really bothers me, because the 'System' menu in the menubar lacks them while every other menu (including it's submenu) has them, and they're just visually nice. Now I have to play in gconf to enable them. Whenever something gets relegated to gconf it usually means it's just a matter of time before they decide to remove it completely. 

The same deal with editable menu shortcuts. This is basic functionality which should be turned on by default and they've hidden it in the bowels of gconf.

---

### Post by Psumi on 2010-04-02
> **weezerBo said:**
> It's beginning to get to the point where instead of looking for new features in a GNOME release I look for the features that they chopped because they weren't fitting with their lowest common denominator extremism. 

Within seconds of upgrading to 2.30 (Arch) I noticed they chopped the interface tab in gnome-appearance-properties. The lack of icons in menus really bothers me, because the 'System' menu in the menubar lacks them while every other menu (including it's submenu) has them, and they're just visually nice. Now I have to play in gconf to enable them. Whenever something gets relegated to gconf it usually means it's just a matter of time before they decide to remove it completely. 

The same deal with editable menu shortcuts. This is basic functionality which should be turned on by default and they've hidden it in the bowels of gconf.

Know what those gconf settings are? What values they accept, etc?

Also, this is because of panel being scrapped for shell, which won't have those menus.

---

### Post by burton247 on 2010-04-02
I use gnome but have replaced metacity with xmonad. I hope this is still possible with gnome-shell, ill have to test it out sometime. Xubuntu has awesome speed but the setup makes it harder for me to use xmonad with it, it sucks. If it all goes to pot looks like ill have just have an xmonad session :(

With any luck they will try and increase speed and not decrease it

---

### Post by weezerBo on 2010-04-02
> **Psumi said:**
> Know what those gconf settings are? What values they accept, etc?

Also, this is because of panel being scrapped for shell, which won't have those menus.
AFAIK the icons in menus / buttons were originally scrapped because of alignment issues they didn't care to fix. maybe that was just icons in buttons. 

/desktop/gnome/interface/can_change_accels 
/desktop/gnome/interface/menus_have_icons

bool.

---

### Post by symon1980 on 2010-04-02
> **Psumi said:**
> gnome-panel isn't receiving updates after gnome-shell is pushed through, sorry. They don't plan for you to turn it off, they want you to purge, and install panel.

It's called "legacy software," and many linux users should know what that means. Just like how GRUB turned into GRUB2.

I have read countless times that Gnome-Shell will be able to be switched off if you don't want it, and that it won't be forced upon the user... 
show me an official link that says this is not true?
I'm sure you will be able to enable or disable Gnome-shell in the future just like you can currently... otherwise that would be stupid

---

### Post by NightwishFan on 2010-04-02
There is a link in my sig. Also, I believe some of the few mentioned concerns in this thread are valid. I am shopping around for what fits for me, I suppose the only answer is we shall see.

---

### Post by themarker0 on 2010-04-02
SEXY. How do i get this on 9.10

---

### Post by NightwishFan on 2010-04-02
Gnome 2.30 is on Lucid, You can find the Gnome Shell for Karmic or Lucid here:
[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

---

### Post by Psumi on 2010-04-02
> **symon1980 said:**
> I have read countless times that Gnome-Shell will be able to be switched off if you don't want it, and that it won't be forced upon the user... 
show me an official link that says this is not true?
I'm sure you will be able to enable or disable Gnome-shell in the future just like you can currently... otherwise that would be stupid

You can't just "switch off" GNOME Shell:

1. It's a window manager (Compiz is as well.)
2. It's a compositor (Compiz is as well.)
3. It's a panel (Compiz is not.)
4. It's an Application Menu (Compiz is not. Don't compare an application menu with a window manager menu, they aren't the same.)

Number 4 is because "ubuntu Software center" cannot be searched for in GNOME Shell, unless that was already fixed.

You can't run gnome shell while running gnome panel, nor vice versa, it will give you a nice error stating that either "gnome panel: fatal error, could not run." or "gnome shell: GNOME Panel is already running, could not run." So you see, you cannot just simply flip a switch.

---

### Post by burton247 on 2010-04-02
> You can't just "switch off" GNOME Shell:

1. It's a window manager (Compiz is as well.)
2. It's a compositor (Compiz is as well.)
3. It's a panel (Compiz is not.)
4. It's an Application Menu (Compiz is not. Don't compare an application menu with a window manager menu, they aren't the same.)

Yes, but you can opt out of using it. And instead use gnome-panel and metacity/compiz (i dont like compiz however) 

Having said that they are not updating gnome-panel after gnome 3's release.
It would be possible to use another panel, but if your going that far you may was well move away from gnome all together

---

### Post by 23meg on 2010-04-02
> **Psumi said:**
> You can't run gnome shell while running gnome panel, nor vice versa, it will give you a nice error stating that either "gnome panel: fatal error, could not run." or "gnome shell: GNOME Panel is already running, could not run." So you see, you cannot just simply flip a switch.

Since GNOME Shell replaces Metacity *and* GNOME Panel, the definition of "simply flipping a switch" includes both Metacity (or whatever other window manager you want) *and* GNOME Panel.

If you don't like GNOME Shell, you can use those two, since both will still be maintained for a good while. You can also use any other panel or window manager with the rest of GNOME 3.x.

---

### Post by burton247 on 2010-04-02
> If you don't like GNOME Shell, you can use those two, since both will still be maintained for a good while. You can also use any other panel or window manager with the rest of GNOME 3.x.

panels i believe but WMs? are you sure, its just i read it has to use mutter. Gnome-shell really didnt like xmonad. Could have just been me not setting it up properly though

---

### Post by NightwishFan on 2010-04-02
The Gnome Shell esentially is the mutter window manager. A replacement will not work.

---

### Post by burton247 on 2010-04-02
That rules me out of gnome3 then

---

### Post by 23meg on 2010-04-02
> **burton247 said:**
> panels i believe but WMs? are you sure, its just i read it has to use mutter. Gnome-shell really didnt like xmonad. Could have just been me not setting it up properly though

GNOME Shell is a Mutter plugin, so yes, you have to run Mutter to use it. But I was talking about alternatives to running GNOME Shell: you'll be able to run any combination of WM + panel *instead of* GNOME Shell, just like you can run any combination of WM + panel *instead of* Metacity + GNOME Panel now.

---

### Post by Uncle Spellbinder on 2010-04-02
As it is now, I detest Gnome Shell. Simply cannot stand it. I have no real issues with Gnome in Lucid at the moment, but judging from the direction Gnome seems to be taking for version 3, looks like LXDE or XFCE for me, I'm afraid.

---

### Post by Psumi on 2010-04-02
> **Uncle Spellbinder said:**
> As it is now, I detest Gnome Shell. Simply cannot stand it. I have no real issues with Gnome in Lucid at the moment, but judging from the direction Gnome seems to be taking for version 3, looks like LXDE or XFCE for me, I'm afraid.

Or in my case, OpenBox and no DE/DM.

Startx all the way!

---

### Post by NightwishFan on 2010-04-02
My only issue is the required compositing. I do not see why they just did not make it optional. Sure it leaps into the future of 3d interfaces however 2d is not quite dead yet.

I.. may switch to KDE or XFCE if the Gnome Shell is terrible. However I am willing to have faith in them for now. The shell itself is great, just perhaps a bad timed idea. All the Gnome applications are much more to my liking than KDE ones, which I am sad to say.

---

### Post by burton247 on 2010-04-02
> Or in my case, OpenBox and no DE/DM.

Startx all the way!

Do you still run ubuntu? [edit] read your sig [/edit]

as XFCE cant intergrate different WMs easily im looking to ditch DE's too. I used to do the old startx on my arch build into openbox, but i dont really use that computer anymore, just wondered cause it's looking like ubuntu's future has no place for me. Unless i just do a stripped down base install - i can see more people opting for this down the line

---

### Post by 23meg on 2010-04-02
> **Uncle Spellbinder said:**
> As it is now, I detest Gnome Shell. Simply cannot stand it. I have no real issues with Gnome in Lucid at the moment, but judging from the direction Gnome seems to be taking for version 3, looks like LXDE or XFCE for me, I'm afraid.

If you don't like GNOME Shell, for whatever reason, you'll be able to use the GNOME 2.x panel, together with all the applets, the menu, and whatever WM you want (including Metacity and Compiz) for a good few years in a supported state, since if nothing else, Ubuntu 10.04, which will be supported for three years, is shipping them. 

If you're fine with GNOME as it is, you most likely won't have to switch to anything.

---

### Post by Uncle Spellbinder on 2010-04-02
> **23meg said:**
> If you don't like GNOME Shell, for whatever reason, you'll be able to use the GNOME 2.x panel, together with all the applets, the menu, and whatever WM you want (including Metacity and Compiz) for a good few years in a supported state, since if nothing else, Ubuntu 10.04, which will be supported for three years, is shipping them. 

If you're fine with GNOME as it is, you most likely won't have to switch to anything.

That's a bit of good news. At least I'll get the chance to try out Gnome 3/Gnome Shell and see if I can get use to it while continuing to use 2.x.

---

### Post by NightwishFan on 2010-04-02
I am in a bit of limbo with distributions as well. Debian seems to fit my needs very well, however it is always much work to get it where I want it. OpenSUSE used to be excellent yet lately it is one of the buggiest systems I have used. Fedora may be an option, I have not tried it lately. Arch and Gentoo do not appeal to me, neither does Mandriva.

I suppose I shall just continue to support Ubuntu and Debian.

---

### Post by Simian Man on 2010-04-02
Gnome has a lot of good software, but gnome-panel and metacity are really not among them.  The panel forgets the location of applets, doesn't come out of auto-hide correctly, doesn't work on the side of screens and can't switch monitors easily.  And metacity is just so laughably limited and ugly IMHO.  I really am not at all upset to see them go the way of the dodos.

Xfce's panel and window manager are head and shoulders above their Gnome counterparts.  Give them a try if you haven't.

---

### Post by NightwishFan on 2010-04-02
I agree about the panel, but I do like Nautilus. Thunar is good, but Dolpin is terrible. (In my opinion of course)

---

### Post by themarker0 on 2010-04-02
You guys got to remember, Ubuntu has to keep up with the times. Us people who prefer will have to adapt or fork. I'll adapt if i must :P

---

### Post by Simian Man on 2010-04-02
> **NightwishFan said:**
> I agree about the panel, but I do like Nautilus. Thunar is good, but Dolpin is terrible. (In my opinion of course)

Yeah I don't know which project has the better file manager.  I love Thunar's ability to add custom right-click options so easily, but wish it had tabs.  Now nautilus looks to have [even more features]("http://library.gnome.org/misc/release-notes/2.30/#rnusers.nautilus").

My desktop is always an amalgam of the best of Gnome, Xfce and other Gtk projects :).

---

### Post by Psumi on 2010-04-02
> **themarker0 said:**
> You guys got to remember, Ubuntu has to keep up with the times. Us people who prefer will have to adapt or fork. I'll adapt if i must :P

Or just use ubuntu's base, debian, and build your own install.

```
## Remember to use alsamixer then, after quitting it with desired settings, use alsactl store.
## In pcmanfm, make sure it's the desktop manager.
## .config/openbox/autostart.sh
## ## Add pcmanfm -d
## ## Add conky
## /etc/apt/sources.list
## ## Add deb http://www.debian-multimedia.org squeeze main non-free contrib
## ## Add contrib to all the debian repos.
## After installing flash, replace it with 10.1, as it's much faster.
apt-get install openbox obmenu menu obconf gtk-themes-murrine gtk-chtheme alsa-utils iceweasel xorg pcmanfm gnome-icon-theme notify-osd conky flashplugin-nonfree hplip xsane gimp pidgin pidgin-libnotify gstreamer0.10-x gstreamer0.10-ffmpeg ffmpeg faad faac totem freepats x264 libdvdcss2 lxterminal htop --no-install-recommends
```

Wait. All done. Reboot. Login. Startx.

Conkyrc:
```
# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2009 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
# All rights reserved.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints sticky,undecorated,below,skip_taskbar,skip_pager
background no
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
# fiddle with window
use_spacer yes
use_xft yes
# Update interval in seconds
update_interval 0.5
# Minimum size of text area
#minimum_size 5 5
# Draw shades?
draw_shades yes
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
# Stippled borders?
stippled_borders 8

# border margins
border_margin 4
# border width
border_width 1
# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white
own_window_colour brown
own_window_transparent yes
# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right
# Gap between borders of screen and text
gap_x 10
gap_y 10
# stuff after 'TEXT' will be formatted on screen
override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT
${offset 0}${color lightgrey}Kern:${color }$kernel ][ ${offset 0}${color lightgrey}${time %a, } ${color }${time %e %B %G} ][ ${offset 0}${color lightgrey}${time %Z,    }${color }${time %H:%M:%S} ][ ${offset 0}${color lightgrey}CPU:${color } $cpu% ${acpitemp}C ${offset 0}${cpubar 3,100} ][ ${offset 0}${color lightgrey}MEM:  ${color } $memperc% $mem/$memmax ${offset 0}${membar 3,100} ${offset 0}${color lightgrey} ][ SWAP: ${color }$swapperc% $swap/$swapmax ${offset 0}${swapbar 3,100} ][ ${offset 0}${color lightgrey}NET: ${offset 0}${color}Up: ${color }${upspeed eth0} ${offset 0}${color}Down: ${color }${downspeed eth0}${color}
```

.config/openbox/autostart.sh
```
# Run the system-wide support stuff
. $GLOBALAUTOSTART

# Programs that will run after Openbox has started
(sleep 2 && pcmanfm -d) &
(sleep 2 && conky -d) &
```

.config/openbox/menu.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<openbox_menu xmlns="http://openbox.org/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://openbox.org/                 file:///usr/share/openbox/menu.xsd">
	<menu id="root-menu" label="Openbox 3">
		<item label="Terminal emulator">
			<action name="Execute">
				<execute>
					x-terminal-emulator
				</execute>
			</action>
		</item>
		<item label="Web browser">
			<action name="Execute">
				<execute>
					x-www-browser
				</execute>
			</action>
		</item>
		<!-- This requires the presence of the 'menu' package to work -->
		<item label="Pidgin">
			<action name="Execute">
				<execute>
					pidgin
				</execute>
			</action>
		</item>
		<item label="Conky">
			<action name="Execute">
				<execute>
					conky
				</execute>
			</action>
		</item>
		<menu id="Debian"/>
		<separator/>
		<item label="Screenshot">
			<action name="Execute">
				<execute>
					scrot -q 100 -d 5 screenshot-%F-%H%M%S.jpg
				</execute>
			</action>
		</item>
		<menu id="client-list-menu"/>
		<separator/>
		<item label="ObConf">
			<action name="Execute">
				<execute>
					obconf
				</execute>
			</action>
		</item>
		<item label="Exit">
			<action name="Execute">
				<execute>
					gksu /home/psumi/.scripts/excuIsuma
				</execute>
			</action>
		</item>
	</menu>
</openbox_menu>
```

.gtkrc.mine:
```
## icon theme...
gtk-icon-theme-name = "Voyager-Simple-Dark.05"

## Tooltips
style "tooltip" {
bg[NORMAL] = "#FBF7B0"
fg[NORMAL] = "#000000"
}

widget "gtk-tooltip*" style "tooltip"
```

cups is: localhost:631

add printers/scanners through it.

---

### Post by Dark Aspect on 2010-04-02
Runs great on my netbook with Arch Linux - Updated today.

---

### Post by GMU_DodgyHodgy on 2010-04-02
I started out not liking Gnome 3 (Gnome Shell).

However, after using it for a while, and getting used to working with the environment I actually like it.  

Unlike KDE's focus on shiny glittering things - Gnome's approach has been to focus on changing on how you work with the desktop. I find myself better organized and more focused when working with the shell.  

Reading up on the planned enhancements and improvements - I am actually looking forward to it.  

Having said this - I needed to get a wide-screen monitor to really enjoy the new environment. 

But I like it.

---

### Post by themarker0 on 2010-04-02
> **Psumi said:**
> Or just use ubuntu's base, debian, and build your own install.
-snip-

I mean Gnome itself.

---

### Post by Psumi on 2010-04-02
> **themarker0 said:**
> I mean Gnome itself.

apt-get install gnome-core xorg gdm gksu totem alsa-utils

BAM!

---

### Post by Simian Man on 2010-04-02
> **Psumi said:**
> Or just use ubuntu's base, debian, and build your own install.

*stuff*

Do you not realize you can do that exact same thing with *any* distribution?

---

### Post by Psumi on 2010-04-02
> **Simian Man said:**
> Do you not realize you can do that exact same thing with *any* distribution?

I like it better in debian. Yum scares me.

---

### Post by symon1980 on 2010-04-02
> **burton247 said:**
> Yes, but you can opt out of using it. And instead use gnome-panel and metacity/compiz (i dont like compiz however) 

Having said that they are not updating gnome-panel after gnome 3's release.
It would be possible to use another panel, but if your going that far you may was well move away from gnome all together

Psumi, thats exactly what I was trying to say... I didn't mean run gnome panel and gnome-shell at the same time, I meant you can turn off gnome-shell and replace it with Metacity/Gnome panel, Just like you can right now

---

### Post by Psumi on 2010-04-02
> **symon1980 said:**
> Psumi, thats exactly what I was trying to say... I didn't mean run gnome panel and gnome-shell at the same time, I meant you can turn off gnome-shell and replace it with Metacity/Gnome panel, Just like you can right now

But you FIRST have to send a killall signal to one or the other, otherwise you can't change.

Killing GNOME Shell, if I recall, will cause the dreaded "No Window Decorations" deal.

---

### Post by NightwishFan on 2010-04-02
Perhaps you should know of the dreaded 'debugexit' which should cause the Gnome shell to completely revert to the previous environment. The only exception is if you started it natively, in which case it will try to revert to itself.

Press alt+f2, and away you go!
```
debugexit
```

My advice on the Gnome shell is do not knock it until you tried it. If you tried it do not condemn it until it is released. If you do not like it then, condemn it but perhaps respect it as a free software project. ;)

Cheers to everyone trying to keep this thread mainly flame free, though it was mainly intended to be about 2.30 not 2.32/3.0

---

### Post by symon1980 on 2010-04-02
> **Psumi said:**
> But you FIRST have to send a killall signal to one or the other, otherwise you can't change.

Killing GNOME Shell, if I recall, will cause the dreaded "No Window Decorations" deal.

You CAN change from metacity to gnome-shell and back again currently, although its a bit dodge.... 
gnome-shell --replace to turn Gnome-shell on

metacity --replace is a bit dodge to turn it back on, but theres a debug mode command that makes it work, i just can't be bothered looking it up at the moment. When Gnome 3 and Gnome-shell is finished, there will be an easy way to change between window managers that doesn't cause errors, that is a goal mentioned....

[http://blogs.gnome.org/metacity/2009/03/31/mutter-integration-the-story-so-far/](http://blogs.gnome.org/metacity/2009/03/31/mutter-integration-the-story-so-far/)

so there you have it
you WILL be able to switch off Gnome-Shell if you don't want to use it with ease, it just hasn't got there yet... it WILL by the time its ready

---

### Post by symon1980 on 2010-04-02
> **NightwishFan said:**
> Perhaps you should know of the dreaded 'debugexit' which should cause the Gnome shell to completely revert to the previous environment. The only exception is if you started it natively, in which case it will try to revert to itself.

Press alt+f2, and away you go!
```
debugexit
```

My advice on the Gnome shell is do not knock it until you tried it. If you tried it do not condemn it until it is released. If you do not like it then, condemn it but perhaps respect it as a free software project. ;)

Cheers to everyone trying to keep this thread mainly flame free, though it was mainly intended to be about 2.30 not 2.32/3.0


Exactly
thankyou

---

### Post by skooter1121 on 2010-04-03
Will 2.30 be included in the Update Manager?

If so any idea when?

running 9.10 now.

-THANX

---

### Post by Psumi on 2010-04-03
> **skooter1121 said:**
> Will 2.30 be included in the Update Manager?

If so any idea when?

running 9.10 now.

-THANX

No, it won't be.

---

### Post by chris4585 on 2010-04-03
I'm running Ubuntu 10.04 beta and Gnome 2.30 on my laptop and I'm lovin' it.  Thats great news about being able to switch to the 'legacy' desktop.

---

