---
title: "Can I build a cluster, where standalone sessions exist on nodes?"
date: 2010-01-18
forum: Server Platforms
---

### Post by tarekeldeeb on 2010-01-18
Hello server admins,

I'd like to build a computer lab with ubuntu. Some needed tools need to much processing. So I want a cluster. On the other hand, I need those PCs to run standalone sessions.

So ..
1- there's a Master of the cluster, and acts as a server as well (DHCP/Auth ..)
2- all client PCs may receive jobs from the master, and send their CPU usage for a balanced load on the whole cluster.
3- all clients may startup their own sessions as well, and may start a remote job on the master to be distributed amoung the cluster. I.e. clients may run local programs and remotely distributed programs.

Is there anything in real life that fits my dreams? ;)

Thanks in advance,
Tarek

---

### Post by DanYoSon on 2010-01-18
lately i have been looking into Ubuntu Enterprise Cloud UEC and this sounds like what you want to do

Correct me if im wrong i am traveling right now and have not been able to play with UEC yet

---

### Post by leandromartinez98 on 2010-01-18
It seems that you have to:

1 - Install the master and configure a DHCP server in it. Probably with fixed-IP, so get the MAC addresses of the other machines to configure the DHCP.

2 - Install the other machines as standard desktop machines (you need the Desktop? Otherwise you can install the server edition everywhere.) Configure the network of the nodes such that they get the IP given by the master.

3 - You must, probably, depending on what you want, share the /home directory of the master on all nodes. For doing so you need to install the nfs (network file system) server on the master and the client on the nodes. The original /home directory of each node can be used as something else, as for storage.

4 - Configure password-less ssh logins between nodes and between the master and the node (you need ssh public and private keys for that), and it is very easy if you have properly configured the /home share.

That's it, you have a cluster :-) . Basically a cluster is a bunch of machines in the same network which share a /home directory.

Concerning the load distribution, you can do that manually, by scripts, or use qsub. qsub distributes the jobs using complex strategies of user priorities. But, if the number of users of the cluster is relatively small it is not even worthwhile to do that, just talk with others.

---

### Post by tarekeldeeb on 2010-01-18
> **leandromartinez98 said:**
> 
That's it, you have a cluster :-) . Basically a cluster is a bunch of machines in the same network which share a /home directory.

Sorry , but this is a network with shared storage. Not a cluster that distributes CPU load on the clients.

Your description does not provide how a client may ask the master to run a heavy distributed job!

Or.. what do you think ?

---

