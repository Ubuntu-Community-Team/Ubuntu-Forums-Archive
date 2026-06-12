---
title: "Why does Ubuntu have better Security than Windows"
date: 2007-09-25
forum: Server Platforms
---

### Post by Black Mage on 2007-09-25
I'm currently writing an comparson for switching from Windows to Ubuntu in a work enviroment. Notes are at [http://ubuntuforums.org/showthread.php?t=559551](http://ubuntuforums.org/showthread.php?t=559551). But I'm hazzy on the part to why Ubuntu is more secure than Windows, besides the amount of people who just don't like windows and make viruses for it. Can anyone give clear reasons why security is better on Linux (Ubuntu) that windows? Like with Viruses, Spyware, hacking, identity theft, etc.

---

### Post by overkillm on 2007-09-25
Others here could probably expand upon this much better than I can, but the basics as I understand them, are:

- Normal users do not have access to modify system files or settings. These require root privileges, given temporarily by use of sudo (or gksu or kdesu), which in turn requires entering a password.  Since malware such as viruses and spyware only have the privileges of the user account they are run under, they have no ability to really destroy your Ubuntu system unless you explicitly allow it.

- You can't even log in as the almighty "root" user in Ubuntu without first modifying system settings to allow you to do so. In Windows, you are set up as the root (or Admin) user by default, and thus any malware you contract will have absolute power over all your files and settings.

- All ports are closed by default, reducing the number of attack vectors for hackers.  In Windows, many ports are left open for various services, presenting openings for malicious users and/or programs.

- Software installed from the central repository is signed as trusted.  The software is all examined to ensure it is non-malicious.  Meaning no more surfing the web and installing random apps that may or may not do what they say they do.

- no Internet Explorer means no IE exploits owning your machine.

Unfortunately phishing is often less dependent/predatory upon the operating system and more on the user... entering sensitive data in a phisher's web form will have similar effect regardless of your OS.  

There's more that I'm missing, I'm certain.

---

### Post by Nevon on 2007-09-25
> **overkillm said:**
> Normal users do not have access to modify system files or settings. These require root privileges, given temporarily by use of sudo (or gksu or kdesu), which in turn requires entering a password.  Since malware such as viruses and spyware only have the privileges of the user account they are run under, they have no ability to really destroy your Ubuntu system unless you explicitly allow it.
I read a pretty good counter-argument (if you can call it that) on that. "What would pain you the most to lose - Your operating system or your personal photos, work files etc.?"

---

### Post by netlogic on 2007-09-25
i will make a short list

1. hybrid kernel is old. it is so  1993s. Dave Cutler from Digital was a smart man, but it is time to change tons of low level stuff.
2. micro/hybrid kernel is unstable. it isn't hard to insert codes inside the hybrid k (example:some antivirus) monolithic kernel is proven to be more secure.
3. you can make a rootkit to run in windows without ever being detected by any rootkit finders. Only way to truly find the rootkit is boot it off Knoppix with wine and use the windows rootkit finder tools.
4. IE - BAD design. Let's start over. Your desktop and file manager shouldn't be a browser without having the proper tools to run in a lock state. 
5. virus
6. malware
7. spyware
8. reboots - not hard to send a reboot dialog to a user and insert something in the registry to install any app you want.
9. still NO dll inspection tools (why???)
10. registry (windows 3.1 had a better idea... ini is a lot better than registry) oh, windows can't boot... time to reinstall the entire OS with all the apps. people tried to make text based registry tools, they don't work.
11. if things are broken, but fixes feel like features to microsoft, you have to wait for the next release of windows.
12. some companies can't wait a full month for fixes
13. uptime? 
14. why did they integrated IE so tightly that I need to reboot my servers after every IE updates?
15. beta version of MS 2008 is a pure garbage.
16. there are no rules in the registry placement. a lazy developer can insert
keys anywhere in the registry. there is no rule that says... everything must be /etc /home like unix.
17. cloning a similar machine is a nightmare. why can't i just image a machine and run a simple custom script to change configuration settings?
18. please... keep your library calls simple and stupid. have you ran dll utilities and realize how complex NT is?
19. Underneath the hood, NT has most complex booting procedures. MS can't keep things clean and stupid.
20. Windows RPC - it is insecure compare to an interactive shell.
21. Nightmare!! I used manage a NT based data center. My girlfriend has to visit me at work, because she forgot how I look like.
22. i can go on if i have more time.
---------------
However, Windows has more killer commercial apps large companies need and AD isn't too bad when it doesn't break.

