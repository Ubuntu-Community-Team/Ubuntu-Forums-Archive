---
title: "sudo command"
date: 2013-04-11
forum: Security
---

### Post by gordie69 on 2013-04-11
hey guys I was told that the sudo command was not secure like once you type in a sudo command and type in your admin pass it lets in intruders thats not true is it because I also thought sudo was a way of installing or retreiving from terminal

---

### Post by prodigy_ on 2013-04-11
Told by whom and in what context?

Barring possible bugs, sudo is secure. It does what it's supposed to do and nothing more. The problem is, it's supposed to execute *something else* with root (unrestricted) privileges. When someone tricks you into running a malicious command or a piece of malware with sudo, you're indeed at the mercy of the attacker.

---

### Post by Frogs Hair on 2013-04-11
Sudo allows elevated privileges  to the system and a user or attacker can certainly break things. If you stick to the software center for installing applications you will avoid installation of malicious software( no system is perfect). Remember that  software doesn't get installed without elevated permissions or a password. Sticking to a user account rather than administrative is another simple safe guard .
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by maglinu on 2013-04-11
> **gordie69 said:**
> hey guys I was told that the sudo command was not secure like once you type in a sudo command and type in your admin pass it lets in intruders thats not true is it because I also thought sudo was a way of installing or retreiving from terminal

I have read that sort of comment on eg the PCLOS forum [http://www.pclinuxos.com/forum/index.php/topic,90479.msg758079.html#msg758079](http://www.pclinuxos.com/forum/index.php/topic,90479.msg758079.html#msg758079). 
Some folks there have a beef with sudo being used otherwise to original intent. For a single user desktop installation it appears to me to make no real difference.
 
Also some with the preservation of the elevated privileges for a default period - 15 minutes. You can reduce or eliminate that if you want though.
[https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

---

### Post by CharlesA on 2013-04-11
> **maglinu said:**
> I have read that sort of comment on eg the PCLOS forum [http://www.pclinuxos.com/forum/index.php/topic,90479.msg758079.html#msg758079](http://www.pclinuxos.com/forum/index.php/topic,90479.msg758079.html#msg758079). 
Some folks there have a beef with sudo being used otherwise to original intent. For a single user desktop installation it appears to me to make no real difference.

Wow, that post by Old-Polack sure spells their stance out. The post is about two years old and I thought both Debian and Fedora allowed sudo usage like that.

*shrugs*

To each their own. If you want a specific user to have "admin rights" via sudo, add them to the sudo group and there you go.

---

### Post by gordie69 on 2013-04-11
Thanks guys the tip I'll stick with the software center thanks

---

