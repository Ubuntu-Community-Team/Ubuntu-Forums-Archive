---
title: "OpenCa Ubuntu Server"
date: 2007-07-09
forum: Server Platforms
---

### Post by Hugo Allamel on 2007-07-09
When I try to install openca, I have one error: the install.sh script is not
in the good folder (/OPENCA_INSTALL/src/scripts and /OPENCA_INSTALL/src/common/etc). After moving the install.sh script in this folders. I try to do(after doing configure & make):

$ make install-offline

and I get a new error:

cannot create directory /OPENCA_DIR/openca/etc/bp/ file exists
make [8]: *** [__install_dir] Error 1

Hope you can help me.
Thanks

---

