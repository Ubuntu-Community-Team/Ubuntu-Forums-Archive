---
title: "Courier MTA"
date: 2005-04-18
forum: Server Platforms
---

### Post by Chris_Grindstaff on 2005-04-18
Hello All,
I just installed Hoary yesterday and was trying to setup the Courier statck. I noticed that mail > main contains part of the stack: courier-base, courier-authdaemon, courier-imap, and courier-pop. I don't see a courier-mta however for smtp.

I did see courier-mta in universe but when I try to install it from aptitude it says it's broken - I think due to postfix being installed and included in Ubuntu base.

So my question is there a way around this besides the obvious installing from source? I guess another option would be to configure postfix to work with courier. Is this just a "work in progress" issue and I can expect the next version of Ubuntu to contain courier-mta?

Thanks for the info and great distribution.
-Chris

---

### Post by ScatterBrain on 2005-04-19
[QUOTE=Chris_Grindstaff]I did see courier-mta in universe but when I try to install it from aptitude it says it's broken - I think due to postfix being installed and included in Ubuntu base.[/QUOTE]

 I *think* you can remove postfix if you wish

```
sudo apt-get remove postfix
```
then
```
sudo apt-get install courier-mta
```

I've never tried it, because I prefer postfix, but I see no reason why it wouldn't work.

---

### Post by Chris_Grindstaff on 2005-04-19
Worked like a charm ScatterBrain, much thanks.

[QUOTE=ScatterBrain]I *think* you can remove postfix if you wish

```
sudo apt-get remove postfix
```
then
```
sudo apt-get install courier-mta
```

I've never tried it, because I prefer postfix, but I see no reason why it wouldn't work.[/QUOTE]

---

