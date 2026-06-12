---
title: "Rapache Fix Didn't Work"
date: 2009-12-16
forum: Server Platforms
---

### Post by fiveironfrnzy08 on 2009-12-16
Hi,

I've gone through the Rapache fix "#HACK..." in RapacheGui.py and all that on my last install of Ubuntu and it worked. However, now with 9.10, the fix isn't working. I edited the RapacheGui.py file and Rapache is still freezing up when I edit or add anything...
Thoughts?

-Ryan

---

### Post by ievans on 2009-12-17
It worked for me on 9.10
/usr/share/pyshared/RapacheGtk\RapacheGui.py



        Master.register(self)
        if not Shell.command.ask_password(): sys.exit(1) ####Added this line 79####

        self.denormalized_virtual_hosts = {}

---

### Post by eneBeanee on 2010-01-10
The only way I got it to work was to add the hack and then start it via a terminal with sudo.

It asked for my password again once it had started.  If I started it normally it would fail after asking for the password.

---

### Post by Joshfokis on 2010-04-22
i cant get it to work for me at all... is there any way to get an updated version or what?

---

