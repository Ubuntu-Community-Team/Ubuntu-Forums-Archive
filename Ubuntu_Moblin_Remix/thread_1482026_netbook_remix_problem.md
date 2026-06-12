---
title: "netbook remix problem"
date: 2010-05-13
forum: Ubuntu Moblin Remix
---

### Post by LordOfTheBoards on 2010-05-13
Hello everyone!

My problem is that I have ubuntu netbook remix installed on a nettop system, atom 330 + ion. It seemed quite ok, but I wanted to experiment, so I installed th moblin-session package. When Install finished I logged out and logged in with the moblin session. Now the bad things start. Once logged in I don't see anything but the background and thoe mouse cursor. When I reboot the computer it automatically logs me into this moblin session and I can't do anything. Is ther a shortcut to stop ubuntu from logging in automatically. Or any other easy way to get out of this misery, or do I have to remove moblin session via terminal and the apt-get command (won't that screw up things?)?

Thanks for some help!
lotb

---

### Post by sanderd17 on 2010-05-13
can you try the follwing?
[LIST]
[*]hit CTRL+F2 once you're logged in.
[*]you shoud see a startup prompt, type gnome-terminal and execute
[*]in the gnome terminal you can uninstall the moblin package with
[/LIST]
```

sudo apt-get purge moblin-session

```
Then you can try to reboot.

---

### Post by Zionoxis on 2010-05-13
I was curious about this myself with my desktop. Does that fix change it so the OS starts up normally or does it allow Windows to boot as the primary? And when the time comes that I become fluent in Ubuntu, how can I set it as the default OS?

---

### Post by LordOfTheBoards on 2010-05-14
That's  what I did, actually with the apt-get remove command. Works fine now, but I am sure I have some unneded moblin packages installed. Would purge take care of them too?

"And when the time comes that I become fluent in Ubuntu, how can I set it as the default OS?"

To set which Os boots up by default you have to change the boot order in GRUB. I'm sure you'll find information needed in the forums. Don't know where to look for those settings off the top of  my head.

---

