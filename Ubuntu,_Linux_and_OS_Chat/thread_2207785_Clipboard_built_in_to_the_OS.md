---
title: "Clipboard built in to the OS?"
date: 2014-02-25
forum: Ubuntu, Linux and OS Chat
---

### Post by MrWestwood on 2014-02-25
I've used Ubuntu since 8.04 and it still baffles me that I can't copy and paste data if I've closed the application I'm pasting from. E.G. If I want to copy text from gedit into Firefox. Once I've copied the text I must keep gedit open in order to paste the text elsewhere.

Will this ever be implemented or do I have to download Parcelite?

---

### Post by TheFu on 2014-02-25
I'm still pissed that many apps don't honor the 30+ yr old X/Windows x-buffer select-paste methods.  You know - select with the left mouse button, then paste with the middle button.  I'm talking about Firefox, but many others.

As a former X/Windows coder, I know they have to go out of their way to break this behavior. Congratulations GUI creators. Nice job.

For your needs, install a paste buffer manager.

---

### Post by ssam on 2014-02-25
The reason for this is that the 2 programs need to negotiate which format to do the transfer in. To make a mechanism that allows the sender to close, you have to have a buffer somewhere that either holds all possible formats (which uses lots of memory) or just a simple format (plain text) that can be guaranteed to work.

---

### Post by SeijiSensei on 2014-02-25
The built-in Klipper applet in KDE has a "save contents after exit" option which is on by default on my Kubuntu 14.04 machine and likely enabled in earlier versions as well.  Klipper shows up in the task bar as part of the default Kubuntu installation.

---

### Post by rewyllys on 2014-02-25
> **SeijiSensei said:**
> The built-in Klipper applet in KDE has a "save contents after exit" option which is on by default on my Kubuntu 14.04 machine and likely enabled in earlier versions as well.  Klipper shows up in the task bar as part of the default Kubuntu installation.
Back in the good old Gnome 2 days, Glipper served as the Gnome version of Klipper, and did the job just fine.  But Glipper disappeared with the much lamented switch to Gnome 3.

Nowadays I use Parcellite, which has worked beautifully for me in Linux Mint 13 (which is based on Ubuntu 12.04).

---

### Post by 3rdalbum on 2014-02-25
Totally agreed. It is an embarrassment that we can't even copy and paste correctly. At least Wayland and Mir might resolve this.

---

### Post by mastablasta on 2014-02-26
i was surprised when i saw that Klipper saved stuff that i copied into buffer some time ago on the netbook that is constantly turned off and on...

i am even more surprised the same functionality doesn't exists by default in Unity. 
:(

---

### Post by su:bhatta on 2014-02-26
Just read this thread yesterday and this came up in webupd8 ! Now that is coincidence !

But this might be a solution : [http://www.webupd8.org/2014/02/gnome-shell-clipboard-extension-gpaste.html](http://www.webupd8.org/2014/02/gnome-shell-clipboard-extension-gpaste.html)

Using KDE, if I need, I use Klipper !

---

### Post by dbass81 on 2014-02-27
I use ClipIt on Openbox, or there is Parcellite, those are both in GTK+

---

### Post by vasa1 on 2014-02-27
> **dbass81 said:**
> I use ClipIt on Openbox, or there is Parcellite, those are both in GTK+
+1 for Clipit although I don't use any clipboard manager at all. I just remember to paste before closing ;)

---

