---
title: "Apparmor not restricting access to the home folder?"
date: 2012-06-16
forum: Security
---

### Post by xeemo on 2012-06-16
In the apparmor profile for firefox it mentions that firefox can download to the Downloads directoroy and upload from the Public directory.  I've enforced the profile, and I've confirmed it is running in enforce mode as it's restricting write access to certain folders (not to mention apparmor_status clearly says it's running in enforce mode).

Oddly enough I was not only able to download things to my home folder when I maybe shouldn't be able to, but I was also able to install add-ons when the profile seems to deny write access to the add-ons directory.  Or at the very least that seems to be my interpretation of these lines:

[PHP]
# Default profile allows downloads to ~/Downloads and uploads from ~/Public
  owner @{HOME}/ r,
  owner @{HOME}/Public/ r,
  owner @{HOME}/Public/* r,
  owner @{HOME}/Downloads/ r,
  owner @{HOME}/Downloads/* rw,[/PHP]


[PHP]  # noisy
  deny @{MOZ_LIBDIR}/** w,
  deny /usr/lib/firefox-addons/** w,
  deny /usr/lib/xulrunner-addons/** w,
  deny /usr/lib/xulrunner-*/components/*.tmp w,
[/PHP]

Why is it exactly that those deny lines are in the profile under noisy?  Are they actually doing anything?  Just wondering.

I'm also a bit confused as to what this Downloads folder and Public folder buisiness is.  I haven't tried to upload anything yet, but there's a line that grants read access to everything by default, so I'm not quite sure why there's extra emphasis on the public folder.

Is this supposed to just be a template of sorts to build a profile from?  Either way I'm glad to see default apparmor profiles in Ubuntu and would love to see more eventually.

Edit:  I'm also wondering how I would go about securing flash.  I've disabled direct access to my home folder for firefox, but flash still seems to have access.  When you view a flash video for the first time a .macromedia folder is made in your home folder.  I've deleting this folder, and it comes back every time I watch a flash video, leading me to believe flash is compeltely uncontained.

It's not that I don't want that folder in my home directory, it's that I don't want flash to be able to make such a folder without permission. 

Is there something I could point aa-genprof at to make a profile for plugin-container or the flashplugin?  What I've tried hasn't detected anything.

---

### Post by Alex1357 on 2012-08-08
By default, the AppArmor profile for Firefox contains the line 
[PHP]
#include <abstractions/ubuntu-browsers.d/firefox>
[/PHP]which itself contains the line
[PHP]
#include <abstractions/ubuntu-browsers.d/user-files>
[/PHP]which has among others the permissions
[PHP]
@{HOME}/ r,
@{HOME}/ ** r,
owner @{HOME}/ ** w
[/PHP](Remove the spaces between / and *)
So firefox seems indeed to be allowed to do anything in the user's home directory.

---

