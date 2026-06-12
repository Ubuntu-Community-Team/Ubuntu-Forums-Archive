---
title: "HowTo: theme your desktop"
date: 2006-06-24
forum: Tutorials
---

### Post by Nonno Bassotto on 2006-06-24
In this HowTo I just want to collect the different ways you can personalize your desktop. It is divided in different sections; you don't need to follow everything I say, just pick up what you like. There's nothing new amongst the things I say, but I thought it would be handy to have a reference. Another useful reference is [this]("http://ubuntuforums.org/showthread.php?t=77694"). All I know, I've learned it on this forum, but I'm not able to trace back the authors of the original posts. If you think I've just reported something you explained first, then you're probably right, and I thank you for this. Throughout the guide I assume you are using Gnome.

[SIZE="3"][COLOR="Green"]1: What can be skinned[/COLOR][/SIZE]

A lot of things, actually. In this HowTo I will cover:
- Widgets: this are the little elements like buttons, loading bars, menus..., which are used in your applications
- Window borders: the part of the window containing the buttons to close, maximize and minimize
- Icons
- Mouse cursors
- Panels
- Splash screen: this appears when you login before the desktop os ready
- Login manager: the application which greets you after the boot
- Desklets: little apps which show useful information over your desktop
- Fonts
- Grub: the application which lets you choose what operating system you want to boot
- Usplash: what appears when the system is loading at boot

[SIZE="3"][COLOR="Green"]2: Where to find nice themes[/COLOR][/SIZE]

The most common sites where you can find themes for Gnome are [GnomeArt]("http://art.gnome.org") and [Gnome-Look]("http://www.gnome-look.org")
Some other fancy stuff (for example wallpapers) can be found at [Deviant Art]("http://www.deviantart.com")
You may also want to have a look at [Gnome Themes]("http://kwh.kernow-gb.com/~bvc/wp/") and  [Gnome Themes Forum]("http://gnomethemes.org/forum/").

If you know where to find themes, but want some advice on putting all together in a consistent way, have a look [here]("http://www.ubuntuforums.org/showthread.php?t=184150"). That thread is meant to show other people some screenshots and list the themes used to make it. If you get some nice theme, then share it on that thread.

[SIZE="3"][COLOR="Green"]3: Icons, windows, widgets and wallpaper[/COLOR][/SIZE]

The most basic things which characterize the look of your desktop are widgets, window borders and icons. These elements can be managed under
[COLOR="Blue"]System->Preferences->Themes[/COLOR] or equivalently launching
```

gnome-theme-manager

```
in a terminal. You can install here the icons etc. that you have downloaded. Then you choose the elements you will actually use under Theme Details. When you are happy with your settings, you can save your theme, to be able to recall it with a click if you change it.

It may be useful to know where things actually go: icons are stores under [COLOR="Red"]~/.icons[/COLOR], while other elements can be found under [COLOR="Red"]~/.themes[/COLOR].

If you want to install themes system-wide, then you can just invoke the application as root, with
```

sudo gnome-theme-manager

```
Be sure to do this only to install things, and make your choices as a regular user.

Sometimes you may want to change a single icon. You can do this by right-clicking your file and choosing properties. Then click over the icon image and choose a new one. This is useful for special folders, also. Under the [COLOR="Blue"]Symbols[/COLOR] tab you can choose some little emblems and add it to the icon.

