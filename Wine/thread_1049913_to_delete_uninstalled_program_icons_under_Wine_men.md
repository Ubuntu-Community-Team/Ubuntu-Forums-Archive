---
title: "to delete uninstalled program icons under Wine menu"
date: 2009-01-25
forum: Wine
---

### Post by wstay on 2009-01-25
Is there a way to delete uninstalled program icons under the Applications/Wine menu from the task bar?

---

### Post by Meow27 on 2009-01-25
open up the terminal and type

'alacarte' (without the quotes)

have fun :3

---

### Post by wstay on 2009-01-26
> **Meow27 said:**
> open up the terminal and type

'alacarte' (without the quotes)

have fun :3

Thanks.

---

### Post by wstay on 2009-01-28
> **Meow27 said:**
> open up the terminal and type

'alacarte' (without the quotes)

have fun :3

I have another related question.
We bring up the Main Menu with alacarte and ok we can delete the program icon under /wine/program/.
What about the program icon under /wine/.
I can not delete the program icon I have uninstalled under /wine/.
I can only uncheck the program icon.
Is there a way to delete this uninstalled and unwanted progarm icon?

---

### Post by cogadh on 2009-01-28
If you are talking about getting rid of the actual XPM or PNG file used for the icon, just find where it is located in your home directory and delete it. Alacarte should also be able to help you find where it is stored.

---

### Post by wstay on 2009-01-28
> **cogadh said:**
> If you are talking about getting rid of the actual XPM or PNG file used for the icon, just find where it is located in your home directory and delete it. Alacarte should also be able to help you find where it is stored.

I use alacarte to locate the icon - env WINEPREFIX="/home/wstay/.wine" wine "C:\Program Files\ICQ\ICQ.exe" and the whole folder ICQ is already not there. So where can it be that we can delete the uninstalled icon.

---

### Post by cogadh on 2009-01-28
I'm not sure I'm understanding the issue. You should just be able to right-click on a shortcut and select "delete" to get rid of the shortcut. You can only do that in the right-hand pane of Alacarte, so you need to be on the correct "level" of the menu in the left-hand pane in order to do that.

---

### Post by x33a on 2009-01-29
i have been facing exactly the same issue as wstay. i couldn't right click and delete wine related shortcuts, even after uninstalling the programs related to them.

what i did was, manually edit applications.menu under /home/x33a/.config/menus

and delete all those programs related info from .wine under home directory.

---

### Post by wstay on 2009-01-29
> **cogadh said:**
> I'm not sure I'm understanding the issue. You should just be able to right-click on a shortcut and select "delete" to get rid of the shortcut. You can only do that in the right-hand pane of Alacarte, so you need to be on the correct "level" of the menu in the left-hand pane in order to do that.

Alacarte opens a Main Menu.
On the Main Menu when I click Wine on the left (call this 1st level) and the uninstalled ICQ icon appeared on this level on the right with a check box which when I click on it and click delete, it cannot be deleted.
On the second level, that is after clicking Wine and click Programs on the left, everything that appear on the right can be deleted.
So everything on the first level on the right cannot be deleted including uninstalled icons which happen to appear there. The only thing I can do is to uncheck the check box.

---

### Post by Meow27 on 2009-01-29
are you using ubuntu 8.04 or 8.10?

(the 8.10 version allows deleting)

you can go on package search and download the intrepid version, but since its for intrepid its not guaranteed to work (as in, use at your own risk)

---

### Post by cogadh on 2009-01-29
> **wstay said:**
> Alacarte opens a Main Menu.
On the Main Menu when I click Wine on the left (call this 1st level) and the uninstalled ICQ icon appeared on this level on the right with a check box which when I click on it and click delete, it cannot be deleted.
On the second level, that is after clicking Wine and click Programs on the left, everything that appear on the right can be deleted.
So everything on the first level on the right cannot be deleted including uninstalled icons which happen to appear there. The only thing I can do is to uncheck the check box.
You can still go up one more level on the left pane, since the Wine menu is actually part of the larger "Applications" menu. Just click on "Applications" in the left pane, then do your deleting work in the right pane.

---

### Post by nanog on 2009-01-30
I'm running intrepid on multiple upgraded systems and can confirm that legacy wine icons in the "wine" menu item cannot be removed in alacarte. 

I had to manually edit:

```
~/.config/menus/applications-merged
```

and when this did not work and i had to find the xml entry in:

```
~/.config/menus/applications.menu
``` 

and manually delete it.


A fresh install of "wine repo" wine in intrepid allows alacarte editing.

---

### Post by wstay on 2009-01-30
> **Meow27 said:**
> are you using ubuntu 8.04 or 8.10?

(the 8.10 version allows deleting)

you can go on package search and download the intrepid version, but since its for intrepid its not guaranteed to work (as in, use at your own risk)

I know I am using ubuntu 8.10.
To be sure, how can I check this on the terminal or where can I see my version of Ubuntu.

---

### Post by wstay on 2009-01-30
> **nanog said:**
> I'm running intrepid on multiple upgraded systems and can confirm that legacy wine icons in the "wine" menu item cannot be removed in alacarte. 

I had to manually edit:

```
~/.config/menus/applications-merged
```

and when this did not work and i had to find the xml entry in:

```
~/.config/menus/applications.menu
``` 

and manually delete it.


A fresh install of "wine repo" wine in intrepid allows alacarte editing.


I got the following from /.config/menus/applications.menu:

<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>wine-wine</Name>
		<Menu>
			<Name>wine-Programs</Name>
			<Menu>
				<Name>wine-Programs-ICQ</Name>
				<Deleted/>
			</Menu>
			<Menu>
				<Name>wine-Programs-ICQ 5.1</Name>
				<Deleted/>
			</Menu>
			<Menu>
				<Name>wine-Programs-Yahoo! Messenger</Name>
				<Deleted/>
			</Menu>
			<Menu>
				<Name>wine-Programs-Ares</Name>
				<Deleted/>
			</Menu>
			<Menu>
				<Name>wine-Programs-Ares Lite Edition</Name>
				<Deleted/>
			</Menu>
		</Menu>
		<AppDir>/home/wstay/.local/share/applications</AppDir>
		<Include>
			<Filename>wine-ICQ.desktop</Filename>
		</Include>
		<Include>
			<Filename>wine-ICQ 5.1.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Other</Name>
		<Include>
			<Filename>wine.desktop</Filename>
		</Include>
		<AppDir>/home/wstay/.local/share/applications</AppDir>
		<Include>
			<Filename>winefish-project.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Multimedia</Name>
		<Include>
			<Filename>totem-gstreamer.desktop</Filename>
		</Include>
		<AppDir>/home/wstay/.local/share/applications</AppDir>
		<Include>
			<Filename>gnome-volume-control.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>System</Name>
		<Include>
			<Filename>gconf-editor.desktop</Filename>
		</Include>
		<AppDir>/home/wstay/.local/share/applications</AppDir>
	</Menu>
</Menu>

I do not know how to edit it to get rid of the uninstalled ICQ icons.
Could you please show me how?

And also do you mean I have to uninstall wine and do a fresh re-install of wine using Synaptic Package Manager in Intrepid to allow alacarte editing.

---

