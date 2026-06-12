---
title: "Passwordless SSH issue."
date: 2008-05-16
forum: Security
---

### Post by fieldyweb on 2008-05-16
I'm trying to setup a passwordles SSH system, which has Ubuntu workstations, bringing files, on each boot, from a central Ubuntu server, this process has to be with no user input, and occur before GDM Starts up.

I have figured out how to setup the passwordles ssh i think, by following these instructions:

> ssh-keygen -t rsa 2048
 
[this will create a ~/.ssh/id_rsa and ~/.ssh/id_rsa.pub for the private and public keys, respectively ]
 
now copy the ~/.ssh/id_rsa.pub to the remoate system where you want passwordless login
 
scp ~/.ssh/id_rsa.pub root@192.168.0.247:/tm

Now on the remote machine

mkdir ~/.ssh
chmod 700 ~/.ssh
cp /tmp/id_rsa.pub ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
now on the host machine try to login iin , it shold log you in woith outh a password
You can append as many public keys  usig the >> sign 

the problem i am having however is the ssh fingerprint

If i follow the instructions above, the **scp ~/.ssh/id_rsa.pub root@192.168.0.247:/tm** command asks me to verify the fingerprint, and passwordless ssh authentication will work. 

the Ubuntu Workstations however, are being prebuilt however, and have the 

> mkdir ~/.ssh
chmod 700 ~/.ssh
cp /tmp/id_rsa.pub ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys

Done as part of the build, which doesn't actually incorperate the server they will eventually SSH to.

Whats happening, is the Pc's will boot, and get to the point they are trying to SSH into the server, and stop until i enter in Y to verify the finger print. At chich point they will then carry on copying the files down.

this happens on first boot every time, and is a bit of a pain, as we will have to roll out these workstations to many remote sites.

My question is, how, where, what do i do to have the fingerprint of the remote SSH server already on the workstations, so it doesn't need verifying on the first workstation boot?

what file, needs to go where, with what permissions, for all to be happy, and the SSH occur unnoticed at boot time.

It should be said, this will all be happening on a secure internal network, with no outside internet access, this is a fully private network.

---

### Post by Dr Small on 2008-05-16
The fingerprint should be automatically be added to .ssh/known_hosts

---

### Post by kevdog on 2008-05-17
You can bypass this fingerprint verification if you want -- its part of a security measure -- but you can turn it off.

If you copy the the ssh_config (the system wide default option file for every client) to the user's .ssh directory (~/.ssh), you can customize this file on a per user basis. (Or you can simply edit the /etc/ssh_config file itself if you want it applicable to every user).  Anyway edit the file and change this line:

#   StrictHostKeyChecking ask

to

StrictHostKeyChecking no

---

### Post by fieldyweb on 2008-05-17
KevDog, i'll give that a go when i get back to the office. It sounds like it could work.

---

### Post by Oldsoldier2003 on 2008-05-17
> **fieldyweb said:**
> KevDog, i'll give that a go when i get back to the office. It sounds like it could work.

why not just copy the server fingerprint into each workstations known_hosts? that would solve the strict checking issue

---

### Post by Meson on 2008-05-17
Hey fieldyweb, have you tried tweaking the StrictHostKeyChecking option in /etc/ssh/ssh_config

Check it out in 'man ssh_config'

---

### Post by cdtech on 2008-05-17
Just a question, why are you using an encryption algorithm such as RSA and not the DSA for signatures? I just want to know what the benifits are.

---

### Post by Meson on 2008-05-18
> **cdtech said:**
> Just a question, why are you using an encryption algorithm such as RSA and not the DSA for signatures? I just want to know what the benifits are.

I think speed is in the favor of RSA.

---

### Post by kevdog on 2008-05-18
Not aware dsa was necessarily slower than rsa?  Is this in fact the case?

---

### Post by cdtech on 2008-05-18
I believe that RSA is an encryption algorithm, whereas DSA is for signatures only and is not an encryption algorithm. Correct me if I'm wrong. I'm still learning about encryption myself. :)

---

### Post by Meson on 2008-05-18
> **kevdog said:**
> Not aware dsa was necessarily slower than rsa?  Is this in fact the case?

From my personal experience yes.  Also if you read through this thread and some of the references: [http://www.linuxforums.org/forum/linux-security/48093-openssh-user-host-authentication-rsa-versus-dsa-provides-stronger-security.html](http://www.linuxforums.org/forum/linux-security/48093-openssh-user-host-authentication-rsa-versus-dsa-provides-stronger-security.html)
not only does the consensus seem to be in favor of RSA for speed, but for security as well.  People are weary of the DSA implementation and the required key strength.

Keep in mind if you're using ssh-keygen to use -t RSA and not -t RSA1 unless you absolutely need the SSH v1 protocol.

---

### Post by kevdog on 2008-05-18
Still not following since that page you linked too was very weak evidence -- if any evidence at all.

Ok -- key generation process -- rsa might be faster, however who cares?? This is a one time process.

dsa/rsa keys are only involved in the authentication process.  I haven't timed the authentication process so I have no idea which process would be "faster".

The actual encrypted communication uses a symmetric cipher such as AES, 3DES, etc.  So the rsa/dsa keys are not even involved in this scenaio, and this is where speed would be the most noticeable and most important.  Asymmetric methods are far too slow for this process.

RSA I believe is still closed source (not that this is bad).

No one should use ssh protocol 1 IMO.

So where is your hangup on using DSA keys?? I just don't understand, or maybe my understanding of how OpenSSH works is flawed.

---

### Post by angelmartinezn on 2008-05-19
and what about using NFS?

---

### Post by jdong on 2008-05-19
> **kevdog said:**
> 
RSA I believe is still closed source (not that this is bad).


No, it WAS patent-encumbered for some time which motivated DSA but I don't believe that's the case in any jurisdiction any longer.

---

### Post by fieldyweb on 2008-05-20
Editing the /etc/ssh/ssh_config file and making the previous changes did solve the fingerprint issue, thanks there.

As to RSA/DSA, personal preference, use RSA on everything else. and it works correctly.

---

