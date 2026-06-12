---
title: "being hacked"
date: 2007-11-20
forum: Server Platforms
---

### Post by benetook on 2007-11-20
here is the problem and what I would like to achieve.

somebody somehow logged in to my server as my root password and created an account called energie and password the same.  At this stage he does not seem to have done any damage YET!!!.

1st, what is the command to delete an account. (Easy one)

2nd, I would like to restrict access to my server to the local network, obviously this person was able to access my root password, maybe by keylogger, (I am no expert). from over the internet, can this be done or is a firewall the answer, (As I said, I am no expert), and would this still allow people to view the server pages?

Thank you

---

### Post by MJN on 2007-11-20
You have absolutely no idea whether they've caused any 'damage' hence your only option is to reinstall everything from scratch. With root access it is trivial to completely cover your tracks. There are no ifs and buts when it comes to this - wipe and reinstall.
 
When you're back up and running you should check the sshd_config man pages out and disable root logins and restrict access to only your LAN IP range. Your server pages (I assume you're referring to a website?) will be unaffected.
 
Mathew

---

### Post by benetook on 2007-11-20
I know they have caused no damage, as I logged in as the account and used the upward key to check previous entered commands, (This is how I discovered the new account in the first place under root), it has only been created today.

My site works perfectly and every setting I have checked is correct and all site paged are correct and unchanged including main page, blog section and oscommerce section.

so at this stage i just want to restrict modifications from outside the local network and delete the account.  rm does not work or I am using it wrong.

---

### Post by wieman01 on 2007-11-20
Mathew is right though... with root privileges they could have installed any sort of software/program that you are not even aware of. You must assume your system has been compromised and will grant them access even in future by opening a backdoor or something similar.

A firewall won't protect you if your system is not up-to-date in terms of security updates and if your passwords are weak.

Do you use SSH for remote login? Telnet is totally insecure, so you should never use it.

---

### Post by benetook on 2007-11-20
editing  /etc/ssh/sshd_config to restrict to LAN IP range as you suggested, cannot see which lines I have to edit to do this.

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

---

### Post by benetook on 2007-11-20
Thanks wieman, I mainly use Konqueror on another Ubuntu machine to do all editing and on a rare occasion I use Konsole

---

### Post by kvonb on 2007-11-20
-

---

### Post by MJN on 2007-11-20
> **benetook said:**
> I know they have caused no damage, as I logged in as the account and used the upward key to check previous entered commands,
 
That is an incorrect assumption. They could have easily modified the history to cover their tracks. Don't fall into the trap of thinking 'they didnt change the history because I can see they created an account'. You NEED to reinstall - it's as simple as that.
 
For the IP restrictions, I assumed SSHD would allow you to do this natively however it appears not. Hence, add the following into your /etc/hosts.allow file:
 
```
sshd : 192.168.0.0/255.255.0.0 : allow
sshd : ALL : deny
```
 
