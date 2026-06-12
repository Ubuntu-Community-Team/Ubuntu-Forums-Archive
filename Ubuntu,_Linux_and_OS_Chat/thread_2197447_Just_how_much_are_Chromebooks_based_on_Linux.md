---
title: "Just how much are Chromebooks based on Linux?"
date: 2014-01-03
forum: Ubuntu, Linux and OS Chat
---

### Post by go.harrison on 2014-01-03
So I understand the fact that the Chrome OS is based on Linux but by how much?
With the rise of Chromebooks, viruses, maleware, hackers, and spywares will likely increase. Also, _what about Android_?
That being said, wouldn't that make Linux users with various distros vulnerable?
I also understand that Linux OS' make up a real small fraction of the desktop OS market share (which is less than 2%)

This is more of a discussion than a required question and answer. So I'm open to what you guys have in mind.

---

### Post by vasa1 on 2014-01-03
I suspect this is a "**recurring**" discussion. Will "Linux" be targeted more because of its increasing popularity? Probably so, but is there anything better?

And while it certainly would be nice to know how much the Chrome OS is based on "Linux", I doubt there's a final answer. Both are evolving. It seems that Chromebooks are, for now at least, a success: [http://www.computerworld.com/s/article/9245119/Steven_J._Vaughan_Nichols_The_Windows_killer_Chromebook](http://www.computerworld.com/s/article/9245119/Steven_J._Vaughan_Nichols_The_Windows_killer_Chromebook)

My suspicious mind leads me to anticipate another flurry of sock puppet articles about how Linux will become more insecure because of increasing popularity. I wonder what the writers of those articles will suggest as secure alternatives :)

---

### Post by tgalati4 on 2014-01-03
It used to be 1%.

---

### Post by lykwydchykyn on 2014-01-04
Strictly speaking, "Linux" is a kernel -- a set of hardware drivers and basic memory management routines that form the core of the operating system.  Colloquially speaking, "Linux" is a somewhat nebulous stack of software that is built on top of the Linux kernel that typically includes the GNU userland (shell, C libraries, core utilities, compilers, etc) and a variety of other subsystems like an X server, an init system, a bootloader, programming libraries, etc.

Android and ChromeOS are both technically "Linux" in that they use the Linux kernel.  Android has almost nothing else in common with the stack decribed above, it's basically a java runtime sitting on a Linux kernel.  ChromeOS is much more like a traditional Linux distribution, but has its own custom graphical environment and Chrome is pretty much the focus of the whole interface.

The thing about "Linuxes" is that it's a much broader and looser designation than say, OSX or Windows.  *Any* OS built on any version or variation of the Linux kernel can be realistically called "Linux" in the colloquial sense.  This diversity poses problems for the would-be malware author.

For example, if you exploit a flaw in the current kernel version in ChromeOS, there's no reason to expect that flaw will exist in Ubuntu, Arch, or Suse, which are all using different versions of the kernel with different patches and configurations applied.  If you try a social engineering exploit by trying to mimic a native error message, "native" is totally different between Chrome, Android, Ubuntu, Suse, Crunchbang, RHEL, etc.

I think it's more likely (and already happening to some extent) that malware will shift focus from the OS level to the browser or common browser plugins.

---

