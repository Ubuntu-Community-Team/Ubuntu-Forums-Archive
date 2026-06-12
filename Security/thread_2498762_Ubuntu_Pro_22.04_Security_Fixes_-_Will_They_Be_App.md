---
title: "Ubuntu Pro 22.04 Security Fixes - Will They Be Applied To Standard 22.04 Version?"
date: 2024-06-26
forum: Security
---

### Post by marc190511 on 2024-06-26
Hello,

We have a Linux Virtual Machine running on our Azure estate with Microsoft Defender for Endpoint deployed in active mode for security threat detection and automatic remediation. We are considering upgrading the current cross-platform OS, Ubuntu, to Ubuntu Pro to access the Enhanced Security Measures (ESM) packages as PEN testing has identified several security vulnerabilities which are as follows:

The packages are as follows:

**ImageMagick**
imagemagick_8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3
imagemagick-6-common_8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3
imagemagick-6.q16_8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3
libmagickcore-6.q16-6_8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3
libmagickcore-6.q16-6-extra_8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3
libmagickwand-6.q16-6_8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3

**OpenEXR**
libopenexr25_2.5.7-1

**Traceroute**
traceroute_1:2.1.0-2

**libde265**
libde265-0_1.0.8-1ubuntu0.3

We have been advised the remediations are available with the Ubuntu Pro 22.04 or later version however unfortunately Microsoft has confirmed that MS Defender for Endpoint is not compatible as MS Defender for Linux has a dependency on systemd which is not available in Ubuntu Pro.

Can I please ask if there is any plan to apply the relevant fixes to these vulnerabilities to the standard Ubuntu version and if so, is there a timeframe for when this would be available?

Many thanks in advance.

Marc

---

### Post by currentshaft on 2024-06-26
First, it's a "pen" test, short for "penetration". Calling it a PEN test is like calling Tor TOR - not right.

Now I have to ask, is the software identified as vulnerable actually being used? Like, can someone demonstrate the risk of having a vulnerable version of traceroute lying around?

And is there even actual security content in these updates? I looked at [https://launchpad.net/ubuntu/+source/traceroute/1:2.1.0-2](https://launchpad.net/ubuntu/+source/traceroute/1:2.1.0-2) and it's a low-priority bug fix only, for example.

Can the requesting team make an objective case for why these updates are necessary?

---

### Post by deadflowr on 2024-06-26
> Can I please ask if there is any plan to apply the relevant fixes to these vulnerabilities to the standard Ubuntu version and if so, is there a timeframe for when this would be available?
No timeframe for something that isn't planned.

---

### Post by 0f4d0335 on 2024-06-27
Hi there, good question. ):P

The patch is available now. And you don't need Ubuntu Pro for 22.04 until 2027.

[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)

You can check the status of the latest packages from here: [https://packages.ubuntu.com/](https://packages.ubuntu.com/)

For example, in 22.04 LTS, the security fix available for ImageMagick is Package: **imagemagick (8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3 and others) [security] [universe]**

See here: [https://packages.ubuntu.com/jammy/imagemagick](https://packages.ubuntu.com/jammy/imagemagick)

However, since it's a universe package, it's **community supported,** which Ubuntu patches in the OS using the ESM program (Ubuntu Pro). Here's an [explanation]("https://askubuntu.com/questions/1452497/what-are-esm-apps-and-how-do-they-relate-to-ubuntu-pro") of what's included.

> The ‘Universe’ repository holds all of the other open source packages in  Ubuntu, from Debian and the Ubuntu community. Universe is a much bigger  repository of over 23,000 packages per release. Historically those  packages came with no security maintenance commitment from Canonical.  Nevertheless Canonical and the Ubuntu community provided best-effort  maintenance for those packages. With the launch of Ubuntu Pro, all of  the packages of Ubuntu Universe get the same security maintenance  commitment from Canonical as packages in Ubuntu Main.

But I believe you don't need the ESM (Ubuntu Pro) version until 2027.

---

### Post by loycekunze on 2024-07-12
> **marc190511 said:**
> Hello,

We have a Linux Virtual Machine running on our Azure estate with Microsoft Defender for Endpoint deployed in active mode for security threat detection and automatic remediation. We are considering upgrading the current cross-platform OS, Ubuntu, to Ubuntu Pro to access the Enhanced Security Measures (ESM) packages as PEN testing has identified several security vulnerabilities which are as follows:
[COLOR=#000000][FONT=Arial]Thanks for the update, I appreciate it. I also would like to help you out and I would like to share the [https://academized.com/do-my-homework](https://academized.com/do-my-homework) website with all of you. If anyone over here is looking for an essay writer who will do your homework for you then you can visit the given link where you will find a professional essay writer easily. I am also using that website link and they never disappointed me.[/FONT][/COLOR]
The packages are as follows:

**ImageMagick**
imagemagick_8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3
imagemagick-6-common_8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3
imagemagick-6.q16_8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3
libmagickcore-6.q16-6_8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3
libmagickcore-6.q16-6-extra_8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3
libmagickwand-6.q16-6_8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3

**OpenEXR**
libopenexr25_2.5.7-1

**Traceroute**
traceroute_1:2.1.0-2

**libde265**
libde265-0_1.0.8-1ubuntu0.3

We have been advised the remediations are available with the Ubuntu Pro 22.04 or later version however unfortunately Microsoft has confirmed that MS Defender for Endpoint is not compatible as MS Defender for Linux has a dependency on systemd which is not available in Ubuntu Pro.

Can I please ask if there is any plan to apply the relevant fixes to these vulnerabilities to the standard Ubuntu version and if so, is there a timeframe for when this would be available?

Many thanks in advance.

Marc
Thanks for the update, I appreciate it.

---

### Post by deadflowr on 2024-07-12
> For example, in 22.04 LTS, the security fix available for ImageMagick is Package: imagemagick (8:6.9.11.60+dfsg-1.3ubuntu0.22.04.3 and others) [security] [universe]
It's *A* security fix, before the package became part of the pro esm-apps packages.
The security fixes for the non-pro package version is over a year old now.

All the latest fixes require pro.

Main concern I missed the 1st time:
> Microsoft has confirmed that MS Defender for Endpoint is not compatible as MS Defender for Linux has a dependency on systemd which is not available in Ubuntu Pro.
Not sure what pro has to do with that as systemd is core to Ubuntu whether pro is enabled or not.



However I do see your concern when they post rather cryptic comments on the support page saying it supports Ubuntu 16.04 and higher excluding Ubuntu Pro. whatever that means.
I see you posted on microsoft's support page here: [https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/microsoft-defender-for-endpoint-ubuntu-pro-support/m-p/4175494](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/microsoft-defender-for-endpoint-ubuntu-pro-support/m-p/4175494)
I think we shall have to wait for any response or update on what that means.

---

