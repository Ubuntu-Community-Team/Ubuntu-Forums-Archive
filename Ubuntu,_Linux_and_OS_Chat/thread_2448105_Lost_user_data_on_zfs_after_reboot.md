---
title: "Lost user data on zfs after reboot"
date: 2020-08-02
forum: Ubuntu, Linux and OS Chat
---

### Post by uzhao on 2020-08-02
I login my ubuntu 20.04 with ssh. Later I want to restart to clean up my memory. However, after reboot I found that all changes in last 10 days are gone on my zfs raid 1. Is it possible a command line reboot will break the process for zfs commit change? Is it possible to get my changes back? Thanks!

---

### Post by lammert-nijhof on 2020-08-05
First of all, how did you create the ZFS Raid-1. Is it a separate datapool created after the installation? Is Ubuntu installed on ZFS and do you boot from ZFS. Do you know how many snapshots you have? Try "zfs list -t snapshot". My wild guess would be that your BOOT datapool is full or >80% full.

---

