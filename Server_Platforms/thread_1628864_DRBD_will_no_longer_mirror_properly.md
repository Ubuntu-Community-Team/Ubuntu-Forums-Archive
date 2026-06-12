---
title: "DRBD will no longer mirror properly"
date: 2010-11-23
forum: Server Platforms
---

### Post by The Foz on 2010-11-23
I set up DRBD for mirroring between 2 machines. For a while it worked fine, but now I cannot get the mirrors to connect.

Both machines (a server and a laptop) are running Ubuntu 9.10. Both have drbd8-source and drbd8-utils installed. They are directly connected over a 1Gbps Ethernet LAN.

I have 2 5GB partitions on both machines.

This is the important part of the drbd.conf file:
```
common {
  syncer { rate 10M; }
  protocol A;
}

resource sheryl {
  startup {
	become-primary-on df-server1;
  }
  on df-server1 {
	device /dev/drbd1;
	disk /dev/sda2;
	address 192.168.0.2:7789;
	meta-disk internal;
  }
  on acer-laptop {
	device /dev/drbd1;
	disk /dev/sda3;
	address 192.168.0.100:7789;
	meta-disk internal;
  }
}

resource dave {
  startup {
	become-primary-on df-server1;
  }
  on df-server1 {
	device /dev/drbd2;
	disk /dev/sda3;
	address 192.168.0.2:7790;
	meta-disk internal;
  }
  on acer-laptop {
	device /dev/drbd2;
	disk /dev/sda4;
	address 192.168.0.100:7790;
	meta-disk internal;
  }
}
```

Ports 7789 and 7790 are both open on both machines. I have confirmed this by doing a port scan - when there are listeners active, the port scan shows the ports as open.

The problem is that once the second machine is booted, and DRBD attempts to connect, the listeners seem to stop. If I restart the DRBD resources on one machine, then the listeners run (for a while), but if I restart the resources on the other machine, the listeners stop.

In the typical state, drbd-overview on the server gives 
```
 1:sheryl  StandAlone Primary/Unknown UpToDate/DUnknown r---- /media/SherylSharing ext3 4.9G 1.2G 3.4G 26% 
  2:dave    StandAlone Primary/Unknown UpToDate/DUnknown r---- /media/DaveSharing   ext3 4.9G 2.6G 2.1G 55% 

```
and on the laptop gives 
```
  1:sheryl  StandAlone Secondary/Unknown UpToDate/DUnknown r---- 
  2:dave    StandAlone Secondary/Unknown UpToDate/DUnknown r---- 

```

