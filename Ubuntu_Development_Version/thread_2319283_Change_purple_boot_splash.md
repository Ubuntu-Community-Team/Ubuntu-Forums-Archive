---
title: "Change purple boot splash"
date: 2016-04-02
forum: Ubuntu Development Version
---

### Post by izznogooood on 2016-04-02
Is there any way to change from purple to black splash all the way to login?

I have Nvidia with the proprietary drivers and purple with huge black borders does not look pretty. Even though its only for 10 seconds ....

(Btw I've tried removing the "splash" form "quiet splash in /etc/default/grub but that gives me some text and errors on bootup & shutdown looks strange (valid errors none the less i dont want to see them :) ))

---

### Post by QDR06VV9 on 2016-04-02
See this post with the Green Checkmark
[URL="http://askubuntu.com/questions/362722/how-to-fix-plymouth-splash-screen-in-all-ubuntu-releases"]http://askubuntu.com/questions/362722/how-to-fix-plymouth-splash-screen-in-all-ubuntu-releases




[/URL]

---

### Post by izznogooood on 2016-04-02
All that did was slow my boot considerably. (I reverted...)

And from what research I have done it does not seem possible to change the resolution, so what i want is a black ubuntu boot, not purple.
(which is strange Ubuntu has not thought about considering the amount og people with Nvidia GFX cards....)

---

### Post by izznogooood on 2016-04-03
Im giving this a bump :)

---

### Post by justen_m on 2016-04-03
To /etc/default/grub, I added
GRUB_BACKGROUND="/usr/share/backgrounds/warty-final-ubuntu.png"
This replaced the default flat purple with the image I specified (which is purple/red/orange fade). I suppose you could replace this with a flat black image.

As for the quiet splash thing... I personally get rid of it, because I like seeing the messages during boot and shutdown. I watch for errors, and fix them if relevant. e.g. To me, it is sort of a progress indicator. In any case, it isn't there long, especially with SSD boot drives.

---

### Post by grahammechanical on 2016-04-03
You have to find the image that is being used by Plymouth and change it with your own image. This wiki page explains it but it does not apply to Xenial. I have just checked.

