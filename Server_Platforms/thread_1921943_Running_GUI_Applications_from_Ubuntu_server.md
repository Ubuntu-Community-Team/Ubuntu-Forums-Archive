---
title: "Running GUI Applications from Ubuntu server"
date: 2012-02-07
forum: Server Platforms
---

### Post by onlinegeek on 2012-02-07
I like the bash interface of the server edition of Ubuntu. I was wondering if there was any way i can just install that edition and via terminal run gui based applications, ei. A web browser or such. Also would it be possible to run VMPlayer from terminal without having the desktop environment installed.

---

### Post by volkswagner on 2012-02-07
If your hardware supports VirtualMachines, I suggest don't install desktop environment.

Check out the server sticky at the top of this thread for [virtualization]("https://help.ubuntu.com/10.04/serverguide/C/virtualization.html").

You may also be interested in running VirtualBox headless [how-to]("http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.0-on-a-headless-ubuntu-11.04-server") or look into KVM headless [how-to]("http://www.howtoforge.com/installing-kvm-guests-with-virt-install-on-ubuntu-11.04-server").

What are your hardware specs, particularly RAM and CPU?

---

### Post by SeijiSensei on 2012-02-07
Another option is to install just xserver-xorg and its dependencies.  Then you can connect using "ssh -X" and run X applications on the server but display them on your local desktop.  Typing "firefox &" in this arrangement will run Firefox on the remote server but display the browser on the client's screen.

---

