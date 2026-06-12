---
title: "ipmi_si module on Ubuntu Server 6.06 AMD64"
date: 2007-01-09
forum: Server Platforms
---

### Post by drinky76 on 2007-01-09
Hi all

Hopefully someone can help me.

I am setting up some Ubuntu servers using Dapper Server AMD64 with kernel 2.6.15-26-amd64-server. These server will be co-located and so we purchased Supermicro PDSMI+ servers with 64bit Xeons and [Supermicro AOC-IPMI20-E]("http://www.supermicro.com/products/accessories/addon/AOC-IPMI20-E.cfm") IPMI baseboard management controllers for serial over LAN console support and remote power cycling.

As per the Supermicro docs I have used their utility to upload the firmware and give the BMC a unique IP address and a MAC address taken from the IPMI slot on the motherboard.

Ok thats all of the background self-justification out of the way...

The problem I have is that I am unable to load the ipmi_si kernel module which is required for IPMI support.

I am using the following documents:

[http://buttersideup.com/docs/howto/IPMI_on_Debian.html]("http://buttersideup.com/docs/howto/IPMI_on_Debian.html")
[http://www.ecst.csuchico.edu/~dranch/LINUX/IPMI/ipmi-on-linux.html]("http://www.ecst.csuchico.edu/~dranch/LINUX/IPMI/ipmi-on-linux.html") (not the same motherboard).
[The Supermicro docs (via FTP)]("ftp://ftp.supermicro.com/CDR-0010_2.03_for_IPMI_Server_Managment/Manuals/")

I can modprobe ipmi_msghandler and ipmi_devintf cleanly, however ipmi_si won't load, including with options specified in some of the above documents:

root@ns0:~# modprobe ipmi_si
FATAL: Error inserting ipmi_si (/lib/modules/2.6.15-26-amd64-server/kernel/drivers/char/ipmi/ipmi_si.ko): No such device
root@ns0:~# modprobe ipmi_si type=kcs
FATAL: Error inserting ipmi_si (/lib/modules/2.6.15-26-amd64-server/kernel/drivers/char/ipmi/ipmi_si.ko): No such device
root@ns0:~# modprobe ipmi_si type=kcs ports=0xca8
FATAL: Error inserting ipmi_si /lib/modules/2.6.15-26-amd64-server/kernel/drivers/char/ipmi/ipmi_si.ko): No such device
root@ns0:~# modprobe ipmi_si type=kcs ports=0xca8 si_regspacings=4
FATAL: Error inserting ipmi_si (/lib/modules/2.6.15-26-amd64-server/kernel/drivers/char/ipmi/ipmi_si.ko): Unknown symbol in module, or unknown parameter (see dmesg)

From /var/log/kernel.log
Jan  9 12:24:55 ns0 kernel: [ 3633.858808] IPMI System Interface driver.
Jan  9 12:24:55 ns0 kernel: [ 3633.858849] ipmi_si: Trying "kcs" at I/O port 0xca2
Jan  9 12:24:55 ns0 kernel: [ 3633.877471] ipmi_si: Trying "smic" at I/O port 0xca9
Jan  9 12:24:55 ns0 kernel: [ 3633.889584] ipmi_si: Trying "bt" at I/O port 0xe4
Jan  9 12:24:55 ns0 kernel: [ 3633.901701] ipmi_si: Unable to find any System Interface(s)
Jan  9 12:25:01 ns0 kernel: [ 3639.462813] IPMI System Interface driver.
Jan  9 12:25:01 ns0 kernel: [ 3639.462854] ipmi_si: Trying "kcs" at I/O port 0xca2
Jan  9 12:25:01 ns0 kernel: [ 3639.481338] ipmi_si: Trying "smic" at I/O port 0xca9
Jan  9 12:25:01 ns0 kernel: [ 3639.493513] ipmi_si: Trying "bt" at I/O port 0xe4
Jan  9 12:25:01 ns0 kernel: [ 3639.505688] ipmi_si: Unable to find any System Interface(s)
Jan  9 12:25:09 ns0 kernel: [ 3647.529000] IPMI System Interface driver.
Jan  9 12:25:09 ns0 kernel: [ 3647.529003] ipmi_si: Trying "kcs" at I/O port 0xca8
Jan  9 12:25:09 ns0 kernel: [ 3647.550710] ipmi_si: Unable to find any System Interface(s)
Jan  9 12:25:22 ns0 kernel: [ 3660.250967] ipmi_si: Unknown parameter `si_regspacings'

Clutching at straws, I found [this openipmi bug]("http://www.mail-archive.com/openipmi-developer@lists.sourceforge.net/msg00227.html") and tried the suggested pnpacpi=off boot option but it made no difference.

dmidecode shows the following:

Handle 0x001C, DMI type 38, 18 bytes.
IPMI Device Information
        Interface Type: KCS (Keyboard Control Style)
        Specification Version: 2.0
        I2C Slave Address: 0x10
        NV Storage Device: Not Present
        Base Address: 0x0000000000000CA8 (I/O)
        Register Spacing: 32-bit Boundaries

So, according to [this post]("http://lists.us.dell.com/pipermail/linux-poweredge/2006-June/026149.html") on the Dell linux-poweredge list, I should change the ports parameter to the base address reported by dmidecode, 0xca8, however, this also does not work.

There is an interesting document at [http://openipmi.sourceforge.net/IPMI.txt]("http://openipmi.sourceforge.net/IPMI.txt") , however I'm not sure which parameters to pass with which values.

Does anyone have any ideas? These machines are largely pointless without the IPMI facility.

I would also like to cross-post this to x86 64-bit Users in case the architecture has any relevence. Any ideas on how to do this without duplicating threads?

---

### Post by drinky76 on 2007-01-09
Hi

I'm sorry to look like an idiot, but after struggling with this for a week, I found the answer 5 minutes after posting.

In most of my examples, the modprobe parameters were for 2.4 kernels, the actual parameters should be as follows:

modprobe ipmi_si type=kcs ports=0xca8 regspacings=4

And everything should swim along nicely.

---

### Post by honmanm on 2007-01-14
Not so dumb, I think... your note has saved me a couple of days' hair-tearing!

---

### Post by drinky76 on 2007-01-30
Good :) I'm glad it helped you.

I wrote a howto [here]("http://wiki.adamsweet.org/doku.php?id=ipmi_on_linux") just in case you or anyone else needs further advice :)

---