(This assumes your local LAN is using the 192.168 address range - post back if it's not)
 
Mathew
 
P.S. I have perhaps incorrectly assumed that SSH is your only shell access method - you may need to clarify/confirm this as, like the others have mentioned, there are issues with some other methods such as telnet and local physical access.

---

### Post by benetook on 2007-11-20
root@shop:/home/shop# sshd : 192.168.0.0/255.255.0.0 : allow
sshd re-exec requires execution with an absolute path
root@shop:/home/shop# sshd : ALL : deny
sshd re-exec requires execution with an absolute path
root@shop:/home/shop#

---

### Post by MJN on 2007-11-20
Sorry, I should've been clearer. You need to edit the /etc/hosts.allow file and add the configuration lines to it.
 
However, it's too late doing it now - the horse has already bolted. **Get reinstalling!!** Somehow I get the impression you're not heeding this advice, more fool you if this is the case.
 
Mathew

---

### Post by wieman01 on 2007-11-20
Benetook,

I also second that, reinstall the system and start all over again. Not sure what's on the server but it's a risk you should not take.

---

### Post by threeten on 2007-11-20
And AFTER you re-install, set your sshd_config to disallow root logins.  You might also consider restricting logins to authorized keys only.

---

### Post by twistedtwig on 2007-11-20
Matthew and others KNOW their stuff!!! he has helped me on MANY an occassion. I completely agree with reinstalling... regular backups are the only way to make sure you still have your data and can do a reinstall without major worry u are going to loose something.

---

### Post by HermanAB on 2007-11-20
Re-install immediately.  It only takes about 30 minutes and if your data (/home, /var/mysql, whatever) is a separate partition, then you can re-install without even wasting time on making a backup of anything.  If you don't have a separate /home partition - now you know why you should have one...

Some general tips:
a. Run SSHD on a non-standard port.  This will throw off script kiddies. Set the port in /etc/ssh/sshd_config.
b. Use passwords of 9 or more characters for *all* accounts.
c. Disallow root logins in /etc/ssh/sshd_config.
d. Use iptables rate limiting to suppress brute forcers.  Put this at the end of rc.local:
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 6/minute --limit-burst 5 -j ACCEPT

Cheers,

H.

---

### Post by az on 2007-11-20
> **HermanAB said:**
>  It only takes about 30 minutes and if your data (/home, /var/mysql, whatever) is a separate partition, 

If your web application runs a database, you need to audit that, too, to look for unauthorized access.  When you reinstall, do not use the same mysql root password.


> **HermanAB said:**
> 
then you can re-install without even wasting time on making a backup of anything.  If you don't have a separate /home partition - now you know why you should have one...


I disagree.   Everything you will be keeping will need to be audited.  Making backups on a separate medium is more sane.

---

### Post by HermanAB on 2007-11-20
The reason for the re-install is to ensure that any compromised utilities are replaced with good ones.  You have to check your data to see that everything is still OK, but since you are not going to execute the data, this is less of an issue.

---

### Post by twistedtwig on 2007-11-20
aye if you have full external backups you can simply restore the whole system to a safe point (if known).  At least storing data externally means you can wipe the system and start again.

its an **** when you get owned like that!!!

GL bud

---

### Post by Gouki on 2007-11-20
Just to add a bit more information.

Like several have said,reinstall your OS. We can never say this too much.

If this was a critical system, we could probably waste a few days going through logs and doing forensics work to see if it was safe enough to keep the system running with the current OS, however, I don't believe this is the case.

As for remote login security.

root should never be allowed to connect over SSH. Like someone have said, don't run sshd on the default port.

Consider using Fail2Ban (available on official repositories) to block failed logins after X tries. This python script can be very useful, as it allows you to block an IP address after 1/2/3/etc failed logins for SSH, Apache, etc.

Now, for the old schoolers, you can also give port knocking a try.

[Port knocking at Wikipedia.]("http://en.wikipedia.org/wiki/Port_knocking")

---

### Post by mellowd on 2007-11-20
And really, try to get a hardware firewall if possible. I've got one protecting my lan and the only way anything gets in is when I vpn into the firewall.

---

### Post by MJN on 2007-11-20
> **mellowd said:**
> And really, try to get a hardware firewall if possible. I've got one protecting my lan and the only way anything gets in is when I vpn into the firewall.

This sounds like a password compromise so a firewall, hardware or not, would have had no effect.

Mathew

---

### Post by mellowd on 2007-11-20
> **MJN said:**
> This sounds like a password compromise so a firewall, hardware or not, would have had no effect.

Mathew

A firewall would prevent access to the server in the first place. As long as you alone have access through your firewall you will never get to the server. You wouldn't be able to ping it or ssh into it. It then wouldn't matter if he has your root password as they'll never get that far unless your vpn is comprimised

---

### Post by MJN on 2007-11-20
Of course, but one assumes that as this is a server then external access *is* required! The OP specifically mentioned it running a website, and remote SSH access is a common requirement also.

I'm not saying firewalls, and hardware ones at that, are of no use - simply that they would have been of no benefit to the OP in this case.

Mathew

---

### Post by mellowd on 2007-11-20
> **MJN said:**
> Of course, but one assumes that as this is a server then external access *is* required! The OP specifically mentioned it running a website, and remote SSH access is a common requirement also.

I'm not saying firewalls, and hardware ones at that, are of no use - simply that they would have been of no benefit to the OP in this case.

Mathew

Open access may be required but it doesn't mean the server has to be open on all ports to the world. You can set up external full access if you want in a very secure way as long as you know what you're doing. 

If he is running a website then all he needs is a firewall to let port 80 through and nothing else. If he needs ssh access then he can set up a vlan and restrict access locally. As long as he comes into the vlan from anywhere he will be on the local lan. This can all be done through a firewall

---

### Post by MJN on 2007-11-20
Would it have helped in this instance? If not, then please don't suggest it as it just confuses the issue!

Mathew

---

### Post by mellowd on 2007-11-20
> **benetook said:**
> 
2nd, I would like to restrict access to my server to the local network, obviously this person was able to access my root password, maybe by keylogger, (I am no expert). from over the internet, can this be done or is a firewall the answer, (As I said, I am no expert), and would this still allow people to view the server pages?
Thank you

This proves it would have helped in this instance. He wants to restrict access locally but still broadcast his webpages. Have the firewall block everything from the untrust interface barring port 80 and then administer the server remotely with a vlan

---

### Post by MJN on 2007-11-20
With only port 80 open in the firewall, how would you run a VLAN over it?

This is drifting wildly from being any use to the OP - perhaps it might be better to continue the conversation via PM as I'm sure our 'bickering' over these nuances is of little interest to him/her.

Cheers,

Mathew

---

### Post by mellowd on 2007-11-20
> **MJN said:**
> With only port 80 open in the firewall, how would you run a VLAN over it?

This is drifting wildly from being any use to the OP - perhaps it might be better to continue the conversation via PM as I'm sure our 'bickering' over these nuances is of little interest to him/her.

Cheers,

Mathew

Because a VLAN doesn't require a port. Vlan's are layer 2.

And I think the debate helps everyone because it gives everyone a better understanding of the underlying layers. Also its good if anyone else has the same sort of problem.

---

### Post by MJN on 2007-11-20
My bad terminology - I meant if we're only allowing port 80 through the firewall, and blocking everything else (at all layers), then how will a VLAN operate through it? You weren't seriously suggesting a non-VLAN-aware firewall? If your VLAN is compromised then the external 'attacker' effectively becomes internal and your hardware firewall may as well go out of the window.

Whilst this is all jolly interesting are you sure it is helping the OP? Perhaps if you could suggest to him some hardware firewalls that you'd recommend then that may be more in keeping with the advice he's requesting. I'm certain he'd be in no better a position than if he follows the advice already given by others (locking down SSH etc), yet would have a lighter wallet for the privilege.

Mathew

---

### Post by mellowd on 2007-11-20
Of course it helps because it allows him to make an informed decision. Also its really not easy to compramise a vlan even if you physically plug your line into a vlan'd switch. The user would still need to be assigned to the vlan group.

> blocking everything else (at all layers)

How exactly could you do port based blocking at level 1 or 2 anyway? IP is a layer 3 protocol. Vlan's don't care or even look at which ports are actually getting through.

---

### Post by MJN on 2007-11-20
I'm not suggesting port-based blocking - a firewall can operate at all layers.

A layer 2 VLAN is going to be of no use for remote access over the Internet unless you wrap it in IP. If you subsequently punch a hole for this through the firewall then you may as well punch one through for SSH and ensure it is secured. If remote access is not required (notwithstanding the web server) then why do we need a VLAN?

Please do make your hardware firewall recommendation to the OP as it's not really me that you have to convince! ;)

Mathew

---

### Post by mellowd on 2007-11-20
> **MJN said:**
> I'm not suggesting port-based blocking - a firewall can operate at all layers.

A layer 2 VLAN is going to be of no use for remote access over the Internet unless you wrap it in IP. If you subsequently punch a hole for this through the firewall then you may as well punch one through for SSH and ensure it is secured. If remote access is not required (notwithstanding the web server) then why do we need a VLAN?

Please do make your hardware firewall recommendation as it's not really me that you have to convince! ;)

Mathew

You're going both sides of the fence here. I first reccomended a firewall to block everything except port 80. You then said that's no good as he needs external access. Fair enough he could then lock down access to the local network and use a vlan, or he could just use a vpn instead. Now you say if remote access is not required? If not then he can use the firewall to block anything coming in on the untrust interface bar port 80 and be done with it.

Also, firewalls filter on layer 3 and above. They can filter on layter 2 as well only if a vlan is used. Filtering on layer 1 can only be done if you physically unplug it

---

### Post by mellowd on 2007-11-20
And if I had to reccomend a firewall? Well if its a businedd I'd recoomend either a netscreen or pix. There are others though.

---

### Post by MJN on 2007-11-20
From the OP's original and subsequent messages do you *really *suspect this is a business outfit with appropriate levels of resource (both financially and skillset)? (That's no slight on the OP, I'm just painting the level we're discussing here). I don't. Is a Netscreen or PIX therefore a good recommendation based on the OPs requirements and situation?

