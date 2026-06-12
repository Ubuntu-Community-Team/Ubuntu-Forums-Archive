---
title: "Driver HP ML115 G5"
date: 2010-03-27
forum: Server Platforms
---

### Post by Tres_Iqus on 2010-03-27
ubuntu server 64bit and installed in a HP ML115 G5 and these 2 drivers detects and I do not know where I can download these

00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)

10:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G200e [Pilot] ServerEngines (SEP1) (rev 02)

---

### Post by spynappels on 2010-03-27
I'm sorry, but can you explain what the problem is a little more clearly?

Is not all your memory being recognised? Is the video driver not working in that you are not able to see the login prompt when initialisation has finished?

I have worked with both the ML110 G5 and the ML115 G5 and neither have ever given me any problem with any Ubuntu Server flavour.

---

### Post by Tres_Iqus on 2010-03-27
what happens is that these devices have not been claimed, this is the lshw command output

*-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP55 Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0

*-display UNCLAIMED
             description: VGA compatible controller
             product: MGA G200e [Pilot] ServerEngines (SEP1)
             vendor: Matrox Graphics, Inc.
             physical id: 0
             bus info: pci@0000:10:00.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list
             configuration: latency=0

I care more than the ram driver to work properly, the appropriate use of this

---

### Post by Tres_Iqus on 2010-03-29
need install MCP55 ram controller

---

