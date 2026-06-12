---
title: "HOWTO: Make your fonts smooth enough to drool over."
date: 2004-11-15
forum: Tutorials
---

### Post by zenwhen on 2004-11-15
Drop this file in your home directory renamed to ".fonts.conf" and log out and in again. It turns on auto hinting and makes your fonts sexy smooth.  :grin:


Edit: Oops, typo.

---

### Post by az on 2004-11-15
Can't you set your fonts with the desktop configuration utility? Fonts- Advanced...

---

### Post by zenwhen on 2004-11-15
Yes, but auto hinting is not configurable with that utility. This is something you have to do manually until the gnome devs drop it into that tool.

---

### Post by stodge on 2004-11-15
Is this a GNOME only thing, or for Ubuntu in general? I.e. will it work for KDE?

---

### Post by HungSquirrel on 2004-11-15
I see no difference.  ;)

Edit: But when I moved it to .fonts.conf I did.  *_*

---

### Post by dle on 2004-11-15
[QUOTE=stodge]Is this a GNOME only thing, or for Ubuntu in general? I.e. will it work for KDE?[/QUOTE]

It will apply to KDE too.  It won't apply to apps that use older toolkits, like nedit or xpdf.

---

### Post by kidrich on 2004-11-15
[QUOTE=zenwhen]Drop this file in your home directory renamed to "fonts.conf" and log out and in again. It turns on auto hinting and makes your fonts sexy smooth.  :grin:[/QUOTE]

This may not be necessary -- A quick look at my Hoary box shows auto hinting is already enabled by default globally (for all users) in /etc/fonts/local.conf.

---

### Post by p!=f on 2004-11-15
[QUOTE=kidrich]This may not be necessary -- A quick look at my Hoary box shows auto hinting is already enabled by default globally (for all users) in /etc/fonts/local.conf.[/QUOTE] 
 It was not enabled on mine. 
 Much better now anyway. :)

---

### Post by zenwhen on 2004-11-15
Sorry about that typo. :P

---

### Post by bvc on 2004-11-15
[QUOTE=kidrich]This may not be necessary -- A quick look at my Hoary box shows auto hinting is already enabled by default globally (for all users) in /etc/fonts/local.conf.[/QUOTE]
yes, it's there, but not working. Thx zenwhen, is now!

---

### Post by talkingwires on 2004-11-15
[QUOTE=kidrich]This may not be necessary -- A quick look at my Hoary box shows auto hinting is already enabled by default globally (for all users) in /etc/fonts/local.conf.[/QUOTE]
Yeah, Hoary has support for this in the Desktop Preferences. For Hinting, you can choose None, Slight, Medium, and Full and it has an example of each. I'd post a screenshot, but pressing Print Screen results a message saying gnome-panel-screenshot can't be found, and a quick trip to Synaptic turns up zilch. :-?

---

### Post by adbak on 2004-11-15
Anyone who doesn't have Hoary (cuz of the screenshots dilemma) able to take and post before & after pics?  I'm trying to decide if it's really necessary.

---

