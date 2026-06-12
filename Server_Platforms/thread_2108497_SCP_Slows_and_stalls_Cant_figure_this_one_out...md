---
title: "SCP Slows and stalls? Cant figure this one out.."
date: 2013-01-24
forum: Server Platforms
---

### Post by Folfin on 2013-01-24
Hi everyone, I am new here, and fairly new to Linux, so I apologize for my ignorance.

 I just put together a new server on an older computer and I have ssh, sshfs and scp all working. It works brilliant over the internal network (4.5-6 MB/s) but when I try to scp a file (as large as a movie) it slows to around 120 kb/s and stalls intermittently. It will eventually get through the file, but its almost not worth using if it goes that slow.

I am using Ubuntu 12.04 on both machines. I understand this is kind of a common problem but I have not figured out how to fix it. Can anyone help?

Thanks in advance!

---

### Post by tgalati4 on 2013-01-24
Run iperf on each machine and post the results:

On one machine run:
```
iperf -s
```

Then on the other machine run:

tgalati4@tubuntu2:~$  iperf -c 192.168.1.162 -w 1024k -i 2 -t 20
------------------------------------------------------------
Client connecting to 192.168.1.162, TCP port 5001
TCP window size:   206 KByte (WARNING: requested 1.00 MByte)
------------------------------------------------------------
[  3] local 192.168.1.114 port 58093 connected with 192.168.1.162 port 5001
[  3]  0.0- 2.0 sec  16.5 MBytes  69.0 Mbits/sec
[  3]  2.0- 4.0 sec  16.4 MBytes  68.7 Mbits/sec
[  3]  4.0- 6.0 sec  16.4 MBytes  68.7 Mbits/sec
[  3]  6.0- 8.0 sec  16.4 MBytes  68.8 Mbits/sec
[  3]  8.0-10.0 sec  16.1 MBytes  67.6 Mbits/sec
[  3] 10.0-12.0 sec  16.4 MBytes  68.7 Mbits/sec
[  3] 12.0-14.0 sec  16.4 MBytes  68.7 Mbits/sec
[  3] 14.0-16.0 sec  16.3 MBytes  68.6 Mbits/sec
[  3] 16.0-18.0 sec  16.3 MBytes  68.5 Mbits/sec
[  3]  0.0-20.0 sec    162 MBytes  68.0 Mbits/sec

-----------------

Run it both directions and post the results.  Change 192.168.1.162 to your machine's IP address running the iperf server.  You can use the -m switch to output MegaBytes/sec results.

---

### Post by SeijiSensei on 2013-01-24
Chances are it is just normal caching during the transfer.  The file is first copied to a memory buffer on the remote target, then that buffer is written to the drive.  That makes the copy occur in fits and starts.

---

