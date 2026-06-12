---
title: "HOWTO: Set Up an NTP Server"
date: 2008-07-17
forum: Tutorials
---

### Post by mbsullivan on 2008-07-17
**HOWTO: Set Up an NTP Server**

This tutorial describes how to set up your machine as a local Network Time Protocol (NTP) server and/or how to use the NTP daemon to regularly maintain an accurate system time.

**What is NTP?**

The Network Time Protocol (NTP) is a protocol designed for accurately synchronizing local time clocks with networked time servers. The NTP network of time servers is set up as a hierarchical manner, such that any user can enter the system as a server at some level (see the [Wikipedia]("http://en.wikipedia.org/wiki/Network_Time_Protocol") page for more details). 

The NTP hierarchy is separated into different levels, called [clock strata]("http://en.wikipedia.org/wiki/Network_Time_Protocol#Clock_strata"). The most accurate level, Stratum 0, is reserved for atomic clocks, etc. The next level, Stratum 1, is generally used by networked machines locally connected to the Straum 0 clocks. Stratum 2...15 are NTP machines that are connected, in turn, to lower level clocks and each other. 

This guide describes how to synchronize accurately with Stratum 1 and 2 machines, and maintain as accurate of system clock as possible thorughout the day. Sections are also included on how to allow your machine to operate as a Stratum 2/3 server for other machines on your local network.

**Do I have to make an NTP server?**

No... absolutely not! If you're satisfied with the clocks on your network having some unknown difference from the standard time (and each other), then you do not have to set up an NTP server. I set one up on my laptop in order to synchronize multiple machines on a local network within < 1 ms for a bioengineering experiment. There are various other advantages, in addition, which are described below.

**Motivation:**

Regularly, unmodified Ubuntu boxes use ntpdate (/usr/sbin/ntpdate) to synchronize the clock periodically with some external time server. This approach synchronizes the clock with a course resolution (typically once a day). 

Computer clocks are imperfect, and will drift from the (correct) time server during the day. Furthermore, drift rates in the clocks of different computers differ, such that by the end of the day significant differences may exist between different locally networked machines, which may interfere with certain operations (for instance, ever have a makefile complain when moving source code among different machines?).

It is possible to run the NTP daemon locally on a machine on your network. This has multiple advantages: first, the NTP daemon gradually "learns" the drift rate of your local machine, and can correct for it throughout the day. Synchronization with upper level time servers takes place multiple times a day, and many different time servers may be used simultaneously to make the synchronization more accurate. In this way, the NTP daemon acts as an accurate time client, keeping your system clock as close the the standard time as possible.

In addition to maintaining an accurate system clock, the NTP daemon allows a machine on your network (if you would like) to operate as an NTP time server. Doing so will allow other machines on your local network to synchronize with your LAN time server in a very quick and accurate manner, since network latency is minimized. In this way, the differences in clocks between machines on your network is kept as minimal as possible. Mac, and even Windows boxes are also able to synchronize with an NTP server, should you set one up.

There are other, less personal, motivations for setting up a machine as an NTP server. First, doing so may decrease the strain on higher level NTP servers, since other machines on your LAN may synchronize with a locally established time server. Also, ntpdate has been [deprecated]("http://mail-index.netbsd.org/current-users/2007/06/11/0007.html") in favor of using the -q flag for ntpd (which mimics its functionality). Thus, even if you do not want to run ntpd constantly in the background, ntpdate will eventually be replaced with ntpd, so you may want to become familiar with it now :)

**How to Maintain an Accurate System Clock with ntpd**

**1. Install the NTP daemon**

First, install the NTP daemon (ntpd):

```
sudo aptitude install ntpd
```

As was previously mentioned, ntpd can act both as a client (synchronizing your system time) and as a server (providing accurate time for other machines).

Optionally, you may also want to remove the previous (deprecated) time synchronization program, ntpdate. Perhaps it may be wiser to do so after you have ntpd working :)

```

sudo aptitude remove ntpdate
```

**2. Configure the daemon properly**

The configuration file for ntpd is located at /etc/ntp.conf. The default Ubuntu file probably requires some modification for optimal performance.

