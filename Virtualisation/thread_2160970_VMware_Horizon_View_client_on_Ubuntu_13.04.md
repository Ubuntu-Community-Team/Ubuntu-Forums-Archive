---
title: "VMware Horizon View client on Ubuntu 13.04"
date: 2013-07-08
forum: Virtualisation
---

### Post by peedeeramone on 2013-07-08
I haven't seen much information out there about anyone getting the proprietary VMware View client to work in 13.04.  I was able to get the open client to install without a problem, but I believe the proprietary version is more feature packed and I would like to try that version out.  Whenever I attempt to install it, however, I get dependancy errors.  I have seen this with a few different Ubuntu 13.04 installs so I don't believe it to be my particular system, rather an issue with the default software in Ubuntu.  Has anyone else had any experience with this, and if so have any advice on getting it working?  I'm a View administrator at work and I'd love to have it rocking on my Ubuntu desktop at home.

Thanks!

---

### Post by tlotr on 2013-07-09
Hi,

I am having this same problem in 13.04. I have got this link from where we can download VMware Horizon View but when I click on download it opens a popup asking to open the apt with which application and there are no applications to select from. 

[https://my.vmware.com/web/vmware/details?downloadGroup=VIEWCLIENTS_LINUX32_200&productId=331&rPId=3638#product_downloads](https://my.vmware.com/web/vmware/details?downloadGroup=VIEWCLIENTS_LINUX32_200&productId=331&rPId=3638#product_downloads)

Can someone please help in getting this installed on Ubuntu 13.04. 

I also tried the steps provied in this pdf file [https://www.vmware.com/pdf/horizon-view/horizon-view-client-linux-document.pdf](https://www.vmware.com/pdf/horizon-view/horizon-view-client-linux-document.pdf) but still unable to install it through synaptic package manager as well. There is no vmware-view-client option available.

---

### Post by peedeeramone on 2013-07-10
I think I can actually answer both of your questions, though I don't think it will actually help you since you will still be stuck.  Anyway, for the program to open them I had to manually point firefox to apturl.  I belive it is in /usr/bin but it may have been some other directory. Google can help you there.  Also, you will need to enable Ubuntu partners repo.  Open up the software & updates window (I just hit win/sys key and type sources) and go to the other software tab from there select canonical parters.

I haven't looked through the .pdf but I'll see whats in there later.

---

