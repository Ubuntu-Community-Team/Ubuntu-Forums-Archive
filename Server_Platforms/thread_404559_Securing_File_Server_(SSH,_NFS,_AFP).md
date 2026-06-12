---
title: "Securing File Server (SSH, NFS, AFP)"
date: 2007-04-08
forum: Server Platforms
---

### Post by thornomad on 2007-04-08
Hello - am putting the final touches on a new file server; will utilize SSH, NFS, and AFP (for use with Macs and Ubuntu boxes).  Need some help/suggestions making sure the file server box is secure.  I will go over what I've done (or know to do) and if you have further suggestions that would be great.

I will use SSH only for accessing the machine remotely; AFP (netatalk) and NFS will be used on the local area network for faster file speeds.  I have my router only forwarding port 22 (more on that) to the file server -- won't forward any other ports.

Here is my basic approach (below); I don't know how to do everything I want to, yet, but hoping someone can point me in the right direction and make some better suggestions.  I think I have a good start securing SSH but do not feel comy with NFS or AFP yet: 

**Security for SSH**:

[LIST]
[*]turn off password login; only use public/private key login (with passphrase)
[*]could use a non-standard port, but would rather be secure in the standard one then rely on someone not to check for a high open port number
[*]could install fail2ban
[*]disable root login (though, if I understand it correctly sudo still will work, which is great)
[/LIST]

**Security for NFS**:

[LIST]
[*]using iptables/firewall, restrict access only to computers on my local network and in a specific range (i don't know how to do this, yet, however)
[*]probably some other settings on the nfs-side of things that can limit access, but I don't know what they are
[/LIST]

**Security for AFP (netatalk)**:

[LIST]
[*]the universe repository version of netatalk installs fine, however, my mac gives a "sending password in clear text" warning ... which is disconcerting.  am still looking at how to fix this, though what I have read so far seems to indicate this is a debian package problem.  I may try to install it from the source and see if that changes anything, though I need to find better documentation. (**EDIT:** I found an answer to this and [posted what I did here]("http://www.damontimm.com/blog/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/"))
[*]as with NFS, use iptables/firewall to restrict access .
[/LIST]

Appreciate any help/advice anyone has.  Thanks.

---

### Post by sonic2000gr on 2007-04-09
> Security for SSH:

    * turn off password login; only use public/private key login (with passphrase)

This is actually the safest approach, no one can login even if they have a valid username / password combo unless they carry a key with them and know the passphrase. 

>     * could use a non-standard port, but would rather be secure in the standard one then rely on someone not to check for a high open port number


I aggree with you here, running on a non standard port is just adding a false sense of security

>    * could install fail2ban

Have not done it myself, the list of banned ips will probably grow too much, and rarely will you see the same IP trying again.

> * disable root login (though, if I understand it correctly sudo still will work, which is great)

You should certainly disable root logins, in fact the key you will create for accessing SSH should be for a standard account. Since you will turn off password (keyboard interactive) authentication no key=no login so you are safe. And yes, you will be able to either su or sudo AFTER login. 

> Security for NFS:

    * using iptables/firewall, restrict access only to computers on my local network and in a specific range (i don't know how to do this, yet, however)

This would be fairly easy to do, since you are running behind a router. Your server will have a well defined local ip address, something like e.g. 192.168.0.10 and your internal network will have similar address in the range 192.168.0.x

You could easily write the following rules:

- Allow all communications from the internal network (192.168.0.x) to the server (192.168.0.10) - that is assuming you trust the internal network.
- Allow incoming data to the server from the outside world assuming the server STARTED the connection in the first place (e.g. you are viewing a web page while sitting at the server console, or you are updating with apt-get etc)
- Allow incoming connections to the SSH port from everywhere
- Quietly ignore everything else.

This is a simple and understandable firewall (more or less what protects my servers) and the following rules implement it:

-A INPUT -d 192.168.0.10 -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A INPUT -s 192.168.0.0/255.255.255.0 -d 192.168.0.10 -j ACCEPT 
-A INPUT -d 192.168.0.10 -p tcp -m tcp --dport 22 -j ACCEPT 
-A INPUT -d 192.168.0.10 -j DROP 

The OUTPUT policy should be set to allow, the INPUT to deny (although the last rule already does that)

If you want to be more specific and restrict ports on the internal network also, bear in mind the NFS server normally uses some random ports at each startup and can present a hassle to firewall. This behavior is however configurable in some way and you may want to research this a bit further. I 've read about it but have not done it myself.

Can't tell you much about netatalk, never had (and probably never will) have to use it...

---

### Post by thornomad on 2007-04-09
Thanks for the reply.  I actually figured out the netatalk (AFP) clear text problem, so, will probably just rely on the firewall you suggested below:

> **sonic2000gr said:**
> -A INPUT -d 192.168.0.10 -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A INPUT -s 192.168.0.0/255.255.255.0 -d 192.168.0.10 -j ACCEPT 
-A INPUT -d 192.168.0.10 -p tcp -m tcp --dport 22 -j ACCEPT 
-A INPUT -d 192.168.0.10 -j DROP 


I will copy these down and take some time to read about setting it all up correctly.

As for the "do I trust my local area network?" ... well, I guess I do.  It is my home and wirelessly I use WEP security.  Not sure if that is enough, but someone would have to park pretty close to my house to get on my system ... and then they would have to break into the WEP bit.

Thanks again.  Great help.

---

### Post by sonic2000gr on 2007-04-09
If it is your home, this firewall is more than enough. The trust on the home network mainly refers to any potential malicious local users. Unless you start attacking the server yourself (I do it on mine from time to time :) ) you are safe enough. If you need help with the rules or anything just ask. By the way, I've written an easy tutorial on this very subject and it is here:

[http://debian12.dyndns.org/index.php/Firewall_Rules]("http://debian12.dyndns.org/index.php/Firewall_Rules")

It is quite complete and has a script you can use to load the rules automatically on startup.

(The link may be a little slow, this is running on my home server as well :))

---

### Post by thornomad on 2007-04-09
Awesome. Thanks.  I've always wanted my own wiki -- smile.  I am a dyndns home user myself.   Hopefully will be trying their dynamic dns service (which isn't free, I guess, but I can use my domain name).

