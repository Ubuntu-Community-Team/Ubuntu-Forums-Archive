---
title: "problems with Kompozer"
date: 2014-06-11
forum: The Cafe
---

### Post by fabiani on 2014-06-11
Hello,


this is a question about Kompozer, previously known as nvu, I'm not sure if this is the best place to ask but I will try.



I  created a web page with Kompozer (in ubuntu). The page looked fine,  however for some reason all my modifications would not show when the  page was loaded with firefox. Then I closed Kompozer and opened the page  again, and this time my modifications would not show in Kompozer  either. I can see them in the "Source" tab, but not in the "Design" tab,  as if they were "commented out" or something.


Can anyone please explain what happened? I don't know much  about html, so I can't really understand what went wrong from the  "Source" tab.


A diff between the new html and the old one does not show anything that I can interpret...
```

$ diff -w Fabiano_Baroni.html  Fabiano_Baroni_old.html  | more


(I'm only showing the first few lines of output)


0a1
> <?xml version="1.0" encoding="UTF-8"?>
2,5d2
< <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"><head>
< 
< 
< 
7a5,6
> <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
>   <head>
12,120c11,22
<     <meta name="viewport" content="width=700" /><title>Fabiano Baroni</title>
<     
<      <link rel="stylesheet" type="text/css" media="screen,print"  href="Fabiano_Baroni_files/Fabiano_Baroni.css" /><!--[if lt IE  8]><link rel='stylesheet' type='text/css' media='screen,
print'   href='Fabiano_Baroni_files/Fabiano_BaroniIE.css'/><![endif]--><!--[if  gte IE 8]><link rel='stylesheet' type='text/css'  media='screen,print' href='Media/IE8.css'/><![endif]-->
<     
<     
<     <script type="text/javascript" src="Scripts/iWebSite.js" />
<     <script type="text/javascript" src="Scripts/Widgets/SharedResources/WidgetCommon.js" />
<     <script type="text/javascript" src="Scripts/Widgets/Navbar/navbar.js" />
<     <script type="text/javascript" src="Scripts/iWebImage.js" />
<      <script type="text/javascript"  src="Fabiano_Baroni_files/Fabiano_Baroni.js" /></head><body  style="margin: 0pt; background: rgb(235, 235, 235) none repeat scroll  0%; -moz-backgroun
d-clip: -moz-initial; -moz-background-origin:  -moz-initial; -moz-background-inline-policy: -moz-initial;"  onload="onPageLoad();" onunload="onPageUnload();">
< <div  id="id2" style="height: 842px; left: 388px; position: absolute; top:  460px; width: 642px; z-index: 1;" class="style_SkipStroke_2  shape-with-text">
<             <div class="text-content graphic_textbox_layout_style_default_External_642_125" style="padding: 0px;">
<               <div class="graphic_textbox_layout_style_default">
<                 



```

Thank you, best


Fabiani

---

### Post by kc1di on 2014-06-11
Kompozer has not been updated for years. and has been dropped from the repositories of most Distros these days.
I have switched to using Sea Monkey's Composer which works much the same and is more reliable now. 
you can install it by following the directions found [here.]("http://linuxg.net/how-to-install-seamonkey-2-25-on-ubuntu-14-0413-1012-1012-04-linux-mint-161413-and-elementary-os-0-2/")

---

### Post by mastablasta on 2014-06-11
another descent option is BlueFish (it might be in the repositories).

Sea monkey is also fine.

otherwise oyu can use some of the good text editors Geany, Kate, gedit, Atom, Sublime....

---

### Post by fabiani on 2014-06-12
Thanks for your feedback, I guess it's quite pointless to look for help with Kompozer at this stage then...

I  was looking for a WYSIWYG html composer so probably SeaMonkey Composer  is my best bet. Otherwise maybe BlueGriffon could also be a possibility.


Many thanks, cheers

---

### Post by mastablasta on 2014-06-12
Blue Griffon had some afair with bundling malware together with the program. i cant remember exactly what was it. i am not sure if this is still the case - for example: [https://groups.google.com/forum/#!topic/bluegriffon/BWykByWd1iE](https://groups.google.com/forum/#!topic/bluegriffon/BWykByWd1iE)

bluefish on the other hand is opensource: [http://bluefish.openoffice.nl/index.html](http://bluefish.openoffice.nl/index.html)

Seamonkey is also good.

---

### Post by rewyllys on 2014-06-12
I tried *Kompozer* a couple of years ago, and quickly gave up on it, for reasons that have already been stated in this thread.

For maintaining my Web files, I use *Bluefish* as my HTML editor, and *Filezilla* for uploading and downloading files.  Together, they work better and more easily, IMHO, than I recall as being my experience with *Dreamweaver* when I used to be a Windows user.

---

### Post by mastablasta on 2014-06-13
In Windows a good editor is Edit Plus (but you need to pay for it), luckily the opensource Notepad++ Will replace it well. well some of us dualboot and do editing HTML on both OS. unfortunatelly Notepad++ though opensource was not ported to Linux i believe.

---

### Post by oygle on 2014-10-29
Seamonkey install instructions are at [http://linuxg.net/how-to-install-seamonkey-2-25-on-ubuntu-14-0413-1012-1012-04-linux-mint-161413-and-elementary-os-0-2/](http://linuxg.net/how-to-install-seamonkey-2-25-on-ubuntu-14-0413-1012-1012-04-linux-mint-161413-and-elementary-os-0-2/)

---

### Post by Tom_Carr on 2014-10-30
Kompozer still works for the simple web sites I am maintaining.   I looked at all the other options listed here and Sea Monkey seems like the best bet.  When Sea Monkey becomes available in the repositories, or when Kompozer stops working for me, I will switch.

I don't understand why a simple WYSIWYG html editor is so hard to come by.  Is there something about creating one of these that is more complex than it seems?

---

