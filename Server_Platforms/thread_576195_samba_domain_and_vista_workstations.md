---
title: "samba domain and vista workstations"
date: 2007-10-14
forum: Server Platforms
---

### Post by k1ll1nt1m3 on 2007-10-14
I have spent a few hours now trying to setup a ubuntu domain server for my home.  I got it close, I think.  I can see the domain controller but I can not join the domain.  I get " bad password or user name" errors when I try to join from my Vista PC.

Has anyone got this working?  Im using ubuntu-server-7.04 and samba 3.0.24.  Thanks.

Edit: I commented out " invalid users = root" and Vista joined.  How unsafe is this?  I am behind a firewall at my home.  Any ideas as to what I have missed?  I have the machine in users and smbpasswd with a different name but it will not login with that name.

---

### Post by HermanAB on 2007-10-15
Go to the Samba site and read the Official Howto.

---

### Post by netlogic on 2007-10-15
[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

---

### Post by HermanAB on 2007-10-15
You may need the experimental Samba version 4.  See the Samba web site for details.

---

### Post by netlogic on 2007-10-15
Also, issue can be authentication. There should be an option in VISTA to use only NTLM v1 and LM. Look for it in the security policy guide. Also, look for Vista technet docs at Microsoft for how to use Vista to log on to NT4 and 2000. It should  guide you to use NTLMV1.
ONly Samba servers to 3.0.22 or higher use NTLMV2

Run secpol.msc
Go to: Local Policies > Security Options
Find "Network Security: LAN Manager authentication level"
Change Setting from "Send NTLMv2 response only" to
"Send LM & NTLM - use NTLMv2 session security if negotiated"
Now, use vista like xp to connect.

---

### Post by netlogic on 2007-10-15
By the way, it is a good idea to use the sniffer. Wireshark is very easy to use.

have fun.

---

### Post by k1ll1nt1m3 on 2007-10-19
I cheated a bit and got my server running.  I allowed root login to join the machine then I removed root login again.  I now have my Vista pc on the domain hosted by ubuntu. 

I just cant get the user login correct.  I went into Vista and set

"Send LM & NTLM - use NTLMv2 session security if negotiated"

It tries to login but cannot find the profile, so I get the "temp profile used" when I login to Vista via a network profile.  I set directories /home/samba/netlogon and /home/samba/profiles to 0777 (for testing).  I have a directory "trial" in each.  All in /home/samba is "users" group, "root" own, and 0777.

Here is the log.vista1 file in samba log...

[2007/10/18 22:58:57, 1] smbd/service.c:make_connection_snum(950)
  vista1 (192.168.1.100) signed connect to service profiles initially as user trial (uid=1004, gid=1004) (pid 17529)
[2007/10/18 22:58:57, 1] smbd/service.c:make_connection_snum(950)
  vista1 (192.168.1.100) signed connect to service netlogon initially as user trial (uid=1004, gid=1004) (pid 17529)
[2007/10/18 22:58:58, 0] smbd/service.c:make_connection(1111)
  vista1 (192.168.1.100) couldn't find service trial
[2007/10/18 22:59:08, 1] smbd/service.c:close_cnum(1150)
  vista1 (192.168.1.100) closed connection to service profiles
[2007/10/18 22:59:08, 1] smbd/service.c:close_cnum(1150)
  vista1 (192.168.1.100) closed connection to service netlogon

Am I correct in thinking it cannot find the profile for user "trial"?  Is it looking for a profile on samba or the Vista?  I have ubuntu's "trial" home set at /home/trial. 

Thanks again

---

### Post by tautech on 2007-10-25
Hi there.

Have a similar problem with my Ubuntu Server.

Root user can login but any other user I create does not.

If I move the user to the Admin Group with 
"usermod -a -G Admin newuser"

Then it allows the newuser to login - if the password is set for the user.
But if I move the user to any other group like geust or users
it does not allow my windows xp pc to login on the ubunto server - domain I set up as workgroup.

This seems to look like a Group pollisy/ security problem.
Seeing that the newuser can login if he is part of the Admin group
And not if he is part of the Users group.

Is there any way to fix the Users group security so the users in the users group can also login from a Win Xp machine.???

---

