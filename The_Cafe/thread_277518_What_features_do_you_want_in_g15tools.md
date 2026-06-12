---
title: "What features do you want in g15tools"
date: 2006-10-14
forum: The Cafe
---

### Post by Aneurysm9 on 2006-10-14
I've been thinking about future development for the g15tools project and I figure that, now that there are a fair number of people using the tools, it makes sense to ask you what you want them to do.  Take the poll.

---

### Post by Aneurysm9 on 2006-10-18
Can I ask those of you who have voted for improving current features for suggestions as to how to do so?  I've got an idea or  two for g15composer, but I'd like to hear how all of you think the tools can be improved.  Thanks.

---

### Post by maniacmusician on 2006-10-18
can you please give some background on g15tools? i have no idea what it is.

---

### Post by Aneurysm9 on 2006-10-18
Sure, it's a set of libraries and utilities for making use of the LCD and extra keys on the logitech G15 keyboard under Linux.  You get get more info at [http://g15tools.sourceforge.net](http://g15tools.sourceforge.net)

---

### Post by daihenka on 2006-10-24
A couple of feature improvements are:

* To have right justified text.  I didn't see anything in the README file for g15composer about it.  I think that will help with some cleaner display work.

* Display switching with g15composer to be switched from the MR button to the proper display switch button beneath the LCD.  (I think you mentioned that you might be putting this in a future version)

---

### Post by Aneurysm9 on 2006-10-24
Right justified text should be fairly simple to implement.  An update for libg15render will be required for right justified TTF text, but that too shouldn't be too big a deal.  Right now, though, I'm in the middle of rewriting g15composer with flex and bison so that it has a proper parser, so it may be a little while before a new release.  If you want to try the new version, there's a g15composer-ng branch in the svn repo that's currently about at feature parity with g15composer-1.1.

The display switch is controlled by g15daemon, which isn't really my project.  I'll talk with mlampard about it.  I think he's planning a rewrite so maybe it can be done then.

---

### Post by Aneurysm9 on 2006-10-29
Mlampard has just committed a changeset to g15daemon svn that makes the L1 key control display switching if g15daemon is started with the -s switch.  You can probably safely use this with my lcdproc driver but will be unable to use the lcdproc menu as L1 is set as the Enter key.  I'll look into allowing the keymapping for lcdproc to be specified in the config file when I get a chance.

---

### Post by FreakinSyco on 2006-10-30
I would love for an easy plugin for rythymbox that displayed current track info. Or just a more user friendly implementation of any part of the tools at this point.

---

### Post by Aneurysm9 on 2006-10-30
Check out the script in this post for a start: [http://ubuntuforums.org/showpost.php?p=928099&postcount=15](http://ubuntuforums.org/showpost.php?p=928099&postcount=15)  You should be able to fairly easily adapt that to output to g15composer.

---

