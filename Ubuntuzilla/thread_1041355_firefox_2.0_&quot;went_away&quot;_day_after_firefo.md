---
title: "firefox 2.0 &quot;went away&quot; day after firefox 3.0 install"
date: 2009-01-16
forum: Ubuntuzilla
---

### Post by rbpember on 2009-01-16
I just installed Firefox 3.0.5 following directions at [http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/). I heeded the warnings and left the old firefox in place so that Gecko based Gnome applications would still run. Today, after rebooting, firing up the old firefox brings up firefox 3.0:

%coot 4: which firefox
/usr/bin/firefox
%coot 5: which firefox-3.0
/usr/bin/firefox-3.0
%coot 6: /usr/bin/firefox -v
Mozilla Firefox 2.0.0.19, Copyright (c) 1998 - 2008 mozilla.org
%coot 7: /usr/bin/firefox-3.0 -v
Mozilla Firefox 3.0.5, Copyright (c) 1998 - 2008 mozilla.org
%coot 8:

When I fire up /usr/bin/firefox, however, it brings up firefox 3.0.5. I verified this under the "About Mozilla Firefox" Help menu item.

Is this something to worry about? I just don't something to break. I don't think I use use any Gecko-based Gnome apps, at least if I can trust what the Synaptic package manager reports when I search on "gecko"

---

### Post by nanotube on 2009-01-19
Hi
as long as everything's working fine, nothing to worry about. these gecko-based gnome apps don't actually use firefox itself, but the libraries that come with it. so don't worry about it.

that said, it is rather curious... :) are you using hardy?

could you post output of
```
ls -al /usr/bin/firefox
```

/usr/bin/firefox SHOULD be the link to the new v3 firefox, and the old v2 firefox should be /usr/bin/firefox.ubuntu... so /usr/bin/firefox should not be showing version 2.

---

### Post by rbpember on 2009-01-19
I am running gutsy, not hardy.

Here's the output you wanted:

%coot 2: ls -al /usr/bin/firefox
lrwxrwxrwx 1 root root 22 Dec 18 10:15 /usr/bin/firefox -> ../lib/firefox/firefox
%coot 3: 

> /usr/bin/firefox SHOULD be the link to the new v3 firefox, and the old v2 
> firefox should be /usr/bin/firefox.ubuntu... so /usr/bin/firefox should 
> not be showing version 2.

Here's what happened for me. The command

ubuntuzilla.py -a install -p firefox

put the new firefox in /opt/firefox/firefox. (I don't if the script gave me a choice in the location or not.)

I then made a link 

ln -s /opt/firefox/firefox /usr/bin/firefox-3.0

since I assumed it was important to leave /usr/bin/firefox around as the 2.X version.

---

### Post by rbpember on 2009-01-19
Now I understand what's happening:

We're in the process of bringing up a new website and we've been seeing different behavior under pre-3.0 and 3.0 Firefox. (This is our problem, not Firefox's). However, to try to understand the behavior, I've been running new and old side by side. This is evidently not possible. Whoever is running first determines which version runs when subsequent Firefox's are invoked. So if I fire up version 2, when I fire up version 3, it comes up as version 2. And vice versa. It's also a "local" phenomenon: if I kill off all Firefox's, I start over. 

For example, if I launch 2, then 3, 3 comes up as 2. If I kill both, and launch 3, 3 comes up as 3. If I keep 3 up and launch 2, 2 comes up as 3.

Why this should happen I have no idea, although it suggests some sort of cookie is being used. 

So 2.0 has not gone away at all. It's just that until now, I hadn't tried launching version 2 before version 3.

---

### Post by nanotube on 2009-01-19
aha i see

well, in case you care, you /can/ run ff2 and ff3 at the same time. look at the "--no-remote" command line argument for ff. when run with --no-remote, firefox does not try to detect if a firefox is already running, and instead just launches another copy. 

i'd also suggest running ff2 with a different profile than ff3 (since ff2 can have trouble swallowing ff3's profile, and, to a lesser extent, the reverse can be true as well). for this, look at the -P option, to specify the profile.

hope this helps. :)

---

### Post by rbpember on 2009-01-20
If either firefox is running, and Ithen  use -no-remote with either firefox, I get a pop-up saying:

Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.

So at least for me "-no-remote" does not seem to be an option for running 2 and 3 side by side.

---

### Post by nanotube on 2009-01-20
> **rbpember said:**
> If either firefox is running, and Ithen  use -no-remote with either firefox, I get a pop-up saying:

Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.

So at least for me "-no-remote" does not seem to be an option for running 2 and 3 side by side.

use a different profile too. it places a .lock file in the profile when it runs.

---

