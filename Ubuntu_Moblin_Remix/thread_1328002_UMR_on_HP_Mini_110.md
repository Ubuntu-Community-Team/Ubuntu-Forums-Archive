---
title: "UMR on HP Mini 110"
date: 2009-11-16
forum: Ubuntu Moblin Remix
---

### Post by xurizaemon on 2009-11-16
I've got Ubuntu Moblin Remix 9.10 installed on my HP Mini 110. A few issues, but it's really interesting to explore Moblin interface with regular Ubuntu under the hood.

So - a few issues, did I say? :)

No sound applet. My sound worked under Ubuntu Netbook Remix (although it was audio out only - see [this bug]("http://bugs.launchpad.net/ubuntu/+source/linux/+bug/376795")) after boot. In Moblin, sound required some manual modprobes to bring up the full sound system, and the volume control applet doesn't appear in the main menu.

Won't boot without noacpi. Sits at blinking cursor rather than firing up Ubuntu logo. No ACPI seems to slow things down. Tried it on a guess but seems to work consistently.

No wifi. Easily resolved by plugging into a wired connection (which worked automatically) and then running ```
sudo apt-get install bmcwl-kernel-source
```.

Unsure how to configure Grub. In UNR this is in the usual spot, /boot/grub/menu.lst and so forth. In UMR there is no /boot/grub menu directory. I see /etc/grub.d but I'm not sure if that's the full story. What's up here? Is this part of Moblin's efforts to speed boot time?

Also, seems like settings are not stored - maybe related to checking the "encrypt home dir" option when installing. Wondering if perms are mangled, but I can write to my home dir as expected.

Thanks in advance for any thoughts you might have!

---

