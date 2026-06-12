---
title: "Securing Ubuntu for Peace of Mind"
date: 2010-06-22
forum: Security
---

### Post by Vimmander on 2010-06-22
Hi all!  I'm not totally new to *nix, since we use Solaris all the time at college.  In fact, I usually use the Unix lab for things like checking email, FaceBook, checking my bank balance, etc etc, almost totally avoiding the Windows lab at every opportunity.  I love the environment, the file management via the Terminal, and just the DIFFERENCES from Windows.  Now, I AM a long time Windows user, and currently have Windows 7 installed on a Dell Inspiron 1501.  I also use McAFee for virus scan, firewall, and other protections.  In fact, I'm so used to needing such a security suite, that I cfind it terribly hard to believe that if I started using Ubuntu as my primary OS, which I'd love to do, that I DO NOT NEED these program suites.  It's almost blasphemous!  I see how Ubuntu, for example, has no viruses because it's not usually a target for malicious intent, and that there's no need for a virus scanner (although I really want to know how it will be handled if the need for one arises).  The one thing that bothers me more than that, however, is the seemingly trivial attention paid to internet and system security.  Now, I'm so darn used to just being able to open McAFee and hit "Stealth" to make my computer as secure as possible without killing my internet connection, that I just can't wrap my head around the firewall in Ubuntu.  Sure, I've messed with it in a VM, but there's just so many utilities that help configure IPtables (Firestarterm lokkit, GUWF, etc etc) that I just can't seem to get anywhere.  So, here's what I want to know:

1.)  Is there a utility out there for manipulating the settings of the Ubuntu firewall such that it's almost as easy as point and click?
2.)  With such a utility at my disposal, am I safe in doing things like online purchasing, paying bills online, managing bank accounts online, etc etc with Ubuntu?
3.)  Is there some add-on fior FireFox, which I also love, that will help protect me from malicious software (malware, spyware, adware), or is that a non-issue in Linux?  I currently use the McAFee SiteAdvisor to get a general idea of a site's safety, and I haven't had an infection in Windows 7 yet.  It usually takes me to a "Do you really want to go to this page?" page before it let's me navigate further, thus giving me an opportunity to back out safely.

I guess I'm just too drawn into the lies of anti-virus companies and full of Windows-based fears.  Can someone, anyone, blind me with the truth here?  I'd really prefer use Ubuntu now that I've had a taste of it.

---

### Post by MCVenom on 2010-06-22
I don't personally use an anti-virus myself; not just because they're not really needed, but because they aren't for catching 'Linux viruses' per se.

As for Firefox, there is NoScript. It'll take some getting used to, though.

---

### Post by bodhi.zazen on 2010-06-22
> **GrogTheDreamer said:**
> Hi all!  I'm not totally new to *nix, since we use Solaris all the time at college.  In fact, I usually use the Unix lab for things like checking email, FaceBook, checking my bank balance, etc etc, almost totally avoiding the Windows lab at every opportunity.  I love the environment, the file management via the Terminal, and just the DIFFERENCES from Windows.  Now, I AM a long time Windows user, and currently have Windows 7 installed on a Dell Inspiron 1501.  I also use McAFee for virus scan, firewall, and other protections.  In fact, I'm so used to needing such a security suite, that I cfind it terribly hard to believe that if I started using Ubuntu as my primary OS, which I'd love to do, that I DO NOT NEED these program suites.  It's almost blasphemous!  I see how Ubuntu, for example, has no viruses because it's not usually a target for malicious intent, and that there's no need for a virus scanner (although I really want to know how it will be handled if the need for one arises).  The one thing that bothers me more than that, however, is the seemingly trivial attention paid to internet and system security.  Now, I'm so darn used to just being able to open McAFee and hit "Stealth" to make my computer as secure as possible without killing my internet connection, that I just can't wrap my head around the firewall in Ubuntu.  Sure, I've messed with it in a VM, but there's just so many utilities that help configure IPtables (Firestarterm lokkit, GUWF, etc etc) that I just can't seem to get anywhere.  So, here's what I want to know:

