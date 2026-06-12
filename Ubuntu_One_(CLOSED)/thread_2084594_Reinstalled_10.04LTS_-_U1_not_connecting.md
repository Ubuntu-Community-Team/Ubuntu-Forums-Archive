---
title: "Reinstalled 10.04LTS - U1 not connecting"
date: 2012-11-15
forum: Ubuntu One (CLOSED)
---

### Post by s1mple_M4N on 2012-11-15
Hi all.

Had issues yesterday with 12.04LTS upgrade on my elderly pc, so did fresh re-install of 10.04LTS and have been going through the process of getting all my programmes back together.
A problem I have run into is with U1 not able to connect, although it has been working fine on my previous installation for the better part of a year or so.
The error I am getting is: [Errno socket error] SSL hostname validation failed.
I'm unsure if we are connecting through proxy, but recently updated our modem/router. Although that didn't affect U1 then.
I have no U1 password key to delete and have followed instructions in this U1 post >> [https://one.ubuntu.com/help/faq/how-do-i-add-my-computer/](https://one.ubuntu.com/help/faq/how-do-i-add-my-computer/) to no avail. I'm unsure where to go next, or might it be a matter of waiting until I've installed the right application to get my pc back to where it was...
Hopefully someone out there can point me in the right direction.

Many thanks,

RoyJ

---

### Post by dask2 on 2012-11-20
Hi RoyJ,

try this:
If you have a backup of your folder /home/user/.gnome2/keyring/ so copy login.keyring back.

or try this:

[LIST]
[*]Open System->Preferences->Passwords and Encryption Keys* and create the key new...
[*]strg+n
[*]saved password
[*]description: UbuntuOne token for [https://ubuntuone.com](https://ubuntuone.com)
[*]oauth-consumer-key: ubuntuone
ubuntuone-realm: [https://ubuntuone.com](https://ubuntuone.com)
[/LIST]
after that, restart the ubuntuone-client and wait until saying: " synching..."


Good luck,
dask2

---

