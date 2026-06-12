---
title: "Local Mirror"
date: 2009-05-08
forum: Server Platforms
---

### Post by pajoohesh on 2009-05-08
[COLOR="Blue"]Dear All,

I want to have a local mirror. I found that apt-mirror and aptoncd do some jobs. the problem with the first one is that I do not know how to customize it to download just required softwares and their dependencies not downloading all the respiratory. 

and the problem with the second one is that not only you should have the program available in your cache but also you can not have multiple architectures.

I wonder if any body can help me with this. I just want to have a multi architechture local mirror but with specific softwares not everything.[/COLOR]

---

### Post by deej1976 on 2009-05-08
Hi,

Have you come apt-proxy? I'm using it in a very mixed environment 

e.g. x86_64, x86, sparc, with combinations of 7.10, 8.04, 8.10 and 9.04.

Just did a complete upgrade from 7.10 to 8.04 without any problems using the apt-proxy server.

Think this is the link I used to set it up.

[https://help.ubuntu.com/community/AptProxy?action=show&redirect=AptProxyHowTo](https://help.ubuntu.com/community/AptProxy?action=show&redirect=AptProxyHowTo)

Deej

---

### Post by cariboo on 2009-05-09
Maybe apt-cacher is more what you are looking for, it is in the repositories.

---

### Post by pajoohesh on 2009-05-09
[COLOR="Blue"]Yeah, the problem is that I do not know how to set the configuration file to just download a few software packages not all the packages. 

I think the apt-cacher is a better choice, as I have understood that it does not download all the respiratory just those that have been requested(if I am right). but the computer that I want to apply this respiratory is completely offline. can I just transfer the cache with an external hard drive to it and install the packages I want?

Second if I install it now will it cache every programs on my computer because there is nothing available now in my apt/cache/ now. and is it also capable of downloading multiple architectures.

[/COLOR]

---

### Post by mac9416 on 2009-05-09
Hi pajoohesh

If you want an easy way to get software with dependencies, try [Keryx]("http://keryxproject.org"). It won't make the repository (though the next release should), but it can get the software for you. I created a Python script that will turn a Keryx project into a repository, though, so if you want I can post it here. I use it every few days, because whenever I get software with Keryx I make a local repo with it to install with APT for convenience.

Hope that helps. If you have any questions, please don't hesitate to ask!
-mac

---

### Post by pajoohesh on 2009-05-11
> **mac9416 said:**
> Hi pajoohesh

If you want an easy way to get software with dependencies, try [Keryx]("http://keryxproject.org"). It won't make the repository (though the next release should), but it can get the software for you. I created a Python script that will turn a Keryx project into a repository, though, so if you want I can post it here. I use it every few days, because whenever I get software with Keryx I make a local repo with it to install with APT for convenience.

Hope that helps. If you have any questions, please don't hesitate to ask!
-mac

[COLOR="Blue"]Hi mac,

Thank you for your answer. yes i think this is what i was looking for. but the question is that is this capable of downloading a software for multiple architectures or I should have different keryx projects downloading softwares in different architectures separately?

I want to download the same software for multiple architectures actually.[/COLOR]

---

### Post by pajoohesh on 2009-05-11
[COLOR="Blue"]Hello,

I have got completely how it works. it is just perfect in my opinion.

The only problem is that it was much better if I could start from the computer which is connected to internet, and then transfer the files to any computer that I intend. I think it can be done by the programmer in the same way as the default jaunty i386 project that comes with the software itself.

any way, thanks for the great help and recommendation.[/COLOR]

---

### Post by starfry on 2009-05-11
Hi, like pajoohesh says, you want Apt-Cacher.

I use this and it works great. There's a one line config file to stick on each machine you wish to use the cache. If the cache then has the require package it does not download from internet otherwise it does so and caches it for future uses. Works very will, imho :)

---

### Post by mac9416 on 2009-05-11
> **pajoohesh said:**
> [COLOR="Blue"]Hello,

I have got completely how it works. it is just perfect in my opinion.

The only problem is that it was much better if I could start from the computer which is connected to internet, and then transfer the files to any computer that I intend. I think it can be done by the programmer in the same way as the default jaunty i386 project that comes with the software itself.

any way, thanks for the great help and recommendation.[/COLOR]

No problem, pajoohesh. So Keryx will work for you? I'm not sure I understand, but if you need any extra feature, please meet us over at the keryxproject.org forums or the #keryx IRC room and let us know. We always need an idea for new functionality. :-D

---

### Post by pajoohesh on 2009-05-11
[COLOR="Blue"]mac, 

The questions are: 

1- Should I make a separate project for each offline computer or no?

2- Can I create projects on the Internet connected computer not on the off line ones by just supplying some information such as jaunty-i386?

Regards, [/COLOR]

---

### Post by EXCiD3 on 2009-05-11
1) If the computers are both say, fresh installs, or you have installed the exact same packages on them, then you only really need to create one project.

2) Keryx currently comes with a Jaunty-i386 project (it is actually missing the status file at the moment, i need to fix that and reupload it). This would let you download packages for an i386 install that has not had any extra packages installed. The default package will suffice for most users and in the worst case scenario it will just download a few extra packages for people if you have already installed some. I just need to fix that missing status file and you will be able to use that project without going to the offline computer yet.

---

### Post by pajoohesh on 2009-05-11
[COLOR="Blue"]Yeah,

I somehow ignored that by just creating an empty status file but the problem is that it does not recognize which packages are installed and which are not in the alternative runs of the program. 

the other concern about this problem is that one should mark and download programs one by one and there is no possibility, as far as I know without hacking some python code, to download some programs, altogether.

I am definitely waiting for the upload of the program with different projects in different architectures.:)

anyway, thanks for your help. Keryx is great overall.[/COLOR]

---

### Post by EXCiD3 on 2009-05-11
> **pajoohesh said:**
> [COLOR=Blue]Yeah,

I somehow ignored that by just creating an empty status file but the problem is that it does not recognize which packages are installed and which are not in the alternative runs of the program. 

yes without the actual information in the file you won't have a list of currently installed packages which might cause some problems when downloading packages.

> the other concern about this problem is that one should mark and download programs one by one and there is no possibility, as far as I know without hacking some python code, to download some programs, altogether.

Unfortunately for now, you must download each program by itself. At least Keryx is at the point where it can download all of the dependencies for you. It works best if you create your own project for now.

> I am definitely waiting for the upload of the program with different projects in different architectures.:)

anyway, thanks for your help. Keryx is great overall.[/COLOR]
Thanks! I need to do this with Jaunty i386 (with status file), x64, Jaunty Server 32 and 64 bit as well as all the versions of Hardy. I will hopefully be able to get those up sometime this week.

The next version of Keryx is going to have a lot of changes and a bunch of improvements. I hope to have the next version finished before the summer is over. :D

---

