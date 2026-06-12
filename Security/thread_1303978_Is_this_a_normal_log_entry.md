---
title: "Is this a normal log entry?"
date: 2009-10-28
forum: Security
---

### Post by JamesKube on 2009-10-28
Hi All,

Not sure what the below log entry is indicating (sure looks like "outbound" traffic to a remote desktop session to me...which would really suck since I neither authorized, nor initiated any remote desktop sessions, but being a noob, hopefully I'm wrong):

[LOG]
Oct 25 19:54:24 james-box kernel: [446124.507227] Outbound IN= OUT=eth0 SRC=192.168.1.149 DST=208.203.4.205 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=14020 DF PROTO=TCP SPT=57717 DPT=21 WINDOW=5840 RES=0x00 SYN URGP=0 
[/LOG]

There are several occurances of the above entry, some with different IP's. I've shutdown the box and am considering reformatting after creating an image for later "analysis".

Also, the box I'm currently using (another Ubunutu box) shows that my main account (account I'm currently logged in under) as:

**Never Logged in**

Is this a pretty sure sign that this box has also been compromised?

Thanks in advance,
James

---

### Post by JamesKube on 2009-10-28
Also, got the below from running 'netstat':

unix  3      [ ]         STREAM     CONNECTED     25311    
unix  3      [ ]         STREAM     CONNECTED     25309    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     25308    
unix  3      [ ]         STREAM     CONNECTED     25283    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     25282    
unix  3      [ ]         STREAM     CONNECTED     25275    @/tmp/.X11-unix/X0


...Is this normal?

---

### Post by gombadi on 2009-10-28
> 
Oct 25 19:54:24 james-box kernel: [446124.507227] Outbound IN= OUT=eth0 SRC=192.168.1.149 DST=208.203.4.205 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=14020 DF PROTO=TCP SPT=57717 DPT=21 WINDOW=5840 RES=0x00 SYN URGP=0


Destination is -
```

 dig +short -x 208.203.4.205
ftp.gateway.com.

```

DPT=21 indicates that it was an ftp connection from your machine to a remote ftp server. The nameservers for ftp.gateway.com look like they are from acer.com. Where you going to an acer.com site at the time?

---

### Post by unspawn on 2009-10-29
The most important parts:
Outbound # Iptables custom chain name
IN= # Inbound ethernet device name
OUT=eth0 # Outbound ethernet device name
DST=208.203.4.205 # Per previous reply resolves to "ftp.gateway.com"
PROTO=TCP # IP suite protocol TCP
SPT=57717 # Ephemeral source port, usually denotes user-initiated side of the connection
DPT=21 # Destination port, usually denotes service, see: 'getent services 21'
SYN # SYN denotes initializing a connection.


> **JamesKube said:**
> There are several occurances of the above entry, some with different IP's. I've shutdown the box and am considering reformatting after creating an image for later "analysis".
As long as the SYN traffic flow is from you -> to other servers that's OK (unless you say SSH into your machine from remote or publicly allow other services).


> **JamesKube said:**
> Also, the box I'm currently using (another Ubunutu box) shows that my main account (account I'm currently logged in under) as:
**Never Logged in**
Is this a pretty sure sign that this box has also been compromised?
It's odd but this 'lastlog' entry is not necessarily a sign of a breach of security. Depending on how much you log in per day running 'sudo last -n 30' should show them.


> **JamesKube said:**
> unix 3 [ ] STREAM CONNECTED 25309 @/tmp/.X11-unix/X0
If it's in use then running 'sudo /sbin/fuser -v /tmp/.X11-unix/X0' should return the process Id (PID) field, so running 'sudo /usr/sbin/lsof -Pwnp [returnedPID]' should show more information. By default this should belong to X11 / Xorg and the file is a socket. Again not a sign of a breach of security.


* While there's nothing wrong with the previous reply I think it's best to provide people with the default tools to use so they can find out things themselves. Self-reliance and such. HTH

---

### Post by JamesKube on 2009-10-30
Gombadi/Unspawn,

Thanks to both of you; Gombadi's on the money, I was actually searching for drivers for an old Gateway box (apparently Gateway was bought out by Acer back in 2007).

Unspawn, definitely appreciate the "teach a man to fish" mentality, best way to learn.  I feel fairly confident after reading both your and Gombadi's posts, and running the suggested commands, just a little taken aback in regard to how many returns I've gotten for the below command...if you're monitoring this thread and get the chance I'd appreciate any insight you ight have into the return from my 'lsof' command (I've reviewed the results and nothing pops out to me of the bat, but I'm not sure that I would know a 'bad' entry from a normal, still learning).  

Regardless, thanks to you both!

