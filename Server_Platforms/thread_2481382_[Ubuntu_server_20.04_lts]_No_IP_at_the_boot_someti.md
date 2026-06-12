---
title: "[Ubuntu server 20.04 lts] No IP at the boot sometimes"
date: 2022-11-28
forum: Server Platforms
---

### Post by johndid on 2022-11-28
Hi,

As I already said here:

[https://ubuntuforums.org/showthread.php?t=2481341&p=14120796#post14120796](https://ubuntuforums.org/showthread.php?t=2481341&p=14120796#post14120796)

 I installed Ubuntu Server 20.04 LTS on a laptop. It seems that it sometimes has some problem with connecting to my LAN.
When the boot process ends, I shoud see on its screen :

```
*Web console: https://server:9090/ or https://192.168.10.10:9090/*
```

But it happens that I often can only see this line ***[https://server:9090/](https://server:9090/)   (Server ***is its hostname)***. ***

In this case, I can't connect to it via browser nor start a ssh  connection via putty from my PC. Thus, I only can reboot hoping that it  will show its IP next time.

I already ran the the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") and sent it to pastebin:

[https://pastebin.com/vfzisxGX](https://pastebin.com/vfzisxGX)

Could you help me fix this too?Thanks

---

### Post by TheFu on 2022-11-28
Servers should have a static IP, set ON-THE-SERVER.  In 20.04, that setting happens via the netplan YAML file in /etc/netplan/.
Post your netplan file wrapped in forum 'code tags' so the indentation is retained.

netplan.io has examples, if you need to learn more about netplan.

---

### Post by johndid on 2022-11-28
> **TheFu said:**
> Servers should have a static IP, set ON-THE-SERVER.  In 20.04, that setting happens via the netplan YAML file in /etc/netplan/.
Post your netplan file wrapped in forum 'code tags' so the indentation is retained.

netplan.io has examples, if you need to learn more about netplan.

I made its IP static via my router's DHCP server; I thought that it was ok.
Anyway, here is the 00-installer-config.yaml


```


# This is the network config written by 'subiquity'
network:
  ethernets:
    enp6s0:
      dhcp4: true
  version: 2




```

Thanks for the link. When it comes to linux I always need to learn more.

---

### Post by TheFu on 2022-11-28
There are different opinions about using DHCP for servers.  I'm against it for a number of reasons, having been burned multiple times when DHCP servers failed.
A slow DHCP server can't answer fast enough, so no IP will be found.  That can be traced back to slow equipment, bad networking, or a misconfiguration on the DHCP server-side.

Using static IPs configured on the system, avoids that completely.  Of course, if a laptop gets moved to a different network, the system will need to be turned back to using DHCP, but when it is behaving as a server, it should have a locally set, static, IP.

IMHO.

Your netplan file is just for DHCP, which is pretty useless for a server.  You'll need to know the IP, netmask, gateway and 2 DNS server IPs to be used to manually setup the netplan YAML file(s).  There are rules for those - just be certain you pick a static IP outside the DHCP range used by other clients.

---

### Post by johndid on 2022-11-28
> **TheFu said:**
> There are different opinions about using DHCP for servers.  I'm against it for a number of reasons, having been burned multiple times when DHCP servers failed.
A slow DHCP server can't answer fast enough, so no IP will be found.  That can be traced back to slow equipment, bad networking, or a misconfiguration on the DHCP server-side.

Using static IPs configured on the system, avoids that completely.  Of course, if a laptop gets moved to a different network, the system will need to be turned back to using DHCP, but when it is behaving as a server, it should have a locally set, static, IP.

IMHO.

Your netplan file is just for DHCP, which is pretty useless for a server.  You'll need to know the IP, netmask, gateway and 2 DNS server IPs to be used to manually setup the netplan YAML file(s).  There are rules for those - just be certain you pick a static IP outside the DHCP range used by other clients.



I see.

Ok. Let's say that my ubuntu server static IP is going to be192.168.10.10/24, gateway 192.168.10.1 (my router IP) and 1.1.1.1, 8.8.8.8 or just my router IP again as DNS server/s.
What would the YAML file above look like?

Meanwhile I found this article:

[https://netplan.io/examples](https://netplan.io/examples)

Let's see if I come up with something which works properly.
Thanks

---

### Post by TheFu on 2022-11-28
Lots of people have posted working netplan yaml files in these forums, including me.  Search and I bet you'll find examples here.  Netplan is actively developed still, so some settings that are posted may not apply anymore. Be certain to look for non-22.04 posts.

---

### Post by MAFoElffen on 2022-11-28
Also as a note to TheFu and the OP... I didn't mention it, because we were working on another issue...

If you look at manually installed packages in his 'system-info' report, he does have Samba installed, but I don't think he installed the LAMP stack. 

I do not see Apache installed or configured... [s]So I am a bit confused why he would get that [server_ip]:9090 message. Is there anything for him to actually connect "to" by another machine running Console?[/s]

He also does have openssh-server installed, so he should be able to connect to to it via SSH from another machine.

Getting his static ip worked out should sort out everything...

Edit: He has 'cockpit' installed on his server... But I didn't see 'cockpit.podman' installed for container support. Once it is installed, then to finish the connection to (so he can connect via port 9090)
```

sudo systemctl enable cockpit
sudo systemctl status cockpit
sudo systemctl enable podman
sudo systemctl status podman

```

---

### Post by johndid on 2022-11-28
> **TheFu said:**
> Lots of people have posted working netplan yaml files in these forums, including me.  Search and I bet you'll find examples here.  Netplan is actively developed still, so some settings that are posted may not apply anymore. Be certain to look for non-22.04 posts.

ok, I will. Thanks

---

### Post by johndid on 2022-11-28
> **MAFoElffen said:**
> Also as a note to TheFu and the OP... I didn't mention it, because we were working on another issue...

If you look at manually installed packages in his 'system-info' report, he does have Samba installed, but I don't think he installed the LAMP stack. 

I do not see Apache installed or configured... [s]So I am a bit confused why he would get that [server_ip]:9090 message. Is there anything for him to actually connect "to" by another machine running Console?[/s]

He also does have openssh-server installed, so he should be able to connect to to it via SSH from another machine.

Getting his static ip worked out should sort out everything...

Edit: He has 'cockpit' installed on his server... But I didn't see 'cockpit.podman' installed for container support. Once it is installed, then to finish the connection to (so he can connect via port 9090)
```

sudo systemctl enable cockpit
sudo systemctl status cockpit
sudo systemctl enable podman
sudo systemctl status podman

```

Not sure what you exactly mean.
Anyway. I haven't such a podman:

```
luke@server:~$ sudo systemctl status podman
Unit podman.service could not be found.

```

as for  cockpit:

```

luke@server:~$ sudo systemctl status cockpit
[sudo] password for luke:
&#9679; cockpit.service - Cockpit Web Service
     Loaded: loaded (/lib/systemd/system/cockpit.service; static; vendor preset: enabled)
     Active: inactive (dead) since Mon 2022-11-28 19:53:34 CET; 6min ago
TriggeredBy: &#9679; cockpit.socket
       Docs: man:cockpit-ws(8)
    Process: 116327 ExecStartPre=/usr/sbin/remotectl certificate --ensure --user=root --group=cockpit-ws --selinux-type= (code=e>
    Process: 116330 ExecStart=/usr/lib/cockpit/cockpit-tls (code=exited, status=0/SUCCESS)
   Main PID: 116330 (code=exited, status=0/SUCCESS)

Nov 28 19:51:30 server systemd[1]: Starting Cockpit Web Service...
Nov 28 19:51:31 server systemd[1]: Started Cockpit Web Service.
Nov 28 19:51:31 server cockpit-tls[116330]: cockpit-tls: gnutls_handshake failed: A TLS fatal alert has been received.
Nov 28 19:53:34 server systemd[1]: cockpit.service: Succeeded.



```

Thank you

---

### Post by TheFu on 2022-11-28
Cockpit is a webapp.  The jury is still out on whether it is all that useful, or just opens many attack vectors to a system.  

If you take the laptop anywhere, please, please, please, please, remember to disable cockpit.  When on a LAN that is secure and protected by multiple layers, it isn't likely to be abused too much, but all webapps are problems when any javascript is allowed on the subnet.  For example, your "server" is at .10 and your desktop running a web-site's javascript is on .233.  The javascript can run a scan on your entire subnet in a few seconds, find all open network services, then based on what it finds, load attacks specific to each from the internet through your normal web browser.  It makes every javascript web browser and attackers dream tool, all because you either visited a website or somehow they tricked an advertising company into loading their javascript (which sadly, isn't too hard).  Sigh.  Better to just stop now and don't use webapps for any management of infrastructure.
Let's be clear, node.js servers aren't the issue, though they have plenty of security issues based on the times they've been caught with infested code in the npm repos.  The problem is when js is run from your trusted browser.
[https://defuse.ca/in-browser-port-scanning.htm](https://defuse.ca/in-browser-port-scanning.htm) has an example scanner that has been around a few years.  Scanning is just the first step.

---

### Post by MAFoElffen on 2022-11-28
> **johndid said:**
> ```

Nov 28 19:51:31 server cockpit-tls[116330]: cockpit-tls: gnutls_handshake failed: A TLS fatal alert has been received.

```
I only see one error reported there. If it were more, then I would worry that it was related this this problem, 
[https://github.com/cockpit-project/cockpit/issues/14896](https://github.com/cockpit-project/cockpit/issues/14896)
which seems to have been ongoing since before this... Because before that one, there was another issue where they changed the TLS timeout to 90 for RedHat...

Sorry... Got ahead of myself. You do not have PodMan. You have Docker. So cockpit-podman would give you nothing. But if you added ppa:cockpit-project/cockpit, you could install package cockpit-docker, where you could remotely manage your docker containers via cockpit (GUI). Since you seem to want to do remote GUI management...

EDIT: They don't have LXD support (yet)... But:
[https://www.virtualizationhowto.com/2021/07/lxc-container-management-gui-installation-and-configuration/](https://www.virtualizationhowto.com/2021/07/lxc-container-management-gui-installation-and-configuration/)

---

### Post by TheFu on 2022-11-28
Gotta ask - is the static IP thing SOLVED?  If so, please mark this thead SOLVE using the Thread Tools link near the top.  Helps everyone out ... er ... before we get too off-topic.

---

### Post by johndid on 2022-11-29
> **TheFu said:**
> Gotta ask - is the static IP thing SOLVED?  If so, please mark this thead SOLVE using the Thread Tools link near the top.  Helps everyone out ... er ... before we get too off-topic.

not yet. I hope that I'll have time to fix it within the day. Thanks

---

### Post by johndid on 2022-11-29
> **MAFoElffen said:**
> I only see one error reported there. If it were more, then I would worry that it was related this this problem, 
[https://github.com/cockpit-project/cockpit/issues/14896](https://github.com/cockpit-project/cockpit/issues/14896)
which seems to have been ongoing since before this... Because before that one, there was another issue where they changed the TLS timeout to 90 for RedHat...

Sorry... Got ahead of myself. You do not have PodMan. You have Docker. So cockpit-podman would give you nothing. But if you added ppa:cockpit-project/cockpit, you could install package cockpit-docker, where you could remotely manage your docker containers via cockpit (GUI). Since you seem to want to do remote GUI management...

EDIT: They don't have LXD support (yet)... But:
[https://www.virtualizationhowto.com/2021/07/lxc-container-management-gui-installation-and-configuration/](https://www.virtualizationhowto.com/2021/07/lxc-container-management-gui-installation-and-configuration/)

thanks for the links.
I'll read them through carefully.

---

### Post by johndid on 2022-11-29
> **TheFu said:**
> Cockpit is a webapp.  The jury is still out on whether it is all that useful, or just opens many attack vectors to a system.  

If you take the laptop anywhere, please, please, please, please, remember to disable cockpit.  When on a LAN that is secure and protected by multiple layers, it isn't likely to be abused too much, but all webapps are problems when any javascript is allowed on the subnet.  For example, your "server" is at .10 and your desktop running a web-site's javascript is on .233.  The javascript can run a scan on your entire subnet in a few seconds, find all open network services, then based on what it finds, load attacks specific to each from the internet through your normal web browser.  It makes every javascript web browser and attackers dream tool, all because you either visited a website or somehow they tricked an advertising company into loading their javascript (which sadly, isn't too hard).  Sigh.  Better to just stop now and don't use webapps for any management of infrastructure.
Let's be clear, node.js servers aren't the issue, though they have plenty of security issues based on the times they've been caught with infested code in the npm repos.  The problem is when js is run from your trusted browser.
[https://defuse.ca/in-browser-port-scanning.htm](https://defuse.ca/in-browser-port-scanning.htm) has an example scanner that has been around a few years.  Scanning is just the first step.

I didn't know that Cockpit could have such security issues.
Anyway, the laptop on which I installed Ubuntu is an old one. I can't carry it around because its battery is gone. Its keyboard and screen have a few issues as well.
BUT it is a small piece of hardware, which still works decently, and perfectly fits my humble and little needs at home. Last but not least, it is low energy consuming 
which makes it also even more very welcome considering that  the electricity price has skyrocketted lately.

When needed (very few times actually), I get access to it from outside only via VPN (Wireguard or Tailscale).

Thanks for the hints

---

### Post by johndid on 2022-11-29
Ok. The problem seems to have been fixed.
It actually haven't shown up since I fixed the "sleep" issue we talked about in my previous topic. I don't know if it has something to do with it, or if it is just a coincidence anyway.

Thanks

---

