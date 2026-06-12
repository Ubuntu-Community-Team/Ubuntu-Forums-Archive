---
title: "call for testing: ipfs"
date: 2017-03-03
forum: Ubuntu Development Version
---

### Post by elopio on 2017-03-03
Hello!

I have been testing our end-to-end workflow from packaging a snap to continuous delivery to the store using IPFS. 

IPFS is a really interesting free project for distributed storage. You can read more about it and watch a demo here:
[https://ipfs.io/](https://ipfs.io/)

Now, the IPFS project itself is in active development. In this new world where upstream delivers software directly to the store with no maintainers in the middle, the role of the Ubuntu community is a little different. We have direct and quick access to the features that the developers are writing, so we can help them directly.
We don't need to report a bug to Ubuntu, which will be copied to Debian, then raised from the maintainers to the developers. After the bug is fixed, we don't have to wait for it to land in Debian, then to be copied to Ubuntu, and finally, we won't have to upgrade to the newest release to get it if we don't want to.

So, you can tell that I'm having a lot of fun here :) It would be great if you can help us exploring this new world, and at the same time, help IPFS which is very cool. Give it a try:

```
$ sudo snap install ipfs
```

That will get you ipfs v0.4.5.

I have written a simple guide to get started testing it:
[https://gist.github.com/elopio/7492a28bd1aef6c4a86b5dcf5d5cb65b#smoke-tests-for-the-ipfs-snap](https://gist.github.com/elopio/7492a28bd1aef6c4a86b5dcf5d5cb65b#smoke-tests-for-the-ipfs-snap)

If you finish that successfully, stop the damon with Ctrl+C and run:

```
$ sudo snap refresh ipfs --candidate
```

That will get you ipfs v0.4.6, the newest version just published by upstream yesterday. Run the smoke test again on this new version, and that way we can confirm that it's safe to push 0.4.6 to the stable channel. Once the new version is in stable, all the users will get the update automatically.

This is one of the features I love the most. Please let me know how the tests go. And if you have any questions or suggestions, I'd also be happy to talk about that.

pura vida.

---

### Post by ventrical on 2017-03-03
There were some errors during 'connections'

```

01:21:24.593 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID ceDnMe>) failed: dial attempt failed: <peer.ID WDPtLj> --> <peer.ID ceDnMe> dial attempt failed: dial tcp4 84.76.127.168:4001: getsockopt: connection refused wantmanager.go:220
01:21:27.692 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID dZxnFG>) failed: dial attempt failed: <peer.ID WDPtLj> --> <peer.ID dZxnFG> dial attempt failed: dial tcp4 192.168.2.245:4001: i/o timeout wantmanager.go:220
01:22:26.337 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID akazk9>) failed: dial attempt failed: <peer.ID WDPtLj> --> <peer.ID akazk9> dial attempt failed: dial tcp6 [fc82:4905:b68a:8154:4087:182a:7856:6e2e]:4001: connect: network is unreachable wantmanager.go:220
01:22:28.484 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID RKLGRE>) failed: dial attempt failed: context deadline exceeded wantmanager.go:220
01:22:29.967 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID VE38JN>) failed: dial attempt failed: <peer.ID WDPtLj> --> <peer.ID VE38JN> dial attempt failed: i/o timeout wantmanager.go:220
01:22:33.500 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID Tm7RdP>) failed: dial attempt failed: <peer.ID WDPtLj> --> <peer.ID Tm7RdP> dial attempt failed: dial tcp6 [2001:41d0:401:3100::186]:4001: connect: network is unreachable wantmanager.go:220

```

---

### Post by cariboo on 2017-03-03
Tested on Xubuntu 17.04, everything works as it should except for the readme. Running:

```
ipfs cat /ipfs/$hash/readme
```

results in:

```
Error: selected encoding not supported
```

---

### Post by ventrical on 2017-03-03
eheheh .. awesome

---

### Post by ventrical on 2017-03-03
> **elopio said:**
> Hello!

I have been testing our end-to-end workflow from packaging a snap to continuous delivery to the store using IPFS. 

IPFS is a really interesting free project for distributed storage. You can read more about it and watch a demo here:

pura vida.

That was refreshing :)

Regards..

---

### Post by howefield on 2017-03-03
Tested in Xenial wIth Yakkety HWE.

2 errors..
```
ipfs cat /ipfs/$hash/readme
Error: path must contain at least one component
```
and
```
09:26:48.100 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID VdjZbw>) failed: dial attempt failed: context deadline exceeded wantmanager.go:220
```

---

### Post by elopio on 2017-03-03
Awesome. Thanks a lot, again <3

I've asked on #ipfs on freenode about your bitswap issue.

@whyrusleeping | elopio: Yeah... thats indicative of a bug we're trying to track down 
@whyrusleeping | elopio: its nothing to worry about for now, tracking issue is here: [https://github.com/ipfs/go-ipfs/issues/3651](https://github.com/ipfs/go-ipfs/issues/3651)

In launchpad we have a way to mark the bug as affecting us. Github doesn't have that, but you can leave +1 with a thumbs-up emoticon. That gives a sense of how common the bug is. If you have something to add to the discussion there, you can leave a comment.

@howefield, please note that on the readme step you have to replace $hash with the value returned by the ipfs init command. I'm not sure how to make that clearer without being too verbose. It's not clear at all now, so suggestions to improve the gist are also welcome.

pura vida

---

### Post by howefield on 2017-03-03
> **elopio said:**
> In launchpad we have a way to mark the bug as affecting us. Github doesn't have that, but you can leave +1 with a thumbs-up emoticon. That gives a sense of how common the bug is. If you have something to add to the discussion there, you can leave a comment.

Done +1 

> @howefield, please note that on the readme step you have to replace $hash with the value returned by the ipfs init command. I'm not sure how to make that clearer without being too verbose. It's not clear at all now, so suggestions to improve the gist are also welcome.

Ooops, sorry about that, I should have been able to work that out.. :redface:

---

### Post by elopio on 2017-03-06
I wrote about the continuous delivery of IPFS to Ubuntu: [http://elopio.net/blog/ipfs-crowdtesting/](http://elopio.net/blog/ipfs-crowdtesting/)

---

### Post by howefield on 2017-03-07
Nice post elopio and good read, many thanks.

---

### Post by elopio on 2017-03-21
Hello!

IPFS 0.4.7 was released last week. I have just pushed it to the
candidate channel. Sorry for the delay, I have been slacking a little
here.

If you have a few spare minutes, please help running the update tests
to make sure we can push this version safely to the stable channel:
[https://gist.github.com/elopio/7492a28bd1aef6c4a86b5dcf5d5cb65b#file-ipfs-update-tests-md](https://gist.github.com/elopio/7492a28bd1aef6c4a86b5dcf5d5cb65b#file-ipfs-update-tests-md)

Let me know how it goes :)

---

### Post by howefield on 2017-03-25
> **elopio said:**
> Let me know how it goes :)

Just getting some time to test, all appeared to work as it should although terminal spammed with messages such as

```
09:01:35.795 ERROR       mdns: mdns lookup error: failed to bind to any unicast udp port mdns.go:135
09:01:54.595 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID RcT1Wd>) failed: dial attempt failed: failed to add conn to ps.Swarm: read tcp6 [2a02:c7f:8e38:e200:6999:cf73:4ba9:4b75]:51644->[2001:4b98:dc0:41:216:3eff:feb8:3e1a]:4001: i/o timeout wantmanager.go:233
09:01:55.795 ERROR       mdns: mdns lookup error: failed to bind to any unicast udp port mdns.go:135
```

---

### Post by elopio on 2017-03-27
Thanks howefield!
If you search those error messages in [https://github.com/ipfs/go-ipfs/issues](https://github.com/ipfs/go-ipfs/issues) you will find a few bugs already reported, and they are working on those. If you want to contribute with the upstream team, you can attach your logs to the bugs that seem more closely related to what you are experiencing.

pura vida.

---

### Post by cariboo on 2017-03-27
I ran the test this morning, and it came up with quite a few errors.

```
11:09:15.105 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID ZjAgBd>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID ZjAgBd> dial attempt failed: dial tcp4 172.17.0.2:4001: i/o timeout wantmanager.go:233
11:09:15.365 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID VjEQAU>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:17.448 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID NnMBRw>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:17.449 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID Uv4itV>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID Uv4itV> dial attempt failed: dial tcp6 [::2]:4001: connect: network is unreachable wantmanager.go:233
11:09:19.306 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID ZTEqmm>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID ZTEqmm> dial attempt failed: dial tcp6 [fc54:8329:2fd7:7a:37b7:53d4:d339:939c]:4001: connect: network is unreachable wantmanager.go:233
11:09:19.911 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID bPfWMB>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:20.468 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID d8vvkW>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID d8vvkW> dial attempt failed: connection refused wantmanager.go:233
11:09:20.988 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID UgNCzh>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID UgNCzh> dial attempt failed: connection refused wantmanager.go:233
11:09:21.621 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID dLgCyX>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID dLgCyX> dial attempt failed: connection refused wantmanager.go:233
11:09:21.920 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID WmJfJK>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID WmJfJK> dial attempt failed: connection refused wantmanager.go:233
11:09:23.787 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID bE4S5E>) failed: dial attempt failed: misdial to <peer.ID bE4S5E> through /ip4/127.0.0.2/tcp/4001 (got <peer.ID evA9Qx>): read tcp 127.0.0.1:4001->127.0.0.2:4001: use of closed network connection wantmanager.go:233
11:09:23.891 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID dsoQ8x>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:24.161 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID R1mXyi>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:25.748 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID Uyo4YP>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:25.852 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID PeCS6U>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID PeCS6U> dial attempt failed: dial tcp6 [2a01:7e01::f03c:91ff:fe9b:b8f3]:4001: connect: network is unreachable wantmanager.go:233
11:09:26.028 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID PRB9SN>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:26.526 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID evzdCP>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:26.796 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID Z86ow1>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID Z86ow1> dial attempt failed: connection refused wantmanager.go:233
11:09:27.363 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID PxgtHF>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID PxgtHF> dial attempt failed: connection refused wantmanager.go:233
11:09:29.482 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID bmA3sM>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID bmA3sM> dial attempt failed: dial tcp6 [fd42:d54a:6d3f:7576::1]:4001: connect: network is unreachable wantmanager.go:233
11:09:30.037 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID fM9xyC>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:30.312 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID YfXkBF>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:33.045 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID e9kKrt>) failed: session shutdown wantmanager.go:233
11:09:33.189 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID cFnB8b>) failed: session shutdown wantmanager.go:233
11:09:33.302 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID U355Sf>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID U355Sf> dial attempt failed: dial tcp6 [2604:a880:400:d0::828:6001]:4001: connect: network is unreachable wantmanager.go:233
11:09:33.846 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID UAB7eq>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:33.917 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID Zxeotf>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:35.322 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID cfmjwC>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:35.322 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID e2DQ3g>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID e2DQ3g> dial attempt failed: dial tcp4 188.98.206.76:4001: i/o timeout wantmanager.go:233
11:09:36.521 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID W2XWsn>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:37.504 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID Nz4kQs>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID Nz4kQs> dial attempt failed: i/o timeout wantmanager.go:233
11:09:38.126 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID aykFUP>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:38.685 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID YfmBh8>) failed: session shutdown wantmanager.go:233
11:09:38.743 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID R1d22Y>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID R1d22Y> dial attempt failed: dial tcp6 [2001:19f0:7001:20e7:5400:ff:fe49:67aa]:4001: connect: network is unreachable wantmanager.go:233
11:09:38.863 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID bWKGFp>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:39.476 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID VPq1mj>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:39.813 ERROR       mdns: mdns lookup error: failed to bind to any unicast udp port mdns.go:135
11:09:40.585 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID P13QaQ>) failed: session shutdown wantmanager.go:233
11:09:40.645 ERROR     flatfs: too many open files, retrying in 100ms flatfs.go:180
11:09:40.745 ERROR     flatfs: too many open files, retrying in 200ms flatfs.go:180
11:09:40.946 ERROR     flatfs: too many open files, retrying in 300ms flatfs.go:180
11:09:41.011 ERROR     flatfs: too many open files, retrying in 100ms flatfs.go:180
11:09:41.012 ERROR     flatfs: too many open files, retrying in 100ms flatfs.go:180
11:09:41.066 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID bPFhS9>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID bPFhS9> dial attempt failed: connection refused wantmanager.go:233
11:09:41.107 ERROR     flatfs: too many open files, retrying in 100ms flatfs.go:180
11:09:41.111 ERROR     flatfs: too many open files, retrying in 200ms flatfs.go:180
11:09:41.113 ERROR     flatfs: too many open files, retrying in 200ms flatfs.go:180
11:09:41.129 ERROR     flatfs: too many open files, retrying in 100ms flatfs.go:180
11:09:41.373 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID cP8J9x>) failed: session shutdown wantmanager.go:233
11:09:41.517 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID Tv99La>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:41.520 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID UJapsx>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID UJapsx> dial attempt failed: connection refused wantmanager.go:233
11:09:41.520 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID SMSC9S>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID SMSC9S> dial attempt failed: dial tcp4 58.83.219.152:4001: i/o timeout wantmanager.go:233
11:09:42.052 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID bTnF8g>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID bTnF8g> dial attempt failed: dial tcp6 [2a01:4f8:162:14d0::2]:4001: connect: network is unreachable wantmanager.go:233
11:09:42.298 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID XVgWdf>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID XVgWdf> dial attempt failed: dial tcp6 [2a03:b0c0:3:d0::2fe9:7001]:56349: connect: network is unreachable wantmanager.go:233
11:09:42.440 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID dKc2md>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:43.017 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID bGfW4U>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:43.161 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID eMsvVh>) failed: session shutdown wantmanager.go:233
11:09:43.230 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID WyLSnM>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID WyLSnM> dial attempt failed: dial tcp6 [2604:a880:800:a1::79d:1001]:4001: connect: network is unreachable wantmanager.go:233
11:09:43.230 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID SoLMeW>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID SoLMeW> dial attempt failed: dial tcp6 [2a03:b0c0:1:d0::e7:1]:4001: connect: network is unreachable wantmanager.go:233
11:09:43.230 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID TaqVy1>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID TaqVy1> dial attempt failed: dial tcp6 [fda7:77f5:dfa6:c259:7989:4337:66e9:f8f9]:4001: connect: network is unreachable wantmanager.go:233
11:09:43.230 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID bBktuT>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID bBktuT> dial attempt failed: dial tcp6 [2a03:4000:6:3218::4]:4001: connect: network is unreachable wantmanager.go:233
11:09:43.318 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID YyGrx4>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID YyGrx4> dial attempt failed: dial tcp6 [::ac15:101]:4001: connect: network is unreachable wantmanager.go:233
11:09:43.342 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID Nn8JBK>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID Nn8JBK> dial attempt failed: dial tcp6 [2604:180:1:2a3::db76]:53728: connect: network is unreachable wantmanager.go:233
11:09:43.376 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID YrLf6B>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:43.473 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID WTyP5F>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID WTyP5F> dial attempt failed: dial tcp6 [2a02:908:1060:2f00:725a:b6ff:fe4a:a50f]:4001: connect: network is unreachable wantmanager.go:233
11:09:44.529 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID bJgvyh>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID bJgvyh> dial attempt failed: connection refused wantmanager.go:233
11:09:46.468 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID cefwkE>) failed: dial attempt failed: context deadline exceeded wantmanager.go:233
11:09:46.761 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID Tt8KxY>) failed: session shutdown wantmanager.go:233
11:09:49.813 ERROR       mdns: mdns lookup error: failed to bind to any unicast udp port mdns.go:135
11:09:49.826 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID WjZ7en>) failed: session shutdown wantmanager.go:233
11:09:50.256 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID VvWyHB>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID VvWyHB> dial attempt failed: dial tcp6 [2001:41d0:302:2100::63ae]:51086: connect: network is unreachable wantmanager.go:233
11:09:55.061 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID ep8Lti>) failed: session shutdown wantmanager.go:233
11:09:59.813 ERROR       mdns: mdns lookup error: failed to bind to any unicast udp port mdns.go:135
11:10:02.858 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID R7ihAg>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID R7ihAg> dial attempt failed: dial tcp4 92.167.228.248:50334: socket: too many open files wantmanager.go:233
11:10:21.957 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID ZVUo6V>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID ZVUo6V> dial attempt failed: dial tcp6 [2a01:7e00::f03c:91ff:fedb:9693]:4001: connect: network is unreachable wantmanager.go:233
11:10:22.267 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID XsfKno>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID XsfKno> dial attempt failed: connection refused wantmanager.go:233
11:10:24.633 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID aRqhCF>) failed: dial attempt failed: <peer.ID evA9Qx> --> <peer.ID aRqhCF> dial attempt failed: dial tcp4 177.55.224.253:4001: socket: too many open files wantmanager.go:233
11:10:34.189 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID SoLer2>) failed: dial attempt failed: failed to add conn to ps.Swarm: read tcp4 192.168.0.104:33558->178.62.158.247:4001: i/o timeout wantmanager.go:233
11:10:35.523 ERROR    bitswap: couldnt open sender again after SendMsg(<peer.ID fJ4cFr>) failed: dial attempt failed: failed to add conn to ps.Swarm: read tcp4 192.168.0.104:42768->5.9.14.80:4001: i/o timeout wantmanager.go:233
```

and

```
sensible-browser http://localhost:5001/webui
[10281:10281:0327/110847.474782:ERROR:child_thread_impl.cc(762)] Request for unknown Channel-associated interface: ui::mojom::GpuMain
```

---

