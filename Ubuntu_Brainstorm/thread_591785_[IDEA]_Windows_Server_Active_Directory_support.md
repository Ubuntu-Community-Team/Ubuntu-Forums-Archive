---
title: "[IDEA] Windows Server Active Directory support"
date: 2007-10-25
forum: Ubuntu Brainstorm
---

### Post by stijngysemans on 2007-10-25
if I currently want to use my ubuntu pc to connect to my work windows domain controller, I have to dive into some serious settings files to make it actually work.

In OSX this works pretty neat.
For more information check this out:
[http://www.experts-exchange.com/Apple/Operating_Systems/OS_X/Tiger_Mac_OS_10.4/Q_22155681.html](http://www.experts-exchange.com/Apple/Operating_Systems/OS_X/Tiger_Mac_OS_10.4/Q_22155681.html)

---

### Post by smartboyathome on 2007-10-25
If you would post an explenation for how they do it on OSX without us having to pay for it, I would know what you were talking about.

---

### Post by SonicSteve on 2007-10-25
I would like to see Ubuntu support enterprise environments better. Mainly authenticating to Windows Active Directory domain controllers. It makes it very hard to suggest using it when it can't authenticate against AD security servers. Until this becomes easier I can't recommend it to my school. Truthfully it would be hard anyway because of some windows only apps that we need to use to submit reports to the Government. Reality is though that not properly authenticating to the main servers is a deal breaker.

Apparently it can be setup to authenticate but it's a fairly complicated procedure and it would have to be done on each installation. We have 140 computers, I'm just not doing that.

---

### Post by stijngysemans on 2007-10-26
[http://ubuntuforums.org/showthread.php?t=590991](http://ubuntuforums.org/showthread.php?t=590991)

I posted the same idea.

Moderators: can you join these two threads and make it one?

---

### Post by veratyr on 2007-10-26
If ubuntu is going to break into the enterprise environment then Active Directory support is a must have. +1

---

### Post by amlucent23 on 2007-10-26
Suse does it fairly easily. I think they use just a script. Im pretty sure that script is GPL'd. Or you could just integrate [sadms]("http://sadms.sourceforge.net/")

This is defiantly a feature that IT professionals like myself find missing from Ubuntu.

---

### Post by BrentNewland on 2007-10-26
I would mostly like to see the user switching fixed - if I have two users logged on, I'm in the second account, then I log out of that account, before it switches to the screen saying that the screen is locked, it shows the entire contents of my desktop. Not good.

---

### Post by SonicSteve on 2007-10-26
> **stijngysemans said:**
> [http://ubuntuforums.org/showthread.php?t=590991](http://ubuntuforums.org/showthread.php?t=590991)

I posted the same idea.

Moderators: can you join these two threads and make it one?

Hey I'm all for that it seems to make sense, unless of course it'll get more attention having two threads. :)

---

### Post by Gunner_Sr on 2007-10-27
I think you might want to look at what is happening over in the SAMBA camp. V4 of SAMBA is working towards Active Directory support. I don't think that Ubuntu should be responsible for that, it is more SAMBA.

Cheers.:KS

---

### Post by ddoctor on 2007-10-27
Samba is responsible, yes. They need to make their configuration much easier, and have it work well with AD out-of-the-box, instead of mucking around with the myriad of config options.

However, getting a nice configuration tool that "just works" is a matter for samba AND/OR the distro to handle. Eg, Fedora has a control panel for configuring this (system-config-authentication?). It almost works... but there is nothing like this in Ubuntu.


Moreover, I would like to see the Linux world offer an ALTERNATIVE to the windows login protocols. i.e. provide a server which gives the same power of AD/samba etc, and can administer windows and linux. You'd need to install a separate login client on windows, rather than using built-in ones (like Netware does).

I think Novell is winning on the windows+linux admin... but not with free software.

---

### Post by SonicSteve on 2007-10-28
> **ddoctor said:**
> Samba is responsible, yes. 

However, getting a nice configuration tool that "just works" is a matter for samba AND/OR the distro to handle. Eg, **[COLOR="Blue"]Fedora has a control panel for configuring this (system-config-authentication?)[/COLOR]**. It almost works... but there is nothing like this in Ubuntu.

I was going to point to Fedora as an example also. It's already possible but the mucking about is too much. As a network admin I need something easier than that. If Fedora could do it with the current version of Samba then Ubuntu could also.

---

### Post by 23meg on 2007-10-29
Threads merged.

---

### Post by ddoctor on 2007-11-02
There is a nice little tool called SADMS which can configure a lot of this for you. However, for me it didn't quite work. There are a few other tools out there (authconfig-gtk and the Fedora one)... SWAT also falls into this category.

However, IMHO, these tools present the user with a way to configure the underlying settings - a fairly thin line above them. Their UI's are designed from the perspective of the underlying configuration, not from the use case sysadmins are looking for.

What we want in this scenario is EXACTLY what happens when you join a domain in windows.

Let's look at the UI windows uses:
- system properties
- choose "domain" instead of workgroup
- specify the domain
- click ok
- log in as admin to join domain

That's it. Compare that to the convoluted process Linux users have to go through.

Notice that, from the user's perspective, the above process is basically equivalent to the "net ads join -U Administrator". IMHO, that single command should be all that is required to configure windows auth.


Mac OS X got it right. They have a few more options, but I still found it quite simple to set up. Being based on BSD, there's obviously samba-related stuff going on, but they make it "just work".


From the user's perspective, there should be a very small number of auth settings:
1. System: AD / LDAP / Kerberos / Netware etc
2. domain (or equivalent)


Even if Linux doesn't get this far, these things can be simplified (probably better directed at the samba project):

1. Remove the "winbind use default domain" option. Just figure it out. Look at what windows does.

2. Don't ask for the password server in smb.conf. This is provided in the SRV records in DNS.

3. Turf the /etc/hosts entries for the domain controller - its not necessary. AD servers are required to be properly registered in DNS.

4. id mappings should not need to be configured. Just figure it out.

5. "winbind enum groups/users" should be turfed. Enum groups if this machine is a member of a windows domain.

6. Don't allow overriding of the winbind separator character ("\"). AD usernames are username@domain or domain\username. End of story. I see no value in diverging from this.

7. Read group policy for things like "profile location", folder redirection etc. Use this to determine whether to mount remote home directories, or synchronise roaming profiles.

8. Domain Admins should be sudoers by default. I think even Mac gets this wrong. This should NOT be configured via the /etc/sudoers file. This file should specify that the local "Admins" group can sudo. The Domain Admins domain group should be added to the local Admins group, just like it is on windows.

9. It'd be nice if the local users/groups control panels could find domain users/groups - eg to add domain groups to local groups. SADMS does a nice job of this.

10. pam_mount should support mounting, eg //server/share/* (* = username). Presently, it can only handle //server/*, because it can only mount shares - it can't mount subfolders of shares. This is crap, because who creates a separate share for each user?

You can "remap" or "bind" or something, once mounted, but this is silly. I think this is a limitation of pam_mount and/or 'mount' itself. 

11. Pam is powerful, but confusing. The semantics of the "required/optional/sufficient" keywords attempt to be intuitive, but they are not. This could be simplified, or hidden away, not to be touched. If you need an "advanced pam configuration" dialog, maybe display it as a flowchart. 

The "required/optional/sufficient" etc keywords basically implement a logic control structure - to me, it would be more intuitive to capture this with a script - using if/then/else. 


I think the Samba project focuses more on the technical detective work of handling the protocols, rather than the tools to administer this easily. And, kinda rightly so - the protocols are the hard bit. But someone needs to step in fill this void. SADMS is probably the closest so far.

But this is so important its not funny. Xandros, eg, prides itself on its windows interoperability. Ubuntu doesn't even install samba by default!


I think it might be time for me to join the Samba, SADMS and Ubuntu projects and get this right for people. Seriously, if this one single task was easier, you'd see a lot more Linux in corporate environments.

---

### Post by ddoctor on 2007-11-02
_

---

### Post by jethro10 on 2007-11-05
> **amlucent23 said:**
> Suse does it fairly easily. I think they use just a script. Im pretty sure that script is GPL'd. Or you could just integrate [sadms]("http://sadms.sourceforge.net/")

This is defiantly a feature that IT professionals like myself find missing from Ubuntu.

Even using this I failed miserably.
J

---

### Post by thorin39 on 2007-11-13
SADMS kill my DC :mad:

---

### Post by greenhat on 2007-11-26
I hope this idea gets some legs with Canonical!  I'd really like to use Ubuntu Gutsy at work.  Seems like there are only a couple things I need:

1) Ability to log into a windows domain
2) Ability to communicate with people on Windows Communicator 2005

