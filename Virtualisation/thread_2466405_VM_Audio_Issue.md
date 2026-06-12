---
title: "VM Audio Issue"
date: 2021-08-27
forum: Virtualisation
---

### Post by vmburner2000 on 2021-08-27
The way I'm setting up my vm is I'm passing through my graphics card so that my main output is through my cpu's dedicated graphics. After I isolate the GPU my pc acts all glitchy in that the audio stuffs up, so say if I watch a video random sounds from the video play randomly. Oddly enough if I take out the graphics card and use my pc without it this issue isn't present. I couldn't find anyone else posting about this issue. Thanks in advance.

---

### Post by TheFu on 2021-08-27
Most GPUs used for passthru would have audio processing built-into them.
Most motherboards have audio processing built-into them.

You've probably already checked, but ensure that the hostOS uses the MB audio - always
and the VM getting the GPU for exclusive use chooses to use the GPU audio - always.

How all this is done will be highly dependent on the hypervisor, but inside the guest VM, the trick would be use use the correct audio source and sink.  Use pavucontrol to disable the hardware that will be passed VM-hypervisor created.

---

