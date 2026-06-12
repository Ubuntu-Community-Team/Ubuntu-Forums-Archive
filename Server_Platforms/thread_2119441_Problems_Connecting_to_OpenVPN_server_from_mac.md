---
title: "Problems Connecting to OpenVPN server from mac"
date: 2013-02-23
forum: Server Platforms
---

### Post by eyced on 2013-02-23
Hi there, 

Firstly, sorry if this is in the wrong section. I don't usually post, anyway. 

I finally got around to installing and configuring OpenVPN on my Ubuntu 12.04.2 home server using the tut on help.ubuntu.com and I'm attempting to connect to it via TunnelBlick from my mac.  After setting up the config files and trying to connect I get this error message: "Tunnelblick was unable to start OpenVPN to connect AlexHomeVPN. For details, see the OpenVPN log in the VPN Details&#8230; window"

I've tried a few different things and I really don't know what else to do.  

I've attached the OpenVPN config file from the server side and the tunnelblick client side config file. I removed my IP though for obvious reasons. 

The one thing I'm not sure on is what IP I should put in for the client config file? I didn't use the local. I just used the same one I use to ssh into the machine.  

If you guys need any more files or readouts then just let me know. Thanks a lot.

Also, this is the error log from tunnelblick
2013-02-23 21:19:24 *Tunnelblick: OS X 10.8.2; Tunnelblick 3.3beta21b (build 3114.3185)
2013-02-23 21:19:24 *Tunnelblick: Attempting connection with AlexHomeVPN; Set nameserver = 1; monitoring connection
2013-02-23 21:19:24 *Tunnelblick: /Applications/Tunnelblick.app/Contents/Resources/openvpnstart start AlexHomeVPN.tblk 1337 1 0 0 0 49 -atADGNWradsgnw 
2013-02-23 21:19:24 *Tunnelblick:

Could not start OpenVPN (openvpnstart returned with status #242)

Contents of the openvpnstart log:

     OpenVPN returned with status 1, errno = 2:
          No such file or directory
     
     Command used to start OpenVPN (one argument per displayed line):
     
          /Applications/Tunnelblick.app/Contents/Resources/openvpn/openvpn-2.3-alpha1/openvpn
          --cd
          /Users/me/Library/Application Support/Tunnelblick/Configurations/AlexHomeVPN.tblk/Contents/Resources
          --daemon
          --management
          127.0.0.1
          1337
          --config
          /Users/me/Library/Application Support/Tunnelblick/Configurations/AlexHomeVPN.tblk/Contents/Resources/config.ovpn
          --log
          /Library/Application Support/Tunnelblick/Logs/-SUsers-Sme-SLibrary-SApplication Support-STunnelblick-SConfigurations-SAlexHomeVPN.tblk-SContents-SResources-Sconfig.ovpn.1_0_0_0_49.1337.openvpn.log
          --management-query-passwords
          --management-hold
          --script-security
          2
          --up
          /Applications/Tunnelblick.app/Contents/Resources/client.up.tunnelblick.sh -m -w -d -atADGNWradsgnw
          --down
          /Applications/Tunnelblick.app/Contents/Resources/client.down.tunnelblick.sh -m -w -d -atADGNWradsgnw
          --up-restart
          --route-pre-down
          /Applications/Tunnelblick.app/Contents/Resources/client.route-pre-down.tunnelblick.sh -m -w -d -atADGNWradsgnw
     
     Contents of the OpenVPN log:
     
          
     More details may be in the Console Log's "All Messages"

---

### Post by ahallubuntu on 2013-02-23
~

---

### Post by Bucky Ball on 2013-02-23
*Thread moved to **Server Platforms**.*

---

### Post by eyced on 2013-02-23
> **ahallubuntu said:**
> I have an OpenVPN server setup with Ubuntu 10.04 LTS and I have users connecting to it routinely with Tunnelblick, without issues.  So I know in concept it works fine.

My server isn't 12.04 though.  I suspect it shouldn't make that much of a difference.

I suspect the problem is on the client side, though.  The fact that you are getting a "No such file or directory" message there generally means a file is misplaced or something of that nature.

Double check all references to files in "/Users/me/Desktop" referenced in your Tunnelblick/client config file; make sure they all exist.

Can I assume you've downloaded and used the correct version of Tunnelblick?  There are different recommended versions depending on your Mac OS X version.  When you are downloading Tunnelblick, there  should be notations on which version is recommended for which version of OS X.  I think the latest version of OS X needs the beta version of Tunnelblick.

As far as the IP: yes, you'd use your public IP, the same one you'd use to connect via ssh.  But you must forward a port (probably 1194) through your firewall to the Ubuntu server, the same way you forward (probably) port 22 to it.

All of the paths point to the correct files. 
My lynksys router is glitched out in that it won't allow me to make changes to the single port forwarding section, so I opened a range of ports from 1193 to 1194.

---

### Post by d4m1r on 2013-02-25
What model of router do you have exactly? What kind of internet connection do you have?

Do you see any errors in the OpenVPN logs on the server? Does it even see you trying to make a connection?

---

