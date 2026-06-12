---
title: "DHCP/DNS configuration for Orchestra provisioning server"
date: 2012-01-04
forum: Server Platforms
---

### Post by dehuszar on 2012-01-04
I've tried following a [variety]("https://help.ubuntu.com/community/Orchestra/Installation") of the [tutorials]("http://voices.canonical.com/shang.wu/2011/08/31/oneiric-ubuntu-orchestra-server-provision-server-setup/") for [setting up Orchestra]("http://cloud.ubuntu.com/2011/10/getting-started-with-ubuntu-orchestra-servers-in-concert/")/Juju, and they all pass on letting the Orchestra provisioning server handle DHCP/DNS.  None offer an explanation as to why, but they all suggest that if you want to use Juju (which is one of the reasons I started this experiment) you should use let Orchestra handle these functions.  

I've tried letting Orchestra handle DHCP/DNS, but they don't appear to work and I am unable to get DHCP to issue addresses if I tell Orchestra to handle it, nor are my local domains resolving. I've scoured the web, but I can't find any docs or tutorials for doing this, only package information about the provisioning server.

Anyone have experience or insight here?

Thanks in advance.

---

### Post by mward29 on 2012-01-21
I'm looking for an answer to this same question.

---

### Post by claytronic on 2012-03-17
Did you two ever get any answers to your questions? Let me know if I can help.

---

