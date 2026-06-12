---
title: "Workaround for Changing keyboard shortcuts  such as copy and paste using Autokey"
date: 2011-05-21
forum: Tutorials
---

### Post by edchuu on 2011-05-21
I was looking all around the internet for a way to change the shortcuts such as copy and pastes since I changed my keyboard layout to Dvorak. Sadly, I have not found one yet (May 2011). However, I found that Autokey can replace keyboard commands. It isn't a complete fix but a workaround. If someone has a better solution please do share with us. 

**Step 1**

Download **Autokey** from either the Ubuntu Software Center or use the terminal
>  sudo apt-get install autokey-gtk 

**Step 2 **

Open Autokey **Menu -> Accessories -> Autokey (GTK)**

**Step 3**

Create a New Top-Level Folder from **File -> create -> New Top-Level Folder**

**Step 4** 

Select Folder and create New Script from **File -> create -> New Script**

**Step 5** 

in the "# Enter script code" enter "keyboard.send_keys([COLOR="Red"]shortcut you desire to imitate[/COLOR])" 

Examples

1. keyboard.send_keys("<ctrl>+v")
2. keyboard.send_keys("<ctrl>+c")
3. keyboard.send_keys("<ctrl>+s")

NOTE: repeat Step 4-5 for each hotkey you want to add

**Step 6** 

Click on the second "set" on the Hotkey and set your hotkey

**Step 7**

Test them out.

It should work now. 

**Extra Stuff**

Enable automatically start Autokey at login (**Edit -> preferences -> general) **, clear the special hotkeys **(Edit -> preferences -> Special Hotkeys)** and we are done.

[COLOR="Red"]This is my first forum post so go easy on me :) [/COLOR]

---

### Post by Tinos on 2011-11-25
Thanks! I just set the phrases under My Phrases. Strangely the QT version tried to install an insane number of packages.

---

### Post by bjlorenzen on 2012-03-18
Thanks so much for this Edchuu! I wish there were options to change keybindings by default in Ubuntu, but this workaround suffices.

---

