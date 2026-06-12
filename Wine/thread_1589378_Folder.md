---
title: "Folder"
date: 2010-10-06
forum: Wine
---

### Post by FahadMKS on 2010-10-06
Hi,

I had been using the Wine software for a while and now I have uninstalled from my computer as there is no longer need of that.
I uninstalled the Wine Via Ubuntu Software Center.
But now the issue is that the Wine is listed there on my Applications menu.
I need to get rid of that.
Can anyone help me with that issue?

---

### Post by t.rei on 2010-10-06
rightclick the menu -> edit menus -> uncheck wine

:)

---

### Post by FahadMKS on 2010-10-06
That was pretty good dude.
It really worked.

Now if you do not mind, I have a question left.
When I try to open a file using the option "Open With" a lot of applications including the Wine applications is listed there.
I removed some of them using the button remove, but in case of the Wine Applications mentioned there, I am not able to do that.

Can you help me with that issue too..... Please.......

---

### Post by t.rei on 2010-10-09
Hm, as far as I know every entry you see there can be edited by:

rightclick the file-icon -> properties -> open with (tab)

I remember having the same thing, I think thats what I did.

---

### Post by Soulcage on 2010-10-09
rm -rf $HOME/.wine && rm -f $HOME/.config/menus/applications-merged/wine* && rm -rf $HOME/.local/share/applications/wine && rm -f $HOME/.local/share/desktop-directories/wine* && rm -f $HOME/.local/share/icons/????_*.xpm && rm -f $HOME/.local/share/applications/wine-extension*

Copy all of that part above and paste it at once into a terminal.

Also open ~/.local/share/icons and delete the appropriate files. If there's anything else in there.

---

### Post by FahadMKS on 2010-10-09
I had posted this as a seperate Thread as there was no reply for this one and I have got the issue resolved.

But I thank you for the Time you spent to answer my query.
Thank you guys.

---

