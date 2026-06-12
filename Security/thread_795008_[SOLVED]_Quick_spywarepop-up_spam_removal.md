---
title: "[SOLVED] Quick spyware/pop-up spam removal"
date: 2008-05-15
forum: Security
---

### Post by ubergam3r on 2008-05-15
hi, due to my uni friend donging around on my computer looking at "Trampoline porn" and such like. I now get repeated spam pop-ups and spy ware alerts. I think its just on the wine windows partion as wine has to create the pop-ups.

any quick removal tools for linux

---

### Post by calraith on 2008-05-15
Not really any one-size-fits-all solutions here, I don't think.  I'd heard that it's possible for wine to get infected by trojans and viruses, but never encountered any anecdotal evidence of such.

I'd say try running the following command:
```
wineboot -s -f -k
killall -9 wine
```to simulate a shutdown of windows in your wine bottle and kill any running wine processes.

Now.  Clamscan will detect some malware, so that might be worth a shot.
```
clamscan --infected --recursive --move=/tmp --max-space=16536 ~/.wine
```

Of course, the quickest way to get rid of whatever wee beastie would be simply to remove the ~/.wine directory, then use winecfg to recreate your bottle.  That would mean reinstalling whatever apps you run in wine, though.

---

### Post by ubergam3r on 2008-05-15
sound found 3 odd Trojans and ad ware no more pop ups or annoying stuff thanx

---

