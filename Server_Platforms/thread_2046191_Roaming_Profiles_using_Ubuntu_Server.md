---
title: "Roaming Profiles using Ubuntu Server"
date: 2012-08-22
forum: Server Platforms
---

### Post by cbarron on 2012-08-22
I am trying to setup Roaming profiles for about 100 Windows users (yeah I know bad word)
I would like to use ubuntu to manage the roaming profiles.
I have read several different ways of doing this with no real answer as to how to make it work right.
Any one here have ideas/experience with this type of setup?

---

### Post by LHammonds on 2012-08-22
Even with a 100% Windows network, I don't know how to make roaming profiles work without problems.  It has never worked well for me and I've been avoiding it.

A workaround that works fairly well in place of it is the 'ol trick of setting up a desktop how you want everyone setup and copying that user's profile to the default profile.  Anyone new to that machine will get the pre-configured desktop.

We also re-direct My Documents and the office applications save locations to their personal network drive letter.

We try to make sure nobody saves anything to the PC's hard drive that they don't mind losing.

LHammonds

---

### Post by cbarron on 2012-08-23
That is a good idea.
But we have about 50 employees that can and will switch computers sometimes on a daily basis. What we are trying to keep from happening is me touching each computer every time we get a new employee or lose an employee. That is why I thought roaming profiles would be easier to manage while still letting the EU customize their desktop experience.

Any other Ideas?

---

### Post by koenn on 2012-08-23
In so far that Roaming Profiles are just Windows file shares, a linux server with samba can be used for the sharing, AFAIK.
You probably will want samba to authenticate against MS Active Directory, and posix ACL might help to get the permissions right - Windows is very finicky when it coms to ACL on user profiles. 


Contrary to LHammonds' experience, my experience is that roaming profiles work well for the use case you describe, and folder redirection is a bit hit and miss. On Win XP, at least.

On Windows 7/Windows 2008 server, Folder redirection works quite well (and MS recommends it over roaming profiles), but the "offline files" feature that usually goes with it seems to act up a bit too often.

---