Running grep drbd kern.log on the server gives 
```
Nov 19 08:11:31 df-server1 kernel: [   26.664368] drbd: initialized. Version: 8.3.3 (api:88/proto:86-91)
Nov 19 08:11:31 df-server1 kernel: [   26.664372] drbd: GIT-hash: 49bfeeaf3690ad0b9afd5376feda9e9eb34a30f3 build by nobody@df-server1, 2010-11-10 08:49:02
Nov 19 08:11:31 df-server1 kernel: [   26.664375] drbd: registered as block device major 147
Nov 19 08:11:31 df-server1 kernel: [   26.664377] drbd: minor_table @ 0xffff880154369e00
Nov 19 08:11:32 df-server1 kernel: [   26.702783] block drbd1: Starting worker thread (from cqueue [2337])
Nov 19 08:11:32 df-server1 kernel: [   26.704507] block drbd1: disk( Diskless -> Attaching ) 
Nov 19 08:11:32 df-server1 kernel: [   26.742996] block drbd1: Found 4 transactions (14 active extents) in activity log.
Nov 19 08:11:32 df-server1 kernel: [   26.743001] block drbd1: Method to ensure write ordering: barrier
Nov 19 08:11:32 df-server1 kernel: [   26.743006] block drbd1: max_segment_size ( = BIO size ) = 32768
Nov 19 08:11:32 df-server1 kernel: [   26.743011] block drbd1: drbd_bm_resize called with capacity == 10233008
Nov 19 08:11:32 df-server1 kernel: [   26.743061] block drbd1: resync bitmap: bits=1279126 words=19987
Nov 19 08:11:32 df-server1 kernel: [   26.743065] block drbd1: size = 4997 MB (5116504 KB)
Nov 19 08:11:32 df-server1 kernel: [   26.753058] block drbd1: recounting of set bits took additional 0 jiffies
Nov 19 08:11:32 df-server1 kernel: [   26.753062] block drbd1: 772 KB (193 bits) marked out-of-sync by on disk bit-map.
Nov 19 08:11:32 df-server1 kernel: [   26.753071] block drbd1: Marked additional 51 MB as out-of-sync based on AL.
Nov 19 08:11:32 df-server1 kernel: [   26.791070] block drbd1: disk( Attaching -> UpToDate ) 
Nov 19 08:11:32 df-server1 kernel: [   26.810695] block drbd2: Starting worker thread (from cqueue [2337])
Nov 19 08:11:32 df-server1 kernel: [   26.812390] block drbd2: disk( Diskless -> Attaching ) 
Nov 19 08:11:32 df-server1 kernel: [   26.862182] block drbd2: Found 4 transactions (17 active extents) in activity log.
Nov 19 08:11:32 df-server1 kernel: [   26.862188] block drbd2: Method to ensure write ordering: barrier
Nov 19 08:11:32 df-server1 kernel: [   26.862193] block drbd2: max_segment_size ( = BIO size ) = 32768
Nov 19 08:11:32 df-server1 kernel: [   26.862199] block drbd2: drbd_bm_resize called with capacity == 10233008
Nov 19 08:11:32 df-server1 kernel: [   26.862241] block drbd2: resync bitmap: bits=1279126 words=19987
Nov 19 08:11:32 df-server1 kernel: [   26.862245] block drbd2: size = 4997 MB (5116504 KB)
Nov 19 08:11:32 df-server1 kernel: [   26.868031] block drbd2: recounting of set bits took additional 0 jiffies
Nov 19 08:11:32 df-server1 kernel: [   26.868034] block drbd2: 4444 KB (1111 bits) marked out-of-sync by on disk bit-map.
Nov 19 08:11:32 df-server1 kernel: [   26.868045] block drbd2: Marked additional 63 MB as out-of-sync based on AL.
Nov 19 08:11:32 df-server1 kernel: [   26.880482] block drbd2: disk( Attaching -> UpToDate ) 
Nov 19 08:11:32 df-server1 kernel: [   26.902350] block drbd1: conn( StandAlone -> Unconnected ) 
Nov 19 08:11:32 df-server1 kernel: [   26.902441] block drbd1: Starting receiver thread (from drbd1_worker [2340])
Nov 19 08:11:32 df-server1 kernel: [   26.902515] block drbd1: receiver (re)started
Nov 19 08:11:32 df-server1 kernel: [   26.902528] block drbd1: conn( Unconnected -> WFConnection ) 
Nov 19 08:11:32 df-server1 kernel: [   26.903772] block drbd2: conn( StandAlone -> Unconnected ) 
Nov 19 08:11:32 df-server1 kernel: [   26.903791] block drbd1: bind before connect failed, err = -99
Nov 19 08:11:32 df-server1 kernel: [   26.903797] block drbd1: conn( WFConnection -> Disconnecting ) 
Nov 19 08:11:32 df-server1 kernel: [   26.903841] block drbd2: Starting receiver thread (from drbd2_worker [2349])
Nov 19 08:11:32 df-server1 kernel: [   26.903874] block drbd2: receiver (re)started
Nov 19 08:11:32 df-server1 kernel: [   26.903879] block drbd2: conn( Unconnected -> WFConnection ) 
Nov 19 08:11:32 df-server1 kernel: [   26.903903] block drbd2: bind before connect failed, err = -99
Nov 19 08:11:32 df-server1 kernel: [   26.903908] block drbd2: conn( WFConnection -> Disconnecting ) 
Nov 19 08:11:32 df-server1 kernel: [   26.930842] block drbd1: role( Secondary -> Primary ) 
Nov 19 08:11:32 df-server1 kernel: [   26.935757] block drbd2: role( Secondary -> Primary ) 
Nov 19 08:11:32 df-server1 kernel: [   27.100649] block drbd1: Discarding network configuration.
Nov 19 08:11:32 df-server1 kernel: [   27.100679] block drbd1: Connection closed
Nov 19 08:11:32 df-server1 kernel: [   27.100691] block drbd1: conn( Disconnecting -> StandAlone ) 
Nov 19 08:11:32 df-server1 kernel: [   27.100702] block drbd1: receiver terminated
Nov 19 08:11:32 df-server1 kernel: [   27.100705] block drbd1: Terminating receiver thread
Nov 19 08:11:32 df-server1 kernel: [   27.101272] block drbd2: Discarding network configuration.
Nov 19 08:11:32 df-server1 kernel: [   27.101298] block drbd2: Connection closed
Nov 19 08:11:32 df-server1 kernel: [   27.101309] block drbd2: conn( Disconnecting -> StandAlone ) 
Nov 19 08:11:32 df-server1 kernel: [   27.101321] block drbd2: receiver terminated
Nov 19 08:11:32 df-server1 kernel: [   27.101324] block drbd2: Terminating receiver thread
Nov 19 08:11:32 df-server1 kernel: [   27.178194] EXT3 FS on drbd1, internal journal
Nov 19 08:11:32 df-server1 kernel: [   27.256255] EXT3 FS on drbd2, internal journal

```
There are no more recent entries relating to DRBD.

