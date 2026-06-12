---
title: "how do I...sshd with sftp"
date: 2006-12-21
forum: Server Platforms
---

### Post by finite9 on 2006-12-21
Could someone please give me an example configuration and a quick howto for setting up sshd with sftp access?

I have read the man pages on openssh website and am still at a bit of a loss where to start!

I understand that I start sshd with a config file and I need to enable lots of options, but what do I enable?

I need to access my Ubuntu laptop at home from work.  I plan on mostly using FileZilla FTP client on WinXP to access my Ubuntu box, but also want ssh access.

I do not want root access, and I want it to be secure but dont know how to create the tokens needed.

please help.

---

### Post by bluefrog on 2006-12-21
sudo apt-get install openssh-server

that's all, once it is installed you can ssh into your computer.

James

---

### Post by finite9 on 2006-12-21
I already have it installed, but I need to start the deamon don't I?  Is it started as default once openssh-server is installed?

AFAIK this enables my Ubuntu user account to SSH into the box, but there is very littel security with this...I want to limit to external IP addresses, disable root and use some sort of certificate.  Do I really need a certificate?

EDIT: I also want to enable the sftp-server part of sshd, or is this enabled by default?

---

### Post by bluefrog on 2006-12-21
yes to the "is it enabled by default" questions.

"very littel security with this"
hum we're talking ssh here not vnc... so yes you could be brute forced but unless you are multi million dollar company I wouldn't bother that much..

can't log with root by default, and anyway root in ubuntu has no password, so unless you assigned one to root (why? don't ask me, there is no use to do that) you will not be able to log with root even if you enable root ssh login.

"I need to enable lots of options, but what do I enable"
well if you know what you need then why do you ask what you need to enable? you may mean where do you need to do that, in that case in sshd.conf.

man ssh  will be your friend for all options available.

"plan on mostly using FileZilla FTP "
huh? thought you were concerned about security and you are talking about sending login/password in clear over the networks?  maybe you are certainly thinking of sftp access here.

James

---

### Post by finite9 on 2006-12-21
Hi James,

Thank you for your patience in answering my very hastily composed questions :)

Your last post answered most of my questions, but I suppose what I really want to know is, how to I enable IP address only access to heighten security?  Now that I know where the config file is, I suppose I can do a man sshd or something?

When I said Filezilla, I mean of course using SFTP protocol, which Filezilla has support for, and then my account details wont be sent as plain text.  But I also want normal SSH shell access with my normal user account.  Do I need a seperate SFTP account or can I SFTP into sshd with my normal user account?

I was just concerned that maybe the default setup of sshd only had basic security, and I've heard a lot about password/dictionary attacks on sshd servers by botnets and was concerned that maybe my password was not long enough and therefore wanted to increase security a bit on server side.

---

### Post by bluefrog on 2006-12-21
man ssh   or man sshd  (not on linux right now)  for options, you should find the IP options.

sftp = ftp ssh so an account valid for ssh is valid for sftp

sure you can always tighten security, but then if you think your password is not long enough, it is maybe time to start by addressing that problem first :-)

---

### Post by tturrisi on 2006-12-21
On your xp comp you would be better off using WinSCP client instead of filezilla.  You can use either ssh or sftp with WinSCP.  It's a graphical shell that can be setup to look like Norton Commander or Explorer (I prefer commander look).  If use ssh or ssh2 you will be sent the cert by the server, accept it and your xp comp will be the only comp that can connect via ssh to your server.  It would take a cracker 20-50 weeks of full time brute force continous attack and a bucket of luck to crack an 8 character decent password that use upper case, lower case, a number & a special character...maybe longer than that to crack too.

---

### Post by punx45 on 2006-12-21
i use SSH to get to my desktop at home from work.   I installed openSSH in what i believe is a fairly standard configuration (got it from a howto on lifehacker).   I use puTTY for shell access, and WinSCP for SFTP.   both work with the same login.   WinSCP is pretty easy to use.   you can drag+drop files back and forth and it has a built in dialog to execute shell commands that dont involve output.   good for things like a quick chmod or to cd without too much clicking.

also, dont forget to set up a dynamic dns if you need to. (if you dont have a static IP from your ISP or a domain already)

---

### Post by finite9 on 2006-12-22
> **punx45 said:**
> also, dont forget to set up a dynamic dns if you need to. (if you dont have a static IP from your ISP or a domain already)

