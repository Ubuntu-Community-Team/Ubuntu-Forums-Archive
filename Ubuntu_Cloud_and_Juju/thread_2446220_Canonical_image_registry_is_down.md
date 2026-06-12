---
title: "Canonical image registry is down"
date: 2020-06-26
forum: Ubuntu Cloud and Juju
---

### Post by anantadwi13 on 2020-06-26
Hello guys,

i have just deployed my charmed kubernetes with juju + maas. all nodes are doing well except kubernetes-master node. the status message said "Waiting for 1 kube-system pod to start". so i check kube-system pods by using kubectl command and it showed me that 1 pod is not running. i tried to check it now using this command ```
kubectl describe pod/metrics-server-v0.3.6-74c87686d-9dmtr
``` On the events sections it stucked on pulling image "rocks.canonical.com:443/cdk/metrics-server-amd64:v0.3.6". i do log in to this kubernetes worker node and find out that it failed to download that image.

```
Jun 26 16:31:04 2 dockerd[2675]: time="2020-06-26T16:31:04.750293966Z" level=error msg="Download failed, retrying: unexpected EOF"
Jun 26 16:31:07 2 dockerd[2675]: time="2020-06-26T16:31:07.240452264Z" level=error msg="Download failed, retrying: unexpected EOF"
Jun 26 16:31:47 2 dockerd[2675]: time="2020-06-26T16:31:47.867239216Z" level=error msg="Download failed, retrying: unexpected EOF"

```

then i try to ping and wget to rocks.canonical.com. but there is no response. so is it just me getting this?

---

