---
title: "How to patch a specific patch"
date: 2020-02-20
forum: Security
---

### Post by dtesco on 2020-02-20
Hi,

I am a newbie to patching in Ubuntu and I'm trying to patch for CVE-2019-14835.     When I do "apt list --upgradeble | grep -i security",  the system tells me that "0 updates are security update".  Yet our vulnerability scanner tells me that this system has the CVE-2019-14835 vuleralbility.

So I am trying to download the necessary patch file and apply it.  But I haven't a clue how that's done.  It seems like a Kernel patch so it seems I may have to recompile the Kernel at one point but what tools are available or method is used to apply one off patches like that in Ubuntu.  Any help would be appreciated.

Thanks,

Dave

---

### Post by guiverc on 2020-02-20
You didn't mention for which release, as your system may already be patched if you check (and have all upgrades applied)

[https://people.canonical.com/~ubuntu-security/cve/main.html](https://people.canonical.com/~ubuntu-security/cve/main.html)

Also if you're using the pending* release; it'll be simpler to just use *-proposed* anyway.

---

### Post by EuclideanCoffee on 2020-02-20
I agree with guiverc of course.

Note, on using guiverc's recommended resource, simply search your CVE to retrieve the tabled information.

Some CVEs alone are considered non-critical. Simply Googling it or using the below resources will provide information.

[https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-14835](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-14835)

[https://security-tracker.debian.org/tracker/CVE-2019-14835](https://security-tracker.debian.org/tracker/CVE-2019-14835)

*A buffer overflow flaw was found, in versions from 2.6.34 to 5.2.x, ***[5.3 is the Ubuntu latest desktop for 18.04, so this would affect most users] ***in  the way Linux kernel's vhost functionality that translates virtqueue  buffers to IOVs, logged the buffer descriptors during migration. A  privileged guest user able to pass descriptors with invalid length to  the host when migration is underway, could use this flaw to increase  their privileges on the host.*

Since this flaw escalates a user's privilege, it is quite substantial.

Ubuntu addresses this flaw here.

[https://usn.ubuntu.com/4135-1/](https://usn.ubuntu.com/4135-1/)

[https://usn.ubuntu.com/4135-2/](https://usn.ubuntu.com/4135-2/)

And that is how you research the security flaw, using these tools. :)

If you're unfamiliar with Ubuntu, it may be helpful to know this context. [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

Best of luck. :)

---

### Post by dtesco on 2020-02-21
Thanks for the feedback, guys!   I meant to but forgot to mention the version of Ubuntu on the server.  It's version 18.04.2 LTS.

Following the link  [https://usn.ubuntu.com/4135-1/](https://usn.ubuntu.com/4135-1/)   I come to the recommendation to update the system to the following package versions:

   Ubuntu 18.04 LTS             linux-image-4.15.0-1025-oracle - 4.15.0-1025.28
             linux-image-4.15.0-1044-gcp - 4.15.0-1044.70
             ...   
             ...    
             long list

The problem is 1.  How do I determine which one is the appropriate one for me to use and 2.  How do I update to any one of them?  Clicking on one eventually takes you to a resource which has downloadable files(including tar.gz) but how would you install that on a system that's in operation.

Or do you just do a     "sudo apt-get update"   then "sudo apt-get dist-upgrade" and let the system do the update automatically?

Thanks!

Dave Tesco

---

### Post by deadflowr on 2020-02-21
> Or do you just do a "sudo apt-get update" then "sudo apt-get dist-upgrade" and let the system do the update automatically?

Do that.
Fwiw, there have been kernel updates since the usn-4135 fixes.
It'll grab and install whatever is the latest patched kernel for you automatically.

---

### Post by EuclideanCoffee on 2020-02-21
What apt update and apt upgrade will do is install the latest versions of software, apply patches, and security fixes. The update could do one, two, or all three at once. So you should consider what is necessary when updating. Sometimes an update may stop your web application from working, and you'll need to reconfigure it.

If you can provide anymore information on what you might be doing with the server, I could provide more specific advice. But it appears you simply want to upgrade it like deadflowr recommends.

---

### Post by dtesco on 2020-02-24
Thanks, all!  Using the commands below updated the Kernel and fixed the vulnerability.  
$ sudo apt-get update$ sudo apt-get dist-upgrade

But I would still be interested in knowing what all those different packages represent since they all seem to be addressing the same CVE for the same Ubuntu version?  Are they just produced by different sources?

Thanks,

Dave

---

### Post by deadflowr on 2020-02-24
> But I would still be interested in knowing what all those different packages represent since they all seem to be addressing the same CVE for the same Ubuntu version? Are they just produced by different sources?

They all come from the same source, but different circumstances require different builds and packaging.
Different versions are optimized for the platforms they are built for.

---

### Post by EuclideanCoffee on 2020-02-24
You can locate the sources in your apt folder.

$ cat /etc/apt/sources.list

You may also want to check the /etc/apt/sources.list.d/ folder for any files. These contain sources too.

Apt controls the security with gpg keys, a form of encryption and checksum.

You may add other repositories or create your own. To do this, simply add the deb address to your sources file.

Ubuntu sourced packages can be looked up using the [https://packages.ubuntu.com](https://packages.ubuntu.com) tool. For example: [https://packages.ubuntu.com/bionic/linux-image-generic](https://packages.ubuntu.com/bionic/linux-image-generic)

Here you can check the changelog: [http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-meta/linux-meta_4.15.0.88.80/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-meta/linux-meta_4.15.0.88.80/changelog)

This change log is located on the package page as well.

Good luck with your server administration.

---

