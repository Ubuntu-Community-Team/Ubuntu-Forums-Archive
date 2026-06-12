---
title: "Which *box do you prefer?"
date: 2008-07-27
forum: The Cafe
---

### Post by RiceMonster on 2008-07-27
If you're using a *box, which one are you using? 

I'm using Openbox. I like it because it's really "bare bones", so i can run it without a panel. I also like how the two configuration files are XML rather than a custom syntax like Fluxbox.

Mods: Feel free to move this to recurring discussion if necessary.

---

### Post by cardinals_fan on 2008-07-27
I'm an Xfce user, but I've used Openbox extensively and it's awesome.  It's not technically a *box, but I consider Pekwm to fit the same mold.

---

### Post by chucky chuckaluck on 2008-07-27
i've used openbox more than anything else and i'm back with it after a long, torrid affair with tiling wm's. really don't see a whole ton of difference between openbox and fluxbox, but i hate most of the themes for fluxbox. i agree that pekwm probably fits in here. didn't know blackbox still existed.

---

### Post by Mateo on 2008-07-27
X-box.

---

### Post by Canis familiaris on 2008-07-27
I have only used Fluxbox in DSL and I was impressed.
But I prefer IceWM.

> **Mateo said:**
> X-box.
So this poll was about all *box

So I'll vote for [GeeXboX]("http://geexbox.org/en/index.html")

---

### Post by walkerk on 2008-07-27
Ob ftw :)

---

### Post by billgoldberg on 2008-07-27
Fluxbox.

---

### Post by urukrama on 2008-07-27
Openbox, by far the best of those three. I always return to it.

Pekwm is neat too, and an occasional favourite, but has a number of odd quirks.

---

### Post by miggols99 on 2008-07-27
When I need something lightweight, I always turn to **Openbox**. It's great because it's really easy to configure and looks great :)

---

### Post by smartboyathome on 2008-07-27
I would have to say, of the three choices, I would pick Openbox. I am an E17 user, though, so I don't use Openbox that much. ;)

---

### Post by jimrz on 2008-07-27
fluxbox

---

### Post by kitili on 2008-07-27
openbox, i dont like panels..

---

### Post by markp1989 on 2008-07-27
> **Anurag_panda said:**
> I have only used Fluxbox in DSL and I was impressed.
But I prefer IceWM.


So this poll was about all *box

So I'll vote for [GeeXboX]("http://geexbox.org/en/index.html")

lol +1

---

### Post by urukrama on 2008-07-27
> **kitili said:**
> openbox, i dont like panels..

You know you can turn it off in Fluxbox, right?

---

### Post by Mateo on 2008-07-27
> **kitili said:**
> openbox, i dont like panels..

Interesting.  How do you navigate between windows?

---

### Post by RiceMonster on 2008-07-27
> **Mateo said:**
> Interesting.  How do you navigate between windows?

I don't use a panel either. I use alt-tab to raise minimized windows and to switch between them. Then there's keyboard shortcuts like ctrl-alt-right to go to the workspace to the right, alt-f1 for workspace 1, alt-f2 for workspace 2, and so on and so fourth.

In short, keyboard shortcuts.

---

### Post by jviscosi on 2008-07-28
Of that list I would pick Fluxbox, but lately I've been spending all my time in PekWM which is like a first cousin with a different last name.  The latest git version of PekWM fixed most of the problems I had with it, though some quirks do remain.

---

### Post by snowpine on 2008-07-28
> **kitili said:**
> openbox, i dont like panels..

Lately, I've been messing around with crunchbang, which is openbox with panels. :)

I've also used fluxbox a lot, by way of fluxbuntu. 

So I can't really vote in the poll.

---

### Post by Kingsley on 2008-07-28
I have a slight interest in Fluxbox.

---

### Post by vishzilla on 2008-07-28
Openbox

---

### Post by sujoy on 2008-07-28
i use either awesome,xmonad or openbox. used fluxbox only for some weeks, didn't like it much. openbox is so much better. :)

---

### Post by RedSquirrel on 2008-07-28
Openbox, I guess. However, since I don't really like XML I think Fluxbox's custom syntax is nicer. :D

While the default themes that are installed with Fluxbox are nothing to write home about, there are some great-looking themes for Fluxbox elsewhere:

[http://tenr.de/styles/](http://tenr.de/styles/)
[http://box-look.org](http://box-look.org)

I used Fluxbox almost exclusively in the past, but I find myself using tiling window managers most often these days (running [ratpoison]("http://www.nongnu.org/ratpoison/") right now).

Blackbox is not actively maintained anymore.

---

### Post by kitili on 2008-07-28
> **Mateo said:**
> Interesting.  How do you navigate between windows?
middle click, to change, and right to open.

---

### Post by init1 on 2008-07-28
There's also hackedbox, but I don't think many people use that. It was in LNX-BBC. 
[http://en.wikipedia.org/wiki/Hackedbox](http://en.wikipedia.org/wiki/Hackedbox)

---

### Post by chris4585 on 2008-07-28
Openbox <3

Openbox is just really simple, but not really simple.

---

### Post by thisllub on 2008-07-29
> **RiceMonster said:**
> I don't use a panel either. I use alt-tab to raise minimized windows and to switch between them. Then there's keyboard shortcuts like ctrl-alt-right to go to the workspace to the right, alt-f1 for workspace 1, alt-f2 for workspace 2, and so on and so fourth.

In short, keyboard shortcuts.

Some of my rc.xml.
Just these functions make Openbox superior to Gnome & KDE.

E17 will do most of this but it still crashes a bit too much.

> 
 <!-- Shows open applications -->
    <keybind key="C-Menu">
      <action name="ShowMenu">
        <menu>client-list-combined-menu</menu>
      </action>
    </keybind>

  <!-- Moves window to top left and resizes to 1200x1000 (Left monitor)-->
    <keybind key="W-w">
      <action name="MoveResizeTo">
        <height>1000</height>
        <width>1200</width>
        <x>+0</x>
        <y>+0</y>
      </action>
    </keybind>

  <!-- Moves window to top right and resizes to 1600x1000 (Right monitor)-->
    <keybind key="W-e">
      <action name="MoveResizeTo">
        <height>1000</height>
        <width>1600</width>
        <x>-0</x>
        <y>+0</y>
      </action>
    </keybind>
  <!-- Maximise toggle Horizontal-->
    <keybind key="C-A-h">
      <action name="ToggleMaximizeHorz"/>
    </keybind>
  <!-- Maximise toggle Vertical-->
    <keybind key="C-A-v">
      <action name="ToggleMaximizeVert"/>
    </keybind>


---

### Post by tel93 on 2008-07-29
> **sujoy said:**
> openbox is so much better. :)
not to mention faster, prettier, more stable, easier to use, more custiomisable, etc.

---

### Post by dje on 2008-07-29
> **tel93 said:**
> not to mention faster, prettier, more stable, easier to use, more custiomisable, etc.

+1 openbox ftw

---

### Post by snowpine on 2008-07-29
I'd never heard of Blackbox before this poll, so I tried it out last night. It's like Openbox without the bloat, LOL! Seriously, though, there is something rather Zen about it, and I imagine one could be quite productive on it. I'm certainly not planning to switch over full time, though.

---

