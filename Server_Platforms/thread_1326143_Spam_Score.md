---
title: "Spam Score"
date: 2009-11-14
forum: Server Platforms
---

### Post by prsjm3qf on 2009-11-14
Hi All,
New to Ubuntu from other distros. I'm really impressed that everything works as it should and as documented - this is a first for me. Ubuntu 9.10, a most excellent distro.

One minor niggling problem.

My postfix/amavis/clamav/spamassassin/squirrelmail setup. I cannot get the spam threshold to change from the (seeming) default of 6.31 to the published value of 5.0.

I've searched every config file I can find and I can't find the value 6.31 and every setting I can find is already 5.0.

Other changes I make to the config files seem to be applied OK.

Is the 6.31 a composite value calculated from a number of sources?

Where is it coming from and how do I change it.

I suppose I could set the spamassassin score to 4.0 and see if it produces 5.31 but that may have unintended consequences.

Thanks for any pointers.


APOLOGIES.

Me being stupid. Found it. /etc/amavis/conf.d/20-debian_defaults

$sa_tag2_level_deflt = 5.00; # add 'spam detected' headers at that level  (changed from 6.31)
$sa_kill_level_deflt = 5.00; # triggers spam evasive actions (changed from 6.31)

---

