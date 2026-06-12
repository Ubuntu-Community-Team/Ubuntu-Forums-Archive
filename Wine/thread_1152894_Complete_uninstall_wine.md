---
title: "Complete uninstall wine"
date: 2009-05-08
forum: Wine
---

### Post by skygazer on 2009-05-08
I installed and then uninstalled wine on my ubuntu 8.04 LTS. But the installation directory still appears in the Applications menu. I tried uninstalling it but it doesnt go away.
How should i get rid of it?.. Pls help

---

### Post by cogadh on 2009-05-08
Open the menu editor and manually delete it (it is found in the Preferences menu). You should note that if you ever have a need to reinstall Wine, by deleting it the shortcuts won't come back. You might just want to uncheck them from the menu editor.

---

### Post by rcayea on 2009-05-09
I second what cogadh said. I deleted wine from apps menu and I had a heck of a time figuring out how to replace it back to apps menu when I wanted to later on. In case you run into that problem here is the solution:


If you deleted wine from your Applications menu then look in home folder -> .config/menus/applications.menu (.config is a hidden folder, when in home folder go Ctrl+h if not visible

You should see an entry like this (i added the red
Code:

</Menu>
	<Menu>
		<Name>wine-wine</Name>
		[COLOR="Red"]<Deleted/>[/COLOR]
	</Menu>
</Menu>

Remove what's in red, and save

---

### Post by skygazer on 2009-05-09
> **cogadh said:**
> Open the menu editor and manually delete it (it is found in the Preferences menu). You should note that if you ever have a need to reinstall Wine, by deleting it the shortcuts won't come back. You might just want to uncheck them from the menu editor.

thanks for your help... it worked.. i never new you could configure the main menu like that..

---

### Post by rumel1988 on 2009-05-09
> **skygazer said:**
> I installed and then uninstalled wine on my ubuntu 8.04 LTS. But the installation directory still appears in the Applications menu. I tried uninstalling it but it doesnt go away.
How should i get rid of it?.. Pls help
go to synaptic package manager and uninstall wine. :)
[[IMG]http://img219.imageshack.us/img219/2333/screenshotsynapticpacka.th.png[/IMG]](http://img219.imageshack.us/my.php?image=screenshotsynapticpacka.png)

---

### Post by 2Stoned on 2010-04-06
Solved!

---

### Post by anamtamrin on 2010-05-28
> **rcayea said:**
>  If you deleted wine from your Applications menu then look in home folder -> .config/menus/applications.menu (.config is a hidden folder, when in home folder go Ctrl+h if not visible

You should see an entry like this (i added the red
Code:

</Menu>
	<Menu>
		<Name>wine-wine</Name>
		[COLOR="Red"]<Deleted/>[/COLOR]
	</Menu>
</Menu>

Remove what's in red, and save

It does useful when u need to reinstall wine. Thanx!

---

