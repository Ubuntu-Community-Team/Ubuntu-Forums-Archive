---
title: "AUFS status update"
date: 2012-02-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cariboo on 2012-02-29
This is just an update on the status of AUFS:

> Hi All,

Early in the Precise Pangolin 12.04 development cycle, we disabled
support for AUFS in the kernel.  This decision was made at UDS.  The
reasoning behind this decision included:

      * AUFS is not upstream.  Despite previous efforts from it's
        maintainer, it does not appear it will ever land upstream.
      * AUFS is a maintenance burden for the Ubuntu Kernel Team due to
        the fact that it is not upstream.
      * Support for OverlayFS has been available since Oneiric.  We have
        been encouraging migration to OverlayFS. The installer has
        already transitioned to using OverlayFS (which was done in
        Oneiric).

We've noted the disablement of AUFS in every Technical Overview for each
12.04 milestone.  However, we felt it was also necessary to send a
widespread notification.

For anyone struggling with the dropped support of AUFS, we would like to
hear from you.  We'd be particularly interested in specific use case
scenarios where OverlayFS is not meeting the needs/requirements
previously met by AUFS.  We are already aware of some inotify issues
with OverlayFS [1].  We are curious if there are any other specific
cases where people are experiencing issues with OverlayFS.  We'd like to
gather any compelling evidence to support the requests to re-enable
AUFS.

Thanks,
Leann Ogasawara

---

### Post by badgerhill on 2012-03-02
hi,

well i am having troubles using overlayfs as i have never used it before. i could not find any usefull examples on how to use overlayfs.
all i want to do is create a sandboxed home directory, which i used to create with aufs. is there a migration guide or other info you could point me at.

thanks
thomas

---

### Post by cariboo on 2012-03-02
> **badgerhill said:**
> hi,

well i am having troubles using overlayfs as i have never used it before. i could not find any usefull examples on how to use overlayfs.
all i want to do is create a sandboxed home directory, which i used to create with aufs. is there a migration guide or other info you could point me at.

thanks
thomas

Did you read the last paragraph of my quote? If you are having a problem with your user case contact the kernel team You can do it by joining the mailing list [here]("https://lists.ubuntu.com/mailman/listinfo/kernel-team")

---

### Post by dino99 on 2012-03-02
Seems that Tim Gardner have an other opinion for the coming 18-28 kernel:

[ Tim Gardner ]

  * [Config] Enable aufs
    - LP: #943119

---