### Post by bvc on 2004-11-15
install imagemagick (if it's not already) and from a commandline do;
import -window root -quality 85 ~/`date +%Y%m%d-%H%M%S`-lg.png

or copy this and name it something ( I call it sysinfo.sh) and run it from a terminal;
sh sysinfo.sh
```
#!/bin/bash
echo !========================SYS===========================!
cat /etc/debian_version
cat /proc/version
echo #
echo !========================CPU===========================!
cat /proc/cpuinfo | grep "model name"
cat /proc/cpuinfo| grep "cpu MHz"
cat /proc/cpuinfo | grep "bogomips"
cat /proc/cpuinfo | grep "cache size"
echo #
echo !========================MEM===========================!
cat /proc/meminfo | grep "MemTotal"
cat /proc/meminfo | grep "MemFree"
cat /proc/meminfo | grep "SwapTotal"
cat /proc/meminfo | grep "SwapFree"
echo #
echo !========================VIDEO===========================!
#cat /proc/pci | grep audio
#cat /proc/pci | grep VGA
#cat /proc/pci | grep Ethernet
cat /proc/driver/nvidia/version
#cat ~/.fluxbox/version
echo #
echo !=====================SAY CHEESE=======================!
import -window root -quality 85 ~/`date +%Y%m%d-%H%M%S`-lg.png
```
hey, what's up with the space?
=====    =====
?
oh well

---

### Post by piedamaro on 2004-11-15
Consider that it's a screenshot and it's also compressed. Real fonts are better.

Btw, I'm on hoary but I've copied my gnome-panel-screenshot binary and its glade file from my fedora install :-\"

---

### Post by jdodson on 2004-11-15
wow that is a great fix.  i wonder if it will be turned on by default in hoary?  anyways, at least i have this fix, thank you very much!

---

### Post by TravisNewman on 2004-11-16
OK what I was seeing before was complete placebo effect.

This is amazing! Sometimes the fonts seem a bit too fat, but most places this is freaking amazing. You rock!

---

### Post by FLeiXiuS on 2004-11-16
Excellent fix, my eyes are now restrained away from the monitor...i can read them with ease  \\:D/

---

### Post by ispmike on 2004-11-16
What exactly does this do? My fonts seem bigger.

---

### Post by Nick on 2004-11-16
Brilliant. Thanks.

---

### Post by liberal_tugboat on 2004-11-16
you can turn hinting on in the fonts menu in desktop preferences in Warty.

go to Computer>Desktop Preferences>Fonts
Click the "Details..." button.
Select amount of hinting
I chose "Full"
Restart X "ctrl+alt+bckspc"

Hopes this helps! 
Ubuntu is the best linux distro- You will being seeing ALOT more of me here  :-P

---

### Post by p!=f on 2004-11-16
[QUOTE=liberal_tugboat]you can turn hinting on in the fonts menu in desktop preferences in Warty.
  
  go to Computer>Desktop Preferences>Fonts
  Click the "Details..." button.
  Select amount of hinting
  I chose "Full"
  Restart X "ctrl+alt+bckspc"
  [/QUOTE] It doesn't work for me unless I enable autohinting in /etc/fonts/local.conf.

---

### Post by HungSquirrel on 2004-11-16
Nice name, liberal_tugboat!  :lol:

---

### Post by liberal_tugboat on 2004-11-16
Why thank you! I also happen to like it.

---

### Post by liberal_tugboat on 2004-11-16
[QUOTE=p!=f]It doesn't work for me unless I enable autohinting in /etc/fonts/local.conf.[/QUOTE]

Yeah your right I did a little experimenting, and the option to turn it on in the fonts control doesnt work (but it will be fixed in hoary- not asking... demanding hehe)
but the .fonts.conf works GREAT!
it really makes everything easier to read.
I also bumped my fonts up to 11 point (from the default 10) now everything is nice on the eyes in 1280x1024 (19 inch crt)

---

### Post by Magneto on 2004-11-16
Thanks about to try this out

---

### Post by Magneto on 2004-11-16
This is for those who need assistance with TTF - TrueType Fonts
Here are some key words for those using search
font problems
better fonts
MS fonts
microsoft fonts
cleartype fonts

```

This has been directly taken from [http://www.paulandlesley.org/linux/xfree4_tt.html](http://www.paulandlesley.org/linux/xfree4_tt.html)

Table of Contents
1. Introduction
2. Other Resources
3. Obtaining TrueType Fonts

    3.1. Installing Debian-Packaged Fonts
    3.2. Installing Non-Packaged Fonts

4. The fonts.scale and fonts.dir Files

    4.1. Index Files for Packaged Fonts
    4.2. Index Files for Non-Packaged Fonts

5. Creating Fonts Aliases

    5.1. Aliases for Packaged Fonts
    5.2. Aliases for Non-Packaged Fonts
    5.3. Aliases for Helvetica

6. Setting Up the X Server

    6.1. To Server or Not To Server?
    6.2. Loading the TrueType Module
    6.3. Setting the FontPath

7. Configuring Netscape
8. Other Configuration Notes

1. Introduction

One thing that's been widely recognized as lacking on UNIX systems, and Linux is no exception to this as it uses the same graphical display software technology as all other UNIX systems, is good-looking fonts.

However, with the addition of the font server in XFree85 3.x, the capability has existed to get good-looking fonts: TrueType capable font servers such as xfs-xtt and xfsft were created and worked very well. In XFree86 4, loadable modules functionality was added to the X server and among the loadable modules provided were two providing TrueType font support directly in the X server, without requiring an external font server (obviously if you need a font server for some other reason, you are still free to use one).

This document describes how to configure a Debian system with XFree86 4.x installed to enable TrueType fonts using the TrueType module built into the X server.

At the time of this writing, the only way to get XFree86 4 is via the Debian "testing" (or "unstable", of course) distribution. Most of the Debian packages described below are not available in the current Debian "stable" area. You will need to configure your system to be able to see the Debian "testing" or "unstable" areas in order to install them as I've described below.
2. Other Resources

Everything I learned about this process came from one or both of these two excellent resources (plus a bit of experimentation); you should keep them handy as you proceed through this setup. Although they relate mostly to other distributions such as Red Hat (and hence the reason I felt this document was not redundant) they still contain much information of interest:

    *

      [ XFree86 Font Deuglification Mini HOWTO ]
    *

      [ Some Linux for Beginners (TrueType Fonts) ] 

3. Obtaining TrueType Fonts

The standard XFree86 base package does not provide any TrueType fonts. However, there are a number of Debian packages containing TrueType fonts. If there is a Debian package for the TrueType fonts you're interested in, it's simplest to install that rather than getting the fonts separately and installing them yourself. However, I will describe the steps involved with installing your own fonts here as well, for those that are interested.
3.1. Installing Debian-Packaged Fonts

Probably the most common fonts to install are the Microsoft TrueType Core Fonts package. In a stunning display of corporate generosity (or something like that...) Microsoft has released these fonts under an End User License Agreement (EULA) which allows them to be installed and used on an unlimited number of systems, with no limitation on the host platform. So, it's perfectly legal to download them from the Microsoft site and use them on your Debian GNU/Linux system.

Although they are free-beer free, the EULA mandates that the fonts not be redistributed for profit (which means they won't appear on any Debian CD's), and you cannot reverse engineer, decompile, or disassemble them, which means they aren't DFSG-compliant anyway. However, our intrepid Debian packagers have a straightforward workaround, used in other similar packages such as xanim which have non-free components. There is a Debian package, msttcorefonts, which will download those fonts for you off the Web using wget, and install them on your Debian system with all the proper Debian-ization you've come to expect.

To use this package to install the Microsoft fonts, do this:

  # apt-get install msttcorefonts

There are a number of other Debian packages which supply TrueType fonts, most notably for Chinese and Japanese: if you have a need for those feel free to install them as well. I explicitly mention the Microsoft fonts, and will continue to concentrate on them through the rest of the document, because these fonts are used by a large percentage of the sites on the Web. Your web browsing will be a much more pleasant experience if you install them.
3.2. Installing Non-Packaged Fonts

If you have TrueType fonts you want to install which aren't packaged for Debian, you will need to do quite a bit more work. However, the steps needed, while a bit tedious, are not difficult.

The first step is creating a place for your non-packaged fonts. I discourage you from placing them in any of the directories used by the packaged fonts: I feel it's a bad idea to place any kind of local configuration into Debian system directories. Following the de-facto standards from the Font De-Uglification HOWTO, I chose /usr/local/share/fonts/ttfonts. Once you create this directory, copy in the TrueType font files (*.ttf):

  # mkdir -p /usr/local/share/fonts/ttfonts
  # cp /c/windows/fonts/*.ttf /usr/local/share/fonts/ttfonts

4. The fonts.scale and fonts.dir Files

These files provide the X server with an index of the fonts available in the various fonts files. The fonts.dir file is typically used with non-scaled fonts while fonts.scale is used with (surprise!) scaled fonts. Exactly why they are different files, and exactly why we install both files in directories containing scalable fonts (such as TrueType fonts) remains a bit of a mystery to me. But, we do and it works.
4.1. Index Files for Packaged Fonts

The Debian packages for TrueType fonts should install these font index files according to the Debian font management methods. This means that after installation, you'll find a /etc/X11/fonts/TrueType directory containing one or more *.scale files for each TrueType font package you installed (e.g., /etc/X11/fonts/TrueType/msttcorefonts.scale). If you ever update (add, remove, or modify) any of the the *.scale files in this directory yourself you should run the update-fonts-scale utility to be sure it updates the /usr/lib/X11/fonts/TrueType/fonts.scale file properly (this is the file the X server will be reading; see below). You may also need to run update-fonts-dir to update the /usr/lib/X11/fonts/TrueType/fonts.dir file.
4.2. Index Files for Non-Packaged Fonts

If you are installing your own, non-packaged TrueType fonts here is where the majority of the extra work comes in: while the TrueType packages will come with a pre-built fonts.scale file which can be properly installed using the update-fonts-scale and update-fonts-dir utilities, you must create your own index files for non-packaged fonts. Fortunately, there are tools that make this fairly straightforward.

When using non-packaged fonts you will not be using the Debian update-fonts-scale and update-fonts-dir; these are only used with packaged fonts, which install under /etc/X11.
4.2.1. Building fonts.scale

We start by creating fonts.scale. The method I followed here is based on the description in [ Font Deuglification HOWTO, Section 3.2.2.2 Getting the Fonts Ready ] To do this we need the ttmkfdir utility. This is packaged for Debian (testing/unstable only), so install it:

  # apt-get install ttmkfdir

Next, we must invoke it to generate the fonts.scale file. As noted above, we will assume we've put all our TrueType font files into a local directory /usr/local/share/fonts/ttfonts.

  # cd /usr/local/share/fonts/ttfonts
  # ttmkfdir -o fonts.scale

4.2.2. Building fonts.dir

After fonts.scale is completed we could simply copy it to fonts.dir, since the two files should be identical. However, it turns out that ttmkfdir generates its output in the reverse of the ideal order, so we want to to reverse the order of the lines in these files. The following operations are based on those described in [ Some Linux for Beginners (TrueType Fonts) ]. Use these commands:

  # head -1 fonts.scale > fonts.dir
  # tail +2 fonts.scale | tac >> fonts.dir
  # cp fonts.dir fonts.scale

5. Creating Fonts Aliases

Although that should be all the setup necessary for TrueType font indices, it turns out that a number of applications, most notably Netscape 4, do not manage very well with only the data supplied by the fonts.scale file. For the benefit of these applications, we will create a fonts.alias file that provides aliases of more traditional X names for the TrueType fonts.
5.1. Aliases for Packaged Fonts

Although the Debian packages contain default .scale files, they do not (as far as I have seen) provide default .alias files. So, we will need to construct them ourselves. I only have experience with the msttcorefonts package; if you're installing other Debian TrueType fonts packages you should check /etc/X11/fonts/TrueType to see whether they provide a .alias file for their fonts, then decide whether you actually need one or not.

The method used to generate this file will be essentially identical to that described in [ Fuzzy small fonts on the web ].

Although you could generate this file by hand it's extremely tedious. The mkfontalias.py Python script, distributed at [ Fuzzy small fonts on the web ], will take all the grunt-work out of generating the aliases. Of course you will need Python installed on your system to run it. Unfortunately this script is hardcoded to read only a file fonts.dir in the local directory, which is problematic since Debian packages ship only the *.scale file (and it's typically named <:package>.scale to boot). But, as I noted above, the .scale and .dir files should be identical so we can work with that.

Each font typically supports many different character sets, and this script creates an alias for each one: when I ran it on the Microsoft fonts I got a 550K file containing 4247 aliases. This many aliases could give your server a severe belly-ache. Additionally, for Latin 1-based languages you really don't need most of them. I followed the advice of the web site above and extracted the aliases for only the ISO 8859-1 character sets. Remember the other character sets are still available, they just don't have aliases. If you need more character sets or different ones than ISO 8859-1, adjust the grep command below (or use your favorite editor).

The next subject of interest is where the .alias file should be put. As with the .scale file above, it belongs in the Debian-specific font directory /etc/X11/font/TrueType. There should be one alias file for each set, or package, of TrueType fonts. Once there, you can use the update-font-alias utility to construct the appropriate fonts.alias file for the entire TrueType directory and install it.

So, given all the above, the actual commands are rather anti-climactic:

  # cd /etc/X11/fonts/TrueType
  # cp msttcorefonts.scale fonts.dir
  # python <pathto>/mkfontalias.py
  # grep 'iso8859-1"' fonts.alias > msttcorefonts.alias
  # rm -f fonts.dir fonts.alias
  # update-fonts-alias TrueType

This gives me an eminently reasonable .alias file with 336 entries in it, and installs it.

I should probably also point out that this script changes the very smallest font sizes, the 6, 7, and 8 point sizes, to all resolve to 9 point. Some browsers seem to ask for these extremely small point sizes, but when rendered they are completely unreadable. The script incorporates a useful fix of using aliases to map to those extra-small sizes into something very small, but still readable. See [ Fuzzy small fonts on the web ] for more information.

Having said all that, if you don't feel like doing these steps to create the fonts.alias file yourself, you can simply click here to download the file I built for my system, and install it as your /etc/X11/fonts/TrueType/msttcorefonts.alias file, then just run the last step (run update-fonts-alias).
5.2. Aliases for Non-Packaged Fonts

The steps needed to create aliases for non-packaged fonts are identical to those for packaged fonts. The only difference is in the names of the directories, and in the fact that we don't use update-fonts-aliases. Read the above information, then follow these steps:

  # cd /usr/local/share/fonts/ttfonts
  # python <pathto>/mkfontalias.py
  # grep 'iso8859-1"' fonts.alias > new.alias
  # mv new.alias fonts.alias

That's all you need to do; there's no need to run the Debian package update-font-alias utility when installing non-packaged fonts. As above, if you don't want to run these commands yourself you can download the file I built for my system, and copy it to /usr/local/share/fonts/ttfonts/fonts.alias as your alias file; there's no need for any further processing.
5.3. Aliases for Helvetica

This section doesn't strictly deal with TrueType fonts, but as long as you're mucking about you might as well fix up the aliasing for the default Helvetica fonts in X, as well. You can look at [Fuzzy small fonts on the web ] for more details on why this is useful.

That page also discusses how to install the aliases, but not for Debian. On a Debian system things are a little different: we want to install the aliases in the proper place for the update-fonts-alias utility to find them and generate a fonts.alias for the entire 75dpi and 100dpi directories.

So, visit each of the 75dpi and 100dpi, and save them (using your browser's Save As... feature, or just cut & paste) to the /etc/X11/fonts/75dpi/zzmy-fonts.alias and /etc/X11/fonts/100dpi/zzmy-fonts.alias files, respectively. You can name them what you like; I used a prefix of "zz" here simply to be sure my aliases came last.

Once you have installed these new aliases, update the generic fonts.alias files actually used by X just as we did with the packaged TrueType fonts:

  # update-fonts-alias 75dpi 100dpi

6. Setting Up the X Server

At this point we've set up the fonts and their indices for proper use. Next we have to inform the X server about this new batch of fonts. So far as I'm aware, none of the Debian TrueType packages will do this for you when they install themselves, unfortunately.

We will be modifying the XFree86 version 4 X server configuration file; on Debian this is /etc/X11/XF86Config-4 (if you don't have that file, it may be called just /etc/X11/XF86Config).
6.1. To Server or Not To Server?

In previous releases of XFree86, you needed to use an external font server to handle TrueType fonts. In XFree86 4 you no longer need an external server, just to serve TrueType fonts. You may, however, decide you still want one for other reasons. If you would like to use the font server to server TrueType fonts you will need to make sure your font server is capable of doing so, then configure it to see the TrueType fonts installation(s) you created above. This document doesn't deal explicitly with how to do this; you may, however, find useful information in my previous incarnation of this file, which deals with setting up TrueType fonts on XFree86 3.3.6.

If you decide you don't need a font server any longer (I removed mine), then you should remove the Debian package first. Afterwards, edit the X server configuration file and remove any FontPath entries for font servers; these will most likely look similar to one or both of these:

        FontPath        "unix/:7100"

        FontPath        "unix/:7101"

Normally you would need to restart the X server to have the change in font path take effect; however, you can also modify the running X server's font path via the xset utility:

  $ xset -fp unix/:7100

  $ xset -fp unix/:7101

6.2. Loading the TrueType Module

The X server configuration that comes with Debian already loads one of the two X server TrueType font modules by default, the freetype module. Therefore, unless you've done a good bit of hacking on your X configuration file you likely will not need to do anything for this setting. However, you should find the "Module" Section of your configuration file and ensure that a line like this appears in it:

        Load		"freetype"

If not, you should add it. Alternatively, you might decide to Load the xtt module rather than "freetype"; I haven't tried it in XFree86 4 but I did use the font server it is based on in XFree86 3.3.6 and it worked well. I can't tell any difference between them, but use whichever one you prefer. You will need to restart the X server in order for it to take effect. In this case you can do the modifications in the next section first, then just restart once afterwards.
6.3. Setting the FontPath

Next we need to tell the X server where to look for our new fonts. Edit the X configuration file and find the "Files" Section; in most standard versions of this file it'll be right up at the top.

In this Section will be a list of FontPath entries. All you need to do is add our new directory to this list, by adding one or both of these lines, depending on whether you installed packaged or non-packaged fonts (or both):

        FontPath	"/usr/lib/X11/fonts/TrueType"

        FontPath	"/usr/local/share/fonts/ttfonts"

These new paths will take effect the next time the X server is started; in order to restart the X server you must log out of your current session (if you use a display manager like XDM or GDM), or exit X (if you use startx to start it). If you don't want to restart your X server right now, you can also easily add the new font paths to the running instance of the X server with the xset utility, like this:

  $ xset fp+ /usr/lib/X11/fonts/TrueType

  $ xset fp+ /usr/local/share/fonts/ttfonts

Once you've done this (you can use xset q to verify that the new path exists in the running server's font list), you can use X utilities such as xfontsel to check that the new fonts can be used. Run xfontsel and verify that you can choose foundry (fndry) values of Microsoft and Monotype, and ensure that font family (fmly) Arial and Arial Black (for example) appear under the Monotype foundry.
7. Configuring Netscape

As a final note, I'll describe how to configure Netscape to use the new TrueType fonts. First, if you haven't restarted Netscape since you finished the updating of the font path, etc. in your X server you should do so now, so Netscape will be able to see the new system fonts.

In Netscape, select Edit->Preferences.... Then click on Fonts in the left navigation bar.

In the Variable Width Font pulldown you now should see Arial (Monotype) listed. This is the default sans-serif font for Microsoft systems, and so is the one many web pages expect to be displayed in. Not only that, but it's a very nice, clean font with good anti-aliasing in its own right. So, select that one.

In the Size pulldown you should see a number of sizes. If you see only 0 and 12, that means your fonts.alias file was not recognized for some reason. Pick the size that looks best to you; I'm partial to "10" myself. I actually don't know what the Scaling checkbox determines; I can't really see any difference between selecting and de-selecting it myself. If anyone else knows, write to me and I'll add it in.

You might also consider selecting Courier New (Monotype) for your Fixed Width Font; as with the Monotype Arial it's a very nice version of Courier New.
8. Other Configuration Notes

Other Debian users occasionally send me notes on issues or problems with various applications; I haven't verified these myself.

    *
```

      Ross Boylan reports that Wine is apt to crash if you install the Microsoft Windows linotype-palatino fonts; if you have these fonts installed and you have problems using Wine, you can edit the fonts.dir and fonts.scale files, then use xset fp rehash.

---

### Post by jahLux on 2004-11-20
[QUOTE=zenwhen]Drop this file in your home directory renamed to ".fonts.conf" and log out and in again. It turns on auto hinting and makes your fonts sexy smooth.  :grin:


Edit: Oops, typo.[/QUOTE]
 This deserves to be made into a "sticky" .........AWESOME  absof-ckinglutely awesome................!!!

---

### Post by myklgrant on 2004-11-20
Wow! Thanks zehwhen. A world of difference. This just keeps getting better and better.
Michael

---

### Post by LongTooth on 2004-11-25
MyGawd! What a difference! Thanks for the tip, zehwhen.

---

### Post by ale on 2004-11-26
thank you all!

this is indeed a very nice option; however fonts will get a bit blurrier. but the correct scaling compensates for that - i always wondered how can some fonts become bold when scaled - not anymore with autohinting. :)

