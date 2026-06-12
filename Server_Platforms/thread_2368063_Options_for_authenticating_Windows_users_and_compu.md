---
title: "Options for authenticating Windows users and computers via Linux"
date: 2017-08-06
forum: Server Platforms
---

### Post by vbowers on 2017-08-06
I have a small home network of 5 Windows computers, two Linux computers, one Mac, and one Windows server that I want to be able to authenticate to a Linux-based file and print server. I may add an additional Linux server or two later on. The key for me is synchronizing logins. I don't want individual logins to each computer and server. Mac support is optional, as it is not used much anymore.

I have been trying to get Samba to work as an NT Primary Domain Controller, but have gotten stuck in configuring it and no one here has offered assistance on my question, so thinking that maybe not many people are using that authentication system, since I've gotten no feedback. So that leads me to, what are people using for authentication on their networks? I need to use a free server system that will support both Linux and Windows systems, enabling authentication across these systems with one username and password per user.  My family, who I'm supporting here, are mid level experience users, but are not IT technical type users, so the system needs to be fairly easy for end users. I'm obviously new to Linux, but have over 20 years of Windows system administration experience in medium to small business settings (up to 500 end users).

I'm open to any suggestions, but I do ask that you have some hands-on experience with the suggestions. I would like to be able to ask real world questions that you could answer regarding whatever system you might suggest.  Thanks for reading this, I've been over 2 months trying different things to slay this dragon and have gotten rather in the dumps over my lack of success. The last thing I want to do is go out and give money to Microsoft to accomplish this.

---

### Post by TheFu on 2017-08-06
Most of the people here are either going to be professionals doing webapp development for internet sites or home users.  Corporate IT folks don't seem to hang out here.

Everyone here is a volunteer.

I know what I've done in the past. I barely touch Windows these days, so seems I don't meet your requirements to comment. Sorry.

---

### Post by vbowers on 2017-08-06
TheFu,
Thanks for your reply, even if you feel you can't help me out. I know that the Linux community is predominately volunteer, I respect that greatly. I have joined a local Linux users group. Nice guys, but seem to fit the same mold as you describe for here.

I'm a home user and am looking to use this at my home. I just have a corporate IT background that (unfortunately) is almost exclusive Windows. Three years ago I had to retire due to a stroke and am doing this a) to solve a need here at home, and b) to add to my geek background. Initially it was to be a fun way to to meet a need, but is turning into a rather big frustration.

Would anyone have suggestions on how to get in touch with Linux people who might use Linux for similar purposes? It would seem to be a perfect match for home and small office networks. Reasonably modest needs (authentication, file and print services) for a small number of users and systems.

---

### Post by TheFu on 2017-08-06
Honestly, for what you have described, Samba4 seems like the best solution on paper.

On most corporate setups, AD is the system of record for end-user authentication.  MSFT hit on something pretty good with their version - plus having 90+% of the desktops helped.

On my network, there are only 2 systems that I login onto via the console with something like a password. All the other systems are accessed via ssh and keys.  Just don't need to know the passwords on those machines very often.  That is pretty normal for Unix systems.

In places with more Unix than Windows, x.500 or openLDAP or NIS+ are often deployed with 3rd party addons to help Windows authenticate. This is for desktops, not so much for server access.  Server access is almost always handled via centralized ssh key management. There are lots of ways to deal with that. Unfortunately, the easy ways require $$$, and the hard ways require skills and effort.

In the Unix security world, if you are still using passwords, you've already lost the security game.

If you want a point-n-click management (NOT setup) and highly marketable skills, look up **FreeIPA**.  I've never run it, but friends who do love it.  In the typical Redhat way, it is made up of projects that require 50 different languages + java.  I would think it is overkill for a home network.  Sadly, the port to non-RH systems isn't finished or isn't stable enough to use, but the clients work for all platforms (I understand).  I've been meaning to setup a CentOS server here just to run FreeIPA - life always seems to get in the way of that plan.

About a year ago, someone wrote up an LDAP howto for Ubuntu Server and posted it in the forums. I don't recall if they cared about Windows or not.  Would be worth searching.  The nice person used scripts, so it should be highly reproducible.

If you want to get in contact with Linux people trying to accomplish the same thing you are, you'll need to find some corporate IT folks with a 50/50 mix of Linux and Windows.  That is pretty rare.

BTW, if you drop the Windows requirement, I'd be willing to work through some of this stuff with you for a Unix-centric solution.  NFS works very well and so does LDAP, it is just the day-to-day LDAP management that is less than nice.  As for printing - I've been using IPP for a long time. No complaints, if your printers support that protocol.

