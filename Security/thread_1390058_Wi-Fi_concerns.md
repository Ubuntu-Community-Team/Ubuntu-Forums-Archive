---
title: "Wi-Fi concerns"
date: 2010-01-25
forum: Security
---

### Post by oshirowanen on 2010-01-25
Dear Ubuntu community,

If I enable Wi-Fi on my laptop and use a public Wi-Fi hotspot at an airport, will a firewall such as UFW be enough to stop hackers accessing my personal files which are NOT transmitted over the Wi-Fi connection?

---

### Post by tubbygweilo on 2010-01-25
oshirowanen, 
If just browsing the net and not accessing personal files then a quick boot from a liveCD will allow you to browse and surf without too much fear of snooping. 

Browsing with the NoSript, BetterPrivacy and Adblock+ extensions enabled makes you safer still. 

Keeping personal data encrypted within something like a truecrypt container will keep it safe from prying eyes. 

I do believe that the default settings of the Ubuntu firewall are pretty safe but you can always amend them to suite your needs. I am sure someone with more firewall knowledge than I will be along in a moment to offer further advice.

---

### Post by cdenley on 2010-01-25
Firewall or not, there are no services installed by default which would allow anyone to retrieve your files remotely. They can only eavesdrop on the data you send/receive. If you installed some kind of server, then you may have a problem.

---

### Post by CharlesA on 2010-01-25
If you are that paranoid, you could always tunnel all brower traffic over an SSH tunnel when connecting to public hotspots. That way traffic is encrypted and can't be decrypted if there is someone on the network with a packet sniffer.

I'd do that if I used hotspots.

---

### Post by Sarmacid on 2010-01-25
If your firewall is well configured, it will stop them from accessing your machine, however that alone won't stop them from snooping around what you do on the internet. Using https, they can tell what sites you visit, but they can't tell what you're looking at exactly, however they can see the traffic that's not encrypted, such as http sites. If you got a machine at home, I'd suggest establishing a ssh tunnel and sending all your traffic through that tunnel.

---

### Post by bodhi.zazen on 2010-01-25
> **oshirowanen said:**
> Dear Ubuntu community,

If I enable Wi-Fi on my laptop and use a public Wi-Fi hotspot at an airport, will a firewall such as UFW be enough to stop hackers accessing my personal files which are NOT transmitted over the Wi-Fi connection?

To add to the conversation ...

A default installation of Ubuntu has no significant servers listening for incoming connections, so, unless you install a server of some kind, [s]hackers[/s] crackers can not access your personal files.

If you use wireless, your packets travel through the airwaves and can be received by anyone.

Assume any unencrypted traffic (http, ftp) is not private.

If you *must* connect to a bank site or other private use https (ssl).

If you wish to encrypt all your traffic, use VPN or SSH.

---

### Post by HermanAB on 2010-01-25
Howdy,

Yes your files on your local system are OK, but there are other things to worry about.

As mentioned above, all your network traffic is open to the world unless you use encryption such as HTTPS.  So, what you need to worry about is your username and password when you access your email using a web browser.

Google email is now accessible using HTTPS, but they seem to have bigger backdoor problems.  The important thing is that you should never use your email password for anything else, since it is typically a totally insecure service snoped by all and sundry.  Never, ever use your email password for your bank for example!

---

### Post by BkkBonanza on 2010-01-25
I would take that a step further and say "never enter any email passwords (and possibly others)" while surfing via an open connection. You have to remember that if someone snoops your email password then it's often very easy to visit other sites and request password change (forgotten password) such that the site will send you a new one or provide a form to create a new one. So getting access to your email is often as good as getting the ability to change any other passwords for accounts associated via your email. This can even be domain name control and certificate issuance. So it's a bigger threat than you would expect.

If you use Thunderbird/Evolution then be sure to config all accounts to use tls/ssl based pop/imap. This will ensure user/password info is sent over ssl links only. Gmail has had this mandatory for a long time but many other email providers (ISPs!) still use pop3 unsecure access. Change that!

Read up on using ssh as a secure proxy. -D option - it is very powerful and easy to use for secure surfing.

---

