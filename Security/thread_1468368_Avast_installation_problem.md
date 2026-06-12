---
title: "Avast installation problem"
date: 2010-05-01
forum: Security
---

### Post by TXbirder on 2010-05-01
I'm attempting to install Avast anti-virus on my newly-installed KK 9.10. (I know- it's not necessary but I'm paranoid.)    It seems to download OK but when I try to open and install, I get this error message:  Error: Wrong architecture 'i386'   I've tried three times.     The item I'm downloading is: avast4workstation_1.3.0-2_i386.deb  Is this the wrong one?    John

---

### Post by cariboo on 2010-05-01
If you using a 64-bit version, the 32-bit version will not install unless you force it. I would suggest you go back and download the 64-bit version. Look for AMD64.

---

### Post by TXbirder on 2010-05-01
Are you talking about an actual pay-money-for-it virus program?  AVAST website offers these 3 FREE versions:     * avast! Linux Edition (RPM package)     * avast! Linux Edition (DEB package)     * avast! Linux Edition (TAR GZ package)  John

---

### Post by cariboo on 2010-05-02
Personally I have no idea whether it is pay version or not, I just stated that you need a 64-bit version if you are running a 64-bit install.

You do realize that all of the virus scanners scan for Windows viruses only. Clamav claims to scan for Linux viruses, but as of right now there are no Linux viruses in the wild.

If you are having problems installing any third party av applications, that aren't in the repositories, it would be best to check their forums for help, as nobody that answers questions on a regular basis in this sub-forum use an anti virus scanner.

---

### Post by TXbirder on 2010-05-02
You mean that the three items that Avast lists as Linux anti-viruses(listed above) aren't really Linux anti-viruses?   John

---

### Post by Rick B. on 2010-05-02
John,

I tried to install AVAST also but for some reason it is really not compatible with Ubuntu. Also tried to install AVG Free. Same thing; couldn't get it working. 

Instead, I found the Ubuntu BitDefender Antivirua for Unices installation page here:

[https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)

I followed the installation instructions and got it running under 9.10. It works like a charm! Even though so many people say you don't need AV with Linux, try it anyways. 

Also try the ClamAV Virus Scanner and ClamTk (graphical front end for ClamAV). Both are available in the Synaptic Package Manager.

---

### Post by cariboo on 2010-05-02
> **TXbirder said:**
> You mean that the three items that Avast lists as Linux anti-viruses(listed above) aren't really Linux anti-viruses?   John

They are anti-virus programs that run on Linux and scan for Windows viruses. Have a look at [this]("http:///en.wikipedia.org/wiki/Linux_malware") Wikipedia article.

Take note of the first two paragraphs:

> The Linux operating system, Unix and other Unix-like computer operating systems are generally regarded as well-protected, though not immune from computer viruses, compared to Microsoft Windows.

There has not yet been a widespread Linux malware threat of the type that Microsoft Windows software faces; this is commonly attributed to the malware's lack of root access and fast updates to most Linux vulnerabilities.

---

### Post by TXbirder on 2010-05-03
Thank you.  John

---

