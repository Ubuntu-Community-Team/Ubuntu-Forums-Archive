---
title: "Automated real-time deployment of Virtual Machines"
date: 2009-01-07
forum: Virtualisation
---

### Post by meatpan on 2009-01-07
Hello All,

I'm looking for suggestions, feedback, and ideas regarding a design for a cluster that hosts virtual machines.  If you know of any tools that can automate, simplify, or provide better QoS than the technique outlined below, please join the discussion.

The basic requirements are:
1. Select VM images (appliances) for deployment from a library of pre-configured and archived images.
2. Remotely initialize one or more virtual machines on an existing cluster.
3. Configure each remotely initialized VM to automatically connect to a set of persistent resources, such as NTPD, databases, as well as fast and slow filesytems.
4. Stop, checkpoint, and re-archive a vm instance (using the lib in #1)

So far, the current design is comprised of the following:
1. A minimal Ubuntu svr install across all cluster nodes, with each node connected to a common disk via NFS.
2. Installed and configured cluster scheduling software on each node, such as PBS, condor, or SGE.  This allows resource selection, reporting, monitoring, etc...
3. A virtual machine server, such as virtualbox, running on each node.

A user logs in to a 'head' node, and submits one or more cluster jobs.  The vm startup and initialization commands are supplied as the arguments to the script.  Once the VM is up and running, the user logs in to the running VM (ssh or rdesktop), and performs testing, development, etc...

I'm a bit shaky on how the networking, time synch, and file-system mounting will take place in a consistent and automated fashion.  A crude implementation of the 'library' (from #1 req) is essentially an organized shared directory with a manifest file.

There it is.  What do you think?

Meatpan

---

