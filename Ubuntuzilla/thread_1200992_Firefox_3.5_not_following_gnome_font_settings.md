---
title: "Firefox 3.5 not following gnome font settings"
date: 2009-06-30
forum: Ubuntuzilla
---

### Post by Pulka on 2009-06-30
Firefox 3.5 doesn't follow my font hinting settings in Gnome. I've got the impression Firefox is not linking to the system Cairo but to something internal. Is there a workaround? Many thanks in advance.

---

### Post by nanotube on 2009-06-30
Hi
indeed, i noticed that too...

don't know of a way to fix it, but here's a launchpad bug filed about it, which may eventually contain useful info about fixes or workarounds:
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/379761](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/379761)

(there's a purported workaround posted there, but a later post claims it doesn't work...)

---

### Post by aceat64 on 2009-07-01
I managed to get subpixel smoothing working, I created a file in my home directory called ".fonts.conf" and put this in it:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```

Something to keep in mind is that I'm using full smoothing, not medium or slight so your settings may be different.

---

### Post by michaelzap on 2009-07-01
> **aceat64 said:**
> I managed to get subpixel smoothing working, I created a file in my home directory called ".fonts.conf" and put this in it:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```

Something to keep in mind is that I'm using full smoothing, not medium or slight so your settings may be different.

Worked perfectly for me. Thanks! I just changed hintfull to hintslight.

---

### Post by forestwalkerjoe on 2009-07-06
> **aceat64 said:**
> I managed to get subpixel smoothing working, I created a file in my home directory called ".fonts.conf" and put this in it:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```

Something to keep in mind is that I'm using full smoothing, not medium or slight so your settings may be different.

i copied that code from above into a page.. named it the same as you have named it.. and moved it to the PLACES  --  HOME FOLDER.but i see no changes. the text on the LINKS bar is just Heavy BOLD and large. every thing else seems to be ok. will that code you wrote change any thing like that? or did i put it in the wrong place? I named it fonts.conf , that is what you were saying.. right?

---

### Post by nanotube on 2009-07-06
> **forestwalkerjoe said:**
> i copied that code from above into a page.. named it the same as you have named it.. and moved it to the PLACES  --  HOME FOLDER.but i see no changes. the text on the LINKS bar is just Heavy BOLD and large. every thing else seems to be ok. will that code you wrote change any thing like that? or did i put it in the wrong place? I named it fonts.conf , that is what you were saying.. right?

he says he named it ".fonts.conf" (notice the starting dot)
so try renaming your text file to .fonts.conf, and see if that helps? :)

---

### Post by forestwalkerjoe on 2009-07-06
ok.. i hate to sound like the goober here.. but now i have changed that file to add the DOT.. and i am not sure exactly what changes i was supposed to see. i guess it doesnt look as gaudy as it was.. but what was the full effect supposed to be? 

<thumps self in head for not remembering why we did this in the first place> 

FWJ

---

### Post by nanotube on 2009-07-06
well, if everything is looking good to you, then you don't have to worry about this at all. 

the main "problem" here is that firefox doesn't follow the settings you can set if you go to system -> preferences -> appearance -> fonts

personally, i haven't bothered to do anything about it, since the "unhinted" fonts in firefox look ok to me. :)

---

### Post by londonali1010 on 2009-07-07
My eyes love you!!!  Thanks!

---

### Post by InspirationDate on 2009-07-17
this worked perfectly, thanks!

---

### Post by fonfi on 2009-07-17
Great hint - worked like a charm... :) Thank you!

---

### Post by majikshoe on 2009-07-17
There is another way to fix this - at lest it did for me.

From [http://ubuntuforums.org/showthread.php?p=7616965#post7616965](http://ubuntuforums.org/showthread.php?p=7616965#post7616965)

```

sudo rm /etc/fonts/conf.d/10*
sudo dpkg-reconfigure fontconfig

```

Restart firefox 3.5 and it's done, no manual fiddling with config files required.

---

### Post by pjalegria on 2009-08-06
I have done that:
> sudo rm /etc/fonts/conf.d/10*
sudo dpkg-reconfigure fontconfig

but now my Opera fonts are very bad, how can i revert this?

Thanks

---

### Post by Christofferh on 2009-09-22
> **aceat64 said:**
> I managed to get subpixel smoothing working, I created a file in my home directory called ".fonts.conf" and put this in it:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```

