---
title: "One SSH command to multiple servers"
date: 2015-10-08
forum: Ubuntu, Linux and OS Chat
---

### Post by rkillcrazy on 2015-10-08
Strange question....  Been Googling around and I'm either not querying the right term or I'm just really unlucky.  Anyway, I used to use SuperPUTTY to manage a lot of our Ubuntu machines.  I've seen many other Putty connection managers and that's not really what I'm after per se.  I'm after the feature that allows me to send one command to multiple servers I'm SSH'd into.  Anyone ever use that feature and, more importantly, anyone ever find that feature in other apps?  I'm looking for a replacement...

---

### Post by Lars Noodén on 2015-10-08
I used to use KDE's Konsole for that.  You could open multiple tabs and then send keystrokes to all of them.  I don't need the function so much these days and so get by with tmux for that via it's synchronize panes function.  If you have a large number of machines you might look into using something like Ansible instead.

---

### Post by rkillcrazy on 2015-10-08
I mostly used SuperPutty to do periodic maintenance for small groups of servers.  With more experience with Ubuntu's Gnome and Unity desktops, I did not know Konsole had the ability to hit multiple SSH sessions with one command.

---

### Post by Old_Grey_Wolf on 2015-10-08
Look at [ClusterSSH]("https://www.linux.com/learn/tutorials/413853:managing-multiple-linux-servers-with-clusterssh") (cssh) it is in the repository.

Man page at [http://manpages.ubuntu.com/manpages/vivid/en/man1/cssh.1p.html](http://manpages.ubuntu.com/manpages/vivid/en/man1/cssh.1p.html)

---

### Post by rkillcrazy on 2015-10-08
> **Lars Noodén said:**
> I used to use KDE's Konsole for that.  You could open multiple tabs and then send keystrokes to all of them.  I don't need the function so much these days and so get by with tmux for that via it's synchronize panes function.  If you have a large number of machines you might look into using something like Ansible instead.

Just a note for anyone else...  I tested this in Kubuntu 15.04 and it works just fine.  (Side note: It's been a while (2009-2010) since I last saw Kubuntu and I have to admit, at first glance, it looks much nicer than it did before.  I recall the Plasma desktop just *being in my way* more often than not.)  Anyway, I also tried this in an Ubuntu daily build (because I already had one set up) and I could not get it to work.  I'm pretty sure the terminal app in Ubuntu doesn't share this feature with Konsole even though you can get it to open additional terminal screens as tabs.  To get it to work in Konsole, go to **Edit** > **Copy Input To** > **All Tabs in Current Window** or you can select certain tabs.  It seems to reset every time you close and reopen Konsole...

---