The first section you may want to modify is the list of servers to synchronize with. The default section probably looks as follows:

```
# You do need to talk to an NTP server or two (or three).
server ntp.ubuntu.com
```

In order to get the most accurate time possible, it is preferable to communicate with multiple different NTP servers, and keep them as close to your physical location as possible. There are various different server lists online, probably the best is located [here]("http://support.ntp.org/bin/view/Servers/WebHome"). There is some debate over the proper number of servers to use. One is better than two, and three or more probably is a good idea, so long as you don't go too overboard. An example of a few time servers that I used follows:

```
server nist1-dc.WiTime.net iburst
server ntp0.mcs.anl.gov
server 0.us.pool.ntp.org
server 1.us.pool.ntp.org
server 2.us.pool.ntp.org
server 3.us.pool.ntp.org
```

Once a few good servers have been found, add them to the list, putting 'iburst' after the most promising one. For instance:

```
server nist1-dc.WiTime.net iburst
```

This will cause ntpd to synchronize very quickly with this server after starting up. Otherwise, ntpd will slowly tend to drift towards agreement with the server list (as is its nature), and it may take 15-20 minutes to synchronize well enough to act as a time server for the rest of your network. 

Also, add a few extra lines to the bottom of your servers list to provide your current local time as a default should you temporarly lose Internet connectivity:

```
server 127.127.1.0
fudge 127.127.1.0 stratum 10
```

This will prevent any nastiness if you're running ntpd on a laptop or other machine with intermittent periods of disconnectivity from the Internet.

All in all, the server list should look similar to the following (this is mine, your servers will probably be different):

```
# You do need to talk to an NTP server or two (or three).
server nist1-dc.WiTime.net iburst
server ntp0.mcs.anl.gov
server 0.us.pool.ntp.org
server 1.us.pool.ntp.org
server 2.us.pool.ntp.org
server 3.us.pool.ntp.org
server 127.127.1.0
fudge 127.127.1.0 stratum 10
```

**3. Make sure the configuration works**

Now that you have a proper server list in your /etc/ntp.conf file, it is time to run the daemon and see if you synchronize properly! Make sure you have an active Internet connection, and then run:

```
sudo /etc/init.d/ntp restart
```

Next, monitor your system log to see if you synchronize with a time server:

```
tail -f /var/log/syslog
```

In about 10-15 seconds (or up to 15-20 minutes if you forgot to put 'iburst' after your favorite server), you should see something like the following in your system log:

```
Jul 17 16:50:22 hostname ntpd[22402]: synchronized to 140.221.9.20, stratum 2
```

If this message never comes, you have not yet properly synchronized with the NTP server network. Check the list of NTP peers you are communicating with using the following:

```
ntpq -c lpeer
```

If the 'delay', 'offset', and 'jitter' fields are non-zero and you haven't synchronized, it probably means that you just need to wait a while. Check again that you've inserted the 'iburst' argument to your servers list! My peers, for reference, look something like the following:

```
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*milo.mcs.anl.go 192.5.41.40      2 u    4   64   77   46.213   67.753   2.207
-europium.canoni 193.79.237.14    2 u   63   64   37   97.375   71.020   1.875
-dtype.org       69.25.96.13      2 u    2   64   77   86.956   69.178   1.804
+smtp130.junkema 216.218.254.202  2 u    2   64   77   87.266   67.677   0.916
+kechara.flame.o 216.218.254.202  2 u    -   64   77   89.183   68.717   1.713
-host2.kingrst.c 99.150.184.201   2 u    -   64   77   24.306   62.121   2.608
 LOCAL(0)        .LOCL.          10 l   59   64   37    0.000    0.000   0.002

```

**4. Share! (optional)**

Once ntpd is running and is synchronized with the time servers you have selected, you may set it up in order to act as a time server for other machines. To do so, add a section like the following to /etc/ntp.conf:

```
# Allow LAN machines to synchronize with this ntp server
restrict 192.168.1.0 mask 255.255.255.0 nomodify notrap
restrict 192.168.2.0 mask 255.255.255.0 nomodify notrap
```