A hardware firewall dialogue like this does not belong in this thread. Your advice is mistargeted at best (with good intentions I'm sure).

Mathew

---

### Post by mellowd on 2007-11-20
I don't see how its mistargeted. They could either use the information or ignore it. Either way they are more informed.

---

### Post by MJN on 2007-11-20
Fair enough.

Mathew

---

### Post by wirelessmonkey on 2007-11-20
> **mellowd said:**
> Of course it helps because it allows him to make an informed decision. Also its really not easy to compramise a vlan even if you physically plug your line into a vlan'd switch. The user would still need to be assigned to the vlan group.



How exactly could you do port based blocking at level 1 or 2 anyway? IP is a layer 3 protocol. Vlan's don't care or even look at which ports are actually getting through.

802.1X!!!!! !!

---

### Post by mellowd on 2007-11-21
> **wirelessmonkey said:**
> 802.1X!!!!! !!

If you look at the conversation you can see I was talking about IP ports, not switch ports. IP ports can only be blocked at layer 3 because it is a layer 3 protocol. 802.1x is port blocking on the switch. IT's very much similar to a vlan which you noticed I said can already be blocked at layer 2 because its the data link layer

---

### Post by wieman01 on 2007-11-21
> **wirelessmonkey said:**
> 802.1X!!!!! !!
It's all theoretically possible, but for a home user? I doubt it. Interesting threat although it has less to do with the OP's initial request.

---

### Post by Chayak on 2007-11-21
It may be beating a dead horse, but reinstall.
Only open the ports you need, as has been said, but I will make the suggestion of changing your ssh port to something nonstandard such as 2200, 2222, etc.  The only other thing is use a strong password or even better a passphrase like "!@Don't forget m3#@"  I know it may be a pain to type but for a server security should come first.

You can also do things like only allowing logons with allowed ssh keys.  Fail2Ban is also very useful to block the ssh bruteforce bots that troll the net though they tend to only look at port 22

Most of the boxes I've seen rooted are because they're not kept updated and fall victim to something like a buffer overflow or the admins used weak passwords

---

### Post by wirelessmonkey on 2007-11-21
> **wieman01 said:**
> It's all theoretically possible, but for a home user? I doubt it. Interesting threat although it has less to do with the OP's initial request.

802.1X is good for wired security, less so for wireless networks.

I'm sorry, but 802.1X is probably the Only thing that makes enterprise wireless feasible, outside of spanned VPNs.   .1X with wpa2/aes using TLS... is the very best commodity wireless security solution available.


As to my original suggestion of .1X, I apologize, I was only skimming the conversation.

---

### Post by mellowd on 2007-11-21
> **wirelessmonkey said:**
> 
As to my original suggestion of .1X, I apologize, I was only skimming the conversation.

No worries :)

