---
title: "Is there a mac alternative to wine?"
date: 2011-12-20
forum: The Cafe
---

### Post by guyver_dio on 2011-12-20
Not that I'd use it myself but I was curious, is there a mac alternative to what wine does for windows applications?

---

### Post by doorknob60 on 2011-12-20
No. The reason is that it takes a huge amount of effort to reverse engineer an OS, and comsidering that most Mac native apps also have Windows versions, and that Wine has been around since the 90's, it makes much more sense to put all the effort into Wine. Coming up with an even somewhat usable Mac alternative would take years and many people's hard work, all for just a small selection of Mac only software.

---

### Post by aysiu on 2011-12-20
Yes. It's right here:
[http://wiki.winehq.org/MacOSX/Installing](http://wiki.winehq.org/MacOSX/Installing)

---

### Post by guyver_dio on 2011-12-21
@doorknob60: fair enough :)

@aysiu: wasn't what i meant, maybe I should have been clearer. What if you wanted to install a mac installation on linux, is there something like wine that does that.

---

### Post by wolfen69 on 2011-12-21
> **guyver_dio said:**
> @doorknob60: fair enough :)

@aysiu: wasn't what i meant, maybe I should have been clearer. What if you wanted to install a mac installation on linux, is there something like wine that does that.

I too was confused by your original post. Thanks for clarifying. I get it now.

---

### Post by mips on 2011-12-21
PearPC which is an emulator will allow you to run older versions of OS X with PPC support. But this is not exactly what you are after as it still requires the OS and is probably in violation of Apples EULA.

---

### Post by ssam on 2011-12-21
it could be done. it might take roughly as much work as making wine. (maybe slightly less as maxosx is more unixy and has less legacy stuff).

but i have not heard of anyone even starting to do it.

---

### Post by mamamia88 on 2011-12-21
Isn't crossover wine based?

---

### Post by Lucradia on 2011-12-21
> **mamamia88 said:**
> Isn't crossover wine based?

Yes and no. A lot of things work better in crossover, while other things work better in wine. Similarly, ReactOS isn't wine, yet has some code from it (a lot, actually, it's just it has its own kernel, and thus can install Windows drivers, unlike Wine, which takes advantage of the Linux kernel for drivers.)

Mac OS had a wine implementation called darwine, but it's been abandoned for quite some time.

As for installing OSX Stuff on Linux.... Why?

---

### Post by forrestcupp on 2011-12-21
> **Lucradia said:**
> 
As for installing OSX Stuff on Linux.... Why?

Final Cut Pro

---

### Post by juancarlospaco on 2011-12-21
Yes, CocoTron.

[http://cocotron.org](http://cocotron.org)

---

### Post by boast on 2011-12-21
> **Lucradia said:**
> 

As for installing OSX Stuff on Linux.... Why?

maybe itunes, and steam games/other games which come with mac versions.

---

### Post by forrestcupp on 2011-12-21
> **juancarlospaco said:**
> Yes, CocoTron.

[http://cocotron.org](http://cocotron.org)

It looks like that is just a project to make Objective C development cross-platform, kind of like Qt is cross-platform. I don't think it is meant to actually run MacOS X program binaries in other OSs, though.

Still, that's pretty interesting. It would be cool if someone would make a good way to program iOS apps in Objective C without having to have a Mac.

---

### Post by juancarlospaco on 2011-12-21
> **forrestcupp said:**
> It looks like that is just a project to make Objective C development cross-platform


And Wine was only a experiment to run Windows 3.1 programs on Linux and see now...

---

### Post by forrestcupp on 2011-12-21
> **juancarlospaco said:**
> And Wine was only a experiment to run Windows 3.1 programs on Linux and see now...

But the difference is that this is to create binaries that run on different platforms, which is much different than *running* binaries from other platforms. It is creating binaries from source code, not taking a MacOS binary and making it work on a different platform. That would require a lot of reverse engineering, but creating a binary from source doesn't require hardly any reverse engineering, if any at all.

---

### Post by Lucradia on 2011-12-21
> **boast said:**
> maybe itunes, and steam games/other games which come with mac versions.

Steam works fine with Windows Wine. (Just not the overlay with some games.)

Check this for iTunes: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

Check this for Safari: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=5293](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5293)

Check this for Bonjour: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=5408](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5408)

Also, this site is extremely helpful for individual steam games: [http://www.steamgamesonlinux.com/portal-2/](http://www.steamgamesonlinux.com/portal-2/) (Portal 2 given as an example)

Games like Minecraft only require Java and OpenGL. Since OpenGL doesn't have an end-user runtime, and is instead mitigated by the drivers / hardware, it runs on linux if you have JAVA for Linux to handle JAR files. This is why Minecraft.net provides a linux version via just a JAR.

---

### Post by guyver_dio on 2011-12-21
> **Lucradia said:**
> As for installing OSX Stuff on Linux.... Why?

Well I came to ubuntu from windows, so I have alot of windows installations saved on my computer. At least with wine I have some chance of running those programs (even though I rather use linux alternatives since I'm running a linux OS). A Mac user would come from a mac and have many mac installations, all of which are now useless. That's why I thought maybe one exists. Again it was more a curiosity for me, as an ex-window user I'd have no need for it, but a ex-mac user might even though I know alot of software that exists for mac is also available on windows.

---

### Post by Lucradia on 2011-12-21
> **guyver_dio said:**
> I know alot of software that exists for mac is also available on windows.

See the reply above your reply here for some of those.

---

### Post by forrestcupp on 2011-12-22
> **Lucradia said:**
> See the reply above your reply here for some of those.

I think his point was that if you are a previous Mac user, and you have a big MacOS software library that you've invested in, you're not going to want to repurchase the Windows versions of that same software that you already paid for, only to turn around and run it in Wine. It would be nice to have a thing that works like Wine for all of your Mac software that you already own.

Plus, like I said earlier, a lot of Mac users really love things like Final Cut Pro that aren't going to have versions for Windows.

---

### Post by fdrake on 2011-12-22
the best way to emulate the installation/use of Mac apps is in a Mac env. You are better of installing Mac OS X 10.4.6 x86 Install DVD (JaS)  on a virtula machine and install there you mac apps. You won't be able to install in a virtual machine a reg Mac OSX but a hacked version might work,, see this link: [http://pietschsoft.com/post/2007/04/Can-you-run-Mac-OS-X-within-Virtual-PC-2007-on-Windows.aspx](http://pietschsoft.com/post/2007/04/Can-you-run-Mac-OS-X-within-Virtual-PC-2007-on-Windows.aspx)

cannot point you to the torrent file for obvious reasons...

---

### Post by forrestcupp on 2011-12-22
> **fdrake said:**
> You won't be able to install in a virtual machine a reg Mac OSX but a hacked version might work,, see this link: [http://pietschsoft.com/post/2007/04/Can-you-run-Mac-OS-X-within-Virtual-PC-2007-on-Windows.aspx](http://pietschsoft.com/post/2007/04/Can-you-run-Mac-OS-X-within-Virtual-PC-2007-on-Windows.aspx)

That link made my day. :)

I really got a kick out of the commenter who wanted to be able to run MacOS X in VirtualPC within XP that is running on his *Mac* computer. :lol:

---

