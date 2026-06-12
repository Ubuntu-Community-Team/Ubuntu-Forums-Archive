---
title: "Paranoid? SANS Says They're Out to Hack You"
date: 2007-11-28
forum: The Cafe
---

### Post by Sporkman on 2007-11-28
[http://seekingalpha.com/article/55627-paranoid-sans-says-they-re-out-to-hack-you?source=yahoo](http://seekingalpha.com/article/55627-paranoid-sans-says-they-re-out-to-hack-you?source=yahoo)

> 
**Paranoid? SANS Says They're Out to Hack You**

posted on: November 28, 2007

The SANS Institute report on the state of security circa 2007 is enough to make you want to pull your ethernet cord out. Is anything out there secure?

On Wednesday, the SANS Institute released its top 20 security risks update for 2007. It’s pretty bleak across the board. There are client vulnerabilities in browsers, Office software (especially the Microsoft (MSFT) variety), email clients and media players. On the server side, Web applications are a joke, Windows Services are a big target, Unix and Mac operating systems have holes, backup software is an issue as are databases and management servers. Even anti-virus software is a target.

And assuming you button down all of those parts–good luck folks–you have policies to be implemented (rights, access, encrypted laptops etc.) just so people can elude them. Meanwhile, instant messaging, peer-to-peer programs and your VOIP system are vulnerable. The star of the security show is the infamous zero day attack (here’s how to prevent them).

I’m feeling better how about you?

A few notable nuggets to ponder:

Your browser has too many friends. IE and Firefox are full of vulnerabilities. No surprise there. But part of the problem is rich Internet content–and all the plug-ins to go with it. SANs says:

With the explosion of rich content in web sites, a parallel increase has been seen in the number of Browser Helper Object and third-party plug-ins used to access various MIME file types such as multimedia and documents. These plug-ins often support client-side web scripting languages such as Macromedia Flash or Shockwave. Many of these plug-ins are installed (semi-)transparently by a website. Users may thus not be aware that an at-risk helper object or plug-in is installed on his/her system. These additional plug-ins introduce more avenues for hackers to exploit to compromise computers of users visiting malicious web sites.

Microsoft Office is under siege. We’ll let this vulnerability graphic do the talking:

[img]http://static.seekingalpha.com/uploads/2007/11/28/sans.png[/img]

Enterprise 2.0 is full of holes. SANS says:

Web-based applications such as Content Management Systems (CMS), Wikis, Portals, Bulletin Boards, and Discussion Forums are used by small and large organizations. A large number of organizations also develop and maintain custom-built web applications for their businesses (indeed, in many cases, such applications are the business). Every week hundreds of vulnerabilities are reported in commercially available and open source web applications, and are actively exploited. Please note that the custom-built web applications are also attacked and exploited even though the vulnerabilities in these applications are not reported and tracked by public vulnerability databases such as @RISK, CVE or BugTraq. The number of attempted attacks for some of the large web hosting farms range from hundreds of thousands to even millions every day.

When it comes to security Mac and Unix operating systems are very similar. Let’s hear it for reuse of hacks. “Most Unix/Linux systems include multiple standard services in their default installation. Mac OS X often suffers from the same vulnerabilities as Unix systems, since it is based on Unix,” says SANS. Configuration settings are very important.

Backup software is a target. This may be news to some folks since backup software usually just gets information pushed to it. However, backup systems need access to all files. Hackers can take advantage of these access privileges to infect an enterprise system. SANS says:

During 2007 many critical backup software vulnerabilities were discovered. Since the backup software generally runs with high privileges to read all files on a system, vulnerabilities in backup software have led to severe security vulnerabilities. Some of these vulnerabilities were exploited to completely compromise systems running backup servers and/or backup clients. Attackers leveraged these flaws for enterprise-wide compromise and obtained access to the sensitive backed-up data. Exploits have been publicly posted for many of these flaws, and these vulnerabilities are often exploited in the wild.

Anti-virus software is also a weak point because it’s an attractive target. Anti-virus software also happens to be installed everywhere. SANS says:

Multiple remote code execution vulnerabilities have been discovered in the anti-virus software provided by various vendors including Symantec, F-Secure, Trend Micro, McAfee, Computer Associates, ClamAV and Sophos. These vulnerabilities can be used to take a complete control of the user’s system with limited or no user interaction.

Anti-virus software has also been found to be vulnerable to “evasion” attacks. By specially crafting a malicious file (for instance, an HTML file with an executable header) it may be possible to bypass anti-virus scanning. These evasion attacks can be exploited to create a vector for malware propagation, or bypass systems that would otherwise limit malware propagation.

Comforting. Where’s that Ethernet jack again?


---

### Post by science4sail on 2007-11-29
"crack", not "hack" - we don't want the gnus to stampede us


this is why I use Linux

---

### Post by samjh on 2007-11-29
> **science4sail said:**
> "crack", not "hack" - we don't want the gnus to stampede us


this is why I use LinuxWhich won't do any better job at protecting you against user-level vulnerabilities than MacOS, Windows, BSD, or anything else.

---

### Post by beniwtv on 2007-11-29
Err... "Full of exploits"?

I think they should redo all the investigation work, but correctly this time.

While it's true that there are  "exploits" for many projects, services, OSes, hardly they can be exploited in a correctly configured system and environment.

There's a reason user privileges, iptables, routers, cisco firewalls, etc.. exist, isn't there?

---

### Post by plun on 2007-11-29
Well, I am not paranoid but.....  "bad memory" perhaps...:)

