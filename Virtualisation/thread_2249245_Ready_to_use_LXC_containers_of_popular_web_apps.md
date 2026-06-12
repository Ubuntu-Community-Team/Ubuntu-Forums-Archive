---
title: "Ready to use LXC containers of popular web apps"
date: 2014-10-20
forum: Virtualisation
---

### Post by raulb on 2014-10-20
Hi Ubuntu users,

We have been working on a [LXC focused website]("http://www.flockport.com") for users to download and share containers that should be useful for the LXC community here. 

We already host [ over 40 containers of the most popular apps]("http://www.flockport.com/containers") including Wordpress, Drupal, Discourse, Redmine, Gitlab etc even a mail server that LXC users can deploy in seconds. 

Flockport provides ready to use [LXC containers]("http://www.flockport.com/containers") that folks can download and deploy in seconds, [tons of guides]("http://www.flockport.com/news") and [documentation including videos]("http://www.flockport.com/documentation") on using LXC, especially networking and a platform for users to share containers. 

There is still a lot of confusion about LXC, and updated documentation, packages and support beyond Ubuntu is scant. We think LXC is fantastic and the main purpose of Flockport.com is to make LXC easy to use for all users. We hope a lot of users here will find this helpful and will contribute to the nascent LXC community at Flockport too.

---

### Post by TheFu on 2014-10-20
I look forward to trying this stuff out! 
Thanks for posting!

---

### Post by raulb on 2014-10-21
Please do and it would be great to have your feedback, we welcome more LXC users trying out Flockport. Linux containers are a very efficient and flexibile way to deploy apps. 

And with Flockport we want to ensure there is tons of updated documentation, use cases and a growing collection of easy to deploy containers.

Ubuntu is in the unique position of being the best supported distro for LXC, since the LXC project is supported by Ubuntu. We are trying to do the same for Debian with updated packages so LXC works as well out of the box as it does in Ubuntu.

---

### Post by TheFu on 2014-10-21
Tried it and failed following the Ubuntu instructions.  
```
$ sudo lxc-create -n  lxc-test
lxc_container: Error creating container lxc-test

```

Or did I miss something?  BTW, the instructions leave out creating a new container - at least they are not OBVIOUS ENOUGH for me. Other instructions say downloads happen automatically. Plus it is unclear where the downlaoded files need to be placed. I'm dense that way when provided step-by-step instructions ... almost.

All steps prior to that seemed to work perfectly. I did reboot. This is running on real hardware, not inside a VM. 
lxc-checkconfig returns all green/enabled.

Ideas?

Guess I need an **LXC for Dummies Primer**?  BTW, I've watched a few videos from Flockport before starting.

---

### Post by raulb on 2014-10-23
thefu- your command to create the container seems wrong. You didn't pass the container OS template flag to use for creating the container.

It should be ```
sudo lxc-create -n nameofcontainer -t template
```

There is a [LXC getting started guide]("http://www.flockport.com/lxc-guide/") and a [video walkthrough]("http://www.youtube.com/watch?v=XzfIly0rloo") that covers basic LXC functions, and lxc-create is the first one covered. I see some scope for confusion and have updated it. 

WIth the lxc-create command you need to pass the name of the container and the os template you want to use. There are more than 15 container OS templates including Debian, Ubuntu, Fedora, Gentoo, Alpine etc

So to create let's say a Debian container that you want to call 'thefu' you would use the command like this:

```
sudo lxc-create -n thefu -t debian
```

---

### Post by raulb on 2014-10-23
The download you are referring to is probably the 'download' template. When you want to create a container you can use container OS templates that are available locally with the LXC installation. 

The templates in your local LXC installation are stored in /usr/share/lxc/templates (Ubuntu) or /usr/local/share/lxc/templates depending on the distribution. So a basic ls listing like below would show you the templates available locally

```
ls /usr/share/lxc/templates
```

And that's what the instructions in the post above cover.

There is also something called a 'download' template . These are downloaded from the linuxcontainer.org website. These are generally more updated container OS templates, and are mainly designed to create '[unprivileged containers]("http://www.flockport.com/faqs/")'. 

For instance to use a 'download' template you would use a command like this:

