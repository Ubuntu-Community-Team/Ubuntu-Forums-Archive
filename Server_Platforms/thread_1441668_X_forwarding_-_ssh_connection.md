---
title: "X forwarding - ssh connection"
date: 2010-03-29
forum: Server Platforms
---

### Post by satimis on 2010-03-29
Hi folks,

host - ubuntu 9.10 desktop
virtualizer - VirtualBox


What will be the easiest way to ssh connect a VM on VirtualBox, exporting its desktop to host, while it is already running ?


I found;
Howto Access via ssh a Virtualbox Guest machine.
August 12, 2007 | 0:03
[http://mydebian.blogdns.org/?p=148](http://mydebian.blogdns.org/?p=148)
Ben Chapman  | March 27, 2009 | 22:14 

Dimas  | April 29, 2009 | 17:06 

and
How To: set up ssh through NAT to a VirtualBox instance
[http://greybeardedgeek.net/?p=138](http://greybeardedgeek.net/?p=138)


They need to restart VM.

TIA

B.R.
satimis

---

### Post by HermanAB on 2010-03-29
Ensure that ssh-server is installed and that sshd is running on the VM.

Connect like this:
$ ssh -X -C -c blowfish user@ipaddress "gedit /etc/fstab"

or if you want to go click happy:
$ ssh -X -C -c blowfish user@ipaddress "gnome-panel"
then put the remote panel on the side of your local desktop to reduce confusion.

---

### Post by satimis on 2010-03-29
> **HermanAB said:**
> Ensure that ssh-server is installed and that sshd is running on the VM.

Connect like this:
$ ssh -X -C -c blowfish user@ipaddress "gedit /etc/fstab"


Hi HermanAB

Thanks for your advice.  This command works here.


> 
or if you want to go click happy:
$ ssh -X -C -c blowfish user@ipaddress "gnome-panel"


This command fails.


$ ssh -X -C -c blowfish satimischser@192.168.0.202 "gnome-panel"
satimischser@192.168.0.202's password: ```

** (gnome-panel:2663): DEBUG: Adding applet 0.
** (gnome-panel:2663): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:2663): DEBUG: Adding applet 1.
** (gnome-panel:2663): DEBUG: Adding applet 2.
** (gnome-panel:2663): DEBUG: Adding applet 3.
** (gnome-panel:2663): DEBUG: Adding applet 4.
** (gnome-panel:2663): DEBUG: Adding applet 5.
** (gnome-panel:2663): DEBUG: Adding applet 6.
** (gnome-panel:2663): DEBUG: Adding applet 7.
** Message: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

** (gnome-panel:2663): WARNING **: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

** (gnome-panel:2663): WARNING **: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name
** (gnome-panel:2663): DEBUG: Adding applet 8.
** (gnome-panel:2663): DEBUG: Adding applet 9.
[/quote]

Please advise how to fix this problem.  TIA


Edit:

Following command can start remote xterm on host[code]

$ ssh -XfC -c blowfish satimischser@192.168.0.202 xterm


```


satimis

---

### Post by joachi on 2010-06-21
I have tried everything to no avail. This used to work in both 9.04 and 9.10 and now after the upgrade I cannot open a remote xterm period! Here is the debug stuff that comes out:

debug1: Authentications that can continue: gssapi-keyex,gssapi-with-mic,publickey,password,keyboard-interactive
debug1: Next authentication method: gssapi-keyex
debug1: No valid Key exchange context
debug1: Next authentication method: gssapi-with-mic
debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1133' not found

debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1133' not found

debug1: Unspecified GSS failure.  Minor code may provide more information


debug1: Next authentication method: publickey
debug1: Trying private key: /home/dj/.ssh/identity
debug1: Trying private key: /home/dj/.ssh/id_rsa
debug1: Trying private key: /home/dj/.ssh/id_dsa
debug1: Next authentication method: keyboard-interactive
Password: 
debug1: Authentication succeeded (keyboard-interactive).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Requesting X11 forwarding with authentication spoofing.
debug1: Sending environment.
debug1: Sending env LANG = en_US
debug1: Sending command: xterm
debug1: Remote: Channel 0 set: LANG=en_US
Illegal variable name.
xterm Xt error: Can't open display: 
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: channel 0: free: client-session, nchannels 1
Transferred: sent 1392, received 1424 bytes, in 0.2 seconds
Bytes per second: sent 6001.1, received 6139.0
debug1: Exit status 1
debug1: compress outgoing: raw data 315, compressed 249, factor 0.79
debug1: compress incoming: raw data 311, compressed 263, factor 0.85

can someone please help?

---

### Post by joachi on 2010-06-21
Sorry about replying to my own post. I have figured out that the ssh -X etc. does not seem to be working for Solaris based systems. Works fine with Linux servers.

---

