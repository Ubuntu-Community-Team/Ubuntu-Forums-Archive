---
title: "Wine won't update"
date: 2011-04-29
forum: Wine
---

### Post by Albertint on 2011-04-29
Wine has been real stubborn for me. It started right around when 1.3.18 was just out, that I decided to install it. Sure thing, I just go into the terminal, add the repository and update, then uninstall the old version and install the new. However, if I go into wine, it says in the about tab that it's 1.3.16; it also says that in the terminal when I put in 'wine --version'.

So I just updated to 11.04 this morning, hoping the problem would be solved. Did the same thing, and it **still** won't update to 1.3.18... Which is starting to aggravate me. 
Am I doing anything wrong, or am I experiencing a bug?

UPDATE: Even downloading the package straight from the repository site, it will list as 1.3.16, and I'm certain this isn't just a mispell on my system as the game I'm trying to play would function differently with some of the updates... So what the heck?!

---

### Post by cogadh on 2011-04-29
Have you ever compiled Wine from source instead of installing it from a package? If so, that is likely what is causing this. The self-compiled version is still resident somewhere on your system and is "seen" as the default Wine installation. You'll need to run a "make uninstall" from the source directory to get rid of it.

---

### Post by Albertint on 2011-04-30
Ah yes, you may be right. I think I did compile a custom package some time ago, but had forgotten about it. Do I go to the directory where it's installed or what?
EDIT: Oh wait, I know what to do. I'll go try it out now.

SECOND EDIT: I gave the 'make install' root access as it puttered out the first time with this message:

> rmdir: failed to remove `/usr/local/lib/wine': No such file or directory
make: [uninstall] Error 1 (ignored)


A bit longer than that, but basically it just read out file reading errors. I think I screwed it up as I had wine running. Going to try and do it again, or do I actually need the patch I installed with wine?

---

### Post by Albertint on 2011-04-30
Oh! It actually gets 1.3.18 just doing that. Okay... I see.

Thanks again! This is SOLVED. :P

---

