---
title: "Should we use apparmor for every application (rhythmbox, acrobat reader, ...)?"
date: 2011-10-01
forum: Security
---

### Post by newhere_m on 2011-10-01
Do we need in principle, to use apparmor for each application like rhythmbox/totem, acrobat reader, evince and so on? In case we do, it would be better if ready profiles for such applications were available. While one can certainly write suitable profile for personal use, it becomes a time consuming job. What do you think?

---

### Post by CharlesA on 2011-10-01
The problem with "ready-made" profiles is that they would have to be configured for each individual.

I would only confine stuff like Firefox or services such as apache with apparmor.

---

### Post by Dangertux on 2011-10-01
You should run apparmor profiles for applications that you use frequently that can accept user input either locally or remotely.

Examples would be

- Firefox
- Chrome
- Rhythmbox
- XChat
- Libre Office
- Reader, Evince etc

Anything that can accept input can be vulnerable so it is wise to contain it with apparmor.

That being said premade profiles can be very helpful as most of the time premade profiles are written with variables such as {HOME} or {PROC} instead of defined paths, so that they may be transferrable between different users.

If you are looking for premade profiles there are quite a few at these resources.

Bodhi.zazen's blog - [http://bodhizazen.net/Tutorials/aa](http://bodhizazen.net/Tutorials/aa)
OpenSuSe Apparmor Profile Repository : [http://apparmor.opensuse.org/profiles/find_by_name](http://apparmor.opensuse.org/profiles/find_by_name)

Hope this helps.

---

### Post by Porcini M. on 2011-10-01
On a related note, Qubes OS proposes confining each application within its own hypervisor.

---

### Post by bodhi.zazen on 2011-10-03
> **newhere_m said:**
> Do we need in principle, to use apparmor for each application like rhythmbox/totem, acrobat reader, evince and so on? In case we do, it would be better if ready profiles for such applications were available. While one can certainly write suitable profile for personal use, it becomes a time consuming job. What do you think?

Personally I confine all applications that connect to the internet.

Most of them are rather trivial to write a profile for.

> **CharlesA said:**
> The problem with "ready-made" profiles is that they would have to be configured for each individual.

I would only confine stuff like Firefox or services such as apache with apparmor.

Yes, this is the problem with apparmor and selinux, how to balance a restrictive set of security rules with usability.

Just when you get it sorted out, the developers change the package names or locations =)

It is difficult to confine large applications such as firefox and usage of firefox varies greatly.

---

