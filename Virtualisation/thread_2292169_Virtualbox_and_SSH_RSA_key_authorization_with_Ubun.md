---
title: "Virtualbox and SSH /RSA key authorization with Ubuntu 14.04 LTS guests"
date: 2015-08-25
forum: Virtualisation
---

### Post by FlunkyMan on 2015-08-25
Hello all!

I'm very new here, and to Linux in general. I've gotten a long way by reading the various forums and other sites, but now I'm stuck.

I'm running an Ubuntu 14.04 LTS server as host using Virtualbox 5 that is running headless. I've created two Ubuntu 14.04 LTS guests (one original, one clone) that are also running headless. I set up my ethernet connection as bridged, and am able to SSH from my Win 8.1 laptop to host and both guests.  The host and the guests have full internet connectivity.  No problems there.

What I cannot do is get private key verification working in either of the guest installs. Private key verification works just fine on the host, but regardless of what I've tried, I cannot get it to work on either guest.

I'm at a loss now, wondering if I need to do some sort of magic in Virtualbox that allows the guests to verify.  I've tried all of the fixes that I can find on the internet, including those mentioned on these forums, with no luck.

I'm using PuTTY on my Win 8.1 machine to handle the SSH connections, with Puttygen creating the keys, and Pagent to manage the keys.

If anyone has any ideas, I'd be happy to hear them.  Thank you!

---

### Post by TheFu on 2015-08-26
Make all the systems be able to ping each other by name - both directions. That can be done by /etc/hosts or running DNS somewhere on the network.  I assume all three systems are on the same subnet - no NAT between them. The ssh keys contain the hostnames ... and the server wants to validate that the client name matches.

Does password authentication work? That is a critical detail I missed.

Were the public keys from the client machine pushed to the servers and placed into the ~/.ssh/authorized_keys files on each system?  For Unix to Unix, we use the ssh-copy-id tool for that. That tool handles keeping the file/directory permissions correct, which will stop ssh from working. 

There is NOTHING about virtualbox involved, unless you are using host-only or NAT network modes. In bridged mode, the network is just like any other network, so ssh works exactly the same.

---

### Post by Lars Noodén on 2015-08-26
> **FlunkyMan said:**
> I'm using PuTTY on my Win 8.1 machine to handle the SSH connections, with Puttygen creating the keys, and Pagent to manage the keys.

As far as I have read, PuTTYgen does not use the same key format as OpenSSH, so you'll have to convert the public keys before using them.  There is a way to do it manually and there are programs which do the conversion for you.

---

### Post by FlunkyMan on 2015-08-26
Mr. TheFu,

Thank you for your guidance. This problem is SOLVED.

To answer your questions before closing things out, I was not able to ping my machines by host name--only IP. I corrected this by making the proper entries in the /etc/hosts file as you specified.  Yes, all three machines were on the same subnet, and yes, password authentication was working properly as well.

Anyway, after making the changes to the HOSTS files, and checking the ping worked in both ways, I reloaded all of my public keys. Restarted SSH server, and logged back in with PuTTY.  And it worked!! (finally).  So, in my case it must have been important to have the HOSTS file properly updated.

Thank you for your help!

---

### Post by TheFu on 2015-08-26
Mr. TheFu was my father-  I'm just TheFu.

If this is solved, please use the "thread tools" and mark it as SOLVED to help others.

---

