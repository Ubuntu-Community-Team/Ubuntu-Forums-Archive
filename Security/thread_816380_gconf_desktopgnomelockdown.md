---
title: "gconf: /desktop/gnome/lockdown"
date: 2008-06-02
forum: Security
---

### Post by centyx on 2008-06-02
Hi,

I am trying to very lightly ( at first ) lock down gnome for use by a guest user account.

Right now, I am focusing on the restrictions provided by the keys available in /desktop/gnome/lockdown. 

I created these keys myself, and though many are working ( ie. lockdown_desktop_icons, lockdown_panel_config ), I am having trouble with the following keys:

restrict_locations ( boolean, true ) 
allowed_locations ( list, string )
allowed_applications ( list, string )

I have restrict_application_launching set as boolean to True, and this has removed the Run menu item, but the allowed_applications list is not having any effect on the menus nor on which applications I can launch.

Likewise, nautilus does not appear to honour restrict_locations or the allowed_locations list - other locations still show up and are browseable via the places menu. 

Attached is the user's ~/.gconf/desktop/gnome/lockdown/%gconf.xml

Could anyone point me in the right direction?

Thanks!

[ATTACH]72683[/ATTACH]

---

