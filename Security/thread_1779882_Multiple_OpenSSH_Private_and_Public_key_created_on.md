---
title: "Multiple OpenSSH Private and Public key created on same Ubuntu 10.10 Box"
date: 2011-06-11
forum: Security
---

### Post by myandylai on 2011-06-11
I am having some issue with OpenSSH on Ubuntu Box. It's kind of funny actually. I have 3 VPS all running Ubuntu 10.04. I generate 3 difference set of public and private key at my home Ubuntu 10.10 PC and send to all those VPS separately.

VPS1     publickey1 (privatekey1 to access)
VPS2     publickey2 (privatekey2 to access)
VPS3     publickey3 (privatekey3 to access)

I create sshkey set using "ssh-keygen -t rsa". Then I use "ssh-id-copy@vps_ip" to send the publickey file to VPS. Then I rename both id_rsa and id_rsa.pub to id_rsa_vps1 and id_rsa_vps1.pub before start create the second set of key for another VPS.

Then I found that,
publickey1 can be access by privatekey1 only (the 1st set of key generated)
publickey2 can be access by privatekey1 and privatekey2 (the 2nd set of key generated)
publickey3 can be access by privatekey1, privatekey2 and privatekey3 (last set of key generated)

Is this a bug or it's been configure this way so that all publickey generated later can be access by all privatekey file generated earlier?

---