---

### Post by wieman01 on 2007-11-21
> **wirelessmonkey said:**
> I'm sorry, but 802.1X is probably the Only thing that makes enterprise wireless feasible, outside of spanned VPNs.   .1X with wpa2/aes using TLS... is the very best commodity wireless security solution available.


As to my original suggestion of .1X, I apologize, I was only skimming the conversation.
Oh well... today isn't really my day... I ought to know better actually. :-) I should not have said that, hey?

802.1X isn't secure per se I should add as a lot of companies still use LEAP which is utterly flawed when it comes to wireless LANs. It therefore depends on the exact "standard" you use.

In a wired environment I guess you don't really have such risks, do you?

Anyway, side-tracking once again.

---

### Post by Chayak on 2007-11-22
Ok, forgive me for pointing this out.  Mellowd, weiman01, the OP has stated very clearly he isn't an expert so why are you even going off on VLANs and what OSI layer they're on when you might as well be speaking Klingon in regards to the OP or 99.99% (or whatever) of computer users who would give you a blank look when talking about the OSI model and don't even have a clue what a VLAN is.

You're going to confuse the poor guy.

If you want to discuss VLAN or compare the theory of the OSI model to the reality of the TCP/IP model or even digging down to the header composition of packets, or more accurately frames, please take it to another thread.

