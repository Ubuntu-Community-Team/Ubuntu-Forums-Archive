---
title: "Is it possible to get hacked even if incoming connections are denied?"
date: 2011-10-01
forum: Security
---

### Post by arroy_0209 on 2011-10-01
My firewall (using gufw) preferences are: incoming denied, outgoing all denied except to port 80/tcp (http) which is allowed. Is it possible that with this configuration my computer may get hacked? If so, what other changes should be made? 

I am using a router but have no idea how to check its firewall configuration to get an idea how good that one is.

---

### Post by haqking on 2011-10-01
> **arroy_0209 said:**
> My firewall (using gufw) preferences are: incoming denied, outgoing all denied except to port 80/tcp (http) which is allowed. Is it possible that with this configuration my computer may get hacked? If so, what other changes should be made? 

I am using a router but have no idea how to check its firewall configuration to get an idea how good that one is.

**The only guarantee to prevent instrusion is to never connect to outside world**, so to answer your question what changes can be made. There is alot you can do to help secure including use of Sudo, apparmor, IPTables, Tor etc etc.

Please read the following which is my standard answer to such questions ;-)

Virus and General Security under Ubuntu

Linux does not suffer from Viruses like other OS, there are no known viruses in the wild, the main reason using AV on linux is to scan incase you share files with windows users.

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

See here for Anti-Virus information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)

See below for Bodhi.Zazen's overview of Linux Security

**[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)**

Then these stickies:
security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Also see about sudo and why root account is disabled by default in Ubuntu:

rootsudo
**[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)**

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

You might also want to look at Tor for anonymizing your connection:
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Firewalls are not generally needed on a home desktop machine as that is taken care of by your router however there is a hardcoded firewall in Linux called Netfilter/IPTables and can be configured by reading here:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Though most people if use anything use UFW/GUFW which is a interface for managing IPTables without the complicated command line. see here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Also look at apparmor for profiling your applications and there privelege:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)


Have fun

Regards

haqking

---

### Post by Dangertux on 2011-10-01
Shorter answer -- yes. 

If you want absolutely no chance of being compromised your machine must never make contact with the outside world.

Firewalls even with restrictive inbound and outbound rules are easy to circumvent via reverse connections.

---

### Post by iisjman07 on 2011-10-02
Even if the firewall is functioning correctly, one of main ways hackers could compromise your machine would be through exploits (of the OS or software installed (EG: Flash Player)). It's vitally important that you keep software packages up to date, and you should enable automatic security updates.

If you're worried about being hacked, you should encrypt your data (using Truecrypt or similar), so even someone tapped into your machine, they wouldn't be able to get any of your files.

---

### Post by Lars Noodén on 2011-10-02
> **arroy_0209 said:**
> My firewall (using gufw) preferences are: incoming denied, outgoing all denied except to port 80/tcp (http) which is allowed. Is it possible that with this configuration my computer may get hacked? If so, what other changes should be made? 

I am using a router but have no idea how to check its firewall configuration to get an idea how good that one is.

As others pointed out, you are still open on port 80 outgoing and that is where you will have trouble, if any.  Port 53 outgoing UDP must be open, at least to your DNS servers, or you cannot do DNS lookups.  

Odds are that it is your web browser that will use port 80 outgoing.  The two things you can do there are to run an AppArmor profile for the browser and to run NoScript (on firefox) or something like it.

---

### Post by OpSecShellshock on 2011-10-02
There are a lot of things that "getting hacked" could mean. The best  approaches will require you to define what use tasks you need/want your  computer to perform as well as which risks you're trying to address.  What situations are you trying to avoid?

Or, just look [here]("https://grepular.com/Protecting_a_Laptop_from_Simple_and_Sophisticated_Attacks"), and see what a guy who tries to think of everything has to do in order to feel comfortable. Then pare that down to suit your own comfort level.

---

### Post by tubbygweilo on 2011-10-02
One other attack vector is that of physical attack so don't let you kit out of your sight but this may mean a lifestyle change for both you an dyour computing. 

All the best with your quest.

---

### Post by newhere_m on 2011-10-02
OpSecShellshock is very true. Here is what I aim to achieve by enhancing security. I may have to do online banking transactions and I certainly won't like anybody to steal my password and use my account. It is not that I am a very rich person and will use online banking frequently but I want to be safe always. Other than that I need to use internet to exchange emails, download pdf files (for study purpose), and sometimes visit sites which come as results of google search but I am not sure whether such sites are safe or not. It is impossible to first look for safety of a site and then click the link. Also the downloaded pdf files etc should not create problem (I am aware acroread can not be relied blindly due to java-issues). So my aim is to minimize possibility of identity theft and not get my system compromised in any way. I do not know if there are security measures to be taken for each issue separately but there are general procedures like setting file permissions, file encryption, firewall, network-supervision, browser-security, hardening installation and so on. As bodhi.zazen says: "Security is an ongoing process and, like an  onion, it has layers and stinks". I really do not know where to stop when it comes to security-enhancement issue. 
I will be glad if you have any suggestions for me. Thanks.

---

