---
title: "Media Keys on Dell Studio don't work in Ubuntu Studio 14.04"
date: 2016-02-17
forum: Ubuntu Studio
---

### Post by lsnd on 2016-02-17
Hi I just moved to Ubuntu Studio from Linux Mint and it's really cool distro.
I've encounter a problem with my Dell Studio media buttons. The volume controls are just fine but the media controllers are just not working. When pressed the light indicator shows that the button is active but nothing more.

Tried to change the keyboard model from the settings/keyboard/layout but the dell studio keyboard isn't supported just because (as the support.dell.com says) it is Microsoft Internet Keyboard,and when set to MIK the Keyboard Layout Chart shows some standard desktop layout. Though those buttons are on the touch panel just above the keyboard so they may be not in the actual layout.

Another thing I've found is installing dconf.editor to manually change values of the buttons but couldn't find [U]org.gnome.settings-daemon.plugins.media-keys.custom-keybinding.
[/U]
Buttons was fine in Linux Mint and as it is another Ubuntu based distro I assume it is some settings-related issue.
Not sure if it has something to do with KdeConnect install and the media controls assigned by KDE.

<UPDATE>After a distro update buttons partially functional- 'Fwrd' and 'Bwrd' react only when media window is opened in the active workspace, 'Play' and 'Stop' still not working and when change workspace or window everything is back to ... not working.
And when KdeConnect Indicator is active 'Fwrd' and 'Bwrd' not responding even in directly open window.

<UPDATE>After system update org.gnome.settings-daemon.plugins.media-keys is reachable though nothing wrong with the keys : XF86Audio***** value assigned for each function that is not working. So might be something else.

* I Posted the thread in other linux forum first so excuse me for the bit messy look but trying to give as much details  as possible.*

---

