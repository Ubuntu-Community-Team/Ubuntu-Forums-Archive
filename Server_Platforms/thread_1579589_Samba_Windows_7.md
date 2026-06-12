---
title: "Samba Windows 7"
date: 2010-09-22
forum: Server Platforms
---

### Post by s-twig on 2010-09-22
Hi

I've got the strangest of issues, and after days of Googling I'm turning you guys for help.

I've got a Samba server (CentOS)(I swear all my non-work boxes are Ubuntu) that has been working fine in our Active Directory environment for a long time, now that Windows 7 has been forced upon us, we've noticed that Win 7 users aren't able to authenticate to this server unless they access it using the IP address, e.g. \\192.168.1.22

We've tried the different Windows 7 registry hacks and nothing makes a difference.  We were advised to update Samba and we did to 3.3.8.  However, this being a virtual machine, upgrading a clone of this machine did work, the configuration was identical, except the hostname.

Any ideas would be great, thanks.

:confused:

---

### Post by CharlesA on 2010-09-22
If it authenticates using the IP address only, check to make sure that DNS is resolving hostnames correctly.

I'm using Samba 3.4.7 on Ubuntu 10.04.1 without any problems.

---

### Post by Vegan on 2010-09-22
SAMBA by default will only accept localhost connections, you need to change the setup to be available to other clients.

---

### Post by CharlesA on 2010-09-22
> **Vegan said:**
> SAMBA by default will only accept localhost connections, you need to change the setup to be available to other clients.

Source?

---

### Post by Vegan on 2010-09-22
Look at the smb.conf file and it has all the information needed.

---

### Post by luvshines on 2010-09-22
@s-twig

Also check if you can still access [mount/smbclient] from the server itself. Just make sure while checking this, it doesn't loopback to 127... series(remove the entry from /etc/hosts for testing purpose)

Though I haven't seen Samba server accepting only local connections as pointer out by Vegan

---

### Post by CharlesA on 2010-09-22
> **luvshines said:**
> 
Though I haven't seen Samba server accepting only local connections as pointer out by Vegan

Me either. I've gone over the smb.conf that came with 10.04 and didn't see anything mention "localhost" at all.

---

### Post by redmk2 on 2010-09-22
> **CharlesA said:**
> Me either. I've gone over the smb.conf that came with 10.04 and didn't see anything mention "localhost" at all.

Actually, it was a smart-a*s answer from Vegan.  Samba always broadcasts it's presence.  See the following from the Samba documentation```
By default Samba will query the kernel for the
list of all active interfaces and use any interfaces 
**[COLOR="Red"]except 127.0.0.1[/COLOR]** that are broadcast capable.
```

---

### Post by s-twig on 2010-09-22
Thanks for the responses, very active forum. :KS

It mounts to itself fine using DNS to resolve its own name.  The strange thing is that this continues to work with Windows XP just as it always has.

Another virtual machine with the same config (identical) but different hostname was happy with Windows 7 and XP.

A quote from another forum is something that I hadn't come across but found interesting.

> When you are using the IP address, the client does not get a ticket for
the server (requesting a ticket for "192.168.10.11" instead "hostname" -
but the ADS server only has a ticket for "hostname").
After that, the client uses NTLM authentication. If this succeeds you
become transparently connected to the server.

Any more ideas?

---

### Post by CharlesA on 2010-09-22
I don't get it. I've got a Samba box that works fine with Windows 7 (and Vista and XP). I'm not using AD tho. I'll promote a machine to a DC and hook up a Win7 machine to it and see what happens.

EDIT: How are you doing the authentication?

---

### Post by s-twig on 2010-09-22
Hi

Thanks for the time you've taken.

I'm using domain authentication and using the dc as the password server.  This is weird.  I thought it might be DNS or AD related but I can't see anything amiss there either.

:confused:

---

### Post by CharlesA on 2010-09-22
So the passwords that the users are using for samba are stored on the DC, right?

Not quite sure how that's set up. Could you post yer smb.conf file?

Update: I messed around with Server 2K8 and trying to get Samba to authenticate to it and failed. What a pain in the butt.

---

### Post by s-twig on 2010-09-22
```
[global]
        workgroup = AUS
        realm = OURAUS.LOCAL
        server string = Resource Samba Server
        security = DOMAIN
        password server = tango
        log file = /var/log/samba/%m.log
        max log size = 50
        name resolve order = hosts bcast lmhosts wins
        local master = No
        wins server = 192.168.22.4
        wins support = Yes
        idmap uid = 16777216-33554431
        idmap gid = 16777216-33554431
        guest ok = Yes
        hosts allow = 192.168.22., 127.
        cups options = raw
        winbind use default domain = yes
        notify:inotify = false
        log level = 1

