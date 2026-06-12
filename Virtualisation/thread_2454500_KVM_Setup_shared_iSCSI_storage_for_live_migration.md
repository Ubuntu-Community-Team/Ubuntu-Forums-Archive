---
title: "KVM Setup shared iSCSI storage for live migration"
date: 2020-11-30
forum: Virtualisation
---

### Post by diktio on 2020-11-30
Hello,

I have two nodes running Ubuntu 20.04 and KVM. Both nodes have an iSCSI connection to the iSCSI target. 

What I would like to know how to set this up. I don't know which filesystem I have to use. I was trying OCFS2 but I am getting this error: mount.ocfs2: Internal logic failure while trying to join the group

I don't know how to set this up correctly and which filesystem to use for the shared storage for KVM so that is can do I live migration. 

I also couldn't find any good documentation. 

Like to hear from you. 

Thanks,

Regards,

Rob

---

### Post by DuckHook on 2020-11-30
Please use only standard formatting and fonts. Odd styles/fonts are hard on the eyes and do not display properly on small mobile screens.

---

### Post by Raging_Cascadoo on 2020-12-02
I have no experience with KVM clustering and I am curious to learn how this works. I have not seen OCFS2 used outside of the Oracle VM environment. In that environment a separate volume repo is required for a clustered system.

I did see that there are some youtube tutorials out there for performing on Red hat with the GFS filesystem which you can probably have a look at for info.

---

### Post by TheFu on 2020-12-02
OCFS2 never heard of it. If it is tied to Oracle, we wouldn't touch it. Been burned with other products.

When we looked at this need, we were about to deploy Sheepdog after some testing. The other clustered file systems all had issues that seemed to require an in-house expert.
[https://www.admin-magazine.com/Archive/2014/23/Distributed-storage-with-Sheepdog](https://www.admin-magazine.com/Archive/2014/23/Distributed-storage-with-Sheepdog)

---

