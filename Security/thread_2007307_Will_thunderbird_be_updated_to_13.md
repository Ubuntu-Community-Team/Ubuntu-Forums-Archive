---
title: "Will thunderbird be updated to 13?"
date: 2012-06-20
forum: Security
---

### Post by nrundy on 2012-06-20
Thunderbird 13 contains important security updates, yet I'm still at version 12.

How come no update? Where do I look to find out what's going on with Thunderbird updates on Ubuntu?

---

### Post by cariboo on 2012-06-20
Is this what you are referring to?

[http://www.ubuntu.com/usn/usn-1430-3/](http://www.ubuntu.com/usn/usn-1430-3/)

---

### Post by nrundy on 2012-06-20
mozilla shows vulnerabilities here: [https://www.mozilla.org/security/announce/](https://www.mozilla.org/security/announce/)

v13 fixed several vulnerabilities

---

### Post by uRock on 2012-06-20
If you really feel the need to upgrade to 13, then follow the directions [here.]("http://www.ubuntuupdates.org/ppa/mozilla_team_thunderbird_stable") I trust that the security issues in 12 will be fixed in their update for 12.

---

### Post by nrundy on 2012-06-21
> **uRock said:**
> If you really feel the need to upgrade to 13, then follow the directions [here.]("http://www.ubuntuupdates.org/ppa/mozilla_team_thunderbird_stable") I trust that the security issues in 12 will be fixed in their update for 12.

What do you mean "in their update for 12"? This is what I'm talking about. There hasn't been an update for 12.

---

### Post by cariboo on 2012-06-21
> **nrundy said:**
> What do you mean "in their update for 12"? This is what I'm talking about. There hasn't been an update for 12.

There is a link to the updated version of Thunderbird for all supported versions, in the [USN]("http://www.ubuntu.com/usn") I linked to. Go to the bottom of the page.

---

### Post by Dave_L on 2012-06-21
> **cariboo907 said:**
> There is a link to the updated version of Thunderbird for all supported versions, in the [USN]("http://www.ubuntu.com/usn") I linked to. Go to the bottom of the page.

> USN-1430-1 fixed vulnerabilities in Firefox and USN-1430-3 fixed vulnerabilities in Thunderbird. This update provides an AppArmor package with updated abstractions for use with the latest Firefox and Thunderbird.

I applied that update on 6/13. But I don't have an AppArmor profile for Thunderbird. Does that security note imply that Thunderbird should have its own AppArmor profile? Or is Thunderbird protected by the Firefox profile, or one of the others?

---

### Post by spynappels on 2012-06-22
My Thunderbird updated to 13 this morning, check for updated in Synaptic.

---

### Post by uRock on 2012-06-22
> **spynappels said:**
> My Thunderbird updated to 13 this morning, check for updated in Synaptic.

+1 12.04 has been upgraded.

---

