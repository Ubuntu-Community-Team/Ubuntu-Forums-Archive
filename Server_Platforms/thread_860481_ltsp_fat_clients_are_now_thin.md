---
title: "ltsp fat clients are now thin"
date: 2008-07-15
forum: Server Platforms
---

### Post by sumpubu on 2008-07-15
I'm having some trouble with ltsp. I setup Ubuntu desktop and installed ltsp-server-standalone. I then used the workstation plugin found here [https://help.ubuntu.com/community/UbuntuLTSP/LTSPFatClients]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPFatClients")

That part worked fine. I was able to login on a client as the user that was created during the workstation install. I noticed that it was a little behind in updates. It was using Firefox 3 beta 5. I copied /etc/apt/sources.list to /opt/ltsp/i386/etc/apt/ and did apt-get update && apt-get upgrade. I followed that up with ltsp-update-image.

I can no longer log in as the remote user. I can log in on a client as the user on the server. I'm new to LTSP and Ubuntu (but not Linux). Could someone tell me where fat / thin would be set up?

---

### Post by -=Seeker=- on 2008-07-25
Once you update/upgrade your distro, it often upgrades the kernel. In which case you will need to run the ltsp-update-kernels command. This will update your pxelinux.0 image to match the kernel of your thin/fat client distro.

You may also need to re-run the ltsp-update-sshkeys command to update the ssh keys... But pob not needed.

I too am running a fat client environment... Awesome!!!

---

### Post by sumpubu on 2008-07-29
Thanks Seeker, that did it. I would have sworn I did that before. I guess not.

---