>  a) the servers, especially zambezi were running an incredible  amount of web software (over 15 packages[1] that we recognised)and  of all the ones where it's trivial to determine a version, they  were without exception out-of-date and missing security patches.   An attacker could have gotten a shell through almost any of these sites.

   b) FTP (not sftp, without SSL) was being used to access the
      machines, so an attacker (in the right place) could also have
      gotten access by sniffing the clear-text passwords.
 
   c) The servers have not been upgraded past breezy due to problems  with the network card and later kernels.  This probably allowed the attacker to gain root.


[https://lists.ubuntu.com/archives/loco-contacts/2007-August/001510.html](https://lists.ubuntu.com/archives/loco-contacts/2007-August/001510.html)

The world is filled with servers running old junk  which easily can be 
injected with malware exploits.

---

### Post by n3tfury on 2007-11-29
> **beniwtv said:**
> Err... "Full of exploits"?

I think they should redo all the investigation work, but correctly this time.

While it's true that there are  "exploits" for many projects, services, OSes, hardly they can be exploited in a correctly configured system and environment.

There's a reason user privileges, iptables, routers, cisco firewalls, etc.. exist, isn't there?

this is mostly true except it's like using a band-aid on a severed limb.

---

### Post by beniwtv on 2007-11-29
> **n3tfury said:**
> this is mostly true except it's like using a band-aid on a severed limb.

Agreed, but what I originally tried to say was that you can't just rely on the security of your system.

For example, in my company we use Linux servers, but we still have a Cisco Pix in front of them.

While we carefully maintain the security of each system, we also rely on external firewalls, to cut down the possibility of an exploit even more.

Also, the internal informations  of our customers aren't stored on a public server, nor they can be accessed from any public location, as any good company would do.

---

### Post by n3tfury on 2007-11-29
> **beniwtv said:**
> Agreed, but what I originally tried to say was that you can't just rely on the security of your system.

For example, in my company we use Linux servers, but we still have a Cisco Pix in front of them.

While we carefully maintain the security of each system, we also rely on external firewalls, to cut down the possibility of an exploit even more.

Also, the internal informations  of our customers aren't stored on a public server, nor they can be accessed from any public location, as any good company would do.

oh, trust me, i know what you mean.  i work for a top 30 forbes company and it's the same thing here.  Cisco makes up most of our barrier outside of our intranet.  there will always be some exploits within a given system, but as you said, if it's managed well  you'll have little, if any, problems.

---

