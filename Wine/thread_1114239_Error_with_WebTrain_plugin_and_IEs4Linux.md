---
title: "Error with WebTrain plugin and IEs4Linux"
date: 2009-04-02
forum: Wine
---

### Post by ReelExterminator on 2009-04-02
Hi, I am trying to get the webtrain plugin installed on my laptop. I would like to attend some web conferences that are run using this service without having to go to the library to find a Windows computer. The location of the plugin installation file is here: [http://www.webtrain.com/plugin/en/webtrain.exe](http://www.webtrain.com/plugin/en/webtrain.exe)

I installed IEs4Linux and IE runs and displays pages fine. When I tried to install the plugin directly from the website, from the IE 'download file' dialog box, the webtrain installation screen flashed on the screen and disappeared without installing anything. I downloaded the executable manually and tried installing it in wine without success:
```

xxx@xxx:~/.wine/drive_c$ wine ./webtrain.exe

```
gave me a usage error telling me to use a /i flag to install, so I tried
```

xxx@xxx:~/.wine/drive_c$ wine ./webtrain.exe /i
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:DownloadBSC_OnStopBinding No cache file
fixme:msi:MSI_OpenDatabaseW open failed r = 80030003 for L"AI_SETUPEXEPATH=C:\\webtrain.exe"
xxx@xxx:~/.wine/drive_c$ msiexec /i ./webtrain.exe
fixme:msi:MSI_OpenDatabaseW open failed r = 80030050 for L"C:\\windows\\temp\\msi143.tmp"
xxx@xxx:~/.wine/drive_c$

```

Could someone help me and suggest where to go from here?

---

