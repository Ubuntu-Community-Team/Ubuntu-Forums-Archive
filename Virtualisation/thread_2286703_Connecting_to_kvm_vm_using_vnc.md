---
title: "Connecting to kvm vm using vnc"
date: 2015-07-14
forum: Virtualisation
---

### Post by npinn001 on 2015-07-14
Just wondered, by default the virtual machines are set up with access via vnc which virt-manager connects up with, and once its up and running, is it possible to just connect up with a vnc viewer without doing anything additional? And how would you go about that?

Thanks

---

### Post by KillerKelvUK on 2015-07-14
Yes...the vnc server is running on the host as part of the qemu session...you can access this from any compliant viewer application, this applies to both vnc and spice.  Typically with a guest created from virt-manager the vnc server starts from port 5900 and each guest needs a port and so the number is just incremented i.e. your next guest will use port 5901 and so on.

So using your viewer of choice you can point it at the IP of your host and use the port that denotes the vm you wish to connect to.  I use the virt-viewer package which provides a binary called remote-viewer...using this the connection string would look something like this...

```

remote-viewer vnc://localhost:5900 or 
remote-viewer vnc://192.168.1.10:5900 (obviously adjust the IP accordingly if your using a remote connection)
EDIT:  make sure the IP is that of the host and not the guest...the server connection is host side.

```

remote-viewer also supports spice so you just alter the string replacing 'vnc' with 'spice' e.g. remote-viewer spice://x.x.x.x:5900.

Couple of things to note is that the vnc/spice server that is created can be configure to only allow connections from the host so you may need to adjust the config to allow connections in from your local network or from over your internet connection if you are so brave!  In addition you can manually set the port the vnc or spice session is to be created with for that vm i.e. always make the vm us port 5911, that way you have a fixed connection point...just ensure you don't set to vm's to use the same port.

---

### Post by npinn001 on 2015-07-14
> **KillerKelvUK said:**
> Yes...the vnc server is running on the host as part of the qemu session...you can access this from any compliant viewer application, this applies to both vnc and spice.  Typically with a guest created from virt-manager the vnc server starts from port 5900 and each guest needs a port and so the number is just incremented i.e. your next guest will use port 5901 and so on.

So using your viewer of choice you can point it at the IP of your host and use the port that denotes the vm you wish to connect to.  I use the virt-viewer package which provides a binary called remote-viewer...using this the connection string would look something like this...

```

remote-viewer vnc://localhost:5900 or 
remote-viewer vnc://192.168.1.10:5900 (obviously adjust the IP accordingly if your using a remote connection)
EDIT:  make sure the IP is that of the host and not the guest...the server connection is host side.

```

remote-viewer also supports spice so you just alter the string replacing 'vnc' with 'spice' e.g. remote-viewer spice://x.x.x.x:5900.

Couple of things to note is that the vnc/spice server that is created can be configure to only allow connections from the host so you may need to adjust the config to allow connections in from your local network or from over your internet connection if you are so brave!  In addition you can manually set the port the vnc or spice session is to be created with for that vm i.e. always make the vm us port 5911, that way you have a fixed connection point...just ensure you don't set to vm's to use the same port.

Thanks for that, thats really useful. I'll only open it up to local network so I'll check that out. Makes thing snice and easy!

---