So IP tables sort of working like a cascading style sheet ... starts at the top and works down ... and any rules below a rule take precedent?

Thanks.

---

### Post by sonic2000gr on 2007-04-09
The rules work from top to  bottom until the packet either gets accepted by one or gets dropped / rejected. That's why the last rule simply drops everything - that is anything that has not matched any of the rules above. If the packet does not match any rule, then the policy is used. This cannot happen in my version of the rule set though. By the way dropping means silently discarding, what most people referring to firewalls call "stealth"

---

### Post by huygens on 2007-04-10
> **thornomad said:**
> 
**Security for SSH**:[LIST]
[*]turn off password login; only use public/private key login (with passphrase)
[*]could use a non-standard port, but would rather be secure in the standard one then rely on someone not to check for a high open port number
[*]could install fail2ban
[*]disable root login (though, if I understand it correctly sudo still will work, which is great)[/LIST]
Two good resources to secure or let's say improve the security of SSH:[LIST=1]
[*][https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
[*][http://doc.gwos.org/index.php/SecureSSH](http://doc.gwos.org/index.php/SecureSSH)[/LIST]As for the standard port or not... I have also my own server at home which uses SSH. I'm using the default port. However, I have used a different port on the router. I mean that it waits for SSH connection on a non-standard port on the internet side and forward them to my server on my local network on the standard port. I'm not doing that for security reason, but rather because when outside my network and trying to reach my server, the standard SSH port was sometimes blocked by the ISP.
I'm using the HTTPS port on my router because it is one of the few ports that it rarely blocked.

> **thornomad said:**
> 
**Security for NFS**:
[...]
**Security for AFP (netatalk)**:

In my opinion, I would preferably use SMB/CIFS (Samba) instead of NFS, so Windows, Mac OS and Linux/Unix machine can access it using password authentication (encrypted by default since Windows 2K/XP). I'm not sure NFS is much faster than SMB, but I'm sure that sometimes with NFS you end up with a corrupted downloaded file because it usually uses UDP instead of TCP for the transport protocol.

As for protecting this services with a firewall, 'shorewall' is a good solution. It is a command line front end to iptables making them easy to configure.
A [quick start guide for Shorewall]("http://www.shorewall.net/shorewall_quickstart_guide.htm") is available, and most probably this is the specific one for you: [http://www.shorewall.net/standalone.htm](http://www.shorewall.net/standalone.htm)

---

### Post by Catsworth on 2007-04-10
> **thornomad said:**
> It is my home and wirelessly I use WEP security.  Not sure if that is enough, but someone would have to park pretty close to my house to get on my system ... and then they would have to break into the WEP bit.

Upgrade to WPA if you can, WEP is horribly insecure and *very* easy to crack.  This is going to be a real weak point in your security, especially if your firewall's tables are set to *always* trust any traffic from your internal network.  It wouldn't take too long to break that WEP key and get a valid internal address.

---

### Post by huygens on 2007-04-11
> **thornomad said:**
> As for the "do I trust my local area network?" ... well, I guess I do.  It is my home and wirelessly I use WEP security.  Not sure if that is enough, but someone would have to park pretty close to my house to get on my system ... and then they would have to break into the WEP bit.

Seems that for breaking into the WEP bit is becoming easier: [http://www.cdc.informatik.tu-darmstadt.de/aircrack-ptw/](http://www.cdc.informatik.tu-darmstadt.de/aircrack-ptw/)

You can also read this French article if you understand this language: [http://sid.rstack.org/blog/index.php/2007/04/04/180-les-clous-sont-la-mais-vous-aviez-oublie-la-couronne](http://sid.rstack.org/blog/index.php/2007/04/04/180-les-clous-sont-la-mais-vous-aviez-oublie-la-couronne)

---

### Post by thornomad on 2007-04-23
> **huygens said:**
> In my opinion, I would preferably use SMB/CIFS (Samba) instead of NFS, so Windows, Mac OS and Linux/Unix machine can access it using password authentication (encrypted by default since Windows 2K/XP). I'm not sure NFS is much faster than SMB, but I'm sure that sometimes with NFS you end up with a corrupted downloaded file because it usually uses UDP instead of TCP for the transport protocol.

As for protecting this services with a firewall, 'shorewall' is a good solution. It is a command line front end to iptables making them easy to configure.
A [quick start guide for Shorewall]("http://www.shorewall.net/shorewall_quickstart_guide.htm") is available, and most probably this is the specific one for you: [http://www.shorewall.net/standalone.htm](http://www.shorewall.net/standalone.htm)

Thanks for those links; I am going to checkout shorewall.  Seems up my alley.  I have AFP setup (encrypted authentication) and will eventually get around to NFS.  I don't have any windows machines ... I know SMB works with windows but ... well ... I don't know.

Thanks for the SSH links as well.

---

### Post by 655 on 2008-02-16
I, too, have a locally-shared NFS fileserver that I also control via SSH when the need arises.

I have taken no steps to secure it, and this concerns me.  I am in essentially the same position as the OP.  The included links and tutorials are useful to some extent, but I am several ranks below the OP in technical understanding and am kind of overwhelmed.

For instance, I would like to use public/private SSH keys to bolster the SSH end, but I am at a loss as to how to go about this.  The various information I found on the net seems to be written in a way that presupposes certain knowledge on the part of the user.

Long story short, my goal is the same as the OP's: secure both the SSH and NFS end of the local fileshare via keys, restrictive iptables rules, etc... but this is a plea for a more dumbed-down tutorial on how to approach this.

If someone could provide some more user-friendly links, or hand-hold me through some steps, or something along those lines, I'd be most appreciative.  I've done what I can with reading man pages and scouring the net, but I can't find the "missing link" between primer-type information and more advanced stuff.

There is just one PC accessing the fileserver, no Samba, no Windows machines, no Macs or anything, so the physical layout is relatively straightforward, and the scope of its use very limited.

Thank you.

---

