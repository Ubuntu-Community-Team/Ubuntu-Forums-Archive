---
title: "Dvorak Keyboard"
date: 2008-01-31
forum: The Cafe
---

### Post by Dr Small on 2008-01-31
I want to learn dvorak, but I need a dvorak keyboard.
I've searched Ebay, Newegg, TigerDirect and Amazon, but none seem to have any dvorak keyboards, or they are too high priced.

I just want to find a cheap plain one (preferably white or so).
(Yes, I know I could just move my keys around, but it works for most of the keys but two or so, and I had to turn them upside down to get them to go on, so that wasn't good...)

Any ideas where to find one?

---

### Post by peabody on 2008-01-31
Well, I've been a long time dvorak user, but have never had a hardware based dvorak keyboard.  I just switched the layout to dvorak and learned to touch-type it.  Much cheaper that way :), but since you seem so set on getting a hardware based keyboard, I won't say anything else to dissuade you.

---

### Post by Dr Small on 2008-01-31
Ok, I guess I could do that. I may end up getting stickers later though, if I do learn it, but I thought it would help if I could look down at it O.O

:D

Dr Small

---

### Post by peabody on 2008-01-31
> **Dr Small said:**
> Ok, I guess I could do that. I may end up getting stickers later though, if I do learn it, but I thought it would help if I could look down at it O.Ol

heh, for touch-typing you should never be looking at the keys anyway :).

---

### Post by -grubby on 2008-01-31
you can always switch the keys around on the keyboard itself

---

### Post by Dr Small on 2008-01-31
> **nathangrubb said:**
> you can always switch the keys around on the keyboard itself
That didn't work for me...

Say, how would I do it for X11 and TTYs ?
Because i'm on iceWM.

Dr Small

---

### Post by fedex1993 on 2008-01-31
typematrix.com i just bought one tonight

---

### Post by peabody on 2008-01-31
Good question, I don't know, however, I do know that you can set it as default for Xorg, this is my keyboard section for my xorg.conf:

```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
        Option          "XkbVariant"    "dvorak"
EndSection

```

Might be painful for you though, with no way to switch back :).

In gnome you can use the keyboard indicator panel applet and switch back and forth with the gui.  Might be useful to get that setup for yourself in icewm.

---

### Post by der_joachim on 2008-02-01
@OP Welcome brother. We were expecting you. :)

A few tips. I switched 8 months ago and I do not want to switch back. 

1. Just keep using your old keyboard. Instead, learn how to touch type. 

2. Learning how to touch type is a slow and painful process. I recommend to install a program like Ktouch or another typing tutor.

3. If you have any other non Dvorak users at your PC, there still should be a way to switch. There's roughly two ways: by using a key combo or wy using an applet. KDE's keyboard switching applet is my favourite. Just click it and you switch. The other way is by simply pressing Alt+Shift. You'll have to edit your xorg.conf though. Your keyboard section should look like this:
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us(intl),us(dvorak)"
        Option         "XkbOptions" "**grp:alt_shift_toggle**,compose:ralt,eurosign:5,altwin:super_win"
EndSection

```
The bold section is about switching layouts. In my case US QWERTY is default, since my wife occasionally uses linux as well. 

4.  You can quite easily edit your default layout for the console as well. Open /etc/default/console-setup and insert the following lines (after making a backup of the old version):
```

# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.
XKBMODEL="pc105"
XKBLAYOUT="us(dvorak),us(intl)"
#XKBVARIANT="dvorak"
XKBOPTIONS="grp:alt_shift_toggle,compose:ralt,eurosign:5,altwin:super_win"

```

Good luck.

---

### Post by Dr Small on 2008-02-01
Thanks.
As for #4, do I need to reboot for it to work? Because I changed it and it didn't work.

---

### Post by NineKnuckles on 2008-02-01
I'm teaching myself Dvorak ATM.  Luckily for me I haven't learned to touch type with qwerty, so it should be easier.  Anyway, check _[www.keybr.com](www.keybr.com)_ - it's a great website that supports loads of languages and layouts plus its got an onscreen keyboard to get you out of the habbit of looking at your actual keyboard.  There's no downloading or anything, just a quick, simple site that gets the job done.  All you have to do is be able to reconfigure the keyboard your using now.  _[This]("http://www.dvorak-keyboards.com/Change_qwerty_keyboard_to_Dvorak_in_30_seconds.htm")_  should help with that.  But seeing as I'm waiting for my Ubuntu laptop to be delivered, I've only changed my keyboard using XP so far.

---

### Post by der_joachim on 2008-02-02
> **Dr Small said:**
> Thanks.
As for #4, do I need to reboot for it to work? Because I changed it and it didn't work.

A reboot would help. This command might help as well:
```

sudo /etc/init.d/console-setup restart

```

Additionally, there is a configuration tool for the console, which has been mentioned in earlier dvorak threads. Its name eludes me (not enough coffee today yet).

---

### Post by red_Marvin on 2008-02-02
A big part of the reason I wanted to learn dvorak, was that I wouldn't be able to look at the keys to search for the right ones. When I were still learning the key positions I drew the keymap on a piece of paper and hung it on the top of my screen and kept on typing dvorak until i didn't need the cheat-sheet anymore.

I do however make more mistakes now than with qwerty but I would guess that those come from some part of the qwerty layout still stuck in the "muscle memory" and also that I'm somewhat unaccustomed to typing with all fingers and coordinating both hands at the same time.

---

### Post by der_joachim on 2008-02-02
About the fold-out keymap: [this site]("http://dvzine.org/") helped me a lot.

An additional tip for Opera users: it has a dvorak widget. I rarely use it anymore, but it draws a dvorak keyboard layout on your screen.

---

### Post by Dr Small on 2008-03-07
> **Dr Small said:**
> Thanks.
As for #4, do I need to reboot for it to work? Because I changed it and it didn't work.
I finally got around to rebooting (after 39.999999 days of uptime), and two days later I remembered about the console. So I went to it, and now it works with Dvorak!

Thanks for the help :)

---

### Post by EarloftheWest on 2008-05-22
I've been typing with Dvorak for about 10 years. 
A new keyboard variation Colemak has appeared. If I was to learn a new keyboard layout I would probably focus on Colemak. 
Colemak is officially supported by X11.

---

