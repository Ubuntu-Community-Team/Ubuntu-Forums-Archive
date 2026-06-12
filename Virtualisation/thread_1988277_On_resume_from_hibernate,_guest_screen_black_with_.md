---
title: "On resume from hibernate, guest screen black with 100% CPU"
date: 2012-05-27
forum: Virtualisation
---

### Post by Paddy Landau on 2012-05-27
I am running Ubuntu 12.04 (fully updated) as a guest, using the up-to-date version of Virtual Box, with Guest Additions installed.

The host is also Ubuntu 12.04 (fully updated).

If I hibernate the guest (not the host), on resuming the guest three things happen:

[LIST=1]
[*]The guest screen shows the usual purple while resuming, but having resumed the screen is black.
[*]System Monitor on the host shows 100% CPU in use (actually, 200%, as I have allocated two CPU cores to the machine).
[*]The machine does, however, work. For example, if I left the terminal open on hibernation, it is still open on resume, the mouse changes when I hover over the terminal, and I can enter (say) *sudo shutdown now* and have the system shut down.
[/LIST]
This is strange, and I'd love to have it fixed. Are you able to help, please.

---

