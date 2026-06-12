---
title: "Ubuntu 16.04 LTS + LXD/LXC + Manually bridge"
date: 2016-05-04
forum: Virtualisation
---

### Post by responder2 on 2016-05-04
Hi all,

I encountered a problem when I tried to launch a container w/ existing bridge 
device on 16.04 LTS & surprising didn't find any similar case from the Google.  : (

The following is how I configured my unit and hopefully someone can point out
the parts I missed. Thanks in advance.

PS. the container can startup correctly if I used lxd-brigde (lxdbr0).

After a clean 16.04 server LTS installation, I choosed to use the existing bridge (bond0).
```
sudo lxc init
```

My interface setting : /etc/network/interfaces
```
auto eno1
iface eno1 inet manual
    bond-master bond0


auto eno2
iface eno2 inet manual
    bond-master bond0


auto bond0
iface bond0 inet static
    address 192.168.223.110
    netmask 255.255.255.0
    bond-mode 802.3ad
    bond-miimon 100
    bond-lacp-rate 1
    bond-slaves none
```

The bond0 was confirmed to start up correctly.
```
bond0     Link encap:Ethernet  HWaddr 14:18:77:61:ac:02            inet addr:192.168.223.110  Bcast:192.168.223.255  Mask:255.255.255.0
          inet6 addr: fe80::1618:77ff:fe61:ac02/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:74418 errors:0 dropped:8 overruns:0 frame:0
          TX packets:671 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7667798 (7.6 MB)  TX bytes:66211 (66.2 KB)
```

Then I tried to launch a new container but it failed w/ error message.
```

root@LXD00:~# lxc launch "images:debian/jessie/amd64" JessieDev
Creating JessieDev
Starting JessieDev
error: Error calling 'lxd forkstart JessieDev /var/lib/lxd/containers /var/log/lxd/JessieDev/lxc.conf': err='exit status 1'
Try `lxc info --show-log JessieDev` for more info
```

Log as following.
```

root@LXD00:~# lxc info --show-log JessieDev
Name: JessieDev
Architecture: x86_64
Created: 2016/05/04 03:41 UTC
Status: Stopped
Type: persistent
Profiles: default


Log:


            lxc 20160504114119.249 INFO     lxc_confile - confile.c:config_idmap:1498 - read uid map: type u nsid 0 hostid 100000 range 65536
            lxc 20160504114119.249 INFO     lxc_confile - confile.c:config_idmap:1498 - read uid map: type g nsid 0 hostid 100000 range 65536
            lxc 20160504114125.682 INFO     lxc_confile - confile.c:config_idmap:1498 - read uid map: type u nsid 0 hostid 100000 range 65536
            lxc 20160504114125.682 INFO     lxc_confile - confile.c:config_idmap:1498 - read uid map: type g nsid 0 hostid 100000 range 65536
            lxc 20160504114125.698 INFO     lxc_start - start.c:lxc_check_inherited:251 - closed inherited fd 3
            lxc 20160504114125.698 INFO     lxc_start - start.c:lxc_check_inherited:251 - closed inherited fd 8
            lxc 20160504114125.701 INFO     lxc_container - lxccontainer.c:do_lxcapi_start:797 - Attempting to set proc title to [lxc monitor] /var/lib/lxd/containers JessieDev
            lxc 20160504114125.702 INFO     lxc_start - start.c:lxc_check_inherited:251 - closed inherited fd 8
            lxc 20160504114125.702 INFO     lxc_lsm - lsm/lsm.c:lsm_init:48 - LSM security driver AppArmor
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:342 - processing: .reject_force_umount  # comment this to allow umount -f;  not recommended.
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:446 - Adding native rule for reject_force_umount action 0
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:do_resolve_add_rule:216 - Setting seccomp rule to reject force umounts


            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:449 - Adding compat rule for reject_force_umount action 0
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:do_resolve_add_rule:216 - Setting seccomp rule to reject force umounts


            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:342 - processing: .[all].
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:342 - processing: .kexec_load errno 1.
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:446 - Adding native rule for kexec_load action 327681
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:449 - Adding compat rule for kexec_load action 327681
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:342 - processing: .open_by_handle_at errno 1.
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:446 - Adding native rule for open_by_handle_at action 327681
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:449 - Adding compat rule for open_by_handle_at action 327681
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:342 - processing: .init_module errno 1.
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:446 - Adding native rule for init_module action 327681
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:449 - Adding compat rule for init_module action 327681
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:342 - processing: .finit_module errno 1.
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:446 - Adding native rule for finit_module action 327681
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:449 - Adding compat rule for finit_module action 327681
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:342 - processing: .delete_module errno 1.
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:446 - Adding native rule for delete_module action 327681
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:449 - Adding compat rule for delete_module action 327681
            lxc 20160504114125.703 INFO     lxc_seccomp - seccomp.c:parse_config_v2:456 - Merging in the compat seccomp ctx into the main one
            lxc 20160504114125.703 INFO     lxc_conf - conf.c:run_script_argv:367 - Executing script '/usr/bin/lxd callhook /var/lib/lxd 9 start' for container 'JessieDev', config section 'lxc'
            lxc 20160504114125.705 INFO     lxc_start - start.c:lxc_check_inherited:251 - closed inherited fd 3
            lxc 20160504114125.705 INFO     lxc_start - start.c:lxc_check_inherited:251 - closed inherited fd 8
            lxc 20160504114125.707 INFO     lxc_monitor - monitor.c:lxc_monitor_sock_name:178 - using monitor sock name lxc/d78a9d7e97b4b375//var/lib/lxd/containers
            lxc 20160504114125.808 DEBUG    lxc_start - start.c:setup_signal_fd:289 - sigchild handler set
            lxc 20160504114125.809 DEBUG    lxc_console - console.c:lxc_console_peer_default:473 - no console peer
            lxc 20160504114125.809 INFO     lxc_start - start.c:lxc_init:488 - 'JessieDev' is initialized
            lxc 20160504114125.809 INFO     lxc_confile - confile.c:config_idmap:1498 - read uid map: type u nsid 0 hostid 100000 range 65536
            lxc 20160504114125.809 INFO     lxc_confile - confile.c:config_idmap:1498 - read uid map: type g nsid 0 hostid 100000 range 65536
            lxc 20160504114125.809 DEBUG    lxc_start - start.c:__lxc_start:1302 - Not dropping cap_sys_boot or watching utmp
            lxc 20160504114125.809 INFO     lxc_start - start.c:resolve_clone_flags:999 - Cloning a new user namespace
            lxc 20160504114125.814 ERROR    lxc_conf - conf.c:instantiate_veth:2594 - failed to attach 'vethT3MR0S' to the bridge 'bond0': Operation not permitted
            lxc 20160504114125.865 ERROR    lxc_conf - conf.c:lxc_create_network:2871 - failed to create netdev
            lxc 20160504114125.865 ERROR    lxc_start - start.c:lxc_spawn:1066 - failed to create the network
            lxc 20160504114125.865 ERROR    lxc_start - start.c:__lxc_start:1329 - failed to spawn 'JessieDev'
            lxc 20160504114125.865 INFO     lxc_conf - conf.c:run_script_argv:367 - Executing script '/usr/share/lxcfs/lxc.reboot.hook' for container 'JessieDev', config section 'lxc'
            lxc 20160504114126.368 INFO     lxc_conf - conf.c:run_script_argv:367 - Executing script '/usr/bin/lxd callhook /var/lib/lxd 9 stop' for container 'JessieDev', config section 'lxc'
            lxc 20160504114126.464 WARN     lxc_commands - commands.c:lxc_cmd_rsp_recv:172 - command get_cgroup failed to receive response
            lxc 20160504114126.464 WARN     lxc_commands - commands.c:lxc_cmd_rsp_recv:172 - command get_cgroup failed to receive response
            lxc 20160504114126.466 INFO     lxc_confile - confile.c:config_idmap:1498 - read uid map: type u nsid 0 hostid 100000 range 65536
            lxc 20160504114126.466 INFO     lxc_confile - confile.c:config_idmap:1498 - read uid map: type g nsid 0 hostid 100000 range 65536
            lxc 20160504114217.487 INFO     lxc_confile - confile.c:config_idmap:1498 - read uid map: type u nsid 0 hostid 100000 range 65536
            lxc 20160504114217.487 INFO     lxc_confile - confile.c:config_idmap:1498 - read uid map: type g nsid 0 hostid 100000 range 65536
            lxc 20160504114217.493 INFO     lxc_confile - confile.c:config_idmap:1498 - read uid map: type u nsid 0 hostid 100000 range 65536
            lxc 20160504114217.493 INFO     lxc_confile - confile.c:config_idmap:1498 - read uid map: type g nsid 0 hostid 100000 range 65536
```


