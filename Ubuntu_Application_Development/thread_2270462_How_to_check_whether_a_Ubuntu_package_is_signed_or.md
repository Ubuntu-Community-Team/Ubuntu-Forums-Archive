---
title: "How to check whether a Ubuntu package is signed or not ?"
date: 2015-03-23
forum: Ubuntu Application Development
---

### Post by sajeesh-cs on 2015-03-23
What is the way to check whether a debian package is signed or not ,and the publisher who has signed it,  is genuine ? In windows, it is possible and the OS holds the list of genuine publishers. Whether  anything like that is available in Ubuntu ?

---

### Post by ian-weisser on 2015-03-23
Discussed in great detail at [http://debian-handbook.info/browse/stable/sect.package-authentication.html](http://debian-handbook.info/browse/stable/sect.package-authentication.html)

Software distribution and authentication in Linux is NOT like Windows. Analogies may mislead you.
In Windows, you (the sysadmin) are responsible for finding, verifying, and installing software from a publisher website. You need the publisher's signature.
In Ubuntu and other Linux distros, the distro provides preferred tools for finding, verifying, and installing software, AND provides trusted archives/repositories of tested, trusted, compatible software. The distro's archive maintainers verify the source publisher's signature and build the packages separately. You need only the archive key.

The short answer is that apt already checks signatures for you every time using 'apt-key', and complains if a package *isn't* properly signed.
'Properly signed' means an *archive* signature, not an individual developer or project signature, that matches the key on file on your local machine.

Canonical does have a list of genuine publishers...those packages are in the 'partners' repository.

---

### Post by sajeesh-cs on 2015-03-24
What about the .deb packages installed using dpkg ? If I am not wrong, there are no inherent signature checks before installation ,right ?  I think this is an issue ,especially at a time when people have started using Ubuntu for desktops. What do you think ?

---

### Post by ian-weisser on 2015-03-24
I don't think it's an issue.

Dpkg indeed does not know anything about repositories, dependencies, orphans, updates, package caches, marking, pinning, signatures, or many other packaging concepts.
That's why apt does. Dpkg is merely a limited application that installs/uninstalls the packages it's told to...usually by apt. 

The only way dpkg can be used to install malware is via a social-engineering attack ("hey, manually download this file from the internet and then enter this mysterious command, and your password").

---

### Post by sajeesh-cs on 2015-03-24
What I understood is that, there are  no signature checks by the OS. That is not possible also , since the packages themselves don't have any signatures and only the archive has. Am I right ?

---

### Post by ian-weisser on 2015-03-24
> **sajeesh-cs said:**
> What I understood is that, there are  no signature checks by the OS. That is not possible also , since the packages themselves don't have any signatures and only the archive has. Am I right ?

You are right in the specific, irrelevant detail that the uploading developer's signature is not included in the downloaded package.
You are completely wrong if you think adding that developer signature that would be an effective security measure in the Debian/Ubuntu environment.

Using signatures on packages is an *old* technology. It was built into apt and debhelper over a decade ago. Signatures are not perfect - they have flaws, too.
Debian and Ubuntu use *many* methods, including signatures where appropriate, to ensure safe software distribution. All Linux distributions do. 
Providing safe software distribution has been a core task for all serious Linux distributions for decades. It's one of the fundamental reasons that caused Linux distributions to form in the first place, and a main reason why they still exist today.

Are you asking about those many methods to ensure safe packages? Or about packaging?
Or are you asking specifically for information about binary package downloads? Or about how to know whether to trust a source?

---

### Post by sajeesh-cs on 2015-03-26
I will tell about an example. I have downloaded google-chrome-stable_current_i386.deb. When I  extracted the control file,it looks like the following

Package: google-chrome-stable
Version: 41.0.2272.101-1
Architecture: i386
Maintainer: Chrome Linux Team <chromium-dev@chromium.org>.

Without a signature how can the OS verify whether the package owner is Chrome Linux Team indeed ? I could have downloaded that package from any site or else copied from somewhere.? How to check the authenticity of the software ?

---

### Post by ian-weisser on 2015-03-26
> **sajeesh-cs said:**
> Without a signature how can the OS verify whether the package owner is Chrome Linux Team indeed ?

Why would the OS care who the package owner is?

> **sajeesh-cs said:**
> I could have  downloaded that package from any site or else copied from somewhere.?

Yes, *you have the right* to download/install any package from anywhere. You are not locked to any approved source.
You can also install any binaries from any source.
You can also compile any source code you wish from any source.

> **sajeesh-cs said:**
> How to check the authenticity of the software ?

Several ways:
1) By downloading packages from a trusted, signed, source instead of somewhere else.
2) The hash (EXAMPLE: apt-cache show google-chrome-stable | grep SHA1) should match the publisher's.

---

