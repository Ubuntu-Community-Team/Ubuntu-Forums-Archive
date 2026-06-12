---
title: "clam - how can I keep it from doing anything but what I tell it to?"
date: 2016-01-26
forum: Security
---

### Post by Dreamer Fithp Apprentice on 2016-01-26
Once in a blue moon I want to scan something with Clam. I don't any part of it running in the background, autostarting, updating itself automatically, etc. I want it to stay completely dormant until I tell it to update itself and check a specific file or directory.

But whenever I install it, I everafter find some part of it running when I look in lxtask. I don't have clamav-daemon installed. I only have:
clamav
clamav-base
clamav-freshclam
libclamav6

but apparently clamav-freshclam has set itself up as a daemon. Is there a way to make it behave the way I want or must I purge it and reinstall it next time I want to use it?

This is under Trusty with plain Openbox.
--------------------------------------------------------------------
Added later:
I did this:```
sudo apt-get purge clam*
```Oh, just shoot me. It took a list of programs a mile long, none of which had "clam" in the name. Fortunately my lxterm saves a long enough history I can see what it did. I see no alternative to going down it line by line and re-installing them all. Why in the world would it purge all those programs? This may take hours.

---

### Post by deadflowr on 2016-01-26
Moved to ***Security*** sub-forum

You can alter the settings for clamav-freshclam, by running
```
sudo dpkg-reconfigure clamav-freshclam
```
with that, you can switch it from a daemon to something more manageable, like a simple cron job.

Hope it helps.

---

### Post by Dreamer Fithp Apprentice on 2016-01-27
Thank you, Deadflowr. I'll try that when I get it re-installed. I got the things the purge command above took re-installed. I still haven't a clue why it took things like fbreader for example. I looked in the package description in synaptic, properties, and at the names of all the depends (always seemed to me "prereqs" would be a better term). I even copied all that into a text editor and searched the string in case I was just being blind. The string "clam" does not appear, so wth? The only other possibility I can think of is that one of the depends in turn depends on something else that has clam in the name. I may never trust apt-get again. But I suppose that is another subject and belongs in another thread, if anywhere.  So, as a caveat to anyone finding this thread while searching for a solution to a similar problem, I should say I haven't TESTED it yet, and won't until I figure out some weirdness I'm seeing with apt-get, and get clam reinstalled, but I'll regard this as SOLVED

---

### Post by deadflowr on 2016-01-27
Note if you choose to setup a cron job, it'll place a file in /etc/cron.d called clamav-freshclam.
It'll set it with whatever connections you set for it.
The default is 24, so it'll run every hour.
Edit it if you want to set it more to your liking.

I set mine to 2, so it runs every 12 hours.
If I get paranoid, I can always run it manually; ala sudo freshclam

To each his own.

---

### Post by Dreamer Fithp Apprentice on 2016-01-27
Thanks. When I get back to it (I want to figure out this apt-get weirdness first) I'll come back to this thread to remind myself of your suggestions.  My intent is to stop ALL automatic actions re clam - to have it simply dormant on my HD until I tell it to update its database and scan a specific directory or file (which I'll combine in a script - and call the script from a thunar custom action). I don't use it often enough to allocate it any resources regularly. I'm trying to keep my system and my demands on bandwidth ultralight

---

