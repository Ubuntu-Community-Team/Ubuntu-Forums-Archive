---
title: "How I used SSH to &quot;Put it to the man&quot;"
date: 2007-09-06
forum: Server Platforms
---

### Post by Warren Watts on 2007-09-06
My workplace recently restricted Internet access via a highly restrictive firewall.  My answer, I tunnel thru SSH!

After poking around, I discovered that they blocked port 22 (SSH), but left port 23 (telnet) open.  Stupid on their part...

I'm not running telnet anyway, so I set up my SSH server to listen on port 23 instead.  I created a user with no rights of any kind, and restricted the user to using [Iron Bar Shell]("http://ibsh.sourceforge.net/"). 

Using Putty on the machine at work, I open an SSH connection with a dynamic proxy on the port of my choosing, then set IE to use a Socks proxy on localhost using the port of my choosing.

Voila!  Internet access thru tunneled SSH on the telnet port!

Now let's see how long it takes 'em to figger out they left port 23 open...

---

### Post by cyphur on 2007-09-06
thats amusing...

---

### Post by Dr Small on 2007-09-06
I've tested this same method before. It works. 
If they block port 23, just use 443 :p

Dr Small

---

### Post by HermanAB on 2007-09-07
Hmm, you can even use port 80.  Nobody ever blocks that one.  Wonder why - it sure will reduce problems a lot if everyone blocks port 80... :)

---

### Post by Brazen on 2007-09-07
> **HermanAB said:**
> Hmm, you can even use port 80.  Nobody ever blocks that one.  Wonder why - it sure will reduce problems a lot if everyone blocks port 80... :)

Pretty sure the main problem for the OP is that port 80 is blocked, which means port 443 is probably blocked, too.

---

### Post by ssam on 2007-09-07
thanks for pointing out iron bar shell.

i recently found rssh [http://pizzashack.org/rssh/](http://pizzashack.org/rssh/)

is there a good list somewhere for all the various restricted shells for various tasks.

---

### Post by D-EJ915 on 2007-09-08
Just get your daemon to listen to something random and nobody'll ever block it.  That's what I do with some of my "services"

---

### Post by bodhi.zazen on 2007-09-08
You can use Putty or Cygwin on windows.

Winscp is also available if you want to transfer files. Winscp uses putty keys (again you can import your open ssh key).

If you use Putty and keys on the server you can import your open ssh keys like this : [http://linux-sxs.org/networking/openssh.putty.html](http://linux-sxs.org/networking/openssh.putty.html)

If you use Cygwin, install the openssh package.

Cygwin is a command line and allows a number of options :

ssh -fCNT user@<server_IP> -L 5901:127.0.0.1:5901

>  -f = Allows ssh to close after the connection is established.
 -C = Use Compression
 -N = No commands will be issued
 -T = No terminal session will be started
 
 -L = Port forwarding. The terminology is <server_port>:<client_port> the trick is we are using 127.0.0.1:<port> for the client. 127.0.0.1 must be used (not localhost or the client ip address)

If you use that ssh command with the options listed, you open a port without opening a shell :twisted:

The above ssh command forwards 5901, allowing VNC over ssh

[uwiki]SSHHowto[/uwiki]

_**Note**_: Opening a port in this way can have serious consequences including termination of employment, depending on your employer's policies. This information was posted with the assumption such activity has been discussed with your IT department and is allowed.

---