also some interesting stuff i noticed - it seems Gimp uses freetype2 to render fonts. you can try out how fonts will look with or without autohinting before changing your system defaults.

but in Inskape fonts look better. how they do it?? they scale perfectly

---

### Post by artAlexion on 2004-12-04
[QUOTE=kidrich]This may not be necessary -- A quick look at my Hoary box shows auto hinting is already enabled by default globally (for all users) in /etc/fonts/local.conf.[/QUOTE]
 What about the "freetype autohint module"?  What does it do, and is it inconsistent with sub-pixel rendering?

---

### Post by fmerenda on 2004-12-12
Whoa! that's EXACTLY what I was looking for, thanks!!!! My fonts are beautiful now! I *added* that section to my .fonts.conf file, though, so mine now looks like this:

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <dir>~/.fonts</dir>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintmedium</const>
  </edit>
 </match>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>

```

and everything renders beautifully. My eyes THANK YOU!!!!

Take care,
-Frank

---

### Post by ConstableRoark on 2004-12-12
[QUOTE=Magneto]This is for those who need assistance with TTF - TrueType Fonts
Here are some key words for those using search
font problems
better fonts
MS fonts
microsoft fonts
cleartype fonts

...

So, given all the above, the actual commands are rather anti-climactic:

  # cd /etc/X11/fonts/TrueType
  # cp msttcorefonts.scale fonts.dir
  # python <pathto>/mkfontalias.py
  # grep 'iso8859-1"' fonts.alias > msttcorefonts.alias
  # rm -f fonts.dir fonts.alias
  # update-fonts-alias TrueType

...
[/QUOTE]
So I used apt-get install msttcorefonts to download and install it, but the directory /etc/X11/fonts/TrueType was not created.  I'm not sure why, but I cannot run the script and finish this process without fixing this problem.  Anyone have any ideas why this might have happened?

Edit:  In fact, the directory called "Type1" is the sole directory in "fonts".

---

### Post by macewan on 2004-12-18
[IMG]http://www.macewan.org/images/compare.jpg[/IMG]

There really is a fairly clear difference, thanks for the awesome suggestion.

The right side is from screenshot before and the left side is after.

---

### Post by wulf on 2004-12-18
YMMV - I tried it on my laptop and found it made the fonts more blocky and ugly. It certainly makes a difference but end results will vary from display to display. FWIW, I also prefer the appearance of the LH screenshot above - the letter shapes aren't quite as nice but it's less blurry and easier to read on my screen.

Wulf

---

### Post by CowPie on 2005-01-01
[QUOTE=zenwhen]Drop this file in your home directory renamed to ".fonts.conf" and log out and in again. It turns on auto hinting and makes your fonts sexy smooth.  :grin:


Edit: Oops, typo.[/QUOTE]
 OH my god!!!  Now I have to link to this thread for every OSX person who says how shitty and hard to configure Linux fonts are....you rock!!!!

(I aplogize in advance for overloading the server jdong ;))

---

### Post by CowPie on 2005-01-01
[QUOTE=CowPie]OH my god!!!  Now I have to link to this thread for every OSX person who says how shitty and hard to configure Linux fonts are....you rock!!!!

(I aplogize in advance for overloading the server jdong ;))[/QUOTE]
 DOes this website look blocky to anyone else (onlyt he parts that look like times new roman): [http://webster.commnet.edu/grammar/conjunctions.htm](http://webster.commnet.edu/grammar/conjunctions.htm)

---

### Post by Magneto on 2005-01-01
[QUOTE=ConstableRoark]So I used apt-get install msttcorefonts to download and install it, but the directory /etc/X11/fonts/TrueType was not created.  I'm not sure why, but I cannot run the script and finish this process without fixing this problem.  Anyone have any ideas why this might have happened?

Edit:  In fact, the directory called "Type1" is the sole directory in "fonts".[/QUOTE]
 Did you try creating the directory?

mkdir TrueType

---

### Post by jadugarr on 2005-01-17
Very nice guide, exactly what I was looking for.  My fonts are as nice as they are in XP now. :)

---

### Post by ZenPirate on 2005-01-17
Yeah, thanks for this. My lcd monitor no longer hates me :D

---

### Post by akurashy on 2005-01-18
All i can only say is O M G :)))))
this was freaking great! a nice change to gnome font look, 
thanks god i stopped by HOW-TO forums lol
or i could never find this :)

thanks a lot!

---

### Post by Leaf on 2005-01-18
Muchos gracias, zenwhen!

You wouldnt happen to be an ATI driver guru, now would you?

---

### Post by flaming_monkey on 2005-01-21
Just had to add my thanks to this thread. There is a real improvement in the overall look of the fonts.

Thanks for the tip and keep up the good work.

---

### Post by nyrblue35 on 2005-01-21
to be honest i used apt-get install msttcorefonts
anadale mono is the sharpest font to me. ive used it on mandrake, fedora, and now a new install of ubuntu and i like em. great for web browsing.  :mrgreen:

---

### Post by albersag on 2005-01-21
[QUOTE=nyrblue35]to be honest i used apt-get install msttcorefonts
anadale mono is the sharpest font to me. ive used it on mandrake, fedora, and now a new install of ubuntu and i like em. great for web browsing.  :mrgreen:[/QUOTE]
 I cant not get smothered fonts.

I put the config on fonts.conf and local.conf buy nothing changes.

---

### Post by Quest-Master on 2005-01-21
You have to name it .fonts.conf and put it in your home folder, albersag. This is one of the reasons I prefer looking at an Ubuntu desktop rather than a Windows desktop on 1280x1024. :)

---

### Post by nyrblue35 on 2005-01-22
nah i meant i wasnt using this method and wasnt using the posted .fonts.conf, thats all.  8-) 

i was just throwing out another option

---

### Post by Eejay on 2005-01-24
The download disappeared, can't find it
I assumed when the download finished downloading that it would go to the home directory Guess it's going to take a while t get used to Ubuntu ](*,)

---

### Post by Eejay on 2005-01-24
The text wont allow me to rename the file
when I rename the file to ".fonts.conf" the file gos back to the original format /name

---

### Post by fashions on 2005-01-24
[QUOTE=Eejay]The text wont allow me to rename the file
when I rename the file to ".fonts.conf" the file gos back to the original format /name[/QUOTE]

try 
$ cp fonts.txt .fonts.conf

that should do it for you. it copies file "fonts.txt" that was downloaded to your home directory then names the copy ".fonts.conf"
then 
$ ls -a
will let you see it - its a hiden file
$ cat .fonts.conf
will let you view it

---

### Post by fishfishfish on 2005-01-25
Wow! That's a neat trick. This works great in KDE on Warty. Thanks for that, my fonts have never looked so good. 

Cheers,
Matt

---

### Post by twigilicious on 2005-01-26
Fantastic. I already had the TTF fonts installed but they stilled looked kind of crappy. The fix made everything wonderful. Awesome.

---

### Post by Lovechild on 2005-01-26
/me quickly reverts to standard Hoary fonts.conf -- this is horrible, so blurry and nasty..

begun ugly fonts!

---

### Post by Sham on 2005-01-26
Dude, you seem to be a guy in the know. Can I point you to a thread here plz;

[http://ubuntuforums.org/showthread.php?t=12674](http://ubuntuforums.org/showthread.php?t=12674)

My fonts seem blurred around the edges to me. I would really like to have it back the way it was with KDE under FC3 where the black on white contrast is high without loss of definition (and the fonts are BLACK, not this kind of grey I'm seeing here. I've been at my computer for 8 hours, and my head is killing me :(

I've tried the options under Computer -> DEsktop Prefs > Fonts, but nothing seems to help I also turned off antialising too. Again, no joy.

Cheers

---

### Post by nikopol on 2005-01-27
Nice one mate - I had messed up my fonts - they've become really low res and I just couldn't get them back to the correct setting despite loads of attempts (I think due to installing K3b) but that little file sorted everything back again.  Top tip :)

---

### Post by ks- on 2005-01-28
I've tried to install this script as told in the first post.

Since then, everytime I log into Gnome, a popup tells me "you have to be root to run this" or smth, and it opens Synaptic. And of course I don't see any changes regarding my fonts.

Anyone can help me out with this ?

---

### Post by ks- on 2005-01-29
OK I've tried to do "sudo dkpg-configure fontconfig" too and still ugly.

I hate this :(

---

### Post by Yukonjack on 2005-01-30
[QUOTE=zenwhen]Drop this file in your home directory renamed to ".fonts.conf" and log out and in again. It turns on auto hinting and makes your fonts sexy smooth.  :grin:[/QUOTE]

Thank you it works great  :mrgreen: 
Also fix that annoying little letter x on my browsers.

---

### Post by wernst on 2005-02-11
This is definately a "your milage may vary" sort of thing.

On my laptop's LCD running at 1400x1050, the orignal fonts look very smooth, and honestly, better than Windows XP. With the new file, the fonts look more muddled and you start to see werid aliased-color-hinting between characters.

The before-and-after screenshot is very representative: the "before" side on the right looks MUCH BETTER on my LCD.

Anyway, thanks for the tip. I'll try it on my CRT later...

-Warr

---

### Post by foobar on 2005-02-21
i put and renamed the file in the home dir, restarted x but, nothing changed... what else do i need to do?

---

### Post by caiphn on 2005-02-22
Makes a huge difference. Weird thing is when I CTRL+ALT+Backspaced, I lost all GUI. Logged in with username and password and went straight to Bash.. wasn't sure how to start up Gnome again.. or if that is even what I'd want to do at that point.

---

### Post by Jeffredo on 2005-02-22
This looks very much like the Clear Type font enabling used in XP (which helps a great deal).  They do add a tiny bit of green around some letters at certain angles on my LCD set to 1280x1024, but as another poster said, it does take care of the "faded out" letters "x", "k", etc...  I can deal with a slight greenish hint for that!  Good job!  :-)

---

### Post by cdhotfire on 2005-02-23
wow, this almost made me pee myself when i did it. =D> , good work.

---

### Post by Kirin on 2005-02-26
Yes! This looks like it might be what I need to get me using Ubuntu full-time. I'm currently using a G3 iMac, which while nice is quite slooow, and I've been donated a faster PC. I liked all of Ubuntu apart from the fonts (OS X has got me used to heavily anti-aliased fonts). If this looks okay (and I couldn't tell the difference between the fonts in the screenshots and those surrounding them being rendered by OS X) then it may be OSS for me! Yay!

---

### Post by napsy on 2005-02-27
I copied fonts.txt to ~/.fonts.conf but none has changed. The font look is the same; bold. Must I install some specific packages?

Sample:
[IMG]http://freeweb.siol.net/lukan12/sample.png[/IMG]

---

### Post by napsy on 2005-02-27
Got it.  Just reconfigured fontconfig and that was it.

---

### Post by foobar on 2005-02-28
[QUOTE=napsy]Got it.  Just reconfigured fontconfig and that was it.[/QUOTE]
 what did you do to the fontconfig?

---

### Post by Buffalo Soldier on 2005-02-28
I don't know what napsy did to fontconfig. But what I did was, I run terminal and```
sudo dpkg-reconfigure fontconfig
``` and enable the autohinter.

---

### Post by jsgotangco on 2005-03-01
WOW my fonts look so sharp now - it complements Clearlooks. I've never seen fonts so clear in Gnome.

---

### Post by cmsj on 2005-03-01
Something else worth checking is that Gnome is feeding freetype the correct DPI. I'm sure it used to guess this, but both my hoary boxes were wrong when I checked just now.

Firstly, open a terminal and run:

xdpyinfo | grep dots

and you should see something like this:

-(cmsj@tenshu)-(~)- xdpyinfo | grep dots
  resolution:    112x112 dots per inch

Now fire up Gnome's font preferences and click the Details button, set the DPI value in there to, in this case, 112. I'm not 100% sure what you do when your display has unequal horizontal and vertical DPIs, which does seem to happen, but I usually pick a value somewhere in the middle.
In my case Gnome on both machines was at 96, so setting it to 112 makes font sizes larger. You can tweak these down to the same sizes you had before, but in theory it should be rendering them better at that size. Combine that with the autohinting and you should have some very pretty fonts :)

---

### Post by pardasaniman on 2005-03-06
Hmm, I always thought that the default fonts with ubuntu were already very good.  Haven't tried this out yet, but I don't see how it can improve.  Then again, I've been using Linux for a good 3 years, and remember the times when fonts were **really****really***really bad.  

Can someone post a before-after photo?

---

### Post by bored2k on 2005-03-06
[QUOTE=pardasaniman]Hmm, I always thought that the default fonts with ubuntu were already very good.  Haven't tried this out yet, but I don't see how it can improve.  Then again, I've been using Linux for a good 3 years, and remember the times when fonts were **really****really***really bad.  

Can someone post a before-after photo?[/QUOTE]
 there are just 2 many dif. aspects, it looks like they look a lil smaller, but theyre not. Ported M$ fonts look a LOT better, and it overall looks great [works great with msttcorefonts] .

---

### Post by WTF_Shelley on 2005-03-07
Cheers man my fonts are now up to windows standard, (sorry but true)

---

### Post by Jason-X on 2005-03-23
Thanks for this. My fonts look really clear and smooth now!!

Nice one :)

---

### Post by Dex on 2005-05-29
[QUOTE=fashions]try 
$ cp fonts.txt .fonts.conf

that should do it for you. it copies file "fonts.txt" that was downloaded to your home directory then names the copy ".fonts.conf"
then 
$ ls -a
will let you see it - its a hiden file
$ cat .fonts.conf
will let you view it[/QUOTE]
Not sure why but just dropping fonts.txt to home dir and renaming it to .fonts.conf didn't seem to work, but doing it via command line (like above) worked perfectly. This is simply abso-freakin'-lutely-awesome!!!
Kudos to zenwhen - this neat fonts rendering is yet another factor for other distros to blush with jealousy - and windoze with fear. Hey, I can see windoze cracking...
 
Why not submit it to ubuntu folks to make it a default reality with fonts?

---

### Post by vassalle on 2005-06-10
[QUOTE=Dex]Not sure why but just dropping fonts.txt to home dir and renaming it to .fonts.conf didn't seem to work, but doing it via command line (like above) worked perfectly. This is simply abso-freakin'-lutely-awesome!!!
Kudos to zenwhen - this neat fonts rendering is yet another factor for other distros to blush with jealousy - and windoze with fear. Hey, I can see windoze cracking...
 
Why not submit it to ubuntu folks to make it a default reality with fonts?[/QUOTE]
 does this work on hoary too ?

---

### Post by desdinova on 2005-06-10
[QUOTE=vassalle]does this work on hoary too ?[/QUOTE]
 The easiest way to switch on autohinting in Hoary is

sudo  dpkg-reconfigure fontconfig

---

### Post by Rory on 2005-07-02
[QUOTE=desdinova]The easiest way to switch on autohinting in Hoary is

sudo  dpkg-reconfigure fontconfig[/QUOTE]

When I do this I get:

&#9508; Configuring fontconfig &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474;
 &#9474; By default, only outline fonts are used by applications which support     
 &#9474; fontconfig.  Outline fonts are fonts which scale well to various sizes.   
 &#9474; In contrast, bitmapped fonts are often lower quality. Enabling this   
 &#9474; option will affect the systemwide default; this and many other         
 &#9474; fontconfig options may be enabled or disabled on a per-user basis.  
 &#9474;                                                                           
 &#9474; Enable bitmapped fonts by default?                   
 &#9474;                                                                           
 &#9474;                    <Yes>                       <No>  


Can you confirm that I'm supposed to just choose "yes" here?  I'm just being cautious, as it noted that bitmapped fonts are often of lower quality.

Second question:  is this just another way of getting the same result as putting the font.txt file noted at the beginning of this thread in your home at font.conf.  Or, is this something in addition to that trick?

Thanks,
Rory

---

### Post by desdinova on 2005-07-02
[QUOTE=Rory]When I do this I get:

&#9508; Configuring fontconfig &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474;
 &#9474; By default, only outline fonts are used by applications which support     
 &#9474; fontconfig.  Outline fonts are fonts which scale well to various sizes.   
 &#9474; In contrast, bitmapped fonts are often lower quality. Enabling this   
 &#9474; option will affect the systemwide default; this and many other         
 &#9474; fontconfig options may be enabled or disabled on a per-user basis.  
 &#9474;                                                                           
 &#9474; Enable bitmapped fonts by default?                   
 &#9474;                                                                           
 &#9474;                    <Yes>                       <No>  


Can you confirm that I'm supposed to just choose "yes" here? I'm just being cautious, as it noted that bitmapped fonts are often of lower quality.

Second question: is this just another way of getting the same result as putting the font.txt file noted at the beginning of this thread in your home at font.conf. Or, is this something in addition to that trick?

Thanks,
Rory[/QUOTE]

1) Yes you can - it doesn't really aftect you use on the desktop - as bitmapped fonts these days tend to be only used for legacy purposes...

2) Not really - its an addon - fonts.conf allows for VERY fine tuning on font display

;-)

a

---

### Post by mohaham on 2005-07-02
[QUOTE=zenwhen]Drop this file in your home directory renamed to ".fonts.conf" and log out and in again. It turns on auto hinting and makes your fonts sexy smooth.  :grin:
[/QUOTE]

Thanks for the great tip, zenwhen
someone pls sticky this..

---

### Post by Rory on 2005-07-07
FYI, I pointed the maintainer of the ubuntuguide.org toward this thread, as I found the tip posted here so useful.
He immediately added it to the Unofficial Ubuntu Guide with a slight change.  That's even better than putting a sticky on this thread.  Hopefully more will will take advantage of this great tip.

[http://ubuntuguide.org/#extrafonts](http://ubuntuguide.org/#extrafonts)

---

### Post by manicka on 2005-07-07
[QUOTE=desdinova]The easiest way to switch on autohinting in Hoary is

sudo  dpkg-reconfigure fontconfig[/QUOTE]

Thanks desdinova,

I found this a much better way to turn on autohinting than the manual edit for each user, as the effect is system wide.

---

### Post by hamlet_tk on 2005-07-08
[QUOTE=zenwhen]Drop this file in your home directory renamed to ".fonts.conf" and log out and in again. It turns on auto hinting and makes your fonts sexy smooth.  :grin:


Edit: Oops, typo.[/QUOTE]
 Thanks for the great tip.

---

### Post by kvidell on 2005-07-08
They're definitely a great deal smoother, but I don't know if I'm going to lose any bodily fluids over it :-P

Thanks all the same. This... might fix my headaches. We'll see.
- Kev

---

### Post by bugmenot on 2005-11-17
[IMG]http://www.typophile.com/forums/messages/30/69049.gif[/IMG]
from here (more samples on that and the previous page): [http://typophile.com/node/9982?from=50&comments_per_page=50](http://typophile.com/node/9982?from=50&comments_per_page=50)

I myself have 1680x1050 which translates to 129dpi, and I must say on my screen it looks stunning.
CT rendering is a well researched complicated hinting technology, that is not easy to get right. Improving readability is one of MS's prime goals for their next release, and they invested a lot into CT hinted fonts and rendering algos (which have to be adapted to each other). I fear the only thing I envy from them is font rendering. Saldy, that it is one of the most important things that OSes have to do well. IMO.

---

### Post by BLTicklemonster on 2005-11-17
Well, I must say that this is the first time that fonts have looked normal in web pages. The verticals used to almost fade out, like | would almost not appear to be a solid line.

thanks!!!

---

### Post by bored2k on 2005-11-17
As good as the first time I did this on Warty :).

---

### Post by BLTicklemonster on 2005-11-17
[QUOTE=foobar]i put and renamed the file in the home dir, restarted x but, nothing changed... what else do i need to do?[/QUOTE]
I clicked on the download link, and when asked, had it open in a text editor. I then saved it in home as .fonts.conf and it looks great.

---

### Post by mechanic on 2005-11-20
...and talking of font rendering, how does one get freetype2 onto the system? That promises rendering of MS-Cleartype standard.

m.

---

### Post by mechanic on 2005-11-20
[QUOTE=mechanic]...and talking of font rendering, how does one get freetype2 onto the system? That promises rendering of MS-Cleartype standard.[/QUOTE]
Following the shouts of "RTFM, mechanic, you lazy ***!" I see there is a library for FT2 installed in Breezy, and reading the FAQ in /usr/share/doc/libfreetype6/ft2faq.html I see (I think!) that we would expect programmers to include this stuff in their progs at compile time. So why is font rendering so poor? Is it just particular progs ( and perhaps particular fonts) that work properly? Is there a tuning tool like the MSFT clear-type one - which works superbly? Are we just waiting for the Ubuntu programmers to catch up with this stuff?

m.

---

### Post by manicka on 2005-11-20
The font rendering in breezy is oustanding

---

### Post by bfonseca on 2005-11-20
hey thanks for the .font file it works great.  I can see the difference

---

### Post by BLTicklemonster on 2005-11-20
[QUOTE=bfonseca]hey thanks for the .font file it works great.  I can see the difference[/QUOTE]
Freaking amazin' ain't it? My fonts in firefox look way better than ever.

---

### Post by transactionlogfiller on 2005-11-20
Awesome, thanks.

---

### Post by timczer on 2005-11-20
It was funny, I saw this font file in BLTicklemonster's sig and copied it as directed.  I was doing some work on a video so I totally forgot that I had put it in there.  It was a day or so later when I rebooted and my firefox were much better than they were.  I forgot about this file until I read this post, so a belated thanks.

---

### Post by Raeth on 2006-01-02
[QUOTE=zenwhen]Yes, but auto hinting is not configurable with that utility. This is something you have to do manually until the gnome devs drop it into that tool.[/QUOTE]
You can make a compromise and run 'sudo dpkg-reconfigure fontconfig'.

---

### Post by garba on 2006-01-02
this trick is a god-send, thanks, but why on earth isn't this autohint thingie enabled by default? so far everybody seems to have been extremely happy with this tweak... besides, I would reccomend saving the contents of that file to /etc/fonts/local.conf to get autohinting even in kdm.

besides, thanks again!

---

### Post by markus79 on 2006-01-10
Wow!

---

### Post by BinaryDigit on 2006-01-13
This is SO awesome! I am extremely happy!!!

---

### Post by rykel on 2006-01-14
[QUOTE=zenwhen]Drop this file in your home directory renamed to ".fonts.conf" and log out and in again. It turns on auto hinting and makes your fonts sexy smooth.  :grin:


Edit: Oops, typo.[/QUOTE]

hi, i just followed ur instruction in breezy... does it work still? thanks!!!

---

### Post by bored2k on 2006-01-26
Glad this still works.

---

### Post by vassalle on 2006-04-27
does this still work in dapper? :D

---

### Post by Deusiah on 2006-05-03
Just tried it in Dapper Beta 2 and it still works and looks great! One thing to note however is that it only works with the Best Shapes and Best Contrast option, obviously it will not work with the Monochrome option but the Subpixel Smoothing option seems to make the fonts go back to their smooth but not quite smooth enough option. Still this is far from a problem as Subpixel Smoothing always introduced ugly colours around the edges of my fonts that were very noticable. I always use Best Shapes as I find best contrast looks good but tends to distort the spacing of fonts.

---

### Post by tsb on 2006-05-12
different strokes I guess

made my fonts look like garbage IMO 

I like no sub pixel shading best

---

### Post by oyvindaa on 2006-05-13
Yes this worked very well zenwhen. Thanks :)

---

### Post by diegoe on 2006-05-25
If you are using Dapper try my packages here:

[http://ubuntuforums.org/showthread.php?t=182164](http://ubuntuforums.org/showthread.php?t=182164)

---

### Post by CronoDekar on 2006-06-07
Holy wow, I know this is an old thread... but I just installed this on Dapper and it is quite awesome.  The Opera fonts are quite beautiful.  Mucho thanks!

---

### Post by Aramil on 2006-06-07
I followed the simple instructions but nothing happened....Did I do something wrong?When you mean home u mean  e.x /home/user/ right?

---

### Post by CronoDekar on 2006-06-07
Yeah, that's the right folder.  Be sure to make it .font.conf, with the dot at the beginning.  Missed that the first time I did it :)

---

### Post by basse1989 on 2006-06-08
digged ^^

---

### Post by digs on 2006-06-08
Does this override the bytecode thing with microsoft's TTF fonts? After trying this, tahoma and arial looks like freetype2 with bytecode disabled (the default install). The X fonts look better but the TTFs looks like it reverted back with bytecode disabled.

---

### Post by digs on 2006-06-08
With this hack arial & tahoma looks squished - which is what it originally looks like with bytecode disabled & subpixel hinting. For those with bytecode enabled: are you seeing the same squished letters after this hack? I know I am.

---

### Post by nocloud on 2006-06-09
my fonts look kinda blurry and fuzzy around the edges, but other than that, it looks pretty good, but....i wish it was a little bit more clear

also, where is the subpixel settings in kubuntu dapper?

---

### Post by Chris Tucker on 2006-06-11
omg! sooo smoooth!

in firefox everything is so smooth it looks ... bigger! i had to reduce my font size in FF to make it look nice :) 
i love it, but its so nice it almost burns the eyes

---

### Post by larryni on 2006-06-13
Wow, this is really neat. It makes quite a difference. Thanks.

---

### Post by dasnk on 2006-06-17
After a lot of struggling I think I managed to get my fonts almost perfect now.

---

### Post by smartov on 2006-09-27
Seems to look better. Thanks

---

### Post by imaginos on 2006-10-04
Is the file "fonts.txt" from the first post good for setting Ubuntu 6.06 fonts?

I can not download the file. When I click on it's name, instead of starting download manager, forum asks me about my user/pass (which both are entered and ok) and says something aboutmy privilegdes.

---

### Post by LuisC-SM on 2006-10-06
Hi.
Just open your prefered text editor, copy this code and save it as **.fonts.conf** in your $HOME directory (don't forget the first "dot" in .fonts.conf)
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>

```

