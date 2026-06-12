---
title: "Bug in nautilus???? Nemo VS Nautilus - 20.04 vs 18.04"
date: 2020-03-16
forum: Ubuntu Development Version
---

### Post by miguelpires on 2020-03-16
Hi,
I've a problem when accessing files in a samba shared in 20.04:

Via nautilus: smb://ip/name of the folder/test.doc

1. It says that don't exist an application to open the document, and i've to chose Writ3er to open the doc.

2. If I tray to save a file from thunderbird in that shared folder thunderbird crashs 

Via Nemo smb://ip/name of the folder/test.doc

1. Writter opens the document without any problem
2. Can't test via Thunderbird

In 18.04 no problem in any situation. So anyone can point me out how can I debug this?

Regards
Miguel

---

### Post by gchenguelly on 2020-03-18
I have the same issue since upgrade yesterday
I can see the share on the network, but when I try to connect, I get following message
NT_STATUS_CONNECTION_DISCONNECTED
I can connect with Lubuntu 19.10 without issues and I can still connect to a Nas4free share without issues
Wondering what to check?

---

