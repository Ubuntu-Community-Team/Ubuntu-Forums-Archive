---
title: "some comments upgrading to ubuntu jammy development thus far"
date: 2022-02-16
forum: Ubuntu Development Version
---

### Post by Claus7 on 2022-02-16
Hello,

here are some observations upgrading to ubuntu 22.04 development so far from 20.04:

1) I was getting the message "VBoxClient: The virtualbox kernel service is not running..." as here: 
[https://stackoverflow.com/questions/62724599/ubuntu-20-04-lts-host-vboxclient-the-virtualbox-kernel-service-is-not-running](https://stackoverflow.com/questions/62724599/ubuntu-20-04-lts-host-vboxclient-the-virtualbox-kernel-service-is-not-running)

and by following the guidelines there, I went to /opt and found a VBoxGuestAdditions-5.2.42 folder and inside it the file uninstall.sh
I did sudo ./uninstall.sh
and message disappeared.

It also decreased the boot time.

2) I was getting the following error message when trying to install virtualbox guest additions: (3) ERROR: xxx - Failed to calculate strong name from 'C:\Program Files\Oracle\VirtualBox Guest Additions\VBoxGuest.cat'. Check if catalog is valid and if file is in the same directory as the INF.

In order to remove this error I did not install the guest additions 6.1.32.1 package available, yet I went here:
[http://download.virtualbox.org/virtualbox/6.1.26/](http://download.virtualbox.org/virtualbox/6.1.26/)

and downloaded the package:
VBoxGuestAdditions_6.1.26.iso

since I saw that other users were having problems with greater versions that this one as well. I opened vb, started the virtual machine, went on top to Devices->Optical Drives and unchecked everything that was checked. I rebooted the virtual machine and went to Devices->Optical Drives->Choose a disk file... and searched for the aforementioned iso file. Installation went fine.

This action also decreased the boot time. 

3) Boot time has increased almost to double digits than before.

4) From system monitor the total size of memory reported is slightly higher that what it used to. I noticed the same thing under ubuntu 21.10 as well.

5) On desktop (actual desktop) appeared files, which were having in their names the tilde ~ symbol, as regular ones. I 'm thinking if this might be a hdd problem.

6) Memory consumption in flashback seems to be slightly lower.

7) DesktopiconsNG extension supports once again copy paste functionality under ubuntu session. 

Hope it helps in case someone faces the same issues.

edit:
8) on top panel of flashback, only during boot, sometimes the word System near Places shows up just for a little while

9) Num light is never turned on during any boot.

10) During boot I see the following message:
platform gpio_ich.2.auto: failed to claim resource 0: [io  0x0480-0x04ff]

Regards!

---

### Post by Claus7 on 2022-03-11
Hello,

> **Claus7 said:**
> 
.....

3) Boot time has increased almost to double digits than before.
Lightdm, as name suggests, reports lower times compared to gdm3.

> **Claus7 said:**
> 
4) From system monitor the total size of memory reported is slightly higher that what it used to. I noticed the same thing under ubuntu 21.10 as well.
Still, even after the final updates to system monitor it remains the same. The "About" information concerning memory is as it used to.
 
> **Claus7 said:**
> 
5) On desktop (actual desktop) appeared files, which were having in their names the tilde ~ symbol, as regular ones. I 'm thinking if this might be a hdd problem.
It seems that this has ceased.

> **Claus7 said:**
> 
8) on top panel of flashback, only during boot, sometimes the word System near Places shows up just for a little while
It persisted for some time. I have not noticed anything lately.

> **Claus7 said:**
> 
9) Num light is never turned on during any boot.
This, unfortunately, happens only when logging to flashback. Also switching from ubuntu (wayland or xorg) to flashback, Num light turns off.
edit: seems to be a known issue: [https://bugs.launchpad.net/ubuntu/+source/gnome-flashback/+bug/1881486](https://bugs.launchpad.net/ubuntu/+source/gnome-flashback/+bug/1881486)
edit2: installing numlockx, and adding it as startup using the command numlockx on, turns numlock on

> **Claus7 said:**
> 
10) During boot I see the following message:
platform gpio_ich.2.auto: failed to claim resource 0: [io  0x0480-0x04ff]

This message is still there, yet by searching the net I think that it might be harmless.

Regards!

---

### Post by Claus7 on 2022-04-24
Hello,

I would like to add a couple more observations, even if jammy is now released, since they are still working in the released 22.04 lts version, in case someone finds them useful:

1) recent items extension is a very nice one. Even if flashback has recent items ages ago, this extension provides the ability, using right click, to send you directly to the folder the recent item file exists. Flashback has the ability to show the path the file belongs to, yet it is not possible to go there directly. Yet, via nautilus (a.k.a. Files) this can happen though. 

Even if this extension was (is) not ready for regular ubuntu, just adding version 42 in the metadata.json file like this:
>   "shell-version": [
    "3.36",
    "40",
    "41",
    "42"
  ],
will do the work.

