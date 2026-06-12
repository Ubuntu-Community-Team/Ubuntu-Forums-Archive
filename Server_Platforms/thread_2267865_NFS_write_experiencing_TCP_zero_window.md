---
title: "NFS write experiencing TCP zero window"
date: 2015-03-04
forum: Server Platforms
---

### Post by ian77 on 2015-03-04
My laptop mounts NFS shares on my home media server. Reads from the shares are perfect, but writes are awfully slow.
When I upload to the server using a different protocol such as SFTP it works perfect. When I transfer files internally on the server it works perfect.

So I'm pretty confident the issue is isolated to the NFS protocol.

**Network**
100Mbps wired connection.
No duplex mismatch

**Symptoms**
Classic TCP window size zero symptoms. Initial file transfer starts at normal speed and gradually slow and slow and slows until it hits 0 and stops for a while. Then speeds up and slows down and repeats this cycle.

**Wireshark**
Wireshark shows the server transmitting a TCP ZeroWindow packet, shortly followed by a client keepalive.

**Server Load**
Monitoring the server (with dstat) shows it's idle when the connection drops to zero. 

**/etc/exports**
Example of an export:
*/data/music             ian(rw) ian2(rw)*

**/etc/fstab**
Example of stab from client:
biscuit:/data/music     /data/mounts/music      nfs     users,rw,auto, 0 0


Need help with troubleshooting and resolving this issue please.

Cheers,

Ian

---

### Post by nerdtron on 2015-03-06
try adding "sync" option on your nfs mount options and exports file. See it makes a difference.

---

### Post by ian77 on 2015-03-06
Thanks,

I enabled the *sync* and *no_wdelay* options on my shares and performance seems to have improved. I wouldn't say it's perfect and the speed is a little unstable, but it's much, much better than it was.

Cheers

---

### Post by ian77 on 2015-03-11
tried uploading around 40GB of data in one go to my otherwise idle home server, within about 5 seconds of the transfer starting it dropped out to 0MiB/sec. So still experiencing the same problem.
Any further suggestions?

cheers

---

### Post by ian77 on 2015-03-21
Still experiencing terrible performance with NFS on my server. I have completed some more testing:

**Live Linux Distros**
I booted from 2 linux distros. OpenSUSE KDE, Mint Cinnamon. Two different file managers.
Both still experiencing the same terrible write performance when writing to my server. Often hitting 0B/s. Witnessed transfer stalling from both client and server.

Instead of copying with the file manager, I tried copying to the server with dd over NFS.

Transfered 1GB with an average speed of 2MB/s.

**NFS v3**
I disabled NFSv4 by editing /etc/default/nfs-kernel-server as follows:

# Options for rpc.mountd.
# If you have a port-based firewall, you might want to set up
# a fixed port here using the --port option. For more information,
# see rpc.mountd(8) or [http://wiki.debian.org/SecuringNFS](http://wiki.debian.org/SecuringNFS)
# To disable NFSv4 on the server, specify '--no-nfs-version 4' here
RPCMOUNTDOPTS="--manage-gids **--no-nfs-version 4**"

I then restarted the service.

However, when observing the transfer with wireshark, I can see NFSv4 packets being used for the client and server to communicate....

Getting pretty frustrated with Ubuntu server now. I know this is a good sever, I've been using without any issues in the past. However, somethnig is obviously wrong with it now.
Either I'm doing something obviously stupid, or there's a bug somewhere.

Any further help or suggestions would be appreciated.

Cheers,

Ian

---

### Post by SeijiSensei on 2015-03-21
Is there some reason you're using TCP rather than the usual UDP? Usually the latter has better performance.

---

### Post by ian77 on 2015-03-22
I use TCP because I want reliable, connection orientated data transfer to my server.
EDIT: Also experiencing this issue with NFSv3 (forced it from client end).

Opened a bug for this issue: #1434996

---

### Post by SeijiSensei on 2015-03-22
If this is running over a local network, UDP is the preferred method.  There's no reason to impose the overhead of "ACK" packets that TCP requires.  I've used NFS over UDP for decades without any problems.

