---
title: "LXD cannot start containers after install and reboot"
date: 2016-01-20
forum: Virtualisation
---

### Post by michael343 on 2016-01-20
Hi,

I have a fresh build Ubuntu Server 14.04.03 LTS x64 hypervisor/file server with the following config

  CIFs Shares
  NFS shares
  UFW
  iscsi
  NUT
  static IP with network bridge (br0)
  libvirt / kvm 
  lxd

I cannot seem to start lxd/lxc containers with kvm installed.

I managed to start a ubuntu trusty container as root (after sudo newgrp lxc) but then after reboot I get this message when trying to start a container:
*~$ lxc start my-ubuntu*
*error: Error calling 'lxd forkstart my-ubuntu /var/lib/lxd/containers /var/log/lxd/my-ubuntu/lxc.conf': err='exit status 1'*
*Try `lxc info --show-log my-ubuntu` for more info*

Install was based on the page [https://linuxcontainers.org/lxd/getting-started-cli/](https://linuxcontainers.org/lxd/getting-started-cli/)

kvm/libvirt works fine.  I got around the ufw / bridged network issue by modifying the UFW config DEFAULT_FORWARD_POLICY="ACCEPT".

Is it possible to run lxd containers on the same machine as kvm?

This feels more like a permissions issue as I did manage to start a container at the same time as a kvm guest although I did not try to get into the shell.

Thanks

Log below:

```

Name: my-ubuntu
Status: Stopped


Log:


            lxc 1453274863.094 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453274863.094 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453274863.113 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453274875.188 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453274875.188 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453274875.190 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453274875.192 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453274875.197 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453274875.197 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453274875.199 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453274875.202 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453274875.276 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453274875.276 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 9
            lxc 1453274875.277 INFO     lxc_container - lxccontainer.c:do_lxcapi_start:712 - Attempting to set proc title to [lxc monitor] /var/lib/lxd/containers my-ubuntu
            lxc 1453274875.277 ERROR    lxc_utils - utils.c:setproctitle:1455 - Invalid argument - setting cmdline failed
            lxc 1453274875.278 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 9
            lxc 1453274875.278 INFO     lxc_lsm - lsm/lsm.c:lsm_init:48 - LSM security driver AppArmor
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .reject_force_umount  # comment this to allow umount -f;  not recommended.
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for reject_force_umount action 0
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:do_resolve_add_rule:216 - Setting seccomp rule to reject force umounts


            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for reject_force_umount action 0
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:do_resolve_add_rule:216 - Setting seccomp rule to reject force umounts


            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .[all].
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .kexec_load errno 1.
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for kexec_load action 327681
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for kexec_load action 327681
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .open_by_handle_at errno 1.
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for open_by_handle_at action 327681
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for open_by_handle_at action 327681
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .init_module errno 1.
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for init_module action 327681
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for init_module action 327681
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .finit_module errno 1.
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for finit_module action 327681
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for finit_module action 327681
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .delete_module errno 1.
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for delete_module action 327681
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for delete_module action 327681
            lxc 1453274875.278 INFO     lxc_seccomp - seccomp.c:parse_config_v2:436 - Merging in the compat seccomp ctx into the main one
            lxc 1453274875.278 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/bin/lxd callhook /var/lib/lxd 1 start' for container 'my-ubuntu', config section 'lxc'
            lxc 1453274875.279 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 9
            lxc 1453274875.280 INFO     lxc_monitor - monitor.c:lxc_monitor_sock_name:178 - using monitor sock name lxc/d78a9d7e97b4b375//var/lib/lxd/containers
            lxc 1453274875.280 ERROR    lxc_monitor - monitor.c:lxc_monitor_open:209 - connect : backing off 10
            lxc 1453274875.480 DEBUG    lxc_start - start.c:setup_signal_fd:278 - sigchild handler set
            lxc 1453274875.480 INFO     lxc_start - start.c:lxc_init:474 - 'my-ubuntu' is initialized
            lxc 1453274875.480 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453274875.480 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453274875.481 DEBUG    lxc_start - start.c:__lxc_start:1186 - Not dropping cap_sys_boot or watching utmp
            lxc 1453274875.482 INFO     lxc_start - start.c:resolve_clone_flags:883 - Cloning a new user namespace
            lxc 1453274875.489 DEBUG    lxc_conf - conf.c:instantiate_veth:2821 - instantiated veth 'veth0GFWYP/vethFKQL0O', index is '8'
            lxc 1453274875.489 INFO     lxc_cgroup - cgroup.c:cgroup_init:65 - cgroup driver cgmanager initing for my-ubuntu
            lxc 1453274875.493 INFO     lxc_cgmanager - cgmanager.c:cgm_setup_limits:1537 - cgroup limits have been setup
            lxc 1453274875.531 DEBUG    lxc_conf - conf.c:lxc_assign_network:3238 - move 'eth0' to '15875'
            lxc 1453274875.537 NOTICE   lxc_start - start.c:do_start:699 - switching to gid/uid 0 in new user namespace
            lxc 1453274875.539 DEBUG    lxc_conf - conf.c:setup_rootfs:1295 - mounted '/var/lib/lxd/containers/my-ubuntu/rootfs' on '/usr/lib/x86_64-linux-gnu/lxc'
            lxc 1453274875.539 INFO     lxc_conf - conf.c:setup_utsname:928 - 'my-ubuntu' hostname has been setup
            lxc 1453274875.551 DEBUG    lxc_conf - conf.c:setup_hw_addr:2368 - mac address '00:16:3e:f0:8d:90' on 'eth0' has been setup
            lxc 1453274875.551 DEBUG    lxc_conf - conf.c:setup_netdev:2595 - 'eth0' has been setup
            lxc 1453274875.551 INFO     lxc_conf - conf.c:setup_network:2616 - network has been setup
            lxc 1453274875.551 INFO     lxc_conf - conf.c:mount_autodev:1157 - Mounting container /dev
            lxc 1453274875.552 INFO     lxc_conf - conf.c:mount_autodev:1179 - Mounted tmpfs onto /usr/lib/x86_64-linux-gnu/lxc/dev
            lxc 1453274875.552 INFO     lxc_conf - conf.c:mount_autodev:1197 - Mounted container /dev
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1738 - remounting /sys/fs/fuse/connections on /usr/lib/x86_64-linux-gnu/lxc/sys/fs/fuse/connections to respect bind or remount options
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1753 - (at remount) flags for /sys/fs/fuse/connections was 4096, required extra flags are 0
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1762 - mountflags already was 4096, skipping remount
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1788 - mounted '/sys/fs/fuse/connections' on '/usr/lib/x86_64-linux-gnu/lxc/sys/fs/fuse/connections', type 'none'
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1738 - remounting /sys/kernel/debug on /usr/lib/x86_64-linux-gnu/lxc/sys/kernel/debug to respect bind or remount options
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1753 - (at remount) flags for /sys/kernel/debug was 4096, required extra flags are 0
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1762 - mountflags already was 4096, skipping remount
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1788 - mounted '/sys/kernel/debug' on '/usr/lib/x86_64-linux-gnu/lxc/sys/kernel/debug', type 'none'
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1738 - remounting /sys/kernel/security on /usr/lib/x86_64-linux-gnu/lxc/sys/kernel/security to respect bind or remount options
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1753 - (at remount) flags for /sys/kernel/security was 4096, required extra flags are 0
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1762 - mountflags already was 4096, skipping remount
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1788 - mounted '/sys/kernel/security' on '/usr/lib/x86_64-linux-gnu/lxc/sys/kernel/security', type 'none'
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1738 - remounting /sys/fs/pstore on /usr/lib/x86_64-linux-gnu/lxc/sys/fs/pstore to respect bind or remount options
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1753 - (at remount) flags for /sys/fs/pstore was 4096, required extra flags are 0
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1762 - mountflags already was 4096, skipping remount
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1788 - mounted '/sys/fs/pstore' on '/usr/lib/x86_64-linux-gnu/lxc/sys/fs/pstore', type 'none'
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1788 - mounted 'mqueue' on '/usr/lib/x86_64-linux-gnu/lxc/dev/mqueue', type 'mqueue'
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1738 - remounting /dev/console on /usr/lib/x86_64-linux-gnu/lxc/dev/console to respect bind or remount options
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1753 - (at remount) flags for /dev/console was 4096, required extra flags are 0
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1762 - mountflags already was 4096, skipping remount
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1788 - mounted '/dev/console' on '/usr/lib/x86_64-linux-gnu/lxc/dev/console', type 'none'
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1738 - remounting /dev/full on /usr/lib/x86_64-linux-gnu/lxc/dev/full to respect bind or remount options
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1753 - (at remount) flags for /dev/full was 4096, required extra flags are 0
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1762 - mountflags already was 4096, skipping remount
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1788 - mounted '/dev/full' on '/usr/lib/x86_64-linux-gnu/lxc/dev/full', type 'none'
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1738 - remounting /dev/null on /usr/lib/x86_64-linux-gnu/lxc/dev/null to respect bind or remount options
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1753 - (at remount) flags for /dev/null was 4096, required extra flags are 0
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1762 - mountflags already was 4096, skipping remount
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1788 - mounted '/dev/null' on '/usr/lib/x86_64-linux-gnu/lxc/dev/null', type 'none'
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1738 - remounting /dev/random on /usr/lib/x86_64-linux-gnu/lxc/dev/random to respect bind or remount options
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1753 - (at remount) flags for /dev/random was 4096, required extra flags are 0
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1762 - mountflags already was 4096, skipping remount
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1788 - mounted '/dev/random' on '/usr/lib/x86_64-linux-gnu/lxc/dev/random', type 'none'
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1738 - remounting /dev/tty on /usr/lib/x86_64-linux-gnu/lxc/dev/tty to respect bind or remount options
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1753 - (at remount) flags for /dev/tty was 4096, required extra flags are 0
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1762 - mountflags already was 4096, skipping remount
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1788 - mounted '/dev/tty' on '/usr/lib/x86_64-linux-gnu/lxc/dev/tty', type 'none'
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1738 - remounting /dev/urandom on /usr/lib/x86_64-linux-gnu/lxc/dev/urandom to respect bind or remount options
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1753 - (at remount) flags for /dev/urandom was 4096, required extra flags are 0
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1762 - mountflags already was 4096, skipping remount
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1788 - mounted '/dev/urandom' on '/usr/lib/x86_64-linux-gnu/lxc/dev/urandom', type 'none'
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1738 - remounting /dev/zero on /usr/lib/x86_64-linux-gnu/lxc/dev/zero to respect bind or remount options
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1753 - (at remount) flags for /dev/zero was 4096, required extra flags are 0
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1762 - mountflags already was 4096, skipping remount
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1788 - mounted '/dev/zero' on '/usr/lib/x86_64-linux-gnu/lxc/dev/zero', type 'none'
            lxc 1453274875.552 ERROR    lxc_utils - utils.c:open_without_symlink:1620 - No such file or directory - Error examining efi in /usr/lib/x86_64-linux-gnu/lxc/sys/firmware/efi/efivars
            lxc 1453274875.552 INFO     lxc_conf - conf.c:mount_entry:1727 - failed to mount '/sys/firmware/efi/efivars' on '/usr/lib/x86_64-linux-gnu/lxc/sys/firmware/efi/efivars' (optional): No such file or directory
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1738 - remounting /proc/sys/fs/binfmt_misc on /usr/lib/x86_64-linux-gnu/lxc/proc/sys/fs/binfmt_misc to respect bind or remount options
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1753 - (at remount) flags for /proc/sys/fs/binfmt_misc was 4110, required extra flags are 14
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1788 - mounted '/proc/sys/fs/binfmt_misc' on '/usr/lib/x86_64-linux-gnu/lxc/proc/sys/fs/binfmt_misc', type 'none'
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1738 - remounting /var/lib/lxd/devlxd on /usr/lib/x86_64-linux-gnu/lxc/dev/lxd to respect bind or remount options
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1753 - (at remount) flags for /var/lib/lxd/devlxd was 4096, required extra flags are 0
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1762 - mountflags already was 4096, skipping remount
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1788 - mounted '/var/lib/lxd/devlxd' on '/usr/lib/x86_64-linux-gnu/lxc/dev/lxd', type 'none'
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1738 - remounting /var/lib/lxd/shmounts/my-ubuntu on /usr/lib/x86_64-linux-gnu/lxc/dev/.lxd-mounts to respect bind or remount options
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1753 - (at remount) flags for /var/lib/lxd/shmounts/my-ubuntu was 4096, required extra flags are 0
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1762 - mountflags already was 4096, skipping remount
            lxc 1453274875.552 DEBUG    lxc_conf - conf.c:mount_entry:1788 - mounted '/var/lib/lxd/shmounts/my-ubuntu' on '/usr/lib/x86_64-linux-gnu/lxc/dev/.lxd-mounts', type 'none'
            lxc 1453274875.552 INFO     lxc_conf - conf.c:mount_file_entries:2150 - mount points have been setup
            lxc 1453274875.552 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/share/lxcfs/lxc.mount.hook' for container 'my-ubuntu', config section 'lxc'
            lxc 1453274875.631 INFO     lxc_conf - conf.c:fill_autodev:1225 - Creating initial consoles under container /dev
            lxc 1453274875.631 INFO     lxc_conf - conf.c:fill_autodev:1236 - Populating container /dev
            lxc 1453274875.631 INFO     lxc_conf - conf.c:fill_autodev:1269 - Populated container /dev
            lxc 1453274875.631 INFO     lxc_conf - conf.c:setup_dev_console:1498 - no console
            lxc 1453274875.631 INFO     lxc_utils - utils.c:mount_proc_if_needed:1718 - I am 1, /proc/self points to '1'
            lxc 1453274875.639 DEBUG    lxc_conf - conf.c:setup_rootfs_pivot_root:1135 - pivot_root syscall to '/usr/lib/x86_64-linux-gnu/lxc' successful
            lxc 1453274875.639 INFO     lxc_conf - conf.c:setup_tty:1080 - 0 tty(s) has been setup
            lxc 1453274875.639 INFO     lxc_conf - conf.c:setup_personality:1473 - set personality to '0x0'
            lxc 1453274875.639 DEBUG    lxc_conf - conf.c:setup_caps:2279 - drop capability 'mac_admin' (33)
            lxc 1453274875.639 DEBUG    lxc_conf - conf.c:setup_caps:2279 - drop capability 'mac_override' (32)
            lxc 1453274875.639 DEBUG    lxc_conf - conf.c:setup_caps:2279 - drop capability 'sys_time' (25)
            lxc 1453274875.639 DEBUG    lxc_conf - conf.c:setup_caps:2279 - drop capability 'sys_module' (16)
            lxc 1453274875.639 DEBUG    lxc_conf - conf.c:setup_caps:2288 - capabilities have been setup
            lxc 1453274875.639 NOTICE   lxc_conf - conf.c:lxc_setup:4026 - 'my-ubuntu' is setup.
            lxc 1453274875.640 DEBUG    lxc_cgmanager - cgmanager.c:cgm_setup_limits:1533 - cgroup 'devices.deny' set to 'c 5:1 rwm'
            lxc 1453274875.640 INFO     lxc_cgmanager - cgmanager.c:cgm_setup_limits:1537 - cgroup limits have been setup
            lxc 1453274875.640 INFO     lxc_apparmor - lsm/apparmor.c:apparmor_process_label_set:187 - changed apparmor profile to lxd-my-ubuntu_</var/lib/lxd>
            lxc 1453274875.640 NOTICE   lxc_start - start.c:start:1295 - exec'ing '/sbin/init'
            lxc 1453274875.641 NOTICE   lxc_start - start.c:post_start:1306 - '/sbin/init' started with pid '15875'
            lxc 1453274875.641 INFO     lxc_console - console.c:lxc_console_mainloop_add:285 - no console
            lxc 1453274875.641 WARN     lxc_start - start.c:signal_handler:326 - invalid pid for SIGCHLD
            lxc 1453274875.641 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274875.641 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274875.642 DEBUG    lxc_commands - commands.c:lxc_cmd_get_state:579 - 'my-ubuntu' is in 'RUNNING' state
            lxc 1453274875.642 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274875.643 DEBUG    lxc_commands - commands.c:lxc_cmd_get_state:579 - 'my-ubuntu' is in 'RUNNING' state
            lxc 1453274875.643 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274875.645 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274875.647 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274875.647 DEBUG    lxc_commands - commands.c:lxc_cmd_get_state:579 - 'my-ubuntu' is in 'RUNNING' state
            lxc 1453274875.648 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274875.650 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274875.650 DEBUG    lxc_commands - commands.c:lxc_cmd_get_state:579 - 'my-ubuntu' is in 'RUNNING' state
            lxc 1453274875.651 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.903 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453274902.903 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453274902.908 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.909 DEBUG    lxc_commands - commands.c:lxc_cmd_get_state:579 - 'my-ubuntu' is in 'RUNNING' state
            lxc 1453274902.909 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.910 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.912 DEBUG    lxc_commands - commands.c:lxc_cmd_get_state:579 - 'my-ubuntu' is in 'RUNNING' state
            lxc 1453274902.912 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.912 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.912 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.914 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.915 DEBUG    lxc_commands - commands.c:lxc_cmd_get_state:579 - 'my-ubuntu' is in 'RUNNING' state
            lxc 1453274902.915 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.916 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.918 DEBUG    lxc_commands - commands.c:lxc_cmd_get_state:579 - 'my-ubuntu' is in 'RUNNING' state
            lxc 1453274902.918 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.919 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.921 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.923 DEBUG    lxc_commands - commands.c:lxc_cmd_get_state:579 - 'my-ubuntu' is in 'RUNNING' state
            lxc 1453274902.923 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.923 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.924 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.924 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.925 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.925 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.927 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.927 DEBUG    lxc_commands - commands.c:lxc_cmd_get_state:579 - 'my-ubuntu' is in 'RUNNING' state
            lxc 1453274902.928 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453274902.929 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453275163.691 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275163.691 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275163.693 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453275163.695 DEBUG    lxc_commands - commands.c:lxc_cmd_get_state:579 - 'my-ubuntu' is in 'RUNNING' state
            lxc 1453275163.695 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453275163.696 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453275163.698 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453275163.698 DEBUG    lxc_commands - commands.c:lxc_cmd_get_state:579 - 'my-ubuntu' is in 'RUNNING' state
            lxc 1453275163.698 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453275163.700 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 3
            lxc 1453275163.700 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 4
            lxc 1453275163.700 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 5
            lxc 1453275163.700 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 6
            lxc 1453275163.700 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 7
            lxc 1453275163.700 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 8
            lxc 1453275163.700 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 9
            lxc 1453275163.700 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 10
            lxc 1453275163.700 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 11
            lxc 1453275163.700 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 13
            lxc 1453275163.714 INFO     lxc_monitor - monitor.c:lxc_monitor_sock_name:178 - using monitor sock name lxc/d78a9d7e97b4b375//var/lib/lxd/containers
            lxc 1453275163.716 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453275163.718 DEBUG    lxc_commands - commands.c:lxc_cmd_get_state:579 - 'my-ubuntu' is in 'RUNNING' state
            lxc 1453275163.718 DEBUG    lxc_commands - commands.c:lxc_cmd_handler:893 - peer has disconnected
            lxc 1453275164.413 DEBUG    lxc_start - start.c:signal_handler:330 - container init process exited
            lxc 1453275164.413 DEBUG    lxc_start - start.c:__lxc_start:1241 - Container halting
            lxc 1453275164.413 DEBUG    lxc_start - start.c:__lxc_start:1256 - Pushing physical nics back to host namespace
            lxc 1453275164.413 DEBUG    lxc_start - start.c:__lxc_start:1259 - Tearing down virtual network devices used by container
            lxc 1453275164.413 WARN     lxc_conf - conf.c:lxc_delete_network:3114 - failed to remove interface 'eth0'
            lxc 1453275164.413 INFO     lxc_error - error.c:lxc_error_set_and_log:55 - child <15875> ended on signal (2)
            lxc 1453275164.413 WARN     lxc_conf - conf.c:lxc_delete_network:3114 - failed to remove interface 'eth0'
            lxc 1453275164.439 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/share/lxcfs/lxc.reboot.hook' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275164.944 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/bin/lxd callhook /var/lib/lxd 1 stop' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275170.074 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275170.074 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275170.077 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275170.078 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275170.078 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275170.081 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275170.560 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275170.560 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275170.562 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275170.564 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275477.775 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275477.775 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275477.777 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275477.779 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275491.972 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275491.972 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275491.995 ERROR    lxc_cgmanager - cgmanager.c:cgm_dbus_connect:176 - Error cgroup manager api version: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
            lxc 1453275491.996 ERROR    lxc_cgmanager - cgmanager.c:do_cgm_get:872 - Error connecting to cgroup manager
            lxc 1453275491.997 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275491.999 DEBUG    lxc_cgmanager - cgmanager.c:cgm_dbus_connect:152 - Failed opening dbus connection: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /sys/fs/cgroup/cgmanager/sock: Connection refused
            lxc 1453275491.999 ERROR    lxc_cgmanager - cgmanager.c:do_cgm_get:872 - Error connecting to cgroup manager
            lxc 1453275492.000 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275492.008 DEBUG    lxc_cgmanager - cgmanager.c:cgm_dbus_connect:152 - Failed opening dbus connection: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /sys/fs/cgroup/cgmanager/sock: Connection refused
            lxc 1453275492.008 ERROR    lxc_cgmanager - cgmanager.c:do_cgm_get:872 - Error connecting to cgroup manager
            lxc 1453275492.009 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275492.010 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275492.010 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275492.012 DEBUG    lxc_cgmanager - cgmanager.c:cgm_dbus_connect:152 - Failed opening dbus connection: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /sys/fs/cgroup/cgmanager/sock: Connection refused
            lxc 1453275492.012 ERROR    lxc_cgmanager - cgmanager.c:do_cgm_get:872 - Error connecting to cgroup manager
            lxc 1453275492.013 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275527.954 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275527.955 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275527.955 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275527.955 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275527.960 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275527.960 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275527.963 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275570.277 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275570.277 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275570.280 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275570.283 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275576.864 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275576.864 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275576.867 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275576.870 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275576.876 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275576.876 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275576.880 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275576.885 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275576.910 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275576.911 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 10
            lxc 1453275576.912 INFO     lxc_container - lxccontainer.c:do_lxcapi_start:712 - Attempting to set proc title to [lxc monitor] /var/lib/lxd/containers my-ubuntu
            lxc 1453275576.912 ERROR    lxc_utils - utils.c:setproctitle:1455 - Invalid argument - setting cmdline failed
            lxc 1453275576.914 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 10
            lxc 1453275576.914 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 10
            lxc 1453275576.914 INFO     lxc_lsm - lsm/lsm.c:lsm_init:48 - LSM security driver AppArmor
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .reject_force_umount  # comment this to allow umount -f;  not recommended.
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for reject_force_umount action 0
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:do_resolve_add_rule:216 - Setting seccomp rule to reject force umounts


            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for reject_force_umount action 0
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:do_resolve_add_rule:216 - Setting seccomp rule to reject force umounts


            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .[all].
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .kexec_load errno 1.
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for kexec_load action 327681
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for kexec_load action 327681
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .open_by_handle_at errno 1.
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for open_by_handle_at action 327681
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for open_by_handle_at action 327681
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .init_module errno 1.
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for init_module action 327681
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for init_module action 327681
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .finit_module errno 1.
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for finit_module action 327681
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for finit_module action 327681
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .delete_module errno 1.
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for delete_module action 327681
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for delete_module action 327681
            lxc 1453275576.914 INFO     lxc_seccomp - seccomp.c:parse_config_v2:436 - Merging in the compat seccomp ctx into the main one
            lxc 1453275576.914 INFO     lxc_monitor - monitor.c:lxc_monitor_sock_name:178 - using monitor sock name lxc/d78a9d7e97b4b375//var/lib/lxd/containers
            lxc 1453275576.914 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/bin/lxd callhook /var/lib/lxd 1 start' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275576.914 ERROR    lxc_monitor - monitor.c:lxc_monitor_open:209 - connect : backing off 10
            lxc 1453275576.945 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275576.945 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275576.945 DEBUG    lxc_start - start.c:setup_signal_fd:278 - sigchild handler set
            lxc 1453275576.945 INFO     lxc_start - start.c:lxc_init:474 - 'my-ubuntu' is initialized
            lxc 1453275576.946 DEBUG    lxc_start - start.c:__lxc_start:1186 - Not dropping cap_sys_boot or watching utmp
            lxc 1453275576.947 INFO     lxc_start - start.c:resolve_clone_flags:883 - Cloning a new user namespace
            lxc 1453275576.951 DEBUG    lxc_conf - conf.c:instantiate_veth:2821 - instantiated veth 'veth4BYXST/vethW78OXK', index is '7'
            lxc 1453275576.951 INFO     lxc_cgroup - cgroup.c:cgroup_init:65 - cgroup driver cgmanager initing for my-ubuntu
            lxc 1453275577.023 INFO     lxc_cgmanager - cgmanager.c:cgm_setup_limits:1537 - cgroup limits have been setup
            lxc 1453275577.052 DEBUG    lxc_conf - conf.c:lxc_assign_network:3238 - move 'eth0' to '2302'
            lxc 1453275577.059 NOTICE   lxc_start - start.c:do_start:699 - switching to gid/uid 0 in new user namespace
            lxc 1453275577.061 DEBUG    lxc_conf - conf.c:setup_rootfs:1295 - mounted '/var/lib/lxd/containers/my-ubuntu/rootfs' on '/usr/lib/x86_64-linux-gnu/lxc'
            lxc 1453275577.061 INFO     lxc_conf - conf.c:setup_utsname:928 - 'my-ubuntu' hostname has been setup
            lxc 1453275577.072 DEBUG    lxc_conf - conf.c:setup_hw_addr:2368 - mac address '00:16:3e:f0:8d:90' on 'eth0' has been setup
            lxc 1453275577.072 DEBUG    lxc_conf - conf.c:setup_netdev:2595 - 'eth0' has been setup
            lxc 1453275577.072 INFO     lxc_conf - conf.c:setup_network:2616 - network has been setup
            lxc 1453275577.072 INFO     lxc_conf - conf.c:mount_autodev:1157 - Mounting container /dev
            lxc 1453275577.073 INFO     lxc_conf - conf.c:mount_autodev:1179 - Mounted tmpfs onto /usr/lib/x86_64-linux-gnu/lxc/dev
            lxc 1453275577.073 INFO     lxc_conf - conf.c:mount_autodev:1197 - Mounted container /dev
            lxc 1453275577.074 ERROR    lxc_utils - utils.c:safe_mount:1686 - Operation not permitted - Failed to mount proc onto /usr/lib/x86_64-linux-gnu/lxc/proc
            lxc 1453275577.074 ERROR    lxc_conf - conf.c:lxc_mount_auto_mounts:828 - Operation not permitted - error mounting proc on /usr/lib/x86_64-linux-gnu/lxc/proc flags 14
            lxc 1453275577.074 ERROR    lxc_conf - conf.c:lxc_setup:3910 - failed to setup the automatic mounts for 'my-ubuntu'
            lxc 1453275577.074 ERROR    lxc_start - start.c:do_start:731 - failed to setup the container
            lxc 1453275577.074 ERROR    lxc_sync - sync.c:__sync_wait:51 - invalid sequence number 1. expected 2
            lxc 1453275577.074 WARN     lxc_conf - conf.c:lxc_delete_network:3114 - failed to remove interface 'eth0'
            lxc 1453275577.075 ERROR    lxc_start - start.c:__lxc_start:1213 - failed to spawn 'my-ubuntu'
            lxc 1453275577.100 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/share/lxcfs/lxc.reboot.hook' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275577.603 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/bin/lxd callhook /var/lib/lxd 1 stop' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275577.726 WARN     lxc_commands - commands.c:lxc_cmd_rsp_recv:172 - command get_init_pid failed to receive response
            lxc 1453275577.726 WARN     lxc_commands - commands.c:lxc_cmd_rsp_recv:172 - command get_init_pid failed to receive response
            lxc 1453275577.727 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275577.727 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275582.725 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275582.725 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275582.730 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275582.732 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275582.732 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275582.736 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275589.335 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275589.335 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275589.340 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275589.343 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275589.349 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275589.349 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275589.353 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275589.358 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275589.382 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275589.383 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 10
            lxc 1453275589.385 INFO     lxc_container - lxccontainer.c:do_lxcapi_start:712 - Attempting to set proc title to [lxc monitor] /var/lib/lxd/containers my-ubuntu
            lxc 1453275589.385 ERROR    lxc_utils - utils.c:setproctitle:1455 - Invalid argument - setting cmdline failed
            lxc 1453275589.386 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 10
            lxc 1453275589.386 INFO     lxc_lsm - lsm/lsm.c:lsm_init:48 - LSM security driver AppArmor
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .reject_force_umount  # comment this to allow umount -f;  not recommended.
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for reject_force_umount action 0
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:do_resolve_add_rule:216 - Setting seccomp rule to reject force umounts


            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for reject_force_umount action 0
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:do_resolve_add_rule:216 - Setting seccomp rule to reject force umounts


            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .[all].
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .kexec_load errno 1.
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for kexec_load action 327681
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for kexec_load action 327681
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .open_by_handle_at errno 1.
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for open_by_handle_at action 327681
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for open_by_handle_at action 327681
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .init_module errno 1.
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for init_module action 327681
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for init_module action 327681
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .finit_module errno 1.
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for finit_module action 327681
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for finit_module action 327681
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .delete_module errno 1.
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for delete_module action 327681
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for delete_module action 327681
            lxc 1453275589.386 INFO     lxc_seccomp - seccomp.c:parse_config_v2:436 - Merging in the compat seccomp ctx into the main one
            lxc 1453275589.386 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/bin/lxd callhook /var/lib/lxd 1 start' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275589.387 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 10
            lxc 1453275589.388 INFO     lxc_monitor - monitor.c:lxc_monitor_sock_name:178 - using monitor sock name lxc/d78a9d7e97b4b375//var/lib/lxd/containers
            lxc 1453275589.476 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275589.476 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275589.477 DEBUG    lxc_start - start.c:setup_signal_fd:278 - sigchild handler set
            lxc 1453275589.477 INFO     lxc_start - start.c:lxc_init:474 - 'my-ubuntu' is initialized
            lxc 1453275589.478 DEBUG    lxc_start - start.c:__lxc_start:1186 - Not dropping cap_sys_boot or watching utmp
            lxc 1453275589.479 INFO     lxc_start - start.c:resolve_clone_flags:883 - Cloning a new user namespace
            lxc 1453275589.480 DEBUG    lxc_conf - conf.c:instantiate_veth:2821 - instantiated veth 'vethXQY217/veth13IBAI', index is '9'
            lxc 1453275589.480 INFO     lxc_cgroup - cgroup.c:cgroup_init:65 - cgroup driver cgmanager initing for my-ubuntu
            lxc 1453275589.484 INFO     lxc_cgmanager - cgmanager.c:cgm_setup_limits:1537 - cgroup limits have been setup
            lxc 1453275589.520 DEBUG    lxc_conf - conf.c:lxc_assign_network:3238 - move 'eth0' to '2380'
            lxc 1453275589.528 NOTICE   lxc_start - start.c:do_start:699 - switching to gid/uid 0 in new user namespace
            lxc 1453275589.529 DEBUG    lxc_conf - conf.c:setup_rootfs:1295 - mounted '/var/lib/lxd/containers/my-ubuntu/rootfs' on '/usr/lib/x86_64-linux-gnu/lxc'
            lxc 1453275589.529 INFO     lxc_conf - conf.c:setup_utsname:928 - 'my-ubuntu' hostname has been setup
            lxc 1453275589.540 DEBUG    lxc_conf - conf.c:setup_hw_addr:2368 - mac address '00:16:3e:f0:8d:90' on 'eth0' has been setup
            lxc 1453275589.540 DEBUG    lxc_conf - conf.c:setup_netdev:2595 - 'eth0' has been setup
            lxc 1453275589.540 INFO     lxc_conf - conf.c:setup_network:2616 - network has been setup
            lxc 1453275589.540 INFO     lxc_conf - conf.c:mount_autodev:1157 - Mounting container /dev
            lxc 1453275589.540 INFO     lxc_conf - conf.c:mount_autodev:1179 - Mounted tmpfs onto /usr/lib/x86_64-linux-gnu/lxc/dev
            lxc 1453275589.540 INFO     lxc_conf - conf.c:mount_autodev:1197 - Mounted container /dev
            lxc 1453275589.541 ERROR    lxc_utils - utils.c:safe_mount:1686 - Operation not permitted - Failed to mount proc onto /usr/lib/x86_64-linux-gnu/lxc/proc
            lxc 1453275589.541 ERROR    lxc_conf - conf.c:lxc_mount_auto_mounts:828 - Operation not permitted - error mounting proc on /usr/lib/x86_64-linux-gnu/lxc/proc flags 14
            lxc 1453275589.541 ERROR    lxc_conf - conf.c:lxc_setup:3910 - failed to setup the automatic mounts for 'my-ubuntu'
            lxc 1453275589.541 ERROR    lxc_start - start.c:do_start:731 - failed to setup the container
            lxc 1453275589.541 ERROR    lxc_sync - sync.c:__sync_wait:51 - invalid sequence number 1. expected 2
            lxc 1453275589.541 WARN     lxc_conf - conf.c:lxc_delete_network:3114 - failed to remove interface 'eth0'
            lxc 1453275589.541 ERROR    lxc_start - start.c:__lxc_start:1213 - failed to spawn 'my-ubuntu'
            lxc 1453275589.572 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/share/lxcfs/lxc.reboot.hook' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275590.075 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/bin/lxd callhook /var/lib/lxd 1 stop' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275590.197 WARN     lxc_commands - commands.c:lxc_cmd_rsp_recv:172 - command get_init_pid failed to receive response
            lxc 1453275590.197 WARN     lxc_commands - commands.c:lxc_cmd_rsp_recv:172 - command get_init_pid failed to receive response
            lxc 1453275590.198 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275590.198 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275595.196 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275595.196 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275595.200 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275595.203 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275595.203 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275595.208 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275663.995 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275663.995 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275664.000 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275664.003 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275664.008 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275664.008 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275664.013 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275664.019 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275664.043 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275664.044 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 10
            lxc 1453275664.045 INFO     lxc_container - lxccontainer.c:do_lxcapi_start:712 - Attempting to set proc title to [lxc monitor] /var/lib/lxd/containers my-ubuntu
            lxc 1453275664.045 ERROR    lxc_utils - utils.c:setproctitle:1455 - Invalid argument - setting cmdline failed
            lxc 1453275664.046 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 10
            lxc 1453275664.046 INFO     lxc_lsm - lsm/lsm.c:lsm_init:48 - LSM security driver AppArmor
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .reject_force_umount  # comment this to allow umount -f;  not recommended.
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for reject_force_umount action 0
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:do_resolve_add_rule:216 - Setting seccomp rule to reject force umounts


            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for reject_force_umount action 0
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:do_resolve_add_rule:216 - Setting seccomp rule to reject force umounts


            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .[all].
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .kexec_load errno 1.
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for kexec_load action 327681
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for kexec_load action 327681
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .open_by_handle_at errno 1.
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for open_by_handle_at action 327681
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for open_by_handle_at action 327681
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .init_module errno 1.
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for init_module action 327681
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for init_module action 327681
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .finit_module errno 1.
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for finit_module action 327681
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for finit_module action 327681
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .delete_module errno 1.
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for delete_module action 327681
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for delete_module action 327681
            lxc 1453275664.046 INFO     lxc_seccomp - seccomp.c:parse_config_v2:436 - Merging in the compat seccomp ctx into the main one
            lxc 1453275664.046 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/bin/lxd callhook /var/lib/lxd 1 start' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275664.047 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 10
            lxc 1453275664.047 INFO     lxc_monitor - monitor.c:lxc_monitor_sock_name:178 - using monitor sock name lxc/d78a9d7e97b4b375//var/lib/lxd/containers
            lxc 1453275664.047 ERROR    lxc_monitor - monitor.c:lxc_monitor_open:209 - connect : backing off 10
            lxc 1453275664.071 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275664.071 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275664.074 DEBUG    lxc_start - start.c:setup_signal_fd:278 - sigchild handler set
            lxc 1453275664.074 INFO     lxc_start - start.c:lxc_init:474 - 'my-ubuntu' is initialized
            lxc 1453275664.074 DEBUG    lxc_start - start.c:__lxc_start:1186 - Not dropping cap_sys_boot or watching utmp
            lxc 1453275664.076 INFO     lxc_start - start.c:resolve_clone_flags:883 - Cloning a new user namespace
            lxc 1453275664.077 DEBUG    lxc_conf - conf.c:instantiate_veth:2821 - instantiated veth 'veth60KS77/veth4P6P1A', index is '11'
            lxc 1453275664.077 INFO     lxc_cgroup - cgroup.c:cgroup_init:65 - cgroup driver cgmanager initing for my-ubuntu
            lxc 1453275664.139 INFO     lxc_cgmanager - cgmanager.c:cgm_setup_limits:1537 - cgroup limits have been setup
            lxc 1453275664.164 DEBUG    lxc_conf - conf.c:lxc_assign_network:3238 - move 'eth0' to '2542'
            lxc 1453275664.170 NOTICE   lxc_start - start.c:do_start:699 - switching to gid/uid 0 in new user namespace
            lxc 1453275664.172 DEBUG    lxc_conf - conf.c:setup_rootfs:1295 - mounted '/var/lib/lxd/containers/my-ubuntu/rootfs' on '/usr/lib/x86_64-linux-gnu/lxc'
            lxc 1453275664.172 INFO     lxc_conf - conf.c:setup_utsname:928 - 'my-ubuntu' hostname has been setup
            lxc 1453275664.184 DEBUG    lxc_conf - conf.c:setup_hw_addr:2368 - mac address '00:16:3e:f0:8d:90' on 'eth0' has been setup
            lxc 1453275664.184 DEBUG    lxc_conf - conf.c:setup_netdev:2595 - 'eth0' has been setup
            lxc 1453275664.184 INFO     lxc_conf - conf.c:setup_network:2616 - network has been setup
            lxc 1453275664.184 INFO     lxc_conf - conf.c:mount_autodev:1157 - Mounting container /dev
            lxc 1453275664.184 INFO     lxc_conf - conf.c:mount_autodev:1179 - Mounted tmpfs onto /usr/lib/x86_64-linux-gnu/lxc/dev
            lxc 1453275664.185 INFO     lxc_conf - conf.c:mount_autodev:1197 - Mounted container /dev
            lxc 1453275664.185 ERROR    lxc_utils - utils.c:safe_mount:1686 - Operation not permitted - Failed to mount proc onto /usr/lib/x86_64-linux-gnu/lxc/proc
            lxc 1453275664.185 ERROR    lxc_conf - conf.c:lxc_mount_auto_mounts:828 - Operation not permitted - error mounting proc on /usr/lib/x86_64-linux-gnu/lxc/proc flags 14
            lxc 1453275664.185 ERROR    lxc_conf - conf.c:lxc_setup:3910 - failed to setup the automatic mounts for 'my-ubuntu'
            lxc 1453275664.185 ERROR    lxc_start - start.c:do_start:731 - failed to setup the container
            lxc 1453275664.185 ERROR    lxc_sync - sync.c:__sync_wait:51 - invalid sequence number 1. expected 2
            lxc 1453275664.185 WARN     lxc_conf - conf.c:lxc_delete_network:3114 - failed to remove interface 'eth0'
            lxc 1453275664.185 ERROR    lxc_start - start.c:__lxc_start:1213 - failed to spawn 'my-ubuntu'
            lxc 1453275664.212 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/share/lxcfs/lxc.reboot.hook' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275664.715 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/bin/lxd callhook /var/lib/lxd 1 stop' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275664.835 WARN     lxc_commands - commands.c:lxc_cmd_rsp_recv:172 - command get_init_pid failed to receive response
            lxc 1453275664.835 WARN     lxc_commands - commands.c:lxc_cmd_rsp_recv:172 - command get_init_pid failed to receive response
            lxc 1453275664.836 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275664.836 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275669.834 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275669.834 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275669.838 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275669.841 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275669.841 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275669.845 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275708.102 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275708.102 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275708.126 ERROR    lxc_cgmanager - cgmanager.c:cgm_dbus_connect:176 - Error cgroup manager api version: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
            lxc 1453275708.126 ERROR    lxc_cgmanager - cgmanager.c:do_cgm_get:872 - Error connecting to cgroup manager
            lxc 1453275708.127 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275708.132 DEBUG    lxc_cgmanager - cgmanager.c:cgm_dbus_connect:152 - Failed opening dbus connection: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /sys/fs/cgroup/cgmanager/sock: Connection refused
            lxc 1453275708.132 ERROR    lxc_cgmanager - cgmanager.c:do_cgm_get:872 - Error connecting to cgroup manager
            lxc 1453275708.135 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275708.147 DEBUG    lxc_cgmanager - cgmanager.c:cgm_dbus_connect:152 - Failed opening dbus connection: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /sys/fs/cgroup/cgmanager/sock: Connection refused
            lxc 1453275708.148 ERROR    lxc_cgmanager - cgmanager.c:do_cgm_get:872 - Error connecting to cgroup manager
            lxc 1453275708.149 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275708.157 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275708.157 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275708.162 DEBUG    lxc_cgmanager - cgmanager.c:cgm_dbus_connect:152 - Failed opening dbus connection: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /sys/fs/cgroup/cgmanager/sock: Connection refused
            lxc 1453275708.162 ERROR    lxc_cgmanager - cgmanager.c:do_cgm_get:872 - Error connecting to cgroup manager
            lxc 1453275708.163 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275743.803 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275743.803 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275743.806 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275743.806 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275743.808 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275743.812 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275743.814 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275789.891 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275789.891 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275789.895 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275789.898 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275800.962 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275800.962 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275800.966 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275800.969 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275808.977 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275808.977 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275808.981 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275808.984 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275808.989 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275808.989 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275808.992 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275808.996 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275809.021 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275809.022 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 9
            lxc 1453275809.023 INFO     lxc_container - lxccontainer.c:do_lxcapi_start:712 - Attempting to set proc title to [lxc monitor] /var/lib/lxd/containers my-ubuntu
            lxc 1453275809.023 ERROR    lxc_utils - utils.c:setproctitle:1455 - Invalid argument - setting cmdline failed
            lxc 1453275809.024 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 9
            lxc 1453275809.024 INFO     lxc_lsm - lsm/lsm.c:lsm_init:48 - LSM security driver AppArmor
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .reject_force_umount  # comment this to allow umount -f;  not recommended.
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for reject_force_umount action 0
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:do_resolve_add_rule:216 - Setting seccomp rule to reject force umounts


            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for reject_force_umount action 0
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:do_resolve_add_rule:216 - Setting seccomp rule to reject force umounts


            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .[all].
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .kexec_load errno 1.
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for kexec_load action 327681
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for kexec_load action 327681
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .open_by_handle_at errno 1.
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for open_by_handle_at action 327681
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for open_by_handle_at action 327681
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .init_module errno 1.
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for init_module action 327681
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for init_module action 327681
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .finit_module errno 1.
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for finit_module action 327681
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for finit_module action 327681
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .delete_module errno 1.
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for delete_module action 327681
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for delete_module action 327681
            lxc 1453275809.024 INFO     lxc_seccomp - seccomp.c:parse_config_v2:436 - Merging in the compat seccomp ctx into the main one
            lxc 1453275809.024 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/bin/lxd callhook /var/lib/lxd 1 start' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275809.025 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 9
            lxc 1453275809.025 INFO     lxc_monitor - monitor.c:lxc_monitor_sock_name:178 - using monitor sock name lxc/d78a9d7e97b4b375//var/lib/lxd/containers
            lxc 1453275809.026 ERROR    lxc_monitor - monitor.c:lxc_monitor_open:209 - connect : backing off 10
            lxc 1453275809.092 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275809.092 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275809.092 DEBUG    lxc_start - start.c:setup_signal_fd:278 - sigchild handler set
            lxc 1453275809.092 INFO     lxc_start - start.c:lxc_init:474 - 'my-ubuntu' is initialized
            lxc 1453275809.093 DEBUG    lxc_start - start.c:__lxc_start:1186 - Not dropping cap_sys_boot or watching utmp
            lxc 1453275809.094 INFO     lxc_start - start.c:resolve_clone_flags:883 - Cloning a new user namespace
            lxc 1453275809.098 DEBUG    lxc_conf - conf.c:instantiate_veth:2821 - instantiated veth 'vethPAKPM3/vethCGLI7E', index is '7'
            lxc 1453275809.098 INFO     lxc_cgroup - cgroup.c:cgroup_init:65 - cgroup driver cgmanager initing for my-ubuntu
            lxc 1453275809.101 INFO     lxc_cgmanager - cgmanager.c:cgm_setup_limits:1537 - cgroup limits have been setup
            lxc 1453275809.140 DEBUG    lxc_conf - conf.c:lxc_assign_network:3238 - move 'eth0' to '2353'
            lxc 1453275809.146 NOTICE   lxc_start - start.c:do_start:699 - switching to gid/uid 0 in new user namespace
            lxc 1453275809.148 DEBUG    lxc_conf - conf.c:setup_rootfs:1295 - mounted '/var/lib/lxd/containers/my-ubuntu/rootfs' on '/usr/lib/x86_64-linux-gnu/lxc'
            lxc 1453275809.148 INFO     lxc_conf - conf.c:setup_utsname:928 - 'my-ubuntu' hostname has been setup
            lxc 1453275809.160 DEBUG    lxc_conf - conf.c:setup_hw_addr:2368 - mac address '00:16:3e:f0:8d:90' on 'eth0' has been setup
            lxc 1453275809.160 DEBUG    lxc_conf - conf.c:setup_netdev:2595 - 'eth0' has been setup
            lxc 1453275809.160 INFO     lxc_conf - conf.c:setup_network:2616 - network has been setup
            lxc 1453275809.160 INFO     lxc_conf - conf.c:mount_autodev:1157 - Mounting container /dev
            lxc 1453275809.162 INFO     lxc_conf - conf.c:mount_autodev:1179 - Mounted tmpfs onto /usr/lib/x86_64-linux-gnu/lxc/dev
            lxc 1453275809.162 INFO     lxc_conf - conf.c:mount_autodev:1197 - Mounted container /dev
            lxc 1453275809.163 ERROR    lxc_utils - utils.c:safe_mount:1686 - Operation not permitted - Failed to mount proc onto /usr/lib/x86_64-linux-gnu/lxc/proc
            lxc 1453275809.163 ERROR    lxc_conf - conf.c:lxc_mount_auto_mounts:828 - Operation not permitted - error mounting proc on /usr/lib/x86_64-linux-gnu/lxc/proc flags 14
            lxc 1453275809.163 ERROR    lxc_conf - conf.c:lxc_setup:3910 - failed to setup the automatic mounts for 'my-ubuntu'
            lxc 1453275809.163 ERROR    lxc_start - start.c:do_start:731 - failed to setup the container
            lxc 1453275809.163 ERROR    lxc_sync - sync.c:__sync_wait:51 - invalid sequence number 1. expected 2
            lxc 1453275809.163 WARN     lxc_conf - conf.c:lxc_delete_network:3114 - failed to remove interface 'eth0'
            lxc 1453275809.163 ERROR    lxc_start - start.c:__lxc_start:1213 - failed to spawn 'my-ubuntu'
            lxc 1453275809.184 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/share/lxcfs/lxc.reboot.hook' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275809.687 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/bin/lxd callhook /var/lib/lxd 1 stop' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275809.806 WARN     lxc_commands - commands.c:lxc_cmd_rsp_recv:172 - command get_init_pid failed to receive response
            lxc 1453275809.806 WARN     lxc_commands - commands.c:lxc_cmd_rsp_recv:172 - command get_init_pid failed to receive response
            lxc 1453275809.807 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275809.807 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275814.805 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275814.805 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275814.808 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275814.811 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275814.811 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275814.814 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275821.079 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275821.079 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275821.083 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275821.086 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275821.092 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275821.092 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275821.095 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275821.099 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275821.122 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275821.123 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 9
            lxc 1453275821.124 INFO     lxc_container - lxccontainer.c:do_lxcapi_start:712 - Attempting to set proc title to [lxc monitor] /var/lib/lxd/containers my-ubuntu
            lxc 1453275821.124 ERROR    lxc_utils - utils.c:setproctitle:1455 - Invalid argument - setting cmdline failed
            lxc 1453275821.125 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 9
            lxc 1453275821.125 INFO     lxc_lsm - lsm/lsm.c:lsm_init:48 - LSM security driver AppArmor
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .reject_force_umount  # comment this to allow umount -f;  not recommended.
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for reject_force_umount action 0
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:do_resolve_add_rule:216 - Setting seccomp rule to reject force umounts


            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for reject_force_umount action 0
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:do_resolve_add_rule:216 - Setting seccomp rule to reject force umounts


            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .[all].
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .kexec_load errno 1.
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for kexec_load action 327681
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for kexec_load action 327681
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .open_by_handle_at errno 1.
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for open_by_handle_at action 327681
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for open_by_handle_at action 327681
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .init_module errno 1.
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for init_module action 327681
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for init_module action 327681
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .finit_module errno 1.
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for finit_module action 327681
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for finit_module action 327681
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .delete_module errno 1.
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for delete_module action 327681
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for delete_module action 327681
            lxc 1453275821.125 INFO     lxc_seccomp - seccomp.c:parse_config_v2:436 - Merging in the compat seccomp ctx into the main one
            lxc 1453275821.125 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/bin/lxd callhook /var/lib/lxd 1 start' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275821.127 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 9
            lxc 1453275821.127 INFO     lxc_monitor - monitor.c:lxc_monitor_sock_name:178 - using monitor sock name lxc/d78a9d7e97b4b375//var/lib/lxd/containers
            lxc 1453275821.148 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275821.148 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275821.148 DEBUG    lxc_start - start.c:setup_signal_fd:278 - sigchild handler set
            lxc 1453275821.148 INFO     lxc_start - start.c:lxc_init:474 - 'my-ubuntu' is initialized
            lxc 1453275821.148 DEBUG    lxc_start - start.c:__lxc_start:1186 - Not dropping cap_sys_boot or watching utmp
            lxc 1453275821.150 INFO     lxc_start - start.c:resolve_clone_flags:883 - Cloning a new user namespace
            lxc 1453275821.151 DEBUG    lxc_conf - conf.c:instantiate_veth:2821 - instantiated veth 'veth38K943/vethLSK21G', index is '9'
            lxc 1453275821.151 INFO     lxc_cgroup - cgroup.c:cgroup_init:65 - cgroup driver cgmanager initing for my-ubuntu
            lxc 1453275821.235 INFO     lxc_cgmanager - cgmanager.c:cgm_setup_limits:1537 - cgroup limits have been setup
            lxc 1453275821.260 DEBUG    lxc_conf - conf.c:lxc_assign_network:3238 - move 'eth0' to '2509'
            lxc 1453275821.266 NOTICE   lxc_start - start.c:do_start:699 - switching to gid/uid 0 in new user namespace
            lxc 1453275821.268 DEBUG    lxc_conf - conf.c:setup_rootfs:1295 - mounted '/var/lib/lxd/containers/my-ubuntu/rootfs' on '/usr/lib/x86_64-linux-gnu/lxc'
            lxc 1453275821.268 INFO     lxc_conf - conf.c:setup_utsname:928 - 'my-ubuntu' hostname has been setup
            lxc 1453275821.276 DEBUG    lxc_conf - conf.c:setup_hw_addr:2368 - mac address '00:16:3e:f0:8d:90' on 'eth0' has been setup
            lxc 1453275821.276 DEBUG    lxc_conf - conf.c:setup_netdev:2595 - 'eth0' has been setup
            lxc 1453275821.276 INFO     lxc_conf - conf.c:setup_network:2616 - network has been setup
            lxc 1453275821.276 INFO     lxc_conf - conf.c:mount_autodev:1157 - Mounting container /dev
            lxc 1453275821.276 INFO     lxc_conf - conf.c:mount_autodev:1179 - Mounted tmpfs onto /usr/lib/x86_64-linux-gnu/lxc/dev
            lxc 1453275821.276 INFO     lxc_conf - conf.c:mount_autodev:1197 - Mounted container /dev
            lxc 1453275821.277 ERROR    lxc_utils - utils.c:safe_mount:1686 - Operation not permitted - Failed to mount proc onto /usr/lib/x86_64-linux-gnu/lxc/proc
            lxc 1453275821.277 ERROR    lxc_conf - conf.c:lxc_mount_auto_mounts:828 - Operation not permitted - error mounting proc on /usr/lib/x86_64-linux-gnu/lxc/proc flags 14
            lxc 1453275821.277 ERROR    lxc_conf - conf.c:lxc_setup:3910 - failed to setup the automatic mounts for 'my-ubuntu'
            lxc 1453275821.277 ERROR    lxc_start - start.c:do_start:731 - failed to setup the container
            lxc 1453275821.277 ERROR    lxc_sync - sync.c:__sync_wait:51 - invalid sequence number 1. expected 2
            lxc 1453275821.277 WARN     lxc_conf - conf.c:lxc_delete_network:3114 - failed to remove interface 'eth0'
            lxc 1453275821.277 ERROR    lxc_start - start.c:__lxc_start:1213 - failed to spawn 'my-ubuntu'
            lxc 1453275821.304 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/share/lxcfs/lxc.reboot.hook' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275821.807 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/bin/lxd callhook /var/lib/lxd 1 stop' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275821.928 WARN     lxc_commands - commands.c:lxc_cmd_rsp_recv:172 - command get_init_pid failed to receive response
            lxc 1453275821.928 WARN     lxc_commands - commands.c:lxc_cmd_rsp_recv:172 - command get_init_pid failed to receive response
            lxc 1453275821.929 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275821.929 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275826.926 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275826.926 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275826.930 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275826.934 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275826.934 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275826.937 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275866.107 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275866.107 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275866.111 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275866.114 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275866.119 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275866.119 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275866.123 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275866.127 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275866.154 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275866.155 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 9
            lxc 1453275866.156 INFO     lxc_container - lxccontainer.c:do_lxcapi_start:712 - Attempting to set proc title to [lxc monitor] /var/lib/lxd/containers my-ubuntu
            lxc 1453275866.156 ERROR    lxc_utils - utils.c:setproctitle:1455 - Invalid argument - setting cmdline failed
            lxc 1453275866.157 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 9
            lxc 1453275866.157 INFO     lxc_lsm - lsm/lsm.c:lsm_init:48 - LSM security driver AppArmor
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .reject_force_umount  # comment this to allow umount -f;  not recommended.
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for reject_force_umount action 0
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:do_resolve_add_rule:216 - Setting seccomp rule to reject force umounts


            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for reject_force_umount action 0
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:do_resolve_add_rule:216 - Setting seccomp rule to reject force umounts


            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .[all].
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .kexec_load errno 1.
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for kexec_load action 327681
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for kexec_load action 327681
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .open_by_handle_at errno 1.
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for open_by_handle_at action 327681
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for open_by_handle_at action 327681
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .init_module errno 1.
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for init_module action 327681
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for init_module action 327681
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .finit_module errno 1.
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for finit_module action 327681
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for finit_module action 327681
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:324 - processing: .delete_module errno 1.
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:426 - Adding native rule for delete_module action 327681
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:429 - Adding compat rule for delete_module action 327681
            lxc 1453275866.157 INFO     lxc_seccomp - seccomp.c:parse_config_v2:436 - Merging in the compat seccomp ctx into the main one
            lxc 1453275866.157 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/bin/lxd callhook /var/lib/lxd 1 start' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275866.158 INFO     lxc_start - start.c:lxc_check_inherited:240 - closed inherited fd 9
            lxc 1453275866.158 INFO     lxc_monitor - monitor.c:lxc_monitor_sock_name:178 - using monitor sock name lxc/d78a9d7e97b4b375//var/lib/lxd/containers
            lxc 1453275866.158 ERROR    lxc_monitor - monitor.c:lxc_monitor_open:209 - connect : backing off 10
            lxc 1453275866.183 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275866.183 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275866.183 DEBUG    lxc_start - start.c:setup_signal_fd:278 - sigchild handler set
            lxc 1453275866.183 INFO     lxc_start - start.c:lxc_init:474 - 'my-ubuntu' is initialized
            lxc 1453275866.184 DEBUG    lxc_start - start.c:__lxc_start:1186 - Not dropping cap_sys_boot or watching utmp
            lxc 1453275866.185 INFO     lxc_start - start.c:resolve_clone_flags:883 - Cloning a new user namespace
            lxc 1453275866.186 DEBUG    lxc_conf - conf.c:instantiate_veth:2821 - instantiated veth 'vethKMCOA7/vethYFW62Y', index is '11'
            lxc 1453275866.186 INFO     lxc_cgroup - cgroup.c:cgroup_init:65 - cgroup driver cgmanager initing for my-ubuntu
            lxc 1453275866.259 INFO     lxc_cgmanager - cgmanager.c:cgm_setup_limits:1537 - cgroup limits have been setup
            lxc 1453275866.288 DEBUG    lxc_conf - conf.c:lxc_assign_network:3238 - move 'eth0' to '2642'
            lxc 1453275866.294 NOTICE   lxc_start - start.c:do_start:699 - switching to gid/uid 0 in new user namespace
            lxc 1453275866.295 DEBUG    lxc_conf - conf.c:setup_rootfs:1295 - mounted '/var/lib/lxd/containers/my-ubuntu/rootfs' on '/usr/lib/x86_64-linux-gnu/lxc'
            lxc 1453275866.295 INFO     lxc_conf - conf.c:setup_utsname:928 - 'my-ubuntu' hostname has been setup
            lxc 1453275866.308 DEBUG    lxc_conf - conf.c:setup_hw_addr:2368 - mac address '00:16:3e:f0:8d:90' on 'eth0' has been setup
            lxc 1453275866.308 DEBUG    lxc_conf - conf.c:setup_netdev:2595 - 'eth0' has been setup
            lxc 1453275866.308 INFO     lxc_conf - conf.c:setup_network:2616 - network has been setup
            lxc 1453275866.308 INFO     lxc_conf - conf.c:mount_autodev:1157 - Mounting container /dev
            lxc 1453275866.308 INFO     lxc_conf - conf.c:mount_autodev:1179 - Mounted tmpfs onto /usr/lib/x86_64-linux-gnu/lxc/dev
            lxc 1453275866.308 INFO     lxc_conf - conf.c:mount_autodev:1197 - Mounted container /dev
            lxc 1453275866.308 ERROR    lxc_utils - utils.c:safe_mount:1686 - Operation not permitted - Failed to mount proc onto /usr/lib/x86_64-linux-gnu/lxc/proc
            lxc 1453275866.308 ERROR    lxc_conf - conf.c:lxc_mount_auto_mounts:828 - Operation not permitted - error mounting proc on /usr/lib/x86_64-linux-gnu/lxc/proc flags 14
            lxc 1453275866.309 ERROR    lxc_conf - conf.c:lxc_setup:3910 - failed to setup the automatic mounts for 'my-ubuntu'
            lxc 1453275866.309 ERROR    lxc_start - start.c:do_start:731 - failed to setup the container
            lxc 1453275866.309 ERROR    lxc_sync - sync.c:__sync_wait:51 - invalid sequence number 1. expected 2
            lxc 1453275866.309 WARN     lxc_conf - conf.c:lxc_delete_network:3114 - failed to remove interface 'eth0'
            lxc 1453275866.309 ERROR    lxc_start - start.c:__lxc_start:1213 - failed to spawn 'my-ubuntu'
            lxc 1453275866.340 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/share/lxcfs/lxc.reboot.hook' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275866.843 INFO     lxc_conf - conf.c:run_script_argv:362 - Executing script '/usr/bin/lxd callhook /var/lib/lxd 1 stop' for container 'my-ubuntu', config section 'lxc'
            lxc 1453275866.965 WARN     lxc_commands - commands.c:lxc_cmd_rsp_recv:172 - command get_init_pid failed to receive response
            lxc 1453275866.965 WARN     lxc_commands - commands.c:lxc_cmd_rsp_recv:172 - command get_init_pid failed to receive response
            lxc 1453275866.965 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275866.966 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275871.963 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275871.963 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275871.967 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453275871.970 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453275871.970 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453275871.973 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453277097.024 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453277097.024 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453277097.027 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453277097.030 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453277104.551 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453277104.551 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453277104.555 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453277104.557 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453277159.523 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type u nsid 0 hostid 165536 range 65536
            lxc 1453277159.523 INFO     lxc_confile - confile.c:config_idmap:1437 - read uid map: type g nsid 0 hostid 165536 range 65536
            lxc 1453277159.527 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error
            lxc 1453277159.529 WARN     lxc_cgmanager - cgmanager.c:cgm_get:989 - do_cgm_get exited with error




```

---

### Post by MAFoElffen on 2016-01-20
Had an error posting a detailed reply... and trying to get out the door. So I'll give you the summary... 

LXD is the lite version of LXC. I run KVM, Docker and LXC on the same host.

Wrong command. Your command, based on what i do in LXC, should be:
```

sudo lxc-start -n my-ubuntu -d

```
There is also lxc-execute. See the man pages and the Ubuntu LXC Documentatiion page...

---

### Post by michael343 on 2016-01-21
Thanks for the reply MAFoElffen.

I managed to get lxc running on a previous build when I installed lxc "sudo apt-get lxc"  the lxc commands do not work with the (or my!) default 'lxd' installation/configuration.

When I try the sudo lxc-start -n myubuntu -d (which I have used with previous lxc install) on lxd I get this output:

```
sudo lxc-start -n my-ubuntu -d[sudo] password for user:
lxc-start: lxc_start.c: main: 295 Executing '/sbin/init' with no configuration file may crash the host

```

My limited understanding is that lxd has different configuration files to lxc.

So after initial response I did the following:

created a machine using lxc:
```
sudo lxc-create -t download -n u1 -- --dist ubuntu --release trusty --arch amd64
```

Started it and got an error, then tried to start it again and it is running???  But I cannot see the machine with the list commands

```

user@host:~$ sudo lxc-create -t download -n u1 -- --dist ubuntu --release trusty --arch amd64
Using image from local cache
Unpacking the rootfs


---
You just created an Ubuntu container (release=trusty, arch=amd64, variant=default)


To enable sshd, run: apt-get install openssh-server


For security reason, container images ship without user accounts
and without a root password.


Use lxc-attach or chroot directly into the rootfs to set a root password
or create user accounts.

user@host:~$ sudo lxc-start --name u1 --daemon
lxc-start: utils.c: setproctitle: 1455 Invalid argument - setting cmdline failed

user@host:~$ sudo lxc-start -n u1 -d
lxc-start: lxc_start.c: main: 279 Container is already running.

user@host:~$ lxc-ls
user@host:~$ lxc list
+-----------+---------+------+------+-----------+-----------+
|   NAME    |  STATE  | IPV4 | IPV6 | EPHEMERAL | SNAPSHOTS |
+-----------+---------+------+------+-----------+-----------+
| my-ubuntu | STOPPED |      |      | NO        |         0 |
+-----------+---------+------+------+-----------+-----------+

```

Perhaps I am better off using a standard lxc install ...

---

