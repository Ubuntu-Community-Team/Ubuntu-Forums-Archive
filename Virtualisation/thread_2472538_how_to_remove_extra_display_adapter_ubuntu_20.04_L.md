---
title: "how to remove extra display adapter ubuntu 20.04 LTS"
date: 2022-03-02
forum: Virtualisation
---

### Post by noisea on 2022-03-02
[FONT=&amp]I am trying to troubleshoot why I can't get Quick Sync to work for Plex in a VM. I believe I have correctly passed through the iGPU from the Host to the VM and I believe I have the correct driver (i915)[/FONT]
[FONT=&amp]The CPU is an i5-10400[/FONT]
[FONT=&amp]I think the problem is that there are 2 display adapters on the VM. I think that because[/FONT]
[FONT=&amp]```
sudo lshw -c video
```[/FONT]
[FONT=&amp]gives me this:[/FONT]
```
*-display
[FONT=&amp]description: VGA compatible controller[/FONT]
[FONT=&amp]product: SVGA II Adapter[/FONT]
[FONT=&amp]vendor: VMware[/FONT]
[FONT=&amp]physical id: f[/FONT]
[FONT=&amp]bus info: pci@0000:00:0f.0[/FONT]
[FONT=&amp]version: 00[/FONT]
[FONT=&amp]width: 32 bits[/FONT]
[FONT=&amp]clock: 33MHz[/FONT]
[FONT=&amp]capabilities: vga_controller bus_master cap_list rom[/FONT]
[FONT=&amp]configuration: driver=vmwgfx latency=64[/FONT]
[FONT=&amp]resources: irq:16 ioport:1070(size=16) memory:e8000000-efffffff memory:fe000000-fe7fffff memory:c0000-dffff[/FONT]
[FONT=&amp]*-display[/FONT]
[FONT=&amp]description: VGA compatible controller[/FONT]
[FONT=&amp]product: Intel Corporation[/FONT]
[FONT=&amp]vendor: Intel Corporation[/FONT]
[FONT=&amp]physical id: 0[/FONT]
[FONT=&amp]bus info: pci@0000:0b:00.0[/FONT]
[FONT=&amp]version: 03[/FONT]
[FONT=&amp]width: 64 bits[/FONT]
[FONT=&amp]clock: 33MHz[/FONT]
[FONT=&amp]capabilities: pciexpress msi pm vga_controller bus_master cap_list[/FONT]
[FONT=&amp]configuration: driver=i915 latency=64[/FONT]
[FONT=&amp]resources: irq:62 memory:fc000000-fcffffff memory:d0000000-dfffffff ioport:5000(size=64)[/FONT]
```[FONT=&amp]

[/FONT]
[FONT=&amp]I don't know if that is my problem but it seems like I would only want to have 1 and for it to be the intel with the i915 driver - right? If I am wrong on that then please correct me.[/FONT]
[FONT=&amp]How can I fix this if it is the problem? I am new to linux and I have been struggling to find the correct search terms to find out how to correct this.[/FONT]

---

### Post by QIII on 2022-03-02
Moved to Virtualisation

---

### Post by CharlesA on 2022-03-03
Are you using KVM or LXC for your plex server?

---

