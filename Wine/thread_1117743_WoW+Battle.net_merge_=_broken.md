---
title: "WoW+Battle.net merge = broken?"
date: 2009-04-06
forum: Wine
---

### Post by kano on 2009-04-06
Hi all,

I'm not running on ubuntu, but I figured this would get more replies over here than on the Arch forums since there's not many people running WoW on Arch.

I recently merged my WoW account with my battle.net so I could take advantage of the blizzard mobile authenticator on my iPhone. 
Unfortunately, I can no longer even login WoW. :(

I've tried removing the authenticator, but it's still going it since I have to login using battle.net.

Errors from console:
```

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"

```

When logging in I get a runtime error with the following.
```

Runtime Error!

Program:
R6034
An application has made an attempt to load the C runtime library incorrectly.
Please contact the application's support team for more information.
[  OK  ]

```

Hitting ok will close the box and I get a login error from WoW. Doesn't crash.

Anyone else try merging with a battle.net and get this? Google gives me nothing. I'm guessing that the merge is too new for anyone to have noticed the issues.

Hoping there's a solution so I can use the authenticator, or I guess i'm gonna be calling blizzard to un-merge later :(

---

### Post by kano on 2009-04-06
Looks like I spoke too soon, I found a solution right after posting. :KS

Using the winetricks script from [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

$ sh winetricks win2k vcrun2005sp1

fixed the error, and I can login now.

---

### Post by Professor Goat on 2009-05-11
well glad that worked for yuh! i still cant get it to run. get the same error every time. ughh...lack of linux support annoys me. i had it working perfectly before this merg.

---

### Post by robindegen on 2009-07-27
At first i thought the unable to login was a wine problem.. but i'm having the same problems on my win xp dual boot aswell. It's just battle net that's borked really.. the forums are full of it

---

