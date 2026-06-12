---
title: "juju deploy problem with multiple network in openstack"
date: 2017-12-31
forum: Ubuntu Cloud and Juju
---

### Post by gamamtz on 2017-12-31
Hi!:

I have problem to deploy a charm in openstack with multiple networks, when i run ```
juju deploy cs:apache2-22
``` the command executes well, but when i run ```
juju status
``` that give me the following error in message column: 

[HTML]failed to start machine 0 (cannot run instance: failed to run a server with nova.RunServerOpts{Name:"juju-$
2d7ec-prueba-0", FlavorId:"2", ImageId:"4e83fc0f-731d-4bb7-a085-9e7699f7d872", UserData:[]uint8{0x1f, 0x8b,............... 0x0, 0x0}, SecurityGroupNames:[]nova.SecurityGroupName{nova.SecurityGroupName{Name:"juju-3d1a4cc7-cef8-4
f47-84d0-e0dd2daf5fd0-5419b564-e482-4eb9-809b-2908ddb2d7ec"}, nova.SecurityGroupName{Name:"juju-3d1a4cc7-cef8-4f47-84d0-e0dd2daf5fd0-5419b564-e482-4eb9
-809b-2908ddb2d7ec-0"}}, Networks:[]nova.ServerNetworks{}, AvailabilityZone:"nova", Metadata:map[string]string{"juju-model-uuid":"5419b564-e482-4eb9-80
9b-2908ddb2d7ec", "juju-units-deployed":"apache2/0", "juju-controller-uuid":"3d1a4cc7-cef8-4f47-84d0-e0dd2daf5fd0", "juju-machine-id":"prueba-machine-0
"}, ConfigDrive:false}
caused by: request (http://10.1.1.249:8774/v2.1/9f0f4a543e8c4700916a2740f3891116/servers) returned unexpected status: 409; error info: {"conflictingReq
uest": {"message": "Multiple possible networks found, use a Network ID to be more specific.", "code": 409}}), retrying in 10s (10 more attempts)[/HTML]

I had a similar error when i tried to bootstrap the controller, i solved it with ```
--config network=b4928531-b907-41b1-9d50-da6126f42ed6
```, how i specify network id wit juju deploy command?

additional info:

juju version 2.3.1

openstack mitaka private cloud 

I really appreciate any help you can provide.

---

