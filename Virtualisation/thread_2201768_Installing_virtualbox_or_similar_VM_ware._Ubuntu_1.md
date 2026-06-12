---
title: "Installing virtualbox or similar VM ware. Ubuntu 12.04"
date: 2014-01-25
forum: Virtualisation
---

### Post by thault on 2014-01-25
I have a server with the Ubuntu 12.04 and I would like to set up virtual machines that my roommate and I could access. How do I go about installing VirtualBox, or similar VM ware that you would suggest. All the guides I found online seemed a little dated.

---

### Post by QIII on 2014-01-25
Hello!

You will find VirtualBox [here]("https://www.virtualbox.org/wiki/Downloads").  Download the package and install using the instructions [here.]("https://www.virtualbox.org/wiki/Linux_Downloads")  Also install the Extension pack.

When the virtual machine is set up and running, install the Guest Additions.

Does your server have a GUI?  Setting up the machine is fairly simple using the GUI.

We're here if you need any further help.

Best wishes.

---

### Post by thault on 2014-01-26
I've been using command line. Trying to force myself to learn that. So if you have any links on configuring that would help, but I do have webmin installed.

---

### Post by QIII on 2014-01-26
The best documentation is right there on the virtualbox.org website.  [This]("https://www.virtualbox.org/manual/ch08.html") has all the info you will need for the command-line interface.

---

### Post by Bucky Ball on 2014-01-26
Why not install Virtualbox from the Software Centre/Synaptics?

---

### Post by TheFu on 2014-01-26
If you are not running a desktop distro and do not have a GUI, perhaps using something other than virtualbox would be a better choice?
Virtualbox is really for desktop-on-desktop virtualization, IMHO. VBox has locked up my machines - not just the VMs.  Those same machines have been running KVM non-stop 24/7/366 for 2+ yrs.  If you are going to be doing server-on-server virtualization, then there are better virtual machine technologies like KVM, Xen, and a few others.  I love that KVM using libvirt and virt-manager lets me control the hold infrastructure from any Linux GUI client machine anywhere, securely.

With virtualbox, you _can_ manage the machines from the CLI using VBoxManage. The man page and online documentation for it is extensive.

---