You may add as many (or few) CIDR address blocks to allow to synchronize with your machine as you'd like. I included those commonly used with Linksys (192.168.1.*) and SMC (192.168.2.*) routers.

**5. Synchronize! (optional)**

Once you've set up an NTP server using steps 1-4, you can synchronize the other machines on your network with your server in various manners. I outline a couple of them below:

**ntpd:**

If you have ntpd installed on another machine, you can use your first server in the servers list of your ntp.conf file, or can synchronize one time with the -q option, as follows:

```
ntpd -q [IP address of your server]
```

**ntpdate:**

If you still have ntpdate installed on another machine, you may use it to synchronize with your server as follows:

```
ntpdate [IP address of your server]
```

*Note: if you are running ntpd on a machine and for some reason still want to use ntpdate to set the time, you must use the -u option.*

**Windows:**

Windows machines use a simplified version of NTP called Simple Network Time Protocol (SNTP), and can synchronize with NTP servers. In order to synchronize with your new server, double click on the time and go to the "Internet Time" tab. Put the IP address of your server in the "Server" field. I have attached a screenshot of Windows XP synchronizing with a LAN time server, should anybody be interested.

That's it! The entire process is not hard, but can be confusing to somebody who hasn't dealt much with the NTP network before. I hope this helps! Let me know if you have any problems setting up your server.

Mike

**Links**

I found the following links helpful... you may, too!

