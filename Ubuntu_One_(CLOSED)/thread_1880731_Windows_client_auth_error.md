---
title: "Windows client auth error"
date: 2011-11-14
forum: Ubuntu One (CLOSED)
---

### Post by Rincewind on 2011-11-14
Hi,

On my work PC I used to use the new Ubuntu One Windows client fine, but at some point decided to uninstall it and remove the computer from the list of authorised machines via my account page.

I now want to use it from this computer again, but after reinstalling the client, it doesn't prompt for my credentials - it seems to have just stored these somewhere.  The problem is that the machine isn't authorised, and doesn't prompt to be authorised so I get a 'auth error' and it won't work.

I've tried deleting any of the hidden folders in Application Data etc. and searching and removing registry keys to try to wipe out the credentials that are stored, but nothing works.  Any ideas?

---

### Post by Rincewind on 2011-11-14
Sorry, solved myself - there's a registry entry to delete which holds the credentials:
HKEY_CURRENT_USER/Software/Ubuntu One/Keyring/ubuntu_sso

Deleted that and it now prompts for credentials on installation.

---

