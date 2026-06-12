---
title: "snap firefox appamor FAIL"
date: 2022-07-05
forum: Security
---

### Post by vbgf3 on 2022-07-05
Hi,

Something 'interesting' happened last night. I found /var/lib/snapd/apparmor/profiles/snap.firefox.firefox apparmor script. 
And I added to the end a deny @{HOME}/Documents/ rwl as wells as other private directories leaving only Downloads available to firefox.

Then I switched to an unprivileged account with no sudo rights. And went surfing for some Linux things using firefox.

When I ended the surfing session. I went back to my admin account which still have the snap.firefox.firefox script open, I was informed that the file has changed, would I want to reload it. And after the reload, I discovered that my changes were gone.

Now I had announced on another post that I was going to fiddle with apparmor stuff. But I said I was going to make one for Chrome, and didn't say anything about firefox. 

My question is: does firefox replace the appamor script by itself, or was it maliciously replaced by someone. 

If it was replaced by someone, this would be neat trick, as I thought that apparmor was supposedly able to stop even zero days and confine the attacker. How was he able to replace the apparmor profile? The apparmor script is owned by root.

 The machine is a fresh install, with avahi-daemon and cups, the 2 listening services, removed. It also has a firewall with inbound deny and only outgoing allowed for https, http, DNS, and NTP.

---

### Post by TheFu on 2022-07-08
A system that has been compromised cannot be trusted.  Wipe it and start over.  If other systems on the network are likely compromised too, perhaps a smart phone or a tablet, wipe those too and definitely check that your router has been patched within the last quarter and setup reminders to patch it monthly.  My router has updates every 2 weeks, even if just small php version changes.  If your router hasn't been patched in over a quarter, it is passed time to get a new one with better support provided.  

Fixing a compromised computer when the network is compromised is like trying to keep flies out of a horse barn while all the windows are open.

---

### Post by #&amp;thj^% on 2022-07-08
I'll always check in "** /etc/apparmor.d/abstractions**" for un-wanted changes, 
I understand if your not familiar with that directory all would look confusing, but I would check in "user-download" for any changes IE:
```
------------------------------------------------------------------
#
#    Copyright (C) 2002-2006 Novell/SUSE
#    Copyright (C) 2014 Canonical Ltd.
#
#    This program is free software; you can redistribute it and/or
#    modify it under the terms of version 2 of the GNU General Public
#    License published by the Free Software Foundation.
#
# ------------------------------------------------------------------

  abi <abi/3.0>,

# Description: Where common programs should allow users to download
# files

  owner @{HOME}/tmp/**       		rwl,
  owner @{HOME}/[dD]ownload{,s}/	r,
  owner @{HOME}/[dD]ownload{,s}/**	rwl,
  owner @{HOME}/[^.]*			rwl,
  owner @{HOME}/@{XDG_DESKTOP_DIR}/	r,
  owner @{HOME}/@{XDG_DESKTOP_DIR}/*	rwl,
  owner @{HOME}/@{XDG_DOWNLOAD_DIR}/	r,
  owner @{HOME}/@{XDG_DOWNLOAD_DIR}/*	rwl,
  owner "@{HOME}/My Downloads/" 	r,
  owner "@{HOME}/My Downloads/**" 	rwl,

  # Include additions to the abstraction
  include if exists <abstractions/user-download.d>
me@kaisenlinux /etc/apparmor.d/abstractions $ 


```
EDIT:  Apparmor is incredibly granular and requires copious application-system knowledge. :)
AppArmor can only track and protect processes that are started after the kernel module has been loaded. After the apparmor packages have been installed, apparmor will be started. But running processes won't be protected by AppArmor.

---

### Post by vbgf3 on 2022-07-12
I have come to think that the /var/lib/snapd/apprmor/profiles/snap.firefox.firefox apparmor file is refreshed by snap. 

So I think that the firefox apparmor file is designed not to be user modifiable.

That is regretable, because some changes are necessary in my view: 

>   # The ubuntu-core-launcher creates an app-specific private restricted /tmp
  # and will fail to launch the app if something goes wrong. As such, we can
  # simply allow full access to /tmp.
  /tmp/   r,
  /tmp/** mrwlkix,


I don't care what ubuntu core launcher can do to safeguard me, and my view is that tmp should not be writable, and linkable, while being executable. An attacker can write stuff and create links to sbin and run it. Write and executable do NOT go together.

And I don't want the browser to touch any of my Documents. I only want to save what I Download. Hence I added at the end of file:
>  deny @{HOME}/Documents/** rwl,
 deny @{HOME}/Videos/** rwl,
 deny @{HOME}/Music/** rwl,
 deny @{HOME}/Pictures/** rwl,
 deny @{HOME}/Templates/** rwl,
 deny @{HOME}/Public/** rwl,


And there are several other overly generous settings that I changed.

Can someone direct me to see what snap files were refreshed so I can verify this? Man snap-confine has a one liner that says apparmor profiles are Managed by snapd.

---

