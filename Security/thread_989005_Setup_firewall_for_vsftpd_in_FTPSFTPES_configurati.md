---
title: "Setup firewall for vsftpd in FTPS/FTPES configuration"
date: 2008-11-21
forum: Security
---

### Post by HiranChaudhuri on 2008-11-21
I managed to setup vsftpd to allow filezilla connecting via FTPES and download files on the LAN.
Now when I connect to the very same server from the internet, I get a control connection but not the data connection.

How do I setup the firewall, or the vsftpd to allow this?
(note: the firewall is already configured so that FTP went through)

---

### Post by stmurray on 2008-11-21
FTP is a pain in the neck for firewalls.  The problem is that the the ftp client opens a "server" port for data connections, meaning the server connects back to the client on that (random) port.  For a filewall that means:

1) Using a statefull firewall that has the smarts enough to know that when an outgoing ftp (control) connection is open, to allow the external ftp server to connect back to the client for the data connection(s)
2) Open all ports > 1024 for the server to connect to the client (probably opening the firewall more than you want to)

Another solution is use the ftp in "passive" mode.  In passive mode, the server opens the ports for the data connection and the client connects out to those. You have to make sure your clients can connect to the server on to all ports > 1024 (as well as port 21 for the control connection), but that is much better than allowing the remote server to connect to your workstations.  This, in my opinion, is the much better solution if both the server and client support passive mode.  It usually just means a setting  on the client when you open the connection.  (for ftp command line, you use the -p flag)

---

### Post by benanzo on 2008-11-21
To my knowledge, it's not possible to use iptables' ip_conntrack_ftp with FTPS since it will never see the PORT command, and therefore never know which port to open.  So suggestion #1 about using stateful inspection will likely not work.

---