1.)  Is there a utility out there for manipulating the settings of the Ubuntu firewall such that it's almost as easy as point and click?
2.)  With such a utility at my disposal, am I safe in doing things like online purchasing, paying bills online, managing bank accounts online, etc etc with Ubuntu?
3.)  Is there some add-on fior FireFox, which I also love, that will help protect me from malicious software (malware, spyware, adware), or is that a non-issue in Linux?  I currently use the McAFee SiteAdvisor to get a general idea of a site's safety, and I haven't had an infection in Windows 7 yet.  It usually takes me to a "Do you really want to go to this page?" page before it let's me navigate further, thus giving me an opportunity to back out safely.

I guess I'm just too drawn into the lies of anti-virus companies and full of Windows-based fears.  Can someone, anyone, blind me with the truth here?  I'd really prefer use Ubuntu now that I've had a taste of it.

Wow, that is a wall of text and honestly I did not read it all, sorry lost interest ....

Please see the security sticky at the top of these forums.

Use gufw for a firewall.

see [this thread](http://ubuntuforums.org/showpost.php?p=9459358&postcount=4) for a discussion of online banking.

---

### Post by Vimmander on 2010-06-22
I still fail to see how something like this can be so secure without some kind of major proprietary suite to work with.  Is the safety of online transactions really out of the hands of the user?  Does a firewall really do nothing more than block incoming connections? :confused:  It just doesn't seem possible...I've always needed some kind of multi-component program...I saw the effects of not having one with XP; it was a disaster!  My systems was full of...horrible maliciousness XD  It just seems like none of the utilities available in Ubuntu offer the wide span of control that I'm used to, unless that's all an illusion as well.

---

### Post by MCVenom on 2010-06-22
> **GrogTheDreamer said:**
> I still fail to see how something like this can be so secure without some kind of major proprietary suite to work with.  Is the safety of online transactions really out of the hands of the user?  Does a firewall really do nothing more than block incoming connections? :confused:  It just doesn't seem possible...I've always needed some kind of multi-component program...I saw the effects of not having one with XP; it was a disaster!  My systems was full of...horrible maliciousness XD  It just seems like none of the utilities available in Ubuntu offer the wide span of control that I'm used to, unless that's all an illusion as well.
It just is. :lolflag:

I could explain some concepts or point you in the direction of further reading (like bodhi.zazen says, you might want to skim through that security sticky), but I'll do it after I eat. :P

Just off of the top of my head though, a major plus is the way Ubuntu handles adminstrative priveledges, it doesn't give you a root/admin account by default, and the root account is locked up so hackers, malware and other nasties can't use it.

---

### Post by Rubi1200 on 2010-06-23
These links also make for interesting reading and help explain exactly why Linux is much safer than Windows:

[http://freewebsoftwarereviews.blogspot.com/2007/12/why-linux-is-more-secure-than-windows.html](http://freewebsoftwarereviews.blogspot.com/2007/12/why-linux-is-more-secure-than-windows.html)

[http://ubuntuforums.org/showpost.php?p=6312755&postcount=4](http://ubuntuforums.org/showpost.php?p=6312755&postcount=4)

This link explains how Firefox can be secured:

[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

---

### Post by Vimmander on 2010-06-23
> **bodhi.zazen said:**
> Wow, that is a wall of text and honestly I did not read it all, sorry lost interest ....


Sorry 'bout that.  It's how I got A's in college composition :lol:  I'll be more conservative in the future.

---

### Post by Vimmander on 2010-06-23
> **Rubi1200 said:**
> These links also make for interesting reading and help explain exactly why Linux is much safer than Windows:

[http://freewebsoftwarereviews.blogspot.com/2007/12/why-linux-is-more-secure-than-windows.html](http://freewebsoftwarereviews.blogspot.com/2007/12/why-linux-is-more-secure-than-windows.html)

[http://ubuntuforums.org/showpost.php?p=6312755&postcount=4](http://ubuntuforums.org/showpost.php?p=6312755&postcount=4)

This link explains how Firefox can be secured:

[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

Still curious...If you DO get some kind of Windows or, God forbid, one of the few Linux viruses or some kind of malware, how do you detect and remove it?  Windows tools cerainly won't help  I mean, when you use a program or gain root power to do something, and that's what a malicious program is waiting for, what's going to stop it?  Linux's resistance is strong due to its very nature, I'll agree with that.  But resistance eventually becomes futile, does it not?

---

### Post by yeleek on 2010-06-23
Gosh...

OK malware - chkrootkit or rkhunter (both in ubuntu repos)

AV - Clamav - Useful if sharing files with windows users etc (again in ubuntu rebos).  Though BlackOtaku is correct re viruses in linux.

A firewall restricts incoming and outgoing connections, i.e. what ports can be connected to (or out of) and in which direction.  They also offer protection from Denial of Service attacks (google it).

Suggestion?
Follow this [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) for advise.

XP is a very, very different beast to Linux.  For example by default Windows has ports open to allow files to be copied between machines.  By default Linux has no ports open, so there is nothing for a malicious user to try and connect to on your machine (unless you add software requiring open ports).

---

### Post by deepclutch on 2010-06-23
I've rkhunter ran as cronjob(in case).
and For those Who use pppoe broadband connections in **Bridge Mode**(interface is pppx)  ,Easiest Way is "**arno-iptables-firewall**".Easy to Configure a la reminds legacy "lokkit"(another tool similar).
> Description: single- and multi-homed firewall script with DSL/ADSL support
 Unlike other lean iptables frontends in Debian, arno-iptables-firewall
 will setup and load a secure, restrictive firewall by just asking a few
 question. This includes configuring internal networks for internet access
 via NAT and potential network services (e.g. http or ssh).
 .
 However, it is in no way restricted to this simple setup. Some catch words
 of additional features, that can be enabled in the well documented
 configuration file are: DSL/ADSL, Port forwarding, DMZ's,
 portscan detection, MAC address filtering.
Homepage: [http://rocky.eld.leidenuniv.nl/](http://rocky.eld.leidenuniv.nl/)

---

### Post by bodhi.zazen on 2010-06-23
> **GrogTheDreamer said:**
> Still curious...If you DO get some kind of Windows or, God forbid, one of the few Linux viruses or some kind of malware, how do you detect and remove it?  Windows tools cerainly won't help  I mean, when you use a program or gain root power to do something, and that's what a malicious program is waiting for, what's going to stop it?  Linux's resistance is strong due to its very nature, I'll agree with that.  But resistance eventually becomes futile, does it not?

See the security sticky, there are links to HIDS and NIDS.

Linux is not invulnerable, but you need to do some reading to understand the potential vulnerabilities and monitoring.

In general "antivirus" is a non issue, there are no known active Linux viruses at this time.

In Windows, known vulnerabilities go unpatched for years, and thus you need to rely on third party applications .... 

In Linux your system is patched much faster, and thus if your system is up to date, you are not vulnerable to known viruses.

I suggest you check your windows knowledge at the door and read the security sticky, learn how to use apparmor, learn to use any of the HIDS or NIDS tools you wish.

My point here, Linux security is an issue, but you can not apply Windows security to linux, you need to learn some new tricks.

Keep in mind, most of the HIDS tools have one flaw in common, false positives >> true positives.

The only way to learn this is to run the tools, and do the google search yourself. You will then be able to see for yourself how secure the OS is.

If you do not want to do the foot work, relax and enjoy the OS. Watch for security alerts (the do occur infrequently) for vulnerabilities and fixes.

[USN list | Ubuntu - Security alerts]("http://www.ubuntu.com/usn")

In terms of open/closed source apps:

With closed source apps you have to trust someone (Microsoft) when they claim their OS is "secure". With open source you can examine the code for yourself or rely on the hundreds or thousands of people who watch the code for you. 

The "old school" Uinx sys admins will always tell you to examine the code for yourself. If you want to be as secure as possible, add this skill to your armamentarium.

---

### Post by Vimmander on 2010-06-24
I *think* I finally get it.  The Windows Mindset is hard to break  out of.  All I'm worried about now is the following:

1.)  If, by some stupid thing I do, I get a rootkit and I need to  reinstall, where is such a thing stored?  I have a / and a /home  partition, and a swap area.  It seems like I'd only have to trash the /  partition (which is where programs are saved), and that my /home  directory would be safe.
2.)  Do I need to completely change my surfing style?  I collect  wallpapers from Google Image searches (i.e. right-click/save), and I'm  really used to McAFee scanning the downloads for me.  Of course, I could  renew my firewall, use Win7 to download stuff, then mount the drive in  Ubuntu and copy the files over, but that's a lot of rebooting >.>   There's also Windows utilities that allow ext4 manipulation...

I must admit, I'm still scared out of my mind here...this is so foreign  to me.  At least I can look at your ufw guide and do the enabling and  incoming connection denial commands, bodhi.zazen.  I'll also take a look at those NIDS and HIDS stickies.

---

### Post by yeleek on 2010-06-24
> **GrogTheDreamer said:**
> I *think* I finally get it.  The Windows Mindset is hard to break  out of.  All I'm worried about now is the following:

1.)  If, by some stupid thing I do, I get a rootkit and I need to  reinstall, where is such a thing stored?  I have a / and a /home  partition, and a swap area.  It seems like I'd only have to trash the /  partition (which is where programs are saved), and that my /home  directory would be safe.
2.)  Do I need to completely change my surfing style?  I collect  wallpapers from Google Image searches (i.e. right-click/save), and I'm  really used to McAFee scanning the downloads for me.  Of course, I could  renew my firewall, use Win7 to download stuff, then mount the drive in  Ubuntu and copy the files over, but that's a lot of rebooting >.>   There's also Windows utilities that allow ext4 manipulation...

I must admit, I'm still scared out of my mind here...this is so foreign  to me.  At least I can look at your ufw guide and do the enabling and  incoming connection denial commands, bodhi.zazen.  I'll also take a look at those NIDS and HIDS stickies.

1) If you've got / on a separate partition, then yes you can wipe it and keep /home safe.  However if under some rare occurrence you did get a problem requiring a rebuild I'd personally restore /home from a known good backup (you do backup i trust?)

2) Whoa!  No you do not need to change your browsing habits, software cannot install itself onto your system without asking for permissions - or you being very stupid in the configuration of your box - which before you ask, you'd know if you were doing (things like opening services up to the internet, with a password of 123 for example).  Downloaded files cannot be executed without first being given the permission to do so (a command line tool called chmod).

Seriously, install chkrootkit, rkhunter, clamav, noscript.  Run chkrootkit, rkhunter and clamav occasionally.  Try to only install new software from the Ubuntu repositories (which won't contain rootkits) - except noscript which is a firefox addon.  Most importantly chill and enjoy.

---

### Post by Vimmander on 2010-06-24
> **yeleek said:**
> 1) If you've got / on a separate partition, then yes you can wipe it and keep /home safe.  However if under some rare occurrence you did get a problem requiring a rebuild I'd personally restore /home from a known good backup (you do backup i trust?)

Actually, I don't know how to back up my files in Ubuntu (just /home, right?)...All I have is a 250 GB external drive (smallest I could find >.<), and it has a complete backup and image of my Win7 system prior to shrinking my Windows partition (7's backup process was click, click, go-super easy and hard to screw up).  Would I need to partition that, giving it an ext4 file system in order to back up to it?  Also, if something happens to one of my Ubuntu partitions, can it spread to Win7 and vice-versa?

---

### Post by bodhi.zazen on 2010-06-24
Both root kits and viruses are extremely rare on Linux and worrying about these is almost futile.

Read the security sticky, it has links to HIDS and NIDS threads if you are interested.

Rootkits are installed secondarily, ie there is a primary problem (VNC, SSH, etc) which gives an intruder (basically) shell access. They then download rootkits.

Rootkit scanners can only scan for known rootkits and I would not rely on them to detect a rootkit as any cracker who uses these things would use one or modify it so as not to be detected ...

Rootkits can be downloaded and installed / run most anywhere on the file system, /home and /tmp are commonly used.

Your time is much better spent learning to use Apparmor then using antivirus or rootkit detection.

---

### Post by jdunn on 2010-06-24
> **GrogTheDreamer said:**
> 
3.)  Is there some add-on fior FireFox, which I also love, that will help protect me from malicious software (malware, spyware, adware), or is that a non-issue in Linux?  I currently use the McAFee SiteAdvisor to get a general idea of a site's safety, and I haven't had an infection in Windows 7 yet.  It usually takes me to a "Do you really want to go to this page?" page before it let's me navigate further, thus giving me an opportunity to back out safely.

