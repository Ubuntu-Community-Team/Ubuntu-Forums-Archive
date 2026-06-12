---
title: "SELinux Policy Configure in Ubuntu 8.04"
date: 2008-08-28
forum: Security
---

### Post by kindloaf on 2008-08-28
I am trying to use SELinux in Ubuntu 8.04.  Looks like refpolicy is the only supported policy in the repository.
I downloaded policy.22 (refpolicy).  The size of the binary policy is about 360K(accurate size is 360296), much smaller than targeted policy in Fedora8. (about 3.5M).

Then I use dispol tool in checkpolicy to display the policy, seems there are no many useful domains in the policy.  There is no htttpd domain, no ftpd domain...
And the access vector really confuses me. For example, I think the domain insmod_t should be entered through insmod, rmmod, ...
But from the policy,  domain insmod_t has the entrypoint privilege over a lot of types: hplip_etc_t, lpd_tmp_t, proc_afs_t, pam_tmp_t, ... (there are more than 300 of them).

Did I do anything wrong?  And if I am getting the correct binary policy, why the entrypoint privilege is configure this way?

Thanks.

---

