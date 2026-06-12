---
title: "Can Ubuntu run a server in a Windows VM?"
date: 2010-05-28
forum: Server Platforms
---

### Post by HittingSmoke on 2010-05-28
My main PC is not running Windows 7 full time because I got back into gaming. I'm getting back into web development and I need to install a local test server. XAMPP isn't working right (I've not troubleshooted it yet).

I would like to set up a Linux install running Apache. This would be even more convenient if I can install it on my Windows 7 PC in a virtual machine, run a server on it and just start it up whenever I need it and connect to it from the Windows PC. I could learn a bit more about server management this way and would have a quick easy way of starting up my test server only when I needed it.

In short, if I installed a Ubuntu server edition in a VM inside Windows 7, would I be able to install Apache on it and connect from my Win 7 install while the VM is minimized?

---

### Post by Ryan Dwyer on 2010-05-28
Yes.

---

### Post by flandercan on 2010-05-28
A nice quick solution

VMWARE Player 3 from [www.vmware.com](www.vmware.com) (FREE)

and 

Ubuntu Web Server @ VmMarket Place (FREE)
 
[http://www.vmware.com/appliances/directory/1092](http://www.vmware.com/appliances/directory/1092)


Although there are lots of other VM environments like virtual box or dare I say eekk  (virtual PC) I have been running VMPlayer , VMWorkstation and ESX platforms for many years and love the product hence the vmware recommendation. 

fc

---

### Post by HittingSmoke on 2010-05-28
> **Ryan Dwyer said:**
> Yes.

> **flandercan said:**
> A nice quick solution

VMWARE Player 3 from [www.vmware.com](www.vmware.com) (FREE)

and 

Ubuntu Web Server @ VmMarket Place (FREE)
 
[http://www.vmware.com/appliances/directory/1092](http://www.vmware.com/appliances/directory/1092)


Although there are lots of other VM environments like virtual box or dare I say eekk  (virtual PC) I have been running VMPlayer , VMWorkstation and ESX platforms for many years and love the product hence the vmware recommendation. 

fc

Thanks!

So it would be as easy as typing 127.0.0.1 or localhost in the browser to access the server if I'm trying to access it from outside the VM environment?

---

### Post by BobVila on 2010-05-28
> **HittingSmoke said:**
> Thanks!

So it would be as easy as typing 127.0.0.1 or localhost in the browser to access the server if I'm trying to access it from outside the VM environment?
127.0.0.1 would be the loopback for whatever machine you're on. You'll need to connect to the IP of the VM, which will be distinct from that of your host machine. A quick "ifconfig" will tell you what IP to use.

---

### Post by HittingSmoke on 2010-05-28
> **HittingSmoke said:**
> Thanks!

So it would be as easy as typing 127.0.0.1 or localhost in the browser to access the server if I'm trying to access it from outside the VM environment?

That's what I thought but I wasn't sure, thanks!

> **BobVila said:**
> 127.0.0.1 would be the loopback for whatever machine you're on. You'll need to connect to the IP of the VM, which will be distinct from that of your host machine. A quick "ifconfig" will tell you what IP to use.

The download link for Ubuntu Web Server is down, I have a Ubuntu server ISO which I'm assuming I can just use then install the applicable software?

---

### Post by BobVila on 2010-05-28
> **HittingSmoke said:**
> That's what I thought but I wasn't sure, thanks!



The download link for Ubuntu Web Server is down, I have a Ubuntu server ISO which I'm assuming I can just use then install the applicable software?

most definitely. Won't hurt to know how to install those packages and get 'em running, anyway  ;)

---

### Post by fro1269 on 2010-05-28
> **HittingSmoke said:**
>  I have a Ubuntu server ISO which I'm assuming I can just use then install the applicable software?

you will want to install the LAMP package when prompted

---

### Post by Vegan on 2010-05-29
YOu cannot easily get Linux to work with the Microsoft Virtual PC as Microsoft is hostile to Limux.

I use a separate machine for Linux, this way I can have the best of both worlds.

---

### Post by HittingSmoke on 2010-05-29
> **BobVila said:**
> most definitely. Won't hurt to know how to install those packages and get 'em running, anyway  ;)

> **fro1269 said:**
> you will want to install the LAMP package when prompted

> **Vegan said:**
> YOu cannot easily get Linux to work with the Microsoft Virtual PC as Microsoft is hostile to Limux.

I use a separate machine for Linux, this way I can have the best of both worlds.

Got Ubuntu server running with LAMP inside VMware Player and it's working great. Thanks a lot guys.

One last question. Is there an easier way to transfer files other than with FTP? I've used VirtualBox with an add-on that you can install in the virtualized OS that lets you make a shared folder, but I don't know how to do that using the CLI.

---

