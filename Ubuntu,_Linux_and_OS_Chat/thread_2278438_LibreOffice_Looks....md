---
title: "LibreOffice Looks..."
date: 2015-05-16
forum: Ubuntu, Linux and OS Chat
---

### Post by arsenic-creed on 2015-05-16
dated? When did Libreoffice update to look straight out of the early 2000's and is there a way to switch it back to the previous look that rather matched the Ubuntu theme (not sure if that's the word I want, I mean what the menus tend to look like and so on). I've not posted this in support because it's not really a problem, just an offence to my preferred aesthetics. I've included a screenshot for reference to what I mean. (If there isn't a way to change it back, is there a way to make the toolbars bigger, my crappy eyes can't read that.)

---

### Post by Bucky Ball on 2015-05-16
> **arsenic-creed said:**
> dated? When did Libreoffice update to look straight out of the early 2000's ... 

Welcome. Haha. Yea, I'm completely with you, agreed, know exactly what you mean. I use it a LOT and it is disturbing. I particularly don't like the archaic 'Save as', 'Save' or 'Open' GUI pop-up.

> **arsenic-creed said:**
> I've not posted this in support because it's not really a problem, just an offence to my preferred aesthetics. I've included a screenshot for reference to what I mean.

a) Good plan, b) offence to mine too, c) attach the screenshot by going 'Go Advanced' or 'Adv Reply' and using the paperclip icon in the toolbar rather than inserting the pic in the body of the post. Thanks. ;)

I have never actually looked into changing the theme so interested now to know if you can. Sure a quick search for 'change libreoffice theme' will get the ball rolling ... :-k

---

### Post by monkeybrain20122 on 2015-05-16
Well I am not going to stare at an Office Software and marvel at how sexy it looks. Office Software is not sexy, and it is not supposed to be sexy. That's why office drones have sexy calenders :)

---

### Post by arsenic-creed on 2015-05-16
I know how to attach screenshots and just completely forgot to do so! Didn't have enough coffee or something this morning, I guess. ;) (Thank you for the very succinct explanation though.) 
There is actually an option for 'appearance' under the options menu but the default theme is this horrible grey thing and there doesn't seem to be any hints on how to change it.

---

### Post by monkeybrain20122 on 2015-05-16
You have to install the theme packages separately.

---

### Post by arsenic-creed on 2015-05-16
Oh, okay, how do I do that?

---

### Post by monkeybrain20122 on 2015-05-16
You can find some in Synaptic/Software Centre. There may be others in LO's site

Edited: Better check synaptic and search LibreOffice. I think the Software Centre hides some packages assuming that users are stupid and may get confused. If you have not installed synaptic, install it from the Software Centre of in the terminal:
sudo apt-get install synaptic

---

### Post by Bucky Ball on 2015-05-16
I just installed a few theme packages via Synaptics. They only change the icons. Going Tools> Options> Appearance looks to be the path of least resistance. I remember doctoring Openoffice this way years ago now we're talking about it.

(PS: You can also go Tools> Options> Personalisation and select a Firefox theme to use in Libreoffice. I tried this method, but nothing changed for me, didn't seem to work ... :|)

---

### Post by vasa1 on 2015-05-16
> **monkeybrain20122 said:**
> Well I am not going to stare at an Office Software and marvel at how sexy it looks. Office Software is not sexy, and it is not supposed to be sexy. That's why office drones have sexy calenders :)

+1.

Which version of LibreOffice is the one which looks "dated"? I have version 4.3.7.2 and don't find it too different from the previous versions (over the years).

This is what my Calc looks like:

---

### Post by neu5eeCh on 2015-05-16
I actually don't mind "the look". It's functional. I've used MS Office's ribbon interface a couple times (also on WPS office) and didn't cotton to it. Didn't see the point, really; but then I only word process and do minimal formatting. Speaking of which, I've really come to love how Libre Office handles styles -- much, much better than MS Office. 

But, what I would really like is a way to remove the menu with a Firefox style "hamburger". I'd also like a transparent background (for that no-distraction look).

---

### Post by ajgreeny on 2015-05-16
> **arsenic-creed said:**
> dated? When did Libreoffice update to look straight out of the early 2000's and is there a way to switch it back to the previous look that rather matched the Ubuntu theme (not sure if that's the word I want, I mean what the menus tend to look like and so on). I've not posted this in support because it's not really a problem, just an offence to my preferred aesthetics. I've included a screenshot for reference to what I mean. (If there isn't a way to change it back, is there a way to make the toolbars bigger, my crappy eyes can't read that.)
I am not sure I know exactly what you mean, and to be honest I don't really care too much.
LO is just a work application for me and it "does exactly what it says on the tin" as far as I'm concerned.

As for toolbars, yes you can make them, and the icons, larger in Tools->Options->Libreoffice->View, but I can find no Themes which could be added to LO as an extension to make it look any different.

PS: I am using LO v.4.4.3.2 from the ppa, but it doesn't look any different from the way I remember it looking since it updated to v.4 from v.3, which is when I think the green splash screen first appeared, though I may be incorrect about that.

---

### Post by deadflowr on 2015-05-16
> **ajgreeny said:**
> I am not sure I know exactly what you mean, and to be honest I don't really care too much.
LO is just a work application for me and it "does exactly what it says on the tin" as far as I'm concerned.

As for toolbars, yes you can make them, and the icons, larger in Tools->Options->Libreoffice->View, but I can find no Themes which could be added to LO as an extension to make it look any different.

PS: I am using LO v.4.4.3.2 from the ppa, but it doesn't look any different from the way I remember it looking since it updated to v.4 from v.3, which is when I think the green splash screen first appeared, though I may be incorrect about that.

I use firefox themes, for absolutely no reason.
Simple and easy to install.
Follow the path to the View option but go down to Personalizations and select "use own theme"
to get firefox themes simply run a search from the searchbox.

There should also be a set of default libreoffice themes you can choose from as well.
They're basics like starfields or something like that.

There was an older way to do this, but I do not think any versions of Ubuntu use that method, and the only version that does not have this theming option is probably 3.5(precise)

---

### Post by PhilGil on 2015-05-16
[**[COLOR=#000000]arsenic-creed[/COLOR]**]("http://ubuntuforums.org/member.php?u=1910186"), based on your screenshot you appear to be missing the GTK integration package. Install the libreoffice-gtk package from your package manager or from the command line:

```
sudo apt-get install libreoffice-gtk
```

After that you can install any Libreoffice theme you choose or customize the look by hand.

---

### Post by vasa1 on 2015-05-17
> **VTPoet said:**
> ... I'd also like a transparent background (for that no-distraction look).
Well, I use Compton for transparency in ~/.config/compton.conf:

```
opacity-rule = [ 
				"50:name *= '- Google Chrome'",
				"80:name *= '- LibreOffice Calc'",
				"80:name *= '- LibreOffice Writer'",
				"50:name *= 'pdf'"
				];
```

---