Regards

Luis C. Suárez

---

### Post by dagnabit dang doohickey on 2006-10-08
LCD users may get even better results if you use the following code in your .fonts.conf file. This may work for CRT users as well, but I cannot confirm since I have only used this on my laptop.

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">

<!-- the cathectic LCD tweaks, from linuxquestions.org,
http://www.linuxquestions.org/questions/showthread.php?postid=1361098#post1361098
-->

<fontconfig>

<!-- Disable sub-pixel rendering. X detects it anyway, and if you set
this as well, it just looks really horrible  -->
<match target="font" >
 <edit mode="assign" name="rgba" >
  <const>none</const>
 </edit>
 </match>
 <match target="font" >
 <edit mode="assign" name="hinting">
  <bool>true</bool>
 </edit>
 </match>
 <match target="font" >
 <edit mode="assign" name="hintstyle">
  <const>hintfull</const>
 </edit>
 </match>

<!-- The first part of the 'magic.' This makes the fonts start to look
nice, but some of the shapes will be distorted, so hinting is needed
still -->
 <match target="font" >
 <edit mode="assign" name="antialias">
  <bool>true</bool>
 </edit>
 </match>

<!-- Autohinter is not turned on automatically. Only disable this if
you have recompiled Freetype with the bytecode interpreter, which is
run automatically. Although to be honest, Freetype are right, there
isn't much difference between the two. Note that OpenOffice is built
against the bytecode interpreter, so even if you have compiled it and
override it with the autohinter, OOo will still use the bytecode
interpreter -->
 <match target="pattern" >
 <edit mode="assign" name="autohint">
  <bool>true</bool>
 </edit>
 </match>

