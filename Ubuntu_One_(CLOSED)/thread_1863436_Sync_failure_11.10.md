---
title: "Sync failure 11.10"
date: 2011-10-17
forum: Ubuntu One (CLOSED)
---

### Post by HereInOz on 2011-10-17
Hi All,

I have recently built a laptop with 11.10 (was running successfully with 11.04 but I did a clean install to 11.10)

I have had an issue with Ubuntu One syncing, where it takes a long time to sync a small file, and almost never will sync a large file.

The error I am getting in my syncdaemon.log file is:

2011-10-18 09:56:06,615 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING  connection 'With User With Network')>; queue: 1; hash: 0) ----
2011-10-18 09:58:06,615 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING  connection 'With User With Network')>; queue: 1; hash: 0) ----
2011-10-18 09:59:28,589 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Download                     share:''                                       node:'01e1aaa9-cd95-459e-841a-4848325ed38f'   Download(path="'/home/raenalan/Ubuntu One/Utilities/AV/setup_av_free_cnet.exe'", running='False', share_id="''", node_id="'01e1aaa9-cd95-459e-841a-4848325ed38f'", server_hash="'sha1:ff631cb93a31b362a670d5b790fd86b7f6a4b508'") failure: TRY_AGAIN

It just repeats this message over and over again.

Hope there is someone who can assist with this.  

One other thing which is perhaps mentioning is that I used the same hostname for the new installation as I did for the previous installation.  I did remove the original computer from the list of synced computers, and then added the new installation, but I do wonder if this is causing my problems.

Any ideas?

Alan

---

