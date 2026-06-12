---
title: "JeOSVMBuilder and firstboot"
date: 2009-04-03
forum: Virtualisation
---

### Post by freeke on 2009-04-03
I'm trying to build a virtual image using the community docs @ [https://help.ubuntu.com/community/JeOSVMBuilder](https://help.ubuntu.com/community/JeOSVMBuilder) on Intrepid. Everything seems to work fine, and I can access the VM if I install openssh-server via an 'addpkg'.
However, when I try to use the firstboot option with the indicated script to make a more secure setup, I can't access the machine via ssh, so I assume it's not correctly installing the package at boot. 
Any useful tips or hints to get around this problem?

Thanks

freeke

---

### Post by freeke on 2009-04-08
Okay, so I figured trying to connect to the console might be a good idea, but this doesn't work either (using virsh, coonsole command) - the console just hangs, pressing keys (return, ...) doesn't seem to wake it up. When I shut down the VM, virsh simply returns to its prompt.

Is there a good HOWTO for setting up the console?

---

### Post by leechguy on 2009-06-16
Hopefully, you have been able to solve this issue by now. I ran into the same issue today, did some searching and came across your post. Unfortunately, there was no solution for your problem. Luckily, I was able to figure it out on my own.
 
I have an apt-proxy installed on the host and so when invoking vmbuilder I specified --mirror=127.0.0.1:9999 on the command line.
During installation this works fine, however, the 127.0.0.1 ip-address is also used in the sources.list of your newly created guest. Now when your guest boots for the first time and runs the script specified at the --firstboot parameter, it will try to retrieve the openssh-server from 127.0.0.1... this of course fails and no openssh server is installed.
 
In short, do not use --mirror=127.0.0.1:9999 but use --mirror=<ipaddress of host>:9999 instead.

---

### Post by freeke on 2009-06-16
Thanks, that does explain a thing or two!
I did manage to get around the problem by building an image with openssh-server built in, then recreating the keys after logging in. Ugly hack, but it works...
IMHO, it'd be worth while putting your proposal into the JEOSVMBuilder community docs.

---

### Post by borromeotlhs on 2012-05-08
You could also use the firstboot script to wait for the network to become available and then install openssh server that way.  Conversely, if you want ssh, using --ssh-key and specifying a key file will install openssh server for you.  That was back when it was called ubuntu-vm-builder though, so YMMV.

Regards!

---

### Post by geeksmith on 2012-09-12
removed by author

---

### Post by overdrank on 2012-09-12
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

