---
title: "Suggestion for Posting : &quot;Have I been hacked, cracked, pwned or pillaged?&quot; Threads"
date: 2011-12-19
forum: Security
---

### Post by Dangertux on 2011-12-19
If you're posting because you think you have been cracked, hacked , or your system's security has otherwise been compromised please consider including the following information. This will help those trying to support you streamline the process and get you to your solution more quickly.

Prior to posting -- make sure you have a current back up of your system. Often times in the event of a compromised system a full reinstall is the only solution.
[B]
1: What version of Ubuntu are you running? Are you dual booting, and is this system networked with other machines, if so what operating platform and versions are they running?[/B]
[B]
2 : Why do you think you were cracked? Please post a paste from the log file or a screenshot, or written description of what you are experiencing. [/B]

Examples include : auth.log snippets, syslog snippets, av alerts, rkhunter/chkrootkit reports, odd browser behavior, IDS logs, etc.

**3: If this machine is networked with other machines is the same behavior observed there?**
[B]
4: Is this machine shared between multiple users, or is it for your use only. Also, is it using strong credentials for all forms of authentication?[/B]

**5: What services are the machine in question running? Also are any other network services running on other machines on the network? If so what are they?**

Examples : SSH, VNC, FTP, MySQL, Apache HTTP, etc.
[B]
6: Did you recently download or install anything from an untrusted source? (IE: PPA, or from the internet, including bash scripts)[/B]

**7: Is the compromised machine or network in question on a wireless network? If so what type of security measures are in place? WEP/WPA/WPA2/Open ? **

**8: What other security measures are you utilizing on your sytem? Apparmor? UFW? Firestarter? etc...**

**9: Have you added, modified, damaged or replaced any hardware in the system recently? **

**10: Is the noticed activity repeatable?**

Example : If I try to visit facebook on my Ubuntu machine I am always redirected to another site.

Example2: My server runs a cron job I did not create every night. 

Please note that you may not know all of this information, it is perfectly acceptable , and encouraged to ask for clarification. However, try to give as much information as you can at the start below you will find an example of a post that would follow this format.
----------------------------------------------------------------------------------------------------------------------------

*Could someone please help me, I'm pretty sure my system has been cracked. Here is the information suggested in the thread.*

[I]1. I'm running Ubuntu 11.04 Natty, it is the only operating system on the computer and it is connected directly to the internet, there is no router.

2. I noticed in my /etc/passwd file there is a user that I did not create. Below is an exerpt from my passwd file.[/I]

```

dangertux:x:1000:1000:dangertux:/home/dangertux:/bin/bash
qemu:x:107:107:qemu user:/:/sbin/nologin
badguy:x:1001:1001:get owned:/dev/null:/bin/sh

```*Additionally there is this line in my auth.log*

```

Dec 12 18:43:16 server sshd[1577]: Accepted password for dangertux from 3.13.3.7 port 59274 ssh2

```[I]
This is not an ip I use.[/I]


[I]3. There are no other machines.

4. I use a 10 character password based on a dictionary word for my login.

5. My machine runs an SSH server so that I can tunnel from public wifi back to my machine. It is using password authentication.

6. No I haven't.

7. Not on a wireless network it is directly connected.

8. UFW is enabled however port 22 is allowed. 

9. No it's a brand new machine still under factory warranty (minus the fact that I installed Ubuntu)

10. The activity is persistent, and I have not noticed other side effects what should I look for?[/I]
------------------------------------------------------------------------------------------------------------------------

As you can see the information provided here clearly helps those troubleshooting the issue realize that the system was cracked via weak SSH credentials and an additional user was created. At this point it would be acceptable to recommend a full reinstall since the user in question UID 1000 (if settings are default) is a sudoer. If the user is not a sudoer recommendation for removal of the offending account, change of credentials as well as hardening of SSH would be recommended.

This is just one example, and they may not all fit this mold. Just remember that the more information that can be posted in the thread initially the better your chances of getting a fast answer.

---

### Post by Ms. Daisy on 2011-12-19
Brilliant. At the very least we can link to this thread when someone posts a vague question.

---

### Post by elgordodude on 2011-12-20
I agree. However, you should remember that these are generally new users migrating from windows. While a GUI checkbox interface would make everyone's lives easier I can tell you from experience that their eyes will glaze over halfway through question one, and they have no idea what MySQL and Apache are.

What would be nice is if they had the courtesy to post in Absolute Beginner Talk, I tend to surf that one often, when I'm here, and I suspect that's true of most users.

It would be annoying to the posters who think they have a security problem, and an absolute pain in the (expletive) to the mods, but perhaps those threads should simply be moved.

---

### Post by OpSecShellshock on 2011-12-20
Those are good questions. I do think in a lot of cases the answer will be that they don't know, at least for some of the questions. People I think should understand that it's fine to not know how to respond to some of the questions at least, because at least that way folks helping out can provide some instruction on how to get the answers.

Maybe people should also be encouraged to back up important files in preparation, just in case we have to suggest a clean installation? I mean, if a problem persists beyond a clean installation then that provides valuable information as well (sometimes just doing version upgrades from existing installations breaks things in a way that could look suspicious, for example).

---

### Post by spynappels on 2011-12-20
I think this is a good idea, but difficult to get accepted by users. Ideally a subforum might be useful for corralling these type of threads.