<!-- Helvetica is a non true type font, and will look bad. This
replaces it with whatever is the default sans-serif font -->
 <match target="pattern" name="family" >
 <test name="family" qual="any" >
  <string>Helvetica</string>
 </test>
 <edit mode="assign" name="family" >
  <string>sans-serif</string>
 </edit>
 </match>
 <dir>~/.fonts</dir>
</fontconfig>
```


I found this hack [here]("http://www.michael-and-mary.net/?q=node/440")*[michael-and-mary.net]*, who in turn found it from it's original creator [here]("http://www.linuxquestions.org/questions/showthread.php?postid=1361098#post1361098")*[linuxquestions.org]*.

---

### Post by dolphinsonar on 2006-10-08
Hrm, maybe stupid question.  Where is home?

Nevermind.

---

### Post by Ocxic on 2006-10-08
Drool.....

---

### Post by SkyNet2029 on 2006-10-09
Excellent! My KDE finally has that 'wet lollipop' sheen to it..figured I would lower the Gamma while I was there..heh. Thanks for the info.

---

### Post by Ben Sprinkle on 2006-10-09
What's auto-hinting?

---

### Post by xpod on 2006-10-09
It`s a subtle request that you put the fag oot

---

### Post by krypto_wizard on 2006-10-12
I just did what OP had suggested in the first post.

