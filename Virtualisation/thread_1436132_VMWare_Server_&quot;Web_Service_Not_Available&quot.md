---
title: "VMWare Server &quot;Web Service Not Available&quot;"
date: 2010-03-22
forum: Virtualisation
---

### Post by matthewsmart on 2010-03-22
Hello!

I have vmware server 2.0.2 installed on a Karmic box. It worked in the past, and then this error started occuring after I changed some network settings (static IP addresses). Now, whenever I try to log in to the web interface at [https://192.168.1.200:8333/ui/#](https://192.168.1.200:8333/ui/#) I get the error:

Web Service Not Available

This occurs whether I use correct credentials, or just made up username/password pairs. I have read a couple of posts about this occurring before, but nothing that seems pertinent. I have of course restarted all of the vmware services, and cleared all of the server certificates out of my browser. I hope somebody out there has some ideas. Thanks for your time!

---

### Post by matthewsmart on 2010-03-22
update:

The only record of there being a problem in any of the log files that I have is in /var/log/vmware/webAccess/proxy.log where I get the following: 

```
[2010-03-22 13:47:28,204,http-8308-11<=>,RequestProcessor] Error processing action request /action/login : [ServiceNotAvailableException] (301)Moved Permanently
```

---

### Post by knowram on 2010-05-12
I am having the same problem. Did you ever find a fix?

---

### Post by matthewsmart on 2010-05-12
Nope. Tried a lot of things, but nothing ever solved the problem. Sorry. After a month of having no access to our VMs, my boss eventually opted for KVM.

---

### Post by knowram on 2010-05-12
KVM? how is that helping you access your VM's. Are you not running ubuntu server as your base OS, or where you able to get vmware server console to work? As fare as I have been able to tell this web gui is the only way to get to vm's when you are using vmware server. Am I missing something?

---

### Post by matthewsmart on 2010-05-12
We run hosted machines using kvm. We dumped VMWare Server as our virtualization solution. There is no native web interface for KVM hosted machines. You can access them over a command line, and you can view the desktops using something like remote desktop. The documentation for all of this can be found here: [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