I do wonder whether it is ever right to tell people to not run some services when they have no idea on how to find basic information. I don't mean to be harsh, everybody has to learn, but when a thread is posted saying that a user thinks they've been hacked and they've installed a whole bunch of packages, but then are unable to copy and paste extracts from pertinent logs and are unable to follow simple suggestions, I am tempted to sometimes say that if they are unable to do simple tasks like that, they should not be running services like LAMP, SSH etc, as they may be adding to problems, much the same way as Windows machines without A/V are.

Am I way off base here?

---

### Post by Ms. Daisy on 2011-12-20
> **spynappels said:**
> I think this is a good idea, but difficult to get accepted by users. Ideally a subforum might be useful for corralling these type of threads.

I do wonder whether it is ever right to tell people to not run some services when they have no idea on how to find basic information. I don't mean to be harsh, everybody has to learn, but when a thread is posted saying that a user thinks they've been hacked and they've installed a whole bunch of packages, but then are unable to copy and paste extracts from pertinent logs and are unable to follow simple suggestions, I am tempted to sometimes say that if they are unable to do simple tasks like that, they should not be running services like LAMP, SSH etc, as they may be adding to problems, much the same way as Windows machines without A/V are.

Am I way off base here? You're not in my opinion. If you read the wiki in my signature, that's one of the first pieces of advice we give. Don't run it unless you know it.  Perhaps a more diplomatic way to convey this information in this situation is to offer several manuals & tell them they at least need to understand x, y, and z before they run the service again.

---

### Post by Dangertux on 2011-12-20
@OpSecShellshoc - I agree that they may not know the answer to the question. However if they don't know if they have Apache installed, it's more reasonable to assume they probably don't. Though this isn't always the case, Linux is a little more obvious about installing services. You don't (usually) go trying for supertux racer and end up with Oracle DB2. Though there are exceptions to every rule.

@Spynappels - I'm not so much concerned about telling users not to run services. However if someone says they are noticing files popping up on their computer they didn't create in conjunction with telling us they are running a vulnerable version of vsftpd it's safe to assume there was a compromise and we can troubleshoot in that direction as opposed to playing 20 questions about their system configuration.

Also I agree with the backup thing, though the goal would basically be to create a pre-screening "form" if you will, to try to rule out hardware failure, bad configuration, or user error as much as possible.

Just my thoughts.

---

### Post by sudodus on 2011-12-20
> **Dangertux said:**
> ... Also I agree with the backup thing, though the goal would basically be to create a pre-screening "form" if you will, to try to rule out hardware failure, bad configuration, or user error as much as possible.

Just my thoughts.

+1 for a pre-screening "form"
and a sub-forum to make these posts easier to find

---

### Post by emiller12345 on 2011-12-20
> **elgordodude said:**
> While a GUI checkbox interface would make everyone's lives easier I can tell you from experience that their eyes will glaze over halfway through question one, and they have no idea what MySQL and Apache are.
We could always add a hyperlink to the words 'MySQL'...
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
if they do not know what it is or what its used for and even add in a simple oneliner to test if its install and what version.

---

### Post by lisati on 2011-12-20
> **emiller12345 said:**
> We could always add a hyperlink to the words 'MySQL'...
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
if they do not know what it is or what its used for and even add in a simple oneliner to test if its install and what version.
+1
At the risk of offering a "worked for me" answer - it did :D - I've seen a handful of threads where some of the troubleshooting tips on the [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) page might be useful for users to try.

---

### Post by CoffeeRain on 2011-12-20
> **Dangertux said:**
> 

Example2: My server runs a cron job I did not create every night. 



Of course you wouldn't create a cron job every night. :)

---

### Post by Ms. Daisy on 2011-12-20
> **CoffeeRain said:**
> Of course you wouldn't create a cron job every night. :)
No, you'd run a cron job to create a cron job every night :P

---

### Post by mörgæs on 2011-12-20
Good post. I have linked from ['How to get answers...']("http://ubuntuforums.org/showthread.php?t=1422475").

---

### Post by CharlesA on 2011-12-20
> **mörgæs said:**
> Good post. I have linked from ['How to get answers...']("http://ubuntuforums.org/showthread.php?t=1422475").
Thank you, mörgæs.

@DT: Nice job with the checklist. I think that would cover most of not all of the information that is needed to determine if a machine has been compromised or not.

---

### Post by emiller12345 on 2011-12-20
one thing that I really wish existed was a list somewhere for common binaries of various checksums so you can check them manually against your own checksums.  So if any of your files in /bin/, /sbin/, /usr/bin/, etc gets messed with or is not updated, you'll be able to tell.

---

### Post by Dangertux on 2011-12-20
Hey everyone... Thanks so much for the positive feedback, and the link in the "How To Get Answers" Thread.

I'm going to clean up the checklist a little bit formatting wise. If anyone thinks there is any other pertinent information / questions that needs to be there let me know I will add it.

However, I want to try to keep it short and sweet (preferably under 15 questions). We don't want individuals losing interest before they even ask the question. 

Also @ emiller : the binary checksums are a great idea I think I have a list somewhere if I can find it I'll put it up (probably a different thread or possibly my website) if not I'll try to put one together been super busy lately. If anyone else happens to have that list handy, a link would be awesome (be sure to account for different checksums in different build versions and state which build the list is from please).

Thanks again everyone.

---

### Post by mörgæs on 2011-12-20
And thanks to *you*.

Great - such a list would be a good candidate for going into the wiki. In general it would be best to put stuff having long-time value there.

---

### Post by Rubi1200 on 2011-12-20
Nice job Dangertux :)

It's always good to see posts like this that we can all use as a reference point when helping others.

---

