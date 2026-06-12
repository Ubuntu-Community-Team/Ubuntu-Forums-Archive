---
title: "Canadian Multilingual Standard Layout, Update needed!"
date: 2022-03-24
forum: Ubuntu Development Version
---

### Post by alexb678 on 2022-03-24
Hi,

I don't know where should I go for this request but I found an issue with the Canadian Multilingual Standard layout on Ubuntu. This layout has not been updated since 15 years at least because the euro &#8364; sign is not there. I found also the omega sign (lowercase) missing. 

/usr/share/X11/xkb/symbols/ca

Group 1

The currency sign should be added to the gr1/level3 (AE04), **line 179**

```
key <AE04>  { [         4,     dollar,     currency ]       };
```

The Euro Sign should be added to a new line (AD03), group 1/level 3,** line 189**

```
 key <AD03>  { [         e,          E,           EuroSign  ]};
```

Group 2
 
**Line 215-216**, the currency sign should be replaced by the EuroSign (Group 2/Level 2)

```
key <AE04>  { [    onequarter,    EuroSign ]        };
```

Key (AD01), Greek omega (lowercase) should be added, group 2/level 1, **line 225-226**

```
 key <AD01>  { [ Greek_omega,    Greek_OMEGA ]       };

```

Thanks!

---

### Post by QIII on 2022-03-25
The Ubuntu xkb-data package is maintained by Canonical, LTD.  This is a peer-to-peer end user support forum.  Nobody here is an employee of Canonical and nobody here can affect changes to Canonical's main repos.

I would suggest contacting the developers on the mailing list at [ubuntu-devel-discuss]("http://lists.ubuntu.com/mailman/listinfo/Ubuntu-devel-discuss") or on irc.libera.chat at the #ubuntu channel

---

### Post by alexb678 on 2022-03-25
Thanks, your anwser is helpful. :) ! I had no clue where to knock.

---

