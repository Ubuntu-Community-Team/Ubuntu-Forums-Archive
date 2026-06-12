---
title: "Wine Uninstall."
date: 2009-07-10
forum: Wine
---

### Post by Aidenstar on 2009-07-10
I uninstalled wine using synaptic because wine doesnt play my games the way I want it to. However even after I uninstall it, it still shows a folder named wine under my applications menu. I was wondering if anyone can tell me how to take that off. Or what is the command to completely take wine off.

Using my fle manager and searching wine, I can still see that there are a lot of files associated with it, even after uninstalling it. However they are all locked and wont let me delete them. Can someone help me solve this problem.

---

### Post by ackanao on 2009-07-11
Wine menu bug is almost fixed with Wine 1.1.25; You have to delete old menu entries manually:

Goto "**~/.config/menus**" folder, open "applications.menu" file in your text editor and delete everything related to Wine except:

```

	<Menu>
		<Name>wine-wine</Name>
	</Menu>

```

Goto "**applications-merged**" folder and delete everything related to Wine. Then install latest version of Wine - here are the instructions on how to enable WineHQ repositories on Ubuntu:

[http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb")

---

### Post by Aidenstar on 2009-07-12
I had to completely reinstall Ubuntu for an unrelated reason. When I decide to install Wine again I'll be sure to download the newest version.

Thanks for your help.

---

### Post by johnycage on 2009-07-12
didnt  you try to remove it via
**system>preferences>main menu **
& then remove the mark of wine...

it should be OK.

---