Something to keep in mind is that I'm using full smoothing, not medium or slight so your settings may be different.

Awesome ...this solved the blurry text issues in Firefox...now I just need to hunt down the issue with blurry images.

---

### Post by cyanide on 2009-10-05
> **aceat64 said:**
> I managed to get subpixel smoothing working, I created a file in my home directory called ".fonts.conf" and put this in it:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```

Something to keep in mind is that I'm using full smoothing, not medium or slight so your settings may be different.

I have the same font.conf file. However I am not aware of the full smoothing settings. Can you explain a little more in detail??

It would be nice to have a screenshot of your desktop so that I can compare!!

I would also like to reduce the size of the context menu. Look at my screenshot. It illustrates my problem.

Thanks!!

---

### Post by DrKay on 2009-10-30
Thank you so much! I had installed "Shiretoko" (the development build of Firefox 3.5) under Ubuntu 9.04. I then installed the Kubuntu desktop one day to try it out. After that, the Firefox fonts looked terrible under Ubuntu. I was hoping that upgrading to Karmic 9.10 would fix this problem, but it didn't.

Your fix worked well. Thanks again!

---

### Post by boom2k1 on 2009-11-01
Thanks!
an instant fix.

---

### Post by tiras_dude on 2009-11-09
The fix works in Karmic, but it needs tweaking to fork for you  (as it did for me) 
  
 Here is what you do: 

First go System>Preferences>Appearance 
Select Fonts Tab and play with the settings that work best for you monitor. 
Apply them but don't leave the screen. 
Click "Details" button 
Now Pay attention to screen:

If your best screen setting is as follows: 
Smoothing = Subpixel (LCDs) 
 Hinting= Full
Than copy the original code posted by aceat64 (message 3 in the post)

 Open gedit, paste the xml code in there and save the file with the name .fonts.conf in your home directory (aka ~/) 

If your settings differ from the ones described above do the following: 
 
 Open gedit and paste the code below: 

 <?xml version="1.0"?> 
 <!DOCTYPE fontconfig SYSTEM "fonts.dtd"> 
 <fontconfig> 
  <match target="font" > 
   <edit mode="assign" name="value_smoothing" > 
    <const>smothing_setting</const> 
   </edit> 
  </match> 
  <match target="font" > 
   <edit mode="assign" name="hinting" > 
    <bool>true</bool> 
   </edit> 
  </match> 
  <match target="font" > 
   <edit mode="assign" name="hintstyle" > 
    <const>hint_value</const> 
   </edit> 
  </match> 
  <match target="font" > 
   <edit mode="assign" name="antialias" > 
    <bool>antialias_setting</bool> 
   </edit> 
  </match> 
 </fontconfig> 

 Then replace the following with values below dependent on your setting:

Smoothing values
 value_smoothing - grayscale, none 
 smoothing_setting - grayscale, none 

Hinting values
hint_value - hintnone, hintslight, hintmedium, hintfull 

 antialas_setting - true, false 

Save the file with the name .fonts.conf in your home directory 

Restart Firefox 

If you don't like the way it looks, play with the settings values

This method works only for one user, not system wide and does not break fonts in virtualbox, skype and other apps (apparently dependent on qt4) as for example this method:
 
 sudo rm /etc/fonts/conf.d/10*
 sudo dpkg-reconfigure fontconfig
 
 And is easily reversible: simply delete the .fonts.conf
  
 If you find anything wrong with these instructions, please correct them.

---

### Post by mad-kow on 2009-11-11
Thank you so much for that tip, tiras_dude!
Firefox and VirtualBox are now working again on my system!

---

### Post by waynefoutz on 2009-11-16
> **tiras_dude said:**
> The fix works in Karmic, but it needs tweaking to fork for you  (as it did for me) 
  
 Here is what you do: 

First go System>Preferences>Appearance 
Select Fonts Tab and play with the settings that work best for you monitor. 
Apply them but don't leave the screen. 
Click "Details" button 
Now Pay attention to screen:

If your best screen setting is as follows: 
Smoothing = Subpixel (LCDs) 
 Hinting= Full
Than copy the original code posted by aceat64 (message 3 in the post)

 Open gedit, paste the xml code in there and save the file with the name .fonts.conf in your home directory (aka ~/) 

If your settings differ from the ones described above do the following: 
 
 Open gedit and paste the code below: 

 <?xml version="1.0"?> 
 <!DOCTYPE fontconfig SYSTEM "fonts.dtd"> 
 <fontconfig> 
  <match target="font" > 
   <edit mode="assign" name="value_smoothing" > 
    <const>smothing_setting</const> 
   </edit> 
  </match> 
  <match target="font" > 
   <edit mode="assign" name="hinting" > 
    <bool>true</bool> 
   </edit> 
  </match> 
  <match target="font" > 
   <edit mode="assign" name="hintstyle" > 
    <const>hint_value</const> 
   </edit> 
  </match> 
  <match target="font" > 
   <edit mode="assign" name="antialias" > 
    <bool>antialias_setting</bool> 
   </edit> 
  </match> 
 </fontconfig> 

 Then replace the following with values below dependent on your setting:

Smoothing values
 value_smoothing - grayscale, none 
 smoothing_setting - grayscale, none 

Hinting values
hint_value - hintnone, hintslight, hintmedium, hintfull 

 antialas_setting - true, false 

Save the file with the name .fonts.conf in your home directory 

Restart Firefox 

If you don't like the way it looks, play with the settings values

This method works only for one user, not system wide and does not break fonts in virtualbox, skype and other apps (apparently dependent on qt4) as for example this method:
 
 sudo rm /etc/fonts/conf.d/10*
 sudo dpkg-reconfigure fontconfig
 
 And is easily reversible: simply delete the .fonts.conf
  
 If you find anything wrong with these instructions, please correct them.

Changing the text from "hintfull" to "hintslight" made a world of difference for me.

---

### Post by ElSlunko on 2009-11-16
I also use hintslight.

are rgba and rgb also options for value_smoothing and smooth_setting?

---

### Post by hang-time on 2009-12-29
Open Fire Fox -->  Edit --> Preferences  -->  Content  --> Default font

free Sans  / 16   works for me but your mileage may vary

---

### Post by maxino on 2010-01-09
> **aceat64 said:**
> I managed to get subpixel smoothing working, I created a file in my home directory called ".fonts.conf" and put this in it:
...


> **tiras_dude said:**
> The fix works in Karmic, but it needs tweaking to fork for you  (as it did for me):
...


Great posts, thank you both, guys :-)
I have been looking to get rid of those crappy, blurry, eye-straining Firefox fonts for months.
Now webpages text is crystal clear.

What works (great!) for me is:

smoothing = greyscale
hinting = medium

and in FF preferences I have set:

Proportional: Sans Serif
Serif: DejaVu Serif
Sans-serif: DejaVu Sans
Monospace: DejaVu Sans Mono
Also unticked "Allow pages to use their own fonts..."

Ciao,

---

### Post by phoenix49 on 2010-01-11
My settings are following

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>false</bool>
  </edit>
 </match>
</fontconfig>

Slick fonts. 

Thanks for info!

---

### Post by Eromatic on 2010-01-25
Using a .fonts.conf in the home directory doesn't seem to work for Firefox 3.6. under Hardy 32bit. (Ubuntuzilla install) Is there any way to get font smoothing working here?

---

### Post by nanotube on 2010-01-25
> **Eromatic said:**
> Using a .fonts.conf in the home directory doesn't seem to work for Firefox 3.6. under Hardy 32bit. (Ubuntuzilla install) Is there any way to get font smoothing working here?

it seems that this trick doesn't seem to work for firefox3.6...

don't know what else to suggest.

don't know what the deal is with the fonts really myself, since ff3.6 looks just fine both on my intrepid and my karmic machines, so i didn't have to do anything...

---

### Post by Michalxo on 2010-01-25
Agree, I am unable to set correct fonts for firefox 3.6 either. Probably some interesting bug again :-) Over to Chromium / 3.7 :-)

---

### Post by Eromatic on 2010-01-25
Could it be related to the following?

[http://forums.mozillazine.org/viewtopic.php?f=23&t=602280&start=15](http://forums.mozillazine.org/viewtopic.php?f=23&t=602280&start=15)

Specifically, the post by **lenniboy**.

---

### Post by nanotube on 2010-01-25
> **Eromatic said:**
> Could it be related to the following?

[http://forums.mozillazine.org/viewtopic.php?f=23&t=602280&start=15](http://forums.mozillazine.org/viewtopic.php?f=23&t=602280&start=15)

Specifically, the post by **lenniboy**.

hrm, well, could be... 

i myself can't really test anything, since fonts look fine on ff3.6 for me on both my ubuntu systems...

---

### Post by ironjaw33 on 2010-01-28
The .fonts.conf suggestion in this thread works for Firefox 3.5, but on both my Ubuntu systems it has no effect on Firefox 3.6.  I'm running 9.10 32 bit with Ubuntuzilla on one system and 9.10 64 bit on the other, trying both the daily builds and downloading from the Mozilla website.

I also tried the suggestions in [this thread]("http://ubuntuforums.org/showthread.php?t=1389077"), but didn't have any luck.

---

### Post by chandru on 2010-01-28
This worked for me to fix firefox 3.6 font ugliness. Essentially we need to recompile firefox and firefox gnome support with the right compiler options to make it use the system cairo.

Steps are as follows.
1. Install the ubuntu-mozilla-daily ppa source repository. Add to your sources.list
```
deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main
```

2. Update the package lists
```
sudo aptitude update
```

3. Install packages to build firefox
```
sudo apt-get build-dep firefox
```

For some reason this does not install xulrunner development packages, so we have to do it manually
```
sudo aptitude install xulrunner-1.9.2-dev
```

4. Get the source packages for firefox. In a directory of your choice to
```
apt-get source firefox
```

The source will be downloaded to a folder which starts with firefox. Change to that directory

```
cd firefox-...
```

5. Now we need to make some changes to the debian rules file. Open the file with a favourite text editor.

```
gedit debian/rules
```

Around line 29, you should see a line like this
```
DEB_MIN_SYSDEPS		?= 1
```
Change this to
```
DEB_MIN_SYSDEPS		?= 0
```

Now use your search function to search for ubuntu-abrowser.js in the same file. This should lead to you to lines 369 and 371. Change them to look like this
```
binary-install/$(DEBIAN_NAME_OTHER)-branding:: debian/$(DEBIAN_NAME_OTHER)-branding/$(DEBIAN_FF3_DIR)/defaults/preferences/ubuntu-abrowser.js

