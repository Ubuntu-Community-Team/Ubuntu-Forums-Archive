---
title: "RDS and Resara Server"
date: 2013-01-28
forum: Server Platforms
---

### Post by crispy_420 on 2013-01-28
I'm just wondering if anyone has had any luck getting Resara Server (rds package) running on a current version of Ubuntu, preferably LTS. From what I gather they had to compile a custom samba4 to get it working for their prebuilt ISO installer. I works fine but it was built on top of 10.04 I think and support time is running thin.

The packages install fine but setup fails because it cannot find lots of dependencies and files. The main issue seems to be with provisioning samba4. That may go back to the whole having to custom compile. I can't find any good documentation (the original company went under) and searches haven't got me very far.

What I ultimately need is an ldap server that is Active Directory compatible. It needs minimal administration ability and the Resara Console would be perfect. Basically the only thing the local people would be needing are covered in said console tool.

So anyone got a clue or use this server? If it is just essentially dead project I am willing to accept that and move on. But if so what have other users had luck with for an AD replacement that is simple for the end user and provides a GUI to manage? This is for someone else so I need to keep it simple.

---

### Post by binary_dreamer on 2013-02-02
i am having problems with the resara (original ISO) ubuntu 10.04.
it installed without problems. my domain is binary.dreamer and it runs in win xp PCs.
after configuring the shares i am not able to login again to the console and i have lost everything.
is there an issue? shall i proceed to someother installation? 

My setup it needs all the users to have its own folder, load its profiles (especialy a softphone called zoiper, profile). the users will not be sitted in the same PC everyday, so the profile needs to be portable from the PDC

---

### Post by crispy_420 on 2013-02-03
I'm starting to just assume that Resara is a dead project. Too bad, it could have been promising.

---

### Post by binary_dreamer on 2013-02-03
Is there an alternative? i do not like windows AD, also its price is extremely high

---

### Post by cariboo on 2013-02-03
> **crispy_420 said:**
> I'm starting to just assume that Resara is a dead project. Too bad, it could have been promising.

It is, see [here]("http://www.resara.org/"). Seeing as it is open source though, anyone can grab the source, and update it themselves.

---

### Post by crispy_420 on 2013-02-05
I knew it was dead in that respect but the packages are in the current repos but in an essentially broken state. They still seem to be in 13.04 repos as well, broken and all. I could understand stagnant but working but why keep it around if it does not work at all?

Also I don't think open sourced it all, like the custom tweaks to get samba4 working.

So any other suggestions for a simple to use AD replacement?

---

### Post by binary_dreamer on 2013-02-09
i would like to ask since i am stuck. I would like to load the settings of zoiper (softphone). everytime the user logs in into the pc, it will load the drive share and i cannot make it take the profile of the program.
i get a normal login it brings me the drive that is allocated to my login, but not the config of this program. any ideas?

---

### Post by crispy_420 on 2013-02-10
Honestly have never used that program. Maybe a new thread would be best instead of being buried deep in this one.

---

