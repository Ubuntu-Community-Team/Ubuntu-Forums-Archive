---
title: "Need for Speed World - not installing"
date: 2011-06-15
forum: Wine
---

### Post by m4tx1 on 2011-06-15
Hi!

I want to install NFS: World, but installer isn't working. I have this in terminal when I run installer:
```
m4tx@m4tx-EP35-DS4:~/Pobrane$ wine setup_441_en.exe 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:richedit:RTFCharSetToCodePage unknown charset 87
err:richedit:RTFCharSetToCodePage unknown charset 87
err:richedit:RTFCharSetToCodePage unknown charset 87
err:richedit:RTFCharSetToCodePage unknown charset 87
err:richedit:RTFCharSetToCodePage unknown charset 87
err:richedit:RTFCharSetToCodePage unknown charset 87
err:richedit:RTFCharSetToCodePage unknown charset 87
err:richedit:RTFCharSetToCodePage unknown charset 87
err:richedit:RTFCharSetToCodePage unknown charset 87
err:richedit:RTFCharSetToCodePage unknown charset 87
err:richedit:RTFCharSetToCodePage unknown charset 87
err:richedit:RTFCharSetToCodePage unknown charset 87
err:richedit:RTFCharSetToCodePage unknown charset 87
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
```

And this when I click "I agree" button:
```
wine: Unhandled page fault on write access to 0x6e20736d at address 0x7bc44bb6 (thread 0036), starting debugger...
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7bc4756c
```

My questions: why, and how to fix it?

I'm using Ubuntu 11.04 x86_64 and Wine 1.3.21. I have installed dotnet20 and ie7 using winetricks.

Thanks in advance
Regards

---

