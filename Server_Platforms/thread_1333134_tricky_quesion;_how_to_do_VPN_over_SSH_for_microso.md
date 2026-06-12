---
title: "tricky quesion:; how to do VPN over SSH for microsoft xp client?"
date: 2009-11-21
forum: Server Platforms
---

### Post by frenchn00b on 2009-11-21
I made  a picture here: 

[B]I made a schematic of what I would like : 

[http://yellowprotoss.ye.funpic.org/website/pptp_over_ssh/PPTP_SECURED_UBUNTU.jpg](http://yellowprotoss.ye.funpic.org/website/pptp_over_ssh/PPTP_SECURED_UBUNTU.jpg)[/B]


here they say that pptp is not secured: [http://www.poptop.org/](http://www.poptop.org/)

---

### Post by mojorisinagain on 2009-11-21
PPTP is a VPN implementation method, but does not encrypt the payload - i.e. confidentiality.

SSH is a tool for encrypting login and file copy sessions and encrypts a session from point-to-point, client to server, and though it may primarily be used for login and copy sessions, it is often used to tunnel "in-the-clear" sessions like TELNET and FTP.  So, you can look at SSH as a point-to-point VPN solution ... with encryption.

Take a look at the PLINK ... a Windoze SSH-like command line tool:
[http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter7.html#plink](http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter7.html#plink)

There are other ways, but this is pretty straight forward.  You will need to understand port-forwarding.  Here's a reference:
[http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter3.html#using-port-forwarding](http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter3.html#using-port-forwarding)

MJ

---

### Post by frenchn00b on 2009-11-21
> **mojorisinagain said:**
> PPTP is a VPN implementation method, but does not encrypt the payload - i.e. confidentiality.

SSH is a tool for encrypting login and file copy sessions and encrypts a session from point-to-point, client to server, and though it may primarily be used for login and copy sessions, it is often used to tunnel "in-the-clear" sessions like TELNET and FTP.  So, you can look at SSH as a point-to-point VPN solution ... with encryption.

Take a look at the PLINK ... a Windoze SSH-like command line tool:
[http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter7.html#plink](http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter7.html#plink)

There are other ways, but this is pretty straight forward.  You will need to understand port-forwarding.  Here's a reference:
[http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter3.html#using-port-forwarding](http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter3.html#using-port-forwarding)

MJ

I got say that SSH can only forward TCP

and PPTP is GRE :(


can I do this with PLINK ?   [http://yellowprotoss.ye.funpic.org/website/pptp_over_ssh/PPTP_SECURED_UBUNTU.jpg](http://yellowprotoss.ye.funpic.org/website/pptp_over_ssh/PPTP_SECURED_UBUNTU.jpg)
I like the VPN windows XP, to be using hte regular connecting client to server tool as above top right

---

### Post by mojorisinagain on 2009-11-21
What is the goal you're trying to achieve?

The picture you have shows you're trying to use the miniport VPN connection to access 'host.vpn.ucf.edu' ... is this correct? If yes, then the University should have instructions on the VPN client you should use and how to configure it. However, if you're not trying to connect to 'host.vpn.ucf.edu' then please further explain what are your connection requirements.

[LIST=1]
[*]What application or service do you need on the Linux box that you require a VPN?
[*]Is there some application that says you must use PPTP or a VPN?
[*]Do you require a "secure", encrypted VPN connection or unencrypted VPN session (VPNs do not necessarily have to be encrypted - though generally it's implied)?
[/LIST]
MJ

---

### Post by frenchn00b on 2009-11-21
> **mojorisinagain said:**
> What is the goal you're trying to achieve?

The picture you have shows you're trying to use the miniport VPN connection to access 'host.vpn.ucf.edu' ... is this correct? If yes, then the University should have instructions on the VPN client you should use and how to configure it. However, if you're not trying to connect to 'host.vpn.ucf.edu' then please further explain what are your connection requirements.

[LIST=1]
[*]What application or service do you need on the Linux box that you require a VPN?
[*]Is there some application that says you must use PPTP or a VPN?
[*]Do you require a "secure", encrypted VPN connection or unencrypted VPN session (VPNs do not necessarily have to be encrypted - though generally it's implied)?
[/LIST]
MJ

was example
host.vpn.ucf.edu' ... 


I am in the world, australia, japan,... and I access my server using PPTP + securty.

Why not OPENVPN ?
because it is too difficult for me, and I want to use the degfault installed XP microsoft VPN client, as shown.

---

### Post by mojorisinagain on 2009-11-21
Ok . . . I understand that you want to have a secure/encrypted connection to your Linux box.

I don't think OpenVPN would be harder to configure than trying to get PPTP tunneled over SSH.  By itself, SSH (using Windoze utilities PuTTY, PLink, PSCP, WinSCP) can get you command line access, X11 access, and access to a back-end  database (if that's your requirement).

To help you with a good solution, I would like to know:

[LIST=1]
[*]Do you need file sharing access on the Linux box?
[*]Do you need command line access?
[*]Do you need X11 access?
[*]Do you have a Windoze based application that used a database on the Linux box?
[/LIST]
For item #1 above, I've not tried accessing Linux file shares, via SAMBA, over SSH, but I would think it is possible.

Items #2 and #3 above I routinely do via SSH; #2 via the 'ssh' command (Linux/UNIX systems clients, PuTTy from Windoze clients).  I use my Windoze based X11 client over an SSH link (using PLink).

MJ

---

### Post by mojorisinagain on 2009-11-21
FYI ... this may not be everything you need, but it is an idea for further brain-storming.

Access Linux from XP: [http://www.cyberciti.biz/faq/access-linux-from-windows-xp-system/](http://www.cyberciti.biz/faq/access-linux-from-windows-xp-system/)

MJ

---

### Post by frenchn00b on 2009-11-21
> **mojorisinagain said:**
> FYI ... this may not be everything you need, but it is an idea for further brain-storming.

Access Linux from XP: [http://www.cyberciti.biz/faq/access-linux-from-windows-xp-system/](http://www.cyberciti.biz/faq/access-linux-from-windows-xp-system/)

MJ


nice link, SSH and tunneling I do already, port 22. 

I wanted a real VPN to the server box, for working to gaming on all ports enabled like as if I was at home. 

Concerning the VPN would you have any brainstorming ideas?

---

### Post by Akita on 2009-11-21
If you have a decent SSH client on the Windows machine and you can live with TCP-only traffic, you can tunnel pretty much anything and everything. If all you want to do is a default Microsoft PPTP VPN to a single server, there are FAQs and How-Tos all over the place for configuring pptpd on a linux box. PPTP *IS* encrypted, some people just don't like the way it does business much. Unless you're the military or a bank, I doubt anybody cares enough about your traffic to spend the time or the effort to hack your VPN. There is zero need, other than intelectual curiosity, to bog down the tunnel and overly complicate life mixing PPTP with SSH. As somebody already mentioned, if you want something more robust than PPTP, then use something more robust (OpenVPN). The kludge of PPTP over SSH is going to run slower, be harder to configure, be harder to diagnose problems on, etc.

---

### Post by frenchn00b on 2009-11-21
> **Akita said:**
> If you have a decent SSH client on the Windows machine and you can live with TCP-only traffic, you can tunnel pretty much anything and everything. If all you want to do is a default Microsoft PPTP VPN to a single server, there are FAQs and How-Tos all over the place for configuring pptpd on a linux box. PPTP *IS* encrypted, some people just don't like the way it does business much. Unless you're the military or a bank, I doubt anybody cares enough about your traffic to spend the time or the effort to hack your VPN. There is zero need, other than intelectual curiosity, to bog down the tunnel and overly complicate life mixing PPTP with SSH. As somebody already mentioned, if you want something more robust than PPTP, then use something more robust (OpenVPN). The kludge of PPTP over SSH is going to run slower, be harder to configure, be harder to diagnose problems on, etc.

well I was thinking that wiht PUTTY I could do : 
vpn port 1723

I need security, as good as SSL and SSH, but cannot install openvpn on the pc. Just regualr vpn.
 
open putty
put the IP of the SSH/PPTP server, port 22
then
click on + next to SSH
go into tunnels:
```
L1723 localhost:22
```

or I should put as this?
[http://www.vrdc.cornell.edu/guides/how-to-use-VirtualRDC/fig-putty-tunnel2.png](http://www.vrdc.cornell.edu/guides/how-to-use-VirtualRDC/fig-putty-tunnel2.png)
```
L1723 localhost:1723
```

here there is example for vnc
[http://www.maths.utas.edu.au/People/Hill/vnc/vnc.html](http://www.maths.utas.edu.au/People/Hill/vnc/vnc.html)
I just replace 5900 per 1723, no ?
it that possible with pptp?

I heard that not

---

### Post by mojorisinagain on 2009-11-22
The VNC example is very good.  If accessing your Linux box through VNC gets you what you need, then implement.

As a previous poster mentioned, you are going to have a lot of overhead with tunneling PPTP through SSH.  SSH already encrypts the entire link . . . so you do NOT need to tunnel another encryption mechanism (z.b. VPN) within the SSH connection.

To clarify, PuTTy runs on top of SSH.  PLink is the Windoze command line version (same author) so you can create connections from command files versus starting up PuTTy each time you want an SSH connection.

Tunnel through SSH using the examples you are finding.  You WILL have a secure connection, as strong as a connection like SSL ... just make sure you are only using SSH version 2.  Edit your Linux 'sshd_config' file and make sure protocol line looks like this:
[FONT=Courier New][COLOR=Blue]Protocol 2[/COLOR][/FONT]

MJ

---

### Post by frenchn00b on 2009-11-22
> **mojorisinagain said:**
> The VNC example is very good.  If accessing your Linux box through VNC gets you what you need, then implement.

As a previous poster mentioned, you are going to have a lot of overhead with tunneling PPTP through SSH.  SSH already encrypts the entire link . . . so you do NOT need to tunnel another encryption mechanism (z.b. VPN) within the SSH connection.

To clarify, PuTTy runs on top of SSH.  PLink is the Windoze command line version (same author) so you can create connections from command files versus starting up PuTTy each time you want an SSH connection.

Tunnel through SSH using the examples you are finding.  You WILL have a secure connection, as strong as a connection like SSL ... just make sure you are only using SSH version 2.  Edit your Linux 'sshd_config' file and make sure protocol line looks like this:
[FONT=Courier New][COLOR=Blue]Protocol 2[/COLOR][/FONT]

MJ

wow cool
but you know I am not sure it works. 
 
The problem is that I cannot check or try it, I need to be outside the network here. I havent internet other where, just when I am travelling (not today). :( 

i shall be simpel, if someone want to try if he has internet: 
```
apt-get install pptp  ssh
``` on the server
  
take a pc, and get internet by your neighbour:
run XP microsoft
download putty:
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)
then put your server IP and the port 22
then 
into the config of putty, select : 
forward port: 
```
L 1723   localhost
```
and shall it work??

which user login/password shall I use? the same as the login of the linux box?

[COLOR="Red"][B]WHY NOT TO USE IT?
[http://poptop.sourceforge.net/dox/protocol-security.phtml](http://poptop.sourceforge.net/dox/protocol-security.phtml)[/B][/COLOR]
[http://pigtail.net/nicholas/pptp/](http://pigtail.net/nicholas/pptp/)

---

### Post by frenchn00b on 2009-11-22
error

I added the ip to /etc/pptp.conf
and put the password into /etc/ppp/chap something
```
frenchn00b * secret
```

```
Nov 22 20:17:48 frenchn00b pptpd[9239]: CTRL: Client 10.1.1.4 control connection started
Nov 22 20:17:48 frenchn00b pptpd[9239]: CTRL: Starting call (launching pppd, opening GRE)
Nov 22 20:17:48 frenchn00b pppd[9240]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Nov 22 20:17:48 frenchn00b pppd[9240]: The remote system is required to authenticate itself
Nov 22 20:17:48 frenchn00b pppd[9240]: but I couldn't find any suitable secret (password) for it to use to do so.
Nov 22 20:17:48 frenchn00b pppd[9240]: (None of the available passwords would let it use an IP address.)
Nov 22 20:17:48 frenchn00b pptpd[9239]: GRE: read(fd=6,buffer=8058640,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Nov 22 20:17:48 frenchn00b pptpd[9239]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Nov 22 20:17:48 frenchn00b pptpd[9239]: CTRL: Reaping child PPP[9240]
Nov 22 20:17:48 frenchn00b pptpd[9239]: CTRL: Client 10.1.1.4 control connection finished

```

why it isnt working?

---

### Post by frenchn00b on 2009-11-22
Ok I found :

I shall have in chap:
cat /etc/ppp/chap-secrets
```
# Secrets for authentication using CHAP
# client        server  secret                  IP addresses
frenchn00b     *     secret       ** * **
```

The pptp is listening and on the firewall the port 1723 is blocked. So the only way is tunneling on SSH port 22;)

**But the guy told me that GRE CANNOT be tunneled through SSH **




How to install it for having a VPN PPTP for WINDOWS XP:
(1) apt-get install pptpd
(2) add this to  /etc/pptpd.conf
> debug  
localip 10.1.1.2 
remoteip 10.10.1.10-20,10.1.1.245

(3) echo "username    *     secretpassword   * "  >> /etc/ppp/pap-secrets

---

### Post by frenchn00b on 2009-11-24
here we go : 

```
Your proposal is **impractical**, since GRE packets cannot be forwarded over
an SSH connection.
```

---

