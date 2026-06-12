---
title: "Dash focus problems (above/below other windows)"
date: 2011-10-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-17
As far as I can see we still have them now in PP, but CCSM "Window Rules" setting ABOVE to Class & Title of Launcher/Dash stopped functioning. It still is random: After some hours of work it happens, and you can only revert the behavior with unity --replace &

If anyone of you confirms, I think this is a important one. Impossible to use Dash if its under active window.

xprop shows it has _NET_WM_ALLOWED_ACTIONS(ATOM) = _NET_WM_ACTION_ABOVE, _NET_WM_ACTION_BELOW . I don't see the point of it ever being BELOW.

```

$ xprop
_NET_WM_ICON_GEOMETRY(CARDINAL) = 1, 985, 48, 48
_NET_WM_STRUT_PARTIAL(CARDINAL) = 50, 0, 0, 0, 24, 1079, 0, 0, 0, 0, 0, 0
XKLAVIER_STATE(INTEGER) = 0, 0
WM_STATE(WM_STATE):
        window state: Normal
        icon window: 0x0
_NET_WM_DESKTOP(CARDINAL) = 0
_NET_WM_ALLOWED_ACTIONS(ATOM) = _NET_WM_ACTION_ABOVE, _NET_WM_ACTION_BELOW
XdndAware(ATOM) = BITMAP
WM_NAME(STRING) = "launcher"
_NET_WM_WINDOW_TYPE(ATOM) = _NET_WM_WINDOW_TYPE_DOCK
_NET_WM_STATE(ATOM) = _NET_WM_STATE_STICKY, _NET_WM_STATE_SKIP_TASKBAR, _NET_WM_STATE_SKIP_PAGER

```

Regards,
Effenberg

---

### Post by Mr. Picklesworth on 2011-12-08
I had this happening constantly and I narrowed it down to having disabled Nautilus drawing my desktop. If I turned the Nautilus desktop back on, the dash would appear over all windows again.
Not a fix (it's obviously the dash being completely weird), but I'm interested if that's the source of the problem for you, too.

I covered that in comment #73 here:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/805087](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/805087)

That bug is marked as fixed, though, and nobody seems to be paying attention to it as a result. Anyone know if there is another, living bug report at this point?

---

### Post by mc4man on 2011-12-08
Well there is a 'catch all' for corner case stacking issues here (mentioned in your linked 'fixed' report
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/859405](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/859405)

I personally haven't had any stacking issues for quite some time, with or without nautilus handling the desktop though it seems hardware & or use case are possible factors.

---

### Post by ventrical on 2011-12-11
@effenberg


 Ok.. I noticed a big problem when I deactivated Blur from Unity Plugins. I clicked on ronaccs text file and as I moved it (the window) it got all milky and fuzzy (out of focus) ..Just reporting in that it may have somthing to do with your compiz bug.

---

