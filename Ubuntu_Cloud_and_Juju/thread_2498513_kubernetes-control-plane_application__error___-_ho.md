---
title: "kubernetes-control-plane application  error   - hook failed: &quot;update-status&quot;."
date: 2024-06-17
forum: Ubuntu Cloud and Juju
---

### Post by dimitrion4a on 2024-06-17
I'm trying to deploy charmed kubernetes on a test server but kubernetes-control-plane application stays in error   - hook failed: "update-status".

syslog on container 5 shows:

Jun 17 11:24:06 juju-8761cc-5 kernel: [19916.985679] audit: type=1400 audit(1718623446.715:31852): apparmor="DENIED" operation="change_onexec" info="label not found" error=-2 profile="/snap/snapd/21759/usr/lib/snapd/snap-confine" name="snap.kubelet.hook.configure" pid=887436 comm="snap-confine"
Jun 17 11:24:07 juju-8761cc-5 kernel: [19918.095819] audit: type=1400 audit(1718623447.823:31856): apparmor="DENIED" operation="change_onexec" info="label not found" error=-2 profile="/usr/lib/snapd/snap-confine" name="snap.kubelet.daemon" pid=887510 comm="snap-confine"
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: snap.kubelet.daemon.service: Scheduled restart job, restart counter is at 144.
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: snap.kube-controller-manager.daemon.service: Scheduled restart job, restart counter is at 144.
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: snap.kube-scheduler.daemon.service: Scheduled restart job, restart counter is at 144.
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: snap.kube-apiserver.daemon.service: Scheduled restart job, restart counter is at 144.
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: snap.kube-proxy.daemon.service: Scheduled restart job, restart counter is at 144.
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: Stopped Service for snap application kube-apiserver.daemon.
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: Started Service for snap application kube-apiserver.daemon.
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: Stopped Service for snap application kube-controller-manager.daemon.
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: Started Service for snap application kube-controller-manager.daemon.
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: Stopped Service for snap application kube-proxy.daemon.
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: Started Service for snap application kube-proxy.daemon.
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: Stopped Service for snap application kube-scheduler.daemon.
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: Started Service for snap application kube-scheduler.daemon.
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: Stopped Service for snap application kubelet.daemon.
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: Started Service for snap application kubelet.daemon.
Jun 17 11:24:08 juju-8761cc-5 kubelet.daemon[16948]: missing profile snap.kubelet.daemon.
Jun 17 11:24:08 juju-8761cc-5 kubelet.daemon[16948]: Please make sure that the snapd.apparmor service is enabled and started
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: tmp-snap.rootfs_U6sH1O.mount: Deactivated successfully.
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: snap.kubelet.daemon.service: Main process exited, code=exited, status=1/FAILURE
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: snap.kubelet.daemon.service: Failed with result 'exit-code'.
Jun 17 11:24:08 juju-8761cc-5 kube-apiserver.daemon[16999]: missing profile snap-update-ns.kube-apiserver.
Jun 17 11:24:08 juju-8761cc-5 kube-apiserver.daemon[16999]: Please make sure that the snapd.apparmor service is enabled and started
Jun 17 11:24:08 juju-8761cc-5 kube-apiserver.daemon[16944]: snap-update-ns failed with code 1
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: snap.kube-apiserver.daemon.service: Main process exited, code=exited, status=1/FAILURE
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: snap.kube-apiserver.daemon.service: Failed with result 'exit-code'.
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: tmp-snap.rootfs_vcnpg0.mount: Deactivated successfully.
Jun 17 11:24:08 juju-8761cc-5 kube-scheduler.daemon[17003]: missing profile snap-update-ns.kube-scheduler.
Jun 17 11:24:08 juju-8761cc-5 kube-scheduler.daemon[17003]: Please make sure that the snapd.apparmor service is enabled and started
Jun 17 11:24:08 juju-8761cc-5 kube-scheduler.daemon[16947]: snap-update-ns failed with code 1
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: snap.kube-scheduler.daemon.service: Main process exited, code=exited, status=1/FAILURE
Jun 17 11:24:08 juju-8761cc-5 systemd[1]: snap.kube-scheduler.daemon.service: Failed with result 'exit-code'.



juju status is:


Model  Controller           Cloud/Region         Version  SLA          Timestamp
ck8s   localhost-localhost  localhost/localhost  3.5.1    unsupported  14:11:50+03:00


App                       Version  Status   Scale  Charm                     Channel        Rev  Exposed  Message
calico                    3.25.1   active       5  calico                    latest/stable  105  no       Ready
containerd                1.6.8    active       5  containerd                latest/stable   77  no       Container runtime available
easyrsa                   3.0.1    active       1  easyrsa                   latest/stable   58  no       Certificate Authority connected.
etcd                      3.4.22   active       3  etcd                      latest/stable  764  no       Healthy with 3 known peers
kubeapi-load-balancer     1.18.0   active       1  kubeapi-load-balancer     latest/stable  127  yes      Ready
kubernetes-control-plane  1.29.6   error        2  kubernetes-control-plane  latest/stable  440  no       hook failed: "update-status"
kubernetes-worker                  blocked      3  kubernetes-worker         latest/stable  216  yes      Failed to reconcile, see debug-log


Unit                         Workload  Agent  Machine  Public address  Ports         Message
easyrsa/0*                   active    idle   0        10.57.214.172                 Certificate Authority connected.
etcd/0                       active    idle   1        10.57.214.118   2379/tcp      Healthy with 3 known peers
etcd/1*                      active    idle   2        10.57.214.114   2379/tcp      Healthy with 3 known peers
etcd/2                       active    idle   3        10.57.214.229   2379/tcp      Healthy with 3 known peers
kubeapi-load-balancer/0*     active    idle   4        10.57.214.80    443,6443/tcp  Ready
kubernetes-control-plane/0*  error     idle   5        10.57.214.208   6443/tcp      hook failed: "update-status"
  calico/3                   active    idle            10.57.214.208                 Ready
  containerd/3               active    idle            10.57.214.208                 Container runtime available
