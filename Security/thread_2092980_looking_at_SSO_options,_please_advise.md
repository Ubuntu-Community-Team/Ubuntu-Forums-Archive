---
title: "looking at SSO options, please advise"
date: 2012-12-09
forum: Security
---

### Post by teryret on 2012-12-09
Hello all!  I hope you're all having a most excellent day.

I'm working on a proposal to introduce a SSO system at my lab, but I'm an AI guy and I'll be the first to admit that I'm no expert at admin-y sorts of things... unless you compare me to my coworkers, in which case I am an expert.  Anyway any sort of advice you'd care to share would be greatly appreciated.

Right now we've got a few servers running RHEL, some various shared laptops running older versions of Fedora, and a bunch (10 or so) of high end 'buntu 12.04 workstations.  At the moment each machine has its own set of users, so changing a password involves touching more than a dozen boxen.  This is silly.

Moreover, because I came to the lab from the real world, I'm painfully aware of how lousy passwords are even when they're done right.

My ideal solution would be based on public keys so that passwords need only be changed on the private keys, but there are still some questions I don't have answers to:
[LIST=1]
[*]How do I get authorized the first time I log into each machine?
[*]Are there higher level administration tools for such a setup?
[*]Is this dumb for some reason that I don't yet understand?
[/LIST]

Are there better options?  I've vaguely aware that people use LDAP or Kerberos for these sorts of things, but I don't have a clear high level picture of what that looks like.  Can either of these be used in a mode where authorization lists can be cached (so as to be server/ISP crash tolerant)?

Is there a way that I can have different sets of sudoers on each workstation?

Thanks for all your help!

---

### Post by Ms. Daisy on 2012-12-11
> **teryret said:**
> Right now we've got a few servers running RHEL, some various shared laptops running **older versions of Fedora**, and a bunch (10 or so) of high end 'buntu 12.04 workstations. How old exactly?

---

### Post by teryret on 2012-12-11
It varies from machine to machine, targeting FC14 is probably a safe minimum version.

---

### Post by Ms. Daisy on 2012-12-11
OK, well you want to avoid using releases that are EOL. [http://fedoraproject.org/wiki/End_of_life](http://fedoraproject.org/wiki/End_of_life)

There's no point in worrying about SSOs if you don't keep your software updated.  Once you have upgraded all your boxes to operating systems that are supported and have applied all the available patches, then you can worry about SSOs.

---

### Post by teryret on 2012-12-11
Perhaps I'm using the wrong terms.  The lab's router is configure to reject all incomming, I'm not worried about security.  It's a conveince thing, I want to centralize user management so that people don't have to worry about setting up an account on each machine.  This has to be something that has been solved so thoroughly that specific versions of linux don't matter... right?

---

### Post by Ms. Daisy on 2012-12-11
> **teryret said:**
> I'm not worried about security. Why did you post the question in the Security Discussions Forum then? ;)

Yes, there are a myriad of solutions out there. I recommend that you Google SSO and research each of the options. I presume that you would want the most user-friendly, all the solutions I know require advanced knowledge of security and permissions (which you've said you're not interested in, therefore we can eliminate them). Your best and quickest route to your destination is to just try out the solutions you find in Google and see which you like.

---

### Post by CharlesA on 2012-12-12
The OP could set something like LDAP, but that can get messy.

---

### Post by OpSecShellshock on 2012-12-12
> **CharlesA said:**
> The OP could set something like LDAP, but that can get messy.

That's sort of what I was thinking. OpenLDAP for regular every day user authentication and then separate local accounts on systems for specific people who need to elevate privileges on specific devices. Still seems pretty unwieldy though. I think you'd still have to get hands on the server and each of the clients, at least for the initial setup, which doesn't actually solve very many problems at all.

---

### Post by CharlesA on 2012-12-12
> **OpSecShellshock said:**
> That's sort of what I was thinking. OpenLDAP for regular every day user authentication and then separate local accounts on systems for specific people who need to elevate privileges on specific devices. Still seems pretty unwieldy though. I think you'd still have to get hands on the server and each of the clients, at least for the initial setup, which doesn't actually solve very many problems at all.

That's what I was thinking as well, but it would probably be more of a pain in the butt than actually creating local users.

---

### Post by teryret on 2012-12-12
So what would LDAP look like?  If the server was down would we all be locked out?  Would it allow us to ssh around using key pairs instead of passwords?

---

### Post by Ms. Daisy on 2012-12-13
> **teryret said:**
> So what would LDAP look like?  If the server was down would we all be locked out?   You would still have local accounts on the individual boxes so it would probably look a lot like it does right now if the LDAP server went down.

---

### Post by teryret on 2012-12-17
Rats.  Oh well.  Thanks for your help, all.

---