```

james@laptop:~$ sudo lsof -Pwnp 3220
COMMAND  PID USER   FD   TYPE             DEVICE    SIZE       NODE NAME
Xorg    3220 root  cwd    DIR                8,5    4096    2891782 /etc/X11
Xorg    3220 root  rtd    DIR                8,5    4096          2 /
Xorg    3220 root  txt    REG                8,5 1901872    4096020 /usr/bin/Xorg
Xorg    3220 root  DEL    REG                0,9            2490392 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9            2392087 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9            2359318 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9            2326549 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9             458763 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9            2293780 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9            2261011 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9            2228242 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9            2195472 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9            2162703 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9             589834 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9             393225 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9             360456 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9             327687 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9             294918 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9             262149 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9             229380 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9             196611 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9             163842 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9             131073 /SYSV00000000
Xorg    3220 root  mem    REG                8,5   51616    1402031 /lib/libnss_files-2.9.so
Xorg    3220 root  mem    REG                8,5   43472    1402033 /lib/libnss_nis-2.9.so
Xorg    3220 root  mem    REG                8,5   97168    1402028 /lib/libnsl-2.9.so
Xorg    3220 root  mem    REG                8,5   35632    1402029 /lib/libnss_compat-2.9.so
Xorg    3220 root  mem    REG                8,5   56056    4186879 /usr/lib/xorg/modules/input/synaptics_drv.so
Xorg    3220 root  mem    REG                8,5   37416    4186876 /usr/lib/xorg/modules/input/evdev_drv.so
Xorg    3220 root  mem    CHR              226,0               8192 /dev/dri/card0
Xorg    3220 root  mem    REG                8,5  169968    4097840 /usr/lib/libexpat.so.1.5.2
Xorg    3220 root  mem    REG                8,5 2497384    4112518 /usr/lib/dri/r300_dri.so
Xorg    3220 root  mem    REG                0,0               7067 /sys/devices/pci0000 (stat: No such file or directory)
Xorg    3220 root  mem    REG                8,5   72528    4186823 /usr/lib/xorg/modules/libexa.so
Xorg    3220 root  mem    REG                8,5  134032    4186824 /usr/lib/xorg/modules/libfb.so
Xorg    3220 root  mem    REG                8,5  150072    4186825 /usr/lib/xorg/modules/libint10.so
Xorg    3220 root  mem    REG                8,5   27592    4186829 /usr/lib/xorg/modules/libvgahw.so
Xorg    3220 root  mem    REG                8,5  658224    4186853 /usr/lib/xorg/modules/drivers/radeon_drv.so
Xorg    3220 root  mem    REG                8,5   10440    4186872 /usr/lib/xorg/modules/extensions/libdri2.so
Xorg    3220 root  mem    REG                8,5   43216    4097794 /usr/lib/libdrm.so.2.4.0
Xorg    3220 root  mem    REG                8,5   43688    4186871 /usr/lib/xorg/modules/extensions/libdri.so
Xorg    3220 root  mem    REG                8,5   31144    4186875 /usr/lib/xorg/modules/extensions/librecord.so
Xorg    3220 root  mem    REG                8,5  421984    4186874 /usr/lib/xorg/modules/extensions/libglx.so
Xorg    3220 root  mem    REG                8,5   18744    4186870 /usr/lib/xorg/modules/extensions/libdbe.so
Xorg    3220 root  mem    REG                8,5  106016    4186873 /usr/lib/xorg/modules/extensions/libextmod.so
Xorg    3220 root  mem    REG                8,5   96560    1400893 /lib/libgcc_s.so.1
Xorg    3220 root  mem    REG                8,5 1023448    4098468 /usr/lib/libstdc++.so.6.0.10
Xorg    3220 root  mem    REG                8,5  658840    4098437 /usr/lib/libsmbios.so.2.1.0
Xorg    3220 root  mem    REG                8,5  547024    4098169 /usr/lib/libfreetype.so.6.3.20
Xorg    3220 root  mem    REG                8,5   96768    1400989 /lib/libz.so.1.2.3.3
Xorg    3220 root  mem    REG                8,5 1502512    1400938 /lib/libc-2.9.so
Xorg    3220 root  mem    REG                8,5   31656    1402038 /lib/librt-2.9.so
Xorg    3220 root  mem    REG                8,5  542928    1402025 /lib/libm-2.9.so
Xorg    3220 root  mem    REG                8,5 1594824    1400853 /lib/libcrypto.so.0.9.8
Xorg    3220 root  mem    REG                8,5  325120    1400855 /lib/libssl.so.0.9.8
Xorg    3220 root  mem    REG                8,5   19640    4097594 /usr/lib/libXdmcp.so.6.0.0
Xorg    3220 root  mem    REG                8,5  248440    1400898 /lib/libdbus-1.so.3.4.0
Xorg    3220 root  mem    REG                8,5   67808    4096872 /usr/lib/libhal.so.1.0.0
Xorg    3220 root  mem    REG                8,5  282200    4098332 /usr/lib/libpixman-1.so.0.13.2
Xorg    3220 root  mem    REG                8,5   27032    4097852 /usr/lib/libfontenc.so.1.0.0
Xorg    3220 root  mem    REG                8,5   10288    4097583 /usr/lib/libXau.so.6.0.0
Xorg    3220 root  mem    REG                8,5  270896    4097600 /usr/lib/libXfont.so.1.4.1
Xorg    3220 root  mem    REG                8,5  130151    1402036 /lib/libpthread-2.9.so
Xorg    3220 root  mem    REG                8,5   14608    1402024 /lib/libdl-2.9.so
Xorg    3220 root  mem    REG                8,5   26872    4098322 /usr/lib/libpciaccess.so.0.10.2
Xorg    3220 root  mem    REG                8,5  135680    1400881 /lib/ld-2.9.so
Xorg    3220 root  DEL    REG                0,9              98304 /SYSV00000000
Xorg    3220 root  mem    CHR                1,1                707 /dev/mem
Xorg    3220 root  DEL    REG                0,9             524301 /SYSV00000000
Xorg    3220 root  DEL    REG                0,9             491532 /SYSV00000000
Xorg    3220 root  mem    REG                0,0               7068 /sys/devices/pci0000 (stat: No such file or directory)
Xorg    3220 root    0r   REG                8,5   39073    3883072 /var/log/Xorg.0.log
Xorg    3220 root    1u  unix 0xffff8800ad847b80               7829 socket
Xorg    3220 root    2u   REG                8,5    4636    3900171 /var/log/gdm/:0.log
Xorg    3220 root    3r  unix 0xffff8800ad33bb80               7830 /tmp/.X11-unix/X0
Xorg    3220 root    4w   REG                8,5   29902    5472257 /usr/lib/xorg/protocol.txt
Xorg    3220 root    5w   CHR                4,7                716 /dev/tty7
Xorg    3220 root    6w   REG                0,3       0 4026531909 /proc/mtrr
Xorg    3220 root    7r  unix 0xffff8800aed8e000               7900 socket
Xorg    3220 root    8w   REG                0,0     256       7065 /sys/devices/pci0000:00/0000:00:01.0/0000:01:05.0/config
Xorg    3220 root    9u   REG                0,3       0 4026531909 /proc/mtrr
Xorg    3220 root   10r   CHR              226,0               8192 /dev/dri/card0
Xorg    3220 root   11u   CHR              226,0               8192 /dev/dri/card0
Xorg    3220 root   12u  unix 0xffff8800a74a8000               9179 socket
Xorg    3220 root   13u   CHR              13,69               1200 /dev/input/event5
Xorg    3220 root   14u   CHR              13,70               4294 /dev/input/event6
Xorg    3220 root   15u   CHR              13,68               1807 /dev/input/event4
Xorg    3220 root   16u   CHR              13,72               4915 /dev/input/event8
Xorg    3220 root   17u  unix 0xffff8800a74a8840               9186 socket
Xorg    3220 root   18u  unix 0xffff8800a1830000              10636 socket
Xorg    3220 root   19u  unix 0xffff8800a1831340              10652 socket
Xorg    3220 root   20u  unix 0xffff8800a19542c0              10878 socket
Xorg    3220 root   21u  unix 0xffff8800a1954840              10886 socket
Xorg    3220 root   22u  unix 0xffff8800a1955340              10912 socket
Xorg    3220 root   23u  unix 0xffff8800a00d42c0              11097 socket
Xorg    3220 root   24u  unix 0xffff8800a015c2c0              11953 socket
Xorg    3220 root   25u  unix 0xffff8800a015cb00              11958 socket
Xorg    3220 root   26u  unix 0xffff88009e840580              12067 socket
Xorg    3220 root   27u  unix 0xffff88009257adc0              91586 socket
Xorg    3220 root   28u  unix 0xffff88009e841600              12171 socket
Xorg    3220 root   29u  unix 0xffff88009eb7e2c0              12332 socket
Xorg    3220 root   30u  unix 0xffff88009eb7e840              12336 socket
Xorg    3220 root   31u  unix 0xffff88009bd03340              12972 socket
Xorg    3220 root   32u  unix 0xffff88009d532dc0              12446 socket
Xorg    3220 root   33u  unix 0xffff88009d5322c0              12545 socket
Xorg    3220 root   34u  unix 0xffff88009bd03600              12980 socket
Xorg    3220 root   35u  unix 0xffff88009d6f1600              12985 socket
Xorg    3220 root   36u  unix 0xffff88009a062840              13414 socket
Xorg    3220 root   37u  unix 0xffff8800910e7340             110284 socket
Xorg    3220 root   38u  unix 0xffff88009a1782c0              17347 socket
Xorg    3220 root   39u  unix 0xffff88009a174000              17843 socket
Xorg    3220 root   40u  unix 0xffff8800976b9600              17864 socket
Xorg    3220 root   41u  unix 0xffff88009241d8c0              17987 socket
Xorg    3220 root   42u  unix 0xffff8800910e6b00             110288 socket
Xorg    3220 root   43u  unix 0xffff8800911d0000             481105 socket
Xorg    3220 root   44u  unix 0xffff8800910e7b80             481536 socket
Xorg    3220 root   45u  unix 0xffff880097400000             483612 socket
Xorg    3220 root   46u  unix 0xffff880097400840             483620 socket
Xorg    3220 root   47u  unix 0xffff88006ece18c0             483642 socket

```

---

