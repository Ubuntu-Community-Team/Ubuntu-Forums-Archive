---
title: "tftp issue"
date: 2008-06-26
forum: Server Platforms
---

### Post by rtsask on 2008-06-26
Hi I installed tftp server and this is my tftp file config:



service tftp
{
protocol        = udp
port            = 69
socket_type     = dgram
wait            = yes
user            = nobody
server          = /usr/sbin/in.tftpd
server_args     = /tftpboot
disable         = no
}
 

but when I try to get or put some files it gives me : Error code 2: Access violation

any idea on this?

thanks,

-Rouzbeh

---

### Post by RealPSL on 2008-06-26
If I remember well you need to use touch to create a 0 byte file first locally in the /tftpboot directory before you put a file of the same name remotely. Have you done this?

---

### Post by mynk on 2009-04-06
Hi,

I am trying to boot a board with Montavista kernel via tftp.

I am seeing the access violation error -

TFTP from server 10.91.25.109; our IP address is 10.91.25.231
Filename 'uImage'.
Load address: 0x80700000
Loading: *
TFTP error: 'Access violation' (2)

I see this issue on Intrepid. It works fine on Hardy. I created dummy filed in the tftp boot and gave the various locations for the uImage - none of it worked.

# cat /etc/inetd.conf
#<off># netbios-ssn	stream	tcp	nowait	root	/usr/sbin/tcpd	/usr/sbin/smbd
tftp		dgram	udp	wait	nobody	/usr/sbin/tcpd	/usr/sbin/in.tftpd /srv/tftp

This appears to be similar to the Hardy configuration. Am I missing something. Kindly advise.

---

### Post by HermanAB on 2009-04-06
If I recall correctly from my own battles with it, TFTP doesn't use any authentication and requires the directory permissions to be be read only, else it will refuse to do anything for security reasons.  So do a chmod -R -w on it and restart tftpd, then it should magically start to work.

---

### Post by mynk on 2009-04-08
Changed the permission and tried and it didn't help. Debugging further - will share if I find something.

---

### Post by zzz_tftp on 2009-04-14
sudo cat /etc/inetd.conf
#<off># netbios-ssn	stream	tcp	nowait	root	/usr/sbin/tcpd	/usr/sbin/smbd
#tftp		dgram	udp	wait	nobody	/usr/sbin/tcpd	/usr/sbin/in.tftpd /srv/tftp
tftp		dgram	udp	wait	nobody	/usr/sbin/tcpd	/usr/sbin/in.tftpd -s /tftpboot

notice the:
in.tftpd -s 

make it works, haha

---

### Post by dalei on 2010-05-12
1. Make sure the tftp root directory (default is /srv/tftp) has write permission to every one;
2. Make sure there is an existing file with same file name;
3. Make sure the file has write permission to every one.
The commands are (assume the file name is new.file):
```

sudo chmod a+wx /srv/tftp
touch /srv/tftp/new.file
chmod a+w /srv/tftp/new.file

```From the board (assume the server ip is 10.10.10.10):
```
tftp -p -l new.file 10.10.10.10
```
By the way, based on the source code, the service does not take any parameter, like "-s", except tftp root directory.

---

### Post by multiboot on 2010-12-22
dalei,

Many thanks! That was clear, concise and informative.

Not to mention it worked!

Thanks.

---

### Post by admiredone on 2011-01-04
I'm only able to tftp into localhost. When I try to connect using another host ie. QNX machine or U-BOOT TFTP will connect but it times out when I try to do any put/get to the ubuntu TFTP server. 

Any ideas? 

-JC

---

### Post by gruberator on 2012-06-27
Also make sure that in   /etc/xinetd.d/    there is only  one file which name begins with  tftp.

---

