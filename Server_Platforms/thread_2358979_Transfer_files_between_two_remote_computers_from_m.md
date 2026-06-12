---
title: "Transfer files between two remote computers from my local machine."
date: 2017-04-19
forum: Server Platforms
---

### Post by biggyk on 2017-04-19
So I rent a seedbox (remote file server) that runs linux and I use ssh on my windows desktop along with lftp to grab the files off the seedbox to my local media server (ubuntu server) and it works well.

My issue I have is I have another remote machine (windows 10) that I want to transfer files from the seedbox to. Currently Im having to remote desktop into that machine then then just filezilla to transfer. Its a pain as sometimes I end up kicking off the user that may be currently using that machine. Is there a simpler non intrusive way to use ftp between the linux seedbox and that remote windows 10 machine? I managed to install openssh on the win10 machine but havent had any luck getting ftp to work.

---

### Post by TheFu on 2017-04-19
FTP is not sftp. You want SFTP for security reasons.  Plain FTP should have died out in 1994-ish and been forgotten just like telnet.  "Don't use plain FTP" anymore.

Would be helpful to know where each system is network-wise in relationship to each other.  I'm assuming they are all on different LANs and only connect via ssh/vpn over the internet.

openssh has a client and a server. The server provides ssh, scp, and sftp services over the same port, usually port 22/tcp. I don't think the server is considered secure when running on Windows. For the client, most people just use putty on Windows (I hear).  I move files from Linux to Windows 2-times a day, but this is on the same LAN. I've automated it using the Windows Schedule app and teracopy in a perl script.  You could automate it with Windows Schedule and the putty tool - pscp.exe.  Don't know how to secure that, sorry. In my automation, no windows popup, so it shouldn't impact any other currently logged in userid beyond sucking bandwidth.  I do my file moves after 11pm and again around 5am.  This seldom impacts anyone, but the machine is left on 24/7.

Windows will have a proper ssh server that supports sftp/scp/rsync. Someday. We've been waiting since the mid-1990s, so I won't hold my breadth.  Plus it might support ssh-keys for authentication, so passwords (which are inherently non-secure) aren't used.  Until that happens, I think you can only "pull" from the Windows machine were you want the files.

Ok - if we think in crazy ways - ways that might be worse than the current problem, but 

You might want to use storage networking to place the files on the machine you want. You'd need to handle any security yourself, since Windows shares are NOT secure. Most people would use a full VPN like openvpn for this.

You might want to look at getting rsync to work with pscp. Then you could use hardlinks on the remote linux system for any files you want the Win10 box to use. rsync completely rocks.

You might want to suggest they run a tiny Linux version inside a virtual machine and give that VM access to the local storage.  I did this with my Mom's setup years ago, before she switched to Linux full time.

You might want to setup a Plex Server and provide them with access via their plex accounts to your system(s). Then they could stream the media files directly, at the expense of your bandwidth.

I bet there are a few other options to be considered. Hopefully, someone else will make a suggestion.

---

### Post by cmcanulty on 2017-04-19
I log in remotely through a xubuntu 16.04 then transfer remote files internally with windows explorer network locations to windows 10 and xubuntu by just copy and paste. It is all inside a LAN except my initial access via Xubuntu

---

