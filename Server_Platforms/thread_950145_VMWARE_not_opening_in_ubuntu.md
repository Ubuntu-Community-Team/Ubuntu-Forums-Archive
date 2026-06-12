---
title: "VMWARE not opening in ubuntu"
date: 2008-10-16
forum: Server Platforms
---

### Post by gobicse on 2008-10-16
I just installed vmware server 2.0, after it was successfully configured with default settings, I ran vmware from terminal and saw this on terminal:
Code:

[Launching VMware Web Access using /usr/bin/xdg-open

and then my firefox was activated trying to connect to 127.0.0.1:8333 and got this

[Secure Connection Failed

127.0.0.1:8333 uses an invalid security certificate.

The certificate is not trusted because it is self signed.
The certificate is only valid for gobinath-laptop

(Error code: sec_error_ca_cert_invalid)]

---

### Post by tuxxy on 2008-10-16
Have you looked at virtualbox 2.0.2 its much easier to setup and configure.

---

### Post by lykwydchykyn on 2008-10-16
self-signed certificates always cause browser errors like that, it's a security measure.  You should have an option to add an exception, do you not?

---

### Post by snowstorm167 on 2008-10-17
I got same thing with my vmware but i was able to add it to safe list

now I can not get past the finding the addy peice because because it says my java is not installed 


i also have a prob with my firefox being said it not firefox


my system is 8.04 lts server edition x64

---

### Post by lapishc on 2008-10-29
I am having the same issue with VMware. Did you resolve it by chance?

---

### Post by shooter902 on 2008-10-30
Sorry to hijack this, but I am having the same issue with 8.04. I do not have an option to add an exception. However, I went into Firefox / Edit /Preferences /Security /Exceptions and added:

[https://127.0.0.1:8333/](https://127.0.0.1:8333/)

With no success. Any ideas?

Thanks

---

### Post by slick666 on 2008-11-02
lol, Same here too guys.

I installed VMware 2.0 on my 8.10, 64-bit, headless Server. When I try to address it I receive the warning from Firefox when I try to log in from another machine but I add an exception. The page however still does not load.

I've reconfigured the System and found that the administrator was still ''. I've reconfigured it now four or five times and I still get the same from the config script. I suspect my issue is that no one is set as the administrator so that is why the VMware administration page will not load.

Anyone else having this issue in this thread?

---

### Post by toasterboy1 on 2009-01-28
I am also unable to connect with firefox to vmware using the secure connection. However I can connect with [http://localhost:8222](http://localhost:8222). Hope that helps.

---

### Post by parameter on 2009-01-28
> **gobicse said:**
> and then my firefox was activated trying to connect to 127.0.0.1:8333 and got this

[Secure Connection Failed

127.0.0.1:8333 uses an invalid security certificate.

The certificate is not trusted because it is self signed.
The certificate is only valid for gobinath-laptop

(Error code: sec_error_ca_cert_invalid)]

This message is from Firefox, not VMware.  The bottom of this warning should have a link that says "Or you can add an exception…"

1. Click on that and two buttons will appear.  One will say "Get me out of here" and the other will say "Add Exception".  Click on the Add Exception button.

2. The "Add Security Exception" window will appear and the field at the top will be populated with the URL you went to.  

3. Click on the "Get Certificate" button.

4. Ensure that the "Permanently Store This Exception" checkbox at the bottom of the window is checked.

5. Click "Confirm Security Exception".

The page should now reload and you will not be warned about the error.

---

### Post by windependence on 2009-01-29
Parameter is correct on this. Add the exception. Also, you do NOT need java in any way shape or form for VMware.

You all should use VMware ESXi instead of VMware server unless you are planning to work on the host box which is not recommended. ESXi only has a 30 MB footprint and does NOT require a host OS. ESXi is the host OS, and you run your guests on top of it. Much better resource utilization and faster performance. You cannot, however, administer ESXi from the host box. You do it from another box on the network.

As to Virtual Box bein easier, well YMMV. Virtual box also does not support the number of guest OSs that VMware does, and the VMware network options are much more feature rich.

-Tim

---

### Post by danpre on 2009-04-07
> **windependence said:**
> Parameter is correct on this. Add the exception. Also, you do NOT need java in any way shape or form for VMware.

You all should use VMware ESXi instead of VMware server unless you are planning to work on the host box which is not recommended. ESXi only has a 30 MB footprint and does NOT require a host OS. ESXi is the host OS, and you run your guests on top of it. Much better resource utilization and faster performance. You cannot, however, administer ESXi from the host box. You do it from another box on the network.

As to Virtual Box bein easier, well YMMV. Virtual box also does not support the number of guest OSs that VMware does, and the VMware network options are much more feature rich.

-Tim

Well you should know that ESXi doesn't recognize additional SATA disks.
VMware server does.

DANIeL

---

