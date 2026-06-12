---
title: "Server to server decent into madness"
date: 2020-12-16
forum: Server Platforms
---

### Post by carterk on 2020-12-16
Hi all, first post here. Very new to Linux and am having a hell of a time trying to set up two Pi's to run an OpenVPN and Cert Authority on 20.04 headless servers. Here's the setup:

Raspberry Pi 4: 20.04 headless server, OpenVPN, SSH with key authentication to my desktop working no probs
Raspberry Pi 3B: 20.04 headless server, easy-rsa Certificate Authority, SSH with key authentication also to my desktop no probs

I'm following DigitalOceans generally excellent guides on the subject *[https://www.digitalocean.com/community/tutorials/how-to-set-up-and-configure-an-openvpn-server-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-and-configure-an-openvpn-server-on-ubuntu-20-04)* and have reached the point **&#8203;(Step 4)** where I need to send a Certificate Signing Request from the VPN to the CA but this is where I'm stuck.
Using the intermediary PC with SSH and attempting to copy over with *scp* I get *Permission denied (publickey)*, which I assume is because I haven't set up SSH between the two servers. Fair enough. But now when trying to control my servers locally with a keyboard and monitor to do this I find I have no HDMI display on either of them.

Does a headless server setup mean you can only ever access it remotely? Should I have set SSH key authentication between the servers first? I am going about it all completely wrong and am pointlessly wasting weekends and evenings on an endeavour that was doomed from the start?

Any input would be much appreciated!

---

### Post by howefield on 2020-12-16
Thread moved to the "*Server Platforms*" forum.

---

### Post by darkod on 2020-12-16
Which is the exact command where it gives you the error?
```
scp /home/sammy/easy-rsa/pki/reqs/server.req sammy@your_ca_server_ip:/tmp
```

That one?

And I didn't understand the part about intermediary PC. Use your PC to open ssh session to the VPN server. Then from within that session you are doing scp to copy over to another machine. Your PC is not intermediary in anything.

You can set up SSH keys between the servers but it is not necessary. You can always do the ssh or scp from one to another, and type the password when asked (if no ssh keys are used).

---

### Post by carterk on 2020-12-16
Cheers Darko

Yeah that command is the one giving me grief at the moment. SSH keys with passwords deactivated is working between both servers and the desktop, but this Signing Request is the first time I've attempted to have them talk between themselves. Should I have set up all the SSH comms before turning off password authentication?
And excuse my imprecise terminology sorry, still getting my head around which device is doing what at each step at the moment. I did actually attempt to use the desktop as an intermediate transfer step with PuTTY pscp but wasn't able to achieve anything that way either

---

### Post by TheFu on 2020-12-16
> Should I have set up all the SSH comms before turning off password authentication?
yes.

What is the point of putty, besides to add confusion.  The built-in ssh and ssh-server are extremely user friendly. Same for scp, sftp ... or just us any Linux file manager with sftp:// in the URL if you want to drag-n-drop.  Why make things hard?  Putty isn't useful on Linux platforms, IMHO.

ssh is completely separate from any VPN needs.  Most openVPN servers use self-signed certs, so their isn't any need to do a CA request. The fact that the same CA creates the server AND the client certs AND they are self-signed is really added security. If the cert on either side is altered, neither will work. That's good in a VPN.

---

### Post by The Cog on 2020-12-16
I often find that if you boot a pi without the hdmi plugged in, then plugging the hdmi in later doesn't work. You need to reboot with the hdmi plugged in. 
Once you have things set up this doesn't matter too much because you manage remotely. But it is a pain when remote access breaks for some reason.

---

### Post by carterk on 2020-12-17
Thanks for the feedback guys

