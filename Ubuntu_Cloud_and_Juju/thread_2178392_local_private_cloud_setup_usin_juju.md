---
title: "local private cloud setup usin juju"
date: 2013-10-03
forum: Ubuntu Cloud and Juju
---

### Post by narasimha18sv on 2013-10-03
Hi All,
I want to setup my own cloud environment. I have my hardware, created some of the virtual machines(VM) already. Is there a way to deploy some services on those machine using juju?
What i observed with the commands bootstarp and deploy, they are creating new virtual machines(VM) and deploying the services on those virtual machines.

Please let me know the procedure to deploy my own service orchestration on the h/w.

I tried with local environment setup on one of the virtual machine but it is failing with the below error 
error: Put http://<lxc_ip>:8040/tools/juju-1.14.1.1-precise-amd64.tgz: write tcp <xx.xxx.xx.xx>:8080: broken pipe

I have followed the procedure specified in below link
            [https://juju.ubuntu.com/docs/config-local.html](https://juju.ubuntu.com/docs/config-local.html)

Please help me in leveraging the solution for my requirement. 
Thanks in advance.

Regards,
Narasimha

---

### Post by castrojo on 2013-10-03
Juju currently needs to spawn it's own containers to orchestrate, it doesn't yet reuse existing containers that you've made prior to this. You only need to just `juju bootstrap` and then start juju deploying things, you don't need to make the containers by hand. What command did you run before you saw the error?

---

### Post by narasimha18sv on 2013-10-03
"juju bootstrap" is the command for which i got the error. It got resoled . this was due to proxy problem.

Currently juju only configures the ip for the VM  or container and deploys the charm specified. According to my requirement i need to assign the ip for a VM and then i need to deploy the charm. 

I have few doubts ragarding juju:
1. How juju assigns the ip address to a VM or container?
2. How can we install another charm on the container or VM created using juju?
3. Can we redeploy a charm on the same VM or container?
4. How juju is creating VMs or containers? what is the life cycle or architecture of doing it.
5. is there anu document where I can get complete architecture or sequential steps how juju deploys a charm?

Thanks in advance 
Regards,
Narasimha

---

### Post by nagaraju-bingi on 2013-10-04
Hi,

I'm intrested and started exploring the Juju functionality. I have Chef/puppet knowledge prior to this Juju. 

Using chef:

1) Chef-server
2) CHef-client which is DevOps machines
3) Target node where i want to install required tools/softwares on a target machine.
4) i usually go with "knife bootstrap <target-node-ip-addr> <recipes>
5) With the above command i could able manage all the nodes and software installation.

In similar lines, I would like to implement using Juju. Please help me in this regrd.

Thanks in advance.

--Nagaraju B

---

### Post by castrojo on 2013-10-04
For 1. and 4. - Juju isn't really assigning IPs or creating the VMs/containers, the cloud provider you are using does that. For #2 and #3 check out my answer here: [http://askubuntu.com/a/353642/235](http://askubuntu.com/a/353642/235) 

#5 is a tough one, I think this is the closest thing we have: 

- [https://juju.ubuntu.com/docs/authors-charm-anatomy.html](https://juju.ubuntu.com/docs/authors-charm-anatomy.html)
- [http://blog.labix.org/2013/06/25/the-heart-of-juju](http://blog.labix.org/2013/06/25/the-heart-of-juju)

---

### Post by castrojo on 2013-10-04
> **nagaraju-bingi said:**
> Hi,
4) i usually go with "knife bootstrap <target-node-ip-addr> <recipes>


Assuming your charm is what you want to deploy to machine #2 let's say:

   juju deploy --to 2 wordpress

---