If you are having problems with write performance, try disabling sync on the server by adding "async" to the options list in /etc/exports.

---

### Post by lukeiamyourfather on 2015-03-23
> **SeijiSensei said:**
> If you are having problems with write performance, try disabling sync on the server by adding "async" to the options list in /etc/exports.

Yes, what SeijiSensei said. NFS defaults to sync writes which come with a hefty performance impact. Using async writes will probably get you close to wire speed, around 12 MB/s with the network you describe (Fast Ethernet). The trade-off is data could be lost if the server has issues (like power interruption) before async writes are transferred from memory to the drive(s) and applications on the client side would think the writes were made successfully. In a home use scenario this is typically not an issue.

---

### Post by SeijiSensei on 2015-03-23
> **lukeiamyourfather said:**
> In a home use scenario this is typically not an issue.
Connecting the server to an uninterruptbile power supply is also a good way to protect against possible data loss when using async.

I've used async for years and never experienced data loss in practice, but I have a UPS.

---

### Post by ian77 on 2015-03-23
Thanks for the help guys.

I modified one of my shares with the async option as described.

When I uploaded some test data I can see the upload speed is much better. It does vary a bit, but it much more acceptable.
However I did notice the server was still spitting out TCP Zero Window packets. I don't think it should be doing this as the server is not under any pressure.

I uploaded the same test data to one of my other shares which still had the sync option enabled. The data transfer started ok but then stalled. The transfer hung for 50 seconds before restarting.
I appreciate that the sync option might impact performance, but it shouldn't be stopping a connection for 50 seconds for no reason.

My server is connected to a UPS so happy to have async enabled, and will monitor it to see how it goes. But I would still prefer using the sync option even if it did mean a little worse write performance.

Will see how I get on.

Thanks again.

---

### Post by SeijiSensei on 2015-03-23
> **ian77 said:**
> I appreciate that the sync option might impact performance, but it shouldn't be stopping a connection for 50 seconds for no reason.

I've seen delays like that; it's why I stopped using sync.  With sync enabled, the server fills a buffer with the inbound data, then blocks the connection while the data is written to disk.  

I'll just say again that I have used NFS over UDP with async for over two decades and never had a problem with data loss.

---

### Post by lukeiamyourfather on 2015-03-24
What kind of hardware are you working with? What is the underlying storage system?

---

### Post by ian77 on 2015-03-24
**Hardware**
dual core atom @ 1.66Ghz
4GB DDR2 Memory
4x 1TB 7,200 RPM Hitachi HUA72201


**Storage Config**
3x partitions for swap, root and data.
software raid 5 across 4 x 1TB disks as above. Using mdadm.
btrfs v3.12 filesystem.

I also have a 4TB backup disk which can copy files to the main filesystem at normal speeds with no delays or pauses.



> **SeijiSensei said:**
> With sync enabled, the server fills a buffer with the inbound data, then blocks the connection while the data is written to disk.  

Playing devil's advocate here, but that doesn't seem like a very good way or working & surely even sftp tranfers will use a buffer too? I don't get a problem with that. The buffer should be getting flushed to disk in a timely manner without interrupting the TCP connection. It's not like the disks are busy.

I have around 3.5GB of free memory. The tranfers sometimes halt after a few seconds, which means NFS has a buffer size of 50MB...
I don't know. Something doesn't seem right....

Anyway, happy to keep using async for now. Need to keep TCP for when I'm using my UDP VPN.

Thanks again for the help :-)

---

### Post by lukeiamyourfather on 2015-03-25
> **ian77 said:**
> dual core atom @ 1.66Ghz

> **ian77 said:**
> software raid 5 across 4 x 1TB disks as above. Using mdadm.

The performance you're getting is on par with what to expect from that hardware combined with Linux software RAID. Even on the fastest of hardware Linux software RAID is terribly slow compared to other options. In general ZFS on Linux performs much better than Linux software RAID but it requires ECC memory which the Atom processor doesn't support.  Maybe look at ZFS on Linux or a hardware RAID controller in the future if you're after more performance.

---

