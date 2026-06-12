---
title: "Europa Universalis Rome Not working this time"
date: 2009-12-01
forum: Wine
---

### Post by Azuu on 2009-12-01
I have used EU:R for two installations of ubuntu jaunty, and on both of those it worked without a hitch. The mitigating factors are, processor doubleclocking issue, grub command acpi=off, is still present in the exact same form as they were when I started playing and the fact that i am loading the game files and .exe from a ntfs hdd. This reinstall however, it refuses to work beyond the menu screens. Even getting to the menu screen took hours of lowering settings I never had to before. I am using the same user.reg,system.reg settings, and I am using the same computer hardware/installation.

I will attach what the console outputs, but I will outline the highlights as I know them:
1)fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x15a5a0) Unhandled query type 5
(repeats and seems to do nothing to break it.)
2)err:d3d:record_lights Light 0 in stateblock 0x5fea52d8 does not exist in device stateblock 0x15d618.
(important since it happens just after selecting the start game option)
3)wine: Unhandled page fault on read access to 0x000000e4 at address 0x8c78d2 (thread 0046)
(breaks and starts debugging after)
4)Unhandled exception: page fault on read access to 0x000000e4 in 32-bit code (0x008c78d2)
(last error before debug and wine hangs until forcequit from me)

attached is the errors and subsequent debug.'

---

