---
title: "Problem starting up windows Virtualization."
date: 2007-12-14
forum: Virtualisation
---

### Post by Valok on 2007-12-14
So I followed this guide: [http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu](http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu) to the T and get the following error message when I try to power on my virtual machine 

"Unable to change virtual machine power state: The process exited with an error: End of error message."

Im not really sure what this means, or how to go about fixing it.  Please advise.

---

### Post by Valok on 2007-12-14
Here is a more detailed error message.


"Unable to change virtual machine power state: The process exited with an error:
vmxvmdb: Index name being generated from config file
POST(no connection): Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.

POST(no connection): Failed to initialize monitor device.

Failed to initialize VM.
End of error message."

Also I am attempting to use VMware

---

### Post by Valok on 2007-12-15
Still haven't been able to figure this one out.

---

### Post by Valok on 2007-12-16
Back from a weekend vacation and still looking for tips on this problem.

---

### Post by Valok on 2007-12-21
Still looking for advice.

---

### Post by SRP on 2007-12-21
What version of VMware Server are you using?  Any chance you can upgrade to possibly the Beta 2.0? 

I also found this...

If you used the tar installer, did you run vmware-install.pl and did it complete successfully? If you are not sure that it did, you can run it again. The procedure is on this page, step 3e.

[http://pubs.vmware.com/server1/admin/install_server.3.18.html#1027718](http://pubs.vmware.com/server1/admin/install_server.3.18.html#1027718)

---