debian/$(DEBIAN_NAME_OTHER)-branding/$(DEBIAN_FF3_DIR)/defaults/preferences/ubuntu-abrowser.js: debian/ubuntu-abrowser.js.tmpl
```

Essentially, you change pref to preferences.

Save the file and close the editor.

6. Optionally, edit the changelog file. We want to change the version number, so that we don't have to do all this every time the version changes (which is about once a day with the ppa repository).

Change the first line to look like this.
```
firefox (3.6.3) karmic; urgency=low
```

This artificially upgrades the version number, so any update with a version number smaller than this does not undo your hard work.

Save the file and exit.

7. Now compile the package
```
dpkg-buildpackage -rfakeroot -b -uc
```

If you have multiple cores, you can add -j4 as an option. Replace 4 with the number of cores you have. This outputs a lot of deb files in the parent folder of the firefox-... folder.

If there are any error messages, you might need to install additional packages.

8. Install the necessary packages.
```
 cd ..
sudo dpkg -i firefox_3.6.3_amd64.deb firefox-gnome-support_3.6.3_amd64.deb firefox-branding_3.6.3_amd64.deb
```

Replace amd64 with i386 if you have a 32 bit machine. Skip the firefox-branding package if you want the generic abrowser branding.

I had to install only these 3 packages to improve the fonts. YMMV.

In some ways this is an ugly hack, but it makes things better while the devs fix the packages properly.

Regards

---

### Post by jaci87 on 2010-01-28
As alternative, you can add this repository: [https://launchpad.net/~portis25/+archive/test](https://launchpad.net/~portis25/+archive/test)
and let firefox be updated.

---

### Post by chandru on 2010-01-28
That repository is lucid only. So either change the appropriate file in /etc/apt/sources.list.d to lucid or manually download and install the packages.

---

### Post by jaci87 on 2010-01-28
> **chandru said:**
> That repository is lucid only. So either change the appropriate file in /etc/apt/sources.list.d to lucid or manually download and install the packages.
Yeah, sorry.

---

### Post by ironjaw33 on 2010-01-28
Thanks, compiling from source did indeed fix the font problems.

---

### Post by jaci87 on 2010-01-29
However, repo is open for Karmic now. ;)

---

### Post by dcstar on 2010-03-24
> **jaci87 said:**
> As alternative, you can add this repository: [https://launchpad.net/~portis25/+archive/test](https://launchpad.net/~portis25/+archive/test)
and let firefox be updated.

That certainly helps Firefox in my 10.04 Beta system.

---

### Post by Jigen on 2010-04-05
I have installed ff 3.6.3 via ubuntuzilla's repos today and .files.conf workaround described in post #3 worked fine, even though I had to set hinting as "hintslight" and fonts still look a little sharper than my preferred gnome settings (however hintnone would give a worse result)

---

### Post by asaturn on 2010-04-09
> **Jigen said:**
> I have installed ff 3.6.3 via ubuntuzilla's repos today and .files.conf workaround described in post #3 worked fine, even though I had to set hinting as "hintslight" and fonts still look a little sharper than my preferred gnome settings (however hintnone would give a worse result)

+1

this helped me as well... fonts looked HORRIBLY and windows-xp-like ... now they look nice. here is my .fonts.conf file:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

note this isn't REALLY a fix... the font rendering engine in firefox is still not set to be the same as the system's -- it's technically a bug that keeps getting broken.

---

### Post by bburg on 2010-04-27
> **dcstar said:**
> That certainly helps Firefox in my 10.04 Beta system.
[Post 12]("http://ubuntuforums.org/showpost.php?p=7634222&postcount=12") helped me on FF 3.6.3.

---

### Post by hansheijmans on 2010-09-18
I had the same problem with Firefox 3.6.10 after I installed and de-installed KDE. I already had a .fonts.conf file in my home directory. I renamed the file and logged out and logged in again.

My problem was solved!

---

### Post by neu5eeCh on 2010-10-03
I must not be having the same problem, though it sounds very similar. None of the above workarounds have worked.

When I use the Ubuntu Font, the menu doesn't render correctly in Mozilla Software (Firefox or Thunderbird). The Font looks "spindly", as if it needed to be bolded. The font renders correctly in the Gnome panel and other software.

---

### Post by begtognen on 2010-11-12
> **hansheijmans said:**
> I already had a .fonts.conf file in my home directory. I renamed the file and logged out and logged in again.

Thank you, [Hansheijmans]("http://ubuntuforums.org/member.php?u=832618")! This worked beautifully for me.

---

### Post by xtnsgo on 2010-12-21
> **VTPoet said:**
> I must not be having the same problem, though it sounds very similar. None of the above workarounds have worked.

When I use the Ubuntu Font, the menu doesn't render correctly in Mozilla Software (Firefox or Thunderbird). The Font looks "spindly", as if it needed to be bolded. The font renders correctly in the Gnome panel and other software.

I've had real success faking font smoothing with a slight text shadow (also, this method is pretty font-agnostic).  

I added the following to userChrome.css and userContent.css:```
*{
text-shadow: 0px 0px 1px #ababab !important;
}
```Very quick and the improvement is quite dramatic.  This was inspired by the Opera OSX Font Rendering extension ([https://addons.opera.com/addons/extensions/details/mac-osx-font-rendering/1.5/?display=en](https://addons.opera.com/addons/extensions/details/mac-osx-font-rendering/1.5/?display=en)), thanks to the author who really deserves all the credit.  Here is the original javascript:
```
(function() {
var css = "body {\n text-shadow: 0px 0px 1px #909090 !important;\n}";
if (typeof GM_addStyle != "undefined") {
    GM_addStyle(css);
} else if (typeof PRO_addStyle != "undefined") {
    PRO_addStyle(css);
} else if (typeof addStyle != "undefined") {
    addStyle(css);
} else {
    var heads = document.getElementsByTagName("head");
    if (heads.length > 0) {
        var node = document.createElement("style");
        node.type = "text/css";
        node.appendChild(document.createTextNode(css));
        heads[0].appendChild(node); 
    }
}
})();
```I changed the shadow value to a slightly lighter one (the original was way too fuzzy) that gives a tighter (while still smooth) look and also seems to look a bit better against dark backgrounds.

The above javascript could just plug into Greasemonkey, but since there's no Greasmonkey for Firefox 4 and Thunderbird, and since i'd have to add the first snippet to userChrome.css anyway to fix the UI, I just went the userChrome/userContent.css route all the way 'round. It was also just easier that way:)

Anyway, this issue frustrated me for quite a while until I figured this out.  I hope this workaround is something that saves someone else the same frustration.

---