I guess I'm just too drawn into the lies of anti-virus companies and full of Windows-based fears.  Can someone, anyone, blind me with the truth here?  I'd really prefer use Ubuntu now that I've had a taste of it.

Some helpful tips for firefox:  OpenDNS can filter out URLs that transmit malware.  Use NoScript addon, configure browser to delete cookies on exit AND/OR disable cookies w/whitelist, use BetterPrivacy addon to delete flash cookies on exit.

For Google-Chrome:  Disallow javascript so you can whitelist on a per-page basis (not as fine-grained as NoScript but better than nothing),  configure browser to delete cookies on exit AND/OR disable cookies w/whitelist, create a script to delete flash cookies on exit like this:

```

google-chrome
rm -fr $HOME/.macromedia/Flash_Player/#SharedObjects
rm -fr $HOME/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/

```

I have avast! as a stand-alone virus scanner but I almost feel silly using it as there are very few linux viruses in the wild.  Still, there was a linux virus a few months ago in a waterfall screensaver and windows viruses can still be transmitted to/from linux.  I guess it depends on whether you get software strictly from the trusted repositories.

I'm working on getting apparmor to work.

---

### Post by kevdog on 2010-06-24
Honestly although you probably wont like my answer --  the number one defense against malware, viruses, etc is YOU.  Ubuntu is fairly safe as an OS (as compared to windows).  You can use noscript, firewalls, etc, however just use common sense and don't be browsing and downloading files stupidly.  That should pretty much do the trick, in my humble opinion.

