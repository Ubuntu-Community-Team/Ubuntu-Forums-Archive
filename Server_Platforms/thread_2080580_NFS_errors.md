---
title: "NFS errors"
date: 2012-11-04
forum: Server Platforms
---

### Post by dannyboy79 on 2012-11-04
I was trying to help someone else with some stale NFS issues and I find the following errors in the dmesg of the server and the client

server
```
[96300.013041] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[96300.013069] __ratelimit: 1 callbacks suppressed
[96300.013073] nfsd: peername failed (err 107)!
[96300.013168] nfsd: peername failed (err 107)!
[96300.013181] nfsd: peername failed (err 107)!
[96300.013612] nfsd: peername failed (err 107)!
[96300.013631] nfsd: peername failed (err 107)!
[96300.013647] nfsd: peername failed (err 107)!
[96300.013662] nfsd: peername failed (err 107)!
[96300.013678] nfsd: peername failed (err 107)!
[96300.013693] nfsd: peername failed (err 107)!
[96300.013709] nfsd: peername failed (err 107)!
[97116.079007] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[97116.079034] __ratelimit: 37 callbacks suppressed
[97116.079038] nfsd: peername failed (err 107)!
[97116.079132] nfsd: peername failed (err 107)!
[97116.079494] nfsd: peername failed (err 107)!
[97116.079514] nfsd: peername failed (err 107)!
[97116.079530] nfsd: peername failed (err 107)!
[97116.079545] nfsd: peername failed (err 107)!
[97116.079560] nfsd: peername failed (err 107)!
[97116.079575] nfsd: peername failed (err 107)!
[97116.079590] nfsd: peername failed (err 107)!
[97116.079605] nfsd: peername failed (err 107)!
[97246.235091] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[97246.235117] __ratelimit: 5 callbacks suppressed
[97246.235122] nfsd: peername failed (err 107)!
[97655.347834] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[97745.660527] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[98120.272216] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[98664.639040] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[99463.522295] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[99463.522324] nfsd: peername failed (err 107)!
[99463.522870] nfsd: peername failed (err 107)!
[99463.522887] nfsd: peername failed (err 107)!
[99463.523113] nfsd: peername failed (err 107)!
[99463.523126] nfsd: peername failed (err 107)!
[99463.523142] nfsd: peername failed (err 107)!
[99463.523153] nfsd: peername failed (err 107)!
[99463.523169] nfsd: peername failed (err 107)!
[99590.263903] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[99916.413778] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[100307.683982] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[100307.684029] nfsd: peername failed (err 107)!
[100307.684246] nfsd: peername failed (err 107)!
[100307.684635] nfsd: peername failed (err 107)!
[100307.684723] nfsd: peername failed (err 107)!
[100307.684740] nfsd: peername failed (err 107)!
[100307.684773] nfsd: peername failed (err 107)!
[100307.684789] nfsd: peername failed (err 107)!
[100307.684837] nfsd: peername failed (err 107)!
[100307.684854] nfsd: peername failed (err 107)!
[100307.684886] nfsd: peername failed (err 107)!
[100861.660799] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[102076.273633] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[102175.976304] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[102340.922183] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[102849.595859] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[102849.595885] __ratelimit: 1 callbacks suppressed
[102849.595890] nfsd: peername failed (err 107)!
[102849.595985] nfsd: peername failed (err 107)!
[103002.808275] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[103002.808301] nfsd: peername failed (err 107)!
[103644.078707] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[103644.078817] nfsd: peername failed (err 107)!
[103644.078926] nfsd: peername failed (err 107)!
[103644.079546] nfsd: peername failed (err 107)!
[103644.079675] nfsd: peername failed (err 107)!
[103644.079692] nfsd: peername failed (err 107)!
[103644.079709] nfsd: peername failed (err 107)!
[103644.079725] nfsd: peername failed (err 107)!
[103754.328162] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[104251.751080] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[104251.751109] nfsd: peername failed (err 107)!
[104251.751297] nfsd: peername failed (err 107)!
[104251.751715] nfsd: peername failed (err 107)!
[104251.751734] nfsd: peername failed (err 107)!
[104251.751751] nfsd: peername failed (err 107)!
[104251.751766] nfsd: peername failed (err 107)!
[104251.751783] nfsd: peername failed (err 107)!
[104251.751798] nfsd: peername failed (err 107)!
[104251.751814] nfsd: peername failed (err 107)!
[104251.751829] nfsd: peername failed (err 107)!
[104775.000715] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[104973.608276] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[105207.912921] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[105478.147780] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[105729.636163] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[105729.636189] __ratelimit: 9 callbacks suppressed
[105729.636193] nfsd: peername failed (err 107)!
[106168.048283] rpc-srv/tcp: nfsd: got error -104 when sending 8324 bytes - shutting down socket
[106502.776388] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[106502.776416] nfsd: peername failed (err 107)!
[107754.973160] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[107754.973186] nfsd: peername failed (err 107)!
[107754.973280] nfsd: peername failed (err 107)!
[107754.973804] nfsd: peername failed (err 107)!
[107754.973824] nfsd: peername failed (err 107)!
[107754.973840] nfsd: peername failed (err 107)!
[107754.973872] nfsd: peername failed (err 107)!
[107754.973888] nfsd: peername failed (err 107)!
[107754.973904] nfsd: peername failed (err 107)!
[107754.973919] nfsd: peername failed (err 107)!
[107754.973935] nfsd: peername failed (err 107)!
[107871.297883] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[107871.297910] __ratelimit: 41 callbacks suppressed
[107871.297914] nfsd: peername failed (err 107)!
[200601.172040] usb 2-2: new full speed USB device using uhci_hcd and address 2
[200601.351233] usb 2-2: configuration #1 chosen from 1 choice
[200601.354284] scsi6 : SCSI emulation for USB Mass Storage devices
[200601.354467] usb-storage: device found at 2
[200601.354472] usb-storage: waiting for device to settle before scanning
[200606.353433] usb-storage: device scan complete
[200606.398402] scsi 6:0:0:0: Direct-Access     Verbatim STORE N GO       5.00 PQ: 0 ANSI: 0 CCS
[200606.402723] sd 6:0:0:0: Attached scsi generic sg6 type 0
[200607.551263] sd 6:0:0:0: [sdf] 31272960 512-byte logical blocks: (16.0 GB/14.9 GiB)
[200607.554244] sd 6:0:0:0: [sdf] Write Protect is off
[200607.554252] sd 6:0:0:0: [sdf] Mode Sense: 23 00 00 00
[200607.554257] sd 6:0:0:0: [sdf] Assuming drive cache: write through
[200607.569241] sd 6:0:0:0: [sdf] Assuming drive cache: write through
[200607.569261]  sdf: sdf1
[200607.625221] sd 6:0:0:0: [sdf] Assuming drive cache: write through
[200607.625239] sd 6:0:0:0: [sdf] Attached SCSI removable disk
[201707.859382] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[201749.776771] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[201825.834901] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[201825.834930] nfsd: peername failed (err 107)!
[201893.894062] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[202066.625485] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[203049.247820] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[222846.520069] usb 2-2: USB disconnect, address 2
[232690.098862] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[233071.394455] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[233071.394482] nfsd: peername failed (err 107)!
[233675.585002] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[233953.627364] rpc-srv/tcp: nfsd: got error -104 when sending 8324 bytes - shutting down socket
[234191.431787] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[234191.431814] nfsd: peername failed (err 107)!
[238849.123639] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[238849.123664] nfsd: peername failed (err 107)!
[239036.023171] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[239036.023196] nfsd: peername failed (err 107)!
[241552.827215] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[242049.527591] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[242704.991439] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[242704.991467] nfsd: peername failed (err 107)!
[242704.991566] nfsd: peername failed (err 107)!
[242704.991886] nfsd: peername failed (err 107)!
[242704.991906] nfsd: peername failed (err 107)!
[242704.991922] nfsd: peername failed (err 107)!
[242704.991964] nfsd: peername failed (err 107)!
[242704.991981] nfsd: peername failed (err 107)!
[242704.991996] nfsd: peername failed (err 107)!
[242704.992179] nfsd: peername failed (err 107)!
[242704.992321] nfsd: peername failed (err 107)!
[245250.143409] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[245250.143434] __ratelimit: 14 callbacks suppressed
[245250.143438] nfsd: peername failed (err 107)!
[245250.143538] nfsd: peername failed (err 107)!
[295686.907652] UDP: short packet: From 222.187.24.74:1053 1448/109 to 192.168.0.5:46210
[312460.772527] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[312460.772552] nfsd: peername failed (err 107)!
[312460.773261] nfsd: peername failed (err 107)!
[312460.773669] nfsd: peername failed (err 107)!
[312460.773690] nfsd: peername failed (err 107)!
[312460.773706] nfsd: peername failed (err 107)!
[312460.773722] nfsd: peername failed (err 107)!
[312460.773738] nfsd: peername failed (err 107)!
[312460.773754] nfsd: peername failed (err 107)!
[312460.773770] nfsd: peername failed (err 107)!
[312664.903686] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[312664.903714] __ratelimit: 13 callbacks suppressed
[312664.903718] nfsd: peername failed (err 107)!
[312664.903816] nfsd: peername failed (err 107)!
[312703.383195] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[312771.307973] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[312918.866387] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[313063.778205] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[313063.778231] nfsd: peername failed (err 107)!
[313151.652643] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[313151.652669] nfsd: peername failed (err 107)!
[313151.652762] nfsd: peername failed (err 107)!
[313151.653063] nfsd: peername failed (err 107)!
[315069.899369] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[317388.084070] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[318593.401785] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[319595.514010] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[320256.503368] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[321173.763533] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[322372.758405] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[322556.517011] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[322837.002828] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[323172.208233] rpc-srv/tcp: nfsd: got error -104 when sending 248 bytes - shutting down socket
[323172.208262] nfsd: peername failed (err 107)!
[323234.624041] rpc-srv/tcp: nfsd: got error -104 when sending 248 bytes - shutting down socket
[323267.145464] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[324946.580482] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[325779.388867] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[326496.242336] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[327665.467304] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[363228.055183] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[363297.836501] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[363320.077170] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[363469.891534] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[363469.891559] nfsd: peername failed (err 107)!
[363469.891707] nfsd: peername failed (err 107)!
[363469.892164] nfsd: peername failed (err 107)!
[363469.892186] nfsd: peername failed (err 107)!
[363469.892202] nfsd: peername failed (err 107)!
[363469.892219] nfsd: peername failed (err 107)!
[363469.892235] nfsd: peername failed (err 107)!
[372350.934649] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[372751.471256] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[372751.471282] nfsd: peername failed (err 107)!
[372751.471377] nfsd: peername failed (err 107)!
[372988.790176] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[372988.790203] nfsd: peername failed (err 107)!
[372988.790302] nfsd: peername failed (err 107)!
[372988.790657] nfsd: peername failed (err 107)!
[372988.790789] nfsd: peername failed (err 107)!
[372988.790805] nfsd: peername failed (err 107)!
[373029.004131] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[373186.619131] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[373186.619156] nfsd: peername failed (err 107)!
[373186.619259] nfsd: peername failed (err 107)!
[373300.292681] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[373300.292711] nfsd: peername failed (err 107)!
[373333.510296] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[373603.062559] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[373603.062586] nfsd: peername failed (err 107)!
[373603.062684] nfsd: peername failed (err 107)!
[373603.062995] nfsd: peername failed (err 107)!
[373603.063014] nfsd: peername failed (err 107)!
[536428.204831] UDP: short packet: From 178.17.24.199:11746 57477/109 to 192.168.0.5:46210
[536433.523692] UDP: short packet: From 178.17.24.199:11746 556/109 to 192.168.0.5:46210
[544892.503467] UDP: short packet: From 178.17.24.199:11746 50914/109 to 192.168.0.5:46207
[592328.783535] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[594220.831654] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[595532.303435] rpc-srv/tcp: nfsd: got error -104 when sending 8324 bytes - shutting down socket
[596143.361138] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[596538.462333] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[598212.711765] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[599045.836240] rpc-srv/tcp: nfsd: got error -104 when sending 140 bytes - shutting down socket
[618690.300225] nfsd: last server has exited, flushing export cache
[618692.441982] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[618692.476818] NFSD: starting 90-second grace period

```

