---
title: "Setting up a Proxy/VPN server"
date: 2012-10-13
forum: Server Platforms
---

### Post by gcrest on 2012-10-13
:confused:  Please i want to setup a server for  traffic redirection from my local pc. i have some networking ideas on windows.

sometimes my school blocks all tcp/ip traffic  thereby preventing me access to the internet. i have found out that other protocols are opened such as DNS,UDP e.t.c 

Can i redirect the traffic from my pc to the ubuntu server which has internet access and then redirect it back to my pc..... or is it some sort of vpn setup..

if yes how do i go about this setup

---

### Post by Lars Noodén on 2012-10-13
First get the web server set up stand alone before worrying about the networking.  You can add tunnels if needed afterward.

---

### Post by gcrest on 2012-10-13
[@ Lars Noodén]("http://ubuntuforums.org/member.php?u=168643")

I will do just that and i will get back to u ASAP

---

### Post by sandyd on 2012-10-13
**Moved to own thread**

---

### Post by volkswagner on 2012-10-13
I don't think you will need a web server if you just want the tunnel function.

What operating system is the pc at school?  Are you running FireFox web browser on the PC at school?

I have recently created a "Socks Proxy" connection for firefox and a tunnel to my Ubuntu server using Putty on the Windows client.

Here are the links that helped me accomplish this.

[Socks proxy on FireFox]("http://lifehacker.com/237227/geek-to-live--encrypt-your-web-browsing-session-with-an-ssh-socks-proxy").  [Using Putty for the tunnel creation]("http://www.dotcomunderground.com/blogs/2008/12/11/putty-ssh-tunnel-to-hide-ip/").

So the procedure to create the connection would be start Putty first to create the tunnel, then use firefox for the proxy connection.  If you don't want to use the proxy there are solution like using an alternate browser, (chrome, opera) or you will have to disable the socks proxy.  I have heard of creating profiles in Firefox for this, but I have no experience.

You may want to look into security such as ssh with keys and disable password access to ssh, plus running your ssh server on an alternate port my reduce some ssh hits to the machine.

---

### Post by hictio on 2012-10-14
> **gcrest said:**
> :confused:  Please i want to setup a server for  traffic redirection from my local pc. i have some networking ideas on windows.

sometimes my school blocks all tcp/ip traffic  thereby preventing me access to the internet. i have found out that other protocols are opened such as DNS,UDP e.t.c 

Can i redirect the traffic from my pc to the ubuntu server which has internet access and then redirect it back to my pc..... or is it some sort of vpn setup..

if yes how do i go about this setup

Are you sure you are allowed to do what you are asking here?
You should check with whoever runs the network over there, you can get into trouble.
Personally, I would use a dedicated VPN/ firewall distro, setting up a VPN server on [Endian (the community edition)](http://www.endian.com/en/community/) is a piece of cake.

---

