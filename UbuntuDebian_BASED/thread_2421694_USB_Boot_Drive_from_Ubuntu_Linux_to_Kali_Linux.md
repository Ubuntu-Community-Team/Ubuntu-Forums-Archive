---
title: "USB Boot Drive from Ubuntu Linux to Kali Linux"
date: 2019-06-25
forum: Ubuntu/Debian BASED
---

### Post by redus on 2019-06-25
Hi all, so I'm trying to single boot Kali Linux. I currently have Ubuntu Linux and plan on getting rid of that, along with the default Windows 10. I need software to put Kali Linux on my USB. I've tried a bunch of different things already, most just download this .exe file, open it, select Kali, and go. But I don't know how to open those .exe files, or at least do anything useful with them since it's usually just a bunch of documents, folders, and others .exe files. Another thing I tried was some "sudo apt-get install unetbootin" then "sudo dd if=kali-linux-2019.2-amd64.iso of=/dev/sda bs=512k" which seemed to work, but when I start, I have to get into the startup settings and choose the USB. Once I do that it says it isn't "Authentic". So any way you know to fix one of these issues or another way to get Kali Linux would be of huge help!! Thank you very much!

---

### Post by wildmanne39 on 2019-06-25
*Thread moved to **Ubuntu/Debian BASED a more appropriate sub-forum**.*

---

### Post by oldfred on 2019-06-25
Are you sure the issue is not UEFI Secure Boot?
Not sure if Kali supports that.

It was my understanding that Kali was intended to be only on flash drives, even though it can be installed.

---

### Post by lazarocarroll on 2019-06-25
> **oldfred said:**
> Are you sure the issue is not UEFI Secure Boot?


I can't begin to tell you how many times UEFI and Secure Boot has messed me up...

---

### Post by redus on 2019-06-26
What is UEFI?

---

### Post by Rubi1200 on 2019-06-26
Hopefully this will answer most of your questions:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Instructions to install Kali to HD:
[https://docs.kali.org/installation/kali-linux-hard-disk-install](https://docs.kali.org/installation/kali-linux-hard-disk-install)

---

### Post by oldos2er on 2019-06-26
It needs to be said:

"
[h=2]Is Kali Linux Right For You?[/h] As the distribution&#8217;s developers, you  might expect us to recommend that everyone should be using Kali Linux.  The fact of the matter is, however, that Kali is a Linux distribution  specifically geared towards professional penetration testers and  security specialists, and given its unique nature, it is **NOT**  a recommended distribution if you&#8217;re unfamiliar with Linux or are  looking for a general-purpose Linux desktop distribution for  development, web design, gaming, etc."

from [https://docs.kali.org/introduction/should-i-use-kali-linux](https://docs.kali.org/introduction/should-i-use-kali-linux)

Let's just say the idea of running *.exe files on Kali is not a good one.

---

### Post by redus on 2019-06-26
No, none of the links provided have fixed it. From Windows/Ubuntu dual boot I select System setup >> Boot Device options >> select my USB >> then this message comes up "Selected boot image did not Authenticate. Press <Enter> to Continue." and below that is my only option, [Continue]

---

### Post by redus on 2019-06-26
OK I got it! oldfred basically got it right. So I just needed to get into my BIOS >> Startup Information (might not be the right menu name) >> change Secure Boot to Disabled

---

