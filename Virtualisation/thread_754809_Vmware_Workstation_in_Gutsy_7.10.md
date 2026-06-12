---
title: "Vmware Workstation in Gutsy 7.10"
date: 2008-04-14
forum: Virtualisation
---

### Post by TpyKv on 2008-04-14
Good morning,

I have been trying to install VMware Workstation 6.0.3 for Linux, in Ubuntu gutsy, with no success...

I have scoured the internet and this forum but still none the wiser.... as one person says I should download the RPM and convert to a DEB. Another person says that converting like this is bad practice and is known to be unstable.... I tried it anyway and it doesn't work...

The only two files you can download are .rpm and .tar - as I need .tar.gz to work in Ubuntu - does anyone know how this will work?? can I convert the .tar to .tar.gz? the tar just will not extract....

Many thanks!!

---

### Post by hyper_ch on 2008-04-14
you can find the server version in the canonical partner repos... that's probably the easiest way.

---

### Post by TpyKv on 2008-04-14
thanks - is the server the same as the workstation & is it for 6.0.3 - the one with full ubuntu support?

---

### Post by TpyKv on 2008-04-14
I tried it again and it worked this time!! think I might not try and do anything clever at midnight again :)

thanks for your time!!!

---

### Post by TpyKv on 2008-04-14
OK mayb  that post was a bit premature!

it says that it has not been correctly configured, and I need to run usr/bin/vmware-config.pl. 

I do that - but it tells me to do so again !!!? is there something else I should be doing??

---

### Post by hyper_ch on 2008-04-14
```

sudo vmware-config.pl

```

---

### Post by TpyKv on 2008-04-14
thanks for the reply, 

yet that is what I am doing and every time it tells me to do the same thing again...

is it going to stop asking and work if I try it 100 times? 

:)

---

### Post by hyper_ch on 2008-04-14
what exactely does it tell you?

---

### Post by TpyKv on 2008-04-14
It says I need to run the confog script - 

[http://premium1.uploadit.org/mentholist//config.png](http://premium1.uploadit.org/mentholist//config.png)

and then I do it, and it says it again??

I have found somewhere saying I need g++ installed..will try this now...

---

### Post by hyper_ch on 2008-04-14
no clue, never used the workstation... only the server...

---

### Post by TpyKv on 2008-04-14
OK thanks anyway!!

:)

---

### Post by TpyKv on 2008-04-14
Hello,

This is my second thread with the same problem but as the other one got somewhat drawn out, I wanted to start again!

I have installed 6.0.3 workstation and have ran the vmware-config.pl, yet every tme I try to run the vmware command it says I need to the the vmware-config.pl part **_again._** I have installed everything from G++, build essential and linux headers but it still wont work... does anyone have any idea what I might be doing wrong??

[http://premium1.uploadit.org/mentholist//config.png](http://premium1.uploadit.org/mentholist//config.png)

many thanks!!

---

### Post by hyper_ch on 2008-04-14
I'd use vmware server

---

### Post by bodhi.zazen on 2008-04-14
> **TpyKv said:**
> Hello,

This is my second thread with the same problem but as the other one got somewhat drawn out, I wanted to start again!

I have installed 6.0.3 workstation and have ran the vmware-config.pl, yet every tme I try to run the vmware command it says I need to the the vmware-config.pl part **_again._** I have installed everything from G++, build essential and linux headers but it still wont work... does anyone have any idea what I might be doing wrong??

[http://premium1.uploadit.org/mentholist//config.png](http://premium1.uploadit.org/mentholist//config.png)

many thanks!!

Please do not start multiple threads on the same topic.  We just have to look at the first thread to see what has been done.

Multiple threads also lead to duplication of effort and confusion.

I am not sure about VMWare Workstation, I advise you use VMWare Server :

[http://register.vmware.com/content/download.html](http://register.vmware.com/content/download.html)

How to :

[http://howtoforge.com/installing-vmware-server-1.0.4-on-ubuntu-7.10](http://howtoforge.com/installing-vmware-server-1.0.4-on-ubuntu-7.10)

Note you need a patch, from here :

[http://communities.vmware.com/message/76957](http://communities.vmware.com/message/76957)

[http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz)

---

### Post by TpyKv on 2008-04-15
Thank you, I wanted to start another thread as no - one seemed to be looking at the other one & there was lots of information that was not relevant. Anyway cheers for moving. 

I just learnt the server is the free version... I want to be able to make my own virtual machines from CD - which you cannot do unless you have the workstation...

As it's already cost me $200 is there a way to get it working, or shall I ask for a refund?

---

### Post by hyper_ch on 2008-04-15
the howto is outdated. vmware-server is in the canonical partner repos... so very easy to install...

---

### Post by TpyKv on 2008-04-15
I have installed the server and it seems to be working!! and you can make an OS from the install disc....

time to get my dollars back from VMware!! 

this is great people, thanks for your support!!!

:KS

---

### Post by hyper_ch on 2008-04-15
> **TpyKv said:**
> time to get my dollars back from VMware!!
I guess that won't happen :(

---

### Post by dpj23 on 2008-04-16
install method I use:

1. download .tar file to desktop

2. then extract files to desktop

3. browse folder for install.sh

4. double click on it and select run in terminal

5. follow the prompts as it requests and you will complete the install without fail

** you will need to sudo

---

### Post by yeehi on 2008-04-17
If you install and run VMware onto the same machine, is the server as fast as the Workstation?

I read that there is a direct link to the display in the Workstation that makes for better performance... (Whether this is true, I don't know. I don't even know whether the performance is much better.)

---

### Post by TpyKv on 2008-04-19
thanks for that dpj23, but it's still having none of it :( I think it's sony syndrome, everything else now works on this laptop except that, but the server does everything I need so it's all good!!

I'm not sure about performance but I give the VM max memory and so far no problems..

---