[[IMG]http://img350.imageshack.us/img350/8120/icon7us.png[/IMG]](http://imageshack.us) 

==========================================================

Finally, the last element which characterizes your desktop is of course the wallpaper. You can change it using [COLOR="Blue"]System->Preferences->Wallpaper[/COLOR] or equivalently right-clicking on the current wallpaper and choosing "Set wallpaper".

Just an advice here. It is tempting to choose a very beautiful picture or a photo of your family or whatever else, and to change wallpaper frequently. I discourage this, because it will easily lead to an inconsistent theme. Choose your wallpaper as the last thing while themeing, and be sure to use a simple image with few colors, which match your widgets or your window borders. The result will be much more satisfying.

[SIZE="3"][COLOR="Green"]4: Some applications still look bad.[/COLOR][/SIZE]

You're right. There are three kind of applications which will use different widgets and icons.

[COLOR="Sienna"]Root[/COLOR]. The simplest to settle are applications which you run as root. These simply use the root theme. If you want the root theme to match the current user theme, you can just create some symbolic links
```

sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts

```

==========================================================

[COLOR="Sienna"]Qt[/COLOR] Then there are KDE applications. These apps use a different set of widgets, based on the QT graphic libraries, rather than the GTK (GIMP ToolKit) based, which are common on Gnome. The first thing to do is to find a matching QT theme; for this you can have a look [here]("http://www.kde-look.org"). Some themes are also available in the repos, but they may require you to install KDE as well. If you just want to make the apps look nice, but don't want much hassle with theme installation, and you don't care about theme matching, you can find [here]("http://ubuntuforums.org/showthread.php?t=76633") a deb to install Polymer theme, which is quite nice.

After you have installed the theme (the way to do this depends on the theme, and is usually indicated on the site) you have to set it as default. If you have KDE installed you can do this under the K Control Center. Otherwise you can install qtconfig
```

sudo apt-get install qt3-qtconfig qt4-qtconfig

```
You will find two entries under System->Preferences->Qt3 Configuration (or Qt4 of course). You just have to select the right theme (both under Qt3 and Qt4) and the right font. If you use the standard font, then you can choose Bitstream Vera Sans, normal, 10 under the font tab.

==========================================================

[COLOR="Sienna"]Gtk1[/COLOR] Finally there applications which use the old version of the Gtk libraries. You will hardly be able to make them look good, because there are no nice themes for Gtk1. Anyway have a look [here]("http://ubuntuforums.org/showthread.php?t=107135").

[SIZE="3"][COLOR="Green"]5: Panels[/COLOR][/SIZE]

You can play with panels to achieve a more comfortable setting, or just to make your box look like OSX. I will first explain how to customize the standard panels. If you want a OSX-like launcher, you find it in the next paragraph.

By default you should have two panels, one at the top, the other at the bottom. To create a new panel or delete one, you can just right-click on the panel. Under the [COLOR="Blue"]properties[/COLOR] you can also set the position of your panel and its height. If you plan to make a panel with a lot of launchers you may want to make it about 48 high.

Under [COLOR="Blue"]Properties[/COLOR] you can also choose some other things: you may set it to hide automatically your panel or to make it a bit transparent. If your panel doesn't hide correctly, then you have to edit the panel configuration. To do this run
```

gconf-editor

```
or equivalently [COLOR="Blue"]Applications->Administration->Configuration Editor[/COLOR]. Navigate to [COLOR="Red"]/apps/panel/toplevels/top_panel_screen0[/COLOR] and there modify the value of auto_hide_size to 0. Replace top_panel_screen0 with another panel, according to which panel you want to minimize.

Now you can add things to your panels or take them off, again by right-clicking. You can move things on the panel by right-clicking on them; if you are not able to move something past an object, probably that object is locked to the panel (again you can lock or unlock things on the panel with the right-click menu).

At this point you should be able to move things on the panel. For some settings you may like to move the area where your open windows show to the upper panel. You can do this by right-clicking on the upper panel, selecting Add to panel, and then choosing [COLOR="Blue"]Window List[/COLOR]. Be sure to stretch its sides until you feel it is big enough for your needs. If you have some windows open, but still the whole space you reserved is not filled, just don't care, it is a bug in the gnome panel. However the whole area should be filled if you have enough windows open. Now you can delete the Window List on the lower panel. The same can be done with the [COLOR="Blue"]Notification Area[/COLOR], which is the area with the little icons like the network status.

Many people will want to put the window list and the notification area on the upper panel and launchers for the most common applications on the lower (maybe 48 high and with autohide). If you want a panel which does not extend to the borders then you just need to uncheck the expand button in the panel Properties. However it can be nice to have smooth corners in that case (see this [mockup]("http://www.gnome-look.org/content/preview.php?preview=1&id=31128&file1=31128-1.jpg&file2=31128-2.jpg&file3=31128-3.jpg&name=Gentle+Gnome+mockup")). For this you can use a trick: under [COLOR="Blue"]Properties[/COLOR] choose a [COLOR="Blue"]Background image[/COLOR], and put a fake image of a centered panel (you can find one in the gentle theme on [Gnome Themes]("http://kwh.kernow-gb.com/~bvc/wp/")).

[SIZE="3"][COLOR="Green"]6: Desklets[/COLOR][/SIZE]

What if you want an OSX-like bar, with the icons stretching when you pass over with your mouse? 

[[IMG]http://img381.imageshack.us/img381/9991/osxbar2yq.png[/IMG]](http://imageshack.us) 

The most common way to do this in Gnome is to use gDesklets. You can install it with
```

sudo apt-get install gdesklets

```
Then you will find the program under [COLOR="Blue"]Applications->Accessories[/COLOR]. From there you can add a lot of desklets: these are little programs that show over your desktop. The one which will make the OSX-launcher is StarterBar. But you can use a lot of other goodies from there: clocks, disk infos, memory infos, wheather forecasts and whatever else.

[[IMG]http://img70.imageshack.us/img70/8981/clock4qf.png[/IMG]](http://imageshack.us)

A lot of the desklets which are bundled in the repos are broken. To find new desklets or new versions of the ones you have, you can browse both [here]("http://gdesklets.gnomedesktop.org") or [here]("http://gdesklets.org"). When you have downloaded a desklets you can install it with gDesklets manager under the File Menu. The gDesklets symbol should appear in the Notification Area: right-clicking on it you get both the gDesklets manager and the configuration. From the latter you can set a shortcut to put the desklets in front of you windows. Be warned that the desklets will not be transparent, so the visual effect is horrible. You can set the desklets to be transparent from here, but you need a composite manager (see the last paragraph) to make it work (and it seems it not working however).

Finally you will want gDesklets to load at the login. To do this open [COLOR="Blue"]System->Preferences->Sessions[/COLOR], choose the tab [COLOR="Blue"]Program Start[/COLOR] and there add "gdesklets".

If you often change theme, you may want to change the desklets accordingly (for example you may choose other icons on the StarterBar). To be sure not to lose your work, look at the gDesklets manager profiles menu and use a different profile for each theme.

[SIZE="3"][COLOR="Green"]7: Cursors[/COLOR][/SIZE]

The next thing you may want to change is your mouse cursors. You can do this under
[COLOR="Blue"]System->Preferences->Mouse[/COLOR] under the [COLOR="Blue"]cursors[/COLOR] tab. Still you can't add new cursor themes here, so you basically have two ways.

The simplest is to install gcursor, which is in the repositories
```

sudo apt-get install gcursor

```
It will show up under [COLOR="Blue"]System->Preferences->Cursor Selection[/COLOR] and it lets install new cursors. It is quite strange, but it doesn't let you delete themes, so you have to manually remove cursors themes, which are stored under [COLOR="Red"]~/.icons[/COLOR].

The fact that cursors are stored in the same folder as icons can be annoying, because cursor themes will show up under the icon themes settings. Yet this can be useful to remove cursors (just the same way you'd remove icon themes), even if is not intuitive to do.

The second way to install cursors is, as you can now guess to unzip the theme, which usually will be a tar.gz file, under [COLOR="Red"]~/.icons[/COLOR].

[SIZE="3"][COLOR="Green"]8: Splash screen and login manager[/COLOR][/SIZE]

The login manager (GDM) is, of course, the same for all users, so you can change it only as root. You can set it under [COLOR="Blue"]System->Administration->Login Window[/COLOR] and here you can add themes, and choose the one which will be used. You can also choose to pick one of the themes installed at random.

The splash screen needs an external utility, so install gnome-splashscreen-manager
```

sudo apt-get install gnome-splashscreen-manager

```
Then you will find the settings you need under [COLOR="Blue"]System->Preferences->Splash Screen[/COLOR]. Since the splash is a little centered image, you may want to change the background color to match it. you can do this as root under [COLOR="Blue"]System->Administration->Login Window[/COLOR].

[SIZE="3"][COLOR="Green"]9: Fonts[/COLOR][/SIZE]

I don't think there is any need to change Gnome fonts, since they look so good! Anyway you can choose fonts under [COLOR="Blue"]System->Preferences->Font Types[/COLOR]. The default is Bistream Vera Sans 10.

But you may want to have a better-looking antialias of the font. You can find [here]("http://ubuntuforums.org/showthread.php?t=180647") some patched deb files. You just have to install them (you can do this double-clicking on them) to have better looking fonts. Then go under [COLOR="Blue"]System->Preferences->Font Types[/COLOR] and choose the LCD option if your screen is LCD. You won't be able to look at ugly no antialiased fonts anymore!!
Here is the comparison.

Before [[IMG]http://img504.imageshack.us/img504/1786/before7xh.png[/IMG]](http://imageshack.us)

After [[IMG]http://img473.imageshack.us/img473/3994/after4ql.png[/IMG]](http://imageshack.us)

[SIZE="3"][COLOR="Green"]10: Grub and USplash[/COLOR][/SIZE]

First, let me put here a disclaimer. Grub and USplash are loaded at boot, so if you mess them up and are not able to boot anymore, don't hold me responsible. If you fear to modify them, then don't.

Now, let's begin with USplash. You may want to modify its appearance, but I have to warn you that you won't get cool boot splashes with it. The reason is that the only images allowed are 640x480 with 16 colors. The reason for this restriction is that other solutions may give problem with the suspend/hybernate feature (have a look [here]("http://ubuntuforums.org/showthread.php?t=46687") and the links there). The simplest way to change USplash look is to take another theme, but I only know two themes: [Ubuntu Serengeti]("http://ubuntuforums.org/showthread.php?t=185538") and [Ubuntu Minimalistic]("http://ubuntuforums.org/showpost.php?p=1013184&postcount=13") (no text). Follow the instuctions in the threads to install.

If you are not happy with this themes, you can follow this [tutorial]("https://wiki.ubuntu.com/USplashCustomizationHowto") on how to create your own, but it's hard to get really nice-looking themes.

So you may consider to change the program which displays the splash at bootup. The main alternatives are [Splashy]("http://ubuntuforums.org/showthread.php?t=41709") (Debian default) and [FBSplash]("http://ubuntuforums.org/showthread.php?t=178439") (Gentoo default). FBSplash is better looking and has more themes (it supports bootsplash [themes]("http://www.bootsplash.de/files/themes/"), and there are quite a lot), but you'll have to recompile the kernel in order to install it.

==========================================================

Now, let's change Grub image. Make sure you have at least one image (there are some in /boot/grub/splashimages). You can download other images (in xpm.gz format), for example on Gnome-look, and then put them in [COLOR="Red"]/boot/grub/splashimages[/COLOR] typing
```

sudo cp PathToYourFile /boot/grub/splashimages

```

Second, you have to understand under what partition is mounted your [COLOR="Red"]/boot[/COLOR] folder and translate this in grub partition naming. Usually you refer to you partitions as hda1, hda2, hdb1 and so on. The letter refers to the drive ("a" first hard disk, "b" second...), while the progressive number to the partition on the drive. To find out where [COLOR="Red"]/boot[/COLOR] is located open [COLOR="Blue"]System->Administration->Drives[/COLOR] and open the [COLOR="Blue"]Partitions[/COLOR] tab. If you have a separate [COLOR="Red"]/boot[/COLOR] partition, then find which partition has [COLOR="Red"]/boot[/COLOR] as a mount point and look under Peripheals for its name. If you don't have one, just find which partition has / as a mount point.

Now translate this name using Grub conventions. Grub names the first drive with a 0, the second with 1 and so on; the same with the partitions. So hda1 becomes (hd0,0), hda2 becomes (hd0,1), hdb1 becomes (hd1,0) and so on.

To make Grub display a image you'll have to open its configuration file as root
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_old
sudo gedit /boot/grub/menu.lst

```
Then add this line just after the comments at the beginning
```

splashimage=(hd?,?)/boot/grub/splashimages/NameOfTheImage.xpm.gz

```
where of course you have to change (hd?,?) to the partition you found in the preceding step and NameOfTheImage to the actual name of the image. If you have a separate [COLOR="Red"]/boot[/COLOR] partition, then (hd?,?) already refers to [COLOR="Red"]/boot[/COLOR], so change the line to
```

splashimage=(hd?,?)/grub/splashimages/NameOfTheImage.xpm.gz

```
This way your first lines will look something like
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
splashimage=(hd0,1)/boot/grub/splashimages/ubuntu_mark1.xpm.gz

```

If you want to be sure you have correctly understood grub naming scheme, have a look towards the end of menu.lst. You will see something like
```

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

```
The partition listed after root should be the same you have found by the method before, and if you have a separate [COLOR="Red"]/boot[/COLOR] partition, then [COLOR="Red"]/boot[/COLOR] should not appear after kernel and after initrd.

Finally you can save the file and exit. Hopefully you will get your image at next reboot. If you have problems you can restore Grub configuration by typing
```

sudo cp /boot/grub/menu.lst_old /boot/grub/menu.lst

```

==========================================================

The last thing you may want to change is the screen resolution and number of colors while USplash is running. Remember that USplash doesn't use too many colors or a high resolution, so you won't see better colors and the image will only be smaller. 

If however you want to do this, then choose your resolution and number of colors and transform it into a number according to this table.
```

      color           depth   | 640x480  800x600  1024x768 1280x1024

      256             (8bit)  |  769      771       773      775
      32000           (15bit) |  784      787       790      793
      65000           (16bit) |  785      788       791      794
      16.7 Mill.      (24bit) |  786      789       792      795

```

Open again Grub configuration file
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_old
sudo gedit /boot/grub/menu.lst

```
and locate the stanza relative to the kernel you use (it will look something like this)
```

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

```
Then add
```

vga=YourNumber

```
at the end of the "kernel" line, save the file and you're done.

[SIZE="3"][COLOR="Green"]11: Skinnable applications[/COLOR][/SIZE]

Some applications don't use Gnome widgets, but have their own instead; in this case they can often be skinned independently. We cover here how to do it; in most cases you only have to copy the new skins to a Skin directory, so this section aim is mainly to link sites where themes can be found.

==========================================================

[COLOR="Sienna"]Firefox[/COLOR]. Not much to say here. Firefox themes can be managed under [COLOR="Blue"]Tools->Themes[/COLOR]: here you can select the theme you wish to use (you'll have to restart Firefox), uninstall and ungrade installed themes. If you click on [COLOR="Blue"]Download other themes[/COLOR] Firefox will open [this site]("https://addons.mozilla.org/themes.php?"), where you can look for new skins.

==========================================================

[COLOR="Sienna"]Xmms, Beep media player, BmpX, Audacious[/COLOR]. These all share the same skins, which were originally designed for Winamp 2.0. You can look for skins on [XMMS Skins]("http://www.xmms.org/skins.php"), [Freshmeat]("http://themes.freshmeat.net/browse/966/"), [Gnome-look]("http://www.gnome-look.org/?xcontentmode=130"), [Winamp skins]("http://www.winamp.com/skins/"), [Customize.org]("http://www.customize.org/list/winamp2"), [Skinz.org]("http://skinz.org/skins.phtml?category=21"). Skins will usually be compressed, in .zip, .wsz or .tar.gz format.

To install them just means to copy the files in the Skins directory. For example for BMP
```

cp PathToYourSkin /home/YourUsername/.bmp/Skins

```
For a system-wide install just copy the same file under the program folder; for example on BMP
```

sudo cp PathToYourSkin /usr/share/bmp/Skins

```
You will then be able to select the skin under the [COLOR="Blue"]Preferences[/COLOR] in your application.

==========================================================

[COLOR="Sienna"]MPlayer[/COLOR]. Skins can be downloaded on MPlayer official [Mplayer]("http://www.mplayerhq.hu/design7/dload.html#skins") in tar.bz2 format. To install a theme, just extract the file and copy the output directory in the Skins directory (create it if doesn't exist).Assuming the skin is under your home
```

tar -jxvf /home/YourUsername/NameOfTheSkin.tar.bz2
cp -r /home/YourUsername/NameOfTheSkin /home/YourUsername/.mplayer/Skin

```
For a system-wide install just copy the same file under the program folder
```

tar -jxvf /home/YourUsername/NameOfTheSkin.tar.bz2
cp -r /home/YourUsername/NameOfTheSkin /usr/share/mplayer/Skin

```
To select the skin right-click on MPlayer and choose [COLOR="Blue"]Skin Browser[/COLOR].

==========================================================

[COLOR="Sienna"]aMSN[/COLOR]. This is a little more complex. By default aMSN uses a Tcl/Tk interface without antialiased fonts. I'll explain here the simple way (that is, using precompiled packages) to beautify aMSN. If you want to do it the hard way (but it seems with better results, I haven't tried myself so I can't tell), follow this [thread]("http://www.ubuntuforums.org/showthread.php?t=84765") instead.

Let's start from the beginning. Skins can be found [here]("http://amsn.sourceforge.net/skins.php"). If you want to install the skins manually, just extract them and copy the directories under [COLOR="Red"]~/.amsn/skins[/COLOR] (or [COLOR="Red"]/usr/share/amsn/skins[/COLOR] for system-wide install) like for the previous apps; this is not the simplest way to go. On [this thread]("http://ubuntuforums.org/showthread.php?t=87001") you will find a deb package which contains all the skins (just double click on it to install).

The same [thread]("http://ubuntuforums.org/showthread.php?t=87001") contains packages for the latest Tcl/Tk and aMSN with antialiased fonts, so I advice you to install the debs from there. You will need to install from there the plugins package too. Otherwise plugins can be found [here]("http://amsn.sourceforge.net/plugins.php"), except for the Chameleon package, which is [here]("http://amsn.sourceforge.net/kakaroto/Chameleon"). If you want to install the plugins manually, just extract them and copy the directories under [COLOR="Red"]~/.amsn/plugins[/COLOR] (or [COLOR="Red"]/usr/share/amsn/plugins[/COLOR] for system-wide install).

Assuming you have plugins and skins installed either way, let's open aMSN. Under [COLOR="Blue"]Tools->Select Skin[/COLOR] you will be able to select the skin (what else?). Then open [COLOR="Blue"]Tools->Select Plugins[/COLOR], because some plugins actually change aMSN look. The first plugin you'll want to load is Desktop Integration: this allows aMSN to display dialogs using the OS native interface (in our case it will display Gnome dialogs). Second, load Chameleon: this plugin changes the widgets in use with aMSN configuration dialogs. You can configure it use some different sets of widgets, choose the one that fits your desktop best.

Finally open [COLOR="Blue"]Tools->Preferences[/COLOR], choose the [COLOR="Blue"]Interface[/COLOR] tab and click [COLOR="Blue"]Change Fonts[/COLOR] to choose the fonts in use for the chat window (if you want them to match the default system fonts, then choose Bitsream Vera Sans).


[SIZE="3"][COLOR="Green"]12: Transparencies and other eyecandy stuff[/COLOR][/SIZE]

You may have seen a lot of screenshots with nice visual effect (windows fade while minimizing, other windows have transparencies, and wobble while they move and so on). All this can be achieved by the use of a composite manager. A composite manager is some software which elaborates the graphics just before it is sent to the display and combines the various elements. Usually this software is incorporated into a window manager (the program which draws windows) for obvious reasons.

The most common windows&composite manager for Gnome is Compiz. Metacity, which is the default window manager, will have compositing capabilities too. I don't cover composite managers in this HowTo for a good reasons. All this eyecandy is quite resource intensive, so if you want to  use it smoothly you will need to use 3D acceleration with your desktop.

There are two projects which add 3D acceleration capabilities to X, and this are [XGL]("http://en.wikipedia.org/wiki/Xgl") (as a rule of thumb this is better suited if you use proprietary drivers for your video card) and [Aiglx]("http://en.wikipedia.org/wiki/AIGLX") (which is instead better suited for oss drivers). You first have to install one of these, and then run Compiz (or the composite manager of your choice). This can be painless, but can screw everything also. If you want to try, there are a lot of good HowTos on this forum; search for Compiz, XGl or Aiglx.

==========================================================

Just a final trick, if you don't want to enable real transparencies. One thing that has fake transparencies is Gnome terminal; you can enable it under [COLOR="Blue"]Edit->Current Profile->Effects[/COLOR]. Now if you do this, you will understand what I meant by "fake": under the terminal your desktop will be shown, no matter what is actually under it. At least this is good if under the terminal there's really your desktop. But you may find that it covers some icons ](*,) , so what if one wants to launch the terminal in a part of the desktop where there are no icons? You can do this by the command
```

gnome-terminal --working-directory=%f --geometry=75x25+350+205

```
Modify the geometry until you get the right size and the right position. When you are happy you can use [COLOR="Blue"]Applications->Accessories->Alacarte[/COLOR] to modify the menu entry accordingly.

---

### Post by Nonno Bassotto on 2006-06-26
In the next days I plan to add two things.
First, how to skin applications. This is usually trivial, but it may be useful to link sites where you actually can find skins. I will include xmms, mplayer, amsn and whatever you suggest.
Second screenshots. This will take some time, since you have to enable the feature, take the screenshot and crop the detail.
If you have other ideas, let me know.

---

### Post by beko on 2006-06-26
That was really good man especially this part for grub . Keep the good work & I am waiting for the next part.

Thank you

---

### Post by bdude on 2006-06-27
Nice HOWTO! Well done :)

---

### Post by Nonno Bassotto on 2006-06-27
Ok, I've added some applications skinning and tried to improve readability making  manu voices, tabs  and the like in blue and folders in red. Now it looks a bit weird, but I hope it is simpler to read. Comment on this if youdon't like it.

I'd like to add a wine section, but I haven't been able to skin wine application so far, nor to make them use Bitstream vera Sans :( . If you know how to, just post here, so I can edit the original post.

---

### Post by Nonno Bassotto on 2006-06-27
I also added five screenshots to begin with, hosted on ImageShack. But alas, they don't show up for me. Do they show up for anyone?

---

### Post by fonzai on 2006-06-27
[QUOTE=Nonno Bassotto]I also added five screenshots to begin with, hosted on ImageShack. But alas, they don't show up for me. Do they show up for anyone?[/QUOTE]

Yes, I can see the **three** screenshots.

---

### Post by Ahriman on 2006-06-28
I can see four, but they are sort of mingled in with the text.

Good article, though. Go tme thinking about how I want mine to look :D

---

### Post by Nonno Bassotto on 2006-06-28
[QUOTE=Ahriman]I can see four, but they are sort of mingled in with the text.
[/QUOTE]

As soon as I will be able to see them, I will fix them (and add some more, too).

---

### Post by Footissimo on 2006-06-28
A great HOWTO..explained a lot.  Thanks! :)

---

### Post by Turgon on 2006-06-28
Good Howtoo, but remember the "install" in the apt-get **install** command (I offen forget it myself,  the word "get" confuses me).

---

### Post by PingunZ on 2006-06-28
```
sudo apt-get gdesklets
```
Change that to ```
sudo apt-get install gdesklets
```

;) Great howto

Grtz PingunZ

---

### Post by Nonno Bassotto on 2006-06-28
[QUOTE=PingunZ]```
sudo apt-get gdesklets
```
Change that to ```
sudo apt-get install gdesklets
```

;) Great howto

Grtz PingunZ[/QUOTE]
Changed all apt-get (I hope). Cut and paste can be very annoying if you write wrong the first time.

---

### Post by Protostar on 2006-08-11
Nice howto. I'm trying to install themes in Ubuntu, and am using the tar.bz2 format. When I try to install using the theme manager it gives me an error saying "Invalid format." Tar.gz files work just fine. Anyone know how to get around that?

---

### Post by Jvaldezjr on 2006-08-11
Great post...is there a KDE variant, I don't use GNOME.

---

### Post by viviena on 2006-08-11
A good guide, thanks. :) Just a note: the two links to the gDesklets have typos.

---

### Post by Nonno Bassotto on 2006-08-11
> **viviena said:**
> A good guide, thanks. :) Just a note: the two links to the gDesklets have typos.

Corrected the typos, thanks.

---

### Post by fakie_flip on 2006-09-17
Can some people please tell me what the default skin for mplayer in Ubuntu 6.06 Dapper Drake is? I am trying to get the same one for myself in Debian Etch testing unstable. Also, if you would create a link to yours that I could download, that would be great. Thanks.

---

### Post by Nonno Bassotto on 2006-09-18
The standard theme is clearplayer. You can download it on the [Mplayer download page]("http://www.mplayerhq.hu/design7/dload.html") under the skin section. It is now the third from the bottom.

---

### Post by demonhunter on 2007-02-06
thanks man... this helped me to change GDM and create desklets... :guitar:

---

### Post by Zer0Nin3r on 2007-02-07
I came across the following link,  Perhaps is may give some more insight.  Cheers!

[http://www.linuxplanet.com/linuxplanet/tutorials/6223/1/]("http://www.linuxplanet.com/linuxplanet/tutorials/6223/1/")

---

### Post by Somenoob on 2007-02-07
Great HowTo. It would be good to have other such long howto's for KDE and Xfce.

---

### Post by cbrehm on 2007-02-07
Very good, lots of things to play around with. Thank you from a new Ubuntu user!!!

---

### Post by olieviya on 2007-03-02
How can I make an icon theme if I have the icons in png format?

---

### Post by LankanDude on 2007-03-10
I have kubuntu installed, but I can't locate the system pref -> theanms.
Can someone plz tell me where to find this in KDE (or is this something exclusive to Gnome?)

---

### Post by Charron on 2007-03-10
With grub, I have a widescreen resolution (1280x800). Which VGA code should I use?

---

### Post by girard on 2007-03-19
very very helpful thread. thanks a lot.

---

### Post by rcrook on 2007-03-26
How do I change the colors of a gnome theme with out having to resort to editing the gtkrc file and trying to guess what each of the color config variables does? Is there a theme color setting gui like KDEs for gnome?:confused: 


Randall.

---

### Post by Nonno Bassotto on 2007-03-30
There's an application called gnome-color-chooser, but it's not in the official repos. You can find it in [3v1n0's repository]("http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/index.html").

I think you can just download the deb there. If you want the full repository you can add to your /etc/apt/sources.list the following lines
```

deb http://download.tuxfamily.org/3v1deb edgy 3v1n0
deb-src http://download.tuxfamily.org/3v1deb edgy 3v1n0

```
and then authenticate the repo with the command
```

wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add - && sudo apt-get update

```

 I should add it to the HowTo, but... well I should also update it, especially because I make no mention of Compiz/Beryl, which could make sense then, but not now. I should also mention Screenlets, Avant-Window-Navigator and Kiba dock. Also now there is a repository for better fonts, rather than a single package.

I think I will wait for Feisty before updating the HowTo. If anyone wants to write a few lines about the missing topics, I will merge them.

---

### Post by Lucifiel on 2007-03-31
This is a great guide but... isn't there any easier way for installing themes? I've tried installing a theme with tar.gz extension by using the Theme manager but it didn't work. Then, I tried extracting the folder but that didn't work too. 

Don't mind me saying this but Ubuntu really needs to improve on this area and a few others, if they really want to make it extremely accessible for Linux newbies. If a system requires a lot of commands and stuff, it's likely to fry most newbies' minds.

---

### Post by Nonno Bassotto on 2007-03-31
Are you sure you are installing a Gnome theme rather than a KDE one? Where does it come from? 

If the theme does not install it just means it has been packaged in the wrong way. A theme is nothing more than a compressed folder containing images (following some standard direcotry structure) and some text file for settings. So if it doesn't work it's the packager fault, nothing to do with Linux being hard for newbies or something like that.

By the way, I heard they want to change the extension of the theme files so that they will be automatically associated with the theme manager, the result being that you'll just need to double click a theme to have it installed.

---

### Post by Nonno Bassotto on 2007-04-01
I may also mention that in WindowsXP tou have to manually replace a dll or install additional (usually payed for) software in order to be able to switch themes. So I may say that Windows is not suitable for newbies...

---

### Post by feldegast on 2007-05-09
I have created a [Ubuntu 7.04 Grub Bootscreen]("http://www.kde-look.org/content/show.php/show.php?content=57961") and a [Kubuntu 7.04 Grub Bootscreen]("http://www.kde-look.org/content/show.php/Kubuntu+7.04+Grub+Bootscreen?content=56843") i hope you like them

---

### Post by airtonix on 2007-05-15
> **Lucifiel said:**
> isn't there any easier way for installing themes?.

Yes a proper gtk theme ( the buttons and ap controls ) will have a gtk.rc file in it root folder.
so if you ddrag and drop a theme that is packaged with this file in the root of the package then it will install.(ell thats the simple explanation)
what system do you have in mind? provide urls to examples of said systems.

> **Lucifiel said:**
>  I've tried installing a theme with tar.gz extension by using the Theme manager but it didn't work. Then, I tried extracting the folder but that didn't work too. 

like others mention it was proly a kde or an xfce theme. or the author did not package it properly.

I am intending to create a theme packaging gui for authors and users without a clue to manage their themes.

> **Lucifiel said:**
>  Don't mind me saying this but Ubuntu really needs to improve on this area if they really want to make it extremely accessible for Linux newbies.

how do you mean? how do other system do this?provide urls screenshots etc.

> **Lucifiel said:**
>  If a system requires a lot of commands and stuff, it's likely to fry most newbies' minds.

sorry regression is not the way to advance. the system requires no more commands than any other, you percieve that there is more most proly becuase you are not use to seeing that many. run windows system monitor and view all processes.....when i do that for all my platforms(mac,linux,win32) they all seem to be running the same amount of processes.....except the mac and linux ones are under less load with the same kind of usage.

i hope you are not iplying that other systems are easier to theme? 
have you tried theming the appleOs on ipods?
have you tried theming the os on amiga?
have you tried theming windows 3.11/95/98/me/xp/2000? can winXp use SVG images to draw the window borders or even PNG images? and if it did how would you edit or create those themes? are they text files or are they closed binary formats that will be destroyed if your flawed ntfs drive (which perpetually needs defragging) borks it one day whilst reading that theme file? what then ? can you retrieve some of it? no.

have you tried installing rockbox on a ipod?

i tell you now gnome themes are the easiest. you just need to wrap your head around it.




if so provide links cite processes and provide screenshots.....


otherwise.....please take a seat sir ;)

---

### Post by phantomgrave on 2007-05-23
Very nice How-To ;)

---

### Post by damaged on 2007-06-15
Hi,

I'm using GNOME + BERYL on ubuntu and I have installed a dark theme (ubuntustudio). But it doesn't affect KDE apps like Amarok. 

You said:

> Qt Then there are KDE applications. These apps use a different set of widgets, based on the QT graphic libraries, rather than the GTK (GIMP ToolKit) based, which are common on Gnome. The first thing to do is to find a matching QT theme; for this you can have a look here. Some themes are also available in the repos, but they may require you to install KDE as well. If you just want to make the apps look nice, but don't want much hassle with theme installation, and you don't care about theme matching, you can find here a deb to install Polymer theme, which is quite nice.

After you have installed the theme (the way to do this depends on the theme, and is usually indicated on the site) you have to set it as default. If you have KDE installed you can do this under the K Control Center. Otherwise you can install qtconfig

Can you expand on the "After you have installed the theme" bit please? I don't know how to install KDE themes in GNOME so that they affect the KDE apps.

Also how can you edit themes? For example the UbuntuStudio theme makes all text fields have a dark gray and the cursor is almost impossible to see. I would like to modify this. And changing the blue of the theme to other colours would be good too.

Any help would be appreciated.

---

### Post by moredhel on 2007-07-11
sometimes you can change the colours of the theme if it supports it - go into themes then customize button, and the third tab :)

---

### Post by crsd36 on 2007-08-01
I remember seeing a "Post Your Desktop" thread somewhere but I don't remember where.  Does anyone have a link?  Thanks!

---

### Post by Sepero on 2007-08-18
I know this thread is old, but it's still got a lot of good info. A+

---

### Post by ouellettesr on 2007-09-27
airtonix, I for one would be interested in a gnome theme packaging gui. Please let me know if you decide to do this, I will beta test for you.

---

### Post by wickedwordcraft on 2007-10-11
I've finally managed to get my KDE desktop to look JUST the way I want it to look. Last night, I bought a new computer and I've got Kubuntu all installed and ready. 

I need to know how to save my settings from the old system to port them to the new system (wall paper, custom color theme, custom icons, even the way my launch bar looks). Any help here will probably save me hours.

Thanks!

---

### Post by overlord.gaurav on 2007-10-11
I'm not able to start gDesklets.

This is what the terminal returns:
```
overlord@ubuntu:~$ gdesklets
Starting gdesklets-daemon...
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.

```

This is the output in the log file:
```
Log messages of /home/overlord/.gdesklets/logs/gdesklets%3A0.0.log
/usr/lib/gdesklets/main/__init__.py:118: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()

==========================================================[10/12/07-06:07:45]===
Could not import tiling module!


```

---

### Post by overlord.gaurav on 2007-10-12
....any help??

---

### Post by wilerk on 2007-12-20
Kewl article, and thanks I totally transformed my Desktop, I add this to my list of why I should never go back to Bimbos, uhm Windows.

---

### Post by Promaster91 on 2008-05-07
Finally, a great how to on themes!

---

### Post by buddah1620 on 2008-07-01
Thanks so much for the how to :)  I was not able to run the desklet program.  It would install, but when i started it, it would do nothing.  However, the "Screenlets" program works nicely :)

---

### Post by granollie on 2008-07-22
Hi, I have a pretty simple question: 

Nonno Bassotto, in your original post here I really like the blue theme

(in the picture with the tabs generali and simboli that is showing the how to change the icon)

Could you please refer me how to get this theme/ the name of the theme?

Thank you very much!! :)

---

### Post by Orlsend on 2008-07-22
Yeah, I saw Also a program called Epidermis (Used to be Complete Look) those all this for you, You can import the images and theme's

---

### Post by Nonno Bassotto on 2008-08-12
> **granollie said:**
> Hi, I have a pretty simple question: 

Nonno Bassotto, in your original post here I really like the blue theme

(in the picture with the tabs generali and simboli that is showing the how to change the icon)

Could you please refer me how to get this theme/ the name of the theme?

Thank you very much!! :)

I'm sorry I don't remember this... I checked but I don't have that theme installed anymore :(

---

### Post by duckys on 2008-08-19
I believe that this is the best well planned artical on how to do themes with ubuntu. Usually you have to look through 10 articals before you completely understand what is going on. It is simple, short, and to the point. Thanks!!!

---

### Post by zioboy on 2008-12-23
how i can use the codes???

'coz i'm new in ubunto

---

### Post by mtnakd on 2009-02-07
great job. thx bro !

---

### Post by eperry2011 on 2009-02-27
Very thorough post - great job!  Now my desktop is the envy of my friends j/k lol!:lolflag:

---

### Post by magnoliasouth on 2009-03-12
This truly is a wonderful tutorial, but I am still having trouble. Probably because the version used in the tutorial is an older one and the locations are no longer the same, or at least that is my guess. For example, I don't have [COLOR="Blue"]System->Preferences->Themes[/COLOR] and I cannot even find [COLOR="Blue"]Applications->Administration->Configuration Editor[/COLOR]. That's just a couple of examples of what I mean.

Hopefully I can eventually sort it out, but I still do thank you for such a detailed tutorial.

---

### Post by greenbean119 on 2009-03-13
> **magnoliasouth said:**
> This truly is a wonderful tutorial, but I am still having trouble. Probably because the version used in the tutorial is an older one and the locations are no longer the same, or at least that is my guess. For example, I don't have [COLOR="Blue"]System->Preferences->Themes[/COLOR] and I cannot even find [COLOR="Blue"]Applications->Administration->Configuration Editor[/COLOR]. That's just a couple of examples of what I mean.

Hopefully I can eventually sort it out, but I still do thank you for such a detailed tutorial.

I cannot find Themes also but I know how to get to the Configuration Editor, all you do here is type in the Command Line: gconf-editor

---

### Post by UnhappyFace on 2010-05-30
nvmnd soz.

---

### Post by Photonic Nature on 2012-09-24
> 5: Panels

You can play with panels to achieve a more comfortable setting.
---
By default you should have two panels, one at the top, the other at the bottom. To create a new panel or delete one, you can just right-click on the panel.
---
Under Properties you can also choose some other things: you may set it to hide automatically your panel or to make it a bit transparent. If your panel doesn't hide correctly, then you have to edit the panel configuration.
---
 However the whole area should be filled if you have enough windows open. Now you can delete the Window List on the lower panel. The same can be done with the Notification Area, which is the area with the little icons like the network status.

Many people will want to put the window list and the notification area on the upper panel and launchers for the most common applications on the lower.
OR

1. You can keep your top panel as is (24px) expanded and locked.
2. Then change the bottom panels (Right Click > Properties) Orientation to TOP, Expand and Auto Hide.
3. For this to work and have the TOP panel on top again; Change it's orientation to bottom, wait for the bottom panel (now up top) to hide, then change the Top panels orientation back to TOP. 
4. Now your top panel is as it was and when you push your cursor to the very top of the screen, your other panel will pop-down so you can select desktops and active windows.

I've done this and added a Window selector to the original top panel, plus relocated the clock / calendar to the far right and deleted the original 'Menu Bar'  on the left and replaced it with the 'Main Menu' which eliminates all the text and just leaves the ubuntu icon and a lot more room for my frequently used launcher icons along the top.

edit / added comments below...

Why did I do it this way?
Well this panel trick gives me / you more room for windows when your display is real estate challenged like on my old DELL Latitude D610 with a max res. of 1024x768 ... running Lucid 10.04 LTS.
and...
I moved the clock to the far right because on occasion my 'Indicator Applet Session' (power button icon) has a mind of its own and has a tendency to disappear without a trace.

Cheers

---

### Post by vasa1 on 2012-09-24
This one may be soon closed as being old, but whoever is redoing the [Eye Candy Wiki]("https://help.ubuntu.com/community/UbuntuEyeCandy") may want to refer to this thread.

---

### Post by Toz on 2012-09-24
And on that note, closing.

---