How do I go back on the fonts I had back then.

I am using Dapper. Please help.

Thanks

---

### Post by louistan3 on 2006-10-13
this is cool! thanks!

---

### Post by dagnabit dang doohickey on 2006-10-13
> **krypto_wizard said:**
> I just did what OP had suggested in the first post.

How do I go back on the fonts I had back then.

I am using Dapper. Please help.

Thanks

```
rm .fonts.conf
```

---

### Post by krypto_wizard on 2006-10-13
For most part I like the new fonts except for few places where it is kind of thick.

Any comments on it.

Thanks

> **dagnabit dang doohickey said:**
> ```
rm .fonts.conf
```

---

### Post by dagnabit dang doohickey on 2006-10-13
> **krypto_wizard said:**
> For most part I like the new fonts except for few places where it is kind of thick.

Any comments on it.

Thanks

You can try [this fix]("http://ubuntuforums.org/showpost.php?p=1594174&postcount=118") I posted on the previous page. It's what I currently use and it gives the best results I've seen so far.

---

### Post by krypto_wizard on 2006-10-13
Thanks, works like a charm!!!.

> **dagnabit dang doohickey said:**
> You can try [this fix]("http://ubuntuforums.org/showpost.php?p=1594174&postcount=118") I posted on the previous page. It's what I currently use and it gives the best results I've seen so far.

---

### Post by a.v.l on 2006-12-22
> **zenwhen said:**
> Drop this file in your home directory renamed to ".fonts.conf" and log out and in again. It turns on auto hinting and makes your fonts sexy smooth.  :grin:


Edit: Oops, typo.

Thanks for that, It has improved things a little, but still a way to go yet.

---

### Post by EdThaSlayer on 2006-12-22
Wow...my fonts are so smooth...now...thanks a lot!

---

### Post by crimesaucer on 2007-01-18
This is an old thread, but it's still on the edgy wiki for smooth fonts. I had found sub pixel rendering in the user interface settings "Font Rendering", and check all three boxes. It made all my fonts smooth.

Then I added the .fonts.conf from the wiki page and I didn't notice much of a change. Now whenever I use terminal and run mousepad, I get this error:

```
blah@blah-blah:~$ sudo mousepad ~/.fonts.conf
Password:
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
blah@blah-blah:~$ 

```

Should line one be written differently?

```
<?xml version=”1.0” ?>
<!DOCTYPE fontconfig SYSTEM “fonts.dtd”>
<fontconfig>
<match target=”font”>
<edit name=”autohint” mode=”assign”>
<bool>true</bool>
</edit>
</match>
</fontconfig>
```

---

### Post by mohrt on 2007-01-23
I was able to fix the XML validation notices by changing the quotes:

```
<?xml version='1.0' ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target='font'>
<edit name='autohint' mode='assign'>
<bool>true</bool>
</edit>
</match>
</fontconfig>

```

---

### Post by ferd on 2007-04-27
> **dagnabit dang doohickey said:**
> LCD users may get even better results if you use the following code in your .fonts.conf file. This may work for CRT users as well, but I cannot confirm since I have only used this on my laptop.

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">

<!-- the cathectic LCD tweaks, from linuxquestions.org,
http://www.linuxquestions.org/questions/showthread.php?postid=1361098#post1361098
-->

<fontconfig>

<!-- Disable sub-pixel rendering. X detects it anyway, and if you set
this as well, it just looks really horrible  -->
<match target="font" >
 <edit mode="assign" name="rgba" >
  <const>none</const>
 </edit>
 </match>
 <match target="font" >
 <edit mode="assign" name="hinting">
  <bool>true</bool>
 </edit>
 </match>
 <match target="font" >
 <edit mode="assign" name="hintstyle">
  <const>hintfull</const>
 </edit>
 </match>

<!-- The first part of the 'magic.' This makes the fonts start to look
nice, but some of the shapes will be distorted, so hinting is needed
still -->
 <match target="font" >
 <edit mode="assign" name="antialias">
  <bool>true</bool>
 </edit>
 </match>

<!-- Autohinter is not turned on automatically. Only disable this if
you have recompiled Freetype with the bytecode interpreter, which is
run automatically. Although to be honest, Freetype are right, there
isn't much difference between the two. Note that OpenOffice is built
against the bytecode interpreter, so even if you have compiled it and
override it with the autohinter, OOo will still use the bytecode
interpreter -->
 <match target="pattern" >
 <edit mode="assign" name="autohint">
  <bool>true</bool>
 </edit>
 </match>

<!-- Helvetica is a non true type font, and will look bad. This
replaces it with whatever is the default sans-serif font -->
 <match target="pattern" name="family" >
 <test name="family" qual="any" >
  <string>Helvetica</string>
 </test>
 <edit mode="assign" name="family" >
  <string>sans-serif</string>
 </edit>
 </match>
 <dir>~/.fonts</dir>
</fontconfig>
```


I found this hack [here]("http://www.michael-and-mary.net/?q=node/440")*[michael-and-mary.net]*, who in turn found it from it's original creator [here]("http://www.linuxquestions.org/questions/showthread.php?postid=1361098#post1361098")*[linuxquestions.org]*.

I did this and now I have boxes instead of fonts in fasterfox and kde and gedit. I am looking for help on how to restore the original fonts.conf file. I am using opera to type this. Thanks fo all help:confused: I resolved this by using a live CD and replacing fonts.conf with a backup. Thanks for reading.

---

### Post by Alkaif on 2007-04-30
hi there,

i did this and also updated the freetype lib thingy for my edgy install so its automatically smooth... (followed the ubuntuguide.org way) and now i was wondering is there a way to make wine applications have smoother fonts? I managed to install office2003 using wine (works great) but the fonts are not smoothened at all. No cleartype or nothing.

if someone can help me out a little that'd be awesome :).

cheers,
Alkaif.

---

### Post by krypto_wizard on 2007-04-30
I am now using Feisty Fawn. Your .fonts.conf was working great for me till I was using edgy. 

I did an upgrade to Feisty and my fonts don't look smooth anymore.

What should I do ?

My .fonts.conf looks like

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">

<!-- the cathectic LCD tweaks, from linuxquestions.org,
http://www.linuxquestions.org/questions/showthread.php?postid=1361098#post1361098
-->

<fontconfig>

<!-- Disable sub-pixel rendering. X detects it anyway, and if you set
this as well, it just looks really horrible  -->
<match target="font" >
 <edit mode="assign" name="rgba" >
  <const>none</const>
 </edit>
 </match>
 <match target="font" >
 <edit mode="assign" name="hinting">
  <bool>true</bool>
 </edit>
 </match>
 <match target="font" >
 <edit mode="assign" name="hintstyle">
  <const>hintfull</const>
 </edit>
 </match>

<!-- The first part of the 'magic.' This makes the fonts start to look
nice, but some of the shapes will be distorted, so hinting is needed
still -->
 <match target="font" >
 <edit mode="assign" name="antialias">
  <bool>true</bool>
 </edit>
 </match>

<!-- Autohinter is not turned on automatically. Only disable this if
you have recompiled Freetype with the bytecode interpreter, which is
run automatically. Although to be honest, Freetype are right, there
isn't much difference between the two. Note that OpenOffice is built
against the bytecode interpreter, so even if you have compiled it and
override it with the autohinter, OOo will still use the bytecode
interpreter -->
 <match target="pattern" >
 <edit mode="assign" name="autohint">
  <bool>true</bool>
 </edit>
 </match>

<!-- Helvetica is a non true type font, and will look bad. This
replaces it with whatever is the default sans-serif font -->
 <match target="pattern" name="family" >
 <test name="family" qual="any" >
  <string>Helvetica</string>
 </test>
 <edit mode="assign" name="family" >
  <string>sans-serif</string>
 </edit>
 </match>
 <dir>~/.fonts</dir>
</fontconfig>

```


Every help is appreciated.

Thanks

> **dagnabit dang doohickey said:**
> You can try [this fix]("http://ubuntuforums.org/showpost.php?p=1594174&postcount=118") I posted on the previous page. It's what I currently use and it gives the best results I've seen so far.

---

### Post by FrancoNero on 2007-05-01
yeah fonts look kinda shittyin feisty, especially openoffice and firefox (those checkboxes and radio buttones even, yuck... vomit)

---

### Post by mciarlo on 2007-05-02
Ditto--firefox, epiphany, and in general, everywhere.

---

### Post by kaede on 2007-05-03
so this trick don't work anymore in feisy ?

---