=======================================
note: i used MS for many decades. i even migrated over 2000 Netware 3.12  servers in the 90s to NT based system. consultants do whatever customers want. we don't judge their fashion statement. we just help them get dress.

---

### Post by nonewmsgs on 2007-09-25
most modern viruses are office macros that aren't supported by linux.

---

### Post by lisati on 2007-09-25
> **overkillm said:**
> 
Unfortunately phishing is often less dependent/predatory upon the operating system and more on the user... entering sensitive data in a phisher's web form will have similar effect regardless of your OS.  



An alert user can usually spot phishing attempts, like being directed to a website that is almost (but not quite) identical to the one you'd normally use to access personal data. I've received several by email, some better than others. A dead giveaway is when its faked to look like its from people you've never even heard of. Others include being asked for information that you normally wouldn't be asked for, There's always going to be a clue somewhere.....

---

### Post by misfitpierce on 2007-09-25
Simple 3 words... Because its baller.

---

### Post by qamelian on 2007-09-25
> **Nevon said:**
> I read a pretty good counter-argument (if you can call it that) on that. "What would pain you the most to lose - Your operating system or your personal photos, work files etc.?"

Considering that I regularly backup all my data, I don't care if my home folder gets hosed. It takes me all of 10 minutes to get back up and running again. So, this argument doesn't really carry any weight. If people truly believe the "data is king" and they don't implement any kind of backup strategy, they are just begging to get burned no matter what OS they use.

---

### Post by netlogic on 2007-09-25
Windows is good for one thing, hosting commercial apps, but that is it. If terminal sever licenses aren't so expensive, most companies will go Linux everywhere and make users run their favorite commercial apps on a Windows Terminal session. I wish there is a way to dump Windows libraries inside Linux (something like wine) and run any Windows apps natively in Linux without buying extra Windows license. This also means Linux has to adopt DRM in a container format like BSD can do in jailing. Of course, MS will not legally sell anyone dlls.  If these options are available, most companies will dump their Winboxes. The bottom line of Linux adoption is simple. It is all about Desktop clients. If they can move to a newer platform without losing their productivity, most CTO, CFO, and CEO will say YES. They will always ask for the final the year period of TCO. TCO also has to include salaries of employees who might slow down with the new system.

---

### Post by overkillm on 2007-09-25
> **Nevon said:**
> I read a pretty good counter-argument (if you can call it that) on that. "What would pain you the most to lose - Your operating system or your personal photos, work files etc.?"

Yes, this is true, some wacky malware running loose can do nasty damage even if it's constrained to just your /home folder.  A point I forgot to mention in my post.  But, then, that's why doing regular backups is so important.   A hosed /home can be restored easily enough if the OS is still running.  A hosed OS necessitates a full reinstall (often deleting or overwriting your /home anyway) or at the very least, a second functioning computer from which you can hop on Google and research ways of reviving your OS.

---

### Post by overkillm on 2007-09-25
> **lisati said:**
> An alert user can usually spot phishing attempts, like being directed to a website that is almost (but not quite) identical to the one you'd normally use to access personal data. I've received several by email, some better than others. A dead giveaway is when its faked to look like its from people you've never even heard of. Others include being asked for information that you normally wouldn't be asked for, There's always going to be a clue somewhere.....

Very true.  My point was just that there's nothing inherent to Linux (or OSX or BSD or Windows or whatever, for that matter) that will make phishing less likely to succeed.  Good anti-phishing apps/widgets/browser plugins, maybe, but not the OS in and of itself.  Just as you said, it's really more a matter of being an alert, informed user.

---

### Post by netlogic on 2007-09-25
> **overkillm said:**
> Yes, this is true, some wacky malware running loose can do nasty damage even if it's constrained to just your /home folder.  A point I forgot to mention in my post.  But, then, that's why doing regular backups is so important.   A hosed /home can be restored easily enough if the OS is still running.  A hosed OS necessitates a full reinstall (often deleting or overwriting your /home anyway) or at the very least, a second functioning computer from which you can hop on Google and research ways of reviving your OS.

You can't get malware if you follow simple rules. Stick with the distro and learn to compile. I never use debs outside the distro unless it comes from the developers' sites. I rather compile from the source if I can't find the packages that I need. People can't push packages into your system unless they got root or your compiler security is weak.

