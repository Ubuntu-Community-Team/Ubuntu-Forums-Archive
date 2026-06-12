---
title: "Cool software: Newton &amp; Backuppc"
date: 2005-10-01
forum: The Cafe
---

### Post by jdong on 2005-10-01
Hey folks! I'd like to direct your attention to some cool software I found:

(1) Newton Desktop Wiki ([http://newton.sourceforge.net](http://newton.sourceforge.net)). This is a Wiki-like program, primarily designed for use with GNOME. I've found it to be a great thinking pad. It's in extremely early alpha phase, but I've yet to get it to crash. Note that Wiki-style revision history is not implemented, which is currently the weakest flaw. Nonetheless, it's a great place to do day-to-day organization and jot down notes. Not in Ubuntu repositories, but their SF downloads page does sport a nice Ubuntu .deb that works well.

(2) Backuppc ([http://backuppc.sourceforge.net/](http://backuppc.sourceforge.net/)): Just noticed this today -- fancy backup program with a web-based GUI. Boasts the use of hardlinks to save space, while maintaining full restore compatibility with GNU utilities. Has remoting capability. Is in Universe. I'm currently doing some backups with it, and if all goes well, plan to write up a Wiki page.

---

### Post by UbuWu on 2005-10-01
[QUOTE=jdong]Hey folks! I'd like to direct your attention to some cool software I found:
(1) Newton Desktop Wiki. Not in Ubuntu repositories, but their SF downloads page does sport a nice Ubuntu .deb that works well.
[/QUOTE]

Tomboy is very similair and is in the repositories, so for easy installation go for this one.

---

### Post by jdong on 2005-10-01
Tomboy (in my testing at least) hasn't been as featureful, easy-to-use, or organized as Newton...

---

### Post by Knome_fan on 2005-10-01
Newton rocks.
And I think the dev is even hanging around the forums. :D 
[http://ubuntuforums.org/showthread.php?t=37029](http://ubuntuforums.org/showthread.php?t=37029)

---

### Post by darkmatter on 2005-10-01
Newton looks awesome. Think I'll give it a try.

---

### Post by dcraven on 2005-10-02
Well isn't this nice to see. As the author of Newton, it makes me happy to see people that like my little program. Thanks for the mention jdong!

Are you using the svn version or the 0.0.9 release?

Cheers,
~djc

---

### Post by majikstreet on 2005-10-02
[QUOTE=jdong]Hey folks! I'd like to direct your attention to some cool software I found:

(1) Newton Desktop Wiki ([http://newton.sourceforge.net)](http://newton.sourceforge.net)). This is a Wiki-like program, primarily designed for use with GNOME. I've found it to be a great thinking pad. It's in extremely early alpha phase, but I've yet to get it to crash. Note that Wiki-style revision history is not implemented, which is currently the weakest flaw. Nonetheless, it's a great place to do day-to-day organization and jot down notes. Not in Ubuntu repositories, but their SF downloads page does sport a nice Ubuntu .deb that works well.

(2) Backuppc ([http://backuppc.sourceforge.net/):](http://backuppc.sourceforge.net/):) Just noticed this today -- fancy backup program with a web-based GUI. Boasts the use of hardlinks to save space, while maintaining full restore compatibility with GNU utilities. Has remoting capability. Is in Universe. I'm currently doing some backups with it, and if all goes well, plan to write up a Wiki page.[/QUOTE]
you've messed up the links.

---

### Post by dcraven on 2005-10-02
[QUOTE=majikstreet]you've messed up the links.[/QUOTE]
The links provided include the closing bracket (I'm sure you already know this). The proper links are [here](http://newton.sourceforge.net) for Newton and [here](http://backuppc.sourceforge.net) for Backuppc.
Cheers,
~djc

---

### Post by jdong on 2005-10-02
fixed; VBulletin 3.5 has different linking behavior than the old system.

---

### Post by 23meg on 2005-10-02
i've used newton for a while, but then found the much superior [instiki](http://www.instiki.org) and am now using it as a personal wiki in its stead. anyone interested in wikis should definitely be aware of its existence. newton seemed to be lacking many essential features and was very buggy; i'm sure it will get a lot better with time though.

---

### Post by jdong on 2005-10-02
Fascinating -- instiki is definitely more featureful at the moment, but I personally hate having it run as a daemon (yes, I am a security prick).

I'm trying to hack Newton to use a Subversion backend for revision management. As far as bugginess, I haven't experienced any (using SVN snapshot, actually :) )

---

### Post by dcraven on 2005-10-02
[QUOTE=jdong]I'm trying to hack Newton to use a Subversion backend for revision management. As far as bugginess, I haven't experienced any (using SVN snapshot, actually :) )[/QUOTE]
Neato. Sorry 'bout the code. One of my goals is to modularize better and make it neater so that others can hack on it more easily after 0.1 release. It's pretty bad in places at the moment :)

After 0.1, I'm going to be looking into remote access of some form. I'm not sure if I'm going to allow spawning a little server by clicking a "Share" button, or if I'll just enable remote editing via gnomevfs. Maybe both. Whatever ends up being simplest in terms of usability. It'd be nice to use the same wiki from other machines. I'm going to have to think about revision history as well at some point I guess... But that's a big can o' worms that I've avoided thus far. :)

Cheers,
~djc

PS: Instawiki is really cool. I think we're just looking at different users. I personally use Dokuwiki for my "real" wiki. It shows in Newton's stylesheets :)

---

### Post by jdong on 2005-10-02
I don't promise much progress into hacking on SVN... I'm a very busy person :)


As far as sharing, just exporting to ~/public_html per edit is plenty -- Apache is a much stronger (and fairly light) backend that users can install themselves with mod_userdir.

I think having a revision system should be the first priority after 0.1

---

### Post by ardchoille on 2005-12-16
[QUOTE=jdong]Tomboy (in my testing at least) hasn't been as featureful, easy-to-use, or organized as Newton...[/QUOTE]
Well, at least Tomboy works. Newton won't even start up and gives no errors when run from a term.

---

