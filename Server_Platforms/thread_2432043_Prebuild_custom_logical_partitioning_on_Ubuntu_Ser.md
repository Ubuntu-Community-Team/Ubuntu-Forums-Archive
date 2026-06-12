---
title: "Prebuild custom logical partitioning on Ubuntu Server"
date: 2019-11-26
forum: Server Platforms
---

### Post by neeleshbh on 2019-11-26
I have an Ubuntu server image and I am trying to pre-build custom logical partitions during first boot process from USB reader. How can I achieve this? I have tried configuring pre-seed file as well but it doesn't boot. Also the system in which the image is booting is headless so I don't have any control over the installation and configuration.

---

### Post by ajgreeny on 2019-11-26
*Thread moved to **Server Platforms**.* which is more appropriate and a better fit.

---

### Post by LHammonds on 2019-11-26
I have tried to research this in the past but ran into trouble when trying to create separate LVM partitions.  I can work just fine when you use a single "atomic" partition and I guess this is how the devs tested it...but when it comes to multiple, separate partitions, it broke for me in 16.04.  I never found a workable solution with preseed and multi-partition.  I have not researched it in 18.04 since I use a pre-configured server as a template and vmware just rolls them out with a simple deploy command.

But here is some of the information I gathered while chatting in the member's only area:

[Appendix B. Automating the installation using preseeding](https://help.ubuntu.com/lts/installation-guide/amd64/apb.html)
[AskUbuntu.com Question that was self-answered](https://askubuntu.com/questions/806820/how-do-i-create-a-completely-unattended-install-of-ubuntu-desktop-16-04-1-lts)
[Preseed example 1](https://help.ubuntu.com/lts/installation-guide/example-preseed.txt)
[Preseed example 2](https://gist.github.com/lorin/5140029) (look at the forks for more variations)
[Article covering the 3 numbers in the partition setup](https://www.bishnet.net/tim/blog/2015/01/29/understanding-partman-autoexpert_recipe/)

And here is the recipe I was trying to make work (however, with 18.04, we do not need the swap partition anymore since it can be file-based):
```


d-i partman-auto/expert_recipe string prod-server :: \
  500 500 500 ext2 \
    $primary{ } \
    $bootable{ } \
    $lvmignore{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext2 } \
    mountpoint{ /boot } \
    label{ boot } \
  .\
  120% 2048 120% linux-swap \
    $lvmok{ } \
    format{ } \
    in_vg{ LVG } \
    lv_name{ swap } \
    method{ swap } \
  .\
  2000 2000 2000 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ root } \
    mountpoint{ / } \
    label{ root } \
  .\
  200 200 200 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ home } \
    mountpoint{ /home } \
    label{ home } \
  .\
  500 500 500 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ tmp } \
    mountpoint{ /tmp } \
    label{ tmp } \
    options/relatime{ relatime } \
    options/noexec{ noexec } \
    options/rw{ rw } \
  .\
  2000 2000 2000 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ usr } \
    mountpoint{ /usr } \
    label{ usr } \
  .\
  2000 2000 2000 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ var } \
    mountpoint{ /var } \
    label{ var } \
  .\
  200 200 200 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ srv } \
    mountpoint{ /srv } \
    label{ srv } \
  .\
  200 200 200 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ opt } \
    mountpoint{ /opt } \
    label{ opt } \
  .\
  500 500 500 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ bak } \
    mountpoint{ /bak } \
    label{ bak } \
  .\

```

---

