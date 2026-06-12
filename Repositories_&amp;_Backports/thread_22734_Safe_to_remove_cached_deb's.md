---
title: "Safe to remove cached deb's?"
date: 2005-03-29
forum: Repositories &amp; Backports
---

### Post by UbuWu on 2005-03-29
Is it safe to remove the files from /var/cache/apt/archives/ ? Currently there is already 600mb of files there... Or do I need them for upgrading or uninstalling or something else?

---

### Post by Glanz on 2005-03-29
[QUOTE=UbuWu]Is it safe to remove the files from /var/cache/apt/archives/ ? Currently there is already 600mb of files there... Or do I need them for upgrading or uninstalling or something else?[/QUOTE]

the command:
sudo apt-get clean
...will delete all those cached files, with the disadvantage that currently installed apps and utilities won't have a backup for quick reinstallations after the operation.

the command:
sudo apt-get autoclean
..., however will only delete those cached .deb files that are archaic and have been replaced by newer versions, leaving backup .debs for currently installed apps.
I like this option the best because I do not always have a fast connection when I need to reinstall something.

So I recommend autoclean first to see if that creates enough space on your system to relieve it. If you still want more space after that, do a "clean"...

---

### Post by UbuWu on 2005-03-29
Thanks.

I found it in the synaptic preferences as well, under files.

---

### Post by UbuWu on 2005-03-29
Some strange behaviour with synaptic though:

When I select only delete packages which are no longer available, and then hit the big delete button right under it, I expected it to delete the packages which are no longer available, but instead this button removes all packages...

---

### Post by Glanz on 2005-03-29
[QUOTE=UbuWu]Thanks.

I found it in the synaptic preferences as well, under files.[/QUOTE]
 It is better to close Synaptic and do that from a terminal with the commands I listed. Then when you DO open Synaptic, you will note that Synaptic adjusted itself accordingly...

---

### Post by UbuWu on 2005-03-29
hmm... after the previous experience I assumed it would be fine to mark the delete packages which are no longer needed and then synaptic would do this automatically, or am I wrong?

---

### Post by Glanz on 2005-03-29
[QUOTE=UbuWu]hmm... after the previous experience I assumed it would be fine to mark the delete packages which are no longer needed and then synaptic would do this automatically, or am I wrong?[/QUOTE]
 If you do an autoclean via a terminal, there is no need to readjust synaptic afterwards because synaptic is APT-dependant and will have already taken your work on the command line "into consideration." The reason I referred you to "apt-get autoclean" was to save time.

Whereas it is true that one may do most (but not all) of the same things as one may do via APT in a terminal, the fact remains that I do not know how your Synaptic is configured, whether it is correct or not. So to avoid errors, the "apt-get autoclean" is the best bet.

One more thing: you should do an "apt-get update" and then upgrade the packages you wish to upgrade before the autoclean. ALSO NOTE: that if you do an "apt-get update" via a terminal or a "reload" via synaptic then do an "autoclean", APT will remove the archives for the already instaled .debs which may be upgraded even if you didn't actually perform the upgrades for those apps. No harm done anyway.

---

