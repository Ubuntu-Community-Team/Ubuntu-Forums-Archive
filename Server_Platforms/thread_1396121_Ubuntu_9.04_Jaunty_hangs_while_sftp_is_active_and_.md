---
title: "Ubuntu 9.04 Jaunty hangs while sftp is active and dynamic IP changes"
date: 2010-02-01
forum: Server Platforms
---

### Post by softcore on 2010-02-01
Hi All. Thanks in advance for helping me.

I have this strange problem which I am unable to web search on and not sure what to do next. My Linux knowledge is between basic to intermediate but I know how to troubleshoot general hardware problems.

My problem is that Ubuntu 9.04 Jaunty 64-bit hangs while SFTP is active and dynamic IP changes. For example, I SFTP into my home server and transfer file then suddenly my ISP decides to renew my IP and give me a new IP while my SFTP client is still uploading files to my home server. This causes my SFTP client to stop working.

Upon checking, my router is still running with a new IP lease from my ISP. My Linux box still powers on but typing anything from the keyboard does not make it "wake up" and put things on the monitor. Nothing seems to make it respond and the only way is to get about it is to power off and on. During that time, you cannot SSH into the server as there is no respond. SFTP into the server is not possible too because connection fails.

The server has all new hardware, latest BIOS, etc. Memtest86 shows no errors after running for more then 5 hours. I am unable to find anything out of the norm in /var/log/kern.log or in dmesg. All hardware seems to be working.

When I think about it, I tend to think OpenSSH (probably that is the default package in Jaunty) is causing this system hang whenever there is an interrupted connection from the outside world. However, I fail to agree with this is because I am sure the daemon and Linux can tolerate this situation without resorting to system hang. FYI, I have installed vsftp as well but this should not be a problem.

I am at a loss on what is actually going on and I am not sure what to do next, please help. :-(

---

### Post by coral66 on 2010-02-02
Have a look here, it may help ...
[http://www.bjornenki.com/blog/create-own-dyndns-type-static-ip]("http://www.bjornenki.com/blog/create-own-dyndns-type-static-ip")

---

### Post by softcore on 2010-02-02
Hi Coral66.

Thanks for the tip. I will look at this and see how. It might take time to get back because I can replicate this once a day.

In the meantime, does anyone have any other idea? I am (wishful) hoping that there may be an issue with my SSH daemon which is the default OpenSSH package in Jaunty (IIRC) and someone here might have encountered this before and have a solution.

Thanks.

---

