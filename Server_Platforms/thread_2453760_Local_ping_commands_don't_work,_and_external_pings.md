---
title: "Local ping commands don't work, and external pings result in never ending results"
date: 2020-11-16
forum: Server Platforms
---

### Post by ommammo on 2020-11-16
Hi all,
 
First time Ubuntu user here, setting up a dev environment on Ubuntu server 20.1, following [this somewhat older guide]("https://medium.com/@jevgenijdmitrijev/how-to-configuring-the-ssh-connection-with-virtual-local-domain-name-765e5bc28d87") to setting things up. I'm on a Windows 10 machine and have the VM all set up and Ubuntu is running, but I'm encountering a problem in the step after editing my Windows hosts file with my server ip. I ran ifconfig to discover that my IP is 192.168.1.127

I added the following line to my hosts file (and saved in administrator mode):

```
192.168.1.127 ubuntu.local
```

Then I went back to the Ubuntu VM and typed "ping ubuntu.local" which returned a message of "Temporary failure in name resolution."

To check whether I could ping *anything,* I typed "ping google.com" which returned an endless list of results. Really, they never stop. I've watched it count up to icmp_seq=500 and more. I've tried other domains as well with the same kinds of results. 

Anyone know what I'm doing wrong? If it matters, I connect to the internet through a wifi router, and I used the previously linked setup guide to enable the network attached to a bridged adapter.

Thanks in advance.

---

### Post by darkod on 2020-11-16
First of all, the ping command in ubuntu does not work in identical way as windows. It doesn't stop after 4 counts. It will run continuously unless you stop it with Ctrl+C. So that part is normal (that it never stops).

If you want short ping test with 4 counts for example, do:
```
ping -c 4 google.com
```

For the other thing, I didn't quite understand. You put that ubuntu.local entry in the hosts file in Windows? And you are running the 'ping ubuntu.local' on the Ubuntu VM? In that case it is normal to fail, ubuntu will not know what ubuntu.local is if it is declared in the Windows host.

And about the ubuntu version, you say 20.1. Does that mean 20.10? If yes, I suggest to forget about it and recreate the VM with 20.04 LTS. Ubuntu has LTS versions that come out every two years. The latest one is 20.04 LTS. Only these versions have long term support of 5 years and should be considered for more serious work.

So even if you are just doing some testing and learning, I suggest to get used to work with LTS versions only. Don't download the latest ubuntu. Download the latest LTS ubuntu.

---

