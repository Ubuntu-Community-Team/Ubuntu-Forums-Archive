---
title: "Kid safe pc?"
date: 2007-09-28
forum: The Cafe
---

### Post by luvdemheels on 2007-09-28
I have children ages 9 to 4. I want to make a kid safe pc for them with ubuntu. They currently have their own pc that dual boots with windows. I want to just run ubuntu but need to know how to set it up so they can browse the internet without me worrying if they get to the wrong site.

Any ideas for ubuntu?? Hopefully something easy to setup with a gui.

---

### Post by PatrickMay16 on 2007-09-28
I don't have much expertise on this. 
But here is something I do know. If there's a particular site you want to block, you could put something like this in the /etc/hosts file:


127.0.0.1 [www.blockedwebsite.com](www.blockedwebsite.com)

That will make it so that it is not possible for one to get to the example site "blockedwebsite.com".

---

### Post by HermanAB on 2007-09-28
Hmm, there is Edubuntu.

Cheers,

Herman

---

### Post by regomodo on 2007-09-28
opendns

Get an account, set it up and use the filters. 

Done

---

### Post by PriceChild on 2007-09-28
> **regomodo said:**
> opendns

Get an account, set it up and use the filters. 

Done+1

Set your router up with opendns instead of the machine, so that every time your machine dhcp's with it, it will get the opendns stuff settings again incase.

---

### Post by Dark Aspect on 2007-09-28
> **PatrickMay16 said:**
> I don't have much expertise on this. 
But here is something I do know. If there's a particular site you want to block, you could put something like this in the /etc/hosts file:


127.0.0.1 [www.blockedwebsite.com](www.blockedwebsite.com)

That will make it so that it is not possible for one to get to the example site "blockedwebsite.com".
hmm..........Would there be a way to do that with Windows XP?

I use Ubuntu but I was wanting to block a site form someones XP computer.

---

### Post by adamonduty on 2007-09-28
There is an /etc/hosts equivalent file in Windows.... I think it is under c:\windows\system32\drivers\etc .

---

### Post by Dark Aspect on 2007-09-28
> **adamonduty said:**
> There is an /etc/hosts equivalent file in Windows.... I think it is under c:\windows\system32\drivers\etc .
Thanks I'll look around the system32 folder.

---

### Post by n3tfury on 2007-09-28
don't forget to enable hidden files


in windows explorer:  tools>options>view>hidden files and folders>show hidden files and folders

---

### Post by southernman on 2007-09-28
I don't think edubuntu makes the desktop automatically "kid safe" as what your looking for, but I'd suggest if you don't use edubuntu over Ubuntu, I'd still opt to install the educational programs for your childrens age range(s).

Do as already Pricechild confirmed and added own suggestions to.

Good Luck.

---

