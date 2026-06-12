---
title: "[SOLVED] 18.04 - Apt-cacher-ng - Apt proxy not available anymore ?"
date: 2018-09-21
forum: Server Platforms
---

### Post by jibe-dodemont on 2018-09-21
Hello everyone,


I have been a french computer science teacher for many years and so far I have been doing many activities with my students based on the Ubuntu Server distribution.
We were still using Ubuntu 16.04 LTS last year.


Unfortunately for us, our internet line is not very efficient. When thirty or so students install a new apt package at the same time, it takes a loooong time! I do not even tell you what happens when they launch their updates!

To solve this problem, I was using "apt-cacher-ng" which was available in the 16.04LTS. It worked very well! This was even bringing us an 80% savings on Internet bandwidth consumption! Magnificent !

I started to prepare a new virtual server with the 18.04LTS and I am horrified that this package is no longer available. Why ?


I think the project is not really active anymore. Is it because of library incompatibilities that it has been removed?


I started looking for ways to install it from other repositories, or from sources, but I can not find reliable references.


Could you help me ?
An explaination ?
A deb repository ?
A source compatible with the 18.04LTS?

Best regards 

Jibé

---

### Post by darkod on 2018-09-21
According to the search it is available (in the universe repository): [https://packages.ubuntu.com/search?keywords=apt-cacher-ng&searchon=names&suite=bionic&section=all](https://packages.ubuntu.com/search?keywords=apt-cacher-ng&searchon=names&suite=bionic&section=all)

Where did you check?

Make sure that repo is enabled on your server and try installing the package with apt-get.

---

### Post by jibe-dodemont on 2018-09-22
Dear Darko,

You solved my problem !

Thank you so much for your fast answer. I was not searching with the right tools. 

On the 16.04, the package was ready to install just after a bare new installation of Ubuntu Server.

With the 18.04, i dont know if the package has been moved in the universe repository or if the universe repository is not anymore installed in the basic server installation.
BUT with a simple :
 sudo add-apt-repository universe
the package IS installable !

Thanks a lot !

Jibé

---

