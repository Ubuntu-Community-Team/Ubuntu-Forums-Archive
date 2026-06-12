---
title: "Wine and Linux integration"
date: 2009-02-04
forum: Wine
---

### Post by BlackMeTaL on 2009-02-04
I was wondering if something was possible with Wine. I'd like to have some integration with native Linux applications. Like this: when you do some action with a Wine program (uTorrent) that opens a directory it loads the directory in a Wine explorer like program. I'd like it to open Nautilus with the right directory. Also when opening some file, it would be beneficial if it did it with gnome-open.

Is this possible and what are your thoughts?

---

### Post by Ferrat on 2009-02-04
In theory it should be possible but require a massive rewrite, also it would open up the door for breaking the hierarchy rules that help protect your system, for ex. right now a virus can't really do much because the segregation dictates that a lower level can manipulate a higher one but not the other way around but should that change making it possible to do stuff above current "level" it could really make a mess of things. 
Since wine is more or less a wrapper you automaticly get level block between it, wine runs on the same level as user but the app runs inside that, like a bubble around it. 

I use utorrent as well and know what you mean but the loss of security would be to big so it will probably never be a feature like that unless wine is somehow integrated seamlessly in to the OS. 

You might be able to write a program that checks if the file is done and if so puts it on a list or something like an applet? where you can start it or open the containing folder etc?

---

### Post by BlackMeTaL on 2009-02-05
Thanks for your response. I never realized that Wine was like a sandbox. Although I think a virus would still be able to destroy files as it can access and modify every file that a normal user can modify.

---

