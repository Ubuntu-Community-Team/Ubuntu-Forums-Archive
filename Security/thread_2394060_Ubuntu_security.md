---
title: "Ubuntu security"
date: 2018-06-12
forum: Security
---

### Post by linux-user-0987 on 2018-06-12
Online/Firewall:

1) How does ufw work? I have enabled it and the settings are set to deny all incoming connections and allow all outgoing.  These settings are secure and restrictive according to this webpage : [https://wiki.ubuntu.com/BasicSecurity/Firewall](https://wiki.ubuntu.com/BasicSecurity/Firewall) .
How can those settings be more secure then to deny incoming and allow outgoing? If all incoming are denied then how am I able to access the internet and download torrents?

2) What are unsafe sites? How can they be used by a hacker?

3) How can someone gain access to my computer remotely? Does a vpn provide any security other than hiding ip address? If someone has my ip address what would they need to do to access my computer?

4) If someone gains access, what can they do? How does not running the system as root help here? If someone has password for sudo, does it become useless?

Operating system:

1) In windows viruses, malwares are exe files. What kind of unwanted software are in linux? Can they be hidden in documents/audio/video files? 

2) Is it true that if I run a program without root privileges, it should not cause any problems? 

3) Are all software downloaded from terminal safe? If I don't have online access and try to install an infected program, can ubuntu tell that it has been edited?

4) How can I tell if a package has been infected/edited?

---

### Post by The Cog on 2018-06-12
> **linux-user-0987 said:**
> Online/Firewall:

1) How does ufw work? I have enabled it and the settings are set to deny all incoming connections and allow all outgoing.  These settings are secure and restrictive according to this webpage : [https://wiki.ubuntu.com/BasicSecurity/Firewall](https://wiki.ubuntu.com/BasicSecurity/Firewall) .
How can those settings be more secure then to deny incoming and allow outgoing? If all incoming are denied then how am I able to access the internet and download torrents?

The firewall is aware of who initiates a connection. If you make an outgoing connection then that's OK and replies to that connection are allowed back in. But if an incoming packet is not associated with an outgoing call, it is not allowed in. 
> 
2) What are unsafe sites? How can they be used by a hacker?
Good question. I don't think any site is really safe, but I think some disreputable ones only exist to attract and infect people. Bad sites try to take control of your PC by delivering malware embedded in their web pages, or conning you into downloading and installing malware.> 
3) How can someone gain access to my computer remotely? Does a vpn provide any security other than hiding ip address? If someone has my ip address what would they need to do to access my computer?
Three common ways: 
1: Connecting to and abusing a service on the computer that is not firewalled. Fortunately Linux opens very few (if any) open services by default.
2: Serving javascript to your browser that uses security flaws in the browser to take control. Keep your browser up to date with security patches.
3: Persuading you to download and open malware files.
A VPN might possible help with 1:, but don't rely on it.
> 
4) If someone gains access, what can they do? How does not running the system as root help here? If someone has password for sudo, does it become useless?

Take control of your computer and use it for criminal activities, read your files and emails, steal your login passwords for other sites (logging into your bank and transferring all your money elsewhere is popular).
If they gain access as you, not running as root means they have more to do before they get full control of the whole computer.
> 
Operating system:

1) In windows viruses, malwares are exe files. What kind of unwanted software are in linux? Can they be hidden in documents/audio/video files? 

In both Linux and Windows, malware can be almost any file type. Executable files of course, but yes they can be hidden in other documents as you say, where they use flaws in the application that opens them.
> 
2) Is it true that if I run a program without root privileges, it should not cause any problems? 

No. They can still read your files and passwords etc. It makes things harder to get full control of the computer though.
> 
3) Are all software downloaded from terminal safe? If I don't have online access and try to install an infected program, can ubuntu tell that it has been edited?

Software from the Ubuntu repositories is normally considered safe (we trust the suppliers and we're already running their OS anyway), and the installer checks the digital signature to make sure it is not corrupted. Software you download from anywhere else, do you trust the people supplying it?
> 
4) How can I tell if a package has been infected/edited?
Ubuntu packages are digitally signed. Many other downloads provide the checksum on their download site, read about sha256sum. You still have to decide if you trust them though.

---

### Post by TheFu on 2018-06-23
Any answer to each of those questions will have to be very general.  Best advice is to read all the "sticky threads" in the Security subforum to gain that background.  Then follow any terms that aren't understood and read up on each of those till understanding is achieved.   Repeat over and over. After 5 yrs, you'll likely have gained enough background to understand the answers to most of those questions.

Windows viruses are not just EXE files, BTW. They come as DLLs, bogus data that modifies running DLLs and in a number of other forms.

Not using root/sudo does help avoid total system problems, but it doesn't prevent user-inflicted issues.

If you manually download any program/package, it is impossible to trust it, unless it is source code and you are both qualified and take the time to review all the code involved. Thatt's where  trusted repositories, like most Linux distros have, comes into play.  If a trusted person who builds packages that have been trusted decides to change their ways and become "evil", that will probably get very far, depending on the specific package.   Google "linux package signing" for more details about the trust model used.  There are many subtle parts to the model that are not obvious.

Unsafe sites?  There are millions. At any instance, a previously "trusted site" can be hacked to provide bad content that can be harmful to computers. Big sites have been hacked and done this. There are over a million sites running wordpress today that have been hacked and are being used for bad stuff right now.  The owners of those sites may not know or they simply may not care. As long as their site keeps working, having part of it used for phishing by internet gangs is fine to the owners.  

There are millions of ways to attack and own someone elses server.  There will never be a perfectly secure server on a network anywhere.  Security is about mitigating the most likely risks as best we can.  There isn't any 100% certain  way to secure a networked server.

But all these scary things are mostly handled for use end-users by the way that Unix security works, how software maintenance is generally performed on Linux systems using vendor provided repositories.  The primary things a Linux user should do to have the most secure system they can are:
* stay patched; stay on currently supported releases.  Ubuntu LTS is the easy answer.
* have daily, automatic, versioned backups
* use a firewall on your router (yes, you need a separate HW router); keep that router patched at least monthly. If there aren't monthly patches for the router, then that vendor is failing in their patching.
* use a software firewall on your computer if you have any open services.  Block brute force attacks and make passwords useless for authentication. Use key-based auth whenever possible, not passwords.

That should be enough for now.

---

