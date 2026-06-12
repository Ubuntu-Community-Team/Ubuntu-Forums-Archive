---
title: "Writting myVirt"
date: 2011-07-02
forum: Virtualisation
---

### Post by nMehrabi on 2011-07-02
Dear all, 
I'm new in libvirt. I would be glad if you help me.
 

[FONT=Calibri]I want to write a program for controlling all libvirt servers named "MYVIRT". [/FONT]
  [FONT=Calibri]The libvirtd works as fallow:[/FONT]
  [FONT=Calibri]{ CLIENT }  ---------------------> { SERVER A }[/FONT]
  [FONT=Calibri]       |[/FONT]
  [FONT=Calibri]       |[/FONT]
  [FONT=Calibri]       ------------------------------> { SERVER B }[/FONT]
  
  [FONT=Calibri]Now, I want to place MYVIRT between client and libvirtd servers. By calling a command, MYVIRT should execute the command for all servers.[/FONT]
  
  
  [FONT=Calibri]{ CLIENT }[/FONT]
  [FONT=Calibri]       |[/FONT]
  [FONT=Calibri]       |[/FONT]
  [FONT=Calibri]{ MYVIRT }  ---------------------> { SERVER A }[/FONT]
  [FONT=Calibri]       |[/FONT]
  [FONT=Calibri]       |[/FONT]
  [FONT=Calibri]       ------------------------------> { SERVER B }[/FONT]
  
  [FONT=Calibri]The client softwares for libvirtd are virsh and virt-manager. Now I want them to connect to MYVIRT and look it as a libvirtd server.[/FONT]
  
  [FONT=Calibri]Would you please guide me for connecting to MYVIRT through virsh and execute a command on all servers?[/FONT]

---

