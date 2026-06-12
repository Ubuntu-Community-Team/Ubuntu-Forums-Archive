---
title: "Nextcloud remote access via wireguard"
date: 2023-04-22
forum: Server Platforms
---

### Post by aljames2 on 2023-04-22
I have read through this extensive and excellent thread on the various methods of setting up NC:
[https://ubuntuforums.org/showthread.php?t=2484642&highlight=Nextcloud](https://ubuntuforums.org/showthread.php?t=2484642&highlight=Nextcloud)

In deciding that I prefer using a VPN for remote access to a non-internet facing instance of NC, I do have a few network questions.  I could place the Wireguard server on the LAN along with the NC VM, or I do have a separate physical network (nic) available where I could put both there.  Might the separate network be better, and then I could use a LAN device to push data to seed the NC server?  I suppose this additional network method would require a new virtual environment, which may be a downside supplying additional hardware, but doable if the pros make it worthwhile.

Lastly, does NC require a certificate if not internet facing?  I know without a cert, the browser will complain of an untrusted connection, and perhaps this nuisance is enough of a reason to do the LetsEncrypt setup?

---

### Post by ian-weisser on 2023-04-23
> **aljames2 said:**
> Lastly, does NC require a certificate if not internet facing?  I know without a cert, the browser will complain of an untrusted connection, and perhaps this nuisance is enough of a reason to do the LetsEncrypt setup?

Seems like you have answered your own question there:

NextCloud does not require a certificate, and does not care if you have a certificate or not.

Your users' browser is the application that (sensibly) cares about a certificate.

---

### Post by aljames2 on 2023-04-23
Great thanks for confirming this part.  Most tutorials I have seen include getting a certificate, which makes sense if it&#8217;s on the internet. Just wasn&#8217;t sure if it was a prerequisite for it to work over time.

---

