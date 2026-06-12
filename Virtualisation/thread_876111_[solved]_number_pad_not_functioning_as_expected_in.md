---
title: "[solved] number pad not functioning as expected in guest OS"
date: 2008-07-31
forum: Virtualisation
---

### Post by guiliker on 2008-07-31
Not sure if this should go here...

Host OS: Hardy Heron
Guest OS: WinXP Pro Spk 3
Virtualisation: VMWare Server 1.0.6 build-91891

The numeric key pad on my keyboard functions as expected in the host OS however in the guest OS it appeared to do nothing. After a forum search realised that it could be working but not as a key pad. When I pressed the 2,4,6,8 keys in the guest OS I saw them jump between desktop icons the same way as the directional keys work.

The Fix:
```
Press Left Shift + Control + Num Lock
```
you may hear a system beep when attempting to use the numeric keys 2,4,6,8 as directional keys

I do not know if there is somewhere to "select an option" as nothing seems to have changed in Start>Control Panel>Keyboard or Start>Control Panel>Accessibility Options

---

### Post by vesaliuz on 2008-11-12
Simpler answer is generally the best. thank you

---

