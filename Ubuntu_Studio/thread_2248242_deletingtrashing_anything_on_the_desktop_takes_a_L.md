---
title: "deleting/trashing anything on the desktop takes a LONG time"
date: 2014-10-13
forum: Ubuntu Studio
---

### Post by a-you on 2014-10-13
I wonder if anybody else is experiencing this:

If I select anything on the desktop and then right click and "Delete" it it takes maybe a minute for that to actually get moved to the trash. Trashing items from within nemo works fine (I'm using nemo instead of thunar or nautilus). I don't know where to start looking for why this might be.

Also this delay keeps getting gradually longer. That is, over months it has increased. And it used to be so that the first time something was deleted after booting there'd be this delay but then after that first item things would get deleted quickly. Now it has gotten to where it always takes a long time. So in other words the problem gets gradually worse.

If anybody has any ideas about a solution it'd be much appreciated, thanks in advance.

---

### Post by redbull00 on 2014-10-14
I've never experienced this issue, but have you tried to delete other files than from desktop using thunar? Does it take so much time too? If yes, then maybe try to sudo apt-get purge thunar and then reinstal it. It will also partly remove xubuntu-desktop but you can reinstall it afterwards.

---

### Post by a-you on 2014-10-15
That's a good idea; I hadn't thought of it. I just tried it now and curiously the right click menu for a thunar window has both a "move to trash" item and "delete" (the desktop right clickk menu has only "delete" but that moves the item to the trash). I tried both and both happen immediately. This is an odd problem.

---

