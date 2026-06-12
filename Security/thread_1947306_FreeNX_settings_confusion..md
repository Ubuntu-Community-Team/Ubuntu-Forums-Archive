---
title: "FreeNX settings confusion."
date: 2012-03-26
forum: Security
---

### Post by NertSkull on 2012-03-26
So I'm really hoping someone can guide me to an understanding here.  I'm new to the freenx stuff, and don't fully understand it.  Basically my question is, I have a key in .ssh/authorized_keys2 that I can't delete without losing functionality, and I don't understand why that is the case.

This is what I've done.  

I installed freenx using the nxsetup --install script.

I changed port numbers in sshd_config and node.conf (I run my SSH server on a separate port than 22)

I enabled the passdb (ENABLE_PASSDB_AUTHENTICATION=1)

I added my username to the database (nxserver --adduser)

And changed the password (nxserver --passwd)

I added AllowUsers nx above the AllowPAM Yes line in sshd_config

I deleted the default keys in /var/lib/nxserver/home/.ssh/authorized_keys and in the /var/lib/nxserver/home/.ssh/authorized_keys2 files

Then I added my own SSH keys into both of those files (with the same options in the file already there).  I just replaced the keys.

So, everything works and I can login right now.

But I've discovered the install script adds a authorized_keys2 file to me /home/username/.ssh folder.  So I already have my SSH key in the authorized_keys file.

The authorized_keys2 file appears to have a default key in it.  If I delete the authorized_keys2 file (with the default key) I can NOT log in anymore.

But, if I leave it there.  I can log in.  But I can NOT login from the client using the default NoMachine key.  So I must use my SSH key on the client.  But I have to leave the NoMachine key present on the server.

Can someone explain that to me?

I don't know exactly how this all works.  But when I delete the file and login, the log shows user "nx" failing to login, even though the usernam I'm using to login with is "nertskull".

So, it kind of feels as though you login to the server using the "nx" user, and then it logs into your main user (nertskull) using different keys.

Anyway, I'm sure its very apparent to others I'm quite confused how this all works.  So I would love to have someone clarify what's going on here.

In the end, what I really want is to login to my home computer (server) from work(client) using SSH key authentication over SSH.

I already have SSH working perfectly and I use it all the time.  So its just getting it to work with freenx.

Can someone explain.  Thanks!

---

### Post by CharlesA on 2012-03-26
The key in authorized_keys2 is set up to allow you to connect to the FreeNX service via ssh. It uses a forced command to launch the server if I recall correctly.

Basically, the login you use is to connect to SSH, and after you are connected FreeNX launched because of the entry in authorized_keys2, so don't delete it.

---

### Post by NertSkull on 2012-03-27
So, if I don't delete that file, is there any option for lack of security? 

It kind of feels to me that leaving a default setting is not ideal.  But at the same time it appears (if I'm understanding right) that the keys in authorized_keys2 are never visible to the outside world.  But instead are just to connect to the freenx server locally (after using the other nx keys to connect externally).

Is that about right?

---

### Post by CharlesA on 2012-03-27
See [here]("http://en.wikipedia.org/wiki/NX_technology#Use_of_SSH_protocol_and_how_SSH_tunneling_works_in_NX") for how NoMachine and FreeNX works with SSH.

I have only tried using NX with password authentication on SSH. Using keys shouldn't be much different but I haven't tried it.

See here too: [http://serverfault.com/questions/64189/how-bad-is-it-to-use-the-nx-server-default-ssh-key](http://serverfault.com/questions/64189/how-bad-is-it-to-use-the-nx-server-default-ssh-key)

---

### Post by NertSkull on 2012-03-27
Thanks, that helps.  I see now there appears to be two separate things happening here.

---

