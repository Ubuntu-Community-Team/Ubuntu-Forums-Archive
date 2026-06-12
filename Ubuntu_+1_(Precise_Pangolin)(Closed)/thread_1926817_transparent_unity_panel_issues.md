---
title: "transparent unity panel issues"
date: 2012-02-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mc4man on 2012-02-16
If wanting to use transparency in the unity panel it was only an issue if the opacity was set to 0.000 Then any global menu would show in black when focus wasn't on the panel.
Setting to any value above 0.000 would fix that

Now additionally there is this strangeness - 
If a window from either of the top 2 ws's in a 2x2 drifts or is moved into the WS below & you happen to switch to that WS then that window permanetly becomes part of the panel unless it's replaced by another window impinging in another part of the panel

This effect will last till a log out/in or setting the panel trans back to 1.000

bug on the orig. issue + some additional w/ vid
[https://bugs.launchpad.net/unity/+bug/924592](https://bugs.launchpad.net/unity/+bug/924592)

Edit: what's interesting is you can use a synaptic window to 'clean' out the panel by lowering to a WS & switching WS's

The latest compiz which reverts fix_925293.patch: has fixed this for the moment

---

### Post by mc4man on 2012-02-17
There is a new minor issue with panel trans, though it also 'could'? be considered desirable

With the current default plugins in 5.4, as the panel opacity is lowered so is the launcher quicklist opacity.
So at the lower opacities the quicklist becomes almost transparent. (the lowest current advised is 0.0100
 Where this is an issue is if one opens the quicklist over a light colored window, becomes hard to read.

It appears here that the png plugin causes this, intended or not I've no idea

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/934543](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/934543)

---

