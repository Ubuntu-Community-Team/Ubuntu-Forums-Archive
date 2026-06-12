---
title: "Issue Installing IE8 in Wine - Doesn't Show??"
date: 2010-06-27
forum: Wine
---

### Post by zacharyrs on 2010-06-27
Hi I am now trying to install programs in Wine to use for work. I've done the following listed here ([http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html](http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html)) and i go through the entire install process. It tells me to restart my computer to see the changes.

This is what I have in my terminal - seems to show this for a very long time. It shows a ton of stuff but hangs here?

```

```x00000000,0x33f6d0,(nil)): stub
fixme:advapi:ReportEventW  (0xcafe4242,0x0004,0x0000,0x400e111e,0x144128,0x0003,0x00000000,0x144140,(nil)):  stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
zachary@zachary-laptop:~$  fixme:clusapi:GetNodeClusterState ((null),0x33ebbc) stub!
fixme:advapi:DecryptFileA "c:\\6e89b6f843cc4619838b2d46034011\\"  00000000
fixme:advapi:RegisterTraceGuidsW (0x6cd15f38,  0x6cd20180, {e2821408-c59d-418f-ad3f-aa4e792aeb79}, 1, 0x33f898,  (null), (null), 0x6cd20188,)
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:wuapi:update_session_put_ClientApplicationID  0x1b0a08, L"Windows Internet Explorer 8 Setup Utility"
fixme:wuapi:automatic_updates_Pause  
fixme:wuapi:update_searcher_BeginSearch 
fixme:setupapi:pSetupGetGlobalFlags stub
fixme:wintrust:WinVerifyTrust  unimplemented for 4
err:wineboot:ProcessRunKeys Incorrect type of  value #0 (2)



I've done this twice and restarted twice and no IE8 listed under Wine in Applications tab. What am i doing wrong?

Any help is greatly appreciated!

---

### Post by cogadh on 2010-06-27
Despite what those instructions say, you really shouldn't even bother with trying to run IE8 in Wine, it doesn't actually work (yet):
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=16041](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16041)

---

