---
title: "About to Set Up Ubuntu Server, Have a Question"
date: 2011-01-10
forum: Server Platforms
---

### Post by jlacroix on 2011-01-10
Hello everyone. I have a client that owns a small business and I am setting up his network. By small I mean three computers, and potentially one server. Only one more computer might be purchased over the next year. He has one program that he needs to have hosted on a server to be used internally. He will also use the server for file sharing.

My initial inclination is to set up a server with Ubuntu server, and set up a Windows Server VM for his shared app (which requires Windows). My thought is to not have his entire server running Windows, only what is absolutely required to use Windows. I will use Samba for the file sharing.

What I want to achieve is to have the virtual machine start up when the server is turned on, and shut down whenever the server is turned off. The virtual server is to have a static IP.

My question for you guys is which hypervisor package do we download or purchase to accomplish this? I think Virtualbox is out of the question because (as far as I know) it requires you to start the VM's manually. We're only going to have a single virtual machine hosted on an Ubuntu server.

---

### Post by koenn on 2011-01-10
sounds overly complex for such a small environment.
Is this server just going to do file sharing and that Windows app ?

If so, what's your rationale for having this virtualized, or for having Ubuntu ? Windows does Windows File sharing quite well. 

ALso, do you expect that server to be turned on and off alot ? Why ?

---

### Post by jlacroix on 2011-01-10
> **koenn said:**
> sounds overly complex for such a small environment.
Is this server just going to do file sharing and that Windows app ?

If so, what's your rationale for having this virtualized, or for having Ubuntu ? Windows does Windows File sharing quite well. 

ALso, do you expect that server to be turned on and off alot ? Why ?

Here's my reasoning.

1.) I want the virtual machine to load up automatically because the owner isn't going to know how to log in and start a virtual server if the power was to go out, nor would he want to be bothered with doing so.

2.) From experience I know not to rely on straight Windows Server. I don't want one virus to kill the entire server. (And I've had this happen). I use Linux with all my clients unless they absolutely need Windows Server for something.

3.) We're just going to be purchasing a standard desktop computer for the server (since it's only three users) and I'll be doing a simple RAID1. Most desktop computers don't have drivers for Windows Server if I were to install that direct. However, Windows Server loaded in a virtual environment would just use the guest additions for the drivers.

---

### Post by elico on 2011-01-10
well it depends on you windows envierment.. needs... cpu ... ram ... latency.
but you can always use zen...
or any thing that realeated..
like PROXMOX
[http://www.proxmox.com/](http://www.proxmox.com/)
or just ubuntu HYPERVISOR(XEN)
or even CITIRIX XEN 
[http://www.citrix.com/English/ps2/products/product.asp?contentID=683148](http://www.citrix.com/English/ps2/products/product.asp?contentID=683148)


i have used virtualbox, vmware ESX, XEN, OPENVZ and i must say that you can build you own hypervisor with xen 
but as long as you have a good product that just works without playing basketball with you it's very full to work and not debug stupid stuff.

---

### Post by koenn on 2011-01-10
> **jlacroix said:**
> Here's my reasoning.

1.) I want the virtual machine to load up automatically

Vmware does that.

---

### Post by jlacroix on 2011-01-11
Thanks guys.

---

