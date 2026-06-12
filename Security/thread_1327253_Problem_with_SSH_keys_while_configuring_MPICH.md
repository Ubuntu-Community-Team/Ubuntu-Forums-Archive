---
title: "Problem with SSH keys while configuring MPICH"
date: 2009-11-15
forum: Security
---

### Post by theshibboleth on 2009-11-15
Hi, I'm trying to set up MPICH (a parallel computing platform) following the directions at [https://help.ubuntu.com/community/MpichCluster](https://help.ubuntu.com/community/MpichCluster). I'm stuck trying to get one of the computers in the cluster to allow the other computers to ssh onto it just with a public/private key rather than requiring a password.

I've checked /etc/ssh/sshd_config and RSAAuthentication and PubkeyAuthentication are both set to yes and the AuthorizedKeysFile is correct.

When I do ssh hostnameofstuckcomputer hostname, I get a prompt for a password whereas on the other computers I do not get this prompt. Any suggestions on how I can resolve this? I've already reinstalled once (because of an unrelated issue).

---

### Post by kevdog on 2009-11-15
I assume you set 

#PasswordAuthentication yes

to

PasswordAuthentication no


Is this what you want? (and then restarted the server)?

sudo service sshd restart

or 
sudo /etc/init.d/ssh restart

---

### Post by Lars Noodén on 2009-11-16
Look at host-based authentication for ssh.  That will allow the one machine to authenticate to the other.  So a user on the first is allowed in on the second simply by virtue of having logged in on the first.  Obviously there are some risks.  

These are a little old, but give the general idea.  

[http://www.snailbook.com/faq/trusted-host-howto.auto.html](http://www.snailbook.com/faq/trusted-host-howto.auto.html)
[http://cert.uni-stuttgart.de/doc/openssh/host-based.php](http://cert.uni-stuttgart.de/doc/openssh/host-based.php)

(Search engines aren't much use for finding anything other than noise these days.)

Otherwise, you might look at using a key agent.  Ubuntu, at least Kubuntu, loads an agent automatically on startup and it is then only a matter of adding a key to it to be able to use that key repeatedly.n

---

### Post by theshibboleth on 2009-11-16
Well I ended up having success after I decided I would not use the same folder on the same drive for the home folder of all the users and after also having changed /etc/hosts so that none of the hosts had more than one hostname. I'm not sure whether that would work with the single folder setup, but I decided that wasn't the best setup as my computers have different architectures.

---

