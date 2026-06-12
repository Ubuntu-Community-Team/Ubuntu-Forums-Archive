---
title: "Cant access my website"
date: 2012-02-28
forum: Server Platforms
---

### Post by Pally1 on 2012-02-28
im not sure where else to go about this, but i have some extremely serious problem, we have ubuntu server 9.04 running that has all connections here forwarded through it. And for some insane reason, it seems to be blocking my website somehow, while i can access it fro my home computer or any other, but not ones that are part of this network that is forwarded through this server. Im not the guy who is administrating it, hes unavailable, but i really need to resolve this problem.

this is what i get in the logs:

eb 28 09:17:02 jp-d named[4499]: connection refused resolving 'ns1.atspace.me/A/IN': 82.197.131.11#53
Feb 28 09:17:02 jp-d named[4499]: connection refused resolving 'ns1.atspace.me/AAAA/IN': 82.197.131.11#53
Feb 28 09:17:02 jp-d named[4499]: connection refused resolving 'ns2.atspace.me/A/IN': 82.197.131.11#53
Feb 28 09:17:02 jp-d named[4499]: connection refused resolving 'ns2.atspace.me/AAAA/IN': 82.197.131.11#53
Feb 28 09:17:02 jp-d named[4499]: connection refused resolving 'ns1.atspace.me/A/IN': 82.197.130.11#53
Feb 28 09:17:02 jp-d named[4499]: connection refused resolving 'ns1.atspace.me/AAAA/IN': 82.197.130.11#53
Feb 28 09:17:02 jp-d named[4499]: network unreachable resolving 'b0.cctld.afilias-nst.org/A/IN': 2001:500:28::1#53
Feb 28 09:17:02 jp-d named[4499]: connection refused resolving 'ns2.atspace.me/A/IN': 82.197.130.11#53
Feb 28 09:17:02 jp-d named[4499]: connection refused resolving 'ns2.atspace.me/AAAA/IN': 82.197.130.11#53
Feb 28 09:17:02 jp-d named[4499]: connection refused resolving 'ns2.atspace.me/AAAA/IN': 82.197.130.11#53
Feb 28 09:17:02 jp-d named[4499]: connection refused resolving 'ns1.atspace.me/AAAA/IN': 82.197.130.11#53
Feb 28 09:17:03 jp-d named[4499]: connection refused resolving 'ns2.atspace.me/AAAA/IN': 82.197.131.11#53
Feb 28 09:17:03 jp-d named[4499]: connection refused resolving 'ns1.atspace.me/AAAA/IN': 82.197.131.11#53


I need to solve this as fast as possible, it is a matter of life and death :(

please help!

---

### Post by spynappels on 2012-02-28
It looks like there is a problem with your internal DNS, your DNS server appears to be refusing connections.

Did I understand that your site is available from the Internet, but not from the LAN?

If the site is the only site on the server, i.e. it is not set up using VirtualHosts, you could try accessing it just using the IP of the server on which the site is hosted.

---

### Post by Pally1 on 2012-02-28
This server does not host my site it has a different use, it is hosted on atspace. Its ip adress is 82.192.130.114, and i cant acces it to, server is blocking it.

I can access it from my computer at home or any other computer that is not part of this organisations network, which is forwarded through this server.

Is there anything that can be done to resolve this?

---

### Post by spynappels on 2012-02-28
I'm afraid not until the DNS problem is fixed as far as I know, sorry.

The only other option might be to add the IP address to a local hosts file with the URL so that a DNS lookup is not required.

Are the clients Linux or Windows? Which version?

---

### Post by Pally1 on 2012-02-28
This server is ubuntu 9.04, all workstations are running on windows.

How can i fix this dns issue? I began only 5 days ago, before that everything was working fine. This server works as dhcp server or something, ppl only keep some files on it and stuff, it does not host anything.

---

### Post by spynappels on 2012-02-28
I'm afraid I don't know enough about DNS to be of much use to you on this, my advice of a reboot may not be the correct one in a live environment.

Are the workstations running Windows XP or Vista or Win7?

---

### Post by HugoSerrano on 2012-02-28
Hello!
I'm not sure what happening, but you can try to add something like this on /etc/hosts file:
```
82.192.130.114 website.com
```

Regards!

---

### Post by spynappels on 2012-02-28
It looks like the problem is actually with atspace DNS servers, your best bet would be to open a support ticket with them to find out why DNS queries from your Ubuntu server's Public IP are being refused.

Can you also post the URL you are trying to access and I'll try and help you edit a hosts file on a workstation to see if that is a workaround.

---

### Post by spynappels on 2012-02-28
> **HugoSerrano said:**
> Hello!
I'm not sure what happening, but you can try to add something like this on /etc/hosts file:
```
82.192.130.114 website.com
```

Regards!

The workstations are running windows, do you mean adding it to the /etc/hosts on the server?

---

### Post by Pally1 on 2012-02-28
current domain adress is ru.j2psk.lv, i tried editing hosts on linux server, didnt do anything, i cant physicly change host on every workstation :D,  how is it possible that atspace is blocking access only from this place?

I cant even open atspace.com website from these computers.

---

### Post by spynappels on 2012-02-28
I don't know why they are doing that, you'll have to raise a ticket with them.

Do you want to try adding the URL and IP to a single Windows machine to see if that solves the problem?

This URL gives the instructions:
[http://www.windowsreference.com/windows-7/edit-hosts-file-in-windows-7-windows-vista/](http://www.windowsreference.com/windows-7/edit-hosts-file-in-windows-7-windows-vista/)

---

### Post by HugoSerrano on 2012-02-28
> **spynappels said:**
> The workstations are running windows, do you mean adding it to the /etc/hosts on the server?

Oh... windows... should be something like C:/windows/system32/drivers/etc/hosts

Don't remember the right folder... Anyway, this only should be done in one client to try to debug the problem.

To do this in server... it has to be dns server to LAN...

---

### Post by HugoSerrano on 2012-02-28
> **spynappels said:**
> I don't know why they are doing that, you'll have to raise a ticket with them.

Do you want to try adding the URL and IP to a single Windows machine to see if that solves the problem?

This URL gives the instructions:
[http://www.windowsreference.com/windows-7/edit-hosts-file-in-windows-7-windows-vista/](http://www.windowsreference.com/windows-7/edit-hosts-file-in-windows-7-windows-vista/)


Agree. Open a ticket.
Don't change hosts in every single machine. You will forget that and if server change IP, you will lost access to it again and lost one or two days until find that change!

Probably someone inside your network tried to login email, and fail the password 3 or 4 times and your IP get blocked by Brute force. If this it's true, changing hosts file will not work anyway...

---

### Post by Pally1 on 2012-02-28
althou you guys might be right, i thought its this servers fault, il talk to atspace, looks like im gonna change hosting provider. :)

---

### Post by SeijiSensei on 2012-02-28
I recommend [Linode]("http://www.linode.com/").

---