---

### Post by vbowers on 2017-08-06
TheFu,
Thanks for passing on the additional info and comments. I'll look into FreeIPA, the RH requirement isn't an issue for me, possibly even a plus. My son works at a web hosting provider that primarily uses RH and he's looking at getting some RH certs. If he lived closer (1hr away), I'd really go for that, but he's so busy and that far away, not a big help. I'll check out the LDAP option too, but seems like I looked at that when I started and thought it was too much.

Can't drop the Windows requirement, the app's we tend to use on them do not have Linux equivalents. But I do appreciate your being willing to help.

---

### Post by TheFu on 2017-08-06
You can both be on the same machine and share a "screen" to work through issues. [http://wiki.networksecuritytoolkit.org/index.php/HowTo_Share_A_Terminal_Session_Using_Screen](http://wiki.networksecuritytoolkit.org/index.php/HowTo_Share_A_Terminal_Session_Using_Screen)  It is common to admin servers halfway across the planet over the internet.  Direct, local, access is actually less convenient in many situations.

---

### Post by gordintoronto on 2017-08-06
> **vbowers said:**
> ... So that leads me to, what are people using for authentication on their networks?

I suspect that the reason you aren't getting answers is, 99.99% of people here do not do network authentication. My home network has half a dozen computers running a mix of Linux and Windows. I have a file server and shared printer. People log on to their own computer, not "the network".

I have set up personal and public shared folders on the file server using Samba, both on my home network and at the office where we have one Linux-based file server, which is used exclusively for backups of Windows workstations and servers.

Assuming you have installed a member of the Ubuntu family, the version of Samba you have is not even close to being the latest and greatest. It meets my needs, but probably not yours.

Have you run across Zentyal? I had a quick look at it more than a year ago, but it didn't solve the problem I was looking at. However, it might be just the thing in your environment.

---

### Post by volkswagner on 2017-08-07
+1 for SAMBA4. Since you have MS Windows system administration experience, I assume
you're familiar/comfortable with Active Directory.

Following the [SAMBA4 How To]("https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller"), you'll notice it's not recommended to run the file server
on the same server as the Active Directory Domain Controller. It can be done, but there
are limitations and annoyances. 

I suggest if you have hardware available that can be an HyperVisor to host virtual machines
that is an excellent route to take. You can use Hyper-V, KVM, or others. You'll want at least
two VMs (one for ADDC, one fileserver). You can do additional VMs for separate print server and
additional domain controllers (for fun).

If you want to spend less time learning and more time on other things, you can use one of
the pre canned distros like [Univention Corporate Server]("https://www.univention.com/products/ucs/") (based on Debian), [ClearOS]("https://www.clearos.com/") (based on CentOS), or [Zenytal]("http://www.zentyal.org/") (based on Ubuntu). I have only dabbled with the above. I generally stayed clear because the roll your own approach offers a bit more flexibility, compared to the pre canned solutions that have a lot of script magic in the background. One issue I ran into while trying UCS, was I couldn't install 32bit libraries, which means I couldn't install 32bit printer drivers for the CUPS print server to function in my environment (which is why I say they lack flexibility).

Using SAMBA4 as an Active Directory Domain Controller will allow you to administer via RSAT tools on
an MS Windows workstation/Server, including Group Policies.

---

### Post by vbowers on 2017-08-07
Gordintoronto, 
Thanks for the Zenytal suggestion. Hadn't heard of it, so I'll give it a look. I may have to drop my hope of single sign-on, but want to exhaust my options before throwing in the towel.

Volkswagner,
I didn't think to check the SAMBA version on my system, but I certainly will. I am quite familiar with AD, so would like to use those tools. I've simply not been successful getting SAMBA working for me, but perhaps my system isn't running 4. I am planning to deploy all servers as virtual. I have a 16 core, 72GB RAM HP server that I'm going to be using, so it's got the pop to handle a nice number of VM's. I'll also look into the alternate distro's you mentioned, hadn't heard of them. I may find them too limiting, but worth a look.

Thanks guys, you've given me some leads!

---

### Post by TheFu on 2017-08-07
72G of RAM?  I could run over 100 VMs on that!
I've run 20 VMs on 8GB host systems.  If you don't run Windows, you don't need much RAM.

For many family servers, a $35 Raspberry Pi v3 is sufficient to have an email server + nextcloud + news + calendar server. 

When looking for a newer version of Samba4, be certain to look for a reputable PPA first if the repos are too out of date for your needs.

If you go with an all-in-one distro, be careful mixing services that should be on the protected LAN with those that need to be near the WAN.

A rule of thumb I have - if a system isn't being patched weekly, then the maintenance on that system is just a hobby and I don't want it anywhere near the internet.

---

### Post by vbowers on 2017-08-08
TheFu,
Yeah, it's not a modest little system, but I got it for $325 (along with a 325Gb and a 1Tb drive), so couldn't say no. I plan on running a number of servers, production (so to speak) and testing/playing, some of them Windows, some Linux. I also know what you mean about patching; in my working days I handled security (such as it was) for my employer and current patch testing and deployment is something I'm big on. One of the plans I have is weekly inventorying of all of our home systems and ensuring that all are current on patches and anti-malware definitions.

One of the server systems I'm going to be deploying is Sophos UTM. I want to set up some detailed logging of our network traffic, looking for rogue services or malware. We have a number of IoT devices and I want to see just what's flowing via them. I may annoy my family, but I will learn a lot and keep us safer than most at the same time.

After reading through all the comments, last night I cleaned up my Ubuntu system and took a swing at deploying SAMBA4 as an AD DC. So far it's looking like a success. I have started doing some testing of it prior to adding users and systems, but I got stuck running the SMBclient tests. Seems my system didn't have the SMB client installed and when I installed it, it of course wasn't configured for the new domain. I will get it configured yet this week, I hope, and finish the testing. The family and I will be gone for a long weekend, so it may well run over into next week. I will post back how it goes, as so far I'm pretty hopeful.

If this works, I will be demoing this at my local Linux users group later in the year. When I spoke of my needs and efforts at last month's meeting, while no one had much background for assisting me, there was a fair bit of interest in the capabilities of what I was looking to do. So this might be a chance for me to give back to the community, in a small way. I appreciate what you guys have done for me (TheFu, Gordintoronto, and volkswagner) in ideas, suggestions, and comments. Much appreciated!!

---

### Post by TheFu on 2017-08-08
> **vbowers said:**
> TheFu,
Yeah, it's not a modest little system, but I got it for $325 (along with a 325Gb and a 1Tb drive), so couldn't say no. I plan on running a number of servers, production (so to speak) and testing/playing, some of them Windows, some Linux. I also know what you mean about patching; in my working days I handled security (such as it was) for my employer and current patch testing and deployment is something I'm big on. One of the plans I have is weekly inventorying of all of our home systems and ensuring that all are current on patches and anti-malware definitions.

One of the server systems I'm going to be deploying is Sophos UTM. I want to set up some detailed logging of our network traffic, looking for rogue services or malware. We have a number of IoT devices and I want to see just what's flowing via them. I may annoy my family, but I will learn a lot and keep us safer than most at the same time.

After reading through all the comments, last night I cleaned up my Ubuntu system and took a swing at deploying SAMBA4 as an AD DC. So far it's looking like a success. I have started doing some testing of it prior to adding users and systems, but I got stuck running the SMBclient tests. Seems my system didn't have the SMB client installed and when I installed it, it of course wasn't configured for the new domain. I will get it configured yet this week, I hope, and finish the testing. The family and I will be gone for a long weekend, so it may well run over into next week. I will post back how it goes, as so far I'm pretty hopeful.

If this works, I will be demoing this at my local Linux users group later in the year. When I spoke of my needs and efforts at last month's meeting, while no one had much background for assisting me, there was a fair bit of interest in the capabilities of what I was looking to do. So this might be a chance for me to give back to the community, in a small way. I appreciate what you guys have done for me (TheFu, Gordintoronto, and volkswagner) in ideas, suggestions, and comments. Much appreciated!!

I'm certain everyone here is happy to hear something useful came from it.  I know I've learned by reading all the responses too!

Be careful running multiple services on the same system (inside the same VM or on the same subnet) when they really belong elsewhere.  I'm concerned about UTM stuff.  Had a few clients burned by them over the years.  Security has to be layered and conveying a clear "no silver bullet" to the end-users is mandatory.

IoT ... ouch.  I've avoided them for the most part, though I've had a Roku and SIP ATA for a long time. Those devices are on a special subnet, alone.

CIFS security will always be an issue.  For your environment, there isn't much that can be done.

---

### Post by vbowers on 2017-08-08
Yeah, I subnet wireless from wired, servers from clients, etc. For home I don't go *too* crazy, but that's a matter of opinion. I host no external facing systems, firewalled off everything inbound, but still try to be careful.

Have run into a snag on the SAMBA AD DC. Seems that when I ran the SAMBA install ([COLOR=#000000][FONT=monospace]samba-tool domain provision --use-rfc2307 --interactive), it did not create a krb5.conf file. Or if it did, it didn't do so at the location specified in the documentation at [/FONT][/COLOR]https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller.  Supposedly this was done in a [COLOR=#000000][FONT=monospace]/usr/local/samba/private/ folder, but there's no "samba" folder in the /usr/local/ area. Consequently, no working Kerberos. My other tests of the setup work, but not Kerberos.

Pretty sure the file got created, but gotta believe it landed somewhere else. Now I get to learn how to look through all the file folders on a Linux install to see where this puppy landed. Can't have it all go perfectly![/FONT][/COLOR]

---

### Post by TheFu on 2017-08-08
Distros move things around.

Projects tend to assume everyone is installing using their source code packages.

Distros put system-level settings into /etc/

Projects put system-level settings into /usr/local/etc/

Of course, all these locations can be overridden at run-time either by environment variables, config files or command line options.  Usually, it is just easier to go with the distro installs and let them put things into /etc/.

How and why different directories are used is VERY WELL THOUGHT OUT over the decades by Unix people.  For Linux, there is a file system hierarchy document (the wikipedia article is a nice summary).  If you plan to be an admin, reviewing that document is mandatory.  

Disk storage can be local, local-access-only, remote, read-write or read-only.  Files can be system specific, specific to a family of OSes, specific to a specific type of CPU, etc.  It was common for /usr/local/ to be an NFS mount and shared by all the similar systems on a network, for example.  Upgrade the programs in 1 place and 200 workstations all got the update.  /var and /etc must be local storage (or at least unique to a specific OS running instance).  Anyway, there are specific reasons for where and why each directory is on a specific storage and in a specific location.

Make sense?

Oh ... and the 'tree' command will be your friend, but definitely take a look at this: [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) for an overview.

---

### Post by gordintoronto on 2017-08-08
Pragmatic answer:
locate krb5.conf

---

### Post by vbowers on 2017-08-15
Yup, that was the issue. In order to be sure I [FONT=arial][/FONT]got it right, I removed the old SAMBA setup, following the instructions at [https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller](https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller).  Besides being a good set of instructions on setting up the ADDC, it also explains how to clean up SAMBA before starting the install. THIS time I had a notepad where I wrote down where the install put the d*mn krb5.conf file. Instead of [COLOR=#000000][FONT=monospace]/usr/local/samba/private/ [/FONT][/COLOR] as shown in the example, the Ubuntu install put it at /var/lib/samba/private/. 

Armed with that knowledge, I revised the later link instruction so that it could link to the proper file location and things went much better. Unfortunately not perfectly, just much better. At this point, my server now passes all of the recommended AD DC tests except those for Kerberos, which is frustrating. However, the failures are a bit better. The issue now seems to be in configuring Kerberos to specify the local default domain. Hopefully I will be able to find someone out there with a little bit of experience with Kerberos on SAMBA who can help me with that issue. I won't go into boring details, but I think it shouldn't be too hard to fix.  I am going to do more Googling on my own, but if I can't come up with something after an hour of that, I'll post a question on the board here and at AskUbuntu. Hopefully between the two I can find someone who can direct me to the edit I need.

At this point though, I'm hopeful that I can slay this dragon. Server host resolution for what server is the Kerberos server is working (that's new), both for TCP and UDP, so it SEEMS that I'm pretty much down to one issue, figuring out how to specify to the Kerberos setup what the local default realm is and I should be golden.

It's really odd to me that I have not been able to find a decent set of instructions that give a complete list of services needed and configuration instructions for doing this. Once I'm done and have a working, tested solution, I think I'm going to try to write up a solid process for this. IMHO, this would really help someone with a small office/home network situation have a fairly simple, secure method for authenticating computers and users. But the current state of instructions out there really leaves a bit to be desired. None note that you need to set up time synch for your domain systems, but elsewhere I found information on this creating authentication issues, just like it does in a Windows domain environment. Some instructions show how to link UNIX and Windows groups for authentication, some don't, but it's something you really should do. None note that you should put file and print shares on a separate server, but you should, for a variety of reasons. The info is just too scattered and needs to be brought together somehow. If I get this all working, maybe putting together a blog or site dedicated to this might be worthwhile.

---

