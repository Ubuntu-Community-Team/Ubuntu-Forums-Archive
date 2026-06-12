---
title: "ftp server &amp; client behind class A subnets"
date: 2016-09-03
forum: Server Platforms
---

### Post by Vegan on 2016-09-03
I have been trying to figure out how to get a basic unsecure ftp session working

i have vsftpd installed, i can log on but i get a 500 error illegal port with Filezilla

i have port 20 and 21 open rest are firewalled, do i need to open more ports?

i tried using a browser, that did not work either

suggestions or ideas? this day and age world dog have so many NAT layers it hard to figure it all out

---

### Post by TheFu on 2016-09-03
Don't use plain FTP. [Why not?]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp")

There aren't many good reasons to have plain FTP enabled anymore.

---

### Post by Vegan on 2016-09-03
I just need to download logs, nothing important

---

### Post by TheFu on 2016-09-03
> **Vegan said:**
> I just need to download logs, nothing important

Logs often contain highly sensitive stuff. Highly. Sensitive. Even if that data isn't sensitive to you, it might be to the clients, customers, users, visitors.

Plus ... plain FTP should have died in 1995 with telnet (which took a decade longer to die in NE devices).  We should do better and use encrypted transmission whenever possible.  IMHO.

---

### Post by darkod on 2016-09-04
I agree with TheFu that you shouldn't be so "light" on security... Further more, I don't understand why ftp provided you already have ssh access to that server. I assume you do because you must be administering it in some way. So why not use sftp which is secure and needs the same port 22 as ssh that most linux servers already have enabled.

But to go back to your ftp question, you can't simply use ftp behind a firewall. It doesn't rely only on port 20 and 21 but also on dynamic ports (in active mode). That's why behind a firewall you need to use ftp in passive mode. Set a passive port range in the config, and then open and forward those ports in the firewall to your ftp server. That will work...

As for the security, if you want to ignore it, your problem...

---

### Post by Vegan on 2016-09-04
I have opened 55536-55663 which AFAIK the standard upper ports used by FTP

---

### Post by TheFu on 2016-09-04
> **Vegan said:**
> I have opened 55536-55663 which AFAIK the standard upper ports used by FTP

Didn't know there were "standard" ports used for the plain, non-secure, FTP data connection. I know each OS and each FTP server can set the range used  "32768 through 61000" if there is sufficient RAM, is what I've seen for Linux in the OS defaults.  

According to a [vsftpd.conf online manpage]("http://vsftpd.beasts.org/vsftpd_conf.html") - the defaults are to use any ports for FTP data, so you would have needed to change those settings.

---

### Post by Vegan on 2016-09-04
got a setting i can use, nothing in the default popped up

---

### Post by cariboo on 2016-09-04
I use ssh and sftp for everything, no need to set up extra services that aren't needed. Using private/public keys makes it as easy as typing:

```
ssh cariboo@server
```

to log in. Admittedly my home network is private, and no one has access from the outside world, but it would work the same from the outside if I allowed access.

