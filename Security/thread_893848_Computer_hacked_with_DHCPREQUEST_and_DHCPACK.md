---
title: "Computer hacked with DHCPREQUEST and DHCPACK?"
date: 2008-08-18
forum: Security
---

### Post by jonwe195 on 2008-08-18
Hi,

I've made a huge mistake connecting my computer to the internet without a router and/or softare firewall. I'm running kubuntu with KDE 4. After a while I realized my computer was running really slowly and so I turned it off. While logging off I had a message telling me that a computer with a particular IP adress was logged on to one of my users. This was weird, and after having restarted my computer I found the following in my /var/log/auth.log:

```
Aug 18 20:29:25 *computerName* sshd[19610]: reverse mapping checking getaddrinfo for 79-117-132-172.rdsnet.ro [79.117.132.172] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 18 20:29:26 *computerName* sshd[19610]: Accepted password for *userName* from 79.117.132.172 port 2727 ssh2
Aug 18 20:29:26 *computerName* sshd[19619]: pam_unix(sshd:session): session opened for user *userName* by (uid=0)
Aug 18 20:29:40 *computerName* passwd[19721]: pam_unix(passwd:chauthtok): password changed for *userName*
```

While looking in my /var/log/syslog I find lots of DHCPREQUEST and DHCPACK from some computer:

```
Aug 18 20:48:00 *computerName* dhclient: DHCPREQUEST of <null address> on eth0 to 172.17.0.10 port 67
Aug 18 20:48:00 *computerName* dhclient: DHCPACK of 85.8.1.155 from 172.17.0.10
Aug 18 20:48:00 *computerName* NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Aug 18 20:48:00 *computerName* dhclient: bound to 85.8.1.155 -- renewal in 422 seconds.
```

and after the break-in there's lots of sshf segfaults:

```
Aug 18 20:49:03 *computerName* kernel: [ 6809.845216] sshf[21194]: segfault at 00000000 eip 08048e33 esp bfff4120 error 4
Aug 18 20:49:03 *computerName* kernel: [ 6809.990998] sshf[21335]: segfault at 00000000 eip 08048e33 esp bfff4120 error 4
Aug 18 20:49:03 *computerName* kernel: [ 6810.017128] sshf[21272]: segfault at 00000000 eip 08048e33 esp bfff4120 error 4
Aug 18 20:49:03 *computerName* kernel: [ 6810.031169] sshf[21376]: segfault at 00000000 eip 08048e33 esp bfff4120 error 4
```

So, if there's anyone who can give me any hints on what's been going on that would be really nice. I'm not so worried about any fiels on my computer, I don't have anything of importance, but it wouldn't be fun if someone stole my e-mail and other login info. The user that was hacked was only a member of its own group, i.e. not an admin or anything. There seems to be no sudo commands during the period of the hacking (except the ones issued by myself), but is there mabye a risk of the hacker having deleted those entries from the logs?

Any help/guidance on this matter is greatly appreciated!

---

### Post by The Tronyx on 2008-08-19
Initially I wanted to say that someone launched some kind of overflow attack against your ssh but that was mostly because I think they are cool.

After looking at what little snippets of the logs you have provided...
> 
Aug 18 20:29:25 computerName sshd[19610]: reverse mapping checking getaddrinfo for 79-117-132-172.rdsnet.ro [79.117.132.172] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 18 20:29:26 computerName sshd[19610]: Accepted password for userName from 79.117.132.172 port 2727 ssh2
Aug 18 20:29:26 computerName sshd[19619]: pam_unix(sshd:session): session opened for user userName by (uid=0)
Aug 18 20:29:40 computerName passwd[19721]: pam_unix(passwd:chauthtok): password changed for userName

That is someone trying to establish an SSH connection from an ISP (in Romania) that does not support reverse DNS lookups.

> 
Aug 18 20:48:00 computerName dhclient: DHCPREQUEST of <null address> on eth0 to 172.17.0.10 port 67
Aug 18 20:48:00 computerName dhclient: DHCPACK of 85.8.1.155 from 172.17.0.10
Aug 18 20:48:00 computerName NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Aug 18 20:48:00 computerName dhclient: bound to 85.8.1.155 -- renewal in 422 seconds.
That is you getting your IP address (in Sweden).  The login happened 20 minutes prior to the DHCP dialog so this may be immaterial.

As for the SSH segfaults, it's hard to tell what caused them without more info from the logs, maybe the force quit, maybe an exploit (though I am not sure why seeing as how someone already changed your password) who knows.  If you have the logs, feel free to post them here or if you are concerned about your privacy, you can send me a private message on the forums.

To summarize, what I see is, you get an IP address, your SSH has some hiccups and 20 minutes earlier, someone changes your password.

---

### Post by cariboo on 2008-08-19
It looks like you have been hacked, obviously one of your uses had a name that was in a dictionary attack and an easy password to crack. Time to do a complete reinstall. Next time don't make user names so easy to guess and use strong passwords. See this link:

[http://www.linux.com/articles/28057](http://www.linux.com/articles/28057)

If you need port 22 open, use something like denyhosts. I have it set to block an ip address after 3 attempts to break in.

Jim

---

### Post by hyper_ch on 2008-08-19
just out of curiosity: Did you regurarly update your system? There was a ssh security update a few weeks back.

---

### Post by Martin von Wittich on 2008-09-08
> **hyper_ch said:**
> just out of curiosity: Did you regurarly update your system? There was a ssh security update a few weeks back.

This is most probably not a sshd weakness, but just a dictionary-crackable password on the cracked user account.

---

