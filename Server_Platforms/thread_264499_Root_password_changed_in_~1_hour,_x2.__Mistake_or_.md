---
title: "Root password changed in ~1 hour, x2.  Mistake or security problem?"
date: 2006-09-24
forum: Server Platforms
---

### Post by chikin03 on 2006-09-24
Hi,

I've been trying to get a MythTV system up and running, and have been using Ubuntu very scarcely for the past year or so.  Anyways, Myth requires Apache, MySQL and PHP, so those were all new installs for me, and I did very little configuration with them.  I changed the mysql root password, but otherwise had no intention of serving anything outside of 127.0.0.1

So, I'm coming up on the home stretch, having installed MythTV and running checkinstall to encapsulate the compiled plugins.  It hangs every time on "Striping ELF binaries and libraries".  I go to the web, and there's no help.  Make clean, remake, no help.  Checkinstall is just a script, so I figure maybe I can edit it a little and I'll see what's going on.  I download it from a page like this: "http://fresh.t-systems-sfr.com/unix/src/privat2/checkinstall-1.6.0.tgz:a/checkinstall-1.6.0/checkinstall"
 and then search for how to make it executable.  I probably chmod +a+r+x it, or something similar.  I run it in my folder, realize I didn't actually change anything to make it debuggable, and ctrl+c to stop it.

Next thing I know, stuff just starts icing up.  Everything ends up being inaccessible.  Icons disappear, because they're no longer permissable.  I sudo, and the password is no longer valid.  I pull the network cable, and reboot.  No go.  Many boot errors, among them: "unable to start /sbin/klogd"

Am I the victim of a virus, or have I just made a ownership mistake somewhere?  This is the second time it's happened; the first time I was messing with /etc/sudoers so that mythtv could sudo (it couldn't at the time).  I'm getting good at rebuilding mythtv, but I'd like it to work without any trouble next time.  What do you guys think?

--Chi

---

### Post by chikin03 on 2006-09-24
Eh, from further browsing, I probably did something screwy in root.  Things seem awfully fragile, I guess, and I've never had this sort of trouble before.  I'll give it one more try.

Btw, if anyone is interested, the best of the how-to's is 
[http://www.mythtv.org/wiki/index.php/Installing_MythTV_SVN_on_Ubuntu_Breezy](http://www.mythtv.org/wiki/index.php/Installing_MythTV_SVN_on_Ubuntu_Breezy)

---

