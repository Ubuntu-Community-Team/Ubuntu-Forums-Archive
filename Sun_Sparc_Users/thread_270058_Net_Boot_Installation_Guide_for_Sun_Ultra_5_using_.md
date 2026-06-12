---
title: "Net Boot Installation Guide for Sun Ultra 5 using a windows box running RARP and TFTP"
date: 2006-10-02
forum: Sun Sparc Users
---

### Post by Paul Miners on 2006-10-02
1. Download and install a RARP server on the windows box
I use [[http://www.panix.com/~perin/rarpd.zip]](http://www.panix.com/~perin/rarpd.zip])

2. Download and install a TFTP server on the windows box
I use [[http://tftpd32.jounin.net]](http://tftpd32.jounin.net])

3. Download the ubuntu netboot image 
This can be found at [[http://ports.ubuntu.com/ubuntu-ports/dists/dapper/main/installer-sparc/current/images/sparc64/netboot/2.6/boot.img]](http://ports.ubuntu.com/ubuntu-ports/dists/dapper/main/installer-sparc/current/images/sparc64/netboot/2.6/boot.img])

4. Ensure that both the windows box and the Ultra 5 are connected to the same network. In the example the network is 192.168.1.X. and I have reserved 192.168.1.110 as the Ultra 5 IP address.

5. Convert the above chosen IP address into hexadecimal make a note of it.
I use this tool to do this for me [[http://www.kloth.net/services/iplocate.php]](http://www.kloth.net/services/iplocate.php])
*example:* 192.168.1.110 = C0A8016E

5. Setup the RARP server on the Windows box to assign whatever IP you choose (*example* 192.168.1.110). If you use the RARP server described in step 1 then all you need to do is create a file in the same directory as rarpd.exe named rarpd.tbl and insert aa.bb.cc.dd.ee.ff 192.168.1.110 where aa.bb.cc.dd.ee.ff is the MAC address of the Ultra 5 and 192.168.1.10 is the chosen IP address.
If you need to identify the Ultra 5 MAC address then type "boot net" from the OBP and it will display the MAC address.

6. Setup the TFTP server on the Windows box. If you use the TFTP server described in step 2 then select 'Settings' and set the 'Base Directory'. This can be any directory of your choosing.
*example:* c:\tftpboot

7. Now just place the downloaded boot image file [boot.img] into of the above chosen 'Base Directory' and rename it to the converted hex value.
*example:* boot.img renamed as C0A8016E

8. Ensure rarpd.exe and tftpd32.exe are running on the windows box.

9. Start the Ultra 5 and type at the boot prompt:

boot net

The sparc should now boot!

I select ati when promped for video card. This should be selected if you use the onboard video.

---

### Post by netztier on 2006-10-03
Short, quick and concise. Cool. That should go into the HOWTOs and/or into [USDF]("http://doc.gwos.org/index.php/Main_Page") immediately. This all should also work for netbooting other Sun Ultra machines.

Can you add a few more tags such as "rarp", "tftp", "netboot" to facilitate finding the article by searching for it?

---

### Post by torches on 2006-10-03
I agree with netztier. I was trying to install ubuntu on via CDROM and failed until I used this method. but I used a solaris box since the windows box I had at work had a firewall rule (can't disable) that prevented tftp. 

Excellent job.

BTW, It would be nice if we could have a page in here where people can link to their installation successes of different Sun workstations/ servers, something similar the [linux on laptops]("http://www.linux-laptop.net/")

---

