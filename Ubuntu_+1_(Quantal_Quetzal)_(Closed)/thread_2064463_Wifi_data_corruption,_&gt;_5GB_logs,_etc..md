---
title: "Wifi data corruption, &gt; 5GB logs, etc."
date: 2012-09-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by dpc.ucore.info on 2012-09-29
After upgrading to 12.10 I'm strugling with wifi not working properly.

I tried two Pentagram usb wifi cards that I own (different models) and both are experiencing same issues. When I use LAN cable the problem does not happen.

When using wifi, I notice the files I download are often corrupted (wrong checksums etc.), the images in browser are corrupted as well.

From time to time the Internet connection seem to stop working and my logs are getting flooded with:

```
[ 9632.341103] ------------[ cut here ]------------
[ 9632.341105] WARNING: at /build/buildd/linux-3.5.0/net/ipv4/tcp.c:1612 tcp_recvmsg+0xbb5/0xce0()
[ 9632.341106] Hardware name: To Be Filled By O.E.M.
[ 9632.341107] recvmsg bug 2: copied A0A02E84 seq A0A02E84 rcvnxt A0A02EFE fl 0
[ 9632.341107] Modules linked in: ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs reiserfs ext2 sit tunnel4 xt_recent xt_tcpudp xt_LOG nf_conntrack_ipv6 nf_defrag_ipv6 nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ip6table_filter ip6_tables iptable_filter ip_tables x_tables dm_crypt pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) joydev snd_hda_codec_hdmi snd_hda_codec_via pl2303 kvm_amd usbserial r8712u(C) kvm hid_logitech_dj microcode snd_hda_intel snd_hda_codec snd_hwdep snd_pcm edac_core edac_mce_amd snd_seq_midi k10temp snd_rawmidi sp5100_tco snd_seq_midi_event i2c_piix4 psmouse snd_seq serio_raw snd_timer snd_seq_device rfcomm fglrx(PO) bnep mac_hid bluetooth snd parport_pc soundcore snd_page_alloc ppdev w83627ehf hwmon_vid nfsd nfs lp lockd parport fscache auth_rpcgss nfs_acl binfmt_misc sunrpc btrfs zlib_deflate libcrc32c usbhid hid uas usb_storage pata_atiixp r8169 wmi
[ 9632.341137] Pid: 28855, comm: Chrome_IOThread Tainted: P        WC O 3.5.0-15-generic #23-Ubuntu
[ 9632.341138] Call Trace:
[ 9632.341140]  [<ffffffff81051cbf>] warn_slowpath_common+0x7f/0xc0
[ 9632.341143]  [<ffffffff81051db6>] warn_slowpath_fmt+0x46/0x50
[ 9632.341145]  [<ffffffff815b5bb5>] tcp_recvmsg+0xbb5/0xce0
[ 9632.341147]  [<ffffffff81047f1f>] ? native_flush_tlb_others+0x12f/0x140
[ 9632.341149]  [<ffffffff815d98db>] inet_recvmsg+0x6b/0x80
[ 9632.341152]  [<ffffffff8155ae32>] sock_aio_read.part.8+0x142/0x170
[ 9632.341154]  [<ffffffff8155ae85>] sock_aio_read+0x25/0x40
[ 9632.341156]  [<ffffffff81181b96>] do_sync_read+0xe6/0x120
[ 9632.341158]  [<ffffffff812b3132>] ? security_file_permission+0x92/0xb0
[ 9632.341160]  [<ffffffff81182051>] ? rw_verify_area+0x61/0xf0
[ 9632.341162]  [<ffffffff8118259d>] vfs_read+0x15d/0x180
[ 9632.341163]  [<ffffffff8118260a>] sys_read+0x4a/0x90
[ 9632.341166]  [<ffffffff81689ced>] system_call_fastpath+0x1a/0x1f
[ 9632.341167] ---[ end trace c4575c8b9e16be8e ]---
```

The log size can quickly fill up the whole disk (10GB and more).

Most of the time I also see messages like this:

```
[ 2177.981510] IPv4: martian source 192.168.1.105 from 213.180.138.10, on dev wlan0
[ 2177.981529] ll header: 00000000: 00 02 72 93 68 78 b0 48 7a 97 c5 18 08 00        ..r.hx.Hz.....
[ 2178.396552] IPv4: martian source 192.168.1.105 from 213.180.138.10, on dev wlan0
[ 2178.396564] ll header: 00000000: 00 02 72 93 68 78 b0 48 7a 97 c5 18 08 00        ..r.hx.Hz.....
[ 2179.218203] IPv4: martian source 192.168.1.105 from 193.219.28.26, on dev wlan0
[ 2179.218216] ll header: 00000000: 00 02 72 93 68 78 b0 48 7a 97 c5 18 08 00        ..r.hx.Hz.....
[ 2179.226546] IPv4: martian source 192.168.1.105 from 213.180.138.10, on dev wlan0
[ 2179.226558] ll header: 00000000: 00 02 72 93 68 78 b0 48 7a 97 c5 18 08 00        ..r.hx.Hz.....
```

---

### Post by Louisraritan on 2012-09-29
Having the same problem.  Wired networking is fine but wireless is sporadic.  Also, have you noticed that the update gui isn't working?  Ive been using command line update.  Was having sound problems too.  The second two probs don't bug me so much but would really like to get wireless running again.

---

