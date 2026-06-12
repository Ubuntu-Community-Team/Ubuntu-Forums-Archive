---
title: "verifying integrity of system"
date: 2007-12-10
forum: Server Platforms
---

### Post by karl_kashofer on 2007-12-10
Hi all !

I wonder if there is some kind of integrity-check software in ubuntu that will verify the md5 hashes of all packages and files installed on my system, and give me a list of files that have been modified or added ?

I.e. something that like gets the .deb MD5's from the repository, then checks the .deb backup from apt, then md5's all files in the .deb and verifies if the installed files have the same md5 ?
It could then compile a list of all files on the system which have not been installed by apt, i.e. ones that can not be accounted for.

I know lots of /etc files would pop up, but the rest of the system should be quite static shouldnt it ?

Would this kind of auditing make sense ?

Thanks,
Karl

---

### Post by rufius on 2007-12-10
I've not heard of any software like this but I'm sure it could be done.

Though to be honest I'm not sure I'd see what warrants this. What kind of things are you looking for? Rootkits can easily be found by software you install. This kind of paranoia is a little over the top IMHO.

What would cause one to want to audit to this extent?

---

### Post by MJN on 2007-12-10
[Tripwire]("http://sourceforge.net/projects/tripwire/") does exactly this. There are also a [million more]("http://freshmeat.net/search/?q=tripwire&section=projects&x=0&y=0") (or so!) similar tools.

Check Tripwire out first though as it's widely used and somewhat of a benchmark in this area.

Mathew

---

### Post by karl_kashofer on 2007-12-10
> **MJN said:**
> [Tripwire]("http://sourceforge.net/projects/tripwire/") does exactly this. There are also a [million more]("http://freshmeat.net/search/?q=tripwire&section=projects&x=0&y=0") (or so!) similar tools.

Check Tripwire out first though as it's widely used and somewhat of a benchmark in this area.

Mathew

Well its not exactly the same, these just hash all files and check for changes. What I am thinking of is something different, it basically checks if any official ubuntu files have been changed and also if any files have been added. 
Its different in that it trusts ubuntu repos and does not need to do a snapshot of the "uncompromised" system.

Any other thoughts ?

Cheers,
Karl

---

### Post by MJN on 2007-12-10
Ah okay, afraid not.

Mathew

---

