---
title: "nmap and &quot;bin.lua&quot; Lib-file?"
date: 2010-03-23
forum: Server Platforms
---

### Post by KennedyM on 2010-03-23
Hello,

Using 8.04 server, no GUI.

Just installed NMAP from the repos, and, later, LUA5.1 (for nmap scripting). When trying to run various nmap scripts (NSE files), or just something simple like:
```
nmap --script-updatedb
```to refresh the nmap BD file, I got numerous messages about missing LUA files in the Scripts and NSELIB folders. Eg, many NSE and LUA files have "require 'xxx'" statements, and many of these refer to missing NSE or LUA files. 

I downloaded most of the missing ones from the nmap website, but am still stuck on one specific LIB file - "bin.lua". And, this specific LUA file is referenced in many of the other NSEs and LUAs.

The LUA libs ([http://nmap.org/svn/nselib/](http://nmap.org/svn/nselib/)) contain a "bin.luadoc" file (and a "bit.luadoc" file), which I think is only a partial/skeleton LUA file. I've failed to find any proper "bin.lua" file anywhere.

I've never used NMAP before, and have not tried downloading/compiling the latest NMAP sources.

Any suggestions most welcome!
Thank you.
  - Mike.

[PS: just to make matters worse, it seems impossible to use any of the main search engines to locate just "bin.lua", because the embedded "." is ignored, and, AFAIK, cannot be ESCaped. Dang!].

---

### Post by KB1JWQ on 2010-03-23
[https://bugs.launchpad.net/ubuntu/+source/nmap/+bug/288358](https://bugs.launchpad.net/ubuntu/+source/nmap/+bug/288358) looks like it's been fixed.

You updated to the latest version?

I'm involved with doing some testing for the nmap project itself, so I tend to build from subversion.  Sorry. :-/

---

### Post by KennedyM on 2010-03-23
Thank you! WOW!!

> [https://bugs.launchpad.net/ubuntu/+s...ap/+bug/288358](https://bugs.launchpad.net/ubuntu/+s...ap/+bug/288358) looks like it's been fixed. I had seen that thread, and perhaps the issue has been fixed in very recent NMAPs in the repositories here, but, seemingly, not for 8.04 LTS.

> You updated to the latest version? The 8.04 is pretty up-to-date, and the NMAP is 4.53-3 (from the repos).

> I'm involved with doing some testing for the nmap project itself, so I tend to build from subversion. Sorry. :-/ OK. I'll have a "thunk" about that ;-), and probably dive in! I was not hopeful that a full compile would help, because lots of the NSE files (from lots of programmers) have that "require 'bin'" statement, and I expected that any solution would not have involved changing ALL these sources.

Incidentally, if I can help in any way with your testing (which, obviously, is unlikely!), let me know.

Thank you,
  - Mike

Edit:
I just noticed that the latest in the DEB repos is 5.00, and the latest stable in the main nmap SVN is 5.20. Do you recommend either over the other?. Thank you. M.

---

### Post by KB1JWQ on 2010-03-23
Join the nmap-hackers list.  Always room for more!

And yeah, that version you're running is ancient.  Grab the latest sources from subversion and build away; you'll be a lot happier for it, and scan performance will skyrocket-- a LOT Of fun changes happened after 4.76.

---

### Post by KennedyM on 2010-03-23
> Join the nmap-hackers list. Always room for more!

OK. Will do! And I had a very specific use for NMAP anyway (preferably with some of the SMB addons), but that's for another thread - either here or on that "list".

> And yeah, that version you're running is ancient. Grab the latest sources from subversion and build away; you'll be a lot happier for it, and scan performance will skyrocket-- a LOT Of fun changes happened after 4.76. Thank you! Sounds darn GREAT!!

  - Mike.

(Apologies for editing my previous post (re which version to use), before I saw your reply).

---

### Post by KennedyM on 2010-03-24
Just some feedback - I installed nmap 5.00 (as is available for Karmic), and about 8 updated "dependencies", and the BIN/LUA issues have been fully resolved.

Thank you for the above advice and encouragement...
  - Mike

---

### Post by KB1JWQ on 2010-03-24
I'm glad you've gotten it sorted out. ;-)

---

