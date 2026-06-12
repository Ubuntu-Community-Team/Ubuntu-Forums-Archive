---
title: "Wine+CM 03/04 won't start"
date: 2009-10-15
forum: Wine
---

### Post by jackietreehorn on 2009-10-15
I have an old copy of championship manager 03/04 (precursor to Football Manager)[http://en.wikipedia.org/wiki/Championship_Manager_03/04]("http://en.wikipedia.org/wiki/Championship_Mnager_03/04") and the program installs perfectly. However, when I try to run the program from the cli I get an error. A dialog box pops up and says "no disc inserted". 

Here's the output from the cli:

```

err:aspi:SCSI_OpenDevice Failed to open device /dev/hda: Permission denied
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
err:aspi:SCSI_OpenDevice Failed to open device /dev/hdc: No medium found
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 2.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg0: No such file or directory

```

Not sure what the problem is, any help would be appreciated.

---

### Post by asdfoo on 2009-10-16
> **jackietreehorn said:**
> I have an old copy of championship manager 03/04 (precursor to Football Manager)[http://en.wikipedia.org/wiki/Championship_Manager_03/04]("http://en.wikipedia.org/wiki/Championship_Mnager_03/04") and the program installs perfectly. However, when I try to run the program from the cli I get an error. A dialog box pops up and says "no disc inserted". 

Here's the output from the cli:

```

err:aspi:SCSI_OpenDevice Failed to open device /dev/hda: Permission denied
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
err:aspi:SCSI_OpenDevice Failed to open device /dev/hdc: No medium found
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 2.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg0: No such file or directory

```

Not sure what the problem is, any help would be appreciated.

copy protection maybe?   a crack might help

---

### Post by aoanla on 2009-10-16
Yeah, it looks like a copy-protection cd-check which is failing. 
I know there's some work going on with getting cd access working in OSX, but I doubt that's your problem.

No-cd crack will probably fix it, though.

---

