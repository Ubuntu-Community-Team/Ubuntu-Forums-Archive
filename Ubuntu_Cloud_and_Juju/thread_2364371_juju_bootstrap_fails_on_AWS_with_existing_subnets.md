---
title: "juju bootstrap fails on AWS with existing subnets"
date: 2017-06-22
forum: Ubuntu Cloud and Juju
---

### Post by mfraenkel on 2017-06-22
In my environment I have 4 VPCs, 1 default and 17 defined subnets. I already figured out how to use the --to option to get past my first hurdle to install the controller in the proper subnet.
I am now hitting a second issue which I have not been able to work around. The error I get during bootstrap is:

```

ERROR fetching hosted model spaces: adding subnet "10.0.1.0/24": subnet "10.0.1.0/24" already exists
2017-06-22 13:02:36 DEBUG cmd supercommand.go:459 error stack: 
github.com/juju/juju/state/subnets.go:222: subnet "10.0.1.0/24" already exists
github.com/juju/juju/state/subnets.go:235: 
github.com/juju/juju/state/subnets.go:235: adding subnet "10.0.1.0/24"
github.com/juju/juju/state/spacesdiscovery.go:78: 
github.com/juju/juju/state/spacesdiscovery.go:51: 
github.com/juju/juju/agent/agentbootstrap/bootstrap.go:221: fetching hosted model spaces
github.com/juju/juju/cmd/jujud/agent/agent.go:102: 
2017-06-22 13:02:36 DEBUG juju.cmd.jujud main.go:186 jujud complete, code 0, err <nil>

```

10.0.1.0/24 is a subnet that is already defined in AWS and associated with another VPC.

---