[https://help.ubuntu.com/7.10/server/C/NTP.html]("https://help.ubuntu.com/7.10/server/C/NTP.html")
[http://linuxwave.blogspot.com/2007/08/setting-up-your-own-ntp-server.html]("http://linuxwave.blogspot.com/2007/08/setting-up-your-own-ntp-server.html")
[http://lists.ntp.isc.org/pipermail/questions/2006-October/011889.html]("http://lists.ntp.isc.org/pipermail/questions/2006-October/011889.html")
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch24_:_The_NTP_Server#The_.2Fetc.2Fntp.conf_File]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch24_:_The_NTP_Server#The_.2Fetc.2Fntp.conf_File")
[http://www.ntp.org/ntpfaq/NTP-a-faq.htm]("http://www.ntp.org/ntpfaq/NTP-a-faq.htm")

---

### Post by jelevin on 2008-07-20
Thanks.  To sync windows machines to my ubuntu ntp server I really like automacron, see [http://oneguycoding.com/automachron/](http://oneguycoding.com/automachron/)

---

### Post by kevdog on 2008-07-20
Can you add information about what port ntp is running over, so users using a firewall can open up the specific port to allow connections to the ntp server -- Thanks.

---

### Post by NetworkGuy on 2008-07-20
NTP uses port 123/TCP & 123/UDP

---

### Post by kevdog on 2008-07-20
> **NetworkGuy said:**
> NTP uses port 123/TCP & 123/UDP

Incoming and Outgoing -- Just need how to set up open ports for client and server.

---

### Post by mbsullivan on 2008-07-21
> Incoming and Outgoing -- Just need how to set up open ports for client and server.

On the server side, ntpd should just require access to bidirectional UDP traffic on port 123. So long as you only want to share on your LAN, you won't have to manage port forwarding on a hardware firewall, but software firewalls (such as Firestarter) may need to be configured properly.

I think that clients should not have to have any ports open in order to synchronize with an NTP server. Ntpdate, by default, will try and use port 123, but you may use the -u option in order to operate over an arbitrary open port.

Mike

---

### Post by fro1269 on 2011-02-25
Is there a limit to how many times a day I can sync with pool.ntp.org? My reason for doing this is I am running Ubuntu Server 10.04.2 in a virtualbox VM sitting on top of Windows Server 2003. I am trying to "Dummy Proof" the process of keeping time synced. If someone were doing maintenance on the WS2003 box and were to click "save state" and keep it off for an extended period of time , I would want a cron job running every 5-10 minutes that syncs time automatically, so that someone who doesnt know linux wouldn't have to run ntpdate manually.

I have read
[http://www.pool.ntp.org/en/use.html](http://www.pool.ntp.org/en/use.html)

It does not state that multiple updates/hour are not allowed, I am just afraid of them blacklisting my IP if I do it too much.

---

### Post by fro1269 on 2011-02-25
I think I just solved my own problem. For those of you experiencing similar issues please reference

[http://www.virtualbox.org/manual/ch09.html#changetimesync](http://www.virtualbox.org/manual/ch09.html#changetimesync)

---

### Post by mbsullivan on 2011-02-28
> I think I just solved my own problem. For those of you experiencing similar issues please reference

[http://www.virtualbox.org/manual/ch0...changetimesync](http://www.virtualbox.org/manual/ch0...changetimesync)

So, you're not using NTP... Rather, you're just using the Guest Additions (and guest additions parameters) to keep time synchronized, right?

It's a good method, for VMs.

Mike

---

### Post by fro1269 on 2011-02-28
> **mbsullivan said:**
> So, you're not using NTP... Rather, you're just using the Guest Additions (and guest additions parameters) to keep time synchronized, right?

It's a good method, for VMs.

Mike

That is correct, I have been testing it out and it works perfectly. It took a little bit of google searching to figure out how to install guest editions on a server not running X, but it worked out just fine

---

### Post by johnamcclintock on 2011-07-14
Possibly a very stupid question but I'm going to ask it anyway:

Is it possible to set a Ubuntu machine up as an NTP server without it having any external clocks to reference to?

The reason I want to do this is that the machine itself has no Internet connectivity, typically, and is used to monitor Customer networks only so is intended to be secured and isolated from the Internet.

I assume this must be possible but wanted to ask first in case someone can very quickly answer for me.

Cheers,

John

---

### Post by thug777 on 2011-07-16
[http://ubuntuforums.org/showthread.php?t=579418](http://ubuntuforums.org/showthread.php?t=579418)

---

### Post by johnamcclintock on 2011-07-19
Thanks Thug. After some searching around I had figured this out. Unfortunately it's not helping me much as the Cisco switches I am trying to get to synchronise to my NTP server seem to not want to. They are seeing the stratum correctly (fudge+1) NTP server is directly connected into the switch in the NTP association but they are just refusing to use the server most of the time. On occasion, for no discernible reason, they will synch up but a reboot normally quickly fixes that. Most, most frustrating as if I install an NTP server on my Windows it work every time :(

---

### Post by johnamcclintock on 2011-07-26
Right, I have actually finally figured this out completely and the fault does not lie with the Ubuntu NTP server but rather with the switches. Even though the configuration guide claims that, if the switches are synchronised to an external time source they can provide time for other clients, this appears to be either a lie or there is an undocumented bug. Whenever I try to "serve" time from a switch to another switch for some reason the NTP server becomes unreachable to the original switch. This mean that the swtch become unsynchronised and thus no other switches will then synchronise to it! My fix, albeit not the cleanest ever, is to have all switches use the Linux server as the source for time (there is an IPSec tunnel between the network and the Linux machine hence it's not really a very nice solution!).
Now, my major problem seems to be that NTP on Ubuntu does not support authentication. Even the restrict part doesn't seem to stop the server sharing time with anything outside of the restrict list. Is there a definitive way to secure NTP, preferably by some sort of key exchange if possible?

Thanks,

John

---

### Post by sirgad on 2011-12-15
Just FYI: ntpd no longer reports synchronization in syslog, or anywhere else.  This was relayed to me on the mailing list.  Apparently, it was considered too "noisy".  So, you should no longer use the "tail -f /var/log/syslog" command to look for entries of the type:

hostname ntpd[xxxx]: synchronized to x.x.x.x, stratum 2

to confirm synchronization.

S.

---

### Post by rrbaps on 2012-01-26
Hi,
I have connected my Ubuntu 11.04 system on a LAN. On the other machine(MC 2) we have Ubuntu 11.04. I wanna sync my computer to (MC 2)  with atleast nanosecond precision. Can someone throw some light on it?

---

### Post by bdalzell on 2012-06-29
by the time we get to Xubuntu 12.04 ntpd seems to be absent from the archives.

however:

sudo aptitude install ntp 

installed ntp and allowed me to set Applications>Settings>Time and Date

to the setting: 

Keep synchronized with Internet servers

For what it is worth

---