I've looked at some guides for #1, but they are way too complex for me and I'm not sure they actually do what I'm looking for.

I have also done some searching for a Windows Communicator solution in Ubuntu, but haven't seen anything that looks like it would work.

---

### Post by tjagoda on 2007-11-26
I dont know how much luck the previous poster is going to have with Windows Communicator, but I would love to see some sort of easy AD integration.  It would be a major selling point for me to be able to deploy ubuntu at work.

---

### Post by 23meg on 2007-11-26
This is [being worked on]("https://blueprints.launchpad.net/ubuntu/+spec/windows-authentication-integration") for Hardy.

---

### Post by tjagoda on 2007-11-26
Excellent!!

---

### Post by stijngysemans on 2007-12-28
cool.
Then I can install Ubuntu on my work laptop

---

### Post by Rufe0 on 2007-12-29
this is a must have. full stop.

---

### Post by dboot on 2008-01-16
This sounds perfect for my setup:

"Use Cases: Bill runs a Windows network and would like to use an Ubuntu Web Server. It must authenticate through AD like the IIS server it is replacing. "

Can't wait for 8.04 LTS Server Edition! I was just looking into doing this with 6.06 LTS following [this lengthy tutorial]("http://ubuntuforums.org/showthread.php?t=280702").

---

### Post by ewtesterman@cox.net on 2008-01-18
I used [likewise-open]("http://www.likewisesoftware.com/community/") and it works fine. The only problem so far is I have to find a way to map user ids and all of that, I was hoping that since you are all interested in this maybe we could figure it out. BTW if you use likewise I would recommend that you use a static address while joining the domain, I had it fail several time because network-manager takes to long getting an ip address from the dhcp server. So again I just used a static and then went back to roaming mode after the process is complete. I have to say likewise was the easiest way I have found yet, this is after setting it up by hand (hit and miss), SADMS (failed) ... Anyway I am now authenticating against ad without any problems, and I have the Win2k schema not the 03 one with support for NIS. We are working toward getting all of our servers to that point, but I still have about 20 more to upgrade and 7 of those are DC's.

---

### Post by cprofitt on 2008-01-20
> **stijngysemans said:**
> if I currently want to use my ubuntu pc to connect to my work windows domain controller, I have to dive into some serious settings files to make it actually work.

In OSX this works pretty neat.
For more information check this out:
[http://www.experts-exchange.com/Apple/Operating_Systems/OS_X/Tiger_Mac_OS_10.4/Q_22155681.html](http://www.experts-exchange.com/Apple/Operating_Systems/OS_X/Tiger_Mac_OS_10.4/Q_22155681.html)

It also fairly auto-magic for openSUSE and Fedora as well.

---

### Post by prince_niceguy on 2008-01-22
great news... i too suggested this idea in gutsy pool... good to see things moving in this direction....

eagerly waiting to test/use it...

---

