---
title: "ltsp and printers"
date: 2010-07-27
forum: Server Platforms
---

### Post by infringer on 2010-07-27
Hi,

I'm trying to set up something similar to a kiosk, but the users can log in and out.  But what I need to do is lock the users to one printer.  So that is the only printer that they can print to?

Any suggestions on how to do this?

Here is my lts.conf file, you can see where I've tried to set the DEFAULT_PRINTER but they still change the printer:

[Default]
LOCAL_APPS=True
LOCAL_APPS_MENU=True
LOCAL_APPS_MENU_ITEMS = firefox, thunderbird
DNS_SERVER = 24.28.227.64, 24.28.227.65, 137.118.1.33, 216.237.192.2
TIMESERVER = 192.168.10.254
CUPS_SERVER = 192.168.11.12
DEFAULT_PRINTER = shop

Any help is greatly appreciated!
-David

---

