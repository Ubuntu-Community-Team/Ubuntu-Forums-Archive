---
title: "Compiz effects don't work in ubuntu 18.04 ?"
date: 2018-04-04
forum: Ubuntu Development Version
---

### Post by marvi2 on 2018-04-04
Hi guys.
I am a new user of ubuntu and i try to learn .
I switch from windows 10 because i am sick to share my privacy whit microsoft and google
I like to know if compiz  work in ubuntu 18.04 like burn effect ....etc
I have installed compiz and i try the default effects but nothing change
Sorry for my english
Thanks

---

### Post by dino99 on 2018-04-04
compiz is no more used with 'ubuntu' and 'gnome' session. I suppose it is still used with 'gnome-fallback' session and possibly 'lubuntu' or 'mate'

---

### Post by marvi2 on 2018-04-04
Thanks
Any idea is is something else to rplace compiz whith same effcect?

---

### Post by wildmanne39 on 2018-04-04
*Thread moved to **Ubuntu Development Version, a more appropriate forum**.*

---

### Post by monkeybrain20122 on 2018-04-04
You can still use compiz and unity. unity is not default but an easy apt install away on 18.04

```
sudo apt install unity-session xserver-xorg-input-synaptics
```

log out and then in the greeter choose unity session to login again, that's it.

Or you can get a unity respin iso [here]("https://community.ubuntu.com/t/new-ubuntu-unity-iso/2146"). Have been testing it for a month or so, very stable.

---

### Post by Claus7 on 2018-04-05
Hello,

> **marvi2 said:**
> Hi guys.
I am a new user of ubuntu and i try to learn .
I switch from windows 10 because i am sick to share my privacy whit microsoft and google
I like to know if compiz  work in ubuntu 18.04 like burn effect ....etc
I have installed compiz and i try the default effects but nothing change
Sorry for my english
Thanks

the immediate answer is that compiz is working with ubuntu 18.04.

Since you have already opened ccsm then it means that you have already installed it. Open ccsm and for burning effect:
i) go to effects and enable Animations and Animations Add-On
ii) log out and back in
iii) if you select Animations then you will be able to see more options available including the Burn effect
iv) if you would like to add it in minimize options for example, then go to Minimize Animation, press "new" and then in the edit options add:
[table="width: 500, class: grid, align: left"]
[tr]
	[td]Minimize Effect[/td]
	[td]Burn[/td]
[/tr]
[tr]
	[td]Duration[/td]
	[td]220[/td]
[/tr]
[tr]
	[td]Window Match[/td]
	[td](type=Normal | Dialog | ModalDialog | Unknown)[/td]
[/tr]
[/table]

press close, select the new effect and press "up".

Voila! When you minimize your applications you will see a burning effect!

Or if you would like to see the same effect while opening any application, go to Open Animation, press "new", and type in Window Match: 
type=Normal

press "up" until this effect is the first one in the list and any application you open will be on fire!

These took place in gnome-session-flashback compiz. 

Regards!

---