```
lxc-create -t download -n thefu -- -d debian -r wheezy -a amd64
```

Where -d stands for distribution, -r for release and -a for architecture.

To see a list of download container OS templates available you would use this:

```
lxc-create -t download -n thefu
```

I can see the scope for confusion and have updated the LXC getting started guide accordingly. Some of this stuff can get very complex and frustrating quickly and that's why we have tried to provide as much documentation as possible and screencasts to make it easy. 

We do not want users googling endlessly especially since a lot of information regarding LXC is unfortunately often outdated. However its important to go through the documentation we have carefully to avoid frustration, all the information is there.

---

### Post by TheFu on 2014-10-23
That got me thru - thanks!

Don't know how I could have missed the need to specify a template?  Ah - I see how: 
[http://www.flockport.com/start/](http://www.flockport.com/start/) with the Ubuntu tab doesn't clearly say to get templates with a command like the debian tab (probably?) does.

Getting the template took about 4 min.  All is well now.

BTW - I specified "ubuntu" - after all, look where we are. 

Short answer for pure LXC:
```
sudo add-apt-repository ppa:ubuntu-lxc/stable
sudo apt-get update sudo apt-get install lxc 
lxc-checkconfig

```
Edit /etc/default/grub; add or append this (be careful, screwing this line can prevent booting):
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet cgroup_enable=memory swapaccount=1"
```

Don't forget to reboo
```
update-grub
lxc-ls -f
sudo lxc-create -n lxc-test -t ubuntu
sudo lxc-start -n lxc-test -d

```
Now just connect to the lxc-test container and treat it like a base, minimal Ubuntu. Default userid/password is: ubuntu:ubuntu - so change those immediately.  Ubuntu lxc will create a NAT subnet 10.x.x.x for us automatically. 

```
# du -sh /var/lib/lxc/*
524M    /var/lib/lxc/lxc-test
4.0K    /var/lib/lxc/ubuntu
```
Under 600M for a minumal Ubuntu OS - nice. It does cut back on some expected packages, however. I installed aptitude, so the size is slightly higher (more dependencies than I expected were added).

Regardless - these pages helped get me over the lxc troubles I've had in all prior attempts. THANKS!

---

### Post by raulb on 2014-10-23
Excellent! Once you use it for a couple of days and with proper documentation it becomes really simple to use.  I have an alpine linux container that is 5.7MB on disk! The Debian base container comes in  around 220 MB for the 32 bit and around 260 MB for the 64 bit container

The Flockport Wordpress container with the full stack of php, nginx and mysql is around 120 MB compressed and 600 MB on disk.

You should have a look at the [LXC advanced guide]("http://www.flockport.com/lxc-advanced-guide") and some of the guides in the [news section]("http://www.flockport.com/news") should be helpful.

---

### Post by TheFu on 2014-10-23
The documentation has been extremely helpful.

I'm fairly competent at virtualization - over 15 yrs practicing.  Used Xen paravirtual for about 4 yrs, which seems very similar from a high level. Also used Solaris containers a bunch starting in 2006-ish. KVM is the main VM platform for us now. Started switching from Xen and ESXi in 2010.  Finished around 2012. We are extremely happy with KVM, but would always like a little less RAM use and a little less overhead, while maintaining both security and some level of system compartmentalization.  

The idea that we cannot patch a kernel for a high-risk container without taking all containers on the server down is concerning. Do live migrations work for LXC to different kernels? Seems I have some research and lab testing to do.

---

### Post by raulb on 2014-10-23
Wow, with that background LXC should be childs play.  You will soon be writing guides for us :) KVM is fantastic. I think LXC is another great option to have to deploy apps and workloads. And for Ubuntu users unprivileged containers work out of the box, giving users that much more security. 

Live migrations don't work. There is a project CRIU and I did see some discussions in the LXC dev lists about this, but from what I understand CRIU is still far from getting merged in the kernel.

---

### Post by bmullan2 on 2014-10-29
I think the live migration capability is close to being ready but not sure if CRIU (checkpoint & restore) and it are fully functional yet.

This blog is fairly recent and talks about what the author found:

[http://tycho.ws/blog/2014/09/container-migration.html](http://tycho.ws/blog/2014/09/container-migration.html)

---

