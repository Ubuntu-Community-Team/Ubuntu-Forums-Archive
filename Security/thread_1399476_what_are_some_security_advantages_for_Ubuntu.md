---
title: "what are some security advantages for Ubuntu?"
date: 2010-02-05
forum: Security
---

### Post by sig266 on 2010-02-05
I have a project for school and was looking for some help.  I have to give a presentation on the advantages and disadvantages of Ubuntu's security.  Currently the college is running Windows XP.  Any help would be appreciated.  If you need me to be more specific about anything just let me know.

---

### Post by linux4life88 on 2010-02-05
> **sig266 said:**
> I have a project for school and was looking for some help.  I have to give a presentation on the advantages and disadvantages of Ubuntu's security.  Currently the college is running Windows XP.  Any help would be appreciated.  If you need me to be more specific about anything just let me know.

You might want to make the paper about Linux security in general, just a though. Anyways, one of the advantages is the root account. This will give you an extra shield of protection by having one password to log into the computer and then have another completely different password to do administrative (sudo) tasks. Others can give you technical data, which I can not but the root account does help in security.

---

### Post by sig266 on 2010-02-05
Thanks for the info, that is definitely an advantage over Windows.  I have heard that Ubuntu closes all of the extra ports that are normally used for viruses, and that most viruses are coded to affect Windows OS's, and are not a threat to Ubuntu or linux.  Can anyone clarify this for me?

---

### Post by linux4life88 on 2010-02-05
> **sig266 said:**
> Thanks for the info, that is definitely an advantage over Windows.  I have heard that Ubuntu closes all of the extra ports that are normally used for viruses, and that most viruses are coded to affect Windows OS's, and are not a threat to Ubuntu or linux.  Can anyone clarify this for me?

One thing you stated was that viruses are mostly coded for Windows, and this is true. It has to do a lot with market share. Windows has the largest market share and therefore will garner the most attention from attackers. An attacker can affect many more computers by writing a virus for Windows than for any other operating system.

Also, as for ports, these are closed up by firewalls. Linux Journal Issue 189 January 2010 actually had some articles about Linux security. It mention on your computer you can use GRC's ShieldsUp website test to see what ports you have open on your computer. Here is a link to the Linux Journal article:
[URL="http://www.linuxjournal.com/article/10600"]
http://www.linuxjournal.com/article/10600[/URL]

Here is another good article that you might be interested in and might help you:

