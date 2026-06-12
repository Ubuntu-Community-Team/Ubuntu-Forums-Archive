---
title: "[DRBD] State change failed: Refusing to be Outdated while Connected"
date: 2017-11-06
forum: Server Platforms
---

### Post by gkooistrago on 2017-11-06
Last weekend, after rebooting one of our servers, the DRBD synced data from the other server (s1) to the just rebooted server (s0).
The big problem was that both servers didn’t sync the data for multiple weeks, so the s1 was syncing old data to the s0. But why?

In the logfiles, I found the next messages:


```

drbd r1/0 drbd1: Digest integrity check FAILED: 760605752s +4096
drbd r1 s1: error receiving P_DATA, e: -5 l: 4112!
drbd r1 s1: conn( Connected -> ProtocolError ) peer( Primary -> Unknown )
drbd r1/0 drbd1: disk( UpToDate -> Consistent )
drbd r1/0 drbd1 s1: pdsk( UpToDate -> DUnknown ) repl( Established -> Off )
drbd r1 s1: ack_receiver terminated
drbd r1 s1: Terminating ack_recv thread
drbd r1: Preparing cluster-wide state change 4154999068 (1->-1 0/0)
drbd r1: Committing cluster-wide state change 4154999068 (0ms)
drbd r1/0 drbd1: disk( Consistent -> UpToDate )
drbd r1 s1: Connection closed
drbd r1 s1: conn( ProtocolError -> Unconnected )
drbd r1 s1: Restarting receiver thread
drbd r1 s1: conn( Unconnected -> Connecting )
drbd r1 s1: Handshake to peer 0 successful: Agreed network protocol version 112
drbd r1 s1: Feature flags enabled on protocol level: 0x7 TRIM THIN_RESYNC WRITE_SAME.
drbd r1 s1: Starting ack_recv thread (from drbd_r_r1 [4359])
drbd r1 s1: Preparing remote state change 3794016712 (primary_nodes=0, weak_nodes=0)
drbd r1 s1: Committing remote state change 3794016712
drbd r1 s1: conn( Connecting -> Connected ) peer( Unknown -> Primary )
drbd r1/0 drbd1 s1: drbd_sync_handshake:
drbd r1/0 drbd1 s1: self 1BD26E1067B0E940:0000000000000000:4C11B7036A2ED69C:74BE9052677C4A5C bits:0 flags:120
drbd r1/0 drbd1 s1: peer 1BD26E1067B0E941:0000000000000000:4C11B7036A2ED69C:74BE9052677C4A5C bits:228 flags:120
drbd r1/0 drbd1 s1: uuid_compare()=0 by rule 38
drbd r1/0 drbd1 s1: pdsk( DUnknown -> UpToDate ) repl( Off -> Established )
drbd r1/0 drbd1 s1: receive bitmap stats [Bytes(packets)]: plain 0(0), RLE 144(1), total 144; compression: 100.0%
drbd r1/0 drbd1 s1: unexpected repl_state (Established) in receive_bitmap
drbd r1: State change failed: Refusing to be Outdated while Connected
drbd r1/0 drbd1: Failed: disk( UpToDate -> Outdated )
drbd r1/0 drbd1: ASSERT FAILED cstate = Established, expected: WFSyncUUID|WFBitMapT|Behind
drbd r1/0 drbd1: ASSERT FAILED cstate = Established, expected: WFSyncUUID|WFBitMapT|Behind
drbd r1/0 drbd1: ASSERT FAILED cstate = Established, expected: WFSyncUUID|WFBitMapT|Behind
drbd r1/0 drbd1: ASSERT FAILED cstate = Established, expected: WFSyncUUID|WFBitMapT|Behind
drbd r1/0 drbd1: ASSERT FAILED cstate = Established, expected: WFSyncUUID|WFBitMapT|Behind
.....

```

Has someone an idea to prevent this issue.

Version information:
DRBDADM_API_VERSION=2
DRBD_KERNEL_VERSION_CODE=0x090009
DRBD_KERNEL_VERSION=9.0.9
DRBDADM_VERSION_CODE=0x090101
DRBDADM_VERSION=9.1.1

---

