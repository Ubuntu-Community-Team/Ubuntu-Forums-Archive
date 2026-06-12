---
title: "Which FTP with SSL Implicit?"
date: 2006-04-18
forum: Server Platforms
---

### Post by XPerienced on 2006-04-18
Hi!

Which FTP with SSL Impilicit should I choose? It got to work with FlashFXP for local filetransfers.

XPerienced

---

### Post by fdoving on 2006-04-18
I recommend vsftpd.
You can also look at proftpd.

- Frode

---

### Post by jinacio on 2006-04-18
proftpd has had some security "issues".

vsftpd is good, and VERY simple to configure.

btw: from my experiences, FTP with TLS or SSL + firewall = no go :(

---

### Post by XPerienced on 2006-05-01
I'm sorry I missed your answers.

What's the problem with firewall and vsftpd? I have IPCop, but I would like to have a firewall on the computer aswell. I would like to have a secure network to prevent attacks before they happens and not prevent a new a attack when it happed. ;-)

I'll check for HOWTO:s on vsftpd. I think it's pretty common, cause I heard it a couple of times in FTP-disscussions, but I didn't remember that it supported Implicit SSL.

XPerienced

---

### Post by LordHunter317 on 2006-05-01
Implicit SSL?  You mean STARTTLS?

And you cannot have a NAT firewall on a FTP server doing TLS, and a port-filtering device will have to have most ports open.  The problem is it cannot read the FTP protocol to determine what ports to open.  Unless your daemon were smart enough to control the firewall itself (none are) you're stuck.  No point in bothering.

---

### Post by XPerienced on 2006-05-01
So your accually actually mean there's no chance to make the FTP work? Cause I really need a FTP to transfer files secure on the network. I don't care if it's not  necassary. If I would like to have SSL Implicit for local transfers, thats the shit I 'm going to have. So please don't be that guy that argue. :-)

Can I install Implicit FTP with proftd?

XPerienced

---

### Post by LordHunter317 on 2006-05-02
[QUOTE=XPerienced]So your accually actually mean there's no chance to make the FTP work?[/quote]It can be made to work, you just can't do dynamic firewall traversal.  The ports must be left open permamently.

> Cause I really need a FTP to transfer files secure on the network.Use SSH and SFTP.

> Can I install Implicit FTP with proftd?Again, there is no such thing I'm aware of.

---

### Post by XPerienced on 2006-05-02
And leaving three-four ports open permantly is risky even if there od? Like 49839. I don't mean I would open port 21. :-)

XPerienced

---

### Post by LordHunter317 on 2006-05-02
[QUOTE=XPerienced]And leaving three-four ports open permantly is risky even if there od?[/quote]I wouldn't leave just 4, but no, it's not especially risky.

> I don't mean I would open port 21. :-)How would anyone talk to your FTP server then?

I really think you should look at using SFTP.  It already works if you have an SSH server installed, and it's infinitely less fuss to get working with firewall traversal.

---

### Post by XPerienced on 2006-05-02
This really makes me concerned, cause the only thing I need and want is a FTP with Implicit SSL on a secure computer.

Why is it so hard?

I transfered files with SSH, but it's to slow so I would like something else like FTP.

XPerienced

---

### Post by LordHunter317 on 2006-05-02
[QUOTE=XPerienced]This really makes me concerned, cause the only thing I need and want is a FTP with Implicit SSL on a secure computer.[/quote]**Again, what do you mean Implicit SSL?  There is no such thing.**

> I transfered files with SSH, but it's to slow so I would like something else like FTP.FTP/SSL will likely not be any faster.  OpenSSH has some major buffering issues in client and server, but they're generally irrelevant if you're transferring files.  Encryption is rather CPU intensive, did you try blowfish?

---

### Post by behemot on 2006-05-02
[QUOTE=XPerienced]I'm sorry I missed your answers.

I have IPCop, but I would like to have a firewall on the computer aswell. I would like to have a secure network to prevent attacks before they happens and not prevent a new a attack when it happed. ;-)

XPerienced[/QUOTE]

Have you considered old good vpn.  There are adons for Openvpn and OpenSWAN for IPcop.

I am not certain that it will be any faster then ssh though and you will need to install client software.

---

### Post by frio on 2006-07-12
Lordhunter317, I found this in the help file from WS_FTP Pro to explain the differences. I didn't know either until I read this.
 
> 
**SSL vs Implicit SSL** 
WS_FTP uses two types or 'flavors' of the SSL protocol. Explicit SSL and Implicit SSL. The encryption strength and stability is virtually the same. The only difference lies in the way the client communicates with an FTP server during connection negotiations, and the port that the server is 'listening' on.
**Explicit SSL** - Client starts the connection with a connection 'in the clear' and then attempts to secure the connection before sending the username and password.
**Implicit SSL** - In this version, the client sends all negotiations to the server in a secure manner. Implicit SSL connections use port 990, so any attempt at connecting to a server that is not configured for Implicit SSL will fail.


---

### Post by LordHunter317 on 2006-07-13
Which is the STARTTLS extension, like I said eariler.  But there isn't an FTP server out there that supports STARTTLS and does't support a dedicated SSL port.

---

### Post by Jaxilian on 2007-04-27
so still no answer to this thread? There is no client whatsoever with implicit SSL???

---

