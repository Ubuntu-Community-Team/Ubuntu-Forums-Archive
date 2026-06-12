---
title: "Problem with large file transfers"
date: 2006-08-29
forum: Server Platforms
---

### Post by ispmarin on 2006-08-29
Hello everybody. I am facing a strange problem with my network: When I
try to transfer a large fil (larger than 10MB), the transfer stalls,
but the connection is not dropped. I tried sftp, scp and ftp. ping and
a normal ssh conection does not shows any problems. The setup is as
follows:

ubuntu dapper box -> cat6 cable -> 3Com switch(24 ports, large
backplane) -> cat6 cable (~90m) -> 3Com switch (8 ports, small
backplane) -> debian box(3.1). and vice-versa

The cables, when tested with a connection tester, says that the
connection is ok and with Giga link. I already replaced the connectors
on both ends of the cable.

Any clues?

Thank you.

---

### Post by jimm on 2006-08-29
Not sure... Might be completly leading you up the garden path... 

But it sounds like it could be an ethernet window size issue (or something like that). From memory... I had this once before and I found that one of the switches in the chain was buffering data and re-transmitting with a different size window. The effect was that when the switch buffer filled up the transfer stalled or fell over. 

The only thing that makes me wary of that as a solution is that I had the problem years ago on much older and dodgyer gear than you are using! Worth checking out though.

I have seen something like this on one other ocassion to but I can't for the life of me remember what it was! Helpful eh? I'll have a good think and see if I can remember and re-post!#

Thanks,
James

---

### Post by chrisfay on 2006-08-29
If problems stem from using FTP try changing your client to 'PASV' rather than 'PORT' file transfer. I was having trouble with big file transfers as my ftp server kept timing out midway. I found that the problem had to do with my network routing regarding the data port and switching to pasv solved the problem. You can find more info out here:

[http://www.ncftp.com/ncftpd/doc/misc/ftp_and_firewalls.html](http://www.ncftp.com/ncftpd/doc/misc/ftp_and_firewalls.html)

> Since the FTP protocol uses two connections, a control connection for communicating with the client, and another connection to transfer data, there is twice the probability of getting timed-out by an impatient firewall.  The most common instance of this problem occurs during a long file transfer.  When a transfer is initiated (on the control connection), the control connection is idle until the transfer (on the data connection) finishes.  If the routing device does not make a special case for the FTP protocol and the data connection takes longer than the routing device's idle timeout, then the control connection will be timed out.

---

### Post by ispmarin on 2006-08-29
Well, James, anyway this is helpfull... I will try to see if any of the two switchs are giving me trouble, but I tested without both and worked fine. Also, copy large files via the 3Com robust switch shows no problems between the ubuntu boxes in the same network... but I will give it a try.
And no, this is not ftp exclusive, this is scp, sftp, ftp... maybe the same problem for different protocols?

---

### Post by jimm on 2006-08-30
Hi again,

Have you looked at the switches to see if you are getting any errors on the way through?

Is it only the Debian box at the other end that is having problems? Do other machines work okay?

TCPDump or Ethereal at either end might help see what is going on as well...

Thanks,
James

---

### Post by dannyboy79 on 2006-08-30
When you hook up a switch to a switch I believe you have to use a cross-over cable if your switches are being hooked together using the uplink port? is that correct? I was asking this same questions to a colleage today and that's what he told me. I told him that I have a router and then a switch and he said that each device has 2 ports or whatever you want to call them, RX and TX and when you hook a computer to a switch, they are opposite and that's what you need, RX to TX and TX to RX, well when you hook up a switch to a switch then you'll have TX to TX and RX to RX which won't work very good!!! I may be way off here but that's what this other guy told me. So he told me to use a cross over cable to connect the switch and my router, i believe he said to use the uplink plug on the switch. I often trust my colleage but who knows?

---

### Post by ispmarin on 2006-09-02
For switch - switch and the end connections, the cables must be direct, not reversed. Only when you have pc-pc is needed the reversed cable. 
Anyway, I finally nailed down the problem: a faulty net card. sight. Just the new gigabyte new one...

Thanks everybody.

---

### Post by dannyboy79 on 2006-09-05
I am sorry but you are wrong, I have read this here at this website, [http://www.homenethelp.com/web/explain/about-ethernet-crossover.asp](http://www.homenethelp.com/web/explain/about-ethernet-crossover.asp) if your switch has an uplink port than you are correct, you don't need a cross over cable. One normal cat5 cable end would plug into a normal port on switch or router and one end would have to plug into a UPLINK port which has it's port reveresed. If you have a cross over cable and your switch or router don't have a UPLINK port than you can simply go normal port to normal port.

---

### Post by sysops on 2006-09-05
The rules for determining whether or not to use a normal and X-over cable are quite simple

For Like-hosts to Like-Hosts use X-over
For Unlike-Hosts to Unlike-Hosts use Straight

So, PC-to-PC would require X-over, switch-to-switch would require X-over, Hub-to-hub X-over etc. PC-to-Switch=normal, pc-to-hub=normal ,etc. However, somevendors nowadays allow to use either or i.e. the ports on the switches/hubs/SOHO routers will autodetect the type of cable and switch over to accomodate either/or.

It would seem to me that the lags are caused by either of these

1. Duplex settings -- make sure all NICs along the path are either full-duplex or half-duplex, the former allowing for better rates.

2. Buffer sizes - Make sure that the RX/TX buffers for the NICs are sufficiently sized - 64K should suffice.

3. Cache/Memory/CPU load - Make sure your systems arent undergoing anything rigourous whilse performing the transfers, something processor/memory intensive can slow the Xfers down significantly.

---

### Post by dannyboy79 on 2006-09-05
sysops, thank you for your advice but can you please elaborate on HOW to check and make sure each of those things is ok. For example, I wouldn't have any clue how to make sure that all my nics are set to all full or all half duplex etc etc. Thank you if you could do that.

---

