---
title: "A Smart Security Layer to Protect Malicious Commands Execution"
date: 2013-08-17
forum: Security
---

### Post by RLDr on 2013-08-17
First read this [announcement]("http://ubuntuforums.org/announcement.php?f=326") about malicious commands. [COLOR=#ff0000]Please do not try to execute any command mentioned there, they are very dangerous.[/COLOR]

[COLOR=#008000]Is there in Linux systems a smart security layer to protect malicious commands execution, exists or not? If exist, then please mention it in details with references.[/COLOR]

If not, then I think creation of a smart protection layer can be started. I think it would not be too hard to implement. Concept and implementation of sudo command and sudoers file is already protecting root account. A similar kind of protection can be created. Where every command should pass through a security check, if it pass, will be allowed to execute, else not. A special root owned file will list all known malicious commands. Security check system will compare every commands (actual) with that file. If any match found, then it will inform the user and enter a log entry about the potential threat, and deny to execute easily without rigorous authentication procedure.

[COLOR=#0000cd]Do you have any other idea or information? You are all welcome for suggestions. Together we can make Linux systems more secure and stable and hard to crack.[/COLOR]

---

### Post by Hungry Man on 2013-08-17
Unfortunately it is impossible to arbitrarily determine whether any (as in an arbitrary) command is malicious or not. You can heuristically detect this, though you're likely to come up with false positives. You can also blacklist specific commands (like rm -rf /**) but you can rewrite that same command 100 ways, and a million other commands can be just as devastating, so such a blacklist would be unlikely to be effective.

There's a ton of research into 'intent based' access control that would limit code execution on a very fine grained level, but we're not there yet, so instead we have to use tools like Apparmor etc.

---

### Post by Sef on 2013-08-18
> [COLOR=#000000]A special root owned file will list all known malicious commands. [/COLOR]

That is how most anti-virus works: detecting that which is known. However, a slight change can make it inivisible to detection. Best to be a smart user - though we all mess up at times.

---

### Post by texaswriter on 2013-08-18
> **RisingMan said:**
> Is there in Linux systems a smart security layer to protect malicious commands execution, exists or not? If exist, then please mention it in details with references.

On any system, this "smart security layer" should be the user. Computing systems exist for users. 

It is possible for those users to use computing systems without executing malicious commands or code? Yes. 

It depends on a few things. These are some common best practices that I use (I'm sure a security expert would have more), IMO and all that.

1) The operating system should be relatively free of exploits. In Ubuntu or any Linux operating system, the operating system and various aspects of the GUI and system are decoupled (so to speak) and developed independently. This is good compared to Windows where the operating system is not constantly developed and updated. Linux is constantly evolving and conforming to the needs of its various user bases. Whether you need an operating system for a supercomputer, a supercomputer cluster, a PC, laptop/netbook, or a microchip/SBC/etc, Linux is well adapted to the needs of all these.

2) The operating system should have a root level and user level that prevents programs or users from making changes to the system without authenticating. On Ubuntu or any Linux operating system, you are prevented from making any change to the system or a system file by default. You will be asked to authenticate any command that makes changes to the system.

3) The user should only install trusted applications from trusted vendors or repositories. On Ubuntu or almost any version of Linux, this means, a) use the standard repositories whenever and wherever possible for all your software, b) if you have to use a PPA or a .deb (etc) from outside the trusted repositories, ensure it is from a reputable vendor or source, c) if you have to use other binaries, same thing goes, only when necessary and only from trusted sources. 

4) The user should always regularly patch their operating system. On Ubuntu or any Ubuntu flavor, this means running "sudo apt-get update; sudo apt-get upgrade" without the quotation marks in a terminal or using the update manager.

5) The user should always use operating systems that are still being actively maintained.  On Ubuntu, this means use an LTS or the most recent release. (12.04 was the most recent LTS [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS))  

Believe it or not, the so called "smart security layer" can never be perfect. If the user is not trusted, you need to deny them ability to authenticate, ensure the operating system and all programs are updated regularly, and follow the above and other best-practices. 

For example, the standard antivirus/antirootkit/antimalware, detect malicious commands/programs by patterns. This means that they were 100% ineffective when EACH AND EVERY new virus (etc) came out. 


Otherwise, following the above best practices and others is sufficient on Ubuntu/Linux.

---

### Post by RLDr on 2013-08-18
> **Hungry Man said:**
> You can heuristically detect this,Thanks for your suggestion.

> **Sef said:**
> That is how most anti-virus works: detecting that which is known.Thank you. Thinking about checking the engine (source code) of ClamAV and try to upgrade that according to our needs. I believe in the fact that "Reinventing the Wheel" is just wastage of time. So, we should first try to upgrade existing works.
For absolute beginner's info: ClamAV is an anti-virus toolkit for Unix. Good News=> According to Kubuntu's Muon Package Manager: Canonical provides critical updates for clamav until April 2017.

> **Sef said:**
> Best to be a smart user - though we all mess up at times.Sorry, I'm not a smart user, rather a lazy one. After every Linux installation I can't maintain them properly all the times, I don't have so much time. So, trying to solve it in either way and seeking your help. - I'm using Linux from 2003 (though still I'm child in the Linux world), but every time when I went to harden my systems' security I ended up by messing-up my system. You can say me paranoid about security:).

> **texaswriter said:**
> Believe it or not, the so called "smart security layer" can never be perfect.
For example, the standard antivirus/antirootkit/antimalware, detect malicious commands/programs by patterns. This means that they were 100% ineffective when EACH AND EVERY new virus (etc) came out.Thank you for your detailed guidelines.
Nothing is perfect. So, kernel, security and application upgrades are done over time.
Example: I'm not perfect. So, upgrading myself through [http://ubuntuforums.org]("http://ubuntuforums.org/") :).

---

### Post by 1clue on 2013-08-18
Here are steps to best do what you're describing:
[LIST=1]
[*]Never run as root user unless you absolutely have to.
[*]Never set up sudo without a password.
[*]Never give your user special permissions.
[*]Keep strong passwords on your system.
[*]Start learning about security:  [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) is a good place to start.
[*]Pay attention to the things you're about to do.
[*]Don't EVER run something as root that you don't understand.
[*]If you consistently have to be root more than once a week, you're doing something wrong.
[*]READ YOUR LOGS REGULARLY!
[*]Install security-based apps like tripwire, learn how they work, configure them properly and pay attention to the reports.
[/LIST]

---

### Post by 1clue on 2013-08-18
Addendum:

There are strategies to prevent execution of malicious commands.  Mostly they exist between the ears of the person at the terminal.

All strategies which prevent execution of malicious commands which do NOT fall into the category above are easily sidestepped by a single user who's not thinking.

This is true for pretty much any operating system I can think of.

Not running anything as root is the first step, and the most important.  Root user is by definition the unrestricted user for UN*X.

---

### Post by kevdog on 2013-08-18
Although I agree with your premise in theory, I've never really ran across any post that I felt was giving malicious commands.  In fact any command that I didn't really understand, I looked up.  As far as running user-supplied scripts -- yes check them.

---

