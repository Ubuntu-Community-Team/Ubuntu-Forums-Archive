---
title: "Good Ubuntu BTRFS and grub-btrfs Installation Guide"
date: 2023-07-08
forum: Ubuntu, Linux and OS Chat
---

### Post by bmullan2 on 2023-07-08
I've been **[using this excellent BTRFS, Timeshift, grub-btrfs installation Guide from Lorenzo Bettini]("https://www.lorenzobettini.it/2022/10/timeshift-and-grub-btrfs-in-ubuntu/") **for 6 months now with no problems.    

On this machine I installed and am using Ubuntu 22.04.2 on a machine with two BTRFS 2TB NVME.

My NVME1 2TB BTRFS ssd is where I install Ubuntu (and my /home) etc

My NVME2 2TB ssd is used by my system's LXD as a BTRFS Storage Pool for my LXD Containers (example: mesh vpn Ubuntu Container 'server" nodes)
 and LXD **[VMs (example: windows 11)]("https://ubuntu.com/blog/lxd-virtual-machines-an-overview")**.

Also, a nice feature of following this Guide is its Integration instructions for TimeShift and ***apt/dpkg***.

When install is complete, every time you do:
[LIST]
[*][I]apt upgrade
[/I] 
[*][I]apt install AppX
[/I] 
[*]*apt remove/purge AppX* 
[*]etc. 
[/LIST]
    [I]TimeShift will "auto-magically" takes a BTRFS Snapshot!   
    [/I]
*The following is a recent LXD "sub-reddit" post explaining how LXD is smart enough when it creates an LXD Container versus an LXD Virtual Machine (VM) -- on BTRFS *-- ***LXD automatically marks VM files so BTRFS COW is Turned OFF for each VM*.**
as that's a general recommendation for VMs on BTRFS for possibly high disk I/O (such as databases) which negatively impacts VM performance.   
   
**[[SIZE=2]LXD BTRFS "Good to Know" - Question asked was regarding BTRFS COW and LXD VMs - LXD[/SIZE]]("https://www.reddit.com/r/LXD/comments/14s98z7/lxd_btrfs_good_to_know_question_asked_was_re/?utm_source=share&utm_medium=web2x&context=3")**[URL="https://www.reddit.com/r/LXD/comments/14s98z7/lxd_btrfs_good_to_know_question_asked_was_re/?utm_source=share&utm_medium=web2x&context=3"][COLOR=#000000] 

Thanks to Tom Parrott (a Maintainer & Developer on the LXD Project) [/COLOR][/URL][[COLOR=#000000]for the LXD details regarding BTRFS[/COLOR]]("https://www.reddit.com/r/LXD/comments/14s98z7/lxd_btrfs_good_to_know_question_asked_was_re/?utm_source=share&utm_medium=web2x&context=3")[COLOR=#000000] & COW mgmt.[/COLOR][URL="https://www.reddit.com/r/LXD/comments/14s98z7/lxd_btrfs_good_to_know_question_asked_was_re/?utm_source=share&utm_medium=web2x&context=3"]
[/URL][URL="https://www.reddit.com/r/LXD/comments/14s98z7/lxd_btrfs_good_to_know_question_asked_was_re/?utm_source=share&utm_medium=web2x&context=3"]
[/URL]

---

