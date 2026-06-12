---
title: "I don't own a mac... and I just fixed someone's."
date: 2008-12-14
forum: The Cafe
---

### Post by damis648 on 2008-12-14
I just helped somebody fix their Mac... I don't even run OS X or even have a mac. (AND I did it over the phone!) :popcorn: BUT that is thanks to Ubuntu/Linux and a little prior knowledge of Mac OS file structure. What happened was... their user just... disappeared. Yes, Gone. What happened, I really don't know, but /Users/Connor (his home, Mac OS uses /Users as home) still existed. His user was not visible in the login menu, so I though okay, let's try something. So I told him how to reboot into single user mode, and I decided to try to use passwd on the username. NOT FOUND. So what did I do? Again, over the phone, instructed him how to remove .AppleSetupDone (the files which determines the computer is not on its first, setup boot). He did that, and rebooted, and set up a new user (his old one was Connor, the new one he called newconnor). We rebooted into single user again, and I instructed him how to backup /Users/newconnor (in case this didn't work) to /Users/newconnor-bak. I then though what would be fastest, and symlinked /Users/Connor to /Users/newconnor so he would have everything back. Well it didn't work. And then it came to me: Ownership. /Users/Connor, which was symlinked, was still owned by the non-existent Connor. So in short, a quick chown on /Users/Connor did the trick. Anyway, what I am trying to say is thank you. For my own experience with Linux, I was able to solve this issue. :popcorn:

---

### Post by DeadSuperHero on 2008-12-14
Good for you!
I'm often surprised at myself at fixing similar errors in our Mac lab at school. It makes me feel smart, and happy, to know how to get around in a UNIX/UNIX-LIKE system.

---

### Post by tom66 on 2008-12-14
Mac and Linux are very similar as they are both based on the same architecture which is nice for cross-platform fixes, I guess.

---

### Post by Redache on 2008-12-14
> Mac and Linux are very similar as they are both based on the same architecture which is nice for cross-platform fixes, I guess.

They actually use the same Free Software, Linux is more of an implementation of Minix than Unix. Most of the Terminal Commands are the same or similar as they are both derived from the same software source.

Architecturally whilst they are similar they come from different sources. Although, yes Macs and PCs are x86.

---

### Post by Ocxic on 2008-12-14
The proper way would have been to activate the root account, and re-create his user with the same short name of his home folder.

Not to mention that you will have made his life, and mine harder if I ever need to support him when/if he calls in (I'm an Apple Technician) and this could rightly confuse the crap out of anyone trying to troubleshoot an issue on his computer if he ever needs help, since we will not know about the link, and be wondering why there's one there in the first place. And it will screw with our archive and install feature since the link/permissions may not be preserved.

---

### Post by damis648 on 2008-12-14
> **Ocxic said:**
> The proper way would have been to activate the root account, and re-create his user with the same short name of his home folder.

Not to mention that you will have made his life, and mine harder if I ever need to support him when/if he calls in (I'm an Apple Technician) and this could rightly confuse the crap out of anyone trying to troubleshoot an issue on his computer if he ever needs help, since we will not know about the link, and be wondering why there's one there in the first place. And it will screw with our archive and install feature since the link/permissions may not be preserved.

The problem was
1. We had absolutely no way of logging into any GUI login, so the root user could not be enabled and
2. I don't know about Mac OS X, I do not run it. I was cautious because I was afraid if I created a new user to inherit /Users/Connor, it might erase the contents, and I was not going to risk that.

---

### Post by Ocxic on 2008-12-14
"passwd root"  while in single user mode.

---

### Post by damis648 on 2008-12-14
I had no idea that would actually enable it for GUI login... good to know!

---

