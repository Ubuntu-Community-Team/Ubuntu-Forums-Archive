---
title: "LXD container migration to another &quot;host&quot; same hardware?"
date: 2019-08-31
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2019-08-31
I've come to prefer fresh installs on upgrade rather than upgrading in place however this poses a problem for me. I've put all my services into lxd containers. All my containers are currently 18.04 while the host is 16.04. I have a script that can do a debootstrap installation on another partition that I create with Lvm. is there a way to move the containers to the 18.04 installation simply? Or does it only work over the network between running hosts?

*EDIT* Apologies. I forgot to do my google search as I haven't had my caffiene yet. 

[https://www.cyberciti.biz/faq/how-to-movemigrate-lxd-vm-to-another-host-on-linux/](https://www.cyberciti.biz/faq/how-to-movemigrate-lxd-vm-to-another-host-on-linux/)

*EDIT 2*

If anyone can use it, I wrote a script to automate this process. I'm not entirely sure on my rsync switches. Pretty sure though. In my case I name my lvm partitions media1604, or 1804 depending on version. Can be changed easy enough to specify old root mountpoint.

```
PREVIOUSVERSION=$(expr $(grep Ubuntu /etc/issue | awk '{print $2}' | cut -d. -f 1) - 2)
PREVIOUSMOUNT=$(lsblk | grep "$PREVIOUSVERSION"04 | awk '{print $7}')
if mountpoint "$PREVIOUSMOUNT" ; then
  for container in "$PREVIOUSMOUNT"/var/lib/lxd/containers/* ; do
    rsync -auv --progress "$container" /var/lib/lxd/containers/
    lxd import $(basename "$container")
  done
else
  echo "must mount previous installation!"
fi
```

---

