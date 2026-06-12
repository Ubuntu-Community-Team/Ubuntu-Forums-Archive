---
title: "network manager is a disaster"
date: 2008-11-13
forum: Testimonials &amp; Experiences
---

### Post by jworr on 2008-11-13
I've been using Ubuntu since Hoary and I have to say that the current network manager is the worst thus far.  Why?  Because I've spend hours trying to get it connect to my wireless router and it only works 50% of the time.  When I login, the network manager applet will say it's connected, but did it?  No!  How about reconnecting?  Nope, that doesn't change anything, my only solution is to restart and pray it works the next time.  Well that's great, I might as well set my background to grassy rolling hills.  It was rock solid under every other version of Ubuntu I've used and now I've resorted to configuring my interfaces via /etc/network/interfaces.

Which leads me to my next point, poor compatibility with the config file.  Since my previous network configuration was stored there by 8.04, the network manager decided it wouldn't configure my wireless card.  Oh thanks for not telling me that network manager that was so thoughtful. It only took me hours of reading forum posts and [bug reports]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/256054/comments/24") to find that nice piece of info out.  Of course, I should have realized I need to delete my connection settings in order to set it up.

Finally, the gnome keyring decided that the network manager was getting all the fun so it decided to be a pain too.  Deleting the keyring config like this [post]("http://pennsylvania.ubuntuforums.com/showthread.php?p=6069702") only partly fixed the problem.  Now auto-login with gdm wants my password for my keyring.  Oh wait, there isn't one.

Well that's all I've got for my rant, but really can't we just keep a working network manager around for a bit instead of tweaking it each release?

---

### Post by RawMustard on 2008-11-14
Try this, works for me :)

[http://wicd.sourceforge.net/screenshot.php](http://wicd.sourceforge.net/screenshot.php)

---

### Post by SeanHodges on 2008-11-14
No it's not. A lot of people, including myself, are happy with the current network manager.

It's all very well to rant about these things, just as long as you're happy not to get anything constructive out of it.

---

### Post by ukripper on 2008-11-14
Use this - [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

