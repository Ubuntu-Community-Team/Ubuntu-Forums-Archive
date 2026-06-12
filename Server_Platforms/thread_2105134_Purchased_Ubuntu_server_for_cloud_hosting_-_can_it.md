---
title: "Purchased Ubuntu server for cloud hosting - can it only be managed via command line?"
date: 2013-01-15
forum: Server Platforms
---

### Post by ltwinner on 2013-01-15
I am developing a Java EE web app that I will be uploading to the net soon.

I purchased some cloud hosting yesterday for it. I emailed the webhosts about how to set up this hosting with a domain name I also purchased. Here's what I was told in the reply -

> It appears that you have chosen a Ubuntu 12.04 x64 template, it is managed via the command line and direct modification of config files. Please also be aware that it is an unmanaged platform unless you opt for the enhanced support options, of which you can see more on at:

[LIST=1]
[*]What's the deal here, is managing hosting via the command line a standard way of managing an Ubuntu server or cloud hosting in general?
[*]I would much prefer some kind of GUI so I can use a package manager and various other tools to setup and administrate this server. Is this not possible with a Ubuntu server?
[*]Are there other server platforms where it is possible to use a GUI?
[/LIST]

---

### Post by spynappels on 2013-01-15
CLI is the normal way to administer an Ubuntu server, although there is nothing to stop you using a GUI.

Just be aware though that this can increase the attack surface of your server, and as hosted servers normally do not have masses of RAM, it could add serious overhead.

It is often recommended to spend some time getting familiar with the CLI as this is the most flexible and powerful way to administer any Linux/Unix server.

You can install any Desktop Environment you want, for a low power server I'd recommend Lxde or Xfce, you can get familiar with either of these by looking at Lubuntu or Xubuntu respectively.

---

