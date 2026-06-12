---
title: "Updating multiple Ubuntu-machines simultaneously"
date: 2014-01-13
forum: Server Platforms
---

### Post by 11303925 on 2014-01-13
Hello everyone

I'm currently working on a ICT-project as a system administrator in a highschool involving several Ubuntu-machines.
The goal of the project is to find a way to update the computers (Ubuntu) in the network simultaneously. If it's possible, via a command or a series of commands.
I've been looking into this forum to find a solution and I found two things: Landscape en Puppet.
Landscape is no option because it is too expensive. On a threat I found something called Puppet, but I have no idea how this works.
Is there a solution to my problem?
If Puppet is my answer, can someone explain me how to configure the pc's in the network?

Thanks for helping!

Robby

---

### Post by houstonbofh on 2014-01-13
Puppet and Chef are both very powerful system management tools.  But, like all very powerful tools, they are more complex than a single post. You will need to pick one, and take some time to learn it.  However, once you know it, you become quite marketable in the Linux admin space.

---

### Post by devine.steve on 2014-01-13
I manage a large scale system of Linux machines and I use dsh (Distributed Shell) Once set up you can run one command on all the machines over ssh. We have a common NFS share and can reference files in the mounted drives. It works really well.

---

### Post by 11303925 on 2014-01-14
Thanks for replying.
I've tried dsh and it's the thing I'm looking for.
There is just one problem: when I try to use a command to reboot a system in my network, it won't work.
The command I use is: dsh -a -c sudo reboot
Then I give in my password and the next message shows: sudo: no tty present and no askpass program specified

Thanks!

---

### Post by devine.steve on 2014-01-14
You can look into using tee to feed it the password. Another option is to permit root login and use a ssh key to login as root. This is not suggested if you are just starting out in Linux. In our case we allow root logins but we have ssh locked down via firewall, tcp wrappers and vlans.

---

### Post by nerdtron on 2014-01-14
We use this: [https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)
Basically when a computer on the network updates and downloads packages, the apt-cache servers stores the packages so that when other computers update, they don't have to redownload from the internet, they would just copy the ones from the cache server. It will be fast since it is copying only on the LAN.

---

### Post by 11303925 on 2014-01-22
My problem is solved.
I used dsh to run the commands across all the machines. Just had to figure out how to work with the private/public keys.

Thanks a lot you guys!

---

