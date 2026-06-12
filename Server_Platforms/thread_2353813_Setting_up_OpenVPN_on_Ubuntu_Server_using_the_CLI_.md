---
title: "Setting up OpenVPN on Ubuntu Server using the CLI from Client PC."
date: 2017-02-25
forum: Server Platforms
---

### Post by daniel228 on 2017-02-25
As the title says I'm wanting to set up OpenVPN on my server and thus have the OpenVPN client software running on Ubuntu Server. I dont have direct access to the internet using this Server and need to route this connection threw my VPN. At the minute I'm using OpenVPN but I'm wanting to actually get the Server connected using the SSH threw BaSH.

I have no idea how I would copy the files over from my Client PC thats running Mint over to the actual server and the set up the OpenVPN Software on the Server using the CLI.

I have no idea were to start. I am able to log in to the server using SSH from Mint but have never tried to log in to mint from the Server using SSH. I have downloaded and installed the SSH for Mint so can work both ways from the Server and Client Mint machine.

Can anyone provide any assistance on how to copy files over an internal network, and setup OpenVPN using the CLI. I have my credentials ready but I'm stifled on how to manually select a .cert for the OpenVPN setup.

Anyone who replies. Thank you in advance and if any one can provide even just and idea on how to go about this again thank you.

---

### Post by bearlake on 2017-02-25
Hi, 

Running a headless server here and installed my VPN from the client to the server a few times now.

I tried a few of them, the links are below.

[https://github.com/Angristan/OpenVPN-install/blob/master/README.md](https://github.com/Angristan/OpenVPN-install/blob/master/README.md)

[https://github.com/Nyr/openvpn-install](https://github.com/Nyr/openvpn-install)

---

### Post by daniel228 on 2017-02-25
> **bearlake said:**
> Hi, 

Running a headless server here and installed my VPN from the client to the server a few times now.

I tried a few of them, the links are below.

[https://github.com/Angristan/OpenVPN-install/blob/master/README.md](https://github.com/Angristan/OpenVPN-install/blob/master/README.md)

[https://github.com/Nyr/openvpn-install](https://github.com/Nyr/openvpn-install)


I dont have direct access to the internet using this server. I need to set up the OpenVPN on the server first, configure it and then route the internet connection threw it.

Does Ubuntu come installed with OpenVPN or does it have to be downloaded. If it does, I'm gonna have to wait.

---

### Post by bearlake on 2017-02-25
I had to install OpenVPN to the server.

---

### Post by darkod on 2017-02-26
Usually it is complicated to install any packages/application without internet on the machine. That is because apt-get automatically installs all depending related packages. When installing by hand, you have to do that.

But I'm confused about something. To connect to VPN the machine still has to have internet access. So can't you temporarily add some route or something that allows you to use apt-get to install the openvpn package?

Or the VPN connection will be inside a LAN, without going over the internet at all?

You never mentioned which ubuntu version you have. Lets say you have 16.04. The openvpn package for manual download is here:
[http://packages.ubuntu.com/xenial/openvpn](http://packages.ubuntu.com/xenial/openvpn)

As you can see, it depends on a number of packages (marked with red dot) so I think you will have to download each of them. And then check for those packages if they depend on other packages...

Here you can search for any package for any uubntu version that is still supported:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

But I would find a way to enable internet on the machine and use apt-get. Even on a LAN with complex design there are many ways to get internet to a specific machine.

---

