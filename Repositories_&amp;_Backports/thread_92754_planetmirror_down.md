---
title: "planetmirror down?"
date: 2005-11-20
forum: Repositories &amp; Backports
---

### Post by majkmil on 2005-11-20
I recently installed ubuntu on a G4 ibook ppc. It seems that th repositories are different. I am mising a file (libstdc++.so.5). When I use synaptic or apt I get all kinds of errors about planetmirror.

Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-powerpc_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package libstdc++.so.5

Are these mirrors down and can I edit my sources.list file to fix this? Thank You in advance

---

### Post by majkmil on 2005-11-20
I posted first is repositories but there is nobody viewing so I hope it isok to post here.
I recently installed ubuntu on a G4 ibook ppc. It seems that th repositories are different. I am mising a file (libstdc++.so.5). When I use synaptic or apt I get all kinds of errors about planetmirror.

Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_b reezy_free_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_b reezy_non-free_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_p lf_dists_breezy_free_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_p lf_dists_breezy_non-free_binary-powerpc_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package libstdc++.so.5

Are these mirrors down and can I edit my sources.list file to fix this? Thank You in advance

---

### Post by r4ik on 2005-11-20
This is a long shot but since i have got the same probs
like lots of 404 errors and sever acnova no reply my guess
is it might be the firewall in your router that is blocking traffic.
Perhaps connecting directly to the internet will do the trick.
I am gonna try the same thing lets see what it does.
I am not on a notebook so give me a moment.
Let you know asap.

---

### Post by majkmil on 2005-11-20
Thanks let me know. I wonder if there is a port we can open on the router.

---

### Post by aysiu on 2005-11-20
[QUOTE=majkmil]
Are these mirrors down and can I edit my sources.list file to fix this? Thank You in advance[/QUOTE] See my sig.

---

### Post by kingsidy on 2005-11-20
i think that what you can do download the package directly for the debian website. Check the attachment unzip and install it is the package libstdc++.

---

### Post by aysiu on 2005-11-20
[QUOTE=kingsidy]i think that what you can do download the package directly for the debian website. Check the attachment unzip and install it is the package libstdc++.[/QUOTE] Why go to a Debian site when you get the Ubuntu package?

---

### Post by majkmil on 2005-11-20
I tried synaptic but I get the errors there also. Do I install with the dpkg-i command?

---

### Post by majkmil on 2005-11-20
r4ik. did you have any luck bypassing the router. When I tried to install the deb package I got errors about  g++-3.3 . Any ideas

---

### Post by aysiu on 2005-11-20
[QUOTE=majkmil]I tried synaptic but I get the errors there also. Do I install with the dpkg-i command?[/QUOTE] You're getting errors because you probably have a bad sources.list. Follow the instructions in my sig. Then use Synaptic to install it.

---

### Post by majkmil on 2005-11-20
I got the file after installing  g++-3.3. But I still dont know about planetmirror. Anyone please

---

### Post by aysiu on 2005-11-20
I'm sorry. I still don't understand why you think you need planetmirror.
If you want extra repositories (universe and backports), **look at the first link in my sig**. This is the third time I've told you.

---

### Post by r4ik on 2005-11-20
[QUOTE=majkmil]r4ik. did you have any luck bypassing the router. When I tried to install the deb package I got errors about  g++-3.3 . Any ideas[/QUOTE]

No luck trying this gives same props.
Gonna try Aysiu's sig.
Good luck !

---

### Post by majkmil on 2005-11-20
Is this sources list ok for a PPC?

---

### Post by r4ik on 2005-11-20
[QUOTE=majkmil]Is this sources list ok for a PPC?[/QUOTE]

Little patience my friend read his sig.

---

### Post by aysiu on 2005-11-20
Yes, it's fine.

---

### Post by Manuka on 2005-11-20
Hi.

I followed every step given by aysiu, but I still have connection problems.
-in commander, i am told 'connection refused'
-in synaptic, I am told 'proxy authentication required'

my guess is that I have a problem to go through the firewall in my university network. But I don't have a chance to give my details (login/password) as I do for internet.
How can I bypass?

Thanks for helping!

Manu(ka)

---

### Post by aysiu on 2005-11-20
I don't know how to solve that, but these threads may help:
[http://www.ubuntuforums.org/showthread.php?p=220656#post220656](http://www.ubuntuforums.org/showthread.php?p=220656#post220656)
[http://ubuntuforums.org/showthread.php?t=14410](http://ubuntuforums.org/showthread.php?t=14410)

---

### Post by Manuka on 2005-11-20
oops I should have asked support from my IT first!

I have to enable internet using telnet and Ienabler software on my network.

Then it works with the command apt-get update, but still does not work using synaptic directly.

Thanks anyway. I think Ubuntu's great. I'm having so much fun!!!

---

