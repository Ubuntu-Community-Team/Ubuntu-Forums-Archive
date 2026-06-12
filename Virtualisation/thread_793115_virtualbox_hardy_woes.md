---
title: "virtualbox hardy woes"
date: 2008-05-13
forum: Virtualisation
---

### Post by newbsawbit on 2008-05-13
Well, I´m going to put down my shovel and stop diggin my hole deeper. Wow, did I break a lot of software when I upgraded to Hardy. Most importantly Virtualbox which I need for all my finances/billing because I´m still married to msMoney since it&#347; the only thing that talks to my pocketpc. At first it was telling me to run /etc/init.d/vboxdrv setup, but when I did I was getting  make errors in /var/log/vbox-install.log. I tried installing the headers and rerunning the command twice, (per thread @ [http://www.ubuntu-forums.com/showthread.php?t=458494]("http://www.ubuntu-forums.com/showthread.php?t=458494"))
but that didnt work either. Then I installed the ose modules (per thread @ [http://ubuntuforums.org/showthread.php?t=737305]("http://ubuntuforums.org/showthread.php?t=737305")) 
and was able to boot up my existing vmachine - thought I was scott free untill i realized no usb in ose, so no pocketpc or printer. Then I tried to reinstall the puel? version, but no luck, think it was another make error. I also tried the hardy deb downloaded from suns website, but it couldnt make the kernel module either. Now I cant even get ose to work. Help!!!

---

### Post by newbsawbit on 2008-05-13
Well I was able to get it workin thanks to the help of a kind and experienced user in the virtualbox irc. 
first remove - 
> sudo aptitude remove virtualbox-ose virtualbox-ose-modules-`uname -r`
then download and install new version from website:
[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")
(binary - hardy)
worked like a charm
no i just need to iron out the guest additions
oh and by the way - this doesnt remove your old vmachine - it comes right back up

I cannot express the gratitude I feel for those who donate their time and expertise to help others.

---

