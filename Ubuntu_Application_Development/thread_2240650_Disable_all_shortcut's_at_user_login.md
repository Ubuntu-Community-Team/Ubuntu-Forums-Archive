---
title: "Disable all shortcut's at user login"
date: 2014-08-21
forum: Ubuntu Application Development
---

### Post by gijs3 on 2014-08-21
Hi,

[COLOR=#333333][FONT=UbuntuRegular]I'm building a deb package that will create a kiosk user account. When you login to this account, the browser automatically starts and navigates to a pre-given website. Also all the hotkeys should be disabled except for one you defined.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Now I'm at the part that the browser starts and my disable script is excecuted on logon but for exaple, I can still close the browser with Alt + F4. And when i check the dconf-editor for the hotkeys, for every single one the bind is deleted, but mine for close isn't added. Like you can see in the image in the url. (I tried to post it in the post but it was annoyingly big)
[http://i.imgur.com/MnIDBct.jpg](http://i.imgur.com/MnIDBct.jpg)
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I disabled all these keys with this code, one line for evere hotkey[/FONT][/COLOR]
*[COLOR=#000000]gsettings [/COLOR][COLOR=#00008B]set[/COLOR][COLOR=#000000] org[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]gnome[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]desktop[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]wm[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]keybindings begin[/COLOR][COLOR=#000000]-resize [/COLOR]*[COLOR=#000000][I][]
[/I]
[/COLOR][COLOR=#333333][FONT=UbuntuRegular]So this seems to work, but at the bottom of my disable script this line should be executed.[/FONT][/COLOR]
[I][COLOR=#000000]gsettings [/COLOR][COLOR=#00008B]set[/COLOR][COLOR=#000000] org[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]gnome[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]desktop[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]wm[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]keybindings close [/COLOR][COLOR=#000000][[/COLOR][COLOR=#800000]'<Alt>b'[/COLOR][COLOR=#000000]]
[/COLOR][/I][COLOR=#333333][FONT=UbuntuRegular]
Does anyone know why i'm able to unbind all these hotkeys in my dconf-editor but they are able to still do their job? And when it is possible to unbind them, why cant I bind mine? I searched the web for a solution but couldn't find one fitting my needs, I hope some of you know the answer to this.

regards

[/FONT][/COLOR]

---

