---
title: "Amazon EC2: Which settings are reset when you launch a Ubuntu AMI-backed instance?"
date: 2014-04-24
forum: Server Platforms
---

### Post by User4519 on 2014-04-24
Hey guys!

I've been configuring my own EC2 AMI based on the 14.04 official Ubuntu AMI.

Part of it involved setting the locale and creating a password for the ubuntu user.

I've noticed, however that both of these changes are reverted if I create a new AMI based on the configuration and launch it in  a new instance. So does the aptitude repository locations if I use the AMI in a different region (e.g. copying it from eu-west-1 to us-east-1 will cause apt-get to fetch package information from the amazon mirrors in us-east-1).

I'd like to know exactly what settings and configurations are reset or modified when this happens, and also how?

If any one of you know, it'd be most appreciated :)

Thanks,
Daniel

EDIT: Actually, this seems to happen on every reboot (at least the removal of the password I set on the "ubuntu" user).

---

