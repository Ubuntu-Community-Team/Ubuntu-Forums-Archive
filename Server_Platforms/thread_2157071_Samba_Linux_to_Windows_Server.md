---
title: "Samba Linux to Windows Server?"
date: 2013-06-24
forum: Server Platforms
---

### Post by Zowskaz on 2013-06-24
Hello,

     I me and my friend would like to setup a private server for sharing files. We would like the Host for the server to be a linux computer running Samba.
 The client computers would be a mix of linux and Windows computers. I have never made a server before and it would be nice to have some help of how to create this server.
Another question I have is it possible to create a Windows/Linux Samba server that can share files outside of a LAN network. We are planning on setting it up at my friends house 
who doesn't has the same network. Would this be possible to di. And if so could you point me in the right direction to get started setting it up?

Also I've heard OpenSSH is encrypted in secure would I be able to use this is the Samba network. I would like the server to be private.

---

### Post by TheFu on 2013-06-24
If you and your friend are NOT on the same subnet, using samba is a bad idea. It is not secure and most ISPs will block the ports it uses as a way to protect their end-users from themselves.

The best recommendation that I have is to use ssh-based protocols and key-based authentication for your "darknet."  With just a few people involved, **ssh**, scp, **sftp** and sshfs are viable solutions.  Heck, even **rsync** works over ssh, so you can each mirror directories more like a peer-to-peer setup - your own "dropbox", if you will.

Basically, you'll need to setup an ssh-server on both system, then learn how to access the other sides' IP (used to be there were free Dynamic DNS solutions), open the ssh port on the router so it will access remote requests, and login.   This [http://www.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://www.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) should get you started.

If you don't control the router, then you are screwed. At least 1 side of the network will need an open port to allow incoming ssh connections.  I would highly recommend against using the standard port, 22.  Use any other non-standard port and internet attacks will drop to almost zero. If you leave it on port 22, you'll see thousands of attempts every day - most from China, Russia, India, Ukraine, .... you get the idea.

ssh is one of those tools that makes remote connections more secure AND easier than other methods. That doesn't happen too often.

Good luck! AND have fun with this!

---

### Post by Lars Noodén on 2013-06-24
Just to highlight [sshfs](https://help.ubuntu.com/community/SSHFS) that TheFu mentioned, I'd add that it is *very* easy to set up and very secure.  

About Samba, if you want to access Samba over WAN, then you'll need to tighten up security by tunneling it over SSH or something like that.  Tunnelling TCP over TCP is a bit inefficient but it is necessary to wrap an insecure protocol in something secure.  We are talking about a Windows technology after all.  The good news is that you can find lots of guides about tunnelling if you want to go that route.

---

### Post by TheFu on 2013-06-24
> **Lars Noodén said:**
> Just to highlight [sshfs](https://help.ubuntu.com/community/SSHFS) that TheFu mentioned, I'd add that it is *very* easy to set up and very secure.  

About Samba, if you want to access Samba over WAN, then you'll need to tighten up security by tunneling it over SSH or something like that.  Tunnelling TCP over TCP is a bit inefficient but it is necessary to wrap an insecure protocol in something secure.  We are talking about a Windows technology after all.  The good news is that you can find lots of guides about tunnelling if you want to go that route.

Lars is correct ... and since he and I seem to have similar interests, we often post in the same threads here with slightly different information. He's earned my respect.

Now that I come back, I can see where nobody really left enough details for a solution. I'll try to do better below.

* On the ssh-servers, you **need** to force them have static IP addresses on the LAN. That can be accompished many different ways, but the easiest is just to set it on each machine.  Something like 192.168.1.5 - it needs to be outside the DHCP range.  You can also tell some routers to always give the same MAC address (every network card is unique in the world) a specific IP every time it uses DHCP. Not all routers support this feature, but if yours does, it can be much easier. [http://www.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://www.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) tried to explain.  Google "dhcp reservation" for more info.  Without static IPs, you are stuck.

* setup ssh servers on 1 or both systems. This is a good idea even if you just need to access the machine inside your home - I hate having to walk upstairs to do something minor, ssh saves the walk.  On the server, leave the ssh-server listening on the default port, 22.  I do this so it is clear when I'm testing if I'm attempting to connect to the inside IP/port or the public IP/port.

* modify the router settings on 1 or both networks to open some high port, perhaps 54022?, then setup port forwarding from the public 54022 port to an internal, static IP (where the ssh-server runs) and port 22.  This is called "port translation" - if you need to google for a how-to.

* On each system running ssh-server, install **fail2ban**. This is a security tool and should stop 99.9999% of the attacks.

* Test the ssh connections using any ssh client you have.  There are 50 of them and some available for pretty much **any** platform.  On Windows, Putty is the most used and probably the easiest. Once ssh works, then scp, sftp and sshfs all work. On MS-Windows, the best sftp client that I know is WinSCP, but I think filezilla also works. This is how you transfer files using userids and password.  

* That can be a hassle, so you probably want to setup key-based authentication.  On the client, using the account you plan to remote into the server from, generate ssh keys with **ssh-keygen**.   Next, you need to push the public keys to the ssh-server under your account. There is another program, **ssh-copy-id**, that handles that aspect.  You'll be prompted for the userid/password so the file(s) can be copied.  Disconnect from the remote host and ssh to it again. This time and all future times, you will not be prompted for the password on the remote system. Don't forget that you probably need to specify the remote port like this: **  ssh -p 54022 -u userid {remote-server or IP}**
More options for ssh are available - **man ssh** explains them all.  Also, the keygen and copy-id commands are Linux/UNIX only. I don't know how to do this on Windows, but it must be possible. Google is your friend.

* As you setup more and more of these remote connections, it is hard to keep track of the ports, userids, and servers.  ssh has a configuration text file to let you setup aliases for every remote system. It is in ~/.ssh/config and almost every program that uses ssh for the transport honors this file.  That means if you put the high-port for remote-server in the config file, you'll never need to specify it again for ssh, scp, sftp or even rsync or most backup programs that use ssh to protect the network transmissions (rdiff-backup).

After you setup ssh and get sftp working, I hope you'll avoid trying to get samba working over the WAN.  It is possible, but most people that do that will deploy a full VPN, like OpenVPN, and will not try to do it over ssh.  Compared to setting up OpenVPN, ssh is 50x easier.  Both have fairly wide platform support and if your main client machines are going to be Android, OpenVPN is probably the better choice, though you'll still want an ssh port open - ssh is just do handy when a VPN isn't working.

Anyway, if you have any questions, please ask.

---

