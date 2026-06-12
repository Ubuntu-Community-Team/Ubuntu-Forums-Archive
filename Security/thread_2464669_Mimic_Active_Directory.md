---
title: "Mimic Active Directory"
date: 2021-07-08
forum: Security
---

### Post by jag77202 on 2021-07-08
We are a small private school and most of our computers are just desktops with no security and control. All are old versions of windows.

 What I like to do is develop the internal Network to be, if I understand, a mimic of active directory where there is a server that controls your login accounts any of the other things that active directory can do...

So basically have an Ubuntu internal Network and desktops that are controlled by a internal server system.

---

### Post by TheFu on 2021-07-08
SAMBA-AD is probably what you want.   The Ubuntu Server documentation explains how to set this up. Start at help.ubuntu.com, choose "Server", you want 20.04.
[https://ubuntu.com/server/docs/samba-active-directory](https://ubuntu.com/server/docs/samba-active-directory)

The native Linux solution would use LDAP or 389directory.  That is also covered in help.ubuntu.com, it is it more complex.

As for keeping systems patched, configured, and installed with the same stuff, that is normally handled using a DevOPS tool like Ansible. 5 or 5000 systems, doesn't matter. Ansible takes about 20 minutes for an experienced admin to pick up.

As with all Unix/Linux skills, there is no jumping into the middle and being told what to point-n-click.  Skills build on other skills over time.  Normally, it requires years.

If I were setting up a new network, I'd start with
[LIST]
[*]DNS w/ ad-blocking
[*]DHCP w/ reservations; any unknown devices would be put onto 
[*]Ansible for DevOPS
[*]Systems monitoring (lots of choices)
[*]Firewalls on all systems, centrally maintained
[*]Router/Firewall to separate traffic between students, teachers, servers onto their on subnets.
[*]Centralized LDAP w/ Kerberos
[*]NFS
[*]Print using IPP
[*]VPN (inbound)
[*]Document management with Nextcloud
[*]Email ... w/ an IMAP server
[/LIST]

Most of these things would be tied into the LDAP for centralized logins and groups.
Most of these should be split into separate services running on different VMs with a few running in containers under a shared VM.
None of these things should be available over the internet without using the VPN for connectivity.

That's off the top of my head.

---

### Post by CharlesA on 2021-07-08
This isn't mentioned yet, but be sure to get the buy-in from upper management before you do any work toward a conversion.

Also get that in writing if you can (email is fine).

The place I'm working at is a 99% Windows shop, but I've got a couple of Debian boxes kicking around for Zabbix, a Wiki, and some Ubiquiti stuff.

I've got a bit of documentation written up, but no one else wants to learn how to deal with it, so I've got to take lead any time they need updates or upgraded.

---

### Post by TheFu on 2021-07-08
I'm assuming a complete conversion - no more MS-Windows, anywhere. If that isn't the situation, best to clarify in the question.

---

### Post by DuckHook on 2021-07-09
> **jag77202 said:**
> …most of our computers are just desktops with no security and control. All are old versions of windows.
I assume that by "old versions of windows", you mean stuff like XP to Win7, all of which are long out of support.

Given that you are using dead OSes with "no security or control" and are connecting them to the Internet, you are currently juggling a collection of old live hand grenades, any one of which can blow up in your face at any time. Connecting such machines together into an internal LAN will only escalate your already considerable risk by another order of magnitude and create a disaster waiting to happen.

I recommend that you either upgrade all machines to a current Windows before taking another step, or convert your whole school to Linux (this may not be possible if you rely on Windows&#8209;based apps to function).

At any rate, trying to implement anything like Active Directory before you straighten out the fundamentals is like building a castle on top of a bog.

---

### Post by coffeecat on 2021-07-09
@jag77202, you described your setup and outlined a similar desired scenario in this thread from last April: [https://ubuntuforums.org/showthread.php?t=2460597](https://ubuntuforums.org/showthread.php?t=2460597) . Yet you did not respond to some helpful suggestions in that thread. Now you ask essentially the same or a similar question with no indication that you have acted on the earlier suggestions. Please respond to those helping you.

---

### Post by danielperez81 on 2021-08-15
I tryied to install SAMBA-AD and it's really good. Thanks for your guide!

---

### Post by kevdog on 2021-08-19
@TheFu

Having recently explored (well more than recently) setting up OpenLDAP server, how does SambaAD compare to lets say an OpenLDAP server?  For Kerberos add-ons -- would you be suggesting like FreeIPA? 

Hey and lastly with Ansible -- yeah it's pretty easy to pick up the basics and run with it pretty quickly, however it's just like any other tool -- basics in 20 minutes but if you want to get good with Ansible and modify jinja templates and things -- be prepared for a lot of reading and trial and error.  Integrating secrets with Ansible took more over 20 minutes having to read through all the documentation and examples.

---

### Post by TheFu on 2021-08-19
I avoid samba. Don't want anything tied to MSFT here. I don't trust the protocols they design from a security standpoint.  For years, AD/Kerberos in the MSFT implementation had a known flaw that everyone ignored.  Guys in black suites showed up at DefCon and had the paper outing the flaws canceled.  Think that was in 2012.  It wasn't until 2015 that mass media learned about this.

Anyways, my use of Samba today is basically just like it was in 1995.  I think FreeIPA is dead now. RH killed it to concentrate on their own, commercial, answer.  The Server Guide has steps to setup openLDAP w/ Kerberos. 
[https://ubuntu.com/server/docs/service-kerberos-with-openldap-backend](https://ubuntu.com/server/docs/service-kerberos-with-openldap-backend)  
When I ran centralized account management here, we used a specialized front-end for user management.  Training users to only change their passwords in the email webapp was our answer. Never attempt to change your password in any other application, though users with Linux accounts could do it there too.  About 10 webapps and logins to about half our Linux servers were from the LDAP system. I has been awhile since I dealt with that.

I think Canonical has dropped the ball on LDAP integration into every part of Ubuntu. A nice administrative GUI that puts all user accounts above 1000 into an LDAP DB really would be a game changer. And having a 1-stop setup to point a system at an existing LDAP would be great.  Alas, that would likely break all their work on SNAPS, since centralized users almost always means using NFS for HOME directories too. Snaps don't work on NFS.

Like most very capable tools, Ansible takes a few minutes to learn enough to be useful and a lifetime to master. I watched their "quick start" video.  
I'd been to training on Puppet and Chef, so I knew how ugly other solutions were. In an all-day class on Puppet, it was clear from the questions that Puppet was worse than the problem it was trying to solve. 
After 4 hours of Chef training, I walked out. We weren't going to use it, that was clear.  
I wanted to use Rexify (the Perl Devops tool), but even with my love for perl, it was just too hard.
Looked at SaltStack, it has the same issues that Chef and Puppet have. Perhaps if we had 500K systems to manage, Salt would be a solution.
For less than 1000 systems, Ansible has the least bonehead architecture choices, IMHO.  There are puppet people who will claim that most of my issues with puppet don't exist anymore.  Fine.  At the time for this decision, puppet was the MSFT of Devops.  By that I mean you will always have a job, with good pay, with much effort, you'll eventually get it to do what you want, and you'll hate your life.
I don't want to say that Ansible it perfect either. Every few years, they had a habit of deprecating stuff we used, which was a pain.  Often, they'd just change the keyword ... perhaps to provide a "consistent" interface. It is always a pain when they had new releases .... we'd need a week to see what it broke.

I didn't find the jinja templates in Ansible difficult at all.  My first "test" use of Ansible was to maintain /etc/hosts files across about 20 systems. I used templates, since each host needed a customized version.  When I was first learning to script stuff on Unix systems, I created a number of scripts that generated code using templates.  The concept is easy, at least for me.  

When I was learning ansible, there weren't 50 versions (many incompatible) of it and millions of out-of-date webpages on the internet. Having the correct documentation for the correct version is step 1.

---

### Post by scorp123 on 2021-08-19
> **TheFu said:**
>  I'd been to training on Puppet and Chef, so I knew how ugly other solutions were. In an all-day class on Puppet, it was clear from the questions that Puppet was worse than the problem it was trying to solve. 

Yeah no kidding!!  Puppet was ... just wow and "ouch!" ](*,)

Definitely NOT going to miss it. Ansible is sooooo much better \\:D/

---

