---
title: "Unable to create a MaaS KVM VM with multiple disks"
date: 2021-12-10
forum: Ubuntu Cloud and Juju
---

### Post by x-se on 2021-12-10
I am trying to go through the steps to install OpenStack through MaaS and Juju. I originally bought hardware, but it doesn't match so that makes things a little more complicated as far as compute nodes. 

One of my nodes is relatively beefy, so I started messing around with the MaaS KVM-Host thing and, for the most part, it works great. It's just that when I try and create a VM with multiple disks (for a compute node), it fails and tells me:

Error:Pod unable to compose machine: Unable to compose machine because: Failed talking to pod: Failed creating instance record: Failed initialising instance: Failed to add device "disk2": Custom filesystem volumes require a path to be defined

Even though I am just hitting the Add Disk button and changing the allocation. There is plenty of space on disk, which is what I originally thought the problem was so I purchased more disks. 

There is some mention in the documentation about manually creating KVM VMs and then just assigning them to MaaS, that is certainly a possibility. Just wondering if I am doing something wrong to cause this error. Single-disk VMs work without issue, even just removing the extra disks from one that is erroring out works as well.

---

