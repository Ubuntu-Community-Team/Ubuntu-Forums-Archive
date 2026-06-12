---
title: "jaunty server eucalyptus setup"
date: 2009-06-12
forum: Server Platforms
---

### Post by bonytony on 2009-06-12
Hi Guys,
    I have been trying to get the eucalyptus cloud software working on one frontend and one node.
   It has been a challenge for me but I have now registered the cluster and one node in the system.
   I have downloaded my security certificates and I have 'sourced' the ~/.euca/eucarc file. I have built an image with the vmbuilder.

My problem is that when I execute the command

```

tony@tony-desktop:~/eucalyptusimages/creation$ ec2-upload-bundle -b kernel -m ./kernel/vmlinuz-2.6.28-11-generic.manifest.xml
invalid option: --ec2cert
Try 'ec2-upload-bundle --help'

```

I get the error you see.

searching the ubuntu forums some one does present the possible solution of did you source the ~/.euca/eucarc file (and I did) but it does not work for me.

Anyone have an idea of what has gone wrong here?

---

### Post by winter2009 on 2009-07-23
Hi I am also trying to set up the eucalyptus on my machine. I encounter some problem regarding adding nodes to cluster. How did you successfully do that? It already asks me to run some code to generate the ssh key file, but when I copy and paste the code to commandline it doesn't run. How do you generate the key file? Eager to get your reply. Thanks.

---

### Post by eun_liu on 2009-10-08
> **winter2009 said:**
> Hi I am also trying to set up the eucalyptus on my machine. I encounter some problem regarding adding nodes to cluster. How did you successfully do that? It already asks me to run some code to generate the ssh key file, but when I copy and paste the code to commandline it doesn't run. How do you generate the key file? Eager to get your reply. Thanks.

Hello ,I think your problem may be not the same as top guy's.

when adding nodes to cluster using "euca_conf --addnode IP" on server. the server will give you server commands. these command needs to be run on your nodes. one of the commands is the ssh key.

that's my opinion, i think you could try.

---