### Post by leandromartinez98 on 2010-01-18
Well, a network with shared storage IS a cluster. All the clusters I've worked with (built by me or others) are like that. The distribution of the load is not dependent on that architecture, but on other software that will handle it. Qsub is one alternative to manage the cluster load between users.
Check the site of "Rocks" ([http://www.rocksclusters.org/](http://www.rocksclusters.org/)), which is a linux distribution specifically designed for clusters, based on CentOS. You will see that what it does is what I've described, and it provides some tools to facilitate the installation and managing of the cluster afterwards. 

The question on how to run a specific program distributed among the cluster is another one. This depends on the program itself being parallelizable, and is program-specific. The programs are parallelized sending jobs (sub-programs, lets say) to the nodes via ssh (or some other communication protocol), that's why the ssh must be password-less.


EDIT: You don't generally "ask the master to run a job", you usually choose in which nodes you want to run the job, and how many CPUs on each node will be used, that is independent on the job been sent from the master or from some node.

---

### Post by koenn on 2010-01-18
> **leandromartinez98 said:**
>  Basically a cluster is a bunch of machines in the same network which share a /home directory.
> **leandromartinez98 said:**
> Well, a network with shared storage IS a cluster.  ... .
not really - [http://en.wikipedia.org/wiki/Computer_cluster#Cluster_categorizations](http://en.wikipedia.org/wiki/Computer_cluster#Cluster_categorizations)

having a network share for home directories may be a prerequisite for some implementations of some cluster configurations, but a networtk share doe not make a cluster.

---

### Post by koenn on 2010-01-18
> **tarekeldeeb said:**
> Hello server admins,

I'd like to build a computer lab with ubuntu. Some needed tools need to much processing. So I want a cluster. On the other hand, I need those PCs to run standalone sessions.

when you say 'cluster', I think (load balancing) cluster in the classic sense where multiple servers present themselves as 1 single host to the network.
But perhaps you're thinking about some form of distributed computing (a "grid"  - see the wikipedia link in my previous post)

You might want to clarify this in order to get useful replies.

---

### Post by leandromartinez98 on 2010-01-18
> **koenn said:**
> not really - [http://en.wikipedia.org/wiki/Computer_cluster#Cluster_categorizations](http://en.wikipedia.org/wiki/Computer_cluster#Cluster_categorizations)

having a network share for home directories may be a prerequisite for some implementations of some cluster configurations, but a networtk share doe not make a cluster.

More than the shared storage is the capacity of every machine to launch jobs on the other machines that makes the cluster, and for that one only needs a network with ssh (probably password-less). The most complicated part of the communication is made by the MPI, which is program specific, and not dependent (as much as I have seen) on the cluster configuration.

Anyway, what I was trying to say is that the most basic cluster configuration, or if you want, this one: [http://en.wikipedia.org/wiki/Beowulf_cluster](http://en.wikipedia.org/wiki/Beowulf_cluster), requires a local network, a shared storage and a password-less communication protocol. That makes a cluster (not every kind of cluster). This is very likely the most common cluster configuration for high-demand computation in science.

---

### Post by koenn on 2010-01-18
> **leandromartinez98 said:**
> More than the shared storage is the capacity of every machine to launch jobs on the other machines that makes the cluster, and for that one only needs a network with ssh (probably password-less). The most complicated part of the communication is made by the MPI, which is program specific, and not dependent (as much as I have seen) on the cluster configuration.

wouldn't it make sense, then, to say that what essentially makes a bunch of computers "a cluster" is : your grid engine, your MPI, your whatever it is that allows for a coordinated manner of parrallelized, distributed; load balanced .... processing, more so than the fact that this bunch of computers is on a network with file sharing ?

---

### Post by zerubbabel on 2010-01-18
I'd like to build something similar, but hopefully simpler. My concept for a computer lab is having one robust server and a roomful of workstations that boot from the server but use the local disk (for swap space only), memory, and cpu resources of the client to run applications for the user sitting at that station. A user could sit down at any workstation and login to his account, which is hosted on the server, and run whatever applications are installed and available on that server. Is there a well-defined procedure for setting up such a computer lab?

---

### Post by lukeiamyourfather on 2010-01-18
> **tarekeldeeb said:**
> 
2- all client PCs may receive jobs from the master, and send their CPU usage for a balanced load on the whole cluster.
3- all clients may startup their own sessions as well, and may start a remote job on the master to be distributed amoung the cluster. I.e. clients may run local programs and remotely distributed programs.


What kind of jobs will be running on the "cluster", specifically? How parallel is the work, single tasks that happen in arbitrary order? That will be the determining factor in how all this will work or not work. Basically though you'll need a queue manager like Sun Grid Engine or similar. A daemon runs on the server to keep track of all submitted jobs and dish out the work. The "slave" daemon can be started and stopped on each machine by the user which is what allows a machine to pickup a job from the queue. By default the machines could have the slave daemon running, and if a user needs the machine for an interactive session then they can simply stop the slave daemon and use the machine, when they are done start the slave daemon again and the machine will be a part of the "cluster" again. Easier said than done but that's the idea behind most "clusters" out there. Cheers!

---

### Post by BkkBonanza on 2010-01-19
@zerubbabel
What you are asking about is using "Thin CLients" in a Linux Terminal Server type of arrangement. Check out LTSP on wikipedia for a start,
[http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project](http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project)

That of course, is different than a cluster. But a cluster is not simply the same as network shared storage obviously, otherwise every network in the world could be called a cluster. The key element is management of resources and jobs to solve a particular task. Once you overlay this on top of a network you have a cluster. This is usually very problem specific so asking to make a cluster without any idea what it will be doing is just a bit silly. If you want input on specific cluster strategies then start by defining what problem you want to solve. Without that you're just howling in the wind.

---

### Post by tarekeldeeb on 2010-01-19
> **zerubbabel said:**
> .. that boot from the server but use the local disk (for swap space only), memory, and cpu resources of the client to run applications ..

so easy, LTSP with fat client configuration. There are many straight forward tutorials.
1- You setup an image from a chroot on the server
2- clients boot through PXE using this image
3- Login through the server, but use local resources.

---

### Post by tarekeldeeb on 2010-01-19
> **lukeiamyourfather said:**
> What kind of jobs will be running on the "cluster", specifically?

They are EDA tools mostly. Not sure about the parallelizing characteristics of those tools.

> **lukeiamyourfather said:**
> .. when they are done start the slave daemon again and the machine will be a part of the "cluster" again.

You got your hands on the question: Can this daemon run with an existing session? Do I really need to close the session for the slave grid controller to run?

---

### Post by leandromartinez98 on 2010-01-19
> **koenn said:**
> wouldn't it make sense, then, to say that what essentially makes a bunch of computers "a cluster" is : your grid engine, your MPI, your whatever it is that allows for a coordinated manner of parrallelized, distributed; load balanced .... processing, more so than the fact that this bunch of computers is on a network with file sharing ?

Sincerely, I think this is just question of semantics. I work with heavily parallalelized applications in clusters, and my clusters are like that. Each application have its own MPI interface, so I don't put the MPI into my cluster definition.

Back to what he is actually asking:

You can use PXE to boot your "clients" from the master, through the network. However, my advice is not to do that. Currently hard-disks are relatively very cheap, so the work to do that is not usually worthwhile.
For example, even the Rocks distribution I mentioned, designed for very large clusters, requires each node to have a hard disk (this is not the "rule", please, only an example). For small deployments the advantage is even smaller.

It is very easy with simple scripts to on the master to synchronise the user accounts on all "nodes", and to have the same applications installed on all machines. For the users to have the felling of being on their accounts, you only need to share the /home directory.

That's the way we do it. We have already done clusters with PXE with diskless nodes, but we don't do that anymore.

---

### Post by lukeiamyourfather on 2010-01-19
> **tarekeldeeb said:**
> They are EDA tools mostly. Not sure about the parallelizing characteristics of those tools.



You got your hands on the question: Can this daemon run with an existing session? Do I really need to close the session for the slave grid controller to run?

Sounds like Sun Grid Engine would be perfect for managing the job queue. Yes, the daemon can run in an existing session if you want. Depending on what resources the jobs will take you might want to stop the daemon for interactive end user sessions to improve the user experience. Cheers!

---

### Post by koenn on 2010-01-19
> **leandromartinez98 said:**
> Sincerely, I think this is just question of semantics.
Semantics is the study of meaning, so yes, the question whether the words "network" and "cluster" have the same meaning, *is* semantics.  My point is that they do not have the same meaning.

But yeah, let's not hijack this thread any further.

---