```

---

### Post by CharlesA on 2010-09-22
Ah ok. That's way different from the guide I was trying to follow.

So it worked on a VM, but not on the regular machine?

I'd suggest a reboot just to see what happens. I had a similar thing happen on my server with a web app that weren't work. Reboot got everything sorted out.

---

### Post by s-twig on 2010-09-22
I've rebooted a few times.  To me it seems like there is something strange that hostname wise that Windows 7 is requesting that the DC doesn't like...

Thanks

---

### Post by CharlesA on 2010-09-22
Does it happen on any machine not running Win7?

---

### Post by s-twig on 2010-09-22
Yeah, it does it to Vista too.  XP works like a champ :)

---

### Post by CharlesA on 2010-09-22
I wonder if it has to do with Vista and 7 dealing with networking differently.

What OS are you using for the DC? 2K3, or 2k8?

---

### Post by s-twig on 2010-09-22
2003

---

### Post by luvshines on 2010-09-23
I have been using that kind of setup for over an year now.

We did some testing with windows 7 as well, were able to get it working i guess.

Though, I see some unfamiliar entries in your smb.conf file.
I haven't used them, wins server and hosts allow.

Will try to find out something.
Can you try to comment those and for the time being, restart smb daemon and again give it a try :)

---

### Post by s-twig on 2010-09-23
I can do that.  I'll let you know.

---

### Post by SeijiSensei on 2010-09-23
This definitely sounds like a nameservice problem to me.  Can your clients access \\myserver.mydomain\share, but not \\myserver\share?  If so, it sounds like the AD server isn't telling the clients that they're in mydomain.  If you run "ipconfig /all" on the Windows clients, do they have complete DNS information?

(Note that I'm talking about DNS domains here, not anything having to do with AD.)

---

### Post by capscrew on 2010-09-23
> **SeijiSensei said:**
> This definitely sounds like a nameservice problem to me.  Can your clients access \\myserver.mydomain\share, but not \\myserver\share?  If so, it sounds like the AD server isn't telling the clients that they're in mydomain.  If you run "ipconfig /all" on the Windows clients, do they have complete DNS information?

(Note that I'm talking about DNS domains here, not anything having to do with AD.)

SMB resources (shares), are not ultimately identified by DNS names (FQDN or hostname).  Samba in particular takes the hostname and uses it as a NetBIOS name.  SMB resources are allways described in the following manner: //netbios_name/share_name

The OP may have problems with this mapping.  If you set the netbios name in the smb.conf file then the nmbd daemon will use that instead of mapping DNS hostname to netbios name.

This can be accomplished with ```
netbios name = <a 15 character or less name>
# This can be the hostname but does not have to be such
```

See [**_here _**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html")for all the entries in the smb.conf file.

---

### Post by s-twig on 2010-09-24
> **SeijiSensei said:**
> This definitely sounds like a nameservice problem to me.  Can your clients access \\myserver.mydomain\share, but not \\myserver\share?  If so, it sounds like the AD server isn't telling the clients that they're in mydomain.  If you run "ipconfig /all" on the Windows clients, do they have complete DNS information?

(Note that I'm talking about DNS domains here, not anything having to do with AD.)

Thanks for the help.  DNS resolution appears fine, clients (except Vista and 7) can access using either FQDN or just the hostname.  All clients have the correct DNS info.  It's got me beat...

---

### Post by s-twig on 2010-09-24
> **capscrew said:**
> SMB resources (shares), are not ultimately identified by DNS names (FQDN or hostname).  Samba in particular takes the hostname and uses it as a NetBIOS name.  SMB resources are allways described in the following manner: //netbios_name/share_name

The OP may have problems with this mapping.  If you set the netbios name in the smb.conf file then the nmbd daemon will use that instead of mapping DNS hostname to netbios name.

This can be accomplished with ```
netbios name = <a 15 character or less name>
# This can be the hostname but does not have to be such
```

See [**_here _**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html")for all the entries in the smb.conf file.

Thanks, I've tried the netbios name directive but it doesn't seem to have an affect on it.

---

### Post by luvshines on 2010-09-24
Just noticed that you have security = domain in your smb.conf

When I use AD authentication for my samba server, security = ADS is what I use in smb.conf

What steps did you perform to setup AD authentication with Samba ?

---

### Post by capscrew on 2010-09-24
> **s-twig said:**
> Thanks, I've tried the netbios name directive but it doesn't seem to have an affect on it.

I don't use Samba in a AD environment myself.  What I do know is that Samba, by way of smbd and nmbd, works the same regardless of the manner of the storage of the users and groups.  My remarks were in regards to how NetBIOS is used.

In general it seems that most problems involve inappropriate FW settings or incorrect setup of Samba users.  I can only suggest [**_this page _**]("http://wiki.samba.org/index.php/Samba_&_Active_Directory")from the Samba Wiki.  The site is RedHat centric.  So for you that's a bonus.

---

### Post by SeijiSensei on 2010-09-24
> **capscrew said:**
> SMB resources (shares), are not ultimately identified by DNS names (FQDN or hostname).  Samba in particular takes the hostname and uses it as a NetBIOS name.  SMB resources are allways described in the following manner: //netbios_name/share_name

> **s-twig said:**
> I've got a Samba server (CentOS)(I swear all my non-work boxes are Ubuntu) that has been working fine **in our Active Directory environment** for a long time, now that Windows 7 has been forced upon us, we've noticed that Win 7 users aren't able to authenticate to this server unless they access it using the IP address, e.g. \\192.168.1.22

s-twig is running on a Windows network with Microsoft Active Directory.  AD provides, among other things, an RFC-compliant domain name server like [ISC]("http://www.isc.org/") [BIND]("http://www.isc.org/software/bind").  Starting with [Windows Server 2003]("http://technet.microsoft.com/en-us/library/cc759550%28WS.10%29.aspx"), DNS has been Microsoft's preferred technology for naming hosts rather than \\HOST\SHARE style Netbios names.

So I'd suggest s-twig check the AD DNS server to see if it has both an A and a PTR record for 192.168.1.22.  You may need to add them manually.  See if that helps.

---

### Post by capscrew on 2010-09-24
> **SeijiSensei said:**
> s-twig is running on a Windows network with Microsoft Active Directory.  AD provides, among other things, an RFC-compliant domain name server like [ISC]("http://www.isc.org/") [BIND]("http://www.isc.org/software/bind").  Starting with [Windows Server 2003]("http://technet.microsoft.com/en-us/library/cc759550%28WS.10%29.aspx"), DNS has been Microsoft's preferred technology for naming hosts rather than \\HOST\SHARE style Netbios names.
The SMB/CIFS protocols use NetBIOS.  Both Samba and MSuse NetBIOS over TCP (NBT) to communicate.  Use wireshark and you will see this.  Here is a [**_general overview _**]("http://msdn.microsoft.com/en-us/library/aa365236(v=VS.85).aspx")of the process.> 

So I'd suggest s-twig check the AD DNS server to see if it has both an A and a PTR record for 192.168.1.22.  You may need to add them manually.  See if that helps.
This will only ID the host. Not the SMB resource.  My feeling is that the user/group mapping is not correct, an LDAP fault rather than a DNS problem.

---

### Post by s-twig on 2010-09-26
> **capscrew said:**
> The SMB/CIFS protocols use NetBIOS.  Both Samba and MSuse NetBIOS over TCP (NBT) to communicate.  Use wireshark and you will see this.  Here is a [**_general overview _**]("http://msdn.microsoft.com/en-us/library/aa365236(v=VS.85).aspx")of the process.
This will only ID the host. Not the SMB resource.  My feeling is that the user/group mapping is not correct, an LDAP fault rather than a DNS problem.

Thanks for the info.  I was leaning towards a DNS or similar issue only because the same setup worked on another host, only difference being the IP and hostname.  I thought it might be Win 7 passing something different in the Kerberos security ticket that had the wrong host or something.

I don't even know where to head in terms of troubleshooting.  Should I be able to see auth failures in the AD domain controller's security log, or just Samba's logs?

---

### Post by capscrew on 2010-09-27
> **s-twig said:**
> Thanks for the info.  I was leaning towards a DNS or similar issue only because the same setup worked on another host, only difference being the IP and hostname.  I thought it might be Win 7 passing something different in the Kerberos security ticket that had the wrong host or something.

I don't even know where to head in terms of troubleshooting.  Should I be able to see auth failures in the AD domain controller's security log, or just Samba's logs?

Doesn't it really depend on what the real problem is?  Do you see any errors in the either logs.

From my perspective the problem is one of browsing the shares and this has everything to do with the client host being able to retrieve the browse list.

Read [**_this  _**]("http://scottiestech.info/2009/02/14/how-to-determine-the-master-browser-in-a-windows-workgroup/")for further info and try some of the commands from a Win7 host.

The command ```
net view
``` from the windows command line should provide a list of all COMPUTER NAMES available from the browse list.

The article provides a script to check all the resources on the LAN.  I have never used the script so I can't vouch for its abilities.

---

### Post by R.Bucky on 2010-09-27
I struggled with W7/Samba interaction for a couple of hours yesterday. A few hacks that I found and posted on my blog > [http://nwlinux.com/blog/access-samba-shares-with-windows7-professional/]("http://nwlinux.com/blog/access-samba-shares-with-windows7-professional/")

---

