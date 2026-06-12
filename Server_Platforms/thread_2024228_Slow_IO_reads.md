---
title: "Slow I/O reads"
date: 2012-07-13
forum: Server Platforms
---

### Post by peppyuk on 2012-07-13
Hi all, I'm very new to linux. For a little bit of fun last year I set up a Ubuntu server under the desk to see what it could/would do. So for the last 7 months of so it's been happily running samba, vsftpd and a couple of wordpress sites. I access the server using ssh with putty and keep it upto date. A couple of weeks ago I went to copy some files from one PC to another, at which point I just copy them onto the network drive, and copy them off again to the other PC. Coping to the network drive is fine, transfers at around 30MB but when I tried to copy them back off onto another PC it showed transfer of 28KB, I left it for a while but it didn't finish. I also have the same trouble when I try and use the ftp server, can copy to the server just fine, but reading the files again is very slow. Wordpress also behaves in the same manner, although it doesn't seem so bad as I don't move large files.
 
I had a search about on the 'net and found some things about the network drivers not working on the realtek ports. so I follow a couple of 'how tos' to remove the r8169 driver and install the r8168 driver. This hasn't helped. If I check 'top' or 'iostat' the server is pretty much idle.
 
What do I do next?
 
TIA

---

### Post by useufxix on 2012-09-30
Check if link negotiation went well, with
# sudo mii-tool

If your NIC link state is wrong renegotiate, with
# sudo mii-tool -r

Check again to see if it helped, with
# sudo mii-tool

---

