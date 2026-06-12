---
title: "How to Install Japanese Input in Ubuntu 10.10 using iBus"
date: 2010-10-13
forum: Tutorials
---

### Post by ryukent on 2010-10-13
How to Install Japanese Input in Ubuntu 10.10 (Maverick) using iBus

This method uses iBus which is the default and easiest input method to install. It does not require complicated setup or terminal commands.

First, make sure language support is correctly installed. From the desktop, click on System / Administration / Language Support.

If it tells you that the language support is not installed completely, click install.

Click on 'Install / Remove Languages'. Select Japanese and then tick 'Input Methods' and 'Extra Fonts'. Click on close.

Change 'Keyboard input method system to ibus'. Click on close.

The correct files should now have been installed automatically. All you need to do now is configure the the input method. First, log out and then log back in again.

To enable the Japanese input system you have just installed, select 'System / Preferences / Keyboard Input Methods'. Drop down, Japanese, Anthy, Add.

There should be a keyboard icon in the top right of your screen. You can click on it to change to Anthy (Japanese input) or use Ctrl+Space. Open a text editing program, change to Anthy and you can now type in &#26085;&#26412;&#35486;&#12290;

If you want extra options, click on the keyboard (ibus) icon on the top right and select preferences. Then change the 'show language panel' to 'When active'. This will pop up a further language bar that you can use to tweak Anthy.

---

### Post by hirakata on 2010-10-16
Clicking on Keyboard Input Methods in the System Preferences does nothing. It says "Starting..." on the taskbar but then disappears. What am I doing wrong?

---

### Post by crt555 on 2010-10-20
This is perfect. It fixed the weird (and sometimes outright wrong) Japanese fonts I was getting with some websites too. Thanks!

---

### Post by marcthenarc on 2010-10-30
It works great.  Now I can really input &#26085;&#26412;&#35486; in any application.

w00t!

---

### Post by mnoyes on 2010-11-04
Great instructions -- simple, clear, and right. &#12473;&#12466;&#12540;&#65281;&#65281;

---

### Post by dsanjo on 2010-11-11
Great instructions.
Japanese input was a problem I had with Ubuntu years ago. 
I'm happy to see Japanese input can be easily enabled properly now.
Thanks.

---

### Post by ForgotMyOrange on 2010-12-05
This is great thank you.
This is much easier in Windows, to be honest.

I set my key combination to Alt-Shift (the dialog was very difficult to understand)
Now when I press this key combination in a text editor, the input changes to Japanese, but pressing it again does nothing.
But I check the menu in the system tray along the top and it's actually set to "Input method Off"

I have to change the input method back to Japanese and then back to OFF again, then it works.

It took me a while to realise that the way I have it setup, I need to hit my combination **Alt-Shift **to turn Japanese on, then **Ctrl-Space** to turn it off.

This is because Alt-Shift is cycling through keyboard inputs and unlike Windows (which cycles between US/Japanese), Ubuntu is not cycling between Japanese and US, it only considers Japanese an input scheme - and cycling to the next input is useless because there is no US input system to cycle to.

So Alt-Shift, Ctrl-Space... wax on, wax off... it is.

---

### Post by Ferrat on 2011-03-09
Works great and you don't need to log out and back in, if you just try and start the language switching you'll get a pop-up that says the daemon isn't running and give you the option to start it :)&#12288;

---

### Post by BackBONE7 on 2011-03-26
Hi,

