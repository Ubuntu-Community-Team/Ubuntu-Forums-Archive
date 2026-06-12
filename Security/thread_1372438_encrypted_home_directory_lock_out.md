---
title: "encrypted home directory lock out"
date: 2010-01-04
forum: Security
---

### Post by curioshop on 2010-01-04
I am locked out of my home directory after 1) activating root account, 2) removing admin privileges from my account.  I think it happened then.  I have since added admin privs back to my account (from root) and i changed password on my account before i was locked out, then changed it back but i don't know if changing it back was before or after lock out.

Error after putting my password into GDM: "Could not update ICEauthority file /home/me/.ICEauthority" then "There is a problem with the configuration server: (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)" then "[BOLD] Nautilus could not create the following reuired folders: /home/me/Desktop. /home/me/.nautilus. [not bold] Before running Nautilus, please create these folders, or set permissionssuch that Nautilus can create them." then "Update Information   Record Your encryption passphrase... and more" it doesn't take my sign on password, and I no longer have the encryption password.  This is not the behavior I expected.  the desktop will not come up.  An unencrypted /home/me has been created on my first log in attempt containing only: "Access Your Private Data" and README.txt when I run the command in README it tells me the directory is not set up properly.

Going over to CENTOS since that is what everyone at work already uses, though I will have an ubuntu desktop in the future, so there will be no further reports on this.

---