2) Show desktop: in flashback that icon is found on the left hand side of the bottom panel. There are extensions that can enable show-desktop in gnome shell, yet only in top panel, as I'm aware of. Check this "extension", which can be added with the rest of extensions and show desktop on the same spot. 
i) in wayland, some times, show-desktop was underneath the bottom panel, so it is not advisable to use it with wayland, unless you enable and disable it in order to bring it forth (in case it happens to xorg, the same solution applies)
ii) the way it is written, it should show up on the left hand side of your screen. If you have different resolution than mine, you have to tamper with the button.set_position(1, 993) 993 value and choose a value slightly smaller than that of your vertical resolution value
iii) it can be combined with the extension Frippery Bottom Panel by adjusting the 40px value of the stylesheet.css file:
> .window-list-box {
    padding: 1px 40px; /*leave space for show desktop button*/
    spacing: 6px; 
}
which places the application launchers slightly to the right in order to leave space for the show-desktop icon
iv) it is comprised of the following two files:
extension.js
```
const { Atk, Clutter, Gio, GLib, GObject, Meta, Pango, Shell, St } = imports.gi;
const Signals = imports.signals;

const CheckBox = imports.ui.checkBox;
const Layout = imports.ui.layout;
const Main = imports.ui.main;
const ModalDialog = imports.ui.modalDialog;
const PopupMenu = imports.ui.popupMenu;
const WindowManager = imports.ui.windowManager;
const WorkspaceSwitcherPopup = imports.ui.workspaceSwitcherPopup;

let button;

function _showdesktop () {
let stuff = GLib.spawn_command_line_sync("/usr/local/bin/show-desktop");
}

function init() {
    button = new St.Bin({ style_class: 'panel-button',
                          reactive: true,
                          can_focus: true,
                          track_hover: true,
                          height: 30,
                          width: 30 }); /*size of icon*/
                          
    button.set_position(1, 993); /*distance of icon left, top of the screen (close to screen resolution)*/
                          
    let icon = new St.Icon ({ icon_name: 'desktop',
                      style_class: 'system-status-icon' });
    button.set_child(icon);
    button.connect('button-press-event', _showdesktop);
}

function enable() {
        Main.layoutManager.addChrome(button, {
    affectsInputRegion : true,
    trackFullscreen : true,
  }); /*avoid seeing the button when in full screen*/
}

function disable() {
        Main.layoutManager.removeChrome(button);
}
```

and metadata.json taken from another extension and modified in order to fit
```
{
  "_generated": "Generated by SweetTooth, do not edit",
  "debug": false,
  "description": "Minimize/unminimize all open windows with a single click.",
  "extension-id": "show-desktop-button",
  "gettext-domain": "show-desktop-button",
  "localedir": "/usr/share/locale",
  "name": "Show Desktop Button",
  "settings-schema": "org.gnome.shell.extensions.show-desktop-button",
  "shell-version": [
    "40",
    "41",
    "42"
  ],
  "url": "..",
  "uuid": "show_desktop@mine",
  "version": 1
}
```
v) edit: create a show-desktop executable under /usr/local/bin/ with the following content:
> #!/bin/sh
#Record Open Windows and Minimize Them
 open_windows=$(wmctrl -l | cut -f1 -d " ")

 if wmctrl -m | grep -e "mode: OFF" -e "mode: N/A" ; then
  wmctrl -k on 
 fi
#Restore Minimized Windows (in the order in which they were opened - newest on top)*
 if wmctrl -m | grep "mode: ON" ; then
  #for i in $open_windows
   #do 
    #wmctrl -i -R "$i"
    wmctrl -k off
   #done
 fi
vi) use it in a folder named show_desktop@mine
vii) I'm not maintaining extensions. I just add it here in case someone finds it useful.

3) I have observed that Libreoffice is faster in flashback rather than regular ubuntu.

4) Many applications from now on seems that will be gtk4 ones. gtk4 apps use either light or dark theme, so will have either white or black headerbar. In order for someone to find out which gtk version an app is using then go to synaptic package manager, select the desired app, choose properties and then Dependencies and see the gtk version value. A gtk.css file of gtk4 apps can be found under /usr/share/themes. Opening a gtk4 app either in flashback or regular ubuntu it does not respect the legacy theme being responsible for gtk3 apps, so their theme is different from that of their gtk3 counterparts. Trying to solve this just from the /usr/share/themes was not possible. The steps taken in order to change the headerbar (and other things if someone wishes) of the gtk4 apps, so as to match with the rest of the system are (as an example the Yaru-blue theme will be used):

i) go to /usr/share/themes/Yaru-blue/gtk-4.0
ii) check the files included in the binary file gtk.gresource by issuing the command:
gresource list gtk.gresource
iii) extract the gtk.css file from .gresource file
   gresource file is located to a specific path: /usr/share/themes/Yaru-blue/gtk-4.0
   the files inside gresource file have another path: /com/ubuntu/themes/Yaru-blue/4.0/
   and can be extracted to ~/Desktop/somefile.css

   so in order to extract from gtk.gresource the listed file gtk.css, which is a file inside gtk.gresource, and   
   which has the path /com/ubuntu/themes/Yaru-blue/4.0/gtk.css
   the command should be (use similar command for the dark variant): 
```
gresource extract /usr/share/themes/Yaru-blue/gtk-4.0/gtk.gresource /com/ubuntu/themes/Yaru-blue/4.0/gtk.css > ~/Desktop/somefile.css
```

iv) now rename somefile.css as gtk.css (I changed the name in order to avoid confusion), make the desired changes and add it to ~/.config/gtk-4.0 for changes to take effect immediately

Regards!

---

