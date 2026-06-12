---
title: "spamassassin rules updating?"
date: 2010-08-23
forum: Server Platforms
---

### Post by Thijs Koetsier on 2010-08-23
Hi all,

This is a more or less a package-specific question, but since the only answers I can find all refer to different distro's and/or updating/editing by hand, I first wanted to check if there is an Ubuntu-way of fixing this.

Sorry if this already has been discussed someplace else; I couldn't find it.

I'm running the following configuration:
Linux version 2.6.31-22-server (buildd@yellow) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #61-Ubuntu SMP Wed Jul 28 02:58:50 UTC 2010

On this, I have installed Exim4, spamassassin and clamav all by normal package selections and some manual configuration.

Lately the spam on this mailserver is increasing. The sa-update for spamassassin does check for updates daily, the version is still the latest:

output for sa-update:
[9707] dbg: dns: 5.2.3.updates.spamassassin.org => 895075, parsed as 895075
[9707] dbg: channel: current version is 895075, new version is 895075, skipping channel


However, it 'seems like' the rules are not recent, since I get large amounts of spam coming through.

Does anybody know what I need to do to keep this setup updated so that it will tag spam like it used to do when I first installed the system?

Thanks in advance.

---

### Post by edkasky on 2010-08-24
What rulesets are you using?  If you are using just the default ruleset, you should consider at least adding the sought rules to your update channels.  They get updated daily and will certainly increase your accuracy.

cd /etc/mail/spamassassin
sudo wget [http://yerp.org/rules/GPG.KEY](http://yerp.org/rules/GPG.KEY)
sudo sa-update --import GPG.KEY
sudo sa-update --gpgkey 6C6191E3 --channel sought.rules.yerp.org

You should then compile the ruleset and then restart the daemon if you are running the daemon.

If that works for you, then add something like this as a nightly cron job:
sa-update -D --updatedir /usr/share/spamassassin/ --gpgkey 6C6191E3 --channel sought.rules.yerp.org && sa-compile && service spamassassin restart

You can tweak SA even further by adding all sorts of tools. If you haven at least read the FAQ at Spamassassin.org you should....

HTH...

Ed

---

### Post by Thijs Koetsier on 2010-08-24
Ed, 
Thanks a bunch!

---

