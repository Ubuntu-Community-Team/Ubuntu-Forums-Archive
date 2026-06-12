---
title: "If the dash/overview was the default view Gnome 3 would be much better!"
date: 2012-10-01
forum: The Cafe
---

### Post by x-shaney-x on 2012-10-01
If the dash/overview was the default view.

Does anyone know of any way to make this possible?

By default, one has to perform an action (moving the pointer to the top left corner or maybe a hotkey) before they can do anything.

Open the overview THEN search for an app.
Open the overview THEN click on a launcher in the favourites bar.

This has always been an issue for me with Gnome 3 and the main reason I have avoided it in the past.

It would be better if the desktop loaded up and the overview was there, ready and waiting.
You could just start typing straight away to search for an app or just go straight to your web browser or whatever instead of having to go up and left then down to the favourites bar.

When apps are open you would still go top left to go to overview and when all apps are closed, you would be back at the overview ready to do more work.

Why oh why isn't it like this by default and how can I make it so?

---

### Post by cecilpierce on 2012-10-01
I agree, and every time of an update all the extensions stop working...:mad:

---

### Post by @nne on 2012-10-01
If you mean that the dash should show permanently, Unity does that, doesn't it? :)

---

### Post by x-shaney-x on 2012-10-01
Partially but I can no longer use unity (for reasons I won't go into here) so will be switching to Gnome 3 in some form (ubuntu or otherwise) and I don't really understand the point of having an empty desktop when they could have the overview there all the time.

---

### Post by Mr. Picklesworth on 2012-10-01
I agree, and I'm curious why it is the way it is. There might be a clever reason. Maybe you could ask on [the gnome-design IRC channel]("https://live.gnome.org/GnomeIrcChannels")? :)

---

### Post by x-shaney-x on 2012-10-01
> **Mr. Picklesworth said:**
> I agree, and I'm curious why it is the way it is. There might be a clever reason. Maybe you could ask on [the gnome-design IRC channel]("https://live.gnome.org/GnomeIrcChannels")? :)


Well I gave it a go (haven't used IRC in years and got a bit confused).
Apparently, it is mainly down to technical reasons, such as keybindings not working in overview mode, which is being worked on.
So it could become a reality in time, hopefully not too much time though.

---

### Post by alexfish on 2012-10-01
Not sure if 3's load has been lightened to good effect.

IE:

 can it bridge the gap between Desktop 32 and 64 bit to arm ,
 is nautilus as much dependent on gnome , as gnome is to nautilus , is there an alternate compatible lightweight file browser ???

I had a quick look at the Wiki ,no mention to these pointers

If can't bridge the gaps then as far as everyday users are concerned then Gnome 3 has no meaning , except for a development platform. That could be it's + side.

If passed history serves me correct , do they still listen to suggestion. Simple things have often gone straight into deep thought , as in Hitch-hikers guide to the galaxy .

---

### Post by Mr. Picklesworth on 2012-10-01
> **x-shaney-x said:**
> Well I gave it a go (haven't used IRC in years and got a bit confused).
Apparently, it is mainly down to technical reasons, such as keybindings not working in overview mode, which is being worked on.
So it could become a reality in time, hopefully not too much time though.

Neat! Thanks for passing that on.

> **alexfish said:**
> Not sure if 3's load has been lightened to good effect.

IE:

 can it bridge the gap between Desktop 32 and 64 bit to arm ,
 is nautilus as much dependent on gnome , as gnome is to nautilus , is there an alternate compatible lightweight file browser ???

As far as I have noticed, GNOME 3 &#8212; especially with GNOME Shell &#8212; has a vastly improved start time. Quite a lot of work has contributed to this, actually. One thing that helps is the move from gconf to gsettings with the dconf storage backend. dconf is very good at reading a whole lot of config keys, for example at startup. In addition, the dependency on Nautilus is quite minimal. There is no desktop icon thing (by default), so Nautilus is really just an application you use to look at files and folders. There is also much improved autorun (where gnome-session knows which programs can wait for a while before being started, as well as which programs don't need to be started at all), and of course there are far fewer unique processes trying to talk to each other in order to create your desktop shell, which should help a little with overhead.

---

### Post by critin on 2012-10-01
> **x-shaney-x said:**
>  I don't really understand the point of having an empty desktop when they could have the overview there all the time.

I'm so grateful it isn't open all the time.  I'd much rather see my desktop change backgrounds while I'm working.   :p

---

### Post by @nne on 2012-10-02
> **x-shaney-x said:**
> Partially but I can no longer use unity (for reasons I won't go into here) so will be switching to Gnome 3 in some form (ubuntu or otherwise) and I don't really understand the point of having an empty desktop when they could have the overview there all the time.
I do see the point and I'm glad they did it that way. Anyway, if you want all sort of icons on your desktop, you can do it by turning "Have file manager handle the desktop" on in the Tweaks tool, "Desktop" tab. :)

---

### Post by Copper Bezel on 2012-10-02
As a big fan of Shell, I agree with x-shaney-x, and it's something I noticed early on. It's nothing to do with Unity or desktop icons - the overview is like Android's home screen or Win 8's Start screen, and it ought to be the default fallback place to be. Partly because it *is*, but inconsistently. 

At first, I did find t odd that when the last window on a workspace is closed, I drop back to the Overview. I got it, though, when I realised that the Overview just is the place you "fall back" to. So then it became odd that this doesn't apply to the moment I log in - naturally, the first thing I'm going to do is launch something - and why I can select an empty workspace at all.

I don't buy the argument about a clean desktop. I want my desktop clean so crap isn't hidden under my windows, or competing for my attention with non-maxed windows, not so that I can stare at my pretty wallpaper. I also want to access my stuff as efficiently as possible. So the default position when nothing is running ought to be the place I keep my stuff. (This is not the same thing as the overlappity mish-mash of the Win XP-Gnome 2 way of doing things, so please don't think I'm getting nostalgic, though I suppose it's no different from combining the benefits of desktop icons with the interaction mode of the Start menu, which is exactly what Win 8 does, although Shell also tosses in window management.)

But truth be told, I'd settle for a fix to the first problem, that key bindings don't work in the Overview.

---

### Post by handy on 2012-10-02
Using Openbox as its WM would certainly sort out Gnome 3's inherent problems!

---

### Post by kevinmchapman on 2012-10-02
> **handy said:**
> Using Openbox as its WM would certainly sort out Gnome 3's inherent problems!

Not sure it would. My main complaint in Gnome Shell is the window manager window placement. It lacks a "smart" placement setting like Xfce and E17 (ie. non-full-size windows being placed as far apart as possible to avoid overlap). Good as Openbox is, it lacks exactly that feature.

Maybe I've missed the point, but what else does Openbox offer over Mutter, bar a few keybindings?

---

### Post by TeamRocket1233c on 2012-10-03
There's also adding a taskbar to GNOME 3, as well as a start menu, as well as other tweaks to improve the DE's usability.

---

### Post by x-shaney-x on 2012-10-03
> **TeamRocket1233c said:**
> There's also adding a taskbar to GNOME 3, as well as a start menu, as well as other tweaks to improve the DE's usability.

Those can all be done easily via extensions :-)

---

### Post by kevinmchapman on 2012-10-03
> **TeamRocket1233c said:**
> There's also adding a taskbar to GNOME 3, as well as a start menu, as well as other tweaks to improve the DE's usability.

So when you say "improve the DE's usability", you really mean "make it like the Gnome2 I got used to"

---

### Post by pelle.k on 2012-10-03
> **kevinmchapman said:**
> Not sure it would. My main complaint in Gnome Shell is the window manager window placement. It lacks a "smart" placement setting like Xfce and E17 (ie. non-full-size windows being placed as far apart as possible to avoid overlap). Good as Openbox is, it lacks exactly that feature.

Maybe I've missed the point, but what else does Openbox offer over Mutter, bar a few keybindings?

Hurray! Great minds think alike! Compiz and kwin also has "smart" window placement (and quite a few more window placement modes). Cascading is sooo 1999. Why would i want all my windows to default to the upper left corner on my gigantic super widescreen desktop monitor.. :/
That said, mutter is super smooth (YMMV, it's been for me at least), much more so than any other composite window manager with "animations" and such (if that's your cup of tea), and it wouldn't surprise me if window placement is scriptable through an extension or such in the near future. That seems to be gnome-shells biggest strength. Smoothness and scriptability.

---

### Post by TeamRocket1233c on 2012-10-05
> **kevinmchapman said:**
> So when you say "improve the DE's usability", you really mean "make it like the Gnome2 I got used to"

Pretty much.  :lol:

---

### Post by alexfish on 2012-10-05
Using a system is about how you can control it as a user , put bindings and protocol to which defies logic is no way forward.

Gnome. print 1+1=

if x=y then d = Pix_might_do_if pix_will_not_do_if pix_can_not_do_then_do_not_pix
else 
If at_the_end_of_all_that_then if  gnome 1+1 = 3
see help: on how to get a result,

30 pages into help, refer to help , page 194560

paragraph 20456, line 563024......

what a way to use a system , bog it down in crap protocol , no normal logical person will entertain having to write 20 meanings which can have 20 different outcomes, if in simple terms all you want to do is "print 1+1 =2"

---

### Post by Chdslv on 2012-10-05
The simplest thing is to open Nautilus, navigate to /usr/share/applications and keep that window open or minimized. All your applications are there, just a click away. You can't delete any icon from that, if you are not root, so you have **the simplest scrollable menu.** You can have it any way you like, full screen, half screen...;)

The same with PCmanFM, Thunar, Nemo, or any other file-manager.

---

### Post by Chdslv on 2012-10-05
Here is the screenshot with Nemo at work...

---

### Post by alexfish on 2012-10-05
```
alexfish@alexfish-desktop:~$ cd /usr/share/applications
alexfish@alexfish-desktop:/usr/share/applications$ ls
acidrip.desktop
alacarte.desktop
apport-gtk-mime.desktop
apturl.desktop
aqemu.desktop
arista.desktop
at-properties.desktop
avidemux-gtk.desktop
bamf.index
banshee-audiocd.desktop
banshee.desktop
banshee-media-player.desktop
baobab.desktop
blender-fullscreen.desktop
blender-windowed.desktop
bluefish.desktop
bluetooth-properties.desktop
brasero.desktop
brasero-nautilus.desktop
ccsm.desktop
checkbox-gtk.desktop
chromium-browser.desktop
compiz.desktop
computer-janitor-gtk.desktop
dconf-editor.desktop
default-applications.desktop
defaults.list
desktop.en_GB.UTF8.cache
devhelp.desktop
dfeet.desktop
display-properties.desktop
djvulibre-djview4.desktop
dooble.desktop
dvdrip.desktop
empathy-accounts.desktop
empathy.desktop
eog.desktop
evince.desktop
evolution-2.2.desktop
evolution.desktop
evolution-mail.desktop
evolution-settings.desktop
faum.desktop
file-roller.desktop
firefox.desktop
fluid.desktop
foff.desktop
gambas2.desktop
gbrainy.desktop
gcalctool.desktop
gcolor2.desktop
gconf-editor.desktop
gdm-guest-session.desktop
gdmsetup.desktop
gedit.desktop
gimp.desktop
gksu.desktop
glade-3.desktop
gmenu-simple-editor.desktop
gnome-about.desktop
gnome-about-me.desktop
gnome-appearance-properties.desktop
gnomecc.desktop
gnome-font-viewer.desktop
gnome-nettool.desktop
gnome-network-properties.desktop
gnome-panel.desktop
gnome-power-preferences.desktop
gnome-screensaver-preferences.desktop
gnome-screenshot.desktop
gnome-search-tool.desktop
gnome-settings-mouse.desktop
gnome-sound-recorder.desktop
gnome-sudoku.desktop
gnome-system-log.desktop
gnome-system-monitor.desktop
gnome-terminal.desktop
gnome-theme-installer.desktop
gnome-user-share-properties.desktop
gnome-volume-control.desktop
gnome-wm.desktop
gnomine.desktop
gnucash.desktop
Gorm.desktop
gparted.desktop
gpppon.desktop
gstreamer-properties.desktop
gucharmap.desktop
gwibber-accounts.desktop
gwibber.desktop
gwibber-preferences.desktop
gworldclock.desktop
hplj1020.desktop
ibus-setup.desktop
icedtea-netx-javaws.desktop
imagination.desktop
im-switch.desktop
indicator-datetime-preferences.desktop
inkscape.desktop
itweb-settings.desktop
jockey-gtk.desktop
kde
kde4
keybinding.desktop
keyboard.desktop
kompozer.desktop
ktoon.desktop
language-selector.desktop
latexdraw.desktop
lazarus.desktop
libreoffice-base.desktop
libreoffice-calc.desktop
libreoffice-draw.desktop
libreoffice-impress.desktop
libreoffice-math.desktop
libreoffice-startcenter.desktop
libreoffice-writer.desktop
luakit.desktop
mahjongg.desktop
metacity.desktop
mimeinfo.cache
moserial.desktop
mount-archive.desktop
mtpaint.desktop
nautilus-autorun-software.desktop
nautilus-browser.desktop
nautilus-computer.desktop
nautilus.desktop
nautilus-file-management-properties.desktop
nautilus-folder-handler.desktop
nautilus-home.desktop
network-scheme.desktop
nm-connection-editor.desktop
octave3.2.desktop
ogmrip.desktop
onboard.desktop
onboard-settings.desktop
openjdk-6-java.desktop
openjdk-6-policytool.desktop
openshot.desktop
orca.desktop
padevchooser.desktop
padre.desktop
palimpsest.desktop
paman.desktop
paprefs.desktop
pavucontrol.desktop
pavumeter.desktop
pavumeter-record.desktop
pdfedit.desktop
pencil.desktop
pitivi.desktop
podbrowser.desktop
poedit.desktop
ProjectCenter.desktop
python2.6.desktop
python2.7.desktop
rootstock.desktop
screensavers
seahorse.desktop
seahorse-pgp-encrypted.desktop
seahorse-pgp-keys.desktop
seahorse-pgp-preferences.desktop
seahorse-pgp-signature.desktop
seamonkey-addressbook.desktop
seamonkey-composer.desktop
seamonkey.desktop
seamonkey-mail-compose.desktop
seamonkey-mailnews.desktop
seamonkey-navigator.desktop
session-properties.desktop
shares.desktop
shoes.desktop
shotwell.desktop
shotwell-viewer.desktop
shutter.desktop
simple-scan.desktop
skencil.desktop
software-properties-gtk.desktop
sol.desktop
sqliteman.desktop
stopwatch.desktop
synaptic.desktop
synaptic-kde.desktop
system-config-printer.desktop
testdrive-gtk.desktop
thoggen.desktop
thunderbird.desktop
tkgate.desktop
tomboy.desktop
totem.desktop
transmission-gtk.desktop
treeline.desktop
tsclient.desktop
ubuntu-about.desktop
ubuntu-nvidia-settings.desktop
ubuntuone-control-panel-gtk.desktop
ubuntu-software-center.desktop
unity-preferences.desktop
update-manager.desktop
usb-creator-gtk.desktop
users.desktop
vinagre.desktop
vinagre-file.desktop
vino-preferences.desktop
virtualbox-ose.desktop
vlc.desktop
wammu.desktop
window-properties.desktop
wine-browsedrive.desktop
wine.desktop
wine-notepad.desktop
wine-uninstaller.desktop
wine-winecfg.desktop
wine-winetricks.desktop
winff.desktop
winpdb.desktop
wxformbuilder.desktop
xaralx.desktop
xine.desktop
xmlcopyeditor.desktop
yelp.desktop
alexfish@alexfish-desktop:/usr/share/applications$ 
```

I know what most of this means , do you

regards

alexfish

---

### Post by litiform on 2012-10-12
> **x-shaney-x said:**
> If the dash/overview was the default view.

Does anyone know of any way to make this possible?

By default, one has to perform an action (moving the pointer to the top left corner or maybe a hotkey) before they can do anything.

Open the overview THEN search for an app.
Open the overview THEN click on a launcher in the favourites bar.
?

Yeah, is a problem with Gnome. I love Unity Launcher to much to leave Ubuntu.

---

### Post by x-shaney-x on 2012-10-12
There is a gnome shell extension I have started using called "dash-to-dock" which gives a permanent launcher on the desktop.
Unlike the "dock" extensions, this replaces the overview dock, rather than having one for the desktop and another for the overview.
Not only that, it comes complete with the "dodge" intellihide feature ripped out of unity last release.

It solves part of the problem I mentioned and this extension alone has made up my mind once and for all to drop unity completely and go the gnome shell route.

---