I believed it failed when trying to attach the network device.
```

            lxc 20160504114125.814 ERROR    lxc_conf - conf.c:instantiate_veth:2594 - failed to attach 'vethT3MR0S' to the bridge 'bond0': Operation not permitted
            lxc 20160504114125.865 ERROR    lxc_conf - conf.c:lxc_create_network:2871 - failed to create netdev
            lxc 20160504114125.865 ERROR    lxc_start - start.c:lxc_spawn:1066 - failed to create the network
            lxc 20160504114125.865 ERROR    lxc_start - start.c:__lxc_start:1329 - failed to spawn 'JessieDev'
```

Is this an apparmor's issue (or not?). :(
```

[ 4391.555004] audit: type=1400 audit(1462333285.798:27): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lxd-JessieDev_</var/lib/lxd>" pid=4496 comm="apparmor_parser"
[ 4392.212157] audit: type=1400 audit(1462333286.454:28): apparmor="STATUS" operation="profile_remove" profile="unconfined" name="lxd-JessieDev_</var/lib/lxd>" pid=4610 comm="apparmor_parser"
```

I tried the method found on
[https://help.ubuntu.com/lts/serverguide/lxc.html#lxc-apparmor](https://help.ubuntu.com/lts/serverguide/lxc.html#lxc-apparmor)
```
[COLOR=#333333][FONT=UbuntuMono]sudo apparmor_parser -R /etc/apparmor.d/usr.bin.lxc-start
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]sudo ln -s /etc/apparmor.d/usr.bin.lxc-start /etc/apparmor.d/disabled/[/FONT][/COLOR]
```
Still got the same error.

Then I tried to replace the default aa_profile on /var/log/lxd/JessieDev/lxc.conf to
```
lxc.aa_profile = unconfined
```
But it will be changed back to the default value after I start/launch the container.
```
lxc.aa_profile = lxd-JessieDev_</var/lib/lxd>
```

That's the whole story.
Please kindly help.

Thanks a lot.

Good day.

Sincerely yours,
       Responder

---

### Post by responder2 on 2016-05-04
My bad.

I finally figured out why.

I should bridge to a '[COLOR=#ff0000]bridge[/COLOR]' device instead of a '[COLOR=#ff0000]bond[/COLOR]' one.  Orz

---

