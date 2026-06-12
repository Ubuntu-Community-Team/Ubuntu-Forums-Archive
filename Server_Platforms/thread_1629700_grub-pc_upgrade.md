---
title: "grub-pc upgrade"
date: 2010-11-24
forum: Server Platforms
---

### Post by Neikius on 2010-11-24
So today I decide to update my 10.4 server installation and 'lo behold, I get a prompt that I cannot decide what to do with.

I have to select grub install device (choices beeing /dev/sda /dev/sdb and the /dev/sdc that is md raid1 device). Also the installer claims grub was installed to a disk that is no longer present! That is untrue.

So why am I presented with this choice, since everything is obviously working but after this update might not? There is also no cancel button!

I guess I will just kill the updater and be gone with it, but still. I suppose this a nasty bug or a potential to break things. When I installed stuff I didn't care much where grub was. Everything default is ok. But now it seems much scarier choosing.

I guess it should be the same whether I install on /dev/sda+sdb OR on sdc (raid1 of that). True?

---

