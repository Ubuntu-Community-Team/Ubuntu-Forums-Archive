---
title: "GRC Shields Up Test"
date: 2010-07-06
forum: Security
---

### Post by RossTaylor on 2010-07-06
Can someone please tell me if this is good or not?

**Attempting  connection to your computer. . .** 
**Shields UP!** is now attempting  to contact the **Hidden Internet Server** within your PC. It is  likely that no one has told you that your own personal computer may now  be functioning as an **Internet Server** with neither your knowledge  nor your permission. And that it may be serving up all or many of your  personal files for reading, writing, modification and even deletion by  anyone, anywhere, on the Internet!
[IMG]https://www.grc.com/image/reddash.gif[/IMG]

**Your  Internet port 139 does not appear to exist!** 
**One or more ports on this system  are operating in FULL STEALTH MODE!** Standard Internet behavior  requires port connection attempts to be answered with a success or  refusal response. Therefore, only an attempt to connect to a nonexistent  computer results in no response of either kind. **But YOUR computer  has DELIBERATELY CHOSEN NOT TO RESPOND** (that's very cool!) which  represents advanced computer and port stealthing capabilities. A machine  configured in this fashion is well hardened to Internet NetBIOS attack  and intrusion.

[IMG]https://www.grc.com/image/reddash.gif[/IMG]

**Unable  to connect with NetBIOS to your computer.**
All attempts to get **any** information from your computer  have **FAILED**. (This is **very** uncommon for a Windows  networking-based PC.) Relative to vulnerabilities from Windows  networking, this computer appears to be **VERY SECURE** since it is **NOT  exposing ANY** of its internal NetBIOS networking protocol over the

---

### Post by Linuxforall on 2010-07-06
I would say very good. You are totally hidden from the rest.

---

### Post by OpSecShellshock on 2010-07-06
Just means that your computer is not listening for incoming connections on port 139 (or you have a hardware firewall that isn't listening for such connections). "Stealth Mode" is not a real thing in terms of being a standard name for whatever it is they're talking about. Only the Shields Up site uses it. Everyone else says you're quietly dropping requests. Different people will tell you different things about whether it's better to drop or reject, and I don't really think it matters.

---

### Post by CharlesA on 2010-07-06
Doesn't really matter, since the ports are closed reguardless.

The only difference between reject and drop is that reject sends a response that the port is closed and drop just silently drops the packets.

---

