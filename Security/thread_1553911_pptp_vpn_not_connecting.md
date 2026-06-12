---
title: "pptp vpn not connecting"
date: 2010-08-15
forum: Security
---

### Post by dogdo on 2010-08-15
Im using 10.04 with network manager applet. This is the output i get-

Aug 16 02:17:35 daddy-laptop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Aug 16 02:17:35 daddy-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 2249
Aug 16 02:17:35 daddy-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Aug 16 02:17:35 daddy-laptop NetworkManager: <info>  VPN plugin state changed: 1
Aug 16 02:17:35 daddy-laptop NetworkManager: <info>  VPN plugin state changed: 3
Aug 16 02:17:35 daddy-laptop NetworkManager: <info>  VPN connection 'VPN connection 1' (Connect) reply received.
Aug 16 02:17:35 daddy-laptop NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'VPN connection 1' failed to connect: 'invalid gateway 'gateway''.
Aug 16 02:17:35 daddy-laptop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Aug 16 02:17:35 daddy-laptop NetworkManager: <info>  Policy set 'Auto myhomenetwork ' (eth1) as default for routing and DNS.
Aug 16 02:17:48 daddy-laptop NetworkManager: <debug> [1281921468.002458] ensure_killed(): waiting for vpn service pid 2249 to exit
Aug 16 02:17:48 daddy-laptop NetworkManager: <debug> [1281921468.002561] ensure_killed(): vpn service pid 2249 cleaned up

Why cant ubuntu connect me to a pptp vpn?

---

### Post by dogdo on 2010-08-16
Seriously though for me ubuntu is almost perfect- i can do everything i used to be able to do on windows. Except for using a pptp vpn. The one im using is called TUVPN-i tested it on a windows machine and it worked. 

Can someone at least refer me to a vpn that is Known to work with ubuntu 10.04?

---

### Post by kulshoks2121 on 2010-08-22
Aug 16 02:17:35 daddy-laptop NetworkManager: <WARN> nm_vpn_connection_connect_cb(): VPN connection 'VPN connection 1' failed to connect: > 'invalid gateway 'gateway''.

are you sure you have the right IP address of the pptp server? or did you use a domain name instead?

---

