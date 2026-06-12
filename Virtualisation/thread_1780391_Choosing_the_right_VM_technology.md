---
title: "Choosing the right VM technology"
date: 2011-06-11
forum: Virtualisation
---

### Post by JGSD on 2011-06-11
I've been using VMWare on a 8.04 Server LTS installation for a few years for one project and now I have another project to set up a new VM host.

I'm not particularly excited about the prospect of using VMWare Server again since there hasn't been an update for a long time, and I wasn't exactly thrilled with the system performance overall anyway.

So, I'm looking at other technologies, but the information on the options available seems quite confusing, so I thought I'd just go and ask.

The setup I am trying to create is a VM host that will have a full-blown version of Ubuntu Desktop 11.04 with LTSP for a group of 15 thin clients to boot graphical desktops from. This is pretty much the setup I have in VMWare on the old server, but like I said, there have been some performance issues. It's usable, but I think it could be better.

To start with, [http://www.ubuntu.com/business/server/virtualisation](http://www.ubuntu.com/business/server/virtualisation) says that KVM is the core option for both host and guest virtualization in Ubuntu Server. That sounds promising, but then [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM) says that KVM is "primarily for non-graphic servers" which, although a little unclear, makes me think that it may not suit my purposes.

The "mega thread" here in this forum doesn't give any specific information about which technology is the best for a graphical environment but it does say that OpenVZ works is the fastest. However, it doesn't seem to be officially supported by Ubuntu and [https://help.ubuntu.com/community/OpenVZ](https://help.ubuntu.com/community/OpenVZ) points out that KVM is the officially supported VM tech of Ubuntu.

So my question is basically this: What would you recommend in terms of VM tech for an Ubuntu Server VM host installation with an Ubuntu Desktop client running LTSP? I don't really mind whether I admin Ubuntu Server graphically or via CLI, but obviously I'll need some way to access a graphical interface of the host.

Sorry for the long post, but I didn't want to come across as someone who is just asking a lazy question without having done any research first :-)

Joseph

---

### Post by cwmoser on 2011-06-14
vmWare Server with the web interface was a performance dog.  I went to using vmPlayer after that.  Now that I have experienced VirtualBox, I think it is the better choice.

Have not tried KVM.

Carl

---

