---
title: "Best software sources for Ubuntu Server 14.04"
date: 2014-08-03
forum: Server Platforms
---

### Post by ally2 on 2014-08-03
Hi guys have been away from Ubuntu for a little while so am a little bit rusty :)

My question is when I setup a new Ubuntu Server install what sources should I add to get the best packages? 
what sources do you add for your sever builds and can you remind me of the process of adding sources 


Many Thanks

:)

---

### Post by ibjsb4 on 2014-08-04
To add sources you need to open up the console editor 'Nano' (already installed).

[https://help.ubuntu.com/community/Nano](https://help.ubuntu.com/community/Nano)

And then edit your sources list.

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

This method I find to be a pain in the ..

I think it is easier to just add a simple server gui

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=server+gui&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=server+gui&as_qdr=all&sa=Google+Search&lang=en)

And use synaptic package manager

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by Bucky Ball on 2014-08-04
You improve your chances of support if you use thread titles describing your issue/question rather than generic ones. I have changed this one to help things along. Good luck. (As far as I know, a server install will already come with default software sources ... what do you want to add package wise, exactly? Have you checked they are not already available? A server should be kept to the minimal, normally, so try and avoid adding sources you don't need, especially third-party PPAs.)

---

### Post by ian-weisser on 2014-08-04
> **ally2 said:**
> when I setup a new Ubuntu Server install what sources should I add to get the best packages?

I use the defaults that come with the Ubuntu Server install...the normal Ubuntu Repositories.
I have never felt a need to add any other sources to my servers.

I an confused what you mean by 'the best packages' on a server? Is there such a thing as a bleeding-edge-sshd? The newest-featured-httpd? That fabulous-shiny-new dhcp? Is there really some other source for great (or lousy) supported Ubuntu-compatible server software?

---

