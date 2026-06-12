---
title: "Issue joinging machines to Samba domain"
date: 2009-11-02
forum: Server Platforms
---

### Post by tiedyeguy64 on 2009-11-02
I have recently installed a samba 3 PDC on top of Ubuntu 8.04 server. Samba appears to be working correctly, and I have made sure all users have access via my own desktop, which I already joined to the domain.

I have created machine accounts for the next 2 machines to join the domain to start getting the users on the network, but am having an issue I cannot seem to resolve.

On the client machines, I change the computer name to match the machine account I created on the Samba server and reboot. Then I attempt to join the domain. I am using root as the username (I know all the hubbub about enabling root access; this is temporary. Once done, root will be disabled.)

After entering the username (root) and the root password, I get the following error message:

"The RPC Server is unavailable."

I have searched for several days, and cannot find information (I understand) on this issue. Can anyone point me in the right direction?

I should note that I have been able to join my desktop here in the office, a laptop from home, and even my desktop from home to the domain without issue. All three have been assigned different machine names, and had machine accounts created for them.

Thanks.

---

### Post by tiedyeguy64 on 2009-11-02
Also, if it matters, my workstations are getting IP addresses from our router, which is handling DHCP.

Thanks.

---

### Post by tiedyeguy64 on 2009-11-02
Again, fwiw, I just tried a new "clean" laptop (Win XP Pro).

Set windows machine name to laptop005 in system properties, left it in workgroup "workgroup". Rebooted.

Went to samba server, logged in as root, and ran:

useradd -s /bin/false -d /dev/null laptop005\$
smbpasswd -a -m laptop005

Response: "added user laptop005"

Went back to laptop, system properties, "Change" to join domain. Entered "mydomain" (without quotes).

When prompted, I entered "root" as the user (along with the root password, of course).

Still failed, "The RPC server is unavailable"

---

### Post by Zeosa on 2009-11-02
Is samba acting as a wins server? If so, try adding it to the wins server list on the client machines...(in the network adapter properties, tcp/ip properties)

---

### Post by tiedyeguy64 on 2009-11-02
Yes, it is acting as Wins server. I just went through smb.conf again, and noticed I had interfaces = 192.168.0.0 (instead  of 192.168.0.1)

I changed that, and got an "RPC call failed". I tried it again, and was allowed to join the domain, which is good. But I am still toreubled by this issue.

Here  is my smb.conf (minus the shares, etc):
[global]
   workgroup = mynet
   netbios name = server01
   server string = %h
   wins support = yes
   os level = 33
   preferred master = yes
   domain master = yes
   local master = yes
   name resolve order = wins lmhosts host bcast
   interfaces = 127.0.0.1 eth0
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   security = user
   encrypt passwords = true
   passdb backend = smbpasswd
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   domain logons = yes
   logon path = \\%L\profiles\%U
   logon drive = U:
   logon script = /data/home/login/%u.bat
   admin users = @admins
   add machine script = sudo /usr/sbin/useradd -n -g machines -c Machine -d /var/lib/samba -s /bin/false %u
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

Thanks.

---

### Post by tiedyeguy64 on 2009-11-02
I added the samba server's ip in the client side windbind list, as suggested.

I still cannot get most of the computers to join. I keep getting variations of error messages, all having to do with the RPC server.

Unfortunately, I have not familiar enough with RPC calls, so I am a little lost. And I have not successfully been able to find a good tutorial etc to explain it to me.

Thank you for any help you can give, even if its a link to a good explanation of how it works (relating to Samba).

---

### Post by Zeosa on 2009-11-02
How are IP's being assigned on your LAN (dhcp server on the box or a router?)

---

### Post by JonRohan on 2009-11-02
> **tiedyeguy64 said:**
> Also, if it matters, my workstations are getting IP addresses from our router, which is handling DHCP.

Thanks.

> **Zeosa said:**
> How are IP's being assigned on your LAN (dhcp server on the box or a router?)

:p ;)

This could be your problem. I'd look to make your linux box responsible for DHCP and DNS. 

Jon

---

### Post by tiedyeguy64 on 2009-11-03
I was wondering about that. Since I still had more to add to the server (I still need to get a vpn going), I figured using the router for DHCP would give me freedom to take the box with me if I needed it - The router at least can hand out IP addresses & get stand alone workstations on the internet.

I guess my next step is to move DHCP over to the server, and make a try at it. I can always switch it back.

I have been tempted top take an old box and drop debian onto it as a backup server, just in case. I have past experience with Debian; this is my first experience with Ubuntu.

Thanks. I will keep you posted.

---

### Post by Rural on 2009-11-06
I'm having similar issues myself. Starting with a fresh Ubuntu 9.04 Server install, where I've installed SSH, DNS, and Samba, I tailor smb.conf for my needs (set the workgroup, enable domain logons, change the [FONT="Courier New"]add machine script[/FONT] so I don't have to add machines manually, and add a couple of shares), make sure that the Unix admin group maps to Domain Admins, and restart Samba. Then when trying to add a machine to the domain, I get an access denied error on the Windows box. I can still access shares and such, just can't join the domain (which is kind of important in a school setting).

Here's the weird thing. I have another Samba PDC on the network, with a different workgroup name, otherwise set up nearly identically (obviously, I've missed something), that behaves differently:

   1) Joining the domain works great.
   2) In the add machines script, I don't have to sudo it, just [FONT="Courier New"]/usr/sbin/useradd...[/FONT] This fact *really* haunts me.

I've been upping the log level and comparing the logs, but haven't been able to figure out what the difference is.

The problem can be repeated on another server, with different clients, and on a different network. Basically, I've got a server that I set up the way I want (ie. it basically works), and I can't repeat the process.

---

### Post by Rural on 2009-11-06
The fellow in [this thread]("http://ubuntuforums.org/showthread.php?p=7090913") seems to be having a similar issue to myself. His fix was to enable the root account. Not surprisingly, I don't like that fix one bit. There must be a better way.

---

### Post by tiedyeguy64 on 2009-11-08
I had actually enabled the root account temporarily to troubleshoot; it made no difference at all. I was thinking of setting it up as a workgroup, not a PDC. I have only admined Samba as a pdc, and am not sure what (if any) real impact hat change would have...no joining the domain needed, easily add machnes...but can a road warrior vpn into a workgroup and still use samba? (I've never set up a vpn before...)

---

