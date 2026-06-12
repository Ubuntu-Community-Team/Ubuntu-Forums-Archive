---
title: "Zimbra &amp; Ubuntu Server 7.10 How-To"
date: 2008-01-31
forum: Server Platforms
---

### Post by soulskater on 2008-01-31
- Zimbra & Ubuntu Server 7.10 How-To -

During this how-to we will use example.com as domain for easier
explanation of things, this should of course be replaced with your own domain name.

1. Make sure you have Ubuntu Server up and running with static ip and proper dns entries. 

2. Download Latest Zimbra Open Source Edition and unpack it.

3. Add valid mx records to your dns, this is required for Zimbra to work.
	mail.example.com.	A    1.2.3.4
	example.com.		MX 0 example.com.

4. use sudo in interactive mode
	$ sudo -i

5. Install prequisite software reguired for Zimbra
	# apt-get install curl libcurl3 fetchmail libgmp3c2 libstdc++5 openssl libltdl3 ssh openssh-server

6. Start installation of Zimbra
	# ./install.sh

7. Answer yes on following to continue despite wrong ubuntu version
	This platform is UBUNTU7
	Packages found: zimbra-core_5.0.xxx.deb
	This may or may not work

	Install anyway? [N] y

	The system will be modified.  Continue? [N] y

8. Choose default for following questions
	Install zimbra-ldap [Y]
	Install zimbra-logger [Y]
	Install zimbra-mta [Y]
	Install zimbra-snmp [Y]
	Install zimbra-store [Y]
	Install zimbra-apache [Y]
	Install zimbra-spell [Y]
	Install zimbra-proxy [N]

9. Choose yes on following questions
	You appear to be installing packages on a platform different
	than the platform for which they were built

	This platform is UBUNTU7
	Packages found: zimbra-core_5.0.xxx.deb
	This may or may not work

	Install anyway? [N] y

	The system will be modified.  Continue? [N] y

10. Answer no to following question since we don't want mail as @mail.example.com instead we want for @example.com
	DNS ERROR resolving MX for mail.example.com
	It is suggested that the domain name have an MX record configured in DNS
	Change domain name? [Yes] n

11. When installation is done and configuration is showing there are a few thing that must be changed
	- Set correct timezone press 1 => 5 => timezone number => r
	- Set password for admin account press 3 => 4 => set your password => r
	- Change default ldap domain press 2 => 3 => set domain as example.com, not mail.example.com => r
    Finish by pressing a for apply and then press enter on the to following questions
	Save configuration data to a file? [Yes]
	Save config in file: [/opt/zimbra/config.xxx]
    and finally press y to modify the system configuration
	The system will be modified - continue? [No] y

12. Now the system is finishing off and your faced with following question, answer as you please
	Notify Zimbra of your installation? [Yes]

Now you can access the administration through the web via [https://mail.example.com:7071/](https://mail.example.com:7071/)
with user admin and the password you set earlier.
-

---

### Post by K.Mandla on 2008-01-31
Moved to Servers and Security.

---

### Post by notanatheist on 2008-02-12
Howdies, I'm trying to install Zimbra on the current 8.04 alpha. Getting stopped up on "libgmp3". I've installed "libgmp3c2" and "libgmp3-dev" but that doesn't seem to satisfy Zimbra's needs. 

Any suggestions? (other than downgrading which *is* an option if needed)

Could potentially disregard the above. I downloaded the Debian package and not the Ubuntu package. Duh.

---

### Post by soulskater on 2008-02-16
Ok, see that you may have gotten it to work, hope so, post back so others will know.

/Marcus

Btw, sorry for not seeing your post earlier.

---

### Post by notanatheist on 2008-02-16
Just got back around to it today. Personal projects often have to wait for weekends. 

Anyway, same problem. No "libgmp3". Looking at my sources.list I have everything enabled. Any ideas? Does Zimbra in fact run on 7.10? My goal is to run Zimbra and OTRS as well as learn a bit about MYSQL so I'll install 7.10 if I have to.

---

### Post by soulskater on 2008-02-18
I have mine up and runnning on a 7.10.

Did you run this line?
> 
5. Install prequisite software reguired for Zimbra
    # apt-get install curl libcurl3 fetchmail libgmp3c2 libstdc++5 openssl libltdl3 ssh openssh-server
Especially is libgmp3c2 installed?

I don't know about the support for 8.04, can be that it uses newer untested, non offical lib versions and that could be something like that breaks the installation or a missing symbolic link as explained below.

 I have these libgmp3 files under /usr/lib:
libgmp.so.3 (This is a symbolic link to libgmp.so.3.4.1)
libgmp.so.3.4.1

Try to make a symbolic link if the libgmp.so.3 above doesn't exist to the libgmp version you have.

Do like this:
# sudo -i
# cd /usr/lib
# ln -s libgmp.so.x.x.x libgmp.so.3

Test the installation again and see what happens.

/soulskater

---

### Post by notanatheist on 2008-02-20
Had all my links. Even tried recreating them. In the end I blew away the 8.04 alpha and put 7.10 on. Now I'm successfully installing Zimbra. Configuration will be another day.

---

