---
title: "minikube start --vm-driver=none, not working"
date: 2022-10-18
forum: Server Platforms
---

### Post by m.eraj1995 on 2022-10-18
I am installing minikube , after installed, getting error while i start minikube, Meraj# minikube start --vm-driver=none, not working,
Below is mentioned log of minikube,
```

* 
* ==> Audit <==
* |---------|------------------|----------|------|---------|---------------------|----------|
| Command |       Args       | Profile  | User | Version |     Start Time      | End Time |
|---------|------------------|----------|------|---------|---------------------|----------|
| start   | --vm-driver=none | minikube | root | v1.27.1 | 18 Oct 22 08:48 UTC |          |
|---------|------------------|----------|------|---------|---------------------|----------|


* 
* ==> Last Start <==
* Log file created at: 2022/10/18 08:48:39
Running on machine: ip-172-31-1-60
Binary: Built with gc go1.19.1 for linux/amd64
Log line format: [IWEF]mmdd hh:mm:ss.uuuuuu threadid file:line] msg
I1018 08:48:39.278802    6343 out.go:296] Setting OutFile to fd 1 ...
I1018 08:48:39.278991    6343 out.go:343] TERM=xterm,COLORTERM=, which probably does not support color
I1018 08:48:39.278997    6343 out.go:309] Setting ErrFile to fd 2...
I1018 08:48:39.279003    6343 out.go:343] TERM=xterm,COLORTERM=, which probably does not support color
I1018 08:48:39.279095    6343 root.go:333] Updating PATH: /root/.minikube/bin
W1018 08:48:39.279206    6343 root.go:310] Error reading config file at /root/.minikube/config/config.json: open /root/.minikube/config/config.json: no such file or directory
I1018 08:48:39.279618    6343 out.go:303] Setting JSON to false
I1018 08:48:39.280428    6343 start.go:116] hostinfo: {"hostname":"ip-172-31-1-60","uptime":696,"bootTime":1666082224,"procs":165,"os":"linux","platform":"ubuntu","platformFamily":"debian","platformVersion":"22.04","kernelVersion":"5.15.0-1019-aws","kernelArch":"x86_64","virtualizationSystem":"xen","virtualizationRole":"guest","hostId":"ec237a45-78ab-a4e5-6171-15aaa95b6528"}
I1018 08:48:39.280492    6343 start.go:126] virtualization: xen guest
I1018 08:48:39.283991    6343 out.go:177] * minikube v1.27.1 on Ubuntu 22.04 (xen/amd64)
W1018 08:48:39.286087    6343 preload.go:295] Failed to list preload files: open /root/.minikube/cache/preloaded-tarball: no such file or directory
I1018 08:48:39.286108    6343 notify.go:220] Checking for updates...
I1018 08:48:39.286142    6343 driver.go:362] Setting default libvirt URI to qemu:///system
I1018 08:48:39.288448    6343 out.go:177] * Using the none driver based on user configuration
I1018 08:48:39.290494    6343 start.go:282] selected driver: none
I1018 08:48:39.290501    6343 start.go:808] validating driver "none" against <nil>
I1018 08:48:39.290515    6343 start.go:819] status for none: {Installed:true Healthy:true Running:false NeedsImprovement:false Error:<nil> Reason: Fix: Doc: Version:}
I1018 08:48:39.290541    6343 start.go:1568] auto setting extra-config to "kubelet.resolv-conf=/run/systemd/resolve/resolv.conf".
I1018 08:48:39.290790    6343 start_flags.go:303] no existing cluster config was found, will generate one from the flags 
I1018 08:48:39.291238    6343 start_flags.go:384] Using suggested 6000MB memory alloc based on sys=32102MB, container=0MB
I1018 08:48:39.291375    6343 start_flags.go:867] Wait components to verify : map[apiserver:true system_pods:true]
I1018 08:48:39.291388    6343 cni.go:95] Creating CNI manager for ""
I1018 08:48:39.291395    6343 cni.go:149] Driver none used, CNI unnecessary in this configuration, recommending no CNI
I1018 08:48:39.291402    6343 start_flags.go:317] config:
{Name:minikube KeepContext:false EmbedCerts:false MinikubeISO: KicBaseImage:gcr.io/k8s-minikube/kicbase:v0.0.35@sha256:e6f9b2700841634f3b94907f9cfa6785ca4409ef8e428a0322c1781e809d311b Memory:6000 CPUs:2 DiskSize:20000 VMDriver: Driver:none HyperkitVpnKitSock: HyperkitVSockPorts:[] DockerEnv:[] ContainerVolumeMounts:[] InsecureRegistry:[] RegistryMirror:[] HostOnlyCIDR:192.168.59.1/24 HypervVirtualSwitch: HypervUseExternalSwitch:false HypervExternalAdapter: KVMNetwork:default KVMQemuURI:qemu:///system KVMGPU:false KVMHidden:false KVMNUMACount:1 APIServerPort:0 DockerOpt:[] DisableDriverMounts:false NFSShare:[] NFSSharesRoot:/nfsshares UUID: NoVTXCheck:false DNSProxy:false HostDNSResolver:true HostOnlyNicType:virtio NatNicType:virtio SSHIPAddress: SSHUser:root SSHKey: SSHPort:22 KubernetesConfig:{KubernetesVersion:v1.25.2 ClusterName:minikube Namespace:default APIServerName:minikubeCA APIServerNames:[] APIServerIPs:[] DNSDomain:cluster.local ContainerRuntime:docker CRISocket: NetworkPlugin: FeatureGates: ServiceCIDR:10.96.0.0/12 ImageRepository: LoadBalancerStartIP: LoadBalancerEndIP: CustomIngressCert: RegistryAliases: ExtraOptions:[{Component:kubelet Key:resolv-conf Value:/run/systemd/resolve/resolv.conf}] ShouldLoadCachedImages:false EnableDefaultCNI:false CNI: NodeIP: NodePort:8443 NodeName:} Nodes:[] Addons:map[] CustomAddonImages:map[] CustomAddonRegistries:map[] VerifyComponents:map[apiserver:true system_pods:true] StartHostTimeout:6m0s ScheduledStop:<nil> ExposedPorts:[] ListenAddress: Network: Subnet: MultiNodeRequested:false ExtraDisks:0 CertExpiration:26280h0m0s Mount:false MountString:/root:/minikube-host Mount9PVersion:9p2000.L MountGID:docker MountIP: MountMSize:262144 MountOptions:[] MountPort:0 MountType:9p MountUID:docker BinaryMirror: DisableOptimizations:false DisableMetrics:false CustomQemuFirmwarePath: SocketVMnetClientPath:/opt/socket_vmnet/bin/socket_vmnet_client SocketVMnetPath:/var/run/socket_vmnet}
I1018 08:48:39.295452    6343 out.go:177] * Starting control plane node minikube in cluster minikube
I1018 08:48:39.297950    6343 profile.go:148] Saving config to /root/.minikube/profiles/minikube/config.json ...
I1018 08:48:39.297971    6343 lock.go:35] WriteFile acquiring /root/.minikube/profiles/minikube/config.json: {Name:mk270d1b5db5965f2dc9e9e25770a63417031943 Clock:{} Delay:500ms Timeout:1m0s Cancel:<nil>}
I1018 08:48:39.298269    6343 cache.go:208] Successfully downloaded all kic artifacts
I1018 08:48:39.298290    6343 start.go:364] acquiring machines lock for minikube: {Name:mkc8ab01ad3ea83211c505c81a7ee49a8e3ecb89 Clock:{} Delay:500ms Timeout:13m0s Cancel:<nil>}
I1018 08:48:39.298391    6343 start.go:368] acquired machines lock for "minikube" in 83.6µs
I1018 08:48:39.298412    6343 start.go:93] Provisioning new machine with config: &{Name:minikube KeepContext:false EmbedCerts:false MinikubeISO: KicBaseImage:gcr.io/k8s-minikube/kicbase:v0.0.35@sha256:e6f9b2700841634f3b94907f9cfa6785ca4409ef8e428a0322c1781e809d311b Memory:6000 CPUs:2 DiskSize:20000 VMDriver: Driver:none HyperkitVpnKitSock: HyperkitVSockPorts:[] DockerEnv:[] ContainerVolumeMounts:[] InsecureRegistry:[] RegistryMirror:[] HostOnlyCIDR:192.168.59.1/24 HypervVirtualSwitch: HypervUseExternalSwitch:false HypervExternalAdapter: KVMNetwork:default KVMQemuURI:qemu:///system KVMGPU:false KVMHidden:false KVMNUMACount:1 APIServerPort:0 DockerOpt:[] DisableDriverMounts:false NFSShare:[] NFSSharesRoot:/nfsshares UUID: NoVTXCheck:false DNSProxy:false HostDNSResolver:true HostOnlyNicType:virtio NatNicType:virtio SSHIPAddress: SSHUser:root SSHKey: SSHPort:22 KubernetesConfig:{KubernetesVersion:v1.25.2 ClusterName:minikube Namespace:default APIServerName:minikubeCA APIServerNames:[] APIServerIPs:[] DNSDomain:cluster.local ContainerRuntime:docker CRISocket: NetworkPlugin: FeatureGates: ServiceCIDR:10.96.0.0/12 ImageRepository: LoadBalancerStartIP: LoadBalancerEndIP: CustomIngressCert: RegistryAliases: ExtraOptions:[{Component:kubelet Key:resolv-conf Value:/run/systemd/resolve/resolv.conf}] ShouldLoadCachedImages:false EnableDefaultCNI:false CNI: NodeIP: NodePort:8443 NodeName:} Nodes:[{Name:m01 IP: Port:8443 KubernetesVersion:v1.25.2 ContainerRuntime:docker ControlPlane:true Worker:true}] Addons:map[] CustomAddonImages:map[] CustomAddonRegistries:map[] VerifyComponents:map[apiserver:true system_pods:true] StartHostTimeout:6m0s ScheduledStop:<nil> ExposedPorts:[] ListenAddress: Network: Subnet: MultiNodeRequested:false ExtraDisks:0 CertExpiration:26280h0m0s Mount:false MountString:/root:/minikube-host Mount9PVersion:9p2000.L MountGID:docker MountIP: MountMSize:262144 MountOptions:[] MountPort:0 MountType:9p MountUID:docker BinaryMirror: DisableOptimizations:false DisableMetrics:false CustomQemuFirmwarePath: SocketVMnetClientPath:/opt/socket_vmnet/bin/socket_vmnet_client SocketVMnetPath:/var/run/socket_vmnet} &{Name:m01 IP: Port:8443 KubernetesVersion:v1.25.2 ContainerRuntime:docker ControlPlane:true Worker:true}
I1018 08:48:39.298480    6343 start.go:125] createHost starting for "m01" (driver="none")
I1018 08:48:39.301104    6343 out.go:177] * Running on localhost (CPUs=8, Memory=32102MB, Disk=7755MB) ...
I1018 08:48:39.303405    6343 exec_runner.go:51] Run: systemctl --version
I1018 08:48:39.305437    6343 start.go:159] libmachine.API.Create for "minikube" (driver="none")
I1018 08:48:39.305473    6343 client.go:168] LocalClient.Create starting
I1018 08:48:39.305558    6343 main.go:134] libmachine: Creating CA: /root/.minikube/certs/ca.pem
I1018 08:48:39.692549    6343 main.go:134] libmachine: Creating client certificate: /root/.minikube/certs/cert.pem
I1018 08:48:39.828528    6343 client.go:171] LocalClient.Create took 523.049229ms
I1018 08:48:39.828562    6343 start.go:167] duration metric: libmachine.API.Create for "minikube" took 523.127101ms
I1018 08:48:39.828568    6343 start.go:300] post-start starting for "minikube" (driver="none")
I1018 08:48:39.832975    6343 out.go:177] 
W1018 08:48:39.836762    6343 out.go:239] * Exiting due to NOT_FOUND_CRI_DOCKERD: 


W1018 08:48:39.836949    6343 out.go:239] * Suggestion: 


    The none driver with Kubernetes v1.24+ and the docker container-runtime requires cri-dockerd.
    
    Please install cri-dockerd using these instructions:
    
    [https://github.com/Mirantis/cri-dockerd#build-and-install](https://github.com/Mirantis/cri-dockerd#build-and-install)
I1018 08:48:39.840101    6343 out.go:177] 


*
```

---

### Post by MAFoElffen on 2022-10-18
In the 'minicube' docs:
[qoute]
Required: Container or virtual machine manager, such as: [Docker]("https://minikube.sigs.k8s.io/docs/drivers/docker/"), [Hyperkit]("https://minikube.sigs.k8s.io/docs/drivers/hyperkit/"), [Hyper-V]("https://minikube.sigs.k8s.io/docs/drivers/hyperv/"), [KVM]("https://minikube.sigs.k8s.io/docs/drivers/kvm2/"), [Parallels]("https://minikube.sigs.k8s.io/docs/drivers/parallels/"), [Podman]("https://minikube.sigs.k8s.io/docs/drivers/podman/"), [VirtualBox]("https://minikube.sigs.k8s.io/docs/drivers/virtualbox/"), or [VMware Fusion/Workstation]("https://minikube.sigs.k8s.io/docs/drivers/vmware/")
[/quote]
So that the only valid option for "--vmdriver=xxxx" is:
```

* virtualbox
* vmwarefusion
* kvm2
* kvm 
* hyperkit 

```
The error is telling you that if no argument is given, then it uses drivers for kubernetes and dockerd...

What is the result of
```

awk '{print $0}'  ~/.minikube/machines/minikube/config.json 

```

---

