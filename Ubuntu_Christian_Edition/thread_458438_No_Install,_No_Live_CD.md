---
title: "No Install, No Live CD"
date: 2007-05-29
forum: Ubuntu Christian Edition
---

### Post by rcdeacon on 2007-05-29
I already posted on this issue but I am still trying to resolve installing any flavor of Ubuntu 7.04. I am currently downloading Ubuntu CE 3.2. I was trying 3.1. I'm not sure if this will solve the problem or not but if not, is there any way I can use the Esword module on Mepis 6.5 which works great on my computer?

---

### Post by meng on 2007-05-29
Sounds to me as though your computer and the Ubuntu 7.04 kernel aren't playing nice together. I don't think CE 3.2 will solve your problem, since it is just a tweak of Ubuntu 7.04. But esword should run on Mepis OK.
sudo apt-get install esword
(I have no experience using esword, by the way. I know gnomesword used to have some problem when installed from repositories, although that was a long time ago.)

---

### Post by rcdeacon on 2007-05-29
I appreciate the reply, thanks. Will it matter that Mepis 6.5 is based on Dapper? And if not what repository can I find the esword module?

---

### Post by meng on 2007-05-29
MEPIS will be configured to use Dapper repositories. esword is in universe. I am guessing that universe will be enabled by default. If not, your sources.list is recommended to look like this:
[http://www.mepis.org/docs/en/index.php/Sources.list](http://www.mepis.org/docs/en/index.php/Sources.list)

---

### Post by mhancoc7 on 2007-05-29
esword is not in any repo. It is a windows program that I have built a .deb installer for. You can get the installer at [www.christianubuntu.com](www.christianubuntu.com). 

Jereme

---

### Post by rcdeacon on 2007-05-30
Jereme, thanks for the info but I did not see the deb installer on that link. I did see the link to the esword site and I actually run esword all the time but I do it with xp running on vmware server or on xp running native. Did I overlook something?

---

### Post by mhancoc7 on 2007-05-30
> **rcdeacon said:**
> Jereme, thanks for the info but I did not see the deb installer on that link. I did see the link to the esword site and I actually run esword all the time but I do it with xp running on vmware server or on xp running native. Did I overlook something?

Yeah, sorry I did not give you a more direct link. I was in a hurry. :)

Here is the direct link to the Popular Packages page on the Ubuntu CE project site.

[http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html)

Jereme

---

### Post by rcdeacon on 2007-05-30
Thanks Jereme. I will check later to see if it will work in Mepis. Hopefully one day REAL SOON I can install Ubuntu CE 7.04 on my Dell.

---

### Post by mhancoc7 on 2007-05-30
> **rcdeacon said:**
> Thanks Jereme. I will check later to see if it will work in Mepis. Hopefully one day REAL SOON I can install Ubuntu CE 7.04 on my Dell.

No problem. I recently had someone give me feedback on using it on Mepis. The .deb package installs fine and the eSword Installer runs fine until the very end. The menu icons do not get updated to point to the newly installed eSword and eSword Module Manager.

You can fix this by downloading two scripts located at [www.whatwouldjesusdownload.com/bin](www.whatwouldjesusdownload.com/bin). They may need to be set to execute. Then you can set up menu links to these scripts and you should be good to go.

Just let me know if you have any questions.

God Bless, Jereme

---

