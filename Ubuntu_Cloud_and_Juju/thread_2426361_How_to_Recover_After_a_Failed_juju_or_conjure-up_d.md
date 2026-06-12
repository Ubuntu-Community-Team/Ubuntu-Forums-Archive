---
title: "How to Recover After a Failed juju or conjure-up deploy"
date: 2019-09-07
forum: Ubuntu Cloud and Juju
---

### Post by db0west on 2019-09-07
Just tried to conjure-up Openstack NovaKVM and one box was not ready. So one box is listed as failed but the deployment is still waiting for it.

I am using MAAS.

I have the machine now in Ready status that should have the remaining deployment items which are still blocking other things.

Out of the 4 needed machines, labeled 0-3, 2 is the remaining machine that errored out before.

How do I retry machine 2. I am guessing if successful, my ready machine will move to allocated and then deploying in mass and in the Juju gui and with `juju status ` I will see the deployment resume.

Thanks!

---

### Post by db0west on 2019-09-07
I tried this as well.

[last: 0s][~]$ juju retry-provisioning 2 --debug
21:50:15 INFO  juju.cmd supercommand.go:57 running juju [2.6.8 gc go1.10.4]
21:50:15 DEBUG juju.cmd supercommand.go:58   args: []string{"/snap/juju/8873/bin/juju", "retry-provisioning", "2", "--debug"}
21:50:15 INFO  juju.juju api.go:67 connecting to API addresses: [192.168.0.131:17070]
21:50:15 DEBUG juju.api apiclient.go:1092 successfully dialed "wss://192.168.0.131:17070/model/37236835-d3b3-4b2b-8087-5f60789c1e21/api"
21:50:15 INFO  juju.api apiclient.go:624 connection established to "wss://192.168.0.131:17070/model/37236835-d3b3-4b2b-8087-5f60789c1e21/api"
21:50:15 DEBUG juju.api monitor.go:35 RPC connection died
21:50:15 INFO  cmd supercommand.go:502 command finished
[last: 0s][~]$ juju --version
2.6.8-bionic-amd64

---

### Post by digikin on 2020-02-07
What is the output of juju status?

---

### Post by msalmanmasood on 2020-12-31
In my case, juju status returns nothing while debug returns as:

 juju status --debug
07:14:47 INFO  juju.cmd supercommand.go:54 running juju [2.8.7 0 ee2cfeb2c8c716af763a011e184ddea879c0985d gc go1.14.13]
07:14:47 DEBUG juju.cmd supercommand.go:55   args: []string{"/snap/juju/14932/bin/juju", "status", "--debug"}
07:14:47 INFO  juju.juju api.go:67 connecting to API addresses: [10.101.52.4:17070]


Whereas, from the last successfully watch output of the juju status, couldn't find any service listening on 10.101.52.4

Now I would like to tear down the environment successfully incl maas-controller so advice pl.

Thanks.

---

