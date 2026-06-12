---
title: "Passwordless SSH"
date: 2006-07-18
forum: Server Platforms
---

### Post by KittyChunk on 2006-07-18
Hi all. 

I'm busy setting up a scientific compute cluster using Ubuntu Server 6.06 on the nodes. One of the message passing interfaces we are using requires passwordless ssh (rsh, actually, but if ssh pretends to be rsh and doesn't need passwords that's good enough) access between each machine in the cluster.

I've got an interesting glitch. I have two machines, both running sshd and both happily able to connect to each other in the normal way using rlogin and providing a password. Following the advice by i-tech in [this thread]("http://ubuntuforums.org/showthread.php?t=28213"), I generated a DSA key on machine 1 and copied it to authorized_keys on machine 2, and vice versa. Having done that, I am now able to rlogin to machine 2 from machine 1 passwordlessly, but *not* the other way around - rlogin to machine 1 from machine 2 still needs a password! Very strange ;)

Any thoughts?

---

### Post by citylife on 2006-07-18
i dont an idea

---

### Post by superm1 on 2006-07-18
Check permissions on the .ssh folder and authorized_keys file.  I don't know offhand what they are supposed to be, but I've had similar things bite me.

---

### Post by nagilum on 2006-07-18
That's no error. Putting the public key of your keypair on machine 1 into the authorized_keys on machine 2 will of course only allow passwordless connections in this very direction. If you want to have it "bi-directional" create another keypair on machine 2 and put that into the authorized_keys on machine 1. Why should the ssh-server on machine 1 know anything about the authorized keys on another machine?

---

### Post by superm1 on 2006-07-18
My understanding was that he did this vice-versa as in generated on each machine and copied to authorized_keys on the other.

---

### Post by mazirian on 2006-07-18
What shows up in the logs of the remote box.  What error message do you get attempting to make the connection into the box that refusing you?  Are the sshd_config files identical on the two boxes.  Do you have access to port 22 on the box denying access?

---

### Post by harisund on 2006-07-18
Did you try what nagilum suggested? I am pretty sure that is what is lacking, atleast from what you have written

---

### Post by Soleil-Raid on 2006-07-18
Verbose output on SSH is pretty handy for diagnosing these problems.
ssh -v host

Adding successive v's will add more output, such as;
ssh -vv host
ssh -vvv host
Although you will probably find that -v is enough.

---

### Post by KittyChunk on 2006-07-19
Thanks for the suggestions everyone. 

I did in fact do bidirectional key pairing, one of course has to do this on cluster farms where each machine must know about (and thus have keys for) all the others. The problem turned out to be non-identical sshd_config files, as mazirian pointed out. One of the boxes had AuthorizedKeysFile specified as "authorized_keys2" instead of "authorized_keys" - changing this fixed the problem.

---