kubernetes-control-plane/1   error     idle   6        10.57.214.10                  hook failed: "update-status"
  calico/4                   active    idle            10.57.214.10                  Ready
  containerd/4               active    idle            10.57.214.10                  Container runtime available
kubernetes-worker/0*         blocked   idle   7        10.57.214.9     80,443/tcp    Failed to reconcile, see debug-log
  calico/1*                  active    idle            10.57.214.9                   Ready
  containerd/1*              active    idle            10.57.214.9                   Container runtime available
kubernetes-worker/1          blocked   idle   8        10.57.214.144   80,443/tcp    Failed to reconcile, see debug-log
  calico/2                   active    idle            10.57.214.144                 Ready
  containerd/2               active    idle            10.57.214.144                 Container runtime available
kubernetes-worker/2          blocked   idle   9        10.57.214.111   80,443/tcp    Failed to reconcile, see debug-log
  calico/0                   active    idle            10.57.214.111                 Ready
  containerd/0               active    idle            10.57.214.111                 Container runtime available


Machine  State    Address        Inst id        Base          AZ  Message
0        started  10.57.214.172  juju-8761cc-0  ubuntu@22.04      Running
1        started  10.57.214.118  juju-8761cc-1  ubuntu@22.04      Running
2        started  10.57.214.114  juju-8761cc-2  ubuntu@22.04      Running
3        started  10.57.214.229  juju-8761cc-3  ubuntu@22.04      Running
4        started  10.57.214.80   juju-8761cc-4  ubuntu@22.04      Running
5        started  10.57.214.208  juju-8761cc-5  ubuntu@22.04      Running
6        started  10.57.214.10   juju-8761cc-6  ubuntu@22.04      Running
7        started  10.57.214.9    juju-8761cc-7  ubuntu@22.04      Running
8        started  10.57.214.144  juju-8761cc-8  ubuntu@22.04      Running
9        started  10.57.214.111  juju-8761cc-9  ubuntu@22.04      Running

---

### Post by currentshaft on 2024-06-18
"Please make sure that the snapd.apparmor service is enabled and started"

Did you try doing that?

---

### Post by dimitrion4a on 2024-06-21
snapd.apparmor is enabled but not starting:


root@juju-65b80e-5:~# systemctl status snapd.apparmor 
&#9679; snapd.apparmor.service - Load AppArmor profiles managed internally by snapd
     Loaded: loaded (/lib/systemd/system/snapd.apparmor.service; enabled; vendor preset: enabled)
     Active: active (exited) since Fri 2024-06-21 16:35:35 UTC; 6s ago
    Process: 48787 ExecStart=/usr/lib/snapd/snapd-apparmor start (code=exited, status=0/SUCCESS)
   Main PID: 48787 (code=exited, status=0/SUCCESS)
        CPU: 19ms


Jun 21 16:35:35 juju-65b80e-5 systemd[1]: snapd.apparmor.service: Deactivated successfully.
Jun 21 16:35:35 juju-65b80e-5 systemd[1]: Stopped Load AppArmor profiles managed internally by snapd.
Jun 21 16:35:35 juju-65b80e-5 systemd[1]: Stopping Load AppArmor profiles managed internally by snapd...
Jun 21 16:35:35 juju-65b80e-5 systemd[1]: Starting Load AppArmor profiles managed internally by snapd...
Jun 21 16:35:35 juju-65b80e-5 snapd-apparmor[48787]: main.go:166: Inside container environment without internal policy
Jun 21 16:35:35 juju-65b80e-5 systemd[1]: Finished Load AppArmor profiles managed internally by snapd.

In syslog on container :

Jun 21 14:43:01 juju-65b80e-5 apparmor.systemd[183]: Not starting AppArmor in container
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Starting Set console font and keymap...
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Starting Create final runtime dir for shutdown pivot root...
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Starting Tell Plymouth To Write Out Runtime Data...
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Condition check resulted in Show Plymouth Boot Screen being skipped.
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Started Dispatch Password Requests to Console Directory Watch.
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Condition check resulted in Forward Password Requests to Plymouth Directory Watch being skipped.
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Reached target Local Encrypted Volumes.
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Starting Set Up Additional Binary Formats...
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Condition check resulted in Store a System Token in an EFI Variable being skipped.
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Condition check resulted in Commit a transient machine-id on disk being skipped.
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Starting Create Volatile Files and Directories...
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Starting Uncomplicated firewall...
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Finished Load AppArmor profiles.
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Finished Set console font and keymap.
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Finished Create final runtime dir for shutdown pivot root.
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Finished Tell Plymouth To Write Out Runtime Data.
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Finished Set Up Additional Binary Formats.
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Finished Create Volatile Files and Directories.
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Finished Uncomplicated firewall.
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Starting Load AppArmor profiles managed internally by snapd...
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Condition check resulted in Network Time Synchronization being skipped.
Jun 21 14:43:01 juju-65b80e-5 systemd[1]: Reached target System Time Set.
Jun 21 14:43:01 juju-65b80e-5 snapd-apparmor[554]: main.go:166: Inside container environment without internal policy

---

### Post by dimitrion4a on 2024-06-22
Solved with :
apparmor_parser --add /var/lib/snap/apparmor/profiles/*

---

