---
title: "Banshee 0.9.13"
date: 2005-12-02
forum: Requests
---

### Post by vassie on 2005-12-02
[LIST]
[*] Base framework for [Universal DAP support]("http://abock.org/2005/11/21/we-must-have-universal-dap-support/") (*[http://abock.org/2005/11/21/we-must-have-universal-dap-support/](http://abock.org/2005/11/21/we-must-have-universal-dap-support/)*). iPod code refactored to implement new DAP (Digital Audio Player) model *(see notes below)*
[*] ipod-sharp/libipoddevice is no longer a build requirement as DAP implementations are optional and loaded at runtime
[*] New unified HAL layer based on hal-sharp; new DAP layer and Audio CD layer now works off this HAL layer
[*] Multimedia Keys support
[*] Danish translation by Lasse Bang Mikkelsen
[*] Show file name and encoding (bitrate, sample rate, etc.) information in track properties dialog
[*] ID3 2.4 and WMA support
[*] Updated optimized tango bitmap iPod icons from Jakub Steiner [/LIST] 

[http://banshee-project.org/Releases/0.9.13]("http://banshee-project.org/Releases/0.9.13")

Thanks

Ben

---

### Post by sjoeboo on 2005-12-02
this isn't going to happen as far as i know untill mono etc gets backported, which is a big project, so it could be a while.

however, there are unoffical repo's if you wish to use them:

deb [http://packages.filefind.net/](http://packages.filefind.net/) ubuntu-breezy dotnet p2p

there are "backported" mono packages, and i think banshee and f-spot, but these repos are unsupported, although i have had no issues (other than beagle/tomboy conflivting with the newer mono versions)

---

### Post by Omer on 2005-12-02
I think it's better to wait for 0.10, which will be more stable.

---

### Post by sjoeboo on 2005-12-02
agreed, it sounds like there is alot of under the hood changes here. aaron even said in the release nots this is not for stable release channels to use.

that said i built it this morning before work adn all seems fine, except that ipod syncing has been disabled.

---