and on the client 
```
[308405.224031] nfs: server 192.168.0.5 not responding, still trying
[308405.224078] nfs: server 192.168.0.5 not responding, still trying
[308405.224099] nfs: server 192.168.0.5 not responding, still trying
[308405.224121] nfs: server 192.168.0.5 not responding, still trying
[308405.224145] nfs: server 192.168.0.5 not responding, still trying
[308405.224165] nfs: server 192.168.0.5 not responding, still trying
[308405.224187] nfs: server 192.168.0.5 not responding, still trying
[308405.224207] nfs: server 192.168.0.5 not responding, still trying
[308405.224225] nfs: server 192.168.0.5 not responding, still trying
[308405.224246] nfs: server 192.168.0.5 not responding, still trying
[308405.224268] nfs: server 192.168.0.5 not responding, still trying
[308405.224288] nfs: server 192.168.0.5 not responding, still trying
[308405.224302] nfs: server 192.168.0.5 not responding, still trying
[308405.228544] nfs: server 192.168.0.5 not responding, still trying
[308405.228553] nfs: server 192.168.0.5 not responding, still trying
[308405.228557] nfs: server 192.168.0.5 not responding, still trying
[308418.272822] nfs: server 192.168.0.5 OK
[308418.273875] nfs: server 192.168.0.5 OK
[308418.274016] nfs: server 192.168.0.5 OK
[308418.274144] nfs: server 192.168.0.5 OK
[308418.274161] nfs: server 192.168.0.5 OK
[308418.274170] nfs: server 192.168.0.5 OK
[308418.274178] nfs: server 192.168.0.5 OK
[308418.274185] nfs: server 192.168.0.5 OK
[308418.274195] nfs: server 192.168.0.5 OK
[308418.274204] nfs: server 192.168.0.5 OK
[308418.274213] nfs: server 192.168.0.5 OK
[308418.274221] nfs: server 192.168.0.5 OK
[308418.274230] nfs: server 192.168.0.5 OK
[308418.274237] nfs: server 192.168.0.5 OK
[308418.274245] nfs: server 192.168.0.5 OK
[308418.274253] nfs: server 192.168.0.5 OK
[308464.072026] nfs: server 192.168.0.5 not responding, still trying
[308464.072066] nfs: server 192.168.0.5 not responding, still trying
[308464.072085] nfs: server 192.168.0.5 not responding, still trying
[308464.072104] nfs: server 192.168.0.5 not responding, still trying
[308464.072124] nfs: server 192.168.0.5 not responding, still trying
[308464.072141] nfs: server 192.168.0.5 not responding, still trying
[308464.072161] nfs: server 192.168.0.5 not responding, still trying
[308464.072179] nfs: server 192.168.0.5 not responding, still trying
[308464.072197] nfs: server 192.168.0.5 not responding, still trying
[308464.072217] nfs: server 192.168.0.5 not responding, still trying
[308464.072236] nfs: server 192.168.0.5 not responding, still trying
[308464.076511] nfs: server 192.168.0.5 not responding, still trying
[308464.076527] nfs: server 192.168.0.5 not responding, still trying
[308464.076531] nfs: server 192.168.0.5 not responding, still trying
[308464.076534] nfs: server 192.168.0.5 not responding, still trying
[308464.076537] nfs: server 192.168.0.5 not responding, still trying
[308467.704049] nfs: server 192.168.0.5 OK
[308467.704091] nfs: server 192.168.0.5 OK
[308467.704102] nfs: server 192.168.0.5 OK
[308467.704109] nfs: server 192.168.0.5 OK
[308467.704116] nfs: server 192.168.0.5 OK
[308467.704147] nfs: server 192.168.0.5 OK
[308467.704157] nfs: server 192.168.0.5 OK
[308467.704180] nfs: server 192.168.0.5 OK
[308467.704190] nfs: server 192.168.0.5 OK
[308467.704200] nfs: server 192.168.0.5 OK
[308467.704209] nfs: server 192.168.0.5 OK
[308467.704218] nfs: server 192.168.0.5 OK
[308467.704226] nfs: server 192.168.0.5 OK
[308467.704234] nfs: server 192.168.0.5 OK
[308467.704259] nfs: server 192.168.0.5 OK
[308467.704268] nfs: server 192.168.0.5 OK
[308481.992025] nfs: server 192.168.0.5 not responding, still trying
[308482.849501] nfs: server 192.168.0.5 OK

```

client /etc/fstab
```
192.168.0.5:/media/1tb /media/1tb nfs rsize=32768,wsize=32768,intr,hard
```

server /etc/exports
```
/media/1tb 192.168.0.0/24(rw,no_root_squash,async,no_subtree_check,anonuid=1000)
```

---

