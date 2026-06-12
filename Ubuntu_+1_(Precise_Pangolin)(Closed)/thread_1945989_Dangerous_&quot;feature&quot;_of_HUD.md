---
title: "Dangerous &quot;feature&quot; of HUD"
date: 2012-03-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by quequotion on 2012-03-24
So i took the time to do most of the unity-checklist tests.

The tests froze and crashed my desktop no less than three times...

Aside from that I learned something new and terrible about HUD.

If you search for a menu item in HUD, sometimes you get multiple results.

Try searching for "Prefrences"

You may get a result that looks like the application's prefrences you want, ie: "Edit > Prefrences" makes sense for firefox if you know the menu.

You may also get a list of less clear results like three or four "> Preferences"

These "> Something" entries are from the appindicators on the top right.

HUD makes no attempt to tell you where each of these entries came from, so if you happen to be looking for your Sofware Updates prefrences, but you have other indicators installed, you'll never know which one's prefrences "> Prefrences" refers to without clicking on it.

This gets even more dangerous if you search for "Quit", which should return several entries including the application you want and others that look similar and say nothing about which application you are quitting.

---

### Post by keithpeter on 2012-03-24
Hello quequotion

Where is the unity-checklist you tried? I'd like to work through that.

You might want to take this to the unity design mailing list, there is a discussion about how HUD accesses the words it searches on there. The unity devs/designers read and respond to that list.

