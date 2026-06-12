---
title: "Installing Dell firmware updates on Ubuntu Server"
date: 2007-04-11
forum: Server Platforms
---

### Post by inphektion on 2007-04-11
I have a Dell PE 1950 server.  I need to install their firmware update for the ESM found here: [http://ftp.us.dell.com/esm/ESM_FRMW_LX_R149885.BIN](http://ftp.us.dell.com/esm/ESM_FRMW_LX_R149885.BIN)
However when I try running this .bin I get a bunch of lines like this:
./ESM_FRMW_LX_R149885.BIN: 33: typeset: not found
./ESM_FRMW_LX_R149885.BIN: 34: typeset: not found
./ESM_FRMW_LX_R149885.BIN: 37: typeset: not found

Now this .bin said it was for red hat but it worked on fedora and they don't offer one for debian or ubuntu.  I also don't see a floppy image for this like I do for the bios update so I assume I can do the bios via bootable floppy.  

Anyone have ideas how I can get this update on there?  I can't be the only one with a dell server and ubuntu server.  My ubuntu is edgy eft.

---

### Post by inphektion on 2007-04-11
I still don't have a solution but so far I've installed the Dell OMSA 5.1 from the package referenced here:
[http://linux.dell.com/debian_9g.shtml](http://linux.dell.com/debian_9g.shtml)
 
since i read it might need that.  Still get the typeset not found messages.  I vi'd the .bin file and changed the #!/bin/sh to #!/bin/bash to see if that helped. The output looks a little different but still:

/tmp/ESM_FRMW_LX_R149885.BIN-13118-7422/spsetup.sh: 97: typeset: not found
/tmp/ESM_FRMW_LX_R149885.BIN-13118-7422/spsetup.sh: 98: typeset: not found
/tmp/ESM_FRMW_LX_R149885.BIN-13118-7422/spsetup.sh: 99: typeset: not found
/tmp/ESM_FRMW_LX_R149885.BIN-13118-7422/spsetup.sh: 100: typeset: not found
/tmp/ESM_FRMW_LX_R149885.BIN-13118-7422/spsetup.sh: 101: typeset: not found
/tmp/ESM_FRMW_LX_R149885.BIN-13118-7422/spsetup.sh: 102: typeset: not found
/tmp/ESM_FRMW_LX_R149885.BIN-13118-7422/spsetup.sh: 103: typeset: not found

anyone know what's going on here?

---

