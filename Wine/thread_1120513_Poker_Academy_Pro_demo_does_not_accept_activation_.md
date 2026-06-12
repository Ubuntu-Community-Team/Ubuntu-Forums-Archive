---
title: "Poker Academy Pro demo does not accept activation code"
date: 2009-04-09
forum: Wine
---

### Post by alanggn on 2009-04-09
Poker Academy Pro 2 Demo under Ubuntu 8.10 "Intrepid".
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11675](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11675)

Wine Version: 1.0.1

I enter the activation code for the demo and get: "The key entered is not for this product"
I have tried with winecfg set to win98 and xp. Both have same results.
Their tech support says the validation process is not supported under Wine.

Any ideas?
Thanks.

Don't think this will help but here is Terminal Output:
[email]me@ubu:~/.wine[/email]/drive_c/Program Files/PokerAcademyPro2$ wine PokerAcademyPro
fixme:win:EnumDisplayDevicesW ((null),0,0x6acbfc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x6acbfc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x6bdbb8,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
fixme:system:SystemParametersInfoW Unimplemented action: 8204 (SPI_GETFONTSMOOTHINGCONTRAST)
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
fixme:system:SystemParametersInfoW Unimplemented action: 8204 (SPI_GETFONTSMOOTHINGCONTRAST)
fixme:imm:ImmGetOpenStatus (0x1474a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x1d4690): semi-stub
fixme:imm:ImmGetOpenStatus (0x1d50c0): semi-stub
fixme:imm:ImmGetOpenStatus (0x1d7b88): semi-stub
fixme:win:FlashWindowEx 0x786a4cfc
fixme:imm:ImmGetOpenStatus (0x1d7638): semi-stub
[email]me@ubu:~/.wine[/email]/drive_c/Program Files/PokerAcademyPro2$

---