TheFu
Regarding PuTTY, i was simply casting around for things that might work and followed random internet advice that seemed relevant. I have no idea what the difference is between it or scp is really. When a topic is as foreign and abstract as this one to a new player it's difficult to even ask the right question or know what to look for. 
And for OpenVPN, in DigitalOceans instructions they make mention of this:
> [COLOR=#323232][FONT=Sailec-Bold]Note:[/FONT][/COLOR][COLOR=#323232][FONT=Sailec-Regular] While it is technically possible to use your OpenVPN Server or your local machine as your CA, this is not recommended as it opens up your VPN to some security vulnerabilities. Per [/FONT][/COLOR][the official OpenVPN documentation]("https://openvpn.net/index.php/open-source/documentation/")[COLOR=#323232][FONT=Sailec-Regular], you should place your CA on a standalone machine that&#8217;s dedicated to importing and signing certificate requests. For this reason, this guide assumes that your CA is on a separate Ubuntu 20.04 server that also has a non-root user with sudo privileges and a basic firewall enabled.[/FONT][/COLOR] [https://www.digitalocean.com/community/tutorials/how-to-set-up-and-configure-a-certificate-authority-ca-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-and-configure-a-certificate-authority-ca-on-ubuntu-20-04)
Are they envisioning a different use case to what you're thinking or are there just multiple valid ways to set this up?

I'm happy to report I've got passed my current roadblock. Turns out my SSH credentials weren't being passed through while using scp in Windows cmd. Powershell didn't seem to want to add them either, but GIT bash allowed me to run [COLOR=#000000][FONT=Consolas]eval[/FONT][FONT=Consolas] [/FONT][FONT=Consolas]$(ssh-agent) ,[/FONT][/COLOR] then ssh-add , and then log in using [FONT=Consolas]ssh[/FONT][FONT=Consolas] -A. [/FONT]I'm sure this was a super obvious answer to most but for me at this point any deviation to the steps of a tutorial results in hours or days of side questing for answers, haha.

Is there any reason to be using cmd or is Git Bash generally better? And if so why should that be?

---

### Post by TheFu on 2020-12-17
Windows people think "putty" when ever ssh is talked about.  They don't know better.  Win10 has a native ssh client and there is WSL which is just like normal Linux for ssh stuff.  The native Win10 ssh lets us create ssh-keys using exactly the same commands and options as Linux.  That's for connections FROM Windows TO Linux/Unix.  I've helped other people set that up and we didn't see any differences, except that ssh-copy-id doesn't exist on Windows, so doing what it does manually is needed. I don't know if WSL has ssh-copy-id or not.

There are lots of ways to setup OpenVPN. It supports thousands of different configurations to address the needs for trivial setups or extremely complex setups and everything in between.  Everyone tries to use the non-defaults which usually just causes issues for people who don't understand as completely as needed VPNs, CAs, and routing.

I don't use Windows much and don't have Win10, so cannot say much.  I don't know what you mean by "Git Bash" - never hear those terms used in that way, together.  Bash is a shell for Unix systems.  git is a version control tool used by all systems.  If you are in a terminal on any Unix system, it is pretty likely to be using bash as the shell, but there are 40 other shells which can be used.  Some people use csh, tcsh, zsh, fish, psh, ksh - based on personal preference. I used tcsh for about a decade and csh before that, before I bothered even trying to use bash.

For me, the hassles of using Windows to connect with and Unix/Linux makes something to avoid.  When I did use Windows more, for transferring files, I used WinSCP (without keys) or I'd boot a small Linux distro with a minimal X/Windows Server inside a virtual machine and use that. Once you are used to X/11 select/paste and using the transfer tools.

On Windows inside WSL, you can just follow the normal Unix ssh-key setup stuff. That is:
```
Step 1:  Run on the client as the normal user:
   $ ssh-keygen -t ed25519

Step 2:  Run from the client to the server:
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote
 The "username" is optional and not needed if the same between the
 client machine and remote server.
 "remote" can be a DNS name, IP address, some manually setup lookup
 inside the /etc/hosts or configured in the ~/.ssh/config file.

Step 3: Test that ssh works.  ssh into the remote system, 
   $ ssh username@remote
 All ssh-based connections between the client and server should now work
 just as easily.  ssh, sftp, scp, rsync, x2go, rdiff-backup, sshfs, and
  50 others regardless of the program.  Open a file manager like Caja,
 Thunar, whatever, Put sftp://username@remote/ into the URL. Hit <enter>.
 An sftp connection should happen.  Some File Managers use ssh://
 instead.
```
The ssh-copy-id setup may not work. If it doesn't, just manually append the public key onto the remote system inside the ~/.ssh/authorized_keys file.
If you don't understand how the paths between Unix and Windows relate, that will be a stumbling block.  Windows has a HOME directory for each userid, but it isn't as pronounced and the ~/ expansion doesn't work to my knowledge.  But the .ssh/ directory on Windows **is** under the userid's HOME on Windows. Key files **are** placed there.  Key files are read from that directory automatically, if the default names are used for the keys. If you change the keyfile names, then you'll need to specify that different name with every ssh-based command.  
I don't know of ~/.ssh/config is honored on Windows like it is on all Unix systems.  That config file is a key part of my ssh, scp, sftp, rsync, rdiff-backup, sshfs, x2go and all other ssh-based tool use. It allows me to setup an alias for all connection parameters to different systems so I don't need to know userids, ssh-key files, non-standard ports, IP addresses, funky hostnames, or any connection things needed like keepalive settings or when a jump-server or proxy is needed between the 2 systems.

ssh is how Unix systems are connected. It really is sad that Windows ignored this capability for decades.  ssh is one of the few solutions that is both more convenient AND more secure when used.

---

