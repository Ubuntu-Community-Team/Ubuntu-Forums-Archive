---
title: "Hardy Performance on Hardy VMware Server host"
date: 2008-06-13
forum: Virtualisation
---

### Post by Cubus on 2008-06-13
I set up a Hardy Heron Server to virtualize 2 of our servers, installes our webserver-replacement first, now I'm shocked by the bad performance.

Our current webserver is a Windows XP machine running apache 1.3 using PHP/MSSQL on a 2GHZ Athlon with 512MB Ram

The new one is a Hardy Heron with Apache 2.2 PHP/MSSQL-by-Sybase-library on the Hardy Host wich is an Athlon 3.2GHZ with 1GB Ram, 512 of the RAM are dedicated to the VM.

I didnt install the 2nd VM wich is supposed to run on the same hardware yet.

Now, if I pick one of the web-pages wich has quite some DB activity it takes about 2 seconds to load from the Windows/Apache but a little more than 3 seconds from the Linux/Apache.

Now, I'd like to know, is there a general performace-problem with the Linux/PHP/MSSQL library or are the chances better that the error is caused by something else (eg. virtualization)?

Oh, ofc I installed the VMWareTools.

The system is fresh install with only LAMP, Samba and OpenSSH installed.

Any ideas?

Thanks in advance!

---

### Post by robgolding63 on 2008-06-13
RAM is lacking a bit on that host - it's probably paging which is why you're seeing the poor performance.

Run **top**, and see how much swap space is being used. If you want to run 2 VMs on that host you'll need at least another gig of RAM.

Hope this helps,

Rob

---

### Post by Cubus on 2008-06-14
Actually the performance issue is a mix of both, the virtualization and the FreeTDS library.

I installed a native linux box with the same config and ran the website on it, with many queries the linux box is way slower than the windows box: Win/Apache 2 seconds -> Linux/Apache 6 seconds for the same page.

So, this is quite sad for me, I'll have to stick with the wndows webserver :(

---

### Post by fewt on 2008-06-14
> **Cubus said:**
> I set up a Hardy Heron Server to virtualize 2 of our servers, installes our webserver-replacement first, now I'm shocked by the bad performance.

Our current webserver is a Windows XP machine running apache 1.3 using PHP/MSSQL on a 2GHZ Athlon with 512MB Ram

The new one is a Hardy Heron with Apache 2.2 PHP/MSSQL-by-Sybase-library on the Hardy Host wich is an Athlon 3.2GHZ with 1GB Ram, 512 of the RAM are dedicated to the VM.

I didnt install the 2nd VM wich is supposed to run on the same hardware yet.

Now, if I pick one of the web-pages wich has quite some DB activity it takes about 2 seconds to load from the Windows/Apache but a little more than 3 seconds from the Linux/Apache.

Now, I'd like to know, is there a general performace-problem with the Linux/PHP/MSSQL library or are the chances better that the error is caused by something else (eg. virtualization)?

Oh, ofc I installed the VMWareTools.

The system is fresh install with only LAMP, Samba and OpenSSH installed.

Any ideas?

Thanks in advance!

Some tuning advice:
[http://www.fewt.com/2008/06/performance-tuning-vmware-server-on.html](http://www.fewt.com/2008/06/performance-tuning-vmware-server-on.html)

Don't ever give your VMs more memory than they actually need.  Typically, you can give a Windows server VM 192MB (base) and then add to it the amount of memory you need to support your app.

See the how-to above for more tuning advice.

---

