---
title: "update caution"
date: 2015-03-23
forum: Ubuntu Development Version
---

### Post by kerry_s on 2015-03-23
anyone else see this upstart-bin update ?
i'm leaving it alone for now.

doesn't seem safe to remove.
upgrade is weird, it wants to install i386 packages, my install is amd64.

ubuntu 15.04
monday march 23

( sorry just woke up, brain still sleeping :) )

---

### Post by zika on 2015-03-23
[This]("http://ubuntuforums.org/showthread.php?t=2249915&p=13250967#post13250967") might be connected to Your question...

---

### Post by Elfy on 2015-03-23
> **kerry_s said:**
> anyone else see this upstart-bin update ?
i'm leaving it alone for now.

doesn't seem safe to remove.
upgrade is weird, it wants to install i386 packages, my install is amd64.

ubuntu 15.04
monday march 23

( sorry just woke up, brain still sleeping :) )

Wait for the archive to settle - said Adam Conrad

He also said - wait for apt to offer sane upgrade and see if synaptic is still weird


> [19:21] <infinity> elfy: It's confused.  Let the archive settle.
[19:21] <sarnold> stgraber: okay, thanks
[19:21] <stgraber> sarnold: the idea being that sha256sum <file> will match the hash used to refer to it after you import it into lxd
[19:22] <elfy> infinity: ok - I did wonder, but also got asked - thanks
[19:22] <infinity> elfy: That's a remarkably weird behaviour on apt's part, though.  I wouldn't have expected it to break differently. :P
[19:23] <infinity> elfy: Hrm, on mine, is just holds upstart-bin, which seems more sane.
[19:23] * mneptok has quit (Ping timeout: 246 seconds)
[19:23] <infinity> s/is/it/
[19:24] * greyback_ (~gerry@46.7.8.214) has joined #ubuntu-devel
[19:24] <elfy> infinity: apt seems to be doing it right, synaptic is playing games ... 
[19:25] <infinity> elfy: Oh, wow, people still use synaptic?
[19:25] * mneptok (~mneptok@mneptok.com) has joined #ubuntu-devel
[19:25] * mneptok has quit (Changing host)
[19:25] * mneptok (~mneptok@old-fart/mneptok) has joined #ubuntu-devel
[19:25] <elfy> infinity: they do ... 
[19:25] <infinity> elfy: Anyhow, once the archive has settled to the point where apt appears to offer a sane upgrade, can you cancel that and see if synaptic is happier too?
[19:25] <infinity> elfy: Should be another 30m or so at most, I'd think.
[19:25] <elfy> infinity: will do 
[19:25] * jibel has quit (Ping timeout: 246 seconds)
[19:26] <infinity> elfy: The sane upgrade, fwiw, should involve installing "upstart" as a new package, and otherwise just a bunch of upgraded packages.
[19:26] * greyback has quit (Ping timeout: 264 seconds)
[19:26] <infinity> elfy: Assuming it's a system with systemd-sysv installed.
[19:26] <elfy> infinity: it is 
[19:27] * rickspencer3_ (~rick@216-15-52-122.c3-0.nmex-ubr1.lnh-nmex.md.cable.rcn.com) has joined #ubuntu-devel
[19:27] <infinity> elfy: Right.  So, that's what the upgrade should look like when the archive settles.  Lots upgraded, and upstart new.
[19:27] * rickspencer3 has quit (Ping timeout: 272 seconds)
[19:27] <elfy> okey doke

---

### Post by kerry_s on 2015-03-23
> **zika said:**
> [This]("http://ubuntuforums.org/showthread.php?t=2249915&p=13250967#post13250967") might be connected to Your question...

so you ended up installing upstart ?

---

### Post by zika on 2015-03-23
> **kerry_s said:**
> so you ended up installing upstart ?> **zika said:**
> So, now, they learned to coexist (not to say cohabitate)
...
To clarify: no package was killed or harmed during this process and I did not intervene in any of these cohabitating efforts. Notice the difference from post of mine above......

---

### Post by kerry_s on 2015-03-23
> **Elfy said:**
> Wait for the archive to settle - said Adam Conrad

He also said - wait for apt to offer sane upgrade and see if synaptic is still weird

yeah, i'll check it later. it's just a habit to check for updates when i first turn on in the mourning, i saw safe to remove & i was like wait that don't seem right.

---

### Post by Elfy on 2015-03-23
> **kerry_s said:**
> yeah, i'll check it later. it's just a habit to check for updates when i first turn on in the mourning, i saw safe to remove & i was like wait that don't seem right.

basically I think there a few things expected to get through prior to the beta freeze later

---

### Post by kerry_s on 2015-03-23
> **Elfy said:**
> basically I think there a few things expected to get through prior to the beta freeze later