i have japanese language support running for some time now, entering everything with roman letters.
However there is a option to use a japanese keyboard to enter hiragana/katakana directly.
So i bougt myself japanese keyboardstickers, wich works great, eccept i can`t write the carracter RO.
The Key for RO was acctualy used as&#12288;Zenkaku/Hankaku key.
Is there a way to rout this key to another one?

Thank you


....EDIT....
@ForgotMyOrange: CTRL+SPACE works in both ways for me, on and off.

...EDIT2....
Changing the Layout with Xkeycaps is easy (i just found out) everything works now.

---

### Post by beetlejuice321 on 2011-03-31
Hey thanks for the post! I have been trying to figure out how to enable Japanese in Ubuntu 10.10 on my own. Was just missing the step on 

"System / Preferences / Keyboard Input Methods'. Drop down, Japanese, Anthy, Add."

I do like how now they FINALLY have the input method with the icon at the top of the toolbar in Gnome instead of floating around on the page. Thats a very welcome change!

&#26377;&#38627;&#12358;&#65281;

---

### Post by rhapa on 2011-09-13
Thank you very much.
Input japanese on Ubuntu was one of the reasons I didn't use Ubuntu often. Now that I'm capable I'm pretty much using it and I actually prefer using it than I do with OS X (although kotoeri is pretty easy and works like a charm). For some unknown reason Ubuntu runs faster than OS X on my MacbookPro.

---

### Post by naradluffy on 2011-10-15
it's work!!
&#12354;&#12426;&#12364;&#12392;&#12358;&#65281;&#65281;&#65281; 

But, how can I see the other letter? katakana? kanji? in windows, I can do with press F9 and then press narrow down or right click on the sentences.

---

### Post by naradluffy on 2011-10-15
> **naradluffy said:**
> it's work!!
&#12354;&#12426;&#12364;&#12392;&#12358;&#65281;&#65281;&#65281; 

But, how can I see the other letter? katakana? kanji? in windows, I can do with press F9 and then press narrow down or right click on the sentences.

Ah, forget it.
press space.
sorry :D

---

### Post by down_quark on 2011-10-21
> **ryukent said:**
> Click on 'Install / Remove Languages'. Select Japanese and then tick 'Input Methods' and 'Extra Fonts'. Click on close.

I updated to 11.10 recently and the Input Methods/Extra Fonts option is gone and the current default hiragana font is really ugly.
Are these fonts available as a separate package?

---

### Post by TokyoYank on 2011-11-11
For those using 11.10 finding their way to this thread, try the following
[LIST]
[*]System Settings > Language Support
[*](Be aware:  your options for langauges depends on your "Software Sources" mirror server selection.  I chose "United States" to find options besides English) Japanese > add
[*]Input Method > ibus
[*]Log out and immediately log in (Look for the gear-like icon in the upper right corner)
[*](notice the keyboard icon in the upper right corner) that is ibus.
[*]Note:  you might have to Settings > Language Support > Japanese > Add twice.  (I did, and I don't know why.)
[*]hover over the keyboard icon > Preferences > Input Method > Select and Input Method > Japanese > Anthy > Add
[/LIST]
For me it worked immediately; Alt + L_Shift switches between Japanese and English input, as expected.
> **down_quark said:**
> I updated to 11.10 recently and the Input Methods/Extra Fonts option is gone and the current default hiragana font is really ugly.
Are these fonts available as a separate package?

Fonts:  I don't know, but there is a way to switch to the older gnome interface, from dash home search "terminal" and type ```
sudo apt-get install gnome-session-fallback
```Call me old fashioned, but I am looking forward to having useful community "how to" and instructions work again.

---

### Post by fire-fly on 2012-03-11
> **TokyoYank said:**
> For those using 11.10 finding their way to this thread, try the following
[LIST]
[*]System Settings > Language Support
[*](Be aware:  your options for langauges depends on your "Software Sources" mirror server selection.  I chose "United States" to find options besides English) Japanese > add
[*]Input Method > ibus
[*]Log out and immediately log in (Look for the gear-like icon in the upper right corner)
[*](notice the keyboard icon in the upper right corner) that is ibus.
[*]Note:  you might have to Settings > Language Support > Japanese > Add twice.  (I did, and I don't know why.)
[*]hover over the keyboard icon > Preferences > Input Method > Select and Input Method > Japanese > Anthy > Add
[/LIST]
For me it worked immediately; Alt + L_Shift switches between Japanese and English input, as expected.


Fonts:  I don't know, but there is a way to switch to the older gnome interface, from dash home search "terminal" and type ```
sudo apt-get install gnome-session-fallback
```Call me old fashioned, but I am looking forward to having useful community "how to" and instructions work again.

Thanks! working for me

---

### Post by maryannehanna on 2012-05-08
Thank you very much for the information. I got the ime-anthy working on my computer, but I have a little problem. When I get a list of possible characters to choose from, it only shows boxes. If I move the position it shows the character in the original line where I typed the texts. How do I get the list to show actual characters to choose from? Thanks.

---