### Post by Agent ME on 2010-08-22
Do other pptp vpn connections work for you? Try this one - [http://www.swissvpn.net/index.php?cot=faq&lang=en#selected](http://www.swissvpn.net/index.php?cot=faq&lang=en#selected) (note that it will only connect to the swissvpn.net site). If this works then that eliminates the possibility of something being wrong with your network (like pptp being blocked).

---

### Post by Oxwivi on 2010-08-23
Edit the connection and click on the Advanced button. Under Security and Compression, check the first two options as well: Use Point-to-Point encryption (MPPE) and Allow stateful encryption. Doing this allowed me to access two VPNs I tried so far.

Currently using [proXPN]("http://proxpn.com/").

---

### Post by wacky_sung on 2010-08-23
> **Oxwivi said:**
> Edit the connection and click on the Advanced button. Under Security and Compression, check the first two options as well: Use Point-to-Point encryption (MPPE) and Allow stateful encryption. Doing this allowed me to access two VPNs I tried so far.

Currently using [proXPN]("http://proxpn.com/").

I do not trust ProXPN as what they wrote below.

```
Q: Can I use an OpenVPN client instead of yours?
A: No. However, we do offer PPTP VPN manual setup instructions for the iPhone, and you can use this as a guide for setting up a PPTP VPN connection on your computer too. We strongly recommend against this (you'll get much better performance with our client) and will not answer questions about it (if you want to tinker you've got to go it alone) but you're welcome to try it if you like. You'll just need to create an account first. 

```

Probably their client have some kinda monitoring log of what you did or web surfing habits.Nothing is so good to be FREE.

---

### Post by Oxwivi on 2010-08-23
I'm using it WITHOUT the software. It should be obvious since I'm using Ubuntu 10.04 like my profile says. Using the iPhone settings and a bit of tweaking I mentioned above, I got it running.

And you can't help log monitoring. As long as you use internet, I believe there's no privacy. So I don't bother hiding my details either.

---

### Post by wacky_sung on 2010-08-23
> **Oxwivi said:**
> I'm using it WITHOUT the software. It should be obvious since I'm using Ubuntu 10.04 like my profile says. Using the iPhone settings and a bit of tweaking I mentioned above, I got it running.

And you can't help log monitoring. As long as you use internet, I believe there's no privacy. So I don't bother hiding my details either.

Just be extra caution,those logging may include logging your email and login whatever so you are doing.In short, they may use your details for marketing purposes or even selling it for 3rd parties.Look into their terms & conditions plus the policy.Potential they are using as a honeyport to nab those crackers using their service to commit illegal activities.

---

### Post by Oxwivi on 2010-08-23
You got a point but it's the same with wherever you give your email address, be it Facebook or any other forum. Heck, even the email address providers can do that, possibly. But as long as I can mark sources as spam, it's fine with me.

:lolflag:

---

### Post by tco on 2010-10-02
[Oxwivi]("http://www.uluga.ubuntuforums.org/member.php?u=1131907") can you tell me wath options have you enabled?
I try all combinations but i can't connect
I have your same OS.

---

### Post by gmmyabrk on 2010-11-22
I am also curious as to what settings you have used to connect to proxpn.  I have free accounts with both itshidden and proxpn.  I am currently unable to connect with either service with my Ubuntu box. I have successfully connected to the swissvpn service mentioned earlier in the thread with Ubuntu, so I know it isn't my network settings.  I can connect with both on a Windows xp system from the same location, so I have narrowed it down to the settings for network manager.  Looking at the forums and other tech sites are giving the same and sometimes conflicting information as to how to "fix" the problem - None of which seem to work for me.

---

### Post by waynemr on 2010-12-05
> **Oxwivi said:**
> Edit the connection and click on the Advanced button. Under Security and Compression, check the first two options as well: Use Point-to-Point encryption (MPPE) and Allow stateful encryption. Doing this allowed me to access two VPNs I tried so far.

Currently using [proXPN]("http://proxpn.com/").

I'm not able to connect with Ubuntu 10.10 64-bit either. I've used the built-in PPTP and tried the openVPN types to no avail.

---

### Post by Scott O'Nanski on 2011-01-11
> **Oxwivi said:**
> I'm using it WITHOUT the software. It should be obvious since I'm using Ubuntu 10.04 like my profile says. Using the iPhone settings and a bit of tweaking I mentioned above, I got it running.

And you can't help log monitoring. As long as you use internet, I believe there's no privacy. So I don't bother hiding my details either.

Can you provide an example of how you did this? I'm been trying to figure it out myself.

Thanks.

---

### Post by Scott O'Nanski on 2011-01-12
I've contacted proXPN and asked for detailed instruction on how to set up their service with Ubuntu, and Linux in general.

If they respond with a working solution I'll be posting it to the forums as soon as I am able.

---

### Post by Oxwivi on 2011-01-13
To use proXPN, you can't use the usual username and password with which  you used to apply for proXPN account. I had contacted proXPN, my email  was [EMAIL="oxwivi@gmail.com"]oxwivi@gmail.com[/EMAIL], and they told me to use [EMAIL="pptpd_oxwivi@gmail.com"]pptpd_oxwivi@gmail.com[/EMAIL]  instead with another set of password. If you cannot login with your  usual username and password, try contacting them. You can use my account  to access proXPN if you want to as well - I will provide you with my  password on request.

The settings were the same as the iPhone settings they provided, but  there are some additional options to take care of on Ubuntu.

[LIST]
[*]Click on the network icon on the panel, and navigate to VPN Connections and choose Configure VPN...
[*]Click on Add
[*]Select Point-to-Point Tunnelling Protocol (PPTP) from the dropdown list.
[*]Fill in the form with the following details:
[/LIST]
```
**Connection name** [any name you prefer]
**Gateway** pptp.proxpn.com
**Username** [refer to the first paragraph]
**Password** [refer to the first paragraph]
**NT Domain** [leave it empty]
```
[LIST]
[*]Click on the Advanced button after NT Domain, and check the first  two checkboxes under Security and Compression. The last three options  doesn't make a difference.
[/LIST]

---

### Post by Oxwivi on 2011-01-26
proXPN breking news! Successfully connected to proXPN using OpenVPN!

---

### Post by xcal90 on 2011-01-27
Really? That's awesome!! Can u tell us how to set it up.. PPTP is not working for me.. Maybe its my network. Maybe pptp port is blocked.. Hmm.. 

[https://www.vpnreactor.com/linux_openvpn.html](https://www.vpnreactor.com/linux_openvpn.html)

Should we follow the instructions above till number 3?
Thanks =))

---

### Post by Oxwivi on 2011-02-03
Actually, to tell you the truth, I've successfully used it on Windows only, since for a certain software I've been on Windows for most of the time. I'll try to use it on Ubuntu and inform you.

---

### Post by nito2721 on 2012-02-03
I read this thread a few times before finding my answer. Hopefully this helps someone in the future. Remove http:// and / from your server names.

[https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/664453](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/664453)

---