[https://wiki.ubuntu.com/Plymouth](https://wiki.ubuntu.com/Plymouth)

> Contents of /lib/plymouth/themes/default.plymouth: 

  [Plymouth Theme]
  Name=Ubuntu Logo
  Description=A theme that features a blank background with a logo.
  ModuleName=script

  [script]
  ImageDir=/lib/plymouth/themes/ubuntu-logo
  ScriptFile=/lib/plymouth/themes/ubuntu-logo/ubuntu-logo.scriptThis tells plymouthd to use the "script"  splash plugin. This plugin allows the graphical splash experience to be  scripted using Plymouths own scripting language (hence the name). 

The "script" splash plugin exists as /lib/plymouth/script.so (source code: src/plugins/splash/script/script.c) 


[LIST]
[*]"ImageDir" tells plymouthd which directory contains the images used by the "Ubuntu Logo" theme. 
[*]"ScriptFile" is the full path to the Plymouth script which creates the splash experience. 
[/LIST]


But on xenial /lib/plymouth/themes/ only has a folder called ubuntu-text which is empty. You need to find ubuntu-logo and replace it with your own version of ubuntu-logo. But as usual things change. Things are now in /usr/plymouth/themes/ubuntu-logo/

You may have to change the settings in ubuntu-log.script. 

Regards.

---

### Post by Cavsfan on 2016-04-03
My grub menu on a 28" monitor:

[[IMG]http://www.zimagez.com/miniature/20160229163727.jpg[/IMG]]("http://www.zimagez.com/zimage/20160229163727.php")

That's on Arch Linux. On Ubuntu you can have 3 colors: one for the top and bottom where the white font is in that picture, one for the box and the non-highlighted lines and one for the highlighted line.

This is an old one from 2014 in Ubuntu illustrating the 3 colors:

[[IMG]http://www.zimagez.com/miniature/20141222105039.jpg[/IMG]]("http://www.zimagez.com/zimage/20141222105039.php")

You can make the font bigger and have a custom menu or just change the background and the font colors, it's all up to you.

---

### Post by QDR06VV9 on 2016-04-03
> **izznogooood said:**
> All that did was slow my boot considerably. (I reverted...)

And from what research I have done it does not seem possible to change the resolution, so what i want is a black ubuntu boot, not purple.
(which is strange Ubuntu has not thought about considering the amount og people with Nvidia GFX cards....)
My Bad i misunderstood..

---

### Post by deadflowr on 2016-04-03
I think something like this is what the OP wants:
[http://askubuntu.com/questions/20829/how-can-i-change-the-purple-background-color-of-ubuntu-plymouth-boot-screen](http://askubuntu.com/questions/20829/how-can-i-change-the-purple-background-color-of-ubuntu-plymouth-boot-screen)

Note: I believe (or at least for me) that the location of the script is in **/usr/share/plymouth/themes/ubuntu-logo** now.
The part you want to edit is way down at line 169 or so.

---

### Post by izznogooood on 2016-04-03
> **deadflowr said:**
> I think something like this is what the OP wants:
[http://askubuntu.com/questions/20829/how-can-i-change-the-purple-background-color-of-ubuntu-plymouth-boot-screen](http://askubuntu.com/questions/20829/how-can-i-change-the-purple-background-color-of-ubuntu-plymouth-boot-screen)

Note: I believe (or at least for me) that the location of the script is in **/usr/share/plymouth/themes/ubuntu-logo** now.
The part you want to edit is way down at line 169 or so.


Thank you, the Ubuntu startup is now black. 

Grub on the other hand is still purple ass a "black" eye... :/

Edit: There was another file :)

    /usr/share/plymouth/themes/ubuntu-logo/ubuntu-logo.grub

Change the value to : 

if background_color 0,0,0 ; then
  clear
fi

Its all black. And thank you all for your contribution! :)

---

### Post by deadflowr on 2016-04-03
> **izznogooood said:**
> Thank you, the Ubuntu startup is now black. 

Grub on the other hand is still purple ass a "black" eye... :/

Grub's easy.
Just put a black.png picture/image in the /boot/grub folder and run [I]sudo update-grub

[/I]&#8203;

---

### Post by izznogooood on 2016-04-03
Oh, well i found another way, see last post page1 (edit).

---

### Post by izznogooood on 2016-04-11
I'm bringing this up again as i stil have a flash of purple as the log-in screen appears. Its like somewhere its overrulling my dconf.

[ATTACH=CONFIG]268310[/ATTACH]

Does anyone know where/why?

---

### Post by deadflowr on 2016-04-11
Do you mean it loads a purple screen, and then quickly switches to your screen?
Or do you mean something else?

---

### Post by MikeMecanic on 2016-04-11
> **izznogooood said:**
> I'm bringing this up again as i stil have a flash of purple as the log-in screen appears. Its like somewhere its overrulling my dconf.

[ATTACH=CONFIG]268310[/ATTACH]

Does anyone know where/why?

  	 	 	 	   You must also change purple to [#000000]("http://www.colorhexa.com/000000") in the same page before and after.

---

### Post by izznogooood on 2016-04-11
> **deadflowr said:**
> Do you mean it loads a purple screen, and then quickly switches to your screen?

Yes ;)

> **MikeMecanic said:**
> You must also change purple to [#000000]("http://www.colorhexa.com/000000") in the same page before and after.

Please clarify, i cant find any other options for color than the current page.

---

### Post by MikeMecanic on 2016-04-11
> **izznogooood said:**
> Yes ;)

Please clarify, i cant find any other options for color than the current page.

                        There is but I&#8217;m on Kylin.  These two lines show Purple before and after.
 
 
 In Kylin (its not purple):
 # Previous background colour
 # #300a24 --> 0.19, 0.04, 0.14
 # New background colour
 # #2c001e --> 0.16, 0.00, 0.12
 
 
 In Ubuntu:
 Ubuntu Purple: [2c001e]("https://www.colorcodehex.com/2c001e/")= 44,0,30 = 0.17, 0.00, 0.12
 I don&#8217;t have the other color.
 Ubuntu Purple: 2c001e = 44,0,30 = 0.17, 0.00, 0.12 in % = 44/255 and 30/255

---

### Post by deadflowr on 2016-04-11
I think it's the behavior of the system still loading so it uses whatever is set as the system defaults.
I think this is happening before it loads the setting set for whatever the last user are for whichever user was last set in the greeter screen.
(Does that make sense)

I do not think it is changeable within the users dconf controls.
rather you need to create an override for it.

To create an override
open a text editor 
put something like this in it:
```
[com.canonical.unity-greeter]
background-color='#000000'
```
then save it with a name like
99_unity-greeter.gschema.override

It needs to be placed in the directory: /usr/share/glib-2.0/schemas.
So whichever way you want to do that is up to you.
I always create systems docs in my own home and then sudo cp it over to where it needs to be, but you are free just open a text editor as root if you want.

After you copy it over to the schemas folder you need to run the compile command
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/ 
```

After that, when you logout and back in the screen should show a black screen for a second, instead of purple.


Does that help?

---

### Post by izznogooood on 2016-04-12
> **deadflowr said:**
> 

Does that help?

Yes it did, it made the splash at login black but the 1/2 sec show of the default purple wallpaper still showed...

You gave me an idea though, and the location of the files :)

I did: 

```
anders@lenox2:/usr/share/glib-2.0/schemas$ grep -rnw '.' -e "warty-final-ubuntu.png"
./10_ubuntu-settings.gschema.override:6:picture-uri='file:///usr/share/backgrounds/warty-final-ubuntu.png'
./com.canonical.unity-greeter.gschema.xml:5:      <default>'/usr/share/backgrounds/warty-final-ubuntu.png'</default>

```

I edited file 'com.canonical.unity-greeter.gschema.xml'

```
<?xml version="1.0" encoding="UTF-8"?>
<schemalist gettext-domain="unity-greeter">
  <schema id="com.canonical.unity-greeter" path="/com/canonical/unity-greeter/">
    <key name="background" type="s">
      <default>'/usr/share/backgrounds/warty-final-ubuntu.png'</default>
      <summary>Background file to use, either an image path or a color (e.g. #772953)</summary>
    </key>
    <key name="background-color" type="s">
      <default>'#2C001E'</default>
      <summary>Background color (e.g. #772953), set before wallpaper is seen</summary>
    </key>

```
and i changed it to 

```
<?xml version="1.0" encoding="UTF-8"?>
<schemalist gettext-domain="unity-greeter">
  <schema id="com.canonical.unity-greeter" path="/com/canonical/unity-greeter/">
    <key name="background" type="s">
      <default>'#000000'</default>
      <summary>Background file to use, either an image path or a color (e.g. #772953)</summary>
    </key>
    <key name="background-color" type="s">
      <default>'#000000'</default>
      <summary>Background color (e.g. #772953), set before wallpaper is seen</summary>
    </key>

```

I removed the override you gave me before making another update and voila, blackbuntu ;)

Thank you for pointing the way ;)

---

### Post by deadflowr on 2016-04-12
If you try adding the background you want to that file, does that kill off the purple people eater?
Where the file would currently read as:
```
[com.canonical.unity-greeter]
background-color='#000000'
```
add
```
background='path/to-picture-here'
```
so it looks like:
```
[com.canonical.unity-greeter]
background-color='#000000'
background='path/to-picture-here'
```


and of course re-run the glib-compile-schemas command again.

Does that make sense?

---

### Post by izznogooood on 2016-04-12
Oh, i was editing, se post #19

And yes, you make perfect sense ;)

---

### Post by cariboo on 2016-04-30
Seeing as we are now in the Yakkety development cycle, thread closed.

---