### Post by hype on 2007-05-03
Hi, it just works on feisty, but you have to change the [** " **]'s by [** ' **]'s.

Here it is:
```
<?xml version='1.0' ?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
<match target='font'>
<edit name='autohint' mode='assign'>
<bool>true</bool>
</edit>
</match>
</fontconfig>

```

The "XML declaration not well-formed" error is now gone, and  i now , like said, just drool over my fonts.
Small fonts size are more sharp , precise. Nice !

Thanks for info. :)

---

### Post by episodic on 2007-05-04
Thanks - after reading various schemes for over an hour, I found this simple tweak!

This works feisty users! - and well.


> **dagnabit dang doohickey said:**
> LCD users may get even better results if you use the following code in your .fonts.conf file. This may work for CRT users as well, but I cannot confirm since I have only used this on my laptop.

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">

<!-- the cathectic LCD tweaks, from linuxquestions.org,
http://www.linuxquestions.org/questions/showthread.php?postid=1361098#post1361098
-->

<fontconfig>

<!-- Disable sub-pixel rendering. X detects it anyway, and if you set
this as well, it just looks really horrible  -->
<match target="font" >
 <edit mode="assign" name="rgba" >
  <const>none</const>
 </edit>
 </match>
 <match target="font" >
 <edit mode="assign" name="hinting">
  <bool>true</bool>
 </edit>
 </match>
 <match target="font" >
 <edit mode="assign" name="hintstyle">
  <const>hintfull</const>
 </edit>
 </match>

<!-- The first part of the 'magic.' This makes the fonts start to look
nice, but some of the shapes will be distorted, so hinting is needed
still -->
 <match target="font" >
 <edit mode="assign" name="antialias">
  <bool>true</bool>
 </edit>
 </match>

<!-- Autohinter is not turned on automatically. Only disable this if
you have recompiled Freetype with the bytecode interpreter, which is
run automatically. Although to be honest, Freetype are right, there
isn't much difference between the two. Note that OpenOffice is built
against the bytecode interpreter, so even if you have compiled it and
override it with the autohinter, OOo will still use the bytecode
interpreter -->
 <match target="pattern" >
 <edit mode="assign" name="autohint">
  <bool>true</bool>
 </edit>
 </match>

<!-- Helvetica is a non true type font, and will look bad. This
replaces it with whatever is the default sans-serif font -->
 <match target="pattern" name="family" >
 <test name="family" qual="any" >
  <string>Helvetica</string>
 </test>
 <edit mode="assign" name="family" >
  <string>sans-serif</string>
 </edit>
 </match>
 <dir>~/.fonts</dir>
</fontconfig>
```


I found this hack [here]("http://www.michael-and-mary.net/?q=node/440")*[michael-and-mary.net]*, who in turn found it from it's original creator [here]("http://www.linuxquestions.org/questions/showthread.php?postid=1361098#post1361098")*[linuxquestions.org]*.

---

### Post by goodtimetribe on 2007-05-04
This worked great for me. Thanks!

---

### Post by anselm on 2007-05-12
worked for me also  :)

---

### Post by mechanic on 2007-05-12
So can someone explain how, after several versions of Ubuntu, these settings aren't built in or accessible from the System menu?

Regds, m.

---

### Post by md5hash on 2007-05-17
thanks alot, really cool

---

### Post by Lucifiel on 2007-05-17
> **cmsj said:**
> Something else worth checking is that Gnome is feeding freetype the correct DPI. I'm sure it used to guess this, but both my hoary boxes were wrong when I checked just now.

Firstly, open a terminal and run:

xdpyinfo | grep dots

and you should see something like this:

-(cmsj@tenshu)-(~)- xdpyinfo | grep dots
  resolution:    112x112 dots per inch

Now fire up Gnome's font preferences and click the Details button, set the DPI value in there to, in this case, 112. I'm not 100% sure what you do when your display has unequal horizontal and vertical DPIs, which does seem to happen, but I usually pick a value somewhere in the middle.
In my case Gnome on both machines was at 96, so setting it to 112 makes font sizes larger. You can tweak these down to the same sizes you had before, but in theory it should be rendering them better at that size. Combine that with the autohinting and you should have some very pretty fonts :)


That's a really interesting tip!! :)

Hmmm... when I set my DPI at 112, the font became really large but very blurry. Thus, I'd recommend that everyone pick a value slightly lower like 105. 

Note: after I adjusted my DPI to 105, the fonts on my desktop like sda2 , hdc3, etc. became a lot clearer. 

Oh and speaking of desktop fonts, does anyone know how to make all desktop icons display the font in black with the drop-down effects turned off?

---

### Post by Kobalt on 2007-05-21
Man this little piece of .conf is just awsome... Thanks a bunch zenwhen !

---

### Post by stchman on 2007-05-23
Give your Ubuntu that XP look with fonts:

[http://www.stchman.com/ms_fonts.html](http://www.stchman.com/ms_fonts.html)

This works like a charm.

---

### Post by dbbolton on 2007-05-24
simply awesome.

---

### Post by ahawks on 2007-05-25
What's amazing is this thread was started in 2004, and today in May 2007 people are still posting "awesome!", and it's still not a feature of gnome-font-properties.

I just copied-pasted the xml into my existing .fonts.conf and it does indeed look sweet. 

A note though: I only see a difference above a certain font size. For example, using Bitstream Vera Sans Roman, the text looks normal at 10pt, but super smooth at 11pt and above.

---

### Post by Can0n on 2007-05-25
Cant someone upload a before and after screenshot?

---

### Post by XTREEM|RAGE on 2007-06-03
men it really looks sexy! :D Tnx!

---

### Post by r0ydster on 2007-06-13
Finally!!

This makes it look like clear-type in winblows.

Very nice - good find!.

MIke

---

### Post by burnt water on 2007-06-13
> **Can0n said:**
> Cant someone upload a before and after screenshot?


Agreed.

---

### Post by mack1082 on 2007-06-13
Looks much better now.  Thanks for the tip. :D

---

### Post by Garret88 on 2007-06-14
It works perfectly: i see the difference ;)

---

### Post by r0ydster on 2007-06-14
I have before and after shots of Firefox:

Before:

[IMG]http://www.mdrcs.com/images/before.png[/IMG]

After:

[IMG]http://www.mdrcs.com/images/after.png[/IMG]


Mike

---

### Post by huygens on 2007-06-25
> **ahawks said:**
> What's amazing is this thread was started in 2004, and today in May 2007 people are still posting "awesome!", and it's still not a feature of gnome-font-properties.

I think you did not see the option in the Font properties then. I'm using Ubuntu 7.04 and I can modify the hinting within System -> Preferences -> Font. Just click on the "Details" button and you will be able to change the hinting of the fonts.

So this was applicable in 2004 and nowadays you can use a nice GUI for that.

Btw, I do not have a .fonts.conf in my home directory, and my fonts look like they are properly hinted, just like on the various screenshot of this thread.

---

### Post by Enverex on 2007-06-25
Agreed, I just choose "Best Shapes" (or was it contrast) in Gnome's Font thing and they look fine... not quite sure why no-one else can do that...

---

### Post by Lou Quillio on 2007-06-25
Seems like Gnome trumps .fonts.conf with similarly-behaved prefs stored in gconf keys -- which won't help folks who use XFCE.  What the world could *really* use is a GUI tool for configuring .fonts.conf et al., and a way to opt-out of your desktop environment's closed scheme.  Sounds like a job for FreeDesktop.org.

LQ

---

### Post by cdupree on 2007-07-30
Worked on my Kubuntu installation too.  Many thanks!  My Ubuntu came this way, and I loved the fonts.  I'm so glad to get Kubuntu to use them.  Now I don't have any reason to go back.

---

### Post by michael37 on 2007-09-29
It does look better, but I would strongly encourage all LCD users (including all notebooks users) to select

System->Preferences->Font

and select "Subpixel smoothing (LCD)" before making this change.

---

### Post by cn9ne on 2007-09-29
Wow, cool man! It looks way way better! :guitar:

---

### Post by LuisC-SM on 2007-09-29
> **michael37 said:**
> It does look better, but I would strongly encourage all LCD users (including all notebooks users) to select

System->Preferences->Font

and select "Subpixel smoothing (LCD)" before making this change.

I just have to agree. On Feisty this is just enough.... on gutsy, there is no need... everything looks so cool :)

---

### Post by stoomaroo on 2007-10-08
Slick...just slick.

Nice one.

Stoomaroo

---

### Post by darundal on 2007-10-22
For some reason, my Gutsy install is deleting .fonts.conf. I had it in my home directory when I upgraded, and it deleted it. I tried replacing the file, and again, it was deleted. Yes, I had view hidden files enabled. Anyone know why it is doing this?

---

### Post by dgoosens on 2007-10-30
hi,
just wanted to point out that this also works for Gutsy Gibbon...
the file is not deleted (hidden though)
great
thanks a lot !!!!!

---

### Post by rykel on 2007-10-31
Hi all,

I screwed up my Gutsy install and despite spending 20 min with **dpkg-reconfigure -a** the fonts in my Firefox are now skinny-scrawly (UGLY)...

How can I reset the fonts system-wide? Thanks for advice.

UPDATE: I installed msttcorefonts and it partially solved the Firefox in-screen ugly fonts problem... some are still showing up as skinny-scrawly fonts, while some others are OK... how can I reset the Firefox fonts to the default Gutsy ones?

---

### Post by RebateFX on 2007-11-07
Nice. It was just the thing to make my Ubuntu put windows to shame :)

---

### Post by DecemberWinds on 2007-12-30
Um... how do you access this home directory folder? sorry noob here.

---

### Post by dlegend on 2007-12-31
> **DecemberWinds said:**
> Um... how do you access this home directory folder? sorry noob here.

The path is **~/** or **/home/username**. Type that into the file browser path and you should be in your home directory =)

---

### Post by pawitp on 2007-12-31
The preferred way to do this on gutsy is:
```
sudo ln -sf /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/
```

---

### Post by demigod on 2008-01-12
Thanks :) really it worked

---

### Post by bill_greene on 2008-01-29
> **zenwhen said:**
> Drop this file in your home directory renamed to ".fonts.conf" and log out and in again. It turns on auto hinting and makes your fonts sexy smooth.  :grin:


Edit: Oops, typo.

Thanks, looks world better. ;)

---

### Post by gnuyoga on 2008-02-02
thanks man.. it works in my gutsy. am loving it ;-)

---

### Post by randyrick on 2008-02-09
Big difference, thank you, thank you!

---

### Post by doorknob60 on 2008-02-13
I did this, and it made things look weird (I want it back). I did the gusty method a few posts up. Please help! PM me instead of post also.

---

### Post by hgurol on 2008-02-16
> **doorknob60 said:**
> I did this, and it made things look weird (I want it back). I did the gusty method a few posts up. Please help! PM me instead of post also.

Open up your /etc/fonts/conf.d/ file. Find and delete below section, save the file and restart X.

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- debian/autohint.conf -->
<fontconfig>
<!--  Use the Autohinter --> 
  <match target="font">
    <edit name="autohint" mode="assign"><bool>true</bool></edit>
  </match>
</fontconfig>


```

