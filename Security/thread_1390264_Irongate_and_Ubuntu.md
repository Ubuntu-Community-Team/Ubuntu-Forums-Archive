---
title: "Irongate and Ubuntu"
date: 2010-01-25
forum: Security
---

### Post by PaulHuffman on 2010-01-25
My IT is doing something goofy with their new IronPort. [http://www.ironport.com/](http://www.ironport.com/) We use fixed IPs, but all our PCs appear to be on 65.61.118.15 and the common ports seem to be blocked (reported by [http://www.canyouseeme.org/](http://www.canyouseeme.org/)) even though ftp, ssh, telnet, and web still work from Windows Pcs.  But now my Ubuntu 9.1 PC is blocked from using ftp, ssh, telnet, fetch, http, or rsync to the internet. Strangely, my old Solaris box can still ssh or telnet the internet.  Is there anything I can do with Ubuntu or anything I can ask my IT to do for me?

---

### Post by kiranmurari on 2010-01-28
Hi,
Can you check if firewall is running on the Ubuntu machine. Please paste the output of following commands:
```
$ sudo iptables -L -nv
$ sudo iptables -t nat -L -nv
$ sudo iptables -t filter -L -nv
```If firewall is running, can you disable it by the following commands:
```
$ sudo iptables -F
$ sudo iptables -X
```

---

### Post by PaulHuffman on 2010-01-28
Yesterday, http browsing and fetch were blocked, but today I can use a browser again, but facebook is blocked.  They just keep fiddling with it. 

Local firewall settings:
paul@pauleseries:~$ sudo iptables -L -nv
[sudo] password for paul:
Chain INPUT (policy ACCEPT 9519 packets, 4694K bytes)
 pkts bytes target     prot opt in     out     source               destination     

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination     

Chain OUTPUT (policy ACCEPT 8723 packets, 1367K bytes)
 pkts bytes target     prot opt in     out     source               destination     
paul@pauleseries:~$ sudo iptables -t nat -L -nv
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination     

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination     

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination     
paul@pauleseries:~$ sudo iptables -L -nv
Chain INPUT (policy ACCEPT 9927 packets, 5052K bytes)
 pkts bytes target     prot opt in     out     source               destination     

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination     

Chain OUTPUT (policy ACCEPT 9062 packets, 1444K bytes)
 pkts bytes target     prot opt in     out     source               destination     

sudo iptables -t nat -L -nv
Chain PREROUTING (policy ACCEPT 10 packets, 1606 bytes)
 pkts bytes target     prot opt in     out     source               destination     

Chain POSTROUTING (policy ACCEPT 34 packets, 2508 bytes)
 pkts bytes target     prot opt in     out     source               destination     

Chain OUTPUT (policy ACCEPT 34 packets, 2508 bytes)
 pkts bytes target     prot opt in     out     source               destination  

sudo iptables -t filter -L -nv
Chain INPUT (policy ACCEPT 9951 packets, 5054K bytes)
 pkts bytes target     prot opt in     out     source               destination     

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination     

Chain OUTPUT (policy ACCEPT 9080 packets, 1445K bytes)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by kiranmurari on 2010-02-02
> Yesterday, http browsing and fetch were blocked, but today I can use a browser again, but facebook is blocked.  They just keep fiddling with it. May be its your organization policy. It would be better if you can talk with your IT guys.

FORUM DO's & DONT's
[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

---

### Post by PaulHuffman on 2010-02-02
> **kiranmurari said:**
> May be its your organization policy. It would be better if you can talk with your IT guys.

FORUM DO's & DONT's
[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

Unfortunately, I started with my IT guys. They don't know what do do. They are new to IronPort. They can barely make it work for their Windows users. That's why I thought I'd ask around and see if there known issues with Linux and IronPort. 

Did I violate this forum do's and don'ts?

---

### Post by PaulHuffman on 2010-02-02
I've have this long email discussion with our IT department that is pretty much only John. 

>It sounds like it's our iron port filter. I have forwarded this to chester.

>Paul Huffman wrote:
> That's what I first did.  I have a XP laptop set at 20.27 and whatismyip says it's 118.15.   Same with XPs at 20.4 and 20.31. Every PC here so far says it's 118.15
>
> John Houck wrote:
>> Change the address in the XP computer to 20.27 and try it
>>
>> Paul Huffman wrote:
>>> I checked a XP at 20.4 and whatismyip also says 118.15
>>>
>>> John Houck wrote:
>>>> I made one more change, and reloaded the firewall. If this does not work, try using a windows pc with the 20.27 address and see if it see it out side as 118.59.
>>>>
>>>> Paul Huffman wrote:
>>>>> Oops, I meant whatsmyip says it's at 118.15.  Still no ftp, ssh, or rsync to the internet. Just browsing.
>>>>>
>>>>> John Houck wrote:
>>>>>> Cool, That is what we want and the way it should be. So is it doing what you want now?
>>>>>>
>>>>>> Paul Huffman wrote:
>>>>>>> Trying to get out from inside the YIN network at Nelson Springs.  I rebooted the linux PC. It still says it's IP is 20.27, but whatismyip and others says it's IP on the internet is 118.59.  802.1x Security is not checked. 
>>>>>>>
>>>>>>>
>>>>>>>
>>>>>>>
>>>>>>>
>>>>>>> John Houck wrote:
>>>>>>>> Are you trying to get in from outside of out from inside?
>>>>>>>>
>>>>>>>> John Houck wrote:
>>>>>>>>> Well I have no idea. I have your IP set both outgoing and in coming set to 65.61.118.59. It must be something on your end.
>>>>>>>>>
>>>>>>>>> Paul Huffman wrote:
>>>>>>>>>> Still 118.15. 
>>>>>>>>>>
>>>>>>>>>> John Houck wrote:
>>>>>>>>>>> ok try it now
>>>>>>>>>>>
>>>>>>>>>>> Paul Huffman wrote:
>>>>>>>>>>>> Whatismyip still says 118.15
>>>>>>>>>>>>
>>>>>>>>>>>> John Houck wrote:
>>>>>>>>>>>>> It should have changed, I just rebooted the firewall, try it now.
>>>>>>>>>>>>>
>>>>>>>>>>>>>
>>>>>>>>>>>>> Paul Huffman wrote:
>>>>>>>>>>>>>> I'm using 20.27 on my end, but whatismyip.com says that I'm translated to 65.61.118.15.  Should I use whatismyip to change to 118.59?
>>>>>>>>>>>>>>
>>>>>>>>>>>>>> John Houck wrote:
>>>>>>>>>>>>>>> Use the new address is your trying to get into the computer from the outside. Its static address should not change (161.217.20.27), however from the outside it has changed to 65.61.118.59. 161.217.20.27 has full access to get out to the world.
>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>> Paul Huffman wrote:
>>>>>>>>>>>>>>>> No, I didn't make that change at my end. 
>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>> I can change that here, and I can still get out through my 161.217.20.1 gateway?
>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>> John Houck wrote:
>>>>>>>>>>>>>>>>> Are you using the new static address? 161.217.20.27 is now 65.61.118.59
>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>> Paul Huffman wrote:
>>>>>>>>>>>>>>>>>> This port scanner says it can't get to my IP on ports 20-23.  Must be one of your routers in Toppenish, because traceroute gets to 161.217.6.2.
>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>> John Houck wrote:
>>>>>>>>>>>>>>>>>>> Your static address is 65.61.118.59 on the outside. See if that helps.
>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>> Paul Huffman wrote:
>>>>>>>>>>>>>>>>>>>> It still isn't working.  Maybe I should try a static IP address.
>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>> John Houck wrote:
>>>>>>>>>>>>>>>>>>>>> Is it working now? I can set up a static address for this computer if you want, but remember if we do that it will be exposed to the whole world, make sure it has allot of protection. We get hit hard by all kinds of attacks. let me know.
>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>> Paul Huffman wrote:
>>>>>>>>>>>>>>>>>>>>>> I use a Linux PC at 161.217.20.27 to do some ssh and ftp tasks on my web host.  However, last week sometimes, it seems to be unable to get through the firewall for any tasks except browser access. Can't ping anything on the web. Traceroute seems to show that it is not getting outside the firewall:
>>>>>>>>>>>>>>>>>>>>>> traceroute to ykfp.org (69.163.210.60), 30 hops max, 60 byte packets
>>>>>>>>>>>>>>>>>>>>>> 1  161.217.20.1 (161.217.20.1)  5.106 ms  7.327 ms  8.558 ms
>>>>>>>>>>>>>>>>>>>>>> 2  161.217.18.1 (161.217.18.1)  6.039 ms  6.522 ms  6.743 ms
>>>>>>>>>>>>>>>>>>>>>> 3  161.217.6.4 (161.217.6.4)  13.470 ms  13.952 ms  14.431 ms
>>>>>>>>>>>>>>>>>>>>>> 4  161.217.6.2 (161.217.6.2)  15.415 ms  15.896 ms  16.129 ms
>>>>>>>>>>>>>>>>>>>>>> 5  * * *
>>>>>>>>>>>>>>>>>>>>>> 6  * * *
>>>>>>>>>>>>>>>>>>>>>> 7  * * *
>>>>>>>>>>>>>>>>>>>>>>

---

### Post by PaulHuffman on 2010-02-03
I wouldn't think it is the firewall settings on my Ubuntu PC because the PC can still ftp, browse webpages, and ssh other servers on our LAN, he just can't reach outside our LAN to the Internet, past the IronPort.

---

