---
title: "NFS lockd &amp; statd problems with MAC client over OpenVPN"
date: 2010-12-08
forum: Server Platforms
---

### Post by sabhain on 2010-12-08
Hello All,

I'm working through a problem that I can't seem to find recent discussion of.  That usually means the solution is something really simple that I just haven't tried.

I have a 10.10 server running in one facility.  On that server, I have exported an NFS share.  I am running OpenVPN on the server to enable a single user to access some server side things remotely, namely an HTTP app & the NFS share.

The OpenVPN pipe has been reliable and stable as best I can tell.  The user is able to connect without difficulty and use the HTTP resource, ssh in works well, as does NFS mounting.

The remote client is using a MAC (OS X 10.6.5 as I understand it).

He is able to mount the NFS share without trouble.

He is able to create directories in the share (where he is permitted) without trouble.

He is NOT able to create files in the share or within his directory.  It tries to past the file, but he gets an error on his end that "Error -36: some of the information cannot be read or written."  I'm chasing this hard from both ends, working the MAC forums as well.  No luck yet.

In reviewing the server logs, I'm getting Statd & Lockd errors.  This seems to match some of what I'm finding on the MAC side which indicates the file transfer isn't working because the MAC isn't able to lock the file correctly until it is done writing.

From /var/log/messages, I'm seeing a lot of repeating messages like:

kernel: [3046485.158883] lockd: cannot monitor {iMac Machine Name (NOT IP)}

In /var/log/daemon.log, I get the following every time we have a failed write attempt:

rpc.statd[750]: No canonical hostname found for 5.5.8.13
rpc.statd[750]: STAT_FAIL to {servername} for SM_MON of 5.5.8.13

The IP in the second batch of messages corresponds to the MAC machine trying to write the file.

My question is whether or not the lockd & statd are failing to connect the machine name to the IP, and why one would get the name, and the other the IP.

I'm in the midst of trying this with an entry in the server's host file to rationalize the two, but this may not be a viable long term solution, as every time he connects his remote client, it receives a new IP address.  We've tried static IPs on the OpenVPN end, but it wreaks havoc on the MAC with routing of packets not intended for the VPN.

Has anyone encountered this?  I have lots of NFS clients within the same subnet accessing this NFS share without trouble (all Ubuntu clients), and none of them are defined in the host file in either direction, we do the share all with IP, not hostname.  So I'm aware that a variable here is that it's through a VPN.  But since he can mount, copy and create folders .. I figure there's a small thing here that I'm overlooking.

Thank you for your time & consideration of my problem.

---