---

### Post by guevara on 2008-04-27
> **pawitp said:**
> The preferred way to do this on gutsy is:
```
sudo ln -sf /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/
```

oh damn, it's really working. Thank u man you solved my problem :guitar:

---

### Post by QwUo173Hy on 2008-04-27
Will this make the fonts look better on Hardy too? My fonts seem okay, but I'm not quite drooling.

---

### Post by guevara on 2008-04-28
> **jarlath said:**
> Will this make the fonts look better on Hardy too? My fonts seem okay, but I'm not quite drooling.
yep, i tried it on Hardy. Working so good.

---

### Post by hannah187 on 2008-04-28
So I did on my Hardy as well. Perfect..thanks for this hack

---

### Post by QwUo173Hy on 2008-04-28
> **ale said:**
> ...this is indeed a very nice option; however fonts will get a bit blurrier. but the correct scaling compensates for that
Hi ale, I'm finding the fonts a bit smudged looking too. What do you mean by scaling?

---

### Post by K.Morgan on 2008-04-29
Not sure how everybody seems to be getting clear fonts, but I've done everything in this thread and nothing changed, still got blurry fonts.

Kristian

---

### Post by fooman on 2008-05-04
> **K.Morgan said:**
> Not sure how everybody seems to be getting clear fonts, but I've done everything in this thread and nothing changed, still got blurry fonts.

Kristian

this post works best for me (yes, i'm using hardy)....

[http://ubuntuforums.org/showpost.php?p=4049873&postcount=172](http://ubuntuforums.org/showpost.php?p=4049873&postcount=172)

---

### Post by ujwal10101 on 2008-07-16
People have been saying that you can do the same thing (I'm on Hardy) from System->Preferences->Appearance, Fonts tab. I tried it out myself and found out it does work but it doesn't seem to make the changes globally/system-wide (I think it only works for the default GNOME apps like Rhythmbox, Nautilus etc.). 

For e.g. the tool bars in Firefox looked awesome but the text of the web pages looked horrible.
The .fonts.conf seems to make them beautiful in every app (and all components).

I would appreciate it if anyone could test if my hunch is correct.

---

### Post by L815 on 2008-07-16
I didn't think this would make much of a difference, but decided to give it a try.

I must say, NICE JOB :D
It has made my browser fonts much more readable and doesn't make some fonts huge compared to previous settings.

One bad thing I noticed is the mini i when bolded at a certain font size is hard to distinguish between an l.

---

### Post by tobiasly on 2008-08-01
> **pawitp said:**
> The preferred way to do this on gutsy is:
```
sudo ln -sf /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/
```

Yes yes yes yes!! THANK YOU! OMG I have spent **SO** long trying to get my fonts to not be ugly as sin on my 21" LCD at 1680x1050. I'm using Hardy 8.04 and I've spent hours switching out every different combination of font sizes, msttcorefonts, liberation fonts, gsfonts, subpixel smoothing, full/slight/no hinting, fc-config -f -v, restarting X, rebooting, EVERYTHING, and none of it worked until this!

For those who think you can get the same effect by going to Advanced under Font Settings, you can't! This is different from selecting Full Hinting or Subpixel Rendering, because I had tried them ALL before!

So now my only question is: why in the world is this so hard to find, and why isn't it on by default?! It's crap like this that perpetuates the perception that Linux is only for power users because you have to use the command line for too much. Mr. Shuttleworth, you said Ubuntu's goal is to be prettier than Apple's OSX, well this thread should be a testament to you: making fonts look awesome out of the box is very important for a lot of people, and hopefully it gets better sooner rather than later!

Thanks again for the original poster and for # 172 who showed how to do it the "right" way by simlinking into /etc/fonts/conf.d. I'd click Thanks for both of you but I guess your post is too old to enable it.

---

### Post by tom957 on 2008-08-02
man, this looks good!

> **pawitp said:**
> The preferred way to do this on gutsy is:
```
sudo ln -sf /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/
```

---

### Post by Cool Surfer on 2008-08-02
where is the home directory pl and how do I rename it.
:confused::confused::confused:

---

### Post by Anthony T. on 2008-08-02
wow nice, it works

---

### Post by kamiokande on 2008-08-07
> **pawitp said:**
> The preferred way to do this on gutsy is:
```
sudo ln -sf /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/
```

Thanks for the tip. It works really well on my desktop and most applications. However, I noticed that the fonts on some areas of the Ubuntu forums are now warped! Has anyone had this happen before?

(check out the red font on the right)

---

### Post by RavUn on 2008-08-07
> **kamiokande said:**
> Thanks for the tip. It works really well on my desktop and most applications. However, I noticed that the fonts on some areas of the Ubuntu forums are now warped! Has anyone had this happen before?

(check out the red font on the right)

That's happened to me one time before.  It was REAL bad... I restarted firefox and it was fine and hasn't happened since.  I had a lot of processes running and my CPU was at 100% so I don't know if that had something to do with it.

---

### Post by kamiokande on 2008-08-07
> **RavUn said:**
> That's happened to me one time before.  It was REAL bad... I restarted firefox and it was fine and hasn't happened since.  I had a lot of processes running and my CPU was at 100% so I don't know if that had something to do with it.

Yea, after coming back to the site a few times, I've noticed it only happens on some occasions. Strange. I'll consider my CPU usage the next time it happens.

---

### Post by jarrhed on 2008-08-08
The best guide is the one on UbuntuSite.com, it gives fonts that are just as good as Windows and maybe even better

---

### Post by dulus on 2008-08-19
Here is guide too: [http://ubuntuforums.org/showthread.php?t=800724&highlight=nice+font+rendering]("http://ubuntuforums.org/showthread.php?t=800724&highlight=nice+font+rendering")

---

### Post by kamitsukai on 2008-08-19
> **pawitp said:**
> The preferred way to do this on gutsy is:
```
sudo ln -sf /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/
```

Oh yer yummy fonts:KS

---

### Post by aZn137 on 2008-09-19
uh-oh. i dont like the new look. how do you undo the change??

---

### Post by thegizmoguy on 2008-12-09
It's better but still doesn't look quite right (rocking the ms xp and vista fonts).  If you look at the Brainstorm section I believe the font fix one has +1600.

---

### Post by gakudva on 2008-12-27
Wow! ".fonts.conf" in home directory works like charm :KS

I have this setup since few hours now... and I am still drooling over the great looking fonts in my firefox.

thanks so much
best regards, Ganesh

---

### Post by pedrogfrancisco on 2009-01-09
> **tobiasly said:**
> So now my only question is: why in the world is this so hard to find, and why isn't it on by default?! It's crap like this that perpetuates the perception that Linux is only for power users because you have to use the command line for too much. Mr. Shuttleworth, you said Ubuntu's goal is to be prettier than Apple's OSX, well this thread should be a testament to you: making fonts look awesome out of the box is very important for a lot of people, and hopefully it gets better sooner rather than later!

According to [http://www.spodesabode.com/discussion/51/making-ubuntu-look-better/]("http://www.spodesabode.com/discussion/51/making-ubuntu-look-better/") that technique is a patented Apple one...

---

### Post by x12796 on 2009-01-17
I just used the sudo command sudo ln -sf /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/  that was posted earlier in 8.10 and it works rather nicely.

---

### Post by bbarcelo on 2009-02-25
> **hgurol said:**
> Open up your /etc/fonts/conf.d/ file. Find and delete below section, save the file and restart X.

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- debian/autohint.conf -->
<fontconfig>
<!--  Use the Autohinter --> 
  <match target="font">
    <edit name="autohint" mode="assign"><bool>true</bool></edit>
  </match>
</fontconfig>


```

I just used ```
sudo ln -sf /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/
``` in Intrepid 8.10 but don't like the results. I'd like to undo this action and restore the default way fonts are rendered. I've quoted an earlier poster's solution to do so but don't believe it's the correct/best method to do this. Isn't all that is needed to unlink the files? I tried ```
sudo unlink /etc/fonts/conf.d
``` but I am returned the message that it is a directory. This is true whether or not I include the trailing directory slash.

Any ideas?

---

### Post by unutbu on 2009-02-25
Try this:
```
sudo ln -sf /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/10-autohint.conf
```

---

### Post by bbarcelo on 2009-02-27
> **unutbu said:**
> Try this:
```
sudo ln -sf /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/10-autohint.conf
```

Good idea, this should restore the default configuration.

---

### Post by cannonfodder on 2009-04-23
This is in response to kamiokande who said: 
> 
Thanks for the tip. It works really well on my desktop and most applications. However, I noticed that the fonts on some areas of the Ubuntu forums are now warped! Has anyone had this happen before?

I read (I can't recall where, unfortunately) that this happens on systems w/o the Tahoma font installed. 

The HTML / CSS on the Ubuntu forums site calls for Tahoma bold in some spots. The blurriness is a result of the system trying to mimick Tahoma bold and not doing too great a job.

Install Tahoma and the problem goes away, i.e., text will display as intended.

---

### Post by cofcof on 2012-07-24
> **zenwhen said:**
> Drop this file in your home directory renamed to ".fonts.conf" and log out and in again. It turns on auto hinting and makes your fonts sexy smooth.  :grin:


Edit: Oops, typo.

That works amazingly for me!

I spend maybe 10 hours trying different stuff to fix my font settings. I am using Fedora 17 on LXDE, and the fonts just didn't look good, no matter what I tried, but now it finally looks fine!

Thanks!

---

### Post by mechanic on 2012-07-25
I can't believe we're still getting posts on a thread that started nearly eight years ago! What's so hard about smoothing fonts - MS-Windows have had ClearType for years and even Linux distros are usually pretty clean on fonts these days. This issue is so last century!

---

### Post by DGINSD on 2012-07-26
Just curious  is this tip still valid on 12.04?

---

