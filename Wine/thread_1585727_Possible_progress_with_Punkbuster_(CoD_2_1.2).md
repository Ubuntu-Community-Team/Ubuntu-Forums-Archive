---
title: "Possible progress with Punkbuster (CoD 2 1.2)"
date: 2010-09-30
forum: Wine
---

### Post by Sompom on 2010-09-30
This is not to say the punkbuster is completely working, because it's not! My situation now is PB kicks every minute or so with No Packet Flow, still it's progress, right?
Please note that I have been using Play on Linux to sort all my files, I don't know it this will work with normal Wine or not.
What I did:
Firstly, update your CoD 2 Punkbuster. Using the Pbsetup.exe, download the PB files for CoD 1 to some other directory. Delete the file _pbcl.dll_ from your CoD 2 PB directory, and replace it with the same file from CoD 1 PB. When you start your game you also need to start PnkBstrA.exe in your windows/system32 directory. This should neatly bundle away the Unknown Windows API function errors, but I cannot figure out how to get past the next problem that arieses. After just over a minute of play it tells me No Packet Flow. That seems like it should be an easy one to fix, anyone have any ideas?
I have been testing with wine 1.2, and Windows 98 compatibility mode

---

### Post by Half-Left on 2010-10-01
Yeah, it's annoying people cannot play COD4 Modern Warfare MP because of PB. It works great until I get kicked out of the server. PB uses some rare API which Wine doesn't use and that's the issue.

---

### Post by Sompom on 2010-10-01
Further testing reveals that the file responsible for the Unknown Windows API functions is _pbcl.dll_, and that sticking in the CoD 1 pbcl.dll doesn't cause them. This is also the dll responsible for recording whether PB is enabled or not. I shall keep trying.

---

