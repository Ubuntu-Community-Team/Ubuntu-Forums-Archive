---
title: "So I blew up Ubuntu..."
date: 2005-05-29
forum: The Cafe
---

### Post by YourSurrogateGod on 2005-05-29
I didn't know where else I could post this, so I'm trying here...

Well, I had a fun week with my operating systems. Windows... well, lets not go into that right now :) . Then with Ubuntu... My linker, for some ungoddly reason, would not/could not work after I compiled a program (what I did was compile it and when it came to link the program, it gave me an error.) So I figured I'd uninstall gcc and reinstall it. Well, smarty-pants me (no I was not clearly thinking at the moment), I simply did a complete uninstall and got rid of alot of important features (one of them synap), now I can't boot to Ubuntu.

My question is more about the MBR. What I would like to do is use fdisk to get rid of my old Ubuntu partitions and reinstall it (I didn't have many useful files there.) Now, when it comes to configuring grub so that I could boot to Ubuntu, will it be able to do that without any unpredictable consequences? What are the dangers of what I'm trying to do?

---

### Post by tread on 2005-05-29
Umm .. if you don't care about losing files, I don't really see any danger. You can reuse the older partition structure, just format when you are reinstalling. Grub will be installed again too ..

---

### Post by benplaut on 2005-05-29
[QUOTE=YourSurrogateGod]I didn't know where else I could post this, so I'm trying here...

Well, I had a fun week with my operating systems. Windows... well, lets not go into that right now :) . Then with Ubuntu... My linker, for some ungoddly reason, would not/could not work after I compiled a program (what I did was compile it and when it came to link the program, it gave me an error.) So I figured I'd uninstall gcc and reinstall it. Well, smarty-pants me (no I was not clearly thinking at the moment), I simply did a complete uninstall and got rid of alot of important features (one of them synap), now I can't boot to Ubuntu.

My question is more about the MBR. What I would like to do is use fdisk to get rid of my old Ubuntu partitions and reinstall it (I didn't have many useful files there.) Now, when it comes to configuring grub so that I could boot to Ubuntu, will it be able to do that without any unpredictable consequences? What are the dangers of what I'm trying to do?[/QUOTE]

that's the kind of thing you're supposed to do on a test system... pick 'em up for a dime-a-dozen at the local corporite office getting rid of old win 98 machines  \\:D/

---

