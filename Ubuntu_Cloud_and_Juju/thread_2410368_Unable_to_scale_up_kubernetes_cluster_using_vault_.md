---
title: "Unable to scale up kubernetes cluster using vault overlay"
date: 2019-01-14
forum: Ubuntu Cloud and Juju
---

### Post by extulsan on 2019-01-14
I'm having a problem scaling up our canonical-kubernetes cluster which uses the Vault overlay described here:
[https://github.com/juju-solutions/bundle-canonical-kubernetes/wiki/CDK-Certificates-and-Trust-Management](https://github.com/juju-solutions/bundle-canonical-kubernetes/wiki/CDK-Certificates-and-Trust-Management)

Initially, scaling up worked fine. After a few days, we're no longer able to add workers via the **juju** **add-unit kubernetes-worker **command. After adding a new worker, we see that the worker's status is: *Waiting for kube-proxy to start***,** and that the new worker is missing certificates in the /root/cdk folder.

juju debug-log --replay --level ERROR shows this:

unit-vault-0: 02:50:34 ERROR unit.vault/0.juju-log certificates:13: cannot satisfy request, as TTL would result in notAfter 2019-02-11T02:50:34.09260315Z that is beyond the expiration of the CA certificate at 2019-02-08T16:55:12Z


My initial attempt to resolve this was to try tuning the secrets after the deployment is active:

VAULT_TOKEN={token } vault secrets tune -max-lease-ttl=87600h charm-pki-local/
VAULT_TOKEN={token} vault secrets tune -default-lease-ttl=87600h charm-pki-local/

But this did not help. Does anyone have any clues about how I could resolve this?

I've also documented this in the github repo here:
[https://github.com/juju-solutions/bundle-canonical-kubernetes/issues/719](https://github.com/juju-solutions/bundle-canonical-kubernetes/issues/719)

---