trust me i'm reading everything before i click continue. i'm just hopeful i don't end up with just a background & cursor, i kept having to reset with the 14 versions, so i just moved on to other de environments.

fingers crossed ;)

---

### Post by Elfy on 2015-03-23
The only thing here still waiting to upgrade is upstart-bin and it's requirements

---

### Post by Cavsfan on 2015-03-23
You can either wait or install from a new ISO. I believe all the major changes have been made as the final beta is released in 3 days on the 26th.

But the systemd/upstart issue is still up in the air as I have absolutely no way to boot into Upstart unless I did something which I refuse to do.

The new ISOs only have systemd so I am very curious as to which way this goes as final release is one month from today.

Will it be
[LIST=1]
[*]Sytemd as default with Upstart as backup? 
[*]Upstart as default with Systemd as backup? 
[*]Systemd only as those that installed on or after March 16th? 
[*]Or something else? 
[/LIST]

That is the big remaining question. Although there may be others that I'm unaware of.

---

### Post by grahammechanical on 2015-03-23
It is my understanding that when a package is described as "metapackage - safe to remove" it does not mean it will be removed by updating. Of course, it will be removed if we decide to remove it. Has anyone experienced metapackages being removed by the normal update process?

I fully expect some future update/upgrade to un-install all upstart connected packages. I think that they will remain in the archive for some time to come.

I also understand that when Synaptic marks a package with that grey exclamation mark it means that the package is due to be updated but is held back and that we can force the upgrade with Synaptic in the same way as running apt-get dist-upgrade.

Regards.

---

### Post by Elfy on 2015-03-23
> **Cavsfan said:**
> You can either wait or install from a new ISO. I believe all the major changes have been made as the final beta is released in 3 days on the 26th.

But the systemd/upstart issue is still up in the air as I have absolutely no way to boot into Upstart unless I did something which I refuse to do.

The new ISOs only have systemd so I am very curious as to which way this goes as final release is one month from today.

Will it be
[LIST=1]
[*]Sytemd as default with Upstart as backup? 
[*]Upstart as default with Systemd as backup? 
[*]Systemd only as those that installed on or after March 16th? 
[*]Or something else? 
[/LIST]

That is the big remaining question. Although there may be others that I'm unaware of.

mmm - what's this got to do iwith the issue at hand? 

we really don't need every thread to turn into a discussion about systemd do we?

---

### Post by Cavsfan on 2015-03-23
> **Cavsfan said:**
> You can either wait or install from a new ISO. I believe all the major changes have been made as the final beta is released in 3 days on the 26th.

But the systemd/upstart issue is still up in the air as I have absolutely no way to boot into Upstart unless I did something which I refuse to do.

The new ISOs only have systemd so I am very curious as to which way this goes as final release is one month from today.

Will it be
[LIST=1]
[*]Sytemd as default with Upstart as backup? 
[*]Upstart as default with Systemd as backup? 
[*]Systemd only as those that installed on or after March 16th? 
[*]Or something else? 
[/LIST]

That is the big remaining question. Although there may be others that I'm unaware of.

> **Elfy said:**
> mmm - what's this got to do iwith the issue at hand? 

we really don't need every thread to turn into a discussion about systemd do we?

Nope, it sure doesn't. I just thought that since the OP was talking about updating upstart-bin and you were mentioning systemd-sysv in your conversation with Adam Conrad that it already was about the boot options.  My bad. I'll go away now. I was going to post an update I just got but I'll go to the systemd thread.

---

### Post by Elfy on 2015-03-23
> **kerry_s said:**
> anyone else see this upstart-bin update ?
i'm leaving it alone for now.

doesn't seem safe to remove.
upgrade is weird, it wants to install i386 packages, my install is amd64.

ubuntu 15.04
monday march 23

( sorry just woke up, brain still sleeping :) )

Not sure what server you are using, Main here - all upgraded properly - upstart gets added.

---

### Post by kerry_s on 2015-03-23
> **Elfy said:**
> The only thing here still waiting to upgrade is upstart-bin and it's requirements

it should be good now, just did mine it installed upstart

---

### Post by kerry_s on 2015-03-23
> **Elfy said:**
> Not sure what server you are using, Main here - all upgraded properly - upstart gets added.

yeap all good now, guess i just checked to early in the mourning, next time i'll wait a day before asking.

---

### Post by Elfy on 2015-03-23
> **kerry_s said:**
> yeap all good now, guess i just checked to early in the mourning, next time i'll wait a day before asking.
Time doesn't make much difference :) 

I was pondering this at ~7pm :D

---

### Post by ventrical on 2015-03-23
It (upstart) installed just fine here about 2 hours ago.

---

