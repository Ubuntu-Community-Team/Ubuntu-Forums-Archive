---
title: "Server does not start, I did not install cloud service"
date: 2012-04-01
forum: Server Platforms
---

### Post by deepakdeshp on 2012-04-01
The Ubuntu 10.04 server does not start and I am getting timeout error I have not added any cloud services etc.

*The error is** Cloud-init is running . Waiting for metadata services at [http://169.254.169.254/2009-04-04/metadata/instance](http://169.254.169.254/2009-04-04/metadata/instance) id ***.

The boot log is

fsck from util-linux-ng 2.17.2
/dev/sda11: clean, 115767/580496 files, 1432049/2304000 blocks
init: Failed to spawn cloud-init main process: unable to execute: No such file or directory^M
mountall: Event failed
init: Failed to spawn cloud-config-ssh main process: unable to execute: No such file or directory^M
init: Failed to spawn cloud-config-mounts main process: unable to execute: No such file or directory^M
init: Failed to spawn cloud-disable-ec2-metadata main process: unable to execute: No such file or directory^M
init: Failed to spawn cloud-apt-update-upgrade main process: unable to execute: No such file or directory^M
init: Failed to spawn cloud-config-misc main process: unable to execute: No such file or directory^M
init: Failed to spawn cloud-config-puppet main process: unable to execute: No such file or directory^M
 * Starting domain name service... bind9       ^[[170G ^M^[[164G[ OK ]
 * Starting DenyHosts denyhosts       ^[[170G ^M^[[164G[ OK ]
 * Starting No-IP.com dynamic address update noip2       ^[[170G ^M^[[164G[ OK ]
 * Starting the Winbind daemon winbind       ^[[170G ^M^[[164G[ OK ]
 * Starting web server apache2       ^[[170G ^M^[[164G[ OK ]

---

### Post by deepakdeshp on 2012-04-02
I had run apt-get update and upgrade . This created the problem. I found the files in the cloud-init package , and renamed the config file so that the cloud initialization failed. Thus I was at least able to boot the server which wasnt possible after the upgrade.

This is a major bug as the serverUbuntu 10.04 server  doesnt boot after the upgrade.

---