---

### Post by daveshields on 2007-09-26
Ubuntu is a descendant of Unix, which, from its earliest days back in the 1960's, was designed to be a multi-user system. Indeed, the name "Unix" derives from "Multics," a system designed to be multi-user (look up "multics" in wikipedia to learn more).

Windows is a descendant of DOS, which, from its earliest days, was designed to be a single-user system. DOS was based on CP/M, the work of the late Gary Kildall. CP/M was the control program for a single computer, meant for just one user.

Thus, Microsoft has spent over twenty-five years evolving  a single-user system into a multi-user system, all the while trying to maintain backwards compatibility with prior versions. They are very good at it, but have only been able to do so by spending valuable resources.

On the other hand, as Unix became Linux , and then Debian,  and then Ubuntu, multi-user support --  and the security that it implies -- was a given, so the developers could focus on other things.

The key lesson here is that security is fundamental. It *must* be a key part of the initial design; it cannot be later added as a new "feature."

---

### Post by /etc/init.d/ on 2007-09-26
> **Nevon said:**
> I read a pretty good counter-argument (if you can call it that) on that. "What would pain you the most to lose - Your operating system or your personal photos, work files etc.?"
If you don't keep backups, then the data isn't important to you anyway and thus your argument has no standing.

Keeping backups also guards against a much more common threat, hardware failure.

---

### Post by nicola on 2007-09-26
There is also a VERY VERY important reason not mentioned above:
Ubuntu (like other linux distributions) is entirely made of Open Source code. This mean that "How programs work" is known by the whole developers population.

This means that it is impossible to have things like backdoors spyware or other malicious code installed.

to cite Stallmann:
"Nonfree software is controlled by its developer. The developers often implement malicious features--for example, to spy on the user or to restrict the user. Sometimes they keep the malicious features secret. But they also figure that people will be so desperate for the software that they will accept it even with malicious features. Users can't remove the malicious features, because they don't have the source code.

This cannot happen with free software, because free software is controlled by the users. If ever a free program had a malicious feature, any programmer could remove the malicious feature and release a modified version--and all users would choose that version, including nonprogrammers. You won't have to make this change yourself, because someone else will have done the job for you before you get it."

---

### Post by Black Mage on 2007-09-26
Thnx a lot guys, most of this stuff will be added to the docs.

---

### Post by steve.horsley on 2007-09-27
> **overkillm said:**
> - All ports are closed by default, reducing the number of attack vectors for hackers.  In Windows, many ports are left open for various services, presenting openings for malicious users and/or programs.

I'm sad to say that's not true any more, at least with Feisty. Something called avahi-daemon seems to be installed running by default, listening on ports 5353 and 32768. This can be disabled by editing /etc/default/avahi-daemon but it's enabled in a default install. I haven't found any good documentation on what it actually does yet.

---

### Post by koenn on 2007-09-27
> **steve.horsley said:**
> I'm sad to say that's not true any more, at least with Feisty. Something called avahi-daemon seems to be installed running by default, listening on ports 5353 and 32768. This can be disabled by editing /etc/default/avahi-daemon but it's enabled in a default install. I haven't found any good documentation on what it actually does yet.
It's a "zero config" feature and in this case probably used to detect (or be detected by) other hosts on a network to achieve an 'automaticalliy configured" network or "zero config network". 

More to the point (or on topic) : you're right, and it illustrates how the "should work out of the box" requirement is a trade-off against security. 

Windows took it to the other extreme and had all sorts of things installed and running, and not secured at all, just in case someone would want to use it without knowing how to configure it, let alone get security in the way. Some distro's seem to be moving into that direction as well. 

The 'security by design' mentioned by daveshields is, imo, the most important element when discussing Linux security, and it reduces the risk of having services listening on open ports, but it still ...

---

### Post by Brazen on 2007-09-28
I don't think I've seen this mentioned yet, but it is also standard for all services on linux to run with restricted permissions.  Whereas on Windows, all services run with full access to the system (with the SYSTEM account).

This makes it very hard for a virus or hacker to do anything beyond affecting that single server.  If a hacker or virus breaks into a Windows service, it automatically has full run to do whatever it wants on the system.  If a hacker or virus breaks a linux service, it only gets the access allowed to that server which is often only the ability to read files and even then it may only be reading files in a certain directory.

---