### Post by Dangertux on 2011-10-02
> **newhere_m said:**
> OpSecShellshock is very true. Here is what I aim to achieve by enhancing security. I may have to do online banking transactions and I certainly won't like anybody to steal my password and use my account. It is not that I am a very rich person and will use online banking frequently but I want to be safe always. Other than that I need to use internet to exchange emails, download pdf files (for study purpose), and sometimes visit sites which come as results of google search but I am not sure whether such sites are safe or not. It is impossible to first look for safety of a site and then click the link. Also the downloaded pdf files etc should not create problem (I am aware acroread can not be relied blindly due to java-issues). So my aim is to minimize possibility of identity theft and not get my system compromised in any way. I do not know if there are security measures to be taken for each issue separately but there are general procedures like setting file permissions, file encryption, firewall, network-supervision, browser-security, hardening installation and so on. As bodhi.zazen says: "Security is an ongoing process and, like an  onion, it has layers and stinks". I really do not know where to stop when it comes to security-enhancement issue. 
I will be glad if you have any suggestions for me. Thanks.


Well -- as it seems you've already figured out if you let your paranoia take over ; you will never stop with the security kick (I'm pretty sure this is how I ended up doing it for a living lol :-P)

That being said for typical desktop usage (which is pretty much what you described) I would suggest the following.

- Use a browser addon such as NoScript fro Firefox, NotScripts for Chrome

- Force SSL where possible, yes I know TLS 1.0 has issues, however that is an extremely difficult attack to pull off since a Man in the Middle attack still has to occur. (that being said, don't use public wifi, if you do use an ssh tunnel or vpn to protect yourself while utilizing it)

- Use your firewall but don't try to make it a fortress, strict incoming rules and moderate outgoing rules such as allowing http, https , dns , and mail should be fine. Keep in mind , most backdoored programs are using oddball ports they are not going to target port 80 or port 53 this is the action of someone who targeted you specifically. If someone is specifically targeting you it's already game over they will get you eventually.

- Use home folder encryption (more paranoid use full drive encryption)

- Physically secure your machine, lock it to a desk, in a closet or in a safe when not in use.

- I would say use anti-malware, but I will get the flame war of "there is no linux malware" going, the truth is there are no good (free) anti-malware solutions for linux, so there is no point. The fact that Ubuntu and Linux aren't victims of malware attacks are based entirely on the honor system of bad guys don't write malware for it, so we don't need anti-malware.

- Use application firewalling like Apparmor or SELinux (one not both bad things happen if you use both) ; to protect your commonly used applications, particularly those accepting input from untrusted locations (browser, pdf reader, media players and things like LibreOffice)

- Use common sense, if you visit a lot of shady places. This is going to save you the most trouble of all of them, at least 50% of compromised systems requires some form of user interaction.

- USE STRONG PASSWORDS  (and don't use them in multiple places, re-used credentials are the fastest way for gaining access to more systems for potential attackers)

Hope those general guidelines give you a decent idea of what to be thinking about.

---

### Post by newhere_m on 2011-10-03
Thanks for such a detailed reply. However, regarding SSL, do you mean it to be used with firefox/browser or to be used in general, in ubuntu? In firefox, ssl3.0 and tls1.0 are already in use. If you mean to use in ubuntu itself, then I will have to learn first how to configure.

Another duobt I have, in case somebody gets access to my OS (from remote area), how will I realize? What message for example, in log file will unambiguously tell me that?

---

### Post by Dangertux on 2011-10-03
> **newhere_m said:**
> Thanks for such a detailed reply. However, regarding SSL, do you mean it to be used with firefox/browser or to be used in general, in ubuntu? In firefox, ssl3.0 and tls1.0 are already in use. If you mean to use in ubuntu itself, then I will have to learn first how to configure.

Another duobt I have, in case somebody gets access to my OS (from remote area), how will I realize? What message for example, in log file will unambiguously tell me that?

When I said SSL I was referring to browsing, however other services sometimes support it, use it for anything you can (coming to mind are skype some email providers and irc)

As far as logs go I would check out /var/auth.log for evidence of people remotely administering your machine.

---

### Post by Jonathan L on 2011-10-04
> **arroy_0209 said:**
> My firewall (using gufw) preferences are: incoming denied, outgoing all denied except to port 80/tcp (http) which is allowed. Is it possible that with this configuration my computer may get hacked? If so, what other changes should be made? 

I am using a router but have no idea how to check its firewall configuration to get an idea how good that one is.

Hi Arroy

I'm sure the following approach won't be helpful for your situation, but you might consider portions of it, even if just for humour's sake!

Here's what I did to make a change-free system to distribute version-controlled documents:

1.  Don't have any hard disks.  Or flash.
2.  Boot from network, or better yet, CD-ROM.
3.  Have no working passwords for any user.
4.  Get distributions of web site from author on CD-ROM, mount on /var/www
5.  Reboot daily on automatic timer.
6.  Logs, include web, over syslog over the network.

I believe it was pretty secure, but would value others' opinions.   I bet Dangertux will come in through my bluetooth mouse port (I've seen it done!), jam my log server, and crack my CD burner! :)

It was done for the purposes of controlling change to the web documents: the person responsible for the documents satisfied themselves that they had made a good website on the CD-ROM, and the interaction with the systems and systems staff was negligible and simple.

Kind regards,
Jonathan.

---

