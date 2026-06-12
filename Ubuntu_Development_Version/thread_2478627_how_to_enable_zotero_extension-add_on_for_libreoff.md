---
title: "how to enable zotero extension-add on for libreoffice writer"
date: 2022-08-31
forum: Ubuntu Development Version
---

### Post by Claus7 on 2022-08-31
Hello,

I wanted to enable the zotero extention with libreoffice writer using ubuntu 22.10. Initially I tried to install it by downloading the compressed file, yet then I installed it following these instructions:
```
wget -qO- https://raw.githubusercontent.com/retorquere/zotero-deb/master/install.sh | sudo bash
sudo apt update
sudo apt install zotero
```

from here:
[https://github.com/retorquere/zotero-deb](https://github.com/retorquere/zotero-deb)

the thing is that I couldn't make available the zotero toolbar to libreoffice writer. Disabling and enabling the extension from zotero->tools-Add-ons didn't make any difference. So I opened writer and from Tools->Extension manager-> I navigated to /usr/lib/zotero/extensions/zoteroOpenOfficeIntegration@zotero.org/install/Zotero_OpenOffice_Integration.oxt in order to enable it.

Regards!

---

