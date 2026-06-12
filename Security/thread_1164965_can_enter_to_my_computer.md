---
title: "can enter to my computer"
date: 2009-05-20
forum: Security
---

### Post by prog154 on 2009-05-20
[LEFT][FONT=Times New Roman, serif][SIZE=3]I can't enter to my computer using ubuntu because it don't allow me to use English letters to type my user name, does somebody know how to change it? or I should reinstall this program?

looking forward to hear from you!):P
Meir [/SIZE][/FONT] [/LEFT]

---

### Post by b@sh_n3rd on 2009-05-20
That's weird...Did you choose the correct keyboard layout and language when installing Ubuntu?

---

### Post by prog154 on 2009-05-20
> **b@sh_n3rd said:**
> That's weird...Did you choose the correct keyboard layout and language when installing Ubuntu?
 	 	 [LEFT][FONT=Times New Roman, serif][SIZE=3]
Yes I did, after installation I add new language, Hebrew but I didn't delete English, I can use English if I press at the same time shift but it don't help me because in this way the letters are capital. [/SIZE][/FONT] [/LEFT]
 [LEFT]
[/LEFT]
 

Looking forward for your help

---

### Post by b@sh_n3rd on 2009-05-20
Hebrew? cool...my fav. lang :D... So when you type your user name, it comes in Hebrew is it? Is there a menu somewhere on the login screen to choose a language? I haven't really messed with multiple langs on Ubuntu but only on Fedora...But that always had english to login and the language selection menu was only for the GNOME UI after login...

---

### Post by prog154 on 2009-05-20
Yes, it is comes in Hebrew and I can choose language the problem is that it don't show English as option. The only option is Hebrew.

Can I change the properties and add English?

---

### Post by b@sh_n3rd on 2009-05-20
I think English has got removed for some reason...you may have to install it separately...I'll check on it...
What happens when you hit, "Ctrl+Alt+F2"?? You should end up on the console, is the console in english?? If it is, try "sudo apt-get install language-pack-gnome-en-base"...It's strange how it should be hebrew, unless the language defaults were changed in "Language Support"

Hey, I just got a brain wave, how about you boot in recovery mode into a root shell (if ctrl+alt+f2 doesn't give english...this *might*...I hope) and remove, "language-pack-gnome-he-base"...make sure "language-pack-gnome-he" is also removed...when ONE of em (i'm not sure which one, i think base) is removed, apt will remove the other one too..After that, reboot (type, "sudo reboot" or "sudo shutdown -r now") and check if you've got english...I'm sure the defaults have changed in someway...unless someone could point out how to change that from the console...

---