---

### Post by Vimmander on 2010-06-24
I've actually decided to go back to Windows for the time being.  After a week of Ubuntu, I feel that I'm not really ready for something that has so many DIY components, especially in the middle of a database class.  Perhaps I will try again in the future with a later version of Ubuntu, but until then, the LiveCD and VMs will do.  Whoever has the power to do so, please feel free to close this topic, or leave it open for others to discuss these issues.  Personally, I'd delete the whole thing, it's a reminder of my ignorance and I'd hate to have myself as an example of such, but hey, I don't hold the stick here.

Until we meet again.  ):P

---

### Post by bodhi.zazen on 2010-06-24
> **GrogTheDreamer said:**
> I've actually decided to go back to Windows for the time being.  After a week of Ubuntu, I feel that I'm not really ready for something that has so many DIY components, especially in the middle of a database class.  Perhaps I will try again in the future with a later version of Ubuntu, but until then, the LiveCD and VMs will do.  Whoever has the power to do so, please feel free to close this topic, or leave it open for others to discuss these issues.  Personally, I'd delete the whole thing, it's a reminder of my ignorance and I'd hate to have myself as an example of such, but hey, I don't hold the stick here.

Until we meet again.  ):P

Windows is easier to you as it is familiar and came pre-installed.

Most people dual boot as they learn Linux, and some find that they boot Window less and less until one day you realize it has been years, usually when someone has a problem with Windows 7 and they think you know the answer because you are a computer nerd, but as you look at the screen, suddenly windows does not seem so easy.