Yeah, :( Well, I had a DynDNS account, but my router, a Lniksys WRT54GX v2.0 which *supposedly* had support built-in for DynDNS, will no longer update my IP.  I read in the latest Ubuntu newsletter on fridge that there is a no-ip client that does a similar thing to noip.com?  Maybe I will give this a try instead of DynDNS.

Whe using WinSCP, don't you need to have generated a key on the openssh-server first and then transfer that file to the client computer using WinSCP?  Or can I simply start sshd then connect with my Ubuntu account from XP using WinSCP?

---

### Post by finite9 on 2006-12-22
By the way?  Do you reckon it's a sackable offense to open an SSH tunnel from my XP at work so that I can RDP in from home using SSH?   It's not like they say it is forbidden in the IT policy. :)

Sick to death of having to VMware Player an XP VM which sucks up 256MB on a 512MB laptop just so I can start the bloomin' Nortel Contivity Client to RDP in to work as the contract with Nortel doesn't involve giving out the Linux version of the software, only the Windows version, so if an employee asks for the Linux version we have to pay for a second license.

---

### Post by tturrisi on 2006-12-22
Every time I installed openssh I never had to manually generate an individual cert, it was done during the install. For actual certs via a cert authority such as verisign, you must manually generate it.

---

### Post by finite9 on 2006-12-22
I actually just found a good guide for this on UDSF!  Explains how to use ssh-keygen to make 2 keys one of which you transfer to the client...

[http://doc.gwos.org/index.php/SecureSSH](http://doc.gwos.org/index.php/SecureSSH)

---

### Post by MrHorus on 2006-12-22
> **finite9 said:**
> By the way?  Do you reckon it's a sackable offense to open an SSH tunnel from my XP at work so that I can RDP in from home using SSH? 

Probably.

Most companies have clauses that exclude you connecting to most third party networks that are outside of their control and that would seem to include your home network.

---

### Post by punx45 on 2006-12-23
depends on where you work, if you work in a typical office with an IT department and  intranet and all that good office stuff then you might run into trouble.   
im just pluged in to regular old cable broadband. 

heck, in alot of companies its probably against policy to even install unauthorized software, and you would need puTTY or the like for a console ssh session.

---

### Post by lotusleaf on 2006-12-23
"SSHHowto"
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

"AdvancedOpenSSH"
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

"GPGsigningforSSHHowTo"
[https://help.ubuntu.com/community/GPGsigningforSSHHowTo](https://help.ubuntu.com/community/GPGsigningforSSHHowTo)

"Common threads: OpenSSH key management, Part 1
Understanding RSA/DSA authentication"
[http://www-128.ibm.com/developerworks/library/l-keyc.html](http://www-128.ibm.com/developerworks/library/l-keyc.html)

"Common threads: OpenSSH key management, Part 2
Introducing ssh-agent and keychain"
[http://www-128.ibm.com/developerworks/library/l-keyc2/](http://www-128.ibm.com/developerworks/library/l-keyc2/)

"Common threads: OpenSSH key management, Part 3
Agent forwarding and keychain improvements"
[http://www-128.ibm.com/developerworks/library/l-keyc3/](http://www-128.ibm.com/developerworks/library/l-keyc3/)

"Secure Shell"
[http://en.wikipedia.org/wiki/Ssh](http://en.wikipedia.org/wiki/Ssh)

"HOWTO setup a home-server"
[http://gentoo-wiki.com/HOWTO_setup_a_home-server](http://gentoo-wiki.com/HOWTO_setup_a_home-server)

"SSH"
[http://gentoo-wiki.com/SSH](http://gentoo-wiki.com/SSH)

"Index:OpenSSH"
[http://gentoo-wiki.com/Index:OpenSSH](http://gentoo-wiki.com/Index:OpenSSH)

"Automating system administration with ssh and scp Introduction" .PDF
[http://tldp.org/linuxfocus/English/Archives/lf-2003_01-0278.pdf](http://tldp.org/linuxfocus/English/Archives/lf-2003_01-0278.pdf)

"CLI Magic: OpenSSH"
[http://enterprise.linux.com/enterprise/05/02/02/1254222.shtml?tid=89](http://enterprise.linux.com/enterprise/05/02/02/1254222.shtml?tid=89)

"GNU/Linux Command-Line Tools Summary" "Chapter 13. Network Commands"
[http://tldp.org/LDP/GNU-Linux-Tools-Summary/html/remote-administration.html](http://tldp.org/LDP/GNU-Linux-Tools-Summary/html/remote-administration.html)

"Introduction to Linux:" "Chapter 10. Networking"
[http://tldp.org/LDP/intro-linux/html/sect_10_05.html](http://tldp.org/LDP/intro-linux/html/sect_10_05.html)

---

### Post by punx45 on 2006-12-23
holy crap...

Merry Linksmas

---

### Post by chrisfay on 2006-12-24
> Merry Linksmas

Seriously...:p

---

