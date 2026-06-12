---
title: "Launchpad is now open source"
date: 2009-07-21
forum: The Fridge Discussions
---

### Post by TheFridge on 2009-07-21
Hi everyone &#8212; Launchpad is now open source.

 Huge congrats (and thanks) to the Canonical Launchpad team, who worked overtime to make this happen sooner rather than later.

 Note that although we announced previously that we&#8217;d be holding back two components (codehosting and soyuz), we changed our minds :-).  They are opened too &#8212; all the code is open.  Our public announcements are here:

   [http://blog.canonical.com/?p=192](http://blog.canonical.com/?p=192)
  [http://www.ubuntu.com/news/canonical-open-sources-launchpad](http://www.ubuntu.com/news/canonical-open-sources-launchpad)

 The Canonical launchpad developers will be on IRC in #launchpad-dev on irc.freenode.net.  For real time development discussion, that&#8217;s the place to go; for usage questions, #launchpad is still the channel, as before.

 The development wiki is dev.launchpad.net.  Right now, only Canonical people can edit it.  We&#8217;ll expand the access list eventually, but just for these first few days I&#8217;d like to leave it tightly controlled because there will be a lot of eyeballs on it, and we need to figure out the right strategy to allow the good edits while preventing vandalism and spam.  (I&#8217;ve run other wikis, and spam is *by far* the majority of all edits to any open wiki, so we&#8217;ll need to do that carefully.)

 The mailing list is launchpad-dev {AT} lists.launchpad.net, which you can join by visiting [https://launchpad.net/~launchpad-dev](https://launchpad.net/~launchpad-dev) and joining the team there (a team and a mailing list are sort of the same thing in Launchpad).  Again, that&#8217;s the development mailing list; user questions should still go to launchpad-users {AT} lists.launchpad.net.

 Canonical is continuing to host Launchpad.net, of course, so we will vet and shepherd changes onto the production servers.  The wiki explains the basics of how to learn your way around the code, make patches, and get code review; these processes will evolve organically, and we&#8217;ll keep the wiki updated as they do.

 Note that the images/icons are still copyrighted traditionally, to protect Launchpad&#8217;s visual identity.  But they&#8217;re shipped with the code and are fine to use for development and testing purposes.  Just if you launch a production server, it needs to look different &#8212; and have a different name, of course, as &#8220;Launchpad&#8221; is a trademark.  From our point of view, we&#8217;re doing this to improve our hosted service, so if you feel the need to run it on your own servers, that might mean we&#8217;re doing something wrong, in which case we hope you&#8217;ll tell us what.

 Please bear with us as we learn how to be an open source team.  Many of the Launchpad developers have open source experience of course, but as a team we&#8217;ve been working on Launchpad in-house for some years.  This is a big change.  We&#8217;re eager and ready, though.

 That&#8217;s everything.  Questions welcome, and patches too.

 Originally sent to the [launchpad-users mailing list]("https://lists.launchpad.net/launchpad-users/msg05118.html") by Karl Fogel on Mon, 20 Jul 2009 22:31:57 -0700

 

[More...](http://fridge.ubuntu.com/node/1882)

---

### Post by sarfarazkazi on 2009-07-21
wOOt!:D

---

### Post by Vinze on 2009-07-21
Thanks Canonical ^.^

Odd though that you decided to ship LP's icons instead of shipping generic replacements.

---

### Post by Sand &amp; Mercury on 2009-07-21
Very good call!

[IMG]http://i185.photobucket.com/albums/x90/fredapeople/animated/Applause-2.gif[/IMG]

---

### Post by nhandler on 2009-07-22
> **Vinze said:**
> Odd though that you decided to ship LP's icons instead of shipping generic replacements.

To quote the announcement:
> Note that the images/icons are still copyrighted traditionally, to protect Launchpad’s visual identity. But they’re shipped with the code and are fine to use for development and testing purposes. Just if you launch a production server, it needs to look different

The burden of creating new icons falls on users who decide to launch production servers running the Launchpad code. There is no reason for the Launchpad developers to waste time and resources creating new icons, especially since the Launchpad icons are fine for development and testing purposes.

---

