---
title: "Can I add a wine program to the right click open with"
date: 2010-04-23
forum: Wine
---

### Post by everytimeref on 2010-04-23
Can I add a wine program to the right click open with menu?

if so how!

---

### Post by cogadh on 2010-04-23
If Wine is installed properly it should already be associated with Windows executables, so you shouldn't need that functionality, you can just double-click them; though IIRC, it also does add the right click entry when installed properly (not on a Linux machine ATM, can't check). What are you trying to do that requires it?

---

### Post by everytimeref on 2010-04-23
I simply want the option to add photoshop to the list that says open with> fspot, gimp etc when I righ click on a Jpeg in Nautilus

---

### Post by oldrocker99 on 2010-04-23
> **everytimeref said:**
> I simply want the option to add photoshop to the list that says open with> fspot, gimp etc when I righ click on a Jpeg in Nautilus

Interesting...I have yet to get Photoshop to run under Wine...

:guitar:

---

### Post by cogadh on 2010-04-23
> **everytimeref said:**
> I simply want the option to add photoshop to the list that says open with> fspot, gimp etc when I righ click on a Jpeg in Nautilus
Okay, that's a wee bit different than having Open with > Wine available. I'm thinking the easiest way to do it would be to create a script that launches PS and add that to the right-click options. Unfortunately, I currently don't have access to my Linux machine (long story), so I can't experiment with it myself, but I'm sure one of the geniuses around here can come up with something.

---

### Post by everytimeref on 2010-04-24
> **cogadh said:**
> Okay, that's a wee bit different than having Open with > Wine available. I'm thinking the easiest way to do it would be to create a script that launches PS and add that to the right-click options. Unfortunately, I currently don't have access to my Linux machine (long story), so I can't experiment with it myself, but I'm sure one of the geniuses around here can come up with something.


Thanks for helping anyway!

It's a bit confusing, you can create a shortcut to wine but creating a shortcut to open a file in a wine app is hard: The Linux address of the file is not the address that the window app can use, so you can right click on a file and say open with Wine/photoshop which may open photoshop, but the rest of the file address is not a windows address and photoshop doesn't know what to do.

---

### Post by everytimeref on 2010-04-24
> **oldrocker99 said:**
> Interesting...I have yet to get Photoshop to run under Wine...

:guitar:

