---
title: "How do I change my vm display from Spice server to VNC server on KVM? (virt-manager)"
date: 2017-02-28
forum: Virtualisation
---

### Post by fromwin2lin on 2017-02-28
I have several KVM virtual machines on a server (runs Ubuntu Server 16.10) hosted in another part of town. I access them using ssh on my laptop (Running Ubuntu Desktop 16.10) using virt-manager and the terminal. On one of the VMs I made the mistake of not changing the display setting from Spice server to VNC server. Now I am experiencing an issue where if I don't change the display setting from Spice sever to Display Server, I encounter a never-ending password-prompt loop. I have encountered this bug before. And the only way that I could fix it was to delete the VM and and start from scratch. This is not acceptable and I can't afford to do that. I know that virt-manager does not have a VM setting GUI like VMware or virtual box, instead you have to change system files. I have googled on which ones I have to changed and nothing has helped me. I need to know how to change the display setting to VNC server. Any help will be greatly appreciated for I am desperate to find an answer as soon as possible.

Thanks,

fromwin2lin

---

### Post by Doug S on 2017-03-01
Can you use "virsh edit" to edit the .xml definition file directly? I assume you would want to change the graphics and video sections to something like:```
    <graphics type='vnc' port='-1' autoport='yes' listen='0.0.0.0'>
      <listen type='address' address='0.0.0.0'/>
    </graphics>
    <video>
      <model type='vmvga' vram='16384' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>

```See also [here]("http://askubuntu.com/questions/610501/terminal-unusable-in-virtual-machine/610509#610509")

---

