---
title: "How to uninstall the webapps?"
date: 2012-09-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by victor9098 on 2012-09-29
I saw the webapps are now available via synaptic (unity-webapps-*) and gave them a try. Now I have uninstalled them but I can still see the webapps in the applications scope and in the messaging menu. Clicking them just opens a new chrome window (chrome is my default browser) but all the webapp functionality is gone.

So how do I remove the icons? :confused:

EDIT: Adding more info.

Just ran "ls /usr/share/indicators/messages/applications" to see what is listed in the messaging menu and I get;

empathy  gwibber.indicator  thunderbird  ubuntuone-control-panel

But I can still see the extra, leftover, webapps too (facebook, gmail...)

---

### Post by cariboo on 2012-09-29
Do your usual daily backup, and make sure you can access your fallback installation, then remove empathy, gwibber, thunderbird, and ubuntu one, to see what happens.

---

### Post by victor9098 on 2012-09-29
> **cariboo907 said:**
> Do your usual daily backup, and make sure you can access your fallback installation, then remove empathy, gwibber, thunderbird, and ubuntu one, to see what happens.

Good idea, but no sale. Everything else was removed except for the two webapp's. I am thinking this might need to be filed as a bug. Also the app icons in the application scope still have not gone anywhere.

---

### Post by cariboo on 2012-09-29
Right-click the icon, and select Unlock from Launcher?

You could also open up synaptic, and search for webapps, and remove them from their.

---

### Post by mc4man on 2012-09-29
If you gave them a try & still seeing in the apps lens then take a look in 
~/.local/share/applications 
for some .desktop files for those webapps. If there delete

---

### Post by victor9098 on 2012-09-29
> **cariboo907 said:**
> Right-click the icon, and select Unlock from Launcher?

You could also open up synaptic, and search for webapps, and remove them from their.

They are not in the launcher, they are appearing in the message indicator (right clicking just opens a browser window). Then when I open the dash and search in the applications scope all of them I installed (not just the two in the message indicator) are mixed in with everything else.

---

### Post by victor9098 on 2012-09-29
> **mc4man said:**
> If you gave them a try & still seeing in the apps lens then take a look in 
~/.local/share/applications 
for some .desktop files for those webapps. If there delete

Away from that computer right now, will try this and update as soon as I can.

::UPDATE::

Deleting the .desktop files did the trick and removed the icons from the message indicator on the panel.

BUT

The webapps are still littered across applications in the applications scope. Where could I find where those are hiding?

---

### Post by Mr. Picklesworth on 2012-09-29
The Amazon and Ubuntu One webapp shortcuts belong to the package unity-webapps-common. They live in /usr/share/applications:
/usr/share/applications/ubuntu-amazon-default.desktop
/usr/share/applications/UbuntuOneMusiconeubuntucom.desktop

This is the only webapp-related package I have noticed to put anything in /usr/share/applications. Annoyingly, all of the webapp packages have a hard dependency on that one, so there are two ways to get rid of those shortcuts:
Remove unity-webapps-common and don't use the webapps feature.
Edit the offending .desktop files and add NoDisplay=True. (Either add replacements in ~/.local/share/applications or edit the original ones as root).

---

### Post by mc4man on 2012-09-29
> **victor9098 said:**
> 

::UPDATE::

Deleting the .desktop files did the trick and removed the icons from the message indicator on the panel.

BUT

The webapps are still littered across applications in the applications scope. Where could I find where those are hiding?

Other than the 2 default ones, (amazon, ubuntuone music), if a web app installs a .desktop i'd think it would only be locally.

If you are seeing icons still in the apps lens are they in the "Recently Used" or the "Installed'
If in Recent just open a few more apps & they'll be gone for good..

If in Installed then post the display names

---

### Post by victor9098 on 2012-09-29
It looks like deleting all the .desktop entries may have done it. I rebooted the computer after doing that and while the notification ones were gone the applications ones were still there, but logging back in now and I can not see them. So problem solved!

The offending apps were; Twittertwittercom.desktop, Lastfmwwwlastfm.desktop, Googleplusgooglecom.desktop, GMailmailgooglecom.desktop, facebookfacebookcom.desktop,  facebookfacebookcom.desktop

Not a typo, there were two instances of the facebook one. Has anyone else tried installing/uninstalling these? Will everyone have to do this?

Thanks for all the help solving this one.

---

### Post by mc4man on 2012-09-29
> **victor9098 said:**
> Will everyone have to do this?

Thanks for all the help solving this one.
I'd say so  - 
when you install the unity-web whatever package(s) all that is installed are some files that enable the web-app if you then chose to.
At that point, (you as a user choosing to install/enable), these .desktops are written locally.
Uninstalling the package can't & won't remove the local .desktops

---