---

### Post by jdunn on 2010-06-24
Bodhi.Zazen,
I followed your apparmor howto and can't get past a basic stub file.  'genprof <app>' creates the stub and then prompts me to run the app but when I scan, non of the log entries are added to the profile leaving me with a useless stub profile.  please help.

---

### Post by Vimmander on 2010-06-24
> **bodhi.zazen said:**
> Windows is easier to you as it is familiar and came pre-installed.

Most people dual boot as they learn Linux, and some find that they boot Window less and less until one day you realize it has been years, usually when someone has a problem with Windows 7 and they think you know the answer because you are a computer nerd, but as you look at the screen, suddenly windows does not seem so easy.

This is true.  My CS professor hardly ever boots into XP anymore.  He's the one who got me started on Ubuntu, and I still mess with it in Virtual Box.  But yeah, Windows is a bit easier...considering I've used it since 95 came out 15 years ago.  Maybe I'll have more time this winter.  In the mean time, I did pick up a few good security tips to apply to Windows.  Thanks, all!

---

### Post by bodhi.zazen on 2010-06-24
> **jdunn said:**
> Bodhi.Zazen,
I followed your apparmor howto and can't get past a basic stub file.  'genprof <app>' creates the stub and then prompts me to run the app but when I scan, non of the log entries are added to the profile leaving me with a useless stub profile.  please help.

Apparmor takes a while to learn, it does get easier.

I suggest you start a new thread in the security section asking for assistance.

Include the application you are trying to confine and what version of Ubuntu you are using as there are some variations.

Also, check to see if there is already a profile for the application in the Ubuntu repositories. If so, you can use that one or you can use it as an initial template.

---

