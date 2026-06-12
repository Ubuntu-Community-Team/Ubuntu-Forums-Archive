---
title: "TOR, polipo, and apparmor"
date: 2010-03-23
forum: Security
---

### Post by a.walker on 2010-03-23
Does using TOR / polipo open up any security vulnerabilities in an otherwise standard install of ubuntu-desktop? 

Is it worthwhile to try to generate an apparmor profile for polipo? I noticed that the a quick search for "security vulnerabilities polipo" yielded some posts about DOS vulnerabilities.

I'm just curious about any possible security problems related to using TOR.


I also have a more general question...

Who generates custom apparmor profiles for applications on their computers? 
What applications should be protected with an apparmor profile?

---

### Post by trideceth12 on 2010-03-23
I'm not an expert, but I use tor and as I understand it, it is possible for people hosting the exit servers (or whatever they're called) to harvest the information routed through them, such as form data.

I'd like to know the facts from someone with expert info.

---

### Post by Soul-Sing on 2010-03-23
You could read this FAQ: [https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#AnonymityAndSecurity](https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#AnonymityAndSecurity)
Roger Dingledine the leader of the Torproject (afaik til 2009) gave a lecture about the "Security and anonymity vulnerabilities in Tor"
: [http://events.ccc.de/congress/2008/Fahrplan/track/Hacking/2977.en.html](http://events.ccc.de/congress/2008/Fahrplan/track/Hacking/2977.en.html)
Must be said a rather old linkage, but imho still important.
core dangers TOR:
- dangerous Exit-Nodes
- DNS-leaking
- be sure using TOR is just one of many steps to protect your privacy, don't think TOR has anything to do with security.

---

### Post by rookcifer on 2010-03-23
I don't think the above two posters understood your question, OP.  I think what you are asking is whether the mere use of Tor on your machine can open up security holes (after all, Tor is essentially a server listening to the world).  The answer is that, yes, it theoretically could cause security issues locally on your machine.  Anytime you have listening services this could potentially be an issue if the service itself is exploited somehow.

I personally have generated AppArmor profiles for Tor and Polipo.  I will post them below if you want to try them out.

Polipo profile (usr.bin.polipo):

```
#include <tunables/global>

/usr/bin/polipo {
  #include <abstractions/base>
  #include <abstractions/nameservice>

  /etc/polipo/* r,
  owner /var/log/polipo/polipo.log w,
  owner /var/run/polipo/polipo.pid w,

}
```

Tor profile (usr.sbin.tor):

```
#include <tunables/global>

/usr/sbin/tor {
  #include <abstractions/base>
  #include <abstractions/nameservice>

  capability setgid,
  capability setuid,

  /etc/tor/* r,  
  /usr/share/tor/* r,
  owner /var/lib/tor/* rwk,
  owner /var/log/tor/* w,
  owner /var/run/tor/tor.pid w,

}

```

---

### Post by justanothergreysky on 2010-03-24
> **rookcifer said:**
> I think what you are asking is whether the mere use of Tor on your machine can open up security holes (after all, Tor is essentially a server listening to the world).  The answer is that, yes, it theoretically could cause security issues locally on your machine.  Anytime you have listening services this could potentially be an issue if the service itself is exploited somehow.

TOR should be restricted to listening only on the localhost interface by default, which reduces the security risk from this particular issue.

I haven't heard of notable security issues opened up by TOR, except the obvious examples that the usage of TOR can allow (or solicit) additional scrutiny of your traffic (albeit anonymously), through exit nodes, etc.

---

### Post by Ijan on 2010-03-24
> **a.walker said:**
> Does using TOR / polipo open up any security vulnerabilities in an otherwise standard install of ubuntu-desktop?

I  don't know if I got correctly wheather your question was more general or more regarding practical issues, I might add to the above: Not in principle but of course there could be bugs found and exploited in Tor. Make sure to run an up-to-date version downloaded from a credible source. 

If you want to make extra sure you can of course also check the mailinglist and changelogs for error reports [[here](http://archives.seul.org/or/announce/) or even monitor the bug reports.

---