Photshop up to about CS2 (I haven't looked beyond that, but there were problems.)  works fine in Wine. You need to  have microsoft fonts installed (it's been a while, I can't remember specific details).

reset palette location becomes your best friend because of the way linux displays windows, but it works really well.

---

### Post by everytimeref on 2010-04-28
does anybody have any ideas at all about this?

---

### Post by mc4man on 2010-04-29
Pretty simple - will give ex. with photoshop 7 so adjust as needed 

Just r. click on any 1 file type that you want to open in ps, this only needs to  done once.

choose open with -> open with other application -> use a custom command

For command use this - **adjust to reflect your install** 

```
wine "C:\Program Files\Adobe\Photoshop 7.0\Photoshop.exe" Z:%f 
```

Then click open - will now be available in r. click as "wine"

To change name of r.click option from wine

 open home folder (show hidden files) -> .local/share/applications and you should see a file userapp-wine-XXXXXX.desktop or a blue diamond named wine 
(this will depend on what version of ubuntu you are using

You need to open in a text editor, easiest way is just open a terminal, type gedit, hit space bar, drag the .desktop onto terminal, click in terminal to restore focus and press enter

When the .desktop opens you'll see something like this 
> [Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=wine "C:\\Program Files\\Adobe\\Photoshop 7.0\\Photoshop.exe" Z:%f [COLOR="Blue"]%f[/COLOR]
Name=[COLOR="Red"]wine[/COLOR]
Comment=Custom definition for wine
NoDisplay=true



You could remove the %f marked in blue - really doesn't matter (don't leave out of command above

Change the red to anything you wish to see in r. click menu, if desired an icon line and or MimeType line(s) can be added - not really necessary

Note:
*(you could also just create the .desktop from scratch on desktop or home and then mv to ~/.local/share/applications*, instead of the whole deal above

For other filetypes you'll now see "<whatever you named it>" available as a choice or available in the r.click properties to be set as the l. click default

---

### Post by everytimeref on 2010-04-30
This is brilliant, will give it ago tonight and report back!

---

### Post by YokoZar on 2010-04-30
This is something I've been wanting to make easier for a long time now, but it sort of got stalled.

---

### Post by mc4man on 2010-04-30
As a bit of a side 'issue'

I did this on lucid w/ wine 1.2 and after ps was installed a ton of wine-extension XXX.desktops showed up in ~/.local/share/applications

The downside is all of them will show up in your r.click menu, all named photoshop. ( we're not talking a few here

Atm I don't have the time to see if they're useful or not, nor to edit the .desktops to give each one a distinctive name
( a nautilus-action -> open in text editor is quite useful for editing .desktops

If this happens - one needs to remove them from ~/.local/share/applications  to get them out of the context menu.
 
I wouldn't outright delete them in the outside possibility some may prove useful, as I remember wine may not re-create them easily.

Possibly better to move to a storage directory (unless they're of no value

Not all of these are ps related, but did move them all for the moment

```
doug@doug-laptop:~/Desktop/store$ ls *.desktop
wine-extension-8ba.desktop  wine-extension-atf.desktop
wine-extension-8bc.desktop  wine-extension-atn.desktop
wine-extension-8be.desktop  wine-extension-ava.desktop
wine-extension-8bf.desktop  wine-extension-awf.desktop
wine-extension-8bi.desktop  wine-extension-axt.desktop
wine-extension-8bp.desktop  wine-extension-cha.desktop
wine-extension-8bs.desktop  wine-extension-chm.desktop
wine-extension-8bx.desktop  wine-extension-csf.desktop
wine-extension-8by.desktop  wine-extension-csh.desktop
wine-extension-8li.desktop  wine-extension-ffo.desktop
wine-extension-abr.desktop  wine-extension-grd.desktop
wine-extension-acf.desktop  wine-extension-hlp.desktop
wine-extension-aco.desktop  wine-extension-htm.desktop
wine-extension-act.desktop  wine-extension-html.desktop
wine-extension-acv.desktop  wine-extension-ini.desktop
wine-extension-ado.desktop  wine-extension-pat.desktop
wine-extension-ahs.desktop  wine-extension-pcast.desktop
wine-extension-ahu.desktop  wine-extension-psd.desktop
wine-extension-alv.desktop  wine-extension-psf.desktop
wine-extension-amp.desktop  wine-extension-psp.desktop
wine-extension-ams.desktop  wine-extension-rtf.desktop
wine-extension-api.desktop  wine-extension-shc.desktop
wine-extension-apl.desktop  wine-extension-txt.desktop
wine-extension-asl.desktop  wine-extension-wri.desktop
wine-extension-ast.desktop  wine-extension-xml.desktop
wine-extension-asv.desktop
```

---

### Post by everytimeref on 2010-05-01
> **mc4man said:**
> Pretty simple - will give ex. with photoshop 7 so adjust as needed 

Just r. click on any 1 file type that you want to open in ps, this only needs to  done once.

choose open with -> open with other application -> use a custom command

For command use this - **adjust to reflect your install** 

```
wine "C:\Program Files\Adobe\Photoshop 7.0\Photoshop.exe" Z:%f 
```

Then click open - will now be available in r. click as "wine"

To change name of r.click option from wine

 open home folder (show hidden files) -> .local/share/applications and you should see a file userapp-wine-XXXXXX.desktop or a blue diamond named wine 
(this will depend on what version of ubuntu you are using

You need to open in a text editor, easiest way is just open a terminal, type gedit, hit space bar, drag the .desktop onto terminal, click in terminal to restore focus and press enter

When the .desktop opens you'll see something like this 


You could remove the %f marked in blue - really doesn't matter (don't leave out of command above

Change the red to anything you wish to see in r. click menu, if desired an icon line and or MimeType line(s) can be added - not really necessary

Note:
*(you could also just create the .desktop from scratch on desktop or home and then mv to ~/.local/share/applications*, instead of the whole deal above

For other filetypes you'll now see "<whatever you named it>" available as a choice or available in the r.click properties to be set as the l. click default


After a bit of fiddling (mainly down to me not reading properly) this has worked brilliantly. Thank-you very much- I'll probably have to do it all again when I upgrade to Lucid!

---

### Post by everytimeref on 2010-05-01
> **YokoZar said:**
> This is something I've been wanting to make easier for a long time now, but it sort of got stalled.

It would be nice if wine programs could be added to the list of installed programs automatically, it would help to blend wine apps into Ubuntu better.

---

### Post by mc4man on 2010-05-01
> have to do it all again when I upgrade to Lucid! 
I basically gave you the slightly longer way because there's some value in knowing about user-app.desktops and how to give a distinctive name

In this case - ps - as things stand now the custom command required having Z:%f at the end, otherwise ps would open but the file wouldn't be loaded

Here's the simple way (use copy and paste

```

 gedit photoshop.desktop
```

then c&p this into gedit, save and close (again adjust the Exec= to reflect your ps install
```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=wine "C:\\Program Files\\Adobe\\Photoshop 7.0\\Photoshop.exe" Z:%f 
Name=Photoshop
Comment=Custom definition for wine
NoDisplay=true
```
```

mv ~/photoshop.desktop ~/.local/share/applications
```

Then you should see Photoshop as an option in the context menu (initally r. click -> open with -> other application


note: if you see your context menu cluttered with Adobe Photoshop entries refer back to previous post

Edit 
same idea but for a desktop launcher to drop files on to - I give it a slightly different display  name
```

gedit ~/Desktop/Photoshop.desktop
```

C&p this in, edit icon location to your's, (and the Exec=  path if different

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=wine "C:\\Program Files\\Adobe\\Photoshop 7.0\\Photoshop.exe" Z:%f 
Name=Open in Photoshop
Comment=Custom definition for wine
NoDisplay=true
Icon=[COLOR="Blue"]/home/doug/.local/share/icons/cc22_photoshop.0.png[/COLOR]
```

```
chmod u+x ~/Desktop/Photoshop.desktop
```
Then just drop a file onto launcher (launcher can be dragged to panel if desired

---

### Post by frogotronic on 2010-05-26
> **cogadh said:**
> Okay, that's a wee bit different than having Open with > Wine available. ...

I **don't** have "Open with > Wine" available.  How can I add that functionality to nautilus?

- CH

---

