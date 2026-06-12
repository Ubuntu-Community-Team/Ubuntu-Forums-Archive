---
title: "Ubuntu Home Users Security (friendly) Discussion"
date: 2020-11-24
forum: Ubuntu, Linux and OS Chat
---

### Post by Qassis on 2020-11-24
I am aware this post to my fellow Home Ubuntu users may be anathema (a very bad sin) to many, but it is necessary IMHO at this time.
I hope to begin an ongoing "Home Ubuntu User's security discussion".   I hope to keep the discussion at the home user (not System Administrator) level.  Any tips & tricks discussed should be easily implemented by everyone.  
1st Home Security Issue: IMHO, Antivirus and a few other security tools (i.e. GUFW/UFW firewall) are NEEDED for Ubuntu Home users today.
BTW, the Easiest Antivirus for Ubuntu Home (non-professional) users is ClamTK (the graphic/easy install version of ClamAV antivirus), again IMHO.
Discussion: It USED to be true!  But....
I.  The fact that home Linux users didn't need an antivirus program on Linux in 2012 (2012 Cyber Security Wiki that states AV was not required on Linux) was true. The "Basic Linux Security Wiki" (2012) WAS excellent; but is now obsolete; it is dangerous to follow 2012 security guidance today.  We now  have professional, validated up to date guidance telling us otherwise.
II.  The fact is that today you and I need an antivirus program is also true.   
Below is page 1 of the United States Government's (NIST) list (search results) of over 8,000 Linux Vulnerabilities (most are fixed already, don't panic!).  
I searched simply for "Ubuntu" in this search.   This is only one source's samples; but it is quite extensive and I consider it (all the pages together) complete.
III.  Ubuntu and the Linux Community address EVERY Vulnerability as soon as they are discovered, so in MOST instances even someone NOT using anti-virus will be safe once the fix added, IF they update immediately (that's why i set my Ubuntu to auto-update).  Yet it is possible to protect yourself a bit more even before the fixes are in with a just a few easy to install/use security tools (including ClamTK & GUFW), a future discussion.
IV.  Ubuntu Linux is an extremely secure OS, but you can help yourself with just a few simple tools.
END of my discussion today:  I hope to hear from others.

Below page 1 of over 8,000 'NIST Hits' simply to 'show' what I'm talking about.

Searching for "Ubuntu" in the Vulnerabilities (CVEs) list at NIST (The National Vulnerability Database), I found 8,538 results.
    [https://nvd.nist.gov/vuln/search](https://nvd.nist.gov/vuln/search) 
    (Searched for "ubuntu", first page of many pages is below) 
    (Try searches for "linux" and other (mozilla, firefox, etc.) for more)
    
These vulnerabilities concern Ubuntu or one of the libraries, files, or packages within the distribution, which may be exploited by others.

FIRST PAGE OF UBUNTU (Ubuntu or one of the libraries, files, or packages within the distribution).
```
=======================================    
 Vuln ID     Summary     CVSS Severity
=======================================
In this text dump the above show up after each other like this:
  Vuln ID           i.e. CVE-2020-15710
  Summary           Vulnerability short description
  CVSS Severity   LOW, MED, HIGH, etc.
=======================================

CVE-2020-15710
    Potential double free in Bluez 5 module of PulseAudio could allow a local attacker to leak memory or crash the program. The modargs variable may be freed twice in the fail condition in src/modules/bluetooth/module-bluez5-device.c and src/modules/bluetooth/module-bluez5-device.c. Fixed in 1:8.0-0ubuntu3.14.
Published: November 18, 2020; 10:15:12 PM -0500     V3.x:(not available)
V2.0:(not available)

CVE-2020-16127
An Ubuntu-specific modification to AccountsService in versions before 0.6.55-0ubuntu13.2, among other earlier versions, would perform unbounded read operations on user-controlled ~/.pam_environment files, allowing an infinite loop if /dev/zero is symlinked to this location.
Published: November 10, 2020; 11:15:12 PM -0500     V3.1: 5.5 MEDIUM
V2.0: 2.1 LOW

CVE-2020-16126
An Ubuntu-specific modification to AccountsService in versions before 0.6.55-0ubuntu13.2, among other earlier versions, improperly dropped the ruid, allowing untrusted users to send signals to AccountService, thus stopping it from handling D-Bus messages in a timely fashion.
Published: November 10, 2020; 11:15:12 PM -0500     V3.1: 3.3 LOW
V2.0: 2.1 LOW

CVE-2020-16125
gdm3 versions before 3.36.2 or 3.38.2 would start gnome-initial-setup if gdm3 can't contact the accountservice service via dbus in a timely manner; on Ubuntu (and potentially derivatives) this could be be chained with an additional issue that could allow a local user to create a new privileged account.
Published: November 10, 2020; 12:15:11 AM -0500     V3.1: 6.8 MEDIUM
V2.0: 4.6 MEDIUM

CVE-2020-16122
PackageKit's apt backend mistakenly treated all local debs as trusted. The apt security model is based on repository trust and not on the contents of individual files. On sites with configured PolicyKit rules this may allow users to install malicious packages.
Published: November 06, 2020; 11:15:12 PM -0500     V3.1: 7.8 HIGH
V2.0: 2.1 LOW

CVE-2020-16121
PackageKit provided detailed error messages to unprivileged callers that exposed information about file presence and mimetype of files that the user would be unable to determine on its own.
Published: November 06, 2020; 11:15:12 PM -0500     V3.1: 3.3 LOW
V2.0: 2.1 LOW

CVE-2020-15708
Ubuntu's packaging of libvirt in 20.04 LTS created a control socket with world read and write permissions. An attacker could use this to overwrite arbitrary files or execute arbitrary code.
Published: November 05, 2020; 9:15:12 PM -0500     V3.1: 7.8 HIGH
V2.0: 4.6 MEDIUM

CVE-2020-15703
There is no input validation on the Locale property in an apt transaction. An unprivileged user can supply a full path to a writable directory, which lets aptd read a file as root. Having a symlink in place results in an error message if the file exists, and no error otherwise. This way an unprivileged user can check for the existence of any files on the system as root.
Published: October 31, 2020; 12:15:10 AM -0400     V3.1: 3.3 LOW
V2.0: 2.1 LOW

CVE-2019-8790
This issue was addresses by updating incorrect URLSession file descriptors management logic to match Swift 5.0. This issue is fixed in Swift 5.1.1 for Ubuntu. Incorrect management of file descriptors in URLSession could lead to inadvertent data disclosure.
Published: October 27, 2020; 4:15:19 PM -0400     V3.1: 5.5 MEDIUM
V2.0: 2.1 LOW

CVE-2020-15238
Blueman is a GTK+ Bluetooth Manager. In Blueman before 2.1.4, the DhcpClient method of the D-Bus interface to blueman-mechanism is prone to an argument injection vulnerability. The impact highly depends on the system configuration. If Polkit-1 is disabled and for versions lower than 2.0.6, any local user can possibly exploit this. If Polkit-1 is enabled for version 2.0.6 and later, a possible attacker needs to be allowed to use the `org.blueman.dhcp.client` action. That is limited to users in the wheel group in the shipped rules file that do have the privileges anyway. On systems with ISC DHCP client (dhclient), attackers can pass arguments to `ip link` with the interface name that can e.g. be used to bring down an interface or add an arbitrary XDP/BPF program. On systems with dhcpcd and without ISC DHCP client, attackers can even run arbitrary scripts by passing `-c/path/to/script` as an interface name. Patches are included in 2.1.4 and master that change the DhcpClient D-Bus method(s) to accept BlueZ network object paths instead of network interface names. A backport to 2.0(.8) is also available. As a workaround, make sure that Polkit-1-support is enabled and limit privileges for the `org.blueman.dhcp.client` action to users that are able to run arbitrary commands as root anyway in /usr/share/polkit-1/rules.d/blueman.rules.
Published: October 27, 2020; 3:15:12 PM -0400     V3.1: 7.0 HIGH
V2.0: 6.9 MEDIUM

CVE-2020-15157
In containerd (an industry-standard container runtime) before version 1.2.14 there is a credential leaking vulnerability. If a container image manifest in the OCI Image format or Docker Image V2 Schema 2 format includes a URL for the location of a specific image layer (otherwise known as a &#8220;foreign layer&#8221;), the default containerd resolver will follow that URL to attempt to download it. In v1.2.x but not 1.3.0 or later, the default containerd resolver will provide its authentication credentials if the server where the URL is located presents an HTTP 401 status code along with registry-specific HTTP headers. If an attacker publishes a public image with a manifest that directs one of the layers to be fetched from a web server they control and they trick a user or system into pulling the image, they can obtain the credentials used for pulling that image. In some cases, this may be the user's username and password for the registry. In other cases, this may be the credentials attached to the cloud virtual instance which can grant access to other cloud resources in the account. The default containerd resolver is used by the cri-containerd plugin (which can be used by Kubernetes), the ctr development tool, and other client programs that have explicitly linked against it. This vulnerability has been fixed in containerd 1.2.14. containerd 1.3 and later are not affected. If you are using containerd 1.3 or later, you are not affected. If you are using cri-containerd in the 1.2 series or prior, you should ensure you only pull images from trusted sources. Other container runtimes built on top of containerd but not using the default resolver (such as Docker) are not affected.
Published: October 16, 2020; 1:15:11 PM -0400     V3.1: 6.1 MEDIUM
V2.0: 4.3 MEDIUM

CVE-2020-14355
Multiple buffer overflow vulnerabilities were found in the QUIC image decoding process of the SPICE remote display system, before spice-0.14.2-1. Both the SPICE client (spice-gtk) and server are affected by these flaws. These flaws allow a malicious client or server to send specially crafted messages that, when processed by the QUIC image compression algorithm, result in a process crash or potential code execution.
Published: October 07, 2020; 11:15:12 AM -0400     V3.1: 6.6 MEDIUM
V2.0: 6.5 MEDIUM

CVE-2020-25641
    A flaw was found in the Linux kernel's implementation of biovecs in versions before 5.9-rc7. A zero-length biovec request issued by the block subsystem could cause the kernel to enter an infinite loop, causing a denial of service. This flaw allows a local attacker with basic privileges to issue requests to a block device, resulting in a denial of service. The highest threat from this vulnerability is to system availability.
Published: October 06, 2020; 10:15:12 AM -0400     V3.1: 5.5 MEDIUM
V2.0: 4.9 MEDIUM

CVE-2020-7070
In PHP versions 7.2.x below 7.2.34, 7.3.x below 7.3.23 and 7.4.x below 7.4.11, when PHP is processing incoming HTTP cookie values, the cookie names are url-decoded. This may lead to cookies with prefixes like __Host confused with cookies that decode to such prefix, thus leading to an attacker being able to forge cookie which is supposed to be secure. See also CVE-2020-8184 for more information.
Published: October 02, 2020; 11:15:12 AM -0400     V3.1: 5.3 MEDIUM
V2.0: 5.0 MEDIUM

CVE-2020-7069
    In PHP versions 7.2.x below 7.2.34, 7.3.x below 7.3.23 and 7.4.x below 7.4.11, when AES-CCM mode is used with openssl_encrypt() function with 12 bytes IV, only first 7 bytes of the IV is actually used. This can lead to both decreased security and incorrect encryption data.
Published: October 02, 2020; 11:15:12 AM -0400     V3.1: 6.5 MEDIUM
V2.0: 6.4 MEDIUM

CVE-2020-14378
    An integer underflow in dpdk versions before 18.11.10 and before 19.11.5 in the `move_desc` function can lead to large amounts of CPU cycles being eaten up in a long running loop. An attacker could cause `move_desc` to get stuck in a 4,294,967,295-count iteration loop. Depending on how `vhost_crypto` is being used this could prevent other VMs or network tasks from being serviced by the busy DPDK lcore for an extended period.
Published: September 30, 2020; 3:15:12 PM -0400     V3.1: 5.5 MEDIUM
V2.0: 2.1 LOW

CVE-2020-14377
A flaw was found in dpdk in versions before 18.11.10 and before 19.11.5. A complete lack of validation of attacker-controlled parameters can lead to a buffer over read. The results of the over read are then written back to the guest virtual machine memory. This vulnerability can be used by an attacker in a virtual machine to read significant amounts of host memory. The highest threat from this vulnerability is to data confidentiality and system availability.
Published: September 30, 2020; 3:15:12 PM -0400     V3.1: 8.4 HIGH
V2.0: 3.6 LOW

CVE-2020-14376
    A flaw was found in dpdk in versions before 18.11.10 and before 19.11.5. A lack of bounds checking when copying iv_data from the VM guest memory into host memory can lead to a large buffer overflow. The highest threat from this vulnerability is to data confidentiality and integrity as well as system availability.
Published: September 30, 2020; 3:15:12 PM -0400     V3.1: 8.8 HIGH
V2.0: 7.2 HIGH

CVE-2020-14375
A flaw was found in dpdk in versions before 18.11.10 and before 19.11.5. Virtio ring descriptors, and the data they describe are in a region of memory accessible by from both the virtual machine and the host. An attacker in a VM can change the contents of the memory after vhost_crypto has validated it. The highest threat from this vulnerability is to data confidentiality and integrity as well as system availability.
Published: September 30, 2020; 3:15:12 PM -0400     V3.1: 7.8 HIGH
V2.0: 4.4 MEDIUM

CVE-2020-26137
    urllib3 before 1.25.9 allows CRLF injection if the attacker controls the HTTP request method, as demonstrated by inserting CR and LF control characters in the first argument of putrequest(). NOTE: this is similar to CVE-2020-26116.
Published: September 30, 2020; 2:15:26 PM -0400
```

There are THOUSANDS (over 8000) more.  Again, most are fixed already, this is not a 'the sky is falling' post.....

---

### Post by Qassis on 2020-11-24
Message on top of my post says, 
[[COLOR="#C61919"]**Hello HollyGroveUMC, this sub-forum is for chat, not  support – hence the name. If you need technical help, please post in an  appropriate support sub-forum[/COLOR]** ].  
I am not looking for any  technical help. I'm looking for discussion with other home users on our  needs and concerns.   If we hit a need for tech support, I know to take  it to technical help.
The 'Ubuntu Community Forums' lists that it is,  "The water cooler of UbuntuForums, a place to discuss pretty much  anything (within reason). You will also find our resolution centre,  forum council agenda and much more.".   I thought that sounded like what  I was looking  for.  
Am I on the wrong forum -  I'm looking a place to chat with other home users.   
If I'm on the wrong forum, could somebody please point me to the proper one.
Thanks.

---

### Post by wildmanne39 on 2020-11-24
Hi HollyGroveUMC , as you can see below I get the same message, all users do:

> Hello wildmanne39, this sub-forum is for chat, not support – hence the name. If you need technical help, please post in an appropriate support sub-forum. 
I believe this sub-forum is fine, I did consider moving it to the security sub-forum but this is probably the best sub-forum imo.

---

### Post by QIII on 2020-11-24
Please bear in mind that the Ubuntu Forums is populated by people all over the world, in different time zones.  They have lives and might have been eating a meal, spending time with the family, at work, out for a walk, etc., at the time you posted.

I wouldn't expect any immediate response in a chat area.  So be patient.

By the way, everyone sees that tag line above your post.  For me, however, it says "QIII"

---

### Post by mastablasta on 2020-11-25
AV software mostly scans only for windows viruses, so i am not sure why would you feel more secure using them. maybe rootkit hunter is useful. also clamtk has very poor detection rate and will detect many false positives as well.

best security is backup and some hardening. don't open doors (iptables) if you don't want others to enter. they are closed by default.

can you get hacked in linux? yes. my web server got hacked. how? well a small wordpress plugin i wasn't even using had a security vulnerability. that was reported online on thursday. at that time i checked the server on weekends and ran updates. but they hacked me on Friday. on Friday server started sending out spam and spread the botnet. host spotted unusual activity, blocked it and notified me. for some reason their backup didn't work, so we had to use a year old one in combination with theirs to restore the site.

lesson: 

[LIST]
[*]use a malware scanner - scanner compares my files with the original ones
[*]use a service that will let you know when you should update and will warn of strange activity
[*]make another set of automated backups by myself (monthly & weekly)
[*]lock down as much files as possible to read only
[/LIST]

result was a bunch of hackers a day being stopped.

advice for home user:

[LIST]
[*]careful what you download and from where
[*]if you installs services that provide access from outside, use a firewall to manage the connections
[*]if you have a router firewall, utilise that as well.
[*]use good passwords (password managers will help with that)
[*]if possible use secure connections (e.g. no FTP only sFTP)
[*]most importantly - do regular, automated backups. to multiple locations. if possible make an offline backup to unplugged hardware as well. also test the restore process and keep it simple.
[/LIST]

plenty of hardening lists like this one: [https://gist.github.com/lokhman/cc716d2e2d373dd696b2d9264c0287a3](https://gist.github.com/lokhman/cc716d2e2d373dd696b2d9264c0287a3)

---

### Post by DuckHook on 2020-11-25
As a self-described home user you are operating under a number of common misconceptions:
> **HollyGroveUMC said:**
> II. The fact is that today you and I need an antivirus program is also true.
The "truth" of this claim is unsubstantiated. As it stands, it is just a declaration. On what, in detail, are you basing your conclusion?
> III. &#8230;Yet it is possible to protect yourself a bit more even before the fixes are in with a just a few easy to install/use security tools (including ClamTK&#8230;
Please describe in detail how you think ClamAV works. By what specific mechanism(s) does it offer additional protection?

[list=1]
[*]Most Linux power users on these forums are well aware of Linux CVEs. The number of CVEs is irrelevant. What *is* relevant is how many remain outstanding.
[*]ClamAV works by identifying viral signatures in files. It does *not* identify bugs, OS holes or defects. Please conduct this thought experiment: supposing that a significant proportion of those CVEs go unfixed&#8212;just how would ClamAV help?
[*]ClamAV would not identify any of the CVEs that you listed, nor, likely, any of the other 8,000 you allude to. If an attacker could gain entry into your system by exploiting a hole&#8212;say, the infamous "heartbleed"&#8212;no "signature" exists to give away such a compromise.
[*]Since ClamAV only scans for viral signatures, please cite the Linux virii that it catches. (HINT: there are practically none in the wild.)
[/list]
> IV. Ubuntu Linux is an extremely secure OS, but you can help yourself with just a few simple tools.
[list=1]
[*]Linux is not an "extremely secure OS". It is only marginally more secure than Windows. *Any* OS can be compromised and it can be done with ease. One of the most dangerous beliefs is that Linux is magically more secure. For many general users this belief leads to a false sense of security.
[*]The second part of your statement "you can help yourself with just a few simple tools." is incomplete. Security can never be achieved through the installation of tools, simple or complex. Security is all about *behaviours*; the tools are just aids to implement changes in those behaviours.
[*]The focus on tools along with the erroneously rosy assessment of Linux security leads uninformed users to focus on the wrong solutions (antivirus) instead of the right ones (updating always, enforcing challenge/response, practicing least privileges, running minimal services, disabling root account and using sudo, sandboxing all network apps, keeping rolling backups, etc).
[*]I understand that your intentions are entirely noble, but I am obligated to point out that there is an element of magic thinking in your claims. They erroneously treat security as an app rather than as a process. 
[/list]
The distinction between "home users" and "system administrators" is also unnecessary. Security is security. It does not vary. It especially has nothing to do with the expertise of the user.

[list=1]
[*]A foolish user will eventually infect his computer and antivirus *will not stop this*. It is his *behaviour* that will get him in trouble. A foolish sysadmin will inevitably court disaster irrespective of his years of expertise.
[*]A wise user will avoid infection and antivirus won't make a sliver of a shred of an ounce of difference. It is her *behaviour* that will keep her out of trouble. A wise home user is unlikely to have to deal with malware irrespective of how inexperienced she is.
[/list]
There is only one way to attain hardened security: one must put in the work, the learning and, most of all, the behaviour modifications. There are no tricks. There are no shortcuts. There are no magic apps. There are no antivirus, antibiotics or antihistimines.

The proprietary antivirus industry has successfully conditioned users in the proprietary world to shell out good coin for their wares. This is very profitable for them, which, in itself, is not a problem. In the Windows world, it is even necessary. But it incentivizes them to keep marketing their products as magical solutions. This marketing, which is a blend of FUD and magic thinking, is very effective and it inevitably worms its way into the Linux sphere too. But within the Linux ecosystem it is destructive in these ways:

[list=1]
[*]It diverts our limited time, effort and resources from things that work to things that don't work.
[*]It perpetuates falsehoods that not only convey a false sense of security, but sustain bad habits and risky behaviours.
[*]It chokes up our systems with pointless apps, scripts and background services.
[*]It can actually diminish security by adding apps and services that increase our attack surface.
[*]It wastes the time and resources of the larger Linux community in constantly having to correct misconceptions and slaying invisible dragons.
[/list]
It is true that security has gotten harder since 2012. The advent of phishing, spear phishing, ransomware, SSL poisoning, cross site scripting, tracking images and, not least, opaque proprietary apps with hidden spyware payloads (to mention just a few) have made security a much more sophisticated and involved exercise these days. But the fundamentals remain the same. In all of the above threat vectors, it is our *behaviour* that remains the foremost threat. The good practices of yesteryear have not changed. Good principles of security have not changed. And ClamAV will not help against a single one of these threats any more than it helped against anything eight years ago.

---

### Post by SeijiSensei on 2020-11-25
> **mastablasta said:**
> well a small wordpress plugin i wasn't even using had a security vulnerability
Off topic, but do you give the web server write permissions to the WordPress directories? That's a nice convenience if you use automatic updates, but a big security hole otherwise. I run a little script in the WordPress directory before updating that changes the permissions to enable updates.

```

#!/bin/sh
chmod g+w wp-admin wp-includes wp-content -R
chmod g+w *
echo "Run update now"

```
Then when the update is finished I run
```

#!/bin/sh
chmod u+rwx,g+rx wp-admin wp-includes wp-content -R
chmod g-w *

```

These directories are owned by a different user than the apache pseudo-user. That user is in the same group as the user that owns the web sites.

On topic, I use Ubuntu on client computers with no firewall rules. I rely on my router to limit the exposure of my home network. The only time I use anti-virus software (ClamAV in my case) is on my mail server to scan incoming messages. I've been using Linux on the Internet for 25 years now. The only security breach I've ever had was about twenty years ago when I failed to update a copy of the Apache web server software quickly enough. Since then, nada.

---

### Post by mastablasta on 2020-11-26
> **SeijiSensei said:**
> Off topic, but do you give the web server write permissions to the WordPress directories? That's a nice convenience if you use automatic updates, but a big security hole otherwise. I run a little script in the WordPress directory before updating that changes the permissions to enable updates.


i only receive notice it has to be updated. 

it could be they are unlocked. but maybe not, since i use Sucuri and Wordfence and i think one of them locks down various folders until update. because you go through hardening when you set them up and i locked down all sorts of folders. i forgot which ones, because my wife is now mostly doing checks and updating (it's actually her website).

one of the plugins is doing the malware scan, file integrity... the other one is providing firewall/blocks access to folders etc. only one IP is allowed to access higher functions.

---

### Post by Qassis on 2020-11-30
> **wildmanne39 said:**
> Hi HollyGroveUMC , as you can see below I get the same message, all users do:
I believe this sub-forum is fine, I did consider moving it to the security sub-forum but this is probably the best sub-forum imo.
Thank you.   I have changed my username to Qassis. LUV this forum!

---

### Post by Qassis on 2020-11-30
> **QIII said:**
> 

By the way, everyone sees that tag line above your post.  For me, however, it says "QIII"

Thank you!  Got it.

---

### Post by Qassis on 2020-11-30
DuckHook,

  Quote: [I understand that your intentions are entirely noble, but I am obligated to point out that there is an element of magic thinking in your claims. They erroneously treat security as an app rather than as a process.]

Thank you.  I appreciate your reply.  You made your point well concerning viruses and antivirus programs.  No argument - but I'm a bit more paranoid so will follow the more conservative (for antivirus) guidance at: [https://www.linux.com/training-tutorials/myth-busting-linux-immune-viruses/](https://www.linux.com/training-tutorials/myth-busting-linux-immune-viruses/) and keep running mine.  

  Quote: [The distinction between "home users" and "system administrators" is also unnecessary. Security is security. It does not vary. It especially has nothing to do with the expertise of the user.]

OK.  I was discussing the expertise of casual home users (i.e. no IT background, Senior Citizens, other challenges) verses SysAdmins and CyberSecAdmins.  I'm discussing the fact that many home users have switched to Linux from Windows and are GUI/Desktop only users (no shell/command line).  I want to use this cafe to identify those things casual users can do to improve security a bit.   For example, adding GUFW to easily turn-on their (UFW) firewall.

  Quote: [A foolish user will eventually infect his computer and antivirus will not stop this. It is his behaviour that will get him in trouble. A foolish sysadmin will inevitably court disaster irrespective of his years of expertise.
    A wise user will avoid infection and antivirus won't make a sliver of a shred of an ounce of difference. It is her behaviour that will keep her out of trouble. A wise home user is unlikely to have to deal with malware irrespective of how inexperienced she is.]

Amen.  In addition to the foolish, there are wise folks (including those with no IT background, Senior Citizens, and other challenges) who are just not educated in Cyber Security, but who can follow simple guidance (i.e. installing and using GUFW) and improve their own security. 

  Quote: [There is only one way to attain hardened security: one must put in the work, the learning and, most of all, the behaviour modifications. There are no tricks. There are no shortcuts. There are no magic apps. There are no antivirus, antibiotics or antihistimines.]

I can't argue with you when you are right.  Yet there are Ubuntu users who will not be able to put in the "work" or level of learning to achieve hardened security.  I think the tips from knowledgeable folks like you, mastablasta, and others here CAN help even 'casual' users.
Thanks for the reply, advice, and wisdom.   I look forward to your future posts and insights.
P.S.  As soon as I learn to quote portions of the text in the reply as you did I'll start doing so........  Still searching for 'that' instruction.....

---

### Post by Qassis on 2020-11-30
> **mastablasta said:**
> AV software mostly scans only for windows viruses, so i am not sure why would you feel more secure using them. maybe rootkit hunter is useful. also clamtk has very poor detection rate and will detect many false positives as well.

best security is backup and some hardening. don't open doors (iptables) if you don't want others to enter. they are closed by default.

can you get hacked in linux? yes. my web server got hacked. how? well a small wordpress plugin i wasn't even using had a security vulnerability. that was reported online on thursday. at that time i checked the server on weekends and ran updates. but they hacked me on Friday. on Friday server started sending out spam and spread the botnet. host spotted unusual activity, blocked it and notified me. for some reason their backup didn't work, so we had to use a year old one in combination with theirs to restore the site.

lesson: 

[LIST]
[*]use a malware scanner - scanner compares my files with the original ones 
[*]use a service that will let you know when you should update and will warn of strange activity 
[*]make another set of automated backups by myself (monthly & weekly) 
[*]lock down as much files as possible to read only 
[/LIST]

result was a bunch of hackers a day being stopped.

advice for home user:

[LIST]
[*]careful what you download and from where 
[*]if you installs services that provide access from outside, use a firewall to manage the connections 
[*]if you have a router firewall, utilise that as well. 
[*]use good passwords (password managers will help with that) 
[*]if possible use secure connections (e.g. no FTP only sFTP) 
[*]most importantly - do regular, automated backups. to multiple locations. if possible make an offline backup to unplugged hardware as well. also test the restore process and keep it simple. 
[/LIST]

plenty of hardening lists like this one: [https://gist.github.com/lokhman/cc716d2e2d373dd696b2d9264c0287a3](https://gist.github.com/lokhman/cc716d2e2d373dd696b2d9264c0287a3)

WOW, AWESOME REPLY!   Your response is more like a Ubuntu CyberSecurity Wiki or HOWTO!
I guess my thoughts on using an Antivirus are more along the lines of:  [https://www.linux.com/training-tutorials/myth-busting-linux-immune-viruses/](https://www.linux.com/training-tutorials/myth-busting-linux-immune-viruses/) .
I like ClamTK for 'casual users' because it's literally click to install and can run and update automated.   
LOVED your "Lessons"!   What malware scanner are YOU using?  I'm using Lynis, but it's not the 'click and install/use' app I'm looking for (although super easy install/use).
Your "advice for home user is also outstanding (easy to understand/apply).    
Thank for taking the time to respond, the lessons, advice and links.

---

### Post by DuckHook on 2020-11-30
I appreciate your linking to the site where you obtained your information. It actually clears the air and allows for a more considered rebuttal.

Please note the following:

[list=1]
[*]The author, earlier in his piece, readily concedes that: 
[list=a]
[*]"nearly all malicious email attachments target Windows machines."
[*]Even should such an attachment target Linux, it would need the user to foolishly go along by invoking *sudo* to allow it to install&#8230;
[*]barring which, antivirus has no benefit for the Linux user.
[/list]
[*]So why install it? The author's reason is quickly summarized. To quote him: > &#8230;Have you ever forwarded anything with attachments to another user? If so, is that user a Windows user? If so, you could very well have given that attachment a chance at a successful infection. So why not add a virus scan to your Linux system to avoid such an issue?
[*]The only reason given is to protect **Windows** users. Not Linux users, but Windows users.
[*]He then conflates a completely different issue with the one at hand&#8212;by dragging in specialty uses such as mail servers. How many "non-technical home users" run Postfix or Sendmail servers? None. This is an attempt to compare apples to astronauts. It's a silly and fallacious contrivance.
[/list]
The only reason for installing antivirus, then, is this: Linux users are being asked to protect Windows users from themselves.

This is where the author of that piece and I have a fundamental philosophical disagreement. I think that it's not only unfair to ask Linux users to protect Windows users from the consequences of their choices; it is outright dangerous:

[list=1]
[*]We have no more obligation to shield Windows users from their self&#8209;embraced danger than groundlings have to shield mountain climbers or skydivers. Off&#8209;loading risk onto those who are more prudent constitutes what economists call a Moral Hazard.
[*]Even if we take on such obligations, there is no end to them. Windows users do lots of dumb things. Most turn off challenge/response. They run all sessions with admin privileges. They blindly install mysterious apps from i&#8209;pwn&#8209;you.com. If we are not obligated to protect them from these practices, what makes filtering out their viruses for them the oh&#8209;so&#8209;special exception?
[*]There is no reciprocation. Windows does not read EXT files, recognize NFS network protocols, graciously allow for Linux partitions during installation, play nice with Linux file permissions or attributes. Why must we carry water for Windows' shortcomings when they do nothing for us?
[*]So long as we continue to run cover for Windows, Windows users will have little motivation to adopt better practices or change their own behaviour. We do drunkards no favours by handing them more booze.
[*]As I have already stated, running extra apps and servers is not without cost. It impacts our resources and it increases our own malware risk and attack surface. It undermines the Linux principle of smallest footprint and least services.
[*]It perpetuates myths and falsehoods. It diverts time, effort and resources from the useful to the useless. And in adopting Windows behaviour, it introduces bad habits into the Linux ecosystem.
[/list]
Don't get me wrong: if you want to run AV, it's entirely your call. No one can or should stop you. After all, one of the biggest advantages of Linux is the way it empowers every user's choice. But don't do this out of some vague amorphous feeling that AV is somehow virtuous. It is not. It is best to base our practices and beliefs on facts and sound principles. We avoid all sorts of trouble that way.

It may be that you are motivated by a desire to protect your Windows friends and keep them from danger. This is a commendable motive. One would hope that they derive a better understanding of security from the fineness of your own example than from your antivirus. Who knows? A few of them may even take up Linux. ;-)

Good Luck and Happy Ubuntu-ing!

---

### Post by QIII on 2020-11-30
To DuckHook's excellent missives, I will add this:  Security is not fire-and-forget.  It is an iterative *process* that requires the user's frequent and full attention.

---

### Post by EuclideanCoffee on 2020-11-30
I wish to add that my antivirus scanner picked up the first Linux threat I've seen in an email (and this was at home). :)

---

### Post by DuckHook on 2020-11-30
> **EuclideanCoffee said:**
> I wish to add that my antivirus scanner picked up the first Linux threat I've seen in an email (and this was at home). :)
You are one of our 800 pound security gorillas. If you recommend AV for Linux, I may have to revise my views.

Do you recommend it and, if so, why?

---

### Post by EuclideanCoffee on 2020-11-30
Do I recommend AV for Linux? :/ In theory, it's necessary, but it's difficult to get right. Symantec Endpoint Protection in my opinion has the best product.

---

### Post by mastablasta on 2020-12-01
> **EuclideanCoffee said:**
> I wish to add that my antivirus scanner picked up the first Linux threat I've seen in an email (and this was at home). :)

it could have been false positive. 

also if you care what you open and from whom, email should really not be an issue. gmail scans attachments for example.

but nothing is 100% safe. and security is ongoing process. though we are lazy, so virus scanner helps with that :)

---

### Post by mikodo on 2020-12-03
> **DuckHook said:**
>  Do you recommend it and, if so, why? I would like to hear a response also.  Seems time to review the subject of scanning emails in Linux ... Maybe Claws Mail ...

---

### Post by EuclideanCoffee on 2020-12-03
> 
I would like to hear a response also.  Seems time to review the subject of scanning emails in Linux ... Maybe Claws Mail ...


Depends on your risk tolerance. If you have low risk tolerance, you should be using a third-party email provider like Google to do most of this work for you. Then using an anti-virus scanner for advanced threats, not just malware. There is a Carbon Black version for Linux, but you shouldn't need that as a home user.

You may think that you are safer and more secure when using your own default configurations, but you simply are not. You do not know what threats are lurking on your PC. Even if you only go to Ubuntu Forums all day, there are many chances to become infected with malware that will go undetected.

Finally, if you are high risk tolerance, then you should feel comfortable using Linux with no firewall rules and hosting your own email server for convenience. Not recommended. :)

---

### Post by mikodo on 2020-12-03
> **EuclideanCoffee said:**
>  - what you said - 
Thank you, very much! 

I spent most of the day, reading and thinking about my future online, regarding malware with Linux. I learned a lot about 'nasties' and using Clamd with Claws Mail, among other possible solutions. I am very happy though, to follow advice from people, 'within the know'.  As an old casual user, with a rather low risk for tolerance, I will consider using Gmail again. Here is something I saw today about Google's scanning: 
[https://www.forbes.com/sites/daveywinder/2020/02/28/google-confirms-new-ai-tool-scans-300-billion-gmail-attachments-every-week/](https://www.forbes.com/sites/daveywinder/2020/02/28/google-confirms-new-ai-tool-scans-300-billion-gmail-attachments-every-week/)

---

### Post by Qassis on 2020-12-06
NICE Ubuntu Mate 20.04 eBook!  I just found the eBook (you may already  be aware of it), "Using Ubuntu MATE and Its Applications Ubuntu MATE  20.04 LTS Edition", at:
[http://ftp.labdoo.org/download/Public/manuals/manuals-ubuntu/EN/Using%20Ubuntu%20MATE%20and%20Its%20Applications%203rd%20Edition%20-%20PDF%20Version.pdf](http://ftp.labdoo.org/download/Public/manuals/manuals-ubuntu/EN/Using%20Ubuntu%20MATE%20and%20Its%20Applications%203rd%20Edition%20-%20PDF%20Version.pdf)
Very  nicely done.  For this (old linux user but) newbie to Mate, it contains a lot of great Mate  Options and information in an easy to read (lots of screenshots) format.
I'm  always interested in other's perspective on CyberSecurity.  This eBook  takes a stance on anti-virus similar to many who responded here (I'm the  oddball who sees it different); stating, 
  "Although third-party  antivirus software is available for Linux, it is most frequently used to  scan for infections in files that are being shared with or by Windows  users. Ubuntu MATE is designed to make it difficult for viruses,  rootkits, and other malware to be installed and run without conscious  intervention by you, the user.".
I'm enjoying this ebook and the CyberSecurity links (in previous posts) provide me on this forum.   
Never too old to learn, I appreciate all the views shared here and especially those who went to great lengths to include specific guidance.  Although still using antivirus, I've honed my CyberSecurity Tookbox here.

---

