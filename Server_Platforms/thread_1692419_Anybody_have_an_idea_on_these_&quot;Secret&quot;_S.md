---
title: "Anybody have an idea on these &quot;Secret&quot; Samba features?"
date: 2011-02-21
forum: Server Platforms
---

### Post by headvampyre@hotmail.co.uk on 2011-02-21
Hi,
  ive recently been reading through Samba3 HOWTO and in Chapter 4 is stumbled upon this:
Samba ADS Domain Control

Samba-3 is not, and cannot act as, an Active Directory server. It cannot truly function as an Active Directory PDC. **The protocols for some of the functionality of Active Directory domain controllers has been partially implemented on an experimental only basis. Please do not expect Samba-3 to support these protocols. Do not depend on any such functionality either now or in the future. The Samba Team may remove these experimental features or may change their behavior. This is mentioned for the benefit of those who have discovered secret capabilities in Samba-3 and who have asked when this functionality will be completed.** The answer is maybe someday or maybe never!

So, anybody know about some of these, im getting bored of my Samba3 NT test environment and would like to find more out about this.

---

### Post by HermanAB on 2011-02-21
Download the source code and read it.

No I'm not being flippant.  Read the source code.

---

### Post by cariboo on 2011-02-21
You could always try Samba 4 :)

---

### Post by headvampyre@hotmail.co.uk on 2011-02-21
Okay, imma browse the source code later tonight, and as for Samba4 - im currently running it, but im starting to get annoyed that the current GIT repo is kinda messed up, really messed up :( it took 13 reinstalls to actually get TLS certificates to match the key, and samba-tool is missing a lot of libraries, and i just wanted to explore some more of Samba3 :)

---

### Post by headvampyre@hotmail.co.uk on 2011-02-21
Okay, ive browsed through the source files, and it appears that Samba3 can only act as a server in AD, would that be 100% correct? it also appears that with some modification to the source it would be possible to configure SAM to connect to LDAP via ADS mode, therefore hosting AD via samba3. Do you think any of this would be possible?

---

