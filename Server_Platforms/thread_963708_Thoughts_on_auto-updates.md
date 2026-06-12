---
title: "Thoughts on auto-updates"
date: 2008-10-30
forum: Server Platforms
---

### Post by stonneway on 2008-10-30
HI chaps

I'm an intermediate ubuntu server bod, happy to describe myself as a Windows Man :)

I'm setting up a public facing svn/trac server for a client and we are debating the pros/cons of auto-updates, particularly kernals ones. 

Now, for the most part, I prefer manual updates scheduled for once a week/month etc, particularly kernal ones. I almost veer towards saying that if everything is working then only critical updates should go on, and the security layer should be handled by a hardware & application firewall.

However, the client comes from using things like SME Server and Clark Connect which have easy auto update features and is keen to set everything to "Auto update, all the time!".  

What's does the collective mind think about autoupdates? Should they be done regularly using something like "aptitude safe-upgrade" ? 

I'm worried about putting on an updated version of php/apache/mysql/imagemagick etc that has a knock on effect on another application. Sometimes even minor revisions can have a knock on effect. I'm *definately* worried about the server just applying distribuition or even kernal updates on it's own.

Hit me with your thoughts.

Olly

---

### Post by cdenley on 2008-10-30
On a server, I follow [security notices]("http://www.ubuntu.com/usn/") and install updates only when there is a remote security flaw that affects my server. I usually don't worry about local security flaws unless I'm doing maintenance anyway, but local flaws can allow an attacker to escalate privileges if they do manage to gain remote access. I don't update automatically, because there is a very small possibility that something can go wrong, and I want to be there to fix it. Also, kernel updates require a restart before they take effect.

If you use something like "apt-get upgrade", disable everything in /etc/apt/sources.list except security updates.

---

### Post by Thirtysixway on 2008-10-30
Personally I would like having auto-updates, the only thing that's ever broken my server in the past was doing an upgrade to a new version of Ubuntu.  I don't have auto updates enabled just because it gives me an excuse to ssh into my server, but I'd recommend just security updates.

---

### Post by Vegan on 2008-10-30
I put the following into a bash script

sudo apt-get update
sudo apt-get upgrade

and stuffed it into the cron folder and made it executable.

It is in the weekly folder, and this means I can go back to sleep until the server breaks. I wish.

:guitar:

---

### Post by lykwydchykyn on 2008-10-30
I use cron-apt to script automated updates, but only on non-critical servers.  If you're using the LTS version (hardy), don't enable the update, proposed, or backports repos, then theoretically you should only get security updates which are designed to be minimally disruptive while addressing patched security flaws.

Installing a new kernel will not affect anything, as it won't take effect until reboot and Ubuntu has no "feature" to auto-reboot after upgrade (thank heavens).

---

### Post by stonneway on 2008-10-31
So, if i just remove everything except the following lines from /etc/apt/sources.list ?

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

That will give me just security updates?

Wont removing all the other lines prevent me from doing 'apt-get install...' ?

Olly

---

### Post by lykwydchykyn on 2008-10-31
There's no reason to remove the main set of repositories.
Actually, there's probably no reason to remove any lines.  You can set up your script to specifically pull from the security repos only, IIRC.  

Something like:
```

aptitude dist-upgrade -t ubuntu-security

```
Might work.


The line I'm using in cron-apt looks like this (though I'm not just doing security updates):

```

dist-upgrade -y -V -u -o Dpkg::Options::=--force-confold

```

You definitely want that -o Dpkg::Options bit in there, because otherwise it's likely to overwrite config files with defaults.

---

### Post by lykwydchykyn on 2008-10-31
EDIT: doh!  Double post.

---

