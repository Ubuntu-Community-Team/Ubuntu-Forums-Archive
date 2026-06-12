---
title: "sshd + /etc/hosts.allow - deny +tcpwrapper failure :("
date: 2008-10-03
forum: Security
---

### Post by NexusGS on 2008-10-03
Hi everyone and keep up the good work.

I am using ubuntu for sometime now. I have an issue with openssh server and tcpwrapper. sshd is not affected by /etc/hosts.allow\deny.

-sshd is configured
-works with tcpwrapper 
[root@Ferrari:/var/log# ldd /usr/sbin/sshd | grep libwrap
	libwrap.so.0 => /lib/libwrap.so.0 (0xb7e77000)]

Even if i use @ /etc/hosts.deny the option 
sshd : ALL 
or
ALL : ALL
 nothing changes! Sshd is accepting connections from everywhere!

Any suggestion? I cannot find any solution..

---

### Post by NexusGS on 2008-10-03
Just to inform you, I tried reinstalling openssh server and tcpwrappers...Nothing changed :(

---

### Post by cariboo on 2008-10-03
There is no need to reinstall a program, just because it doesn't work the way you expect it to. In most cases the configuration file doesn't get over written when you reinstall, leaving you with exactly what you had before.

Have you tried ALL: PARANOID in hosts deny, and what is in hosts.allow

Jim

---

### Post by NexusGS on 2008-10-04
I reinstalled these progs just in case a file or something was damaged.

Anyway,

/etc/hosts.deny:
ALL : PARANOID

/etc/hosts.allow:
sshd: IP/255.255.255.255 : allow

I can still login from any IP address :(

---

### Post by cariboo on 2008-10-04
> sshd: IP/255.255.255.255 : allow

That is not a valid ip address. Use the ip address of the computer you are using to connect to the remote commputer, then change the ip address to something a little different.
For example if the ip address of your computer is 192.168.1.100 then:

```
ssh: 192.168.1.100 : allow
```

Then change the ip address of your computer to something like 192.168.0.100 and try to connect to the remote computer.

Jim

---

### Post by NexusGS on 2008-10-04
I have a PC that i want to connect from... I changed it as you mentioned and nothing! I can still connect from other computer too!
Just to let you know I have allow file empty ( i allow nothing practically) and at deny file I have only " ALL : PARANOID "and i can still ssh my pc... :( :confused:

---

### Post by amac777 on 2008-10-04
I don't think PARANOID is what you want. From the man page: "The PARANOID wildcard matches any host whose name does not match its address."

I think the problem was you had everybody allowed in your first tests so your hosts.deny file was never checked. From "man hosts.deny":

>  The access control software consults two files. [B]The search stops at the
       first match:[/B]

       ·      Access  will  be  granted when a (daemon,client) pair matches an
              entry in the /etc/hosts.allow file.

       ·      Otherwise, access will be denied  when  a  (daemon,client)  pair
              matches an entry in the /etc/hosts.deny file.

       ·      Otherwise, access will be granted.



So keep your hosts.allow file empty, and try putting "ALL: ALL" in your hosts.deny file. That should prevent everybody including yourself from sshing into your box. Once you confirm that works, you can add your own remote IP address into the hosts.allow file to allow yourself.

---

### Post by NexusGS on 2008-10-04
/etc/hosts.deny
```
ALL : ALL
```

/etc/hosts.allow
```
empty
```

I restarted the ssh service and nothing changed..I can still ssh my pc from a remote pc.... :(

---

### Post by cariboo on 2008-10-04
I've done some experimenting and have got it to work. I should explain my setup, I have a home network that consists of seven computers, 2 in the house and 5 in my detached garage.

What I did is to ssh into my server and then ssh'd from the server to the subject of the expiriment, I could connect with no problem. I then edited hosts allow, it looks like this:

```
 cat /etc/hosts.allow
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
All: 127.0 [::1]
sshd : 192.168.1.100
```

the above allows the 127.0. range , as well as the localhost ipv6 address (didn't need the ipv6 adress, but its there if I want to play). The 192.168.1.100 is the ip address of the computer I'm using now.

Then I edited /etc/hosts.deny, it looks like this:

```
cat /etc/hosts.deny
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID
ALL : ALL

```

The ALL : ALL has to be in upper case, I tried mixing case and it didn't work. You should also hit return after the final ALL or it won't work. I got a no newline error with out the retrun. I used the auth log file to help troubleshoot the case and no return errors

```
cat /var/log/auth.log | grep ssh
```

After making the above changes if I try to log in from my server I get this:

```
user@Willy:~$ ssh minibuntu
ssh_exchange_identification: Connection closed by remote host
user@Willy:~$ 
```

So the subject of the experiment won't allow me to log in from my server, but I can still log in from the computer I'm using.

BTW the changes work right away without having to restart any services.

So just to review If i try to connect like this:

```
Home-->Server-->Minibuntu
```

It doesn't work because the server ip address is not in hosts.allow

```
Home-->Minibuntu
```

Does work because the Home ip address is in host.allow

Jim

---

### Post by NexusGS on 2008-10-05
:D

Solved!!!
I got my 2 hosts files as you mentioned and now it works!!

:popcorn:

Thanx sooooooo much everyone for your help! Thanx!!!!

:guitar:

---