### Post by xpod on 2010-01-25
I`m certainly no network security expert but knowing how relatively simple it is to grab passwords & stuff off a network, https/ssl included,  i think i`d just stick with the assumption that there could well be some little skiddie sitting with the relevant software carrying out all kinds of [mitm](http://en.wikipedia.org/wiki/Man-in-the-middle_attack) attacks on the Wifi spot in question.

---

### Post by cdenley on 2010-01-25
> **xpod said:**
> I`m certainly no network security expert but knowing how relatively simple it is to grab passwords & stuff off a network, https/ssl included,  i think i`d just stick with the assumption that there could well be some little skiddie sitting with the relevant software carrying out all kinds of [mitm](http://en.wikipedia.org/wiki/Man-in-the-middle_attack) attacks on the Wifi spot in question.

A MITM attack can only work with a CA-signed SSL certificate if the user is dumb enough to make a security exception when their browser gives them a very scary warning about an invalid or unsigned certificate.

---

### Post by BkkBonanza on 2010-01-25
Or if they aren't careful with who they are connected to. If the web site address is wrong or if the connection isn't actually https then they can be fooled into continuing. Always be sure to check not just the "little padlock" but the protocol and the address. There are automated mitm attacks that substitute a fake padlock and revert to http to fool users into continuing with their credentials. While we would never fall for that (right?), many people aren't too clear on what these things mean and do fall for them.

---

### Post by Millie.T.Cook on 2010-01-25
Are there any informative websites where I can find some how-to's? Thanks in advance.

MC

---

### Post by xpod on 2010-01-25
> **cdenley said:**
> A MITM attack can only work with a CA-signed SSL certificate **if the user is dumb enough** to make a security exception when their browser gives them a very scary warning about an invalid or unsigned certificate.

I wouldn`t necessarily call them "dumb" but the reality is that many, if not most computer users probably *would* click "accept". Blindly clicking next & accept is rather popular after all.
There are also ways of circumventing the certificate problem for the more determined skiddie.

---

### Post by CharlesA on 2010-01-25
> **Millie.T.Cook said:**
> Are there any informative websites where I can find some how-to's? Thanks in advance.

MC
You can check here for info on setting up a proxy: [http://blogs.techrepublic.com.com/security/?p=408&tag=rbxccnbtr1](http://blogs.techrepublic.com.com/security/?p=408&tag=rbxccnbtr1)

---

### Post by oshirowanen on 2010-01-26
Thanks for all the advice.

Just to clarify, If I have a fully encrypted hard drive, another section on the hard drive where I keep all my sensitive files encrypted, use ssh to get the send files, use https to get into my email account and bank account, and make sure I am blocking all incoming traffic via ufw, will this be enough to keep me secure on public wi-fi hotspots?

---

### Post by cdenley on 2010-01-26
> **oshirowanen said:**
> Thanks for all the advice.

Just to clarify, If I have a fully encrypted hard drive, another section on the hard drive where I keep all my sensitive files encrypted, use ssh to get the send files, use https to get into my email account and bank account, and make sure I am blocking all incoming traffic via ufw, will this be enough to keep me secure on public wi-fi hotspots?

Yes. Filesystem encryption won't protect you at wifi hotspots, though. It only protects you from physical access, like if someone stole your laptop or hard drive. Unless this is a concern, you're just wasting system resources.

---

### Post by CharlesA on 2010-01-26
Easy: run nmap on it.

---

### Post by dogdo on 2010-01-26
> **cdenley said:**
> Yes. Filesystem encryption won't protect you at wifi hotspots, though. It only protects you from physical access, like if someone stole your laptop or hard drive. Unless this is a concern, you're just wasting system resources.

Define filesystem encryption-what programs does this refer to? 

I have a private home folder under encfs- as long as i dont mount this with the passphrase would this data be safe while im using my home wifi network?

---

### Post by cdenley on 2010-01-26
> **dogdo said:**
> Define filesystem encryption-what programs does this refer to? 

I have a private home folder under encfs- as long as i dont mount this with the passphrase would this data be safe while im using my home wifi network?

encfs = encrypted filesystem = a filesystem which is encrypted
I don't know how I can be more specific. I'm sure you know what a filesystem is and what it means for data to be encrypted. There are a few different types of encrypted filesystems.

If it is unmounted, then it would be safe from physical/local access. I suppose you can consider that an extra layer of security in case a remote attacker somehow gained local access to your system. However, relevant to this thread, oshirowanen said he uses full disk encryption, which means it must be decrypted/mounted in order to use the system, so this cannot provide an extra layer of security from remote threats.

---

### Post by bodhi.zazen on 2010-01-26
This thread is meandering through several topics without covering much detail (IMO).

What is it about Wi-Fi that you need to worry about ?

The main potential problem with Wi-Fi (or any untrusted network) is that your network traffic or packets can be "sniffed" for intercepted by others.

So, for example, if you are connecting to a bank or FTP server, others can intercept your packets and read your password.

The solution is to use encryption. Your options are to tunnel over ssh, VPN, or at least make sure you are connecting to a server via ssl (https).

Now given enough packets it is, in theory, possible for someone to intercept and decode the encrypted traffic, but this is unlikely.

The other issues are more general and not at all specific to Wi-Fi.

Firewalls - What is it you wish to accomplish with a firewall ? Are you running a server ? If you are not running a server, then enabling your firewall does very little to add to your security.

Encryption - What makes you think encryption of your data on your hard drive has anything to do with Wi-Fi ? Encryption is helpful to limit access if somebody has physical or remote (shell) access to your computer. If you encrypt your entire file system, and turn your computer off, nobody can access your data without either your password or breaking the encryption. Same if you encrypt a file.

As soon as you boot or decrypt your file, then so long as your computer is on or the file is decrypted, anyone else with physical or remote access can potentially read the data.

Basically if you can read the data (because it has been decrypted), so can root.

[img]http://imgs.xkcd.com/comics/security.png[/img]

I suggest you read the sticky at the top of the security section:

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

