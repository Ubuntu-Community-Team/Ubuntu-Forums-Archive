---
title: "Ubuntu + Multi User Terminal Server"
date: 2010-01-02
forum: Server Platforms
---

### Post by Jasonx86 on 2010-01-02
Morning all,

Does anyone know of any packages that'll turn Ubuntu Karmic into a multi-user terminal server environment?

I'm trying to get 10 or more thin clients with nothing more than tsclient installed to connect to a Ubuntu server that allows multiple GUI connections. So far I've tried using xvnc which is excellent but only allows one user to login at a time.

Thanks in advance.

---

### Post by Cheesemill on 2010-01-02
As far as I know there is no way of setting up an RDP server on Ubuntu.

You may want to look into setting up a Ubuntu LTSP server if your clients have network boot capability.
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

### Post by Jasonx86 on 2010-01-02
> **Cheesemill said:**
> As far as I know there is no way of setting up an RDP server on Ubuntu.

You may want to look into setting up a Ubuntu LTSP server if your clients have network boot capability.
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

Thanks but clients will not have network boot capability as they are notebooks and will connect via wifi. 

There must be a way...

I found NoMachine's NX software which allows a Ubuntu RDP server. Trouble is the software isn't yet supported on Ubuntu Karmic.

Does anybody have experience installing NX server ([http://www.nomachine.com/news-read.php?idnews=284](http://www.nomachine.com/news-read.php?idnews=284)) on Ubuntu Karmic?

---

### Post by wirefly on 2010-01-02
> **Jasonx86 said:**
> Thanks but clients will not have network boot capability as they are notebooks and will connect via wifi. 

I have a couple of old laptops here that don't have netboot function. I've setup a LTSP installation and replaced the hard drive with a compact flash card and a little converter cradle, boot from that and get connected to the terminal server and you have a thin client with no noise from a spinning hard drive.

---

### Post by HermanAB on 2010-01-03
If you want it to be simple and secure, just use SSH with X forwarding enabled.  It is multi-user and secure.  VNC and NX are insecure and don't work any better than SSH.

---

### Post by Jasonx86 on 2010-01-04
Thanks for both of your suggestions.

In in the end I setup an NX server and attached NX Clients. It turns out NX does offer security in the form of encrypted sessions ([http://michigantelephone.wordpress.com/2007/10/15/how-to-install-nx-server-and-client-under-ubuntukubuntu-linux](http://michigantelephone.wordpress.com/2007/10/15/how-to-install-nx-server-and-client-under-ubuntukubuntu-linux)/)

Thanks again

---

