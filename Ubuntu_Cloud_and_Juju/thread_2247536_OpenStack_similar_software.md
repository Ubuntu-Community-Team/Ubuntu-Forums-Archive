---
title: "OpenStack similar software"
date: 2014-10-08
forum: Ubuntu Cloud and Juju
---

### Post by psca119.tech on 2014-10-08
Hello! I am new to the Ubuntu Forums, and have been posting on [http://4chan.org/g/](http://4chan.org/g/) for simple questions of what I am trying to attempt as something that I'm not sure if it has done before, but I wish to be a host, and my end result is possibly to host the three following services in a cloud like system:

- Webhosting (Free & Premium) (Subdomains: joe.mydomain.com)
- Minecraft Server Hosting (Spigot/Bukkit below 1.8)
- Ventrilo Servers
- FIle Hosting

I have many questions but for now I will stick to the most relevant, I will attach an img of my 1 minute drawn diagram.
Mainly I do not like the design of OpenStack, and it's just not for me, maybe in the future, but for now I want my services up and running with something stable,
1) MaaS sounds like what I'm trying to do, but without JuJu, is there a way to simply plug that power into some HyperVisor software that is web-based, like the OpenStack Instance Console? a simple login? a way to modify MaaS to add a page that allows me to spin up and stop instances?
2) My Lenovo TS130 has 14 GB Physical ram, dual-core i3 hyperthreading CPU's, and finally 500 GB HDD storage, how in heck does OpenStack, just from that single server give me at least double the amount of resources:
3) All done in Ubuntu, and no vmware and an attempt to stay away from virtual box would be nice.

50 GB Memory
10 vCPU's
1000 GB Storage

Note I turned Swap OFF. Yet I still get at least 2x the amount of (virtual?) memory? How am I able to get these "Pools" of resources like OpenStack, and simply plug computers via ethernet into a network switch and use them as slaves with MaaS to achieve nodes as the pools of resources and to goto for example: [http://mydomain.com/MAAS](http://mydomain.com/MAAS) or something and then able to see and manage VM's from there, I am not thinking of spinning up 20 VM's, maybe around 3 MAX...

I suppose my next question would be after this is working, in the VM's without using any database is it possible to simple read and write to a php file and save the user details there in a MD_5 hash? Well, I know it is possible, but is it worth it? I have tried many databases and simply do NOT like them at all, and it seems like extra effort to use them to just write a php library to register/de-register users from a php file, async actions might be a conflict however... My real question is what webserver should I use that is similar to IIS, since its super simple and I can literally just bind it to a port and an address and it was super easy and I could run on HTTPS if I wanted to super easy, is there a way to do that, AND have website automation, so when the user registers for webhosting service, he gets a editor, and it creates a new sub-domain that he names it, and to have a <footer> that he cannot remove maybe in php
<?php
require 'http://mydomain.com/assets/footer.php';
?>
and make this forcefully appear, so they only in the editor have control of <head> <body> but not <footer>?


Sorry to post such a long and annoying question, I hope to learn from this experience.
Thanks!

Diagram:
[ATTACH=CONFIG]257054[/ATTACH]
Tags: ubuntu, server, maas, cluster, virtual machine, openstack, switch, help, network, cloud, hosting, minecraft, website, files.

---

