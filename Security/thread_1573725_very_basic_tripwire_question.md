---
title: "very basic tripwire question"
date: 2010-09-13
forum: Security
---

### Post by methodtwo on 2010-09-13
Hi
Is there any need of storing tripwire and it's database on removable media?.Or would it be impossible for an attacker to hide the fact that they've messed with the tripwire database?.If there is a real need of storing on removable media, how would i set this up?.
Thank you very much for your time
regards

---

### Post by OpSecShellshock on 2010-09-13
It's probably best to keep it stored locally. Every time you make a legitimate change to the files you've got it set up to look at, you're going to need to reset your baselines, and with removable storage you're just introducing unnecessary complexity into the configured paths as well as creating the possibility that the storage device won't always be mounted during those legitimate changes. And for all that, there's not really any reduction of risk (because there wasn't really any risk to begin with).

Put another way, external storage that's mounted works pretty much the same way as the local disk, and the permissions for tripwire would have to be the same either way in order to use it.

Also, I'm having a hard time understanding where the threat is for something like this.

---

### Post by bodhi.zazen on 2010-09-13
> **methodtwo said:**
> Hi
Is there any need of storing tripwire and it's database on removable media?.Or would it be impossible for an attacker to hide the fact that they've messed with the tripwire database?.If there is a real need of storing on removable media, how would i set this up?.
Thank you very much for your time
regards

If you are concerned enough to set up tripwire, absolutely keep the database on a separate removable media. Of course an intruder could tamper with the local database.

---

### Post by anomie on 2010-09-13
@methodtwo: 

If you want legitimate intrusion detection on your system, technically the HIDS DB, the HIDS binary, any binaries used by it (and any linked libraries), and its config file(s) are all suspect during a check. 

As an alternative to using removable media (i.e. because you want an automated solution), I follow an approach something like: 
[list=1]
[*] A central HIDS server logs in to various remote hosts to initialize their HIDS DBs. It also captures cryptographic hashes for various binaries / config files (mentioned above). 
[*] At check time, the central HIDS server verifies hashes for each remote host, and then performs its usual HIDS check against the "known good" DB. 
[/list]

Of course, you could just go for a distributed HIDS for the same effect. (But I tend to roll my own utilities.)

---

