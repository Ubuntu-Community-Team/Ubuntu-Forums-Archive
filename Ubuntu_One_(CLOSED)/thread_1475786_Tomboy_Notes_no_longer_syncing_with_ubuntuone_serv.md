---
title: "Tomboy Notes no longer syncing with ubuntuone server"
date: 2010-05-07
forum: Ubuntu One (CLOSED)
---

### Post by tekstr1der on 2010-05-07
As in the title...Syncing stopped working a few days ago. I removed and re-added my computer account as per workaround in the following bug:

Tomboy 1.2.1 can't synchronize Notes to ubuntuone Server not found (404)  
[https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/575937](https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/575937)
 
But this had no effect for me. I still cannot sync notes. Here's what I get when I try:

```

:~$ tomboy
[INFO 08:09:54.286] Initializing Mono.Addins
[ERROR 08:09:59.183] Caught exception. Message: The remote server returned an error: (500) INTERNAL SERVER ERROR.
[ERROR 08:09:59.185] Stack trace for previous exception:   at System.Net.HttpWebRequest.CheckFinalStatus (System.Net.WebAsyncResult result) [0x00000] 
  at System.Net.HttpWebRequest.SetResponseData (System.Net.WebConnectionData data) [0x00000] 
[ERROR 08:09:59.187] Rest of stack trace for above exception:    at System.Environment.get_StackTrace()
   at Tomboy.WebSync.Api.OAuth.MakeWebRequest(RequestMethod method, System.String url, System.Collections.Generic.List`1 parameters, System.String postData)
   at Tomboy.WebSync.Api.OAuth.WebRequest(RequestMethod method, System.String url, System.String postData)
   at Tomboy.WebSync.Api.OAuth.Get(System.String uri, IDictionary`2 queryParameters)
   at Tomboy.WebSync.Api.UserInfo.GetUser(System.String userUri, IWebConnection connection)
   at Tomboy.WebSync.WebSyncServer.BeginSyncTransaction()
   at Tomboy.Sync.SyncManager.SynchronizationThread()
[ERROR 08:09:59.188] Synchronization failed with the following exception: The remote server returned an error: (500) INTERNAL SERVER ERROR.
  at System.Net.HttpWebRequest.CheckFinalStatus (System.Net.WebAsyncResult result) [0x00000] 
  at System.Net.HttpWebRequest.SetResponseData (System.Net.WebConnectionData data) [0x00000] 

(tomboy:1890): GLib-CRITICAL **: g_source_remove: assertion `tag > 0' failed 
```

---

