---
title: "Snort and security"
date: 2010-03-25
forum: Security
---

### Post by Rubi1200 on 2010-03-25
As a general question, I was wondering whether or not it is possible/advisable to install and run Snort on a single laptop with a wireless router (firewall enabled)? Does Snort require root privileges and are there any other issues one needs to be aware of when installing and running software like this?
Thanks in advance.

---

### Post by unspawn on 2010-03-25
> **Rubi1200 said:**
> possible/advisable to install and run Snort on a single laptop with a wireless router (firewall enabled)? 
Possible: yes, advisable: it depends. If you run a properly configured and hardened pure client machine, meaning you don't run networked services exposed to (hostile) networks, then you may not get much out of Snort except a steady stream of alerts to wonder about if they are of any value.


> **Rubi1200 said:**
> Does Snort require root privileges and are there any other issues one needs to be aware of when installing and running software like this?
Snort requires root privileges on startup then drops to its own "snort" user Id. The issues to be aware of are like with any other software: run only what you need (also in other ways like rule sets configuration) and update when (security) updates are available.

---

### Post by OpSecShellshock on 2010-03-25
I don't think it's necessary. It's bound to be process intensive and will mostly result in false positives. If you're willing to put in the time watching the events in order to sort out the real stuff from the coincidental stuff, you might get something interesting out of it, but it's pretty time consuming to do it right. For example, it frequently fires shellcode signatures on encrypted and streamed traffic since it's just trying to match strings. So you'll spend a lot of time trying to translate gibberish for no reason.

---

### Post by Kinstonian on 2010-03-25
I agree with OpSecShellshock.  Most home users aren't going to benefit from a NIDS due to not having the time and/or the skills to follow up on alerts by analyzing network traffic.  However, a HIDS like [OSSEC](http://www.ossec.net/) may be more what you're looking for, especially since you just want to monitor one computer.

---

### Post by Rubi1200 on 2010-03-26
Thanks guys!
As it turns out, Snort cannot be used on a wireless interface (found this on the Ubuntu security forum in the meantime) and I think that the hassle of trying to sort out the "gibberish" is actually not what I am looking for. I will check out OSSEC instead.
Thanks again for the responses.

---

### Post by bodhi.zazen on 2010-03-26
> **OpSecShellshock said:**
> I don't think it's necessary. It's bound to be process intensive and will mostly result in false positives. If you're willing to put in the time watching the events in order to sort out the real stuff from the coincidental stuff, you might get something interesting out of it, but it's pretty time consuming to do it right. For example, it frequently fires shellcode signatures on encrypted and streamed traffic since it's just trying to match strings. So you'll spend a lot of time trying to translate gibberish for no reason.

I agree that snort is not necessary for the vast majority of Linux Desktop Users.

Linux is not Windows and, IMO, we have a ton of new users who, no offense intended, are trained to run firewalls and antivirus and spyware from their experience with Windows.

I would say that for the vast majority of users you do not need to do any of these things, a default installation of Ubuntu is secure enough.

If, however, you are interested in Security, and / or feel you are the paranoid type (nothing like reading the logs to instill a little paranoia) then you need to be prepared to do your home work. Security is a complex discipline and some of what you may know from Windows will apply, but much will not.

The first step to securing a system is understanding how the system works and what "normal" usage or behavior is. this includes becoming familiar with system logs and networking protocols.

Installing a firewall, GUFW, firestarter, etc, does very little to add to your over all security because there are no open ports, so there is nothing to firewall. That is not the same thing as saying firewalls are not an essential tool for security, but, unless we know specific concerns or specific uses for these tools with specific user cases / server / networks it is hard to give more specific advice.

Returning to the Question of snort, similar advice. Snort is an example of NIDS (as is watching the flashing blocked light on Firestarter or reading the logs). The average Desktop user has no need for snort.

Snort monitors Network traffic and filters through the thousands of lines in the log files and brings concerning packets to your attention. Most people feel false positives are preferred to false negatives, and most people who use snort monitor the network traffic and watch for trends, not necessarily over react to a single alert, honestly it depends on the alert and how persistent the IP address is. As a system admin you will need to determine how to use the information Snort provides you.

Snort is one of the defacto industry standard HIDS, but overkill for 99.999% of desktop users. 99.999% of Desktop users either do not need a firewall or are fine with 'sudo ufw enable'

OSSEC is a HIDS and although related very different from snort. It monitors the integrity of system files. Again it has a role but is over kill for most users.

The "take home" message is - Linux is not windows and, IMO, you should not be deploying advanced security tools if you do not understand what you are doing.

I am not suggesting you should ignore security, I am suggesting you should learn the basics first. Start with the security sticky.

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

The vast majority of security problems are :

1. Failure to limit Physical access.

2. Weak passwords.

3. People install or use either SSH or the default VNC server, ie desktop sharing, and forward ports from the internet without securing the server. If you are installing a server be sure you understand the security implications before you forward ports.

4. Social engineering. Do not install applications from untrusted sources. This can extend to Launchpad ppa and even Gnome Look. Use the Repositories 

See : [http://wiki.debian.org/SecureApt](http://wiki.debian.org/SecureApt)

5. There are no known active viruses for Linux. Ubuntu has been patched for the known viruses long ago.

6. There are always potential holes in the code on any OS, both known and unknown, see the security alerts :

[USN list | Ubuntu - Security alerts]("http://www.ubuntu.com/usn") 

The best defense against this threat is to keep your system up to date.

Second line of defense is SELinux / Apparmor (or similar tools) and OSSEC.

7. The new "hot topic" is with using a Live CD for "security" A live CD has uses , but it is limited and the security issues here are basically [Phishing](http://en.wikipedia.org/wiki/Phishing) , connecting to a compromised server, and or packet sniffers. These issues are, IMO, best addressed with Education (Phishing) or addons such as [WOT](https://addons.mozilla.org/en-US/firefox/addon/3456) for Phishing and using https (encryption).

A live CD does not add much, and can be less secure as it does not include the latest security updates. Unlike Windows there are no known spyware like applications or key loggers currently active "in the wild".

Paranoia is one thing, but please do not apply windows security techniques blindly to Linux.

---

### Post by Rubi1200 on 2010-03-27
A huge thanks to you bodhi.zazen for explaining, clearly and intelligently, what I needed to know. I was a long-time paranoid Windows user. I moved to Ubuntu exactly one week ago! My initial impressions from both using the OS and reading around is that Linux is inherently safer than Windows. The real issue of concern for me is that I use a wireless router and wanted to find a way to check if it is really secure. Although I have a firewall enabled on the router and although I also use Wireshark, vestiges of what you call Windows paranoia still linger. 
I will follow your advice and continue reading more on the subject **before** installing software that may potentially expose the system to vulnerabilities or simply overwhelm me with unnecessary information. By the way, the only reason I thought of Snort or OSSEC was because the discussions on the security forum indicated that these are powerful tools to use on Ubuntu.
Regarding the use of a live CD for integrity and security testing, I think I agree with you. I recently looked at Backtrack, but quickly left it when I saw how many tools it included that could potentially really mess things up.
Again, a huge thanks. It is this kind of support and intelligent advice that makes the Ubuntu experience even more pleasurable than it has been thus far.

---

