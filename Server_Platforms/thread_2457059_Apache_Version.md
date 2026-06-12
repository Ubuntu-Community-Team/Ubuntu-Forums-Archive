---
title: "Apache Version"
date: 2021-01-25
forum: Server Platforms
---

### Post by ratman0805 on 2021-01-25
Hi,

i have a question regarding Apache-Versions on Ubuntu-Server.

I'm hosting several Ubuntu Server with different OS-Versions (16.04, 18.04 and 20.04).
From our security department i now got the information that the  installed version are to old and i have to upgrade to Apache 2.4.46.

If i check the installed Apache-Version with the command "apache2 -v" i get different version depending on the OS-Version, but all versions have the same Server built date.
All machines are up to date with newest packages provided by the Ubuntu repositories.

Ubuntu 16.04:
Server version: Apache/2.4.18 (Ubuntu)
Server built:   2020-08-12T21:35:50

Ubuntu 18.04:
Server version: Apache/2.4.29 (Ubuntu)
Server built:   2020-08-12T21:33:25

Ubuntu 20.04:
Server version: Apache/2.4.41 (Ubuntu)
Server built:   2020-08-12T19:46:17

Could it be that the Apache-Version number never change, even the Apache-Package was updated? 
Does the newest build, for example 2.4.18-2ubuntu3.17 for 16.04, includes the official Apache-Version 2.4.46 or all Bugfixes found in Apache-Versions prior 2.4.46?

Or do i have to update Apache to version 2.4.46 with an unsupported ppa like this:
**ppa:ondrej/apache2**

Thanks in advance
Thomas

---

### Post by LHammonds on 2021-01-25
I am unsure about those specific details but rather than design a Frankenstein system, you should look at the bigger picture and upgrade the entire system.

Granted, there could be issues if you are using an outdated application that cannot support newer versions of PHP or Apache but that is also a risk using such software besides just vulnerabilities in services such as Apache.

I would look at how to get your application working on the latest OS/software such as Ubuntu Server 20.04.1 LTS.

If you find that the software you are using cannot be run on the latest version, you need to identify that and document the risk.  If development of that application is too slow or halted, you might want to consider switching to a different application.

LHammonds

---

### Post by rsteinmetz70112 on 2021-01-25
You might want to ask the security department why they want you to upgrade. Is there a specific venerability they are concerned about or do they simply want all versions of everything to be the latest? 
For example 2.4.43 or newer is required in order to operate a TLS 1.3 web server with OpenSSL 1.1.1.

Also you should upgrade any 16.04 LTS instances as it will be EOL shortly.

To answer your original question generally software versions in a Ubuntu LTS are not upgraded but they are patched including security patches. This is done for stability, installing new versions can break things. If you are more interested in keeping everything current then you might want to use the current Ubuntu release 20.10 but you will need to upgrade every 6 months, but even that Ubuntu release may be slightly behind the most current release of some software packages. I haven't checked to see  which version of Apache 2 is included.

---

### Post by ratman0805 on 2021-01-25
Thanks for your replies and your recommendations.

As i said i have different OS-Versions installed, including server 20.04.1.

And also server with 20.04.1 installed are considered insecure by our Security-Scan, because an "old" Apache-Version 2.4.41 is installed.
But this is the newest Apache-Version that i can get from the Ubuntu repositories.
For example, they found the vulnerability **(mod_rewrite potential open redirect (CVE-2019-10098) fixed in Apache 2.4.42)** on my system, because of version 2.4.41.
Do you know how a vulnerability like this (CVE-2019-10098) will be fixed in the Apache-Versions from the Ubuntu repositories.

@rsteinmetz70112 As you wrote **"...but they are patched including security patches"**, do you think/know vulnerability (CVE-2019-10098) or others are patched in Apache-Version 2.4.41 from the Ubuntu repositories.
Are there any official documentations about these patches, that i can send to our Security Department, to show them that it is fixed in my installed version?

Thanks in advance
Thomas

---

### Post by deadflowr on 2021-01-25
> Do you know how a vulnerability like this (CVE-2019-10098) will be fixed in the Apache-Versions from the Ubuntu repositories.
Been patched for years:
[https://ubuntu.com/security/notices/USN-4113-1]("https://ubuntu.com/security/notices/USN-4113-1")

Edit: I should add this too, [https://ubuntu.com/security/CVE-2019-10098#:~:text=In%20Apache%20HTTP%20server%202.4,URL%20within%20the%20request%20URL.]("https://ubuntu.com/security/CVE-2019-10098#:~:text=In%20Apache%20HTTP%20server%202.4,URL%20within%20the%20request%20URL.")

because the security notice applied to Ubuntu releases prior to 20.04,
as 20.04 and newer have had the patch included from the get go.

---

### Post by ratman0805 on 2021-01-25
Copy and Paste mistake :oops:
I wanted to ask about the CVE-2020-1927...
But no i can search for it by my own, using the mentioned links from deadflowr

[https://ubuntu.com/security/cve](https://ubuntu.com/security/cve)
[https://ubuntu.com/security/notices](https://ubuntu.com/security/notices)

That's exactly what i need to show my Security-Department that this is fixed in my installed version, even if the version number is not the same like the current Apache Version.

Thanks to everyone for you quick help.

I appreciate it very much :D

---

