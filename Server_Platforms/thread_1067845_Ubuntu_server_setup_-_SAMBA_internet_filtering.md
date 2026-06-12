---
title: "Ubuntu server setup - SAMBA internet filtering"
date: 2009-02-12
forum: Server Platforms
---

### Post by wstout on 2009-02-12
Ok, I have looked on the forums and have seen a lot of guides, and well haven't gotten a lot to work. This is probably due to my greeness on the server side of things. But, here's what I would like to do: I have Ubuntu server 8.04.2 LTS installed on an old Compaq Proliant 1600, I would like to have network shares that would be accessible on windows machines that do not require passwords to access. I would also like to have content filtering, so I think what I want is all of my internet traffic to go through the server and a filter then out on the network. I have a mix of Windows and Ubuntu machines on the network. Any ideas would be greatly appreciated. Thanks!

---

### Post by bigbearomaha on 2009-02-12
dansguardian is a well known filter that can be set up.

Big Bear

---

### Post by wstout on 2009-02-12
Thanks, Big Bear, my problem has been the set up with dansguardian. Not having any luck getting the internet to go through the server before it goes to the network.

---

### Post by bigbearomaha on 2009-02-12
the modem-bone connects to the filter/proxy-bone, the filter-bone connects to the router/firewall bone.

Big Bear

---

### Post by wstout on 2009-02-12
ha ha :)

---

### Post by HermanAB on 2009-02-12
Hmm, your problem is that Ubuntu Server isn't the easiest Linux around, it is sort of intermediate.  What you want to do is very complicated to set up manually with Ubuntu Server.  Go to the Samba web site and read the Official Howto, then go to the Squid-Cache web site and read their guides, finally go to the Dan's Guardian web site and read that. Setting it all up manually will take a few weeks.  Then consider that you can do it all using the wizards of Mandriva Linux or Suse Linux in an hour or so.

Cheers,

Herman

---

### Post by wstout on 2009-02-12
I'm not opposed to another distro on the server, only problem is the hardware i'm currently using is well... old as dirt. So don't know if using  a GUI is all that good of an option, or would I be working in a CLI version of those?

---

