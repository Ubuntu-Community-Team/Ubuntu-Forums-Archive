---
title: "Ubuntu Jaunty Host -&gt; Vbox 3.02 -&gt; Win 7 Guest File Sharing"
date: 2009-08-02
forum: Virtualisation
---

### Post by rlj1965 on 2009-08-02
I am running Ubuntu Jaunty with virtualbox 3.02 and Windows 7 as guest OS. I currently have two VM's... 1) Win XP, 2) Win 7.

The problem is with sharing files from the host Ubuntu machine with Win 7. All shares are setup correctly in Virtualbox. I have Internet connection in the Win 7 machine, but cannot seem to see the files that I want to share from the host machine. I have tried mapping a drive via the network and sharing center and used the correct path, but win 7 just times out when looking for the shares. 

I do not have this problem when using the XP virtual machine at all.

Can anyone help me to see my shares in the Win 7 virtual machine. I want to be able to see my movies, music and documents.

:confused:

Thanks in advance.

RJ

---

### Post by jocampo on 2009-08-02
> **rlj1965 said:**
> I am running Ubuntu Jaunty with virtualbox 3.02 and Windows 7 as guest OS. I currently have two VM's... 1) Win XP, 2) Win 7.

The problem is with sharing files from the host Ubuntu machine with Win 7. All shares are setup correctly in Virtualbox. I have Internet connection in the Win 7 machine, but cannot seem to see the files that I want to share from the host machine. I have tried mapping a drive via the network and sharing center and used the correct path, but win 7 just times out when looking for the shares. 

I do not have this problem when using the XP virtual machine at all.

Can anyone help me to see my shares in the Win 7 virtual machine. I want to be able to see my movies, music and documents.

:confused:

Thanks in advance.

RJ

Just a very basic suggestion (could not help, could help) ... check network connectivity using basic tools like ping. See if you can reach both machines and resolve names from both sides. And finally, check if you are using a firewall; sometimes firewalls blocks certain ports needed for file sharing.

---

