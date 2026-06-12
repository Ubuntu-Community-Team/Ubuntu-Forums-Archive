---
title: "Error installing Adobe CS3 in VirtualBox :: Ubuntu 7.10, Gutsy"
date: 2007-10-23
forum: Virtualisation
---

### Post by Ralphie on 2007-10-23
This was originally a question, but I have found the answer, thanks to 
Ubuntu user "jespdj".

You can get <CS3 to install on Ubuntu through [VirtualBox]("http://www.virtualbox.org/") running Windows XP with Service Pack 2 installed.

While setting up VirtualBox, set your Base Memory size to something greater than 512MB, I currently have mine set to 1000MB.

After you are finished with the main VirtualBox set up, You should then select your new VM, and click Settings, under General>Basic, set "Video Memory Size" to something larger than 64MB, Mine is set to 90MB.  
Run your VM, and Install XP, and sp2. Next install "Guest Additions" you can do this in Windows, by going to "My Computer" and mounted there as a CD drive should be "Guest Additions" double click and install. This allows you to run windows in a much more natural and stemless way. 
Restart.

Now you should be ready to install <CS3 without a hitch!

This is an old screen shot of my CS3 running under Ubuntu 7.04 / VirtualBox 1.5.0, on a dual head setup, But it runs exactly the same in 7.10 / VB 1.5.2 --
[URL="http://realityhiphop.net/hostedfiles/ubuntu_running_cs3_virtualbox_dual_head.png"][IMG]http://realityhiphop.net/hostedfiles/ubuntu_running_cs3_virtualbox_dual_head_sm.png[/IMG]
[click for full image][/URL]

---

