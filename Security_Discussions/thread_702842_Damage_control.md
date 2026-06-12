---
title: "Damage control"
date: 2008-02-20
forum: Security Discussions
---

### Post by RiazM on 2008-02-20
Eurgh, so, in my stupidity I failed to put a password on the remote desktop access, and my mother, thinking it was me trying to access the computer clicked allow for someone who was not me.

Allow the user to control the desktop was on and although she says she didn't notice anything, I'm understandably suspicious (Why didn't I just put a damn password on the thing?)

Anyway, do I need to reformat the entire system? My mother's account is certainly compromised so I deleted it and made her a new one, but is this enough?  Do I have to reformat the computer? If  so, are people ok logging onto their own users until I can do that?

(I'm not at home right now, so I would appreciate solutions that can be done over SSH)

Thanks guys, I'll be banging my head against that wall over there if you need me.

---

### Post by astrotech226 on 2008-02-20
One of the first things I'd do is check for a rootkit.
[URL="http://www.chkrootkit.org/"]
http://www.chkrootkit.org/[/URL]

Check your log files and look for the usual suspects, like users in your /etc/passwd file that have UID of "0" and are not "root".

---

### Post by euler_fan on 2008-02-21
Don't forget about rkhunter and clamav. Useful tools both. Make sure to run them with the machine not connected to the Internet (e.g. pull the cord out).

Unfortunately the *fastest* way to be sure nothing is wrong is to back up whatever you need to and reinstall.

Since it sounds like we're talking about a basic desktop setup (no fancy software installed from source, custom configurations, etc) it shouldn't take too long once the backups are done.

With respect to logging in as their own users, if I thought I was possibly compromised I would move sensitive files off the machine and boot a live CD to do things like banking, shopping, etc. until the machine is verified to be free from problems. If they do not have to be on the Internet, with the internet unplugged any attacker can't control your machine nor download things.

Another thing I've seen suggested is using Firestarter (on the computer) to set a restrictive *outbound *policy (inboud is *always* restrictive) white-listing only the services you know you need (80 for the web, various ports used by an email or IM client, etc). Then if any rootkit tries to "phone home" it will get stopped by the firewall (you hope).

---

### Post by FakeOutdoorsman on 2008-02-23
Make sure to take a look at the logs in /var/logs and anything (also hidden) in /tmp.  If you backuped your mom's hijacked account, then you should also run "history" (logged in her account) or look at her ~/.bash_history to see if they left any tracks there too.  You can also monitor the ip for spamming, harvesting, etc.  [Project Honeypot]("http://projecthoneypot.org") is great for that.  It can e-mail you when your monitored ip address(es) show up in the database of bad computers.

After rooting around the computer the safest thing to do would be to wipe the drive (Delete the old partitions in Ubuntu install or check out [DBAN]("http://dban.sourceforge.net/"). Easy to use ISO image and quick wipe.) and reinstall Ubuntu with **new** passwords.

---

