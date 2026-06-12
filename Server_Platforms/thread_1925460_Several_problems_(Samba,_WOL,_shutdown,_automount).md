---
title: "Several problems (Samba, WOL, shutdown, automount)"
date: 2012-02-14
forum: Server Platforms
---

### Post by RopeNL on 2012-02-14
Hi guys,

Let me first say that I'm relatively new to Ubuntu, I can make my way around with the Terminal and I now how most things work.
However when it comes to more complex things and dependencies I'm lost.

I'll provide you with the following information before I start explaining what I've done so far.

**Network**
Router: ZTE H220N.
 DMZ: Server staat als DMZ host.
 Portforwarding: UDP port 9 is forwarded to the static IP address of the server.

**Server**
 OS: Ubuntu Server 11.10
 Motherboard: Asrock 890GM pro3 
 Motherboard ACPI config: PCI Devices Power On "Enabled".
 OS ACPI Config: PCI Bridge linked to ethernet controller wake-up "Enabled".
Name: Ubuntu-Media-Server
ShareName: Shared

Ok so I'll start with the first and main problem.

**Backstory**
My  server has been working fine for a few months now and there were no  problems. Then I decided I wanted to be able to wake up my server using **WOL**. So I started searching for the possibilities of my current setup.

According to the on-line documentation my on-board Ethernet-card should be able to be woken up by a Magic Packet.

So I started looking for how this should be done. I started doing some stuff with the network settings. All was well.
I  couldn't get WOL working so I decided to do something else I wanted to  do for somewhile (there might be a problem with my router's firewall and  that might be why I cant get it working, however I cannot access any  part of the firewall since my ISP, who provided the router, has blocked  all access to the firewall and set it on a default level of security,  "high"). Which is have my main account log-in when I start up the  server. I got this working pretty fast.

Since I've got a server and I had samba running I though well, let's see If I can get my main Multiple-Disk array to automount.
This is when the trouble began.

[B]Shutdown
[/B]When  I started to search for option to automount I found out that you needed  to alter the fstab table. Since I didn't really know what I was doing I  might have done something wrong there.
However, when I tried to shutdown/restart the server I encountered a problem. My server refused to shut down. 
It  started the shutdownproces, I can see the services being  shutdown/stopped. But then at the end of the list there is something  saying "Backtrace blabla" and when it reaches that it just stops  shutting down. Like it just freezes up.

**Samba**
After  this happened I thaught to myself lets see if I can fix it. I searched  far and wide but I couldn't get it fixed. In the meanwhile for some  reason my sambaserver stopped working. So I reinstalled it, accidentally  rewriting my smb.conf file to the one that comes with the package.  Since then I've not been able to get access to my shares.
My shares appear on the network but when I try to access them I get this message: "No access to '//ServerName/ShareName'".
When  I try to determine the problem I get the following message: "Windows  has determined the server 'ServerName' exists but could not find  'ShareName'".

I'm guessing this has something to do with the  access-level. I the share to be open to everyone using  samba-system-config but to no avail. I think it should be solveable by  configuring the smb.conf but I've got no idea how I got it working the  last time.
Maybe you guys can help me out with the configuration. If  you want I'll post my current smb.conf just let me know (typing this on a  Windows machine so I've got no access to it right now.).

**Summary**

[LIST=1]
[*]Ubuntu Server 11.10, stuck at shutdown.
[*]Samba shares unaccessable, however they are visible in the network.
[*]Cannot get WOL to work.
[/LIST]
I put it in order of what I find most important to fix first.

I would like to thank anyone who takes the time to help me in advance.

Greetings Rope.

---

### Post by egpetrich on 2012-02-14
There have been several threads related to wake-on-lan in the past, such as:

[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)
[http://ubuntuforums.org/showthread.php?t=1855551](http://ubuntuforums.org/showthread.php?t=1855551)
[http://ubuntuforums.org/showthread.php?t=814939](http://ubuntuforums.org/showthread.php?t=814939)

As long as you are trying to wake your server from the same LAN as the server itself, the firewall settings on your router shouldn't matter. Trying to wake your system from outside your LAN is very troublesome.

---

### Post by maarten03 on 2012-02-15
I have exactly the same problem. Have you got any solution yet? I wonder how to get Samba working.

---

### Post by RopeNL on 2012-02-15
Hi [egpetrich]("http://ubuntuforums.org/member.php?u=615924"),

Thanks for your reply. Yeah I figured as much. But I'm guessing my router is messing things up.
However the WOL thing is not my main concern (though I appreciate your help).
The most important part is getting the server to shut-down properly.  Which I've not been able to do since I started working on the WOL thing.

I'm considering doing a complete re-install of 11.10 but I don't want to do that unless absolutely necessary.

Anybody else got any ideas?

---

### Post by RopeNL on 2012-02-16
Hi [maarten03]("http://ubuntuforums.org/member.php?u=1525611"),

I've not found a solution yet. However it appears that Samba should work on a fresh install of Ubuntu server 11.10. But you have to install python-glade as well as glade. Which you can find in the synaptic package manager. I did this but to no avail for me.

Mayvbe it'll help.

Rope.

---

### Post by RopeNL on 2012-02-17
Hi guys,

Today I was planning to do a complete reinstall of Ubuntu Server but something odd happened. I had made a bootable USB drive I inserted it into the USB-port and I was about to clean up my Ubuntu partition but I thought what the heck, lets give it one more try.

So I started Ubuntu and restarted it, then for some reason the shutdown process continued as normal. As if nothing had happened. I have literally done nothing but insert a USB drive into the USB-port and restart Ubuntu.

So the only thing that remains is the Samba problem. It appears that a lot of people are having problems with this. I'm thinking it's something with the smb.conf file as I got it working before, which was in 11.04 before I upgraded to 11.10.

Any help is appreciated, 

Greetings Rope.

---

### Post by RopeNL on 2012-02-17
Well I'm completely out of ideas right now. I restored the fstab file to its original state, to no avail. Even more the Shutdown problem is now back.

I'll be doing a reinstall of Ubuntu Server when I get the time, or see if I can get a different distro.

---

