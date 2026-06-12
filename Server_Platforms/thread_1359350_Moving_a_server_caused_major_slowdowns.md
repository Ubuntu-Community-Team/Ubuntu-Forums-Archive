---
title: "Moving a server caused major slowdowns?"
date: 2009-12-19
forum: Server Platforms
---

### Post by trillex on 2009-12-19
Hello,

I recently moved my server from one location to another and suddenly find myself with a very slow file transfer (Through Samba). When I say slow, I mean ranging from 30 to 150 kbytes/s. 

The server have seen little to no changes in it in the last couple of months - especially that could be related to network or Samba. The network is different here, however, but I hardly see how it can affect it. In my old place, we had the server connected to a standard 100 mbit switch, while here, we have connected it to a standard 4 port router with wifi. The client trying to transfer is using wireless together with Windows 7. Normally, it is used to stream music or videos (Mediaserver, to some extend) but I am even unable to listen to music without severe skips. 

I am tempted to think that it actually sends it over the internet instead of internally, which certainly would explain that excact transfer rates (I got 2 mbit/2 mbit) but why would it do that and how to avoid it? We are both on the same internal network (192.168.0.0/24).

I am not very hardcore when it comes to troubleshooting network on a linux server - especially when it is hard to figure out where exactly the issue is. A look at the samba log just shows the standard CUPS issue, which I just fixed. No dice there either.

---

### Post by trillex on 2009-12-19
Tested it a bit more and it is definetly sending it over the internet. Tried another network interface so I doubt the error is to be found there.

---

### Post by linuxfrance on 2009-12-19
verify , the speed of both ,your network card , and the switch port 
if they are auto , try to force them to 100 for exaple , both sides must be the same

---

### Post by trillex on 2009-12-19
Both going at 100 mbit.

---

### Post by trillex on 2009-12-19
And fixed. I updated from 9.04 to 9.10. Something got changed and it is now working.

---

### Post by trillex on 2009-12-20
Not fixed. It's faster than before but it is going at around 500 to 1500 kbytes/s. I have also checked on a FTP connection but it's the same thing, which means Samba isn't the issue.

---

### Post by dunix on 2009-12-20
You seem to be assuming it's a network related issue, but have you verified that your drives were not damaged during the move?

---