---

### Post by mellowd on 2007-11-22
> **Chayak said:**
> Ok, forgive me for pointing this out.  Mellowd, weiman01, the OP has stated very clearly he isn't an expert so why are you even going off on VLANs and what OSI layer they're on when you might as well be speaking Klingon in regards to the OP or 99.99% (or whatever) of computer users who would give you a blank look when talking about the OSI model and don't even have a clue what a VLAN is.

You're going to confuse the poor guy.

If you want to discuss VLAN or compare the theory of the OSI model to the reality of the TCP/IP model or even digging down to the header composition of packets, or more accurately frames, please take it to another thread.

My apologies for confusing anyone. I amde a few suggestions and it turned into a debate :p

---

### Post by Emerzen on 2007-11-23
Newb question: if you can't log into your Ubuntu box as root, is it possible to log into SSH as root?  In other words, since their's no root password set by default, how can you log into root even if enabled in sshd_config? 

Thanks

---

### Post by wieman01 on 2007-11-23
> **Emerzen said:**
> Newb question: if you can't log into your Ubuntu box as root, is it possible to log into SSH as root?  In other words, since their's no root password set by default, how can you log into root even if enabled in sshd_config? 

Thanks
No, you can't. You are safe in that case.

---

### Post by Emerzen on 2007-11-23
Thanks wieman01!

---

### Post by herbie_popnecker on 2007-11-24
So here's my problem: I often manage the serverbank from my PC at home, and use WinSCP to upload files.
You can't sudo without using a command line, which is entirely too restrictive.
I need to use a root account and restrict ssh to only my IP... which doesn't help if I'm on the road.
What's you suggestions?

---

### Post by mellowd on 2007-11-24
Are you not able to connect to your desk pc somehow and ssh from there? It's a bit of a mission to do it this way but at least you can then lock ssh access down to just the desk pc

---

### Post by koenn on 2007-11-24
> **herbie_popnecker said:**
> So here's my problem: I often manage the serverbank from my PC at home, and use WinSCP to upload files.
You can't sudo without using a command line, which is entirely too restrictive.
I need to use a root account and restrict ssh to only my IP... which doesn't help if I'm on the road.
What's you suggestions?
set up a vpn sollution, a virtual private network.

---

### Post by koenn on 2007-11-24
> **mellowd said:**
> Are you not able to connect to your desk pc somehow and ssh from there? It's a bit of a mission to do it this way but at least you can then lock ssh access down to just the desk pc

That would just move the problem, wouldn't it ? The desktop pc would now have to be accessible from anywhere ...

---

### Post by mellowd on 2007-11-24
> **koenn said:**
> That would just move the problem, wouldn't it ? The desktop pc would now have to be accessible from anywhere ...

That depends. If he has a firewall of sorts he could vpn into the desktop PC.

---

### Post by koenn on 2007-11-25
or just vpn into the network where the servers are, as I suggested in post #50.

---

