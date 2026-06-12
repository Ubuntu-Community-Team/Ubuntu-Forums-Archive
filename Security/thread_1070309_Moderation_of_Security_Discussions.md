---
title: "Moderation of Security Discussions"
date: 2009-02-15
forum: Security
---

### Post by bodhi.zazen on 2009-02-15
There has been some discussion amongst the staff regarding moderation of security discussions and I would like to share areas of concern with the community as well as elicit feedback from the community.

The goal is to increase the quality of information in these threads and therefore the intention of moderation is to not to stifle discussions.

As an introduction, security on any operating system is an active process and requires a commitment to reading and learning. Security is like an onion, it has layers and it stinks :twisted:

I would appreciate the assistance of the community in reducing distracting behaviors within these discussions.

In no particular order, areas for improvement include :


1. Terminology. As with all technical discussions, please use proper terms in these threads. If you do not know the definition of a [virus]("http://en.wikipedia.org/wiki/Computer_virus"), [worm]("http://en.wikipedia.org/wiki/Computer_worm"), [Trojan horse]("http://en.wikipedia.org/wiki/Trojan_Horse_%28Computing%29"), [rootkits]("http://en.wikipedia.org/wiki/Rootkit"), [social engineering]("http://en.wikipedia.org/wiki/Social_engineering_%28security%29"), [zero day exploits]("http://en.wikipedia.org/wiki/Zero-Day_Attack"), [malware]("http://en.wikipedia.org/wiki/Malware"), [HIDS]("http://en.wikipedia.org/wiki/Host-based_intrusion_detection_system"), [NIDS]("http://en.wikipedia.org/wiki/Network_intrusion_detection_system"), etc look them up and be willing to learn them.
 
This is not a directive to "RTFM", and as always questions are always welcome. It is a request to use proper terms on these threads and avoid debates on semantics.


2. Recurring discussions. As many of you are aware, there are several recurring discussions in the security threads.

When asking for assistance / information general, vague questions often incite such discussions.

For example :

Do I need a firewall ?
Is antivirus necessary in Linux ?

**If you are asking these questions**: it is probably and indication you need to start with some reading. If you are asking these questions, feel free to start here: [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812") or with a Google search.

**If you are answering these threads**: please take the time to educate. Antivirus, Firewalls, etc, these are all tools and can be both used and misused. Education starts by asking how the OP wishes to use these tools and then providing useful information. 

**Please refrain from answering in vague, off topic ways such as "You do not need Antivirus on Linux".**


3. Bug reports. **Please keep in mind that the proper place to file a security concern or "bug report" is Launchpad**. There is an entire section devoted to security.

If you do not know how to file a bug report see [this thread]("http://ubuntuforums.org/showthread.php?t=1011078").


4. A brief message about "Escalation of privileges". This is an area that is often a "Trojan horse" on the security threads.

As a _brief_ overview ...

If an intruder can obtain a shell or execute arbitrary code you in big trouble. There are probably thousands of ways the intruder can then obtain escalate privileges to obtain a root shell (well not thousands, but many many).

The primary problem, or the hole that needs to get fixed is the one that allowed an intruder to obtain shell access or inject arbitrary code in the first place.

This is a "Trojan horse" because often discussions on escalation of privileges present a theoretical "exploit" without using proper terminology. **These conversations often do not explicitly state that the system has already been compromised and that the goal of the OP is to prevent secondary consequences.**

The two mechanisms to assist in limiting escalation of privileges are [apparmor]("http://ubuntuforums.org/showthread.php?t=1008906") (default on Ubuntu and SUSE) and selinux (default of Red Hat / Centos / Fedora). 


5. I would also like to remind the community that when discussing security you will get different opinions. Let us take care not to turn differences of opinion into debates, flame wars, and "recurring discussions" on these threads.

Please **be respectful** of opinions with which you may disagree and while voicing a different or opposing opinion is acceptable, debating opinions or semantics detracts from the conversation.

Once you have added your advice, please **do not engage in ranting, correcting, repeating, "justifying", or debating your opinion(s)**. Such replies may be subject to "moderation".


6. **Please keep your comments "on topic"**. If someone is asking for advice on how to configure apparmor (for example) it is not appropriate to express negative opinions of apparmor. Off topic comments may be subject to "moderation".


Last reminder - **If you see posts / behaviors that are distracting or off topic please report them**.

---

