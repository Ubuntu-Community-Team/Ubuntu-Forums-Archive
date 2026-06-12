---
title: "Annoying Keyboard Layout Switcher"
date: 2014-01-15
forum: Ubuntu Development Version
---

### Post by Yellow Pasque on 2014-01-15
Using Xubuntu..
I now have an annoying keyboard layout switcher in the indicator area. I have a standard English keyboard and I have no need for such a thing. How do I get rid of it?
I looked through all installed packages related to keyboard and the only one I see is kbd (which removes gnome-control-center).

Thanks

---

### Post by Royke on 2014-01-15
@Temüjin,

Hello, it would help to know your xubuntu version. I'm using UbuntuStudio12.04 wich also uses the xfce environment. You might have several (or one) other keyboardlayout installed and if you delete them it might just auto-dissapear after relogging in. 
Good luck!

---

### Post by Yellow Pasque on 2014-01-15
> **Royke said:**
> @Temüjin, it would help to know your xubuntu version.

Huh? This subforum is only for the current Ubuntu development release (Trusty/14.04). I think you got lost :lolflag:

---

### Post by grahammechanical on 2014-01-15
It would not be the first time that someone has posted in this section thinking that it is populated by genius experts who must surely know the answer to every problem. :)

I am not about to load into Xubuntu Trusty Tahr to check this out but when I click on that keyboard icon in Ubuntu and I select Text Entry Settings I see in the dialog that appears a box that is ticked called "Show current input source in the menu bar." When I untick that box the keyboard app indicator icon disappears. Xubuntu might/must have something similar.

I think that this comes about because even if we select UK English as the language for the OS we seem to get a US keyboard layout option as well as an UK keyboard layout option.

Regards.

---

### Post by Bucky Ball on 2014-01-15
Yes, I can confirm this was happening to me on 3.13.0-2-generic, but booting today and it has gone away. I'm not sure if this just happened with a few other updates today or happened when I updated to kernel 3.13.0-3-generic a couple of hours ago. But it definitely was happening.

Do an update/upgrade and see if problem persists.

---

### Post by Royke on 2014-01-15
> **Temüjin said:**
> I think you got lost :lolflag:

Oops, i clicked on the rss-link on my desktop without checking, please excuse..

I hope your ploblem is solved now,

Greetings

---

### Post by Yellow Pasque on 2014-01-16
I guess it's related to ibus
Settings -> Keyboard Input Methods -> General tab -> "show icon on system tray"

---

### Post by Bucky Ball on 2014-01-16
As I mentioned, my problem with this just disappeared, but I'm wondering ... there is another thread about the keyboard not working at login until clicking the keyboard layout icon in the login window. Are these two things connected? Possibly not because I still get that one occasionally, but just a thought ... :-k

---

