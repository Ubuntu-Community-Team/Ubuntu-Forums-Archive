---
title: "Dan's Guardian &amp; Warty?"
date: 2005-02-14
forum: Server Platforms
---

### Post by Mark Rawlings on 2005-02-14
Hi Folks,

Although I've been a Redhat user (although not admin) for a long time, I thought I'd give Ubuntu Warty a whirl (I got sick of rpm) - please consider me a near-newbie for advice purposes. 

Things are mostly wonderful so far, although I have a lingering headache:

I'm trying to make the machine kid-friendly, & came across an excellent article on setting up Dan's Guardian at:

[http://software.newsforge.com/article.pl?sid=04/06/23/1521209](http://software.newsforge.com/article.pl?sid=04/06/23/1521209)

Most of this applies quite nicely to Ubuntu, & is more readable than the work-in-progress paper currently mentioned in the Ideaspool. Maybe you could even use it as a template for an Ubuntu HOWTO. However...

While I've successfully managed to configure both Squid & Dan's Guardian as specified, I can't seem to make the iptables settings stick after a machine restart. Part of this is that there's no chkconfig for Ubuntu (see the "Putting It Into Action" section of the above article), but I've also tried putting the suggested iptables settings, restart commands, & so on into a startup script in /etc/init.d using update-rc.d. The filtering works beautifully if I sudo the script from the command line after login, but it doesn't appear to work before then.

The script is as follows:

iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner squid -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 3128 -m owner --uid-owner squid -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-ports 8080
iptables -t nat -A OUTPUT -p tcp --dport 3128 -j REDIRECT --to-ports 8080
iptables-save > /etc/sysconfig/iptables
iptables restart
squid restart
dansguardian restart

(Which runlevel should it be at, by the way, if I basically want it to run as late as possible?) Also note that I had to create /etc/sysconfig/ by hand, as it wasn't present under my stock Ubuntu installation.

I've set the script up with the same permissions, owner & group as everything else in the /etc/init.d directory, & done

update-rc.d MYSCRIPT start 

I also read that there was a problem with restarting some versions of iptables after a reboot, so I installed the recommended fixed version in the security announcement, but it didn't solve my problem.

(Incidentally, I have shorewall installed, but not configured to run, & I have firestarter installed as well, but I've switched it off while attempting to debug the above. I wanted to keep things simple & just use iptables if possible).

Any help would be greatly appreciated, as I'm getting nagged by the kids for web access!

---

### Post by mendicant on 2005-02-14
Usually, update-rc.d takes more arguments than that:

% update-rc.d <script> defaults 99

---

### Post by Mark Rawlings on 2005-02-14
Thanks - OK, I'll try that tonight.

I might also try uninstalling Firestarter, as I've just read here in the forums that it's really just a glorified configuration front-end for iptables, & I don' t want it to further complicate the script settings.

I'll let people know if I get it working...

---

### Post by Mark Rawlings on 2005-02-14
Hi again,

Aha - it seems to work. I first used Synaptic to do a full removal of shorewall & Firestarter, then removed my script from the startup sequence, then re-added it as per your advice, & tried a reboot. Hey presto - it worked! Thanks again!

---

