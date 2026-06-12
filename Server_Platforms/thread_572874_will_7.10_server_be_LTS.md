---
title: "will 7.10 server be LTS?"
date: 2007-10-10
forum: Server Platforms
---

### Post by hcker2000 on 2007-10-10
Just curious is 7.10 server edition is going to be a Long Term Support release?

---

### Post by James79 on 2007-10-10
From wikipedia:

> During July 2007 at Ubuntu Live 2007, Mark Shuttleworth announced that Ubuntu 8.04 ( out April 2008 ) would be the next LTS (Long Term Support) release.

I'm waiting for the next LTS as well before reinstalling my 6.10 server :)

---

### Post by hcker2000 on 2007-10-10
I was hoping this was a LTS. I am running 5.10 and want to upgrade and do things right this time around.

I still think I am going to install 7.10 and then the next LTS in April if I need it.

---

### Post by primski on 2007-10-11
What about upgrading from LTS to LTS, which is what 4 versions apart? The old-fashioned dist-upgrade would take too much time, and quite frankly, there's a good chance something will break with 4 dist-upgrades...

so my question is, is there any LTS-TO-LTS upgrade tool? Considering a lot of (production) servers use 6.06 LTS and didnt want to dist upgrade through each release, but instead wait till the next LTS release.

---

### Post by Brazen on 2007-10-11
> **James79 said:**
> 

I'm waiting for the next LTS as well before reinstalling my 6.10 server :)

that's why you shoulda used 6.06 server.  Then you could have just dist-upgraded directly to 8.04

> **primski said:**
> What about upgrading from LTS to LTS, which is what 4 versions apart? The old-fashioned dist-upgrade would take too much time, and quite frankly, there's a good chance something will break with 4 dist-upgrades...

so my question is, is there any LTS-TO-LTS upgrade tool? Considering a lot of (production) servers use 6.06 LTS and didn't want to dist upgrade through each release, but instead wait till the next LTS release.

You can dist-upgrade directly from an LTS release to the next LTS release.  At least Canonical has promised you will be able to.  Their big money business customers are going to be dependent on this, so they better get it right.

Doing the dist-upgrade should be no different than dist-upgrading between regular releases, just change your sources from "dapper" to "hardy", then do "sudo aptitude update && sudo aptitude -y dist-upgrade".  Of course, this will be the first chance for people to do a dist-upgrade between LTS releases, so there is no historical data to attest to it's dependability.

---

### Post by MJN on 2007-10-11
> **Brazen said:**
> Of course, this will be the first chance for people to do a dist-upgrade between LTS releases, so there is no historical data to attest to it's dependability.

I can picture the scene...

"Go on... you first. Of course it'll be alright. I'll be right behind you...."

Mathew ;)

---

### Post by James79 on 2007-10-11
> **Brazen said:**
> that's why you shoulda used 6.06 server.  Then you could have just dist-upgraded directly to 8.04


I know.. I know.. I was young and stupid ;)

Hopefully once I get 8.04 installed I won't have to touch it again for 5yrs asides for applying security updates.

---

