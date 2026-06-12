---
title: "cloning a server"
date: 2010-07-27
forum: Server Platforms
---

### Post by Tycho7286 on 2010-07-27
Hi, I need to clone a server across the network, can this be done using a live cd in the computer receiving the image, and xcopy? if so what are the commands, if not what are your recommendations.
Thanks for any info.
 - k

---

### Post by arrrghhh on 2010-07-27
> **Tycho7286 said:**
> Hi, I need to clone a server across the network, can this be done using a live cd in the computer receiving the image, and xcopy? if so what are the commands, if not what are your recommendations.
Thanks for any info.
 - k

Clone?  As in bit-for-bit copy?  I'd recommend Clonezilla if that's the case.

If you just need data 'cloned', then yes... but xcopy is a dos/win command friend.  You'd probably want to use something like rsync or just good ole cp.  May run into permissions issues using those tho, I'm not sure... dd may be a better bet.  If you don't need bit-for-bit copying, perhaps someone has a good method already.

---

### Post by linux18 on 2010-07-27
i think dd if=(your drive) | netcat *something*

someone else needs to fill in the blanks, but that is the general idea.

---

### Post by HermanAB on 2010-07-28
Here you go:
[http://www.aeronetworks.ca/netcat-howto.html](http://www.aeronetworks.ca/netcat-howto.html)

---

### Post by ahbart on 2010-07-28
[System rescue cd]("http://www.sysresccd.org/Main_Page") and use [fsarchiver]("http://www.fsarchiver.org/Main_Page")

---

### Post by speeves on 2010-07-28
The slow way:
[http://speeves.erikin.com/2007/01/using-tar-to-move-file-trees-across.html](http://speeves.erikin.com/2007/01/using-tar-to-move-file-trees-across.html)

The fast way:
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

