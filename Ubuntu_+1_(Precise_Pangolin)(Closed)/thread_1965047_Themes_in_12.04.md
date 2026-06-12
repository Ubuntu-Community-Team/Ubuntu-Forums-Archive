---
title: "Themes in 12.04"
date: 2012-04-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by vasa1 on 2012-04-25
With reference to 12.04 ... 

In /usr/share/themes, there are 20 themes listed. However, when one right-clicks on "Desktop", and then clicks on "Change Desktop Background", the "Look" tab has themes, but only four choices: Ambiance, Radiance, High Contrast, and High Contrast Inverse.

What do I need to do to check out the remaining themes?

(In 11.10, I installed "Advanced Settings" aka "Gnome Tweak Tool" to switch themes. It is still available in the Software Center.)

---

### Post by zombifier25 on 2012-04-25
Ubuntu's default theme changer will NOT list 3rd party themes. You need to install a tool like MyUnity of Ubuntu Tweak for this.

---

### Post by vasa1 on 2012-04-25
> **zombifier25 said:**
> Ubuntu's default theme changer will NOT list 3rd party themes. You need to install a tool like MyUnity of Ubuntu Tweak for this.
So the remaining themes that are installed by default in usr/share/themes are 3rd party?
BTW, Ubuntu Tweak lists a few more.

---

### Post by zombifier25 on 2012-04-25
> **vasa1 said:**
> So the remaining themes that are installed by default in usr/share/themes are 3rd party?
Actually no. In my case most of the themes in /usr/share/themes not listed are Openbox themes. However I have installed LXDE (which comes with Openbox).
Try viewing the themes' folders. If it doesn't contain a folder named gtk-3.0 then that theme is not to be used for GNOME.

---

### Post by grahammechanical on 2012-04-25
did you upgrade to 12.04 or fresh install?

I am using a 12.04 that was slowly upgraded by daily updates from 11.10. I find that in /urs/share/themes there are folders/files/scripts left over from when this OS was 11.10 and there were more themes available.

This could be what you are seeing.

As part of ISO testing I recently installed a default 11.10 and then upgraded it to 12.04. I have just loaded that install and yes, all the 11.10 themes stuff is in /usr/share/themes but they are not available as themes. They are themes created with the gtk-2 tool kit and 12.04 uses themes created with the gtk-3 tool kit. If you open the folders for Ambiance and Radiance you will see that those themes have stuff that is both gtk-2 and gtk-3. Likewise with the other two themes in 12.04 but not with the old themes.

Regards.

---

### Post by vasa1 on 2012-04-25
No, this is a fresh install. (I was thinking about upgrading but decided against it. I even got a new "home").

I'll put up more details in a while about the contents of /usr/share/themes.

And I haven't installed any third party themes or even other DEs. I'm just trying to get to know PP first!

---

### Post by vasa1 on 2012-04-25
Here's a list of what I have in /usr/share/themes:
[https://docs.google.com/file/d/0B4gs9P5_zkgeNkZWa1AxZlFPWGc/edit?pli=1](https://docs.google.com/file/d/0B4gs9P5_zkgeNkZWa1AxZlFPWGc/edit?pli=1)

As I said, I believe this is part of the install of the RC of 12.04 that I grabbed on 21/04. It was a clean install, not upgrade, and I haven't added anything.

---

### Post by ubuntu27 on 2012-04-25
Currently, Ubuntu 12.04 is hardcoded to only show the 4 default themes.

We need to use [MyUnity]("atp://myunity") to select the themes.

---

### Post by marrok1 on 2012-04-25
I use gnome-tweak-tool to change the gtk3 themes on the system as well as the metacity themes

---

### Post by vasa1 on 2012-04-26
> **ubuntu27 said:**
> Currently, Ubuntu 12.04 is hardcoded to only show the 4 default themes.

We need to use [MyUnity]("atp://myunity") to select the themes.
Thank you for clearing that up.

Of the three "tweaking" tools available, I used *Gnome Tweak Tool* with 11.10 and now I'm trying *Ubuntu Tweak*.

Ubuntu Tweak also shows fewer options than are present in /user/share/themes:
Under **Gtk theme**, I see:
Ambiance
HighContrast
HighContrastInverse
LowContrast
and
Radiance.

Under **Window Theme**, I see:
AgingGorilla
Ambiance
Atlanta
Bright
Crux
Esco
Metabox
Radiance
and
Simple.

When on 11.10, I had played with a bunch of css files but changing just one parameter could have multiple effects and so it's not my first choice.

---

