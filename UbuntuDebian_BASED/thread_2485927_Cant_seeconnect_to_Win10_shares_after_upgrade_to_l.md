---
title: "Cant see/connect to Win10 shares after upgrade to latest lxde from pcmanfm/nautilus"
date: 2023-04-14
forum: Ubuntu/Debian BASED
---

### Post by nicktf on 2023-04-14
Hi,

I'd welcome any words of wisdom on this one, I'm stuck! :(

I have checked/reinstalled samba, and thats all good, using the commandlin,  smbclient can see and connect to the Win10 shares. 

However, both (pcmanfm and nautilus) give various errors. Pcmanfm when clicked on  'network' shows my machine and 'windows networks', clicking on windows networks gives 'Failed to retrieve share list from server: No such file or directory'. Also (using wireshark) it does not even query the network!

Given that samba is working, what are the steps to discovering why pcmanfm is failing?

Many thanks
nick

---

### Post by ajgreeny on 2023-04-14
What OS are you actually using?

Saying simply "the latest lxde" is not helpful as that is a DE metapackage, not the actual operating system, and withoit knowing that we are simply guessing.

---

### Post by nicktf on 2023-04-15
[TABLE]
[TR]
[TD="class: field"]Kernel[/TD]
[TD="class: value"]Linux 5.4.0-146-generic (x86_64)[/TD]
[/TR]
 [TR]
[TD="class: field"]Version[/TD]
[TD="class: value"]#163-Ubuntu SMP Fri Mar 17 18:26:02 UTC 2023[/TD]
[/TR]
 [TR]
[TD="class: field"]C Library[/TD]
[TD="class: value"]GNU C Library / (Ubuntu GLIBC 2.31-0ubuntu9.9) 2.31[/TD]
[/TR]
 [TR]
[TD="class: field"]Distribution[/TD]
[TD="class: value"]Ubuntu 20.04.6 LTS[/TD]
[/TR]
[/TABLE]


Hope this helps!

---

### Post by ajgreeny on 2023-04-15
Thanks; that is a help but still doesn't tell us exactly what you installed or have done since.

Did you install Ubuntu 20.04 and then add the Lxde desktop to it or was this Lubuntu of an older version, eg, 18.04 which still used Lxde, or was it Lubuntu 20.04 which uses LXqt, and you added Lxde to that?

---

### Post by Morbius1 on 2023-04-15
> using the commandlin, smbclient can see and connect to the Win10 shares.
Yes, but with smbclient you must specify the host and the share.

You need to do the same thing with your file manager. Don't browse to the host then select the share. Explicitly ask for it.

So in Nautilus for example you would use something like this in the Location Bar ```
smb://win10host/share-name
``` 

win10host could be an ip address like 192.168.0.101 or the mDNS host name of the Win10 box ( the Win10 host name with a **[COLOR="#FF0000"].local[/COLOR]** attached at the end.
That will bypass the bug in gvfs common to anything that uses it on the backend.

---

### Post by nicktf on 2023-04-15
Sorry, I made a typo, its LXLE (Focal 64bit), which when loaded gives the system info in the last post!

---

### Post by ajgreeny on 2023-04-16
> **nicktf said:**
> Sorry, I made a typo, its LXLE (Focal 64bit), which when loaded gives the system info in the last post!

Ah!
That explains a lot but I still can't help as I do not know the distro **Lxle** at all.

---