Running grep drbd kern.log on the laptop gives 
```
Nov 23 10:53:35 acer-laptop kernel: [   20.748559] drbd: initialized. Version: 8.3.3 (api:88/proto:86-91)
Nov 23 10:53:35 acer-laptop kernel: [   20.748564] drbd: GIT-hash: 49bfeeaf3690ad0b9afd5376feda9e9eb34a30f3 build by nobody@acer-laptop, 2010-11-08 14:20:04
Nov 23 10:53:35 acer-laptop kernel: [   20.748568] drbd: registered as block device major 147
Nov 23 10:53:35 acer-laptop kernel: [   20.748571] drbd: minor_table @ 0xf1d95680
Nov 23 10:53:35 acer-laptop kernel: [   20.754797] block drbd1: Starting worker thread (from cqueue [1701])
Nov 23 10:53:35 acer-laptop kernel: [   20.754870] block drbd1: disk( Diskless -> Attaching ) 
Nov 23 10:53:35 acer-laptop kernel: [   20.758805] block drbd1: Found 4 transactions (14 active extents) in activity log.
Nov 23 10:53:35 acer-laptop kernel: [   20.758811] block drbd1: Method to ensure write ordering: barrier
Nov 23 10:53:35 acer-laptop kernel: [   20.758817] block drbd1: max_segment_size ( = BIO size ) = 32768
Nov 23 10:53:35 acer-laptop kernel: [   20.758822] block drbd1: drbd_bm_resize called with capacity == 10233008
Nov 23 10:53:35 acer-laptop kernel: [   20.758893] block drbd1: resync bitmap: bits=1279126 words=39974
Nov 23 10:53:35 acer-laptop kernel: [   20.758898] block drbd1: size = 4997 MB (5116504 KB)
Nov 23 10:53:35 acer-laptop kernel: [   20.761099] block drbd1: recounting of set bits took additional 0 jiffies
Nov 23 10:53:35 acer-laptop kernel: [   20.761103] block drbd1: 44 MB (11264 bits) marked out-of-sync by on disk bit-map.
Nov 23 10:53:35 acer-laptop kernel: [   20.761112] block drbd1: disk( Attaching -> UpToDate ) 
Nov 23 10:53:35 acer-laptop kernel: [   20.825417] block drbd2: Starting worker thread (from cqueue [1701])
Nov 23 10:53:35 acer-laptop kernel: [   20.825510] block drbd2: disk( Diskless -> Attaching ) 
Nov 23 10:53:36 acer-laptop kernel: [   20.860724] block drbd2: Found 4 transactions (6 active extents) in activity log.
Nov 23 10:53:36 acer-laptop kernel: [   20.860730] block drbd2: Method to ensure write ordering: barrier
Nov 23 10:53:36 acer-laptop kernel: [   20.860736] block drbd2: max_segment_size ( = BIO size ) = 32768
Nov 23 10:53:36 acer-laptop kernel: [   20.860741] block drbd2: drbd_bm_resize called with capacity == 10233008
Nov 23 10:53:36 acer-laptop kernel: [   20.860815] block drbd2: resync bitmap: bits=1279126 words=39974
Nov 23 10:53:36 acer-laptop kernel: [   20.860819] block drbd2: size = 4997 MB (5116504 KB)
Nov 23 10:53:36 acer-laptop kernel: [   20.881365] block drbd2: recounting of set bits took additional 0 jiffies
Nov 23 10:53:36 acer-laptop kernel: [   20.881370] block drbd2: 32 KB (8 bits) marked out-of-sync by on disk bit-map.
Nov 23 10:53:36 acer-laptop kernel: [   20.881379] block drbd2: disk( Attaching -> UpToDate ) 
Nov 23 10:53:36 acer-laptop kernel: [   20.908545] block drbd1: conn( StandAlone -> Unconnected ) 
Nov 23 10:53:36 acer-laptop kernel: [   20.908674] block drbd1: Starting receiver thread (from drbd1_worker [1704])
Nov 23 10:53:36 acer-laptop kernel: [   20.908708] block drbd1: receiver (re)started
Nov 23 10:53:36 acer-laptop kernel: [   20.908714] block drbd1: conn( Unconnected -> WFConnection ) 
Nov 23 10:53:36 acer-laptop kernel: [   20.908739] block drbd1: bind before connect failed, err = -99
Nov 23 10:53:36 acer-laptop kernel: [   20.908744] block drbd1: conn( WFConnection -> Disconnecting ) 
Nov 23 10:53:36 acer-laptop kernel: [   20.909978] block drbd2: conn( StandAlone -> Unconnected ) 
Nov 23 10:53:36 acer-laptop kernel: [   20.910298] block drbd2: Starting receiver thread (from drbd2_worker [1713])
Nov 23 10:53:36 acer-laptop kernel: [   20.910332] block drbd2: receiver (re)started
Nov 23 10:53:36 acer-laptop kernel: [   20.910338] block drbd2: conn( Unconnected -> WFConnection ) 
Nov 23 10:53:36 acer-laptop kernel: [   20.910360] block drbd2: bind before connect failed, err = -99
Nov 23 10:53:36 acer-laptop kernel: [   20.910366] block drbd2: conn( WFConnection -> Disconnecting ) 
Nov 23 10:53:36 acer-laptop kernel: [   21.105062] block drbd1: Discarding network configuration.
Nov 23 10:53:36 acer-laptop kernel: [   21.105088] block drbd1: Connection closed
Nov 23 10:53:36 acer-laptop kernel: [   21.105099] block drbd1: conn( Disconnecting -> StandAlone ) 
Nov 23 10:53:36 acer-laptop kernel: [   21.105112] block drbd1: receiver terminated
Nov 23 10:53:36 acer-laptop kernel: [   21.105115] block drbd1: Terminating receiver thread
Nov 23 10:53:36 acer-laptop kernel: [   21.109220] block drbd2: Discarding network configuration.
Nov 23 10:53:36 acer-laptop kernel: [   21.109241] block drbd2: Connection closed
Nov 23 10:53:36 acer-laptop kernel: [   21.109250] block drbd2: conn( Disconnecting -> StandAlone ) 
Nov 23 10:53:36 acer-laptop kernel: [   21.109261] block drbd2: receiver terminated
Nov 23 10:53:36 acer-laptop kernel: [   21.109264] block drbd2: Terminating receiver thread

```

None of the documentation about debugging DRBD seems to help. Does anyone have any ideas?

---

### Post by The Foz on 2011-08-19
I have now worked out how to get DRBD to start.

On booting the server (since upgrading to 10.04), the mirrored file-systems are not ready when the system attempts to mount them, so I skip them manually. Then, once logged-in, I run 'sudo /etc/init.d/drbd restart', and after that 'sudo mount -a', and then everything is fine on the server.

On the laptop I run 'sudo /etc/init.d/drbd restart', after which mirroring runs fine.

It seems like someone needs to do some work on the starting order, in rc*.d.

---

