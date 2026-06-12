---
title: "Landscape Error Openstack"
date: 2016-03-30
forum: Ubuntu Cloud and Juju
---

### Post by corbetrobin94 on 2016-03-30
Hello,

I try to deploy OpenStack with Maas and Landscape and I have the same error every time. The comission work great but not the Deployment. In the first time I got somme Python error (due to hard link protection) but I solved this one. But after a bunch of attempt I keep having the same error message.

**_Error log (Landscape Web UI) :_**
```
juju ended with exit code 1 (out='', err='Bootstrapping environment "20"
Starting new instance for initial state server
Launching instance
 - /MAAS/api/1.0/nodes/node-ccfa4ba4-ecec-11e5-98c3-00505637e44a/
ERROR failed to bootstrap environment: bootstrap instance started but did not change to Deployed state: instance "/MAAS/api/1.0/nodes/node-ccfa4ba4-ecec-11e5-98c3-00505637e44a/" is started but not deployed
')
```

**_MAAS recent log :_**
```

Mar 30 09:40:26 maas maas.bootresources: [INFO] Started importing of boot images from 1 source(s).
Mar 30 09:40:30 maas maas.bootresources: [INFO] Importing images from source: http://maas.ubuntu.com/images/ephemeral-v2/releases/
Mar 30 09:40:34 maas maas.bootresources: [INFO] Finished importing of boot images from 1 source(s).
Mar 30 09:40:35 maas maas.import-images: [INFO] Started importing boot images.
Mar 30 09:40:35 maas maas.import-images: [INFO] Finished importing boot images, the region does not have any new images.



```

---