[http://www.linuxjournal.com/article/10647]("http://www.linuxjournal.com/article/10647")

---

### Post by sig266 on 2010-02-05
thanks for the help, the article is very helpful.  I appreciate the input.  Can you think of any disadvantages Ubuntu's security in comparison with any other operating system out there as far as: OSX, Solaris, any of the newer windows versions...

---

### Post by linux4life88 on 2010-02-05
> **sig266 said:**
> thanks for the help, the article is very helpful.  I appreciate the input.  Can you think of any disadvantages Ubuntu's security in comparison with any other operating system out there as far as: OSX, Solaris, any of the newer windows versions...

As far as I know there are no Linux viruses in the wild. Although, you can still get a virus on Linux. If you use Wine, a windows virus could infect wine and destroy your system. I remember reading a while back an article where someone actually wanted to see how a Windows viruses installed under Wine would affect the Linux system. Low and behold some actually damaged the Linux system. I wish I remember where I read this article at... Also, I've always been curios at how Linux being open source affects its security? Since everyone has the "security playbook" wouldn't that make it easier to attack the system if you wanted too? I don't know the answer to this. Hopefully someone else might shine some light on this, because it is something that I'm interested in knowing.

More Links:
[http://ubuntuforums.org/showthread.php?t=72598]("http://ubuntuforums.org/showthread.php?t=72598")
[http://www.linuxforums.org/forum/wine/118945-can-wine-get-viruses.html]("http://www.linuxforums.org/forum/wine/118945-can-wine-get-viruses.html")
[http://linux.slashdot.org/story/09/10/24/1759213/Now-Linux-Can-Get-Viruses-Via-Wine?from=rss]("http://linux.slashdot.org/story/09/10/24/1759213/Now-Linux-Can-Get-Viruses-Via-Wine?from=rss")

---

### Post by movieman on 2010-02-06
> **sig266 said:**
> Can you think of any disadvantages Ubuntu's security in comparison with any other operating system out there as far as: OSX, Solaris, any of the newer windows versions...

Solaris has some very fancy security features built into the operating system: for example, you can configure it so that users can log in at multiple security levels (e.g. 'public', 'confidental', 'secret', 'top secret') and not only will files at a higher level be invisible to users at lower levels, it won't even let you copy and paste between documents at different security level without confirmation. It's over the top for home use, but I can see that it could be very useful for secure environments.

Other things to consider for Ubuntu's security are Apparmor and SELinux, for which there's no equivalent I'm aware of in Windows. They allow arbitrary restrictions on what an application can do, even if it's run as root: so, for example, you can say that an application is only allowed to connect to the Internet and read and write to /tmp and the operating system would automatically prevent it from doing anything else even if it theoretically had complete access to the system because it was run as root.

A properly configured server using either of those technologies is heavily resistant to remote compromise because a hacker might find a bug allowing them to break into, say, the email server software, but couldn't then access anything else on the system (not that a hacker having control of your email wouldn't be bad in its own right, of course, but at least they couldn't then use that power to take over your web server too).

---

### Post by cariboo on 2010-02-06
+1 to what movieman said, you can do the same thing, in Linux, by restricting what privileges sudoers have.

I strongly disagree that enabling the root account makes a system more secure, as a cracker already knows what one of the user names on the system is if root is enabled, then it is only a matter of cracking the password.

If you have an open to the world port on your system, and you use something like denyhosts or fail2ban, you will see that root is one of the first users names that are tried in a dictionary attack.

Like my colleague, bodhi_zazen frequently likes to say, security is like an onion, the more layers there are, the harder it is to crack the system.

I would suggest you read the stickies at the top of the page, as well as having a look at [Recurring Discussions]("http://ubuntuforums.org/forumdisplay.php?f=302"), you may have to do some digging, but there some great threads on security there.

---

### Post by sig266 on 2010-02-06
what security measures would you take if you were running Ubuntu on your organizations server?

---

### Post by movieman on 2010-02-06
> **sig266 said:**
> what security measures would you take if you were running Ubuntu on your organizations server?

Create Apparmor profiles for every server you're running.
Put ssh on a non-default port if it's visible outside the firewall.
Disable password logins for ssh.
If you're using VNC for remote administration, ensure it only listens to localhost and use ssh to forward the ports when you're using it.
99% of web server exploits seem to come through php, I don't know whether there's any way to harden that.

One interesting idea I read in an NSA guide to Linux hardening was to remove global execute permission on programs that only humans should be able to run, and give them group execute permission for a 'humans' group which all human users belong to. Then, for example, if someone manages to hack the web server, the http user won't be allowed to run system admin type programs because it's not part of the 'humans' group.

---

### Post by rookcifer on 2010-02-06
> **movieman said:**
> Solaris has some very fancy security features built into the operating system: for example, you can configure it so that users can log in at multiple security levels (e.g. 'public', 'confidental', 'secret', 'top secret') and not only will files at a higher level be invisible to users at lower levels, it won't even let you copy and paste between documents at different security level without confirmation. It's over the top for home use, but I can see that it could be very useful for secure environments.

This is known as MLS (multi-level security) and can also be done on Linux with SELinux.  And this is not default Solaris behavior; one must have the "trusted solaris extensions" installed.  MLS is typically required in some sensitive government settings, but is rarely used (and not needed) anywhere else.  However, SELinux can do much more than MLS and can be useful at home.

> Other things to consider for Ubuntu's security are Apparmor and SELinux, for which there's no equivalent I'm aware of in Windows. They allow arbitrary restrictions on what an application can do, even if it's run as root: so, for example, you can say that an application is only allowed to connect to the Internet and read and write to /tmp and the operating system would automatically prevent it from doing anything else even if it theoretically had complete access to the system because it was run as root.

SELinux and AppArmor are only two of the [Mandatory Access Control]("http://en.wikipedia.org/wiki/Mandatory_access_control") systems on Linux.  Others are SMACK, Grsecurity, and TOMOYO.  The only ones NOT built into the vanilla kernel are AppArmor and Grsecurity, though AppArmor is working to get included.  Grsecurity doesn't want to be included.

Most would agree that SELinux is the most powerful of the MAC's since it can also do MLS (as I mentioned above), but it also comes with the penalty of being the most complicated.  The easiest to use are TOMOYO and AppArmor.

And Windows does have something *sort of* like a MAC, but not exactly.  This would be the new [Mandatory Integrity Controls]("http://en.wikipedia.org/wiki/Mandatory_Integrity_Control") (MIC) built into Vista and 7.  However, the Windows "MIC" really isn't configurable (unless one wants to do some registry hacks) and has a slightly different goal than MAC's.  MAC's use the [Bell-LaPadula model]("http://en.wikipedia.org/wiki/Bell-La_Padula_model"), whereas Windows and its MIC uses the [Biba model. ]("http://en.wikipedia.org/wiki/Biba_model")

The main difference in the two is that the Bell-La Padula model typically is more concerned with keeping classified material separate from non-classified material (i.e. it is good for government use).  The Biba model is more concerned with data integrity.  However, SELinux, even though it is Bell-La Padula, can achieve both of these goals.  Really, the lines have been blurred a bit between MAC and MIC; they really try to do the same things most of the time (though I think the Windows implementation is weak).

So, OP, I would say write your paper on the differences in the default security of the two.  Read up on Unix file permissions and contrast them with the default Windows permissions.  Read up on ACL's and compare Windows ACL's with Unix/Linux.  Then read up on the MAC systems.  This is where Linux (and other Unices) really sets itself apart from Windows.  You could also research ASLR/NX and other memory hardening features.  These were first used on Linux and later copied by Microsoft.

---

### Post by jflaker on 2010-02-06
[http://www.google.com/search?q=linux+vs+windows+security&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=linux+vs+windows+security&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

Of course, as part of your paper, you will need to verify your "facts".  Many sources and differing comparisons.  

The biggest security difference is the access to system level files and data in windows does NOT require elevated permissions where in Linux you need to have root authority.  At most, under Linux, your damage will be limited to the user's /home/UserName folders.  While that is a problem, any malware or virus will have a hard time rootkitting itself or infecting system files unless the user has bypassed security and has given him/herself fulltime elevated authority or has downgraded permissions on system folders....all of which I have seen.

---

