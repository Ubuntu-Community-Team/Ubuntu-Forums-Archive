---
title: "Ltsp fat client cannot mount nfs during bootup"
date: 2008-11-20
forum: Server Platforms
---

### Post by jonatman on 2008-11-20
Hi all,
I'm trying to setup Ltsp under Ubuntu 8.10, I follow the instructions from the LTSPFatClients page and used the fat client plugin to setup the image, but whenever I logon the fat client machine, the message "Your home directory is listed as: '/home/user1' but it does not appear to exist...." any ideas?

Thanks in advance
Jonathan.

---

### Post by jonatman on 2008-11-20
I fixed it by adding the server ip address on the nfsmounts.sh
Jonathan

---

### Post by AlexanderDGreat on 2009-09-25
Hi jonatman, I have the same problem, can you pls. help me?

I can't login using my fatclient, it says, "Your home directory is listed as: '/home/user1' but it does not appear to exist...".

What did you do? I found this: [http://up-stream.co.uk/2009/05/installing-a-netbooted-fat-client-with-nubaes-scripts/](http://up-stream.co.uk/2009/05/installing-a-netbooted-fat-client-with-nubaes-scripts/)

Maybe it's what you're talking about.

Can you teach me step by step on how to do it? Plus, when I look at my /etc/nfsmounts.sh - it's empty, how do you put your server IP there? Forgive me for being a newbie.

Also, I already followed these:

sudo apt-get install portmap nfs-kernel-server nfs-common

echo "/home 192.168.2.10/24(rw,no_root_squash,async)" | sudo tee -a /etc/exports /dev/null

(192.168.2.10/24 - my LTSP server)

sudo exportfs -a

But still getting the error message.

Do you really need to tweak the script in nubae.com? Then afterwards, INSTALL sudo ltsp-build-client --chroot (name-of-chroot) --fatclient Ubuntu

just to PUT your SERVER IP address?

Thanks for your time. Hoping to hear from you soon.

---

### Post by AlexanderDGreat on 2009-10-03
Hi, is there anyone using LTSP?

Can anyone help me?

---

### Post by clarkville on 2009-10-04
I'm having the same problem.  The home directory doesn't exist.  Can anyone help with this?

Tim

---

### Post by AlexanderDGreat on 2009-10-05
Hi clarkville, you can press Alt+Ctrl+F1 to switch to terminal1, login and type, mount, as you WILL see, there aren't any "/home" mounts only /proc, /sys, etc...

So you can sudo mount -t nfs 192.168.2.10:/home /home

Where 192.168.2.10 is your server ip.

Then login w/ Alt+F7, then it finds the home directories.

My only question is, how can you do this automatically at boot up?

Is Nubae's script bad or what? I think it's unreliable.

Whachatink?

---