For GUI access I use nautilus, first by opening another tab using Ctrl-t, then opening the address bar by typing Ctrl-l (that's a lower case L) then typing:

```
sftp://cariboo@server
```

I have the systems I need to access aliased in /etc/hosts eg:

```
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	skynet
192.168.0.200	likely
192.168.0.205	willy
192.168.0.201	server2
192.168.0.111	server3
```

You can use the following page to setup ssh:

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by 1clue on 2016-09-04
Ftp was made a really long time ago. Back when gopher was as valid a protocol as http, and the Internet was still used only by the US military, government and schools.  It really really needs to die permanently, for far many more reasons than I can list here.

The biggest reason that applies here is that it's incredibly difficult to setup over NAT.

The second biggest reason is security.  Not for the ftp server, but for your entire network.

I strongly recommend ssh protocol, which can be easily handled by pretty much any firewall, with or without NAT and which does not compromise your network.  You can easily tell it to act like an ftp server (sftp in FileZilla, since you mentioned that) and have limited access both in terms of directories accessible and in terms of things you can do with the connection.

---

### Post by Vegan on 2016-09-05
anyway i have tried hard coding the virtual machine IP address, opened up ports 21-65535

still cannot get a directory

Status:	Connection established, waiting for welcome message...
Status:	Insecure server, it does not support FTP over TLS.
Status:	Server does not support non-ASCII characters.
Status:	Logged in
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is the current directory
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PASV
Response:	550 Permission denied.
Command:	PORT 10,227,110,55,217,106
Response:	200 PORT command successful. Consider using PASV.
Command:	LIST
Response:	500 OOPS: vsf_sysutil_bind
Error:	Failed to retrieve directory listing
Status:	Connection closed by server

---

### Post by TheFu on 2016-09-05
> 
Response: 200 PORT command successful. Consider using PASV.

???  Are all the possible ports open all the way from the internet? Does the ISP not block all those ports ... or some of them?

---

### Post by Vegan on 2016-09-05
i have opened 21-65535 to world+dog

---

### Post by TheFu on 2016-09-05
> **Vegan said:**
> i have opened 21-65535 to world+dog

And the ISP? What have they opened?

OTOH, sftp is much easier. 1 port. Done.

---

### Post by 1clue on 2016-09-05
You're beginning to experience what we've been talking about, at least the first part where configuration is so difficult.  The part where the world hacks every system in your house/office is probably not yet complete.

Reminding you of the steps:
First, your ftp software must be able to handle service through nat.
Second, your ftp server's firewall software must be configured to enable ftp, routing it to your appropriate server hardware. Not sure if NAT knowledge is required here.
Third, your router/firewall/nat device must be designed specifically to handle ftp over NAT.  In most cases, a small office/home router is designed to BE the ftp server, you have to add the disk directly.

Now, if as you say you opened all ports to the world and his dog, then that means you've also allowed the world and his dog access to everything you have in your home or office, wherever this is.  The entire benefit of having a separate device handling your routing and firewall duties is gone.

For the past 15 years, the ISPs I've dealt with do not block ports.  But that doesn't mean all ISPs allow all traffic. I know some advertise that they firewall your connection.

---

### Post by Vegan on 2016-09-05
I have changed the firewall back to port 21 only for FTP

maybe there are some bugs with vsfptd and or Filezilla?

---

### Post by TheFu on 2016-09-06
> **Vegan said:**
> I have changed the firewall back to port 21 only for FTP

maybe there are some bugs with vsfptd and or Filezilla?

I thought plain FTP needed ports 20 and 21 open? All this time, was port 20 closed?
Also, for any non-trivial software, there ARE definitely bugs. vsftpd project has some interesting history related to security. Might be worth looking that up with google. :\

---

### Post by Vegan on 2016-09-06
I am now making a post on my linux site so I can eventually have a solution for others who are swiping my Excedrin

[http://linux-guru.azurewebsites.net/?p=159]("http://linux-guru.azurewebsites.net/?p=159")

---

### Post by 1clue on 2016-09-06
Be sure to include [http://lmgtfy.com/?q=public+ftp+server+security+best+practices](http://lmgtfy.com/?q=public+ftp+server+security+best+practices)

Also keep in mind that standard ftp sends both login and password in plain text. The protocol does this, so there's no fixing it. Meaning that any standard linux account which has ftp access can be retrieved by anyone who has access to any router between you and your ftp server. Let me also point out that coffee shops and restaurants are extremely commonly trolled by people with packet sniffers looking for exactly this sort of information.

---

### Post by Vegan on 2016-09-06
can we get back to the connection problem first, once a connection is achieved then the next step

learn to walk before running

---

### Post by 1clue on 2016-09-06
OK last post then:

My intent was to help you realize that ftp is an extremely bad idea in absolutely every scenario.  *Not only is it insanely difficult to configure, it cannot be made secure, ever.* You risk not only compromising your ftp server data, but the box and the entire network it's attached to.

As a contrast, if you can ssh to the box from outside, then your sftp server is already configured and ready to go. A few things could be done to help secure it but they're really not necessary to have a much more secure server than the ftp protocol can possibly have.

I have been as persistent as I have because you're talking about a datacenter. Which implies a corporate world, which means you have much more to lose than just some files on an ftp server.

Good luck and have fun.

---

### Post by Vegan on 2016-09-08
is openssh available, ideally one that does not suffer from heartbleed

---

### Post by QIII on 2016-09-08
The heartbleed vulnerability was patched some time ago.

That was SSL anyway.

---

### Post by Vegan on 2016-09-08
I noticed that the same problems with secure FTP as before, getting an unroutable address.


#anonymous_enable=YES
#set the local root to whatever the FTP will be using for transfers
ascii_download_enable=NO
ascii_upload_enable=NO
chown_uploads=NO
connect_from_port_20=YES
dirmessage_enable=YES
file_open_mode=0666
ftpd_banner=Welcome to LAMP FTP server on Azure.
listen=YES
local_enable=YES
local_root=/home/ftp
local_umask=0022
log_ftp_protocol=YES
ls_recurse_enable=NO
pam_service_name=vsftpd
pasv_addr_resolve=NO
pasv_enable=YES
pasv_max_port=60002
pasv_min_port=60001
port_enable=YES
rsa_cert_file=/etc/ssl/private/vsftpd.pem
use_localtime=YES
write_enable=YES
xferlog_enable=YES
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=NO

---

### Post by bashiergui on 2016-09-08
> **TheFu said:**
> And the ISP? What have they opened?
I didn't see where you verified that your ISP has your needed ports open.

If yes, then perhaps this detailed guide will help showing how to set up vsftp with ssl using filezilla:
[https://www.digitalocean.com/community/tutorials/how-to-configure-vsftpd-to-use-ssl-tls-on-an-ubuntu-vps](https://www.digitalocean.com/community/tutorials/how-to-configure-vsftpd-to-use-ssl-tls-on-an-ubuntu-vps)

---

### Post by Vegan on 2016-09-08
Status:	Connection established, waiting for welcome message...
Status:	Insecure server, it does not support FTP over TLS.
Status:	Server does not support non-ASCII characters.
Status:	Logged in
Status:	Retrieving directory listing...
Status:	Server sent passive reply with unroutable address. Using server address instead.

---

### Post by Vegan on 2016-09-08
tried SFTP and finally I have a connect, so at least now I can download logs etc

---

### Post by 1clue on 2016-09-09
OK I lied about the last post I guess.

You can do the sftp protocol with openssh-server, and it's secure. You already have openssh on your box. You can remove every other ftp server on your box.

You can easily (in minutes) secure it so some users only get sftp functionality. 

[https://help.ubuntu.com/lts/serverguide/openssh-server.html](https://help.ubuntu.com/lts/serverguide/openssh-server.html) 
[http://askubuntu.com/questions/134425/how-can-i-chroot-sftp-only-ssh-users-into-their-homes](http://askubuntu.com/questions/134425/how-can-i-chroot-sftp-only-ssh-users-into-their-homes)

Doing this is secure, and it handles firewalls, VPNs, NAT and whatever else easily and securely.

I will gladly post examples for this.

In your /etc/ssh/sshd_config file, paste this at the end:
```

Subsystem sftp /usr/lib/openssh/sftp-server

Match Group sftponly
        ChrootDirectory /home/ftp/clients/%u
        ForceCommand internal-sftp
        AllowTcpForwarding no

```

Check /etc/groups for anything ftp, you don't want to collide with something already there.
```
grep ftp /etc/group
```

Find the highest group id below 1000.  1000 and up is, by tradition, where users go. You want to pick unused numbers.
```

sort -t: -nk3 /etc/group | less

```

For me, my group id's went to 117 and 118.
```

addgroup -gid 117 sftponly
addgroup -gid 118 ftp

```

You (probably) want two groups.  sftponly tells openssh which groups to restrict to their home directories.  ftp is file permissions for your ftp shared ftp directory.

For me:
```

$ grep ftp /etc/group
sftponly:x:117:bob,joe
ftp:x:118:ken,joanna,basejump,jkuhn,joe,buildbot,snimavat,aap,teamcity

```

Note that the sftponly people get ONLY the ftp command list. They can connect with FileZilla or any other sftp-enabled client. 

You should ensure that fail2ban is working, because you will surely get brute force attacks on any open standard port.

---

### Post by Vegan on 2016-09-09
so do i need to use vsftpd anymore or should i get rid of it?

---

### Post by 1clue on 2016-09-09
I would get rid of it. It's good software but for a bad protocol that can't be fixed.

---

### Post by Vegan on 2016-09-10
how about TLS etc, anything there i can bolt on?

---

### Post by 1clue on 2016-09-10
TLS should be inherent in your OpenSSH.

```

openssl ciphers -v | grep -i tls

```

---

### Post by 1clue on 2016-09-10
That said there are quite a few things you might want to do to your ssh or ssl configuration.

If it makes sense for your setup, for example, you may require all logins to have a key file.  The possibilities here are numerous, and what works for me will probably not work for you, and vice versa.

ssh is highly configurable. Generally speaking if you can require an ssh key of some sort then your server will be more secure. It's possible to require both a password and a key, and also possible to hook into a multifactor authentication scheme, but I've never attempted it. I believe this involves tying into a service which provides text messaging or callback numbers.

---

### Post by 1clue on 2016-09-10
I would advise caution when playing with this.  Try it on a host where you have physical access to the console, as you can very easily lock yourself out of your system with respect to network shells.  Ask me how I know.

---

### Post by 1clue on 2016-09-10
The place to start with keys is to create one on your client:

```
ssh-keygen -t rsa
```

Then copy your public file to your server:

```
scp ~/.ssh/id_rsa.pub you@your.ftp.com:
```

Login to the remote box and append your local key to the authorized_keys file:

```

ssh you@your.ftp.com
cat id_rsa.pub >> .ssh/authorized_keys
rm id_rsa.pub
exit

```

now you should be able to ssh or sftp to the remote box without a password.  This is actually more secure than the password access as long as you're not dealing with a public terminal as a client.

The good news here is that you haven't disabled logging in with a password yet.  In order to do that you need to change /etc/ssh/sshd_config.

---

### Post by Vegan on 2016-09-10
I have a x.509 certificate tool with Visual Studio, can I use that to make a self signed certificate for a https operation?

---

### Post by 1clue on 2016-09-11
I'm by no means a certificate expert but I have bought ssl/tls  certificates from a certificate authority for more than a decade now.


[LIST=1]
[*]Are you familiar with self-signed certificates?
[*]Do you intend this for development purposes or use within your organization?
[*]Are you using apache2 web server or something else?
[/LIST]

Every time I do a certificate I google the latest process because it changes every few years, in the details at least.  Here's what I ***THINK***:

[LIST=1]
[*]I believe that certificates themselves are cross-platform at least with respect to operating system.
[*]At one point different web servers required different certificate formats. I don't know if that still applies but I think anything can take an x.509 cert.
[*]If you want to do personal development self-signed certs then you need to accept that public key into your browser.
[*]If you have a few computers that want to use the same cert the same process applies.
[*]If you have a large organization that wants to use this setup then you need to set up a certificate authority, add it to every computer in your org and then sign your certificates with its master key.
[*]My experience stops with step 4.
[/LIST]

---

### Post by 1clue on 2016-09-11
Are you asking about an x509 with respect to openssh? I don't have an answer for that at all.  It never occurred to me that someone would do that.

---

### Post by Vegan on 2016-09-11
I am looking to use it with apache

---

### Post by 1clue on 2016-09-12
This should still be relevant on 16.04

[https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)

---

### Post by Vegan on 2016-09-12
I was wondering how much work and how many servers would I need to be a cloud certificate vendor?

---

### Post by 1clue on 2016-09-12
You mean for random users to login to your hosted web servers and not get a warning?

You'll need to set up a public (real) certificate authority, that is recognized/trusted by the likes of VeriSign and such.

If you mean some internal corporate cloud, then it's probably a bit easier. In that case the corporation controls the hardware and software installed, they add their internal-only certificate authority (same software used by VeriSign and others) to every computer in the org, and then you can sign internally. But every client which does not trust your certificate authority will have an "untrusted site" sort of warning.

---

### Post by 1clue on 2016-09-12
It's best if you open a new thread with regards to the x.509 certificate.

There are hundreds of helpful, knowledgeable people on this forum who will ignore this thread because it's related to FTP servers.

I'd suggest a topic like 'Help creating a certificate authority"

---