[https://launchpad.net/~unity-design](https://launchpad.net/~unity-design)

---

### Post by grahammechanical on 2012-03-24
Are we talking about the Unity Checkbox tests suites? There are PPAs here

[http://www.theorangenotebook.com/2012/01/testing-hud-heads-up-display.html]("http://www.theorangenotebook.com/2012/01/testing-hud-heads-up-display.html")

But how useful they are I do not know as this is testing from back in January.

It seems to me that the HUD needs two things. Applications that work with. Libreoffice does not. And it to be used so that it learns what you what when you type quit or preferences.

If HUD does not have any prior references to go by it will default to the app indicators because that is all it is aware of.

Regards.

This is what Synaptic tells me I have on my system

Checkbox 0.13.5 = System testing application. Installed by default.
Checkbox-app-testing 0.4.16 = Manual application tests. System apps that is.
Checkbox-unity 0.4.13 = Checkbox Unity.  Tests Unity
checkbox-gtk 0.13.5 GTK interface for Checkbox.

Oh, by the way. Checkbox-app-testing did not work on my 12.04 that I had daily upgraded from 11.10 but it did work on a default 12.04 Beta 1 which was what it was supposed to test.

---

### Post by zombifier25 on 2012-03-24
That's weird. For me the HUD will show the icon of the application whose menu entry is being selected.

---

### Post by keithpeter on 2012-03-24
> **grahammechanical said:**
> It seems to me that the HUD needs two things. Applications that work with. Libreoffice does not. 

Hello grahammechanical

Try installing lo-menubar. Then LibreOffice has global menu, and I reckon HUD will find the menu strings. Currently on PUIAS so can't check HUD picks up LO menues with lo-menubar installed.

I'll try that reference you gave.

Unity-design mailing list has an intresting thread about a programmer trying to design an app specifically for HUD

[https://lists.launchpad.net/unity-design/msg08762.html](https://lists.launchpad.net/unity-design/msg08762.html)

---

### Post by matt2053 on 2012-03-24
> **zombifier25 said:**
> That's weird. For me the HUD will show the icon of the application whose menu entry is being selected.

Only if you arrow down to select it. Thus, let's say you type "pref": I get these results:

```
[Firefox icon] Edit > Preferences
[No icon] > Preferences...
[No icon] Tools > Adblock Plus > Filter preferences...
[No icon] > Preferences....
```

Now, as I arrow up and down the list, yes, the icon changes to the icon of the list entry currently in focus. However, if I just type "pref" and use my mouse to click the second or fourth options in my list there, I have NO IDEA what I'm choosing.

If the icon updated on mouse-over, it wouldn't be such a problem.

---

### Post by jbicha on 2012-03-24
> **quequotion said:**
> 
You may also get a list of less clear results like three or four "> Preferences"

These "> Something" entries are from the appindicators on the top right.


This sounds to me like a bug against those extra indicators you're using for not following the Ubuntu standard. Ubuntu's power indicator has a button named "Power Settings..." If the indicators would do that, there wouldn't be a problem. Ubuntu's indicators (except bluetooth) followed that pattern for Ubuntu 11.10 too.

---

### Post by VinDSL on 2012-03-24
Truthfully...

I have disabled HUD.

I don't see any reason for it, at this juncture.

It works... sort of... and that's good enough to satisfy my curiosity.

I'll leave it to others, to sort out the details. ;)

---

### Post by matt2053 on 2012-03-25
> **jbicha said:**
> This sounds to me like a bug against those extra indicators you're using for not following the Ubuntu standard. Ubuntu's power indicator has a button named "Power Settings..." If the indicators would do that, there wouldn't be a problem. Ubuntu's indicators (except bluetooth) followed that pattern for Ubuntu 11.10 too.

That's not correct.

What he's saying is that in HUD as you start typing, auto-complete suggestions are populated. Only one icon at a time can be displayed, but it's the icon that has focus. There is no way to see the icon for the other suggestions. See my screenshot.

---

### Post by zombifier25 on 2012-03-25
Maybe they should include a tiny icon next to an entry :P
Just a suggestion.

---

### Post by jbicha on 2012-03-25
Matt, I still think that those apps are wrong. Here's two screenshots from my computer. I submitted a bug to fix the keyboard layout text. The universal access indicator (you only get this if you go to System Settings>Universal Access>Typing>Turn on accessibility features from the keyboard) is broken in so many ways that it should just be disabled for now; at least it's a bit hidden.

Even though Tomboy doesn't really follow the right style, it's still easy to tell that it's Tomboy Preferences. Therefore, it's a bug in the other apps you're using to not use the indicator API correctly.

---

### Post by matt2053 on 2012-03-25
> **zombifier25 said:**
> Maybe they should include a tiny icon next to an entry :P
Just a suggestion.

That's not a bad idea but would probably require some major changes (currently there is only room to display one icon at a time.

My idea would be to update the focus (and show the highlighted entry's icon) when you mouse over it in the list.

I posted it as a suggestion here:

[https://bugs.launchpad.net/ayatana-design/+bug/963986](https://bugs.launchpad.net/ayatana-design/+bug/963986)

---

### Post by screaminj3sus on 2012-03-25
> **matt2053 said:**
> That's not a bad idea but would probably require some major changes (currently there is only room to display one icon at a time.

My idea would be to update the focus (and show the highlighted entry's icon) when you mouse over it in the list.

I posted it as a suggestion here:

[https://bugs.launchpad.net/ayatana-design/+bug/963986](https://bugs.launchpad.net/ayatana-design/+bug/963986)
It (mostly) already does this. It doesn't do it on mouseover, but if you use the keyboard to highlight the entry the icon does change.

---

### Post by matt2053 on 2012-03-26
> **screaminj3sus said:**
> It (mostly) already does this. It doesn't do it on mouseover, but if you use the keyboard to highlight the entry the icon does change.

Yes, exactly. I think this behavior should be extended to mouse-over because many users don't like to use keyboard arrows in these situations.

---

### Post by quequotion on 2012-04-17
> **keithpeter said:**
> Where is the unity-checklist? I never installed it or changed any settings to enable it so I wouldn't know.
My previous installation was an upgrade from Oneiric to Precise and I think it was automatically installed as part of the early testing phase. Since then It would ask me to run the tests over again after every upgrade... Not had to do it yet on a new, fresh install of Precise.

> The unity devs/designers read and respond to that list.
[https://launchpad.net/~unity-design](https://launchpad.net/~unity-design)

That's encouraging. I will take a look.

> **keithpeter said:**
> Try installing lo-menubar. lo-menubar is long dead.
It hasn't worked for quite some time now and no one is maintaining it.

> **jbicha said:**
> Matt, I still think that those apps are wrong.  The apps are not wrong. Canonical's "standard" is wrong.
What standard are these indicators supposed to follow?
How likely is that standard to last six months?

In my honest opinion, there is nothing standard about the entire Ubuntu desktop experience at the moment. Even after the release of Precise I'll consider it beta until I see some major re-adoption from all those refugees who ran to Mint and elsewhere.

---

### Post by jbicha on 2012-04-17
> **quequotion said:**
> 
 The apps are not wrong. Canonical's "standard" is wrong.
What standard are these indicators supposed to follow?
How likely is that standard to last six months?

In my honest opinion, there is nothing standard about the entire Ubuntu desktop experience at the moment. Even after the release of Precise I'll consider it beta until I see some major re-adoption from all those refugees who ran to Mint and elsewhere.

"Power Settings...", "Sound Settings...", etc has been that way for at least 6 months. In Lucid, Maverick and Natty, it was "Sound Preferences..." which is pretty close.

---

### Post by quequotion on 2012-04-19
> **jbicha said:**
> "Power Settings...", "Sound Settings...", etc has been that way for at least 6 months. In Lucid, Maverick and Natty, it was "Sound Preferences..." which is pretty close.

I think you misunderstood; six months is a dismally short time in which to declare anything "standard".

Luckily, Precise is to be an LTS with extended service so it's features will have a chance to become standard--provided they prove worthwhile.

---

### Post by qamelian on 2012-04-19
> **quequotion said:**
> lo-menubar is long dead.
It hasn't worked for quite some time now and no one is maintaining it.

 It works just fine on 12.04 on my netbook.

---

