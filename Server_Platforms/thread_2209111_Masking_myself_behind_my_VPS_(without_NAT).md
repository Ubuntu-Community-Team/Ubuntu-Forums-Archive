---
title: "Masking myself behind my VPS (without NAT)"
date: 2014-03-04
forum: Server Platforms
---

### Post by cylent on 2014-03-04
[COLOR=#333333][FONT=sans-serif]Please help me get this working.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]I have  a VPS running Arch (while i finish my testing).
This VPS has one ether adapter ... its a VM  box running on VMware virtualization. Ok so it works and there's no issues.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]What I want to do: on my home PC i want to connect to the VPS and i'd like to think I am asking about bridging because essentially I want my PC to mask itself in the IP of the VPS.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]I am trying to stay away from DHCP and NAT.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]My brain is not coming up with a solution on[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]But then how would I connect to the VPS? i guess SSH tunneling? but thats limited. how do i make my whole windows pc proxy through that? only a browser and some program will accept a proxy config. (again without nat'ing)[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]Should I ask for another IP/ether port on my VPS, vpn into that and then output from the second adapter? But then again I am trying to stay away from NAT/DHCP and even worse openvpn which will slow me dramatically with this "encryption" ...[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]So... is what i am asking for do'able?
Please help![/FONT][/COLOR]

---

### Post by nerdtron on 2014-03-04
>  [COLOR=#333333][FONT=sans-serif]VM  box running on VMware virtualization 
There should be a setting to set the network interface "Bridge" adapter instead of nat.
In VirtualBox you can do this on the VM settings network section before you boot the VM. Using Bridge mode will make the IP address of the VM the same as the LAN IP address of where the host is. It should have an IP the same as the IP of your local network. You can then ssh directly to it once it boots.
[/FONT][/COLOR]

---

### Post by cylent on 2014-03-04
interesting.

I am not aware of such option though. I'll log into the Vsphere client to see if i have such option.

I am logging into the VPS via a public IP though. Does this still apply?

In bridge mode set (if so) I will have to login to the VPS via my internet connection. How do i change things to become the VPS connection? I am rather confused by this ...

What about the second option of adding a second ether with another public ip to the vps. logging into one and routing traffic through the other?

((See attached image))

---

