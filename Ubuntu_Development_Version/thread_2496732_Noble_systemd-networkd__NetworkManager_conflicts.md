---
title: "Noble systemd-networkd / NetworkManager conflicts ?"
date: 2024-04-10
forum: Ubuntu Development Version
---

### Post by bert.ram.aerts on 2024-04-10
During boot of Noble (upgraded from Mantic to Noble yesterday evening), time is lost due to systemd-networkd-wait-online.service that can not be started.
When I try it after system is booted, I get:

```
bertxfce@legion5ubuntu:~$ sudo systemctl restart systemd-networkd-wait-online.service
Job for systemd-networkd-wait-online.service failed because the control process exited with error code.
See "systemctl status systemd-networkd-wait-online.service" and "journalctl -xeu systemd-networkd-wait-online.service" for details.

bertxfce@legion5ubuntu:~$ sudo systemctl status systemd-networkd-wait-online.service
× systemd-networkd-wait-online.service - Wait for Network to be Configured
     Loaded: loaded (/etc/systemd/system/systemd-networkd-wait-online.service; enabled; preset: enabled)
    Drop-In: /etc/systemd/system/systemd-networkd-wait-online.service.d
             &#9492;&#9472;override.conf
     Active: failed (Result: exit-code) since Wed 2024-04-10 11:44:56 CEST; 1min 14s ago
   Duration: 8min 47.138s
       Docs: man:systemd-networkd-wait-online.service(8)
    Process: 24047 ExecStart=/lib/systemd/systemd-networkd-wait-online (code=exited, status=1/FAILURE)
   Main PID: 24047 (code=exited, status=1/FAILURE)
        CPU: 3ms

apr 10 11:42:56 legion5ubuntu systemd[1]: Starting systemd-networkd-wait-online.service - Wait for Network to be Configured...
apr 10 11:44:56 legion5ubuntu systemd-networkd-wait-online[24047]: Timeout occurred while waiting for network connectivity.
apr 10 11:44:56 legion5ubuntu systemd[1]: systemd-networkd-wait-online.service: Main process exited, code=exited, status=1/FAILURE
apr 10 11:44:56 legion5ubuntu systemd[1]: systemd-networkd-wait-online.service: Failed with result 'exit-code'.
apr 10 11:44:56 legion5ubuntu systemd[1]: Failed to start systemd-networkd-wait-online.service - Wait for Network to be Configured.
bertxfce@legion5ubuntu:~$ 

bertxfce@legion5ubuntu:~$ ifconfig
enp7s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.129.11  netmask 255.255.254.0  broadcast 192.168.129.255
        inet6 fe80::eef7:94bb:8d2f:da2c  prefixlen 64  scopeid 0x20<link>
        inet6 2a02:a03f:e32e:7701:9897:adf3:9a1:55c3  prefixlen 64  scopeid 0x0<global>
        inet6 2a02:a03f:e32e:7701:909d:bb6:d667:796f  prefixlen 64  scopeid 0x0<global>
        ether 8c:8c:aa:ff:c2:8f  txqueuelen 1000  (Ethernet)
        RX packets 944242  bytes 878658165 (878.6 MB)
        RX errors 0  dropped 9244  overruns 0  frame 0
        TX packets 680925  bytes 430961862 (430.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 34873  bytes 126152812 (126.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 34873  bytes 126152812 (126.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

vmnet1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.131.1  netmask 255.255.255.0  broadcast 192.168.131.255
        inet6 fe80::250:56ff:fec0:1  prefixlen 64  scopeid 0x20<link>
        ether 00:50:56:c0:00:01  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 88  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

vmnet8: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.154.1  netmask 255.255.255.0  broadcast 192.168.154.255
        inet6 fe80::250:56ff:fec0:8  prefixlen 64  scopeid 0x20<link>
        inet6 fd15:4ba5:5a2b:1008:6d2c:8a32:71c4:5d0  prefixlen 64  scopeid 0x0<global>
        inet6 fd15:4ba5:5a2b:1008:250:56ff:fec0:8  prefixlen 64  scopeid 0x0<global>
        ether 00:50:56:c0:00:08  txqueuelen 1000  (Ethernet)
        RX packets 280  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 116  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp0s20f3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.129.2  netmask 255.255.254.0  broadcast 192.168.129.255
        inet6 2a02:a03f:e32e:7701:c18f:fe64:7c13:ed  prefixlen 64  scopeid 0x0<global>
        inet6 2a02:a03f:e32e:7701:11a0:1de5:dd44:bc6f  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::d73a:68b1:f454:960f  prefixlen 64  scopeid 0x20<link>
        ether 38:fc:98:61:2b:3c  txqueuelen 1000  (Ethernet)
        RX packets 330967  bytes 405816033 (405.8 MB)
        RX errors 0  dropped 111  overruns 0  frame 0
        TX packets 152781  bytes 26952255 (26.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

bertxfce@legion5ubuntu:~$ systemctl list-dependencies --reverse systemd-networkd-wait-online.service
systemd-networkd-wait-online.service
&#9679; &#9492;&#9472;network-online.target
&#9675;   &#9500;&#9472;cloud-config.service
&#9679;   &#9500;&#9472;cups-browsed.service
&#9679;   &#9500;&#9472;hddtemp.service
&#9679;   &#9500;&#9472;media-NASdata.mount
&#9679;   &#9500;&#9472;media-NASsoftwareLinux.mount
&#9679;   &#9500;&#9472;media-NASsoftwareWindows.mount
&#9679;   &#9500;&#9472;media-NASvideos.mount
&#9679;   &#9500;&#9472;nordvpnd.service
&#9679;   &#9500;&#9472;rpc-statd-notify.service
&#9679;   &#9500;&#9472;vmware.service
&#9675;   &#9492;&#9472;whoopsie.service

```

What can be wrong?

Why do I get "link  is not managed by networkd." here below ?

```

bertxfce@legion5ubuntu:~$  SYSTEMD_LOG_LEVEL=debug /lib/systemd/systemd-networkd-wait-online --timeout=5 --any
Found link lo(1)
Found link enp7s0(2)
Found link wlp0s20f3(3)
Found link vmnet1(4)
Found link vmnet8(5)
wlp0s20f3: link is not managed by networkd.
vmnet1: link is not managed by networkd.
vmnet8: link is not managed by networkd.
lo: link is ignored
enp7s0: link is not managed by networkd.

```

If I check NetworkManager, it is also active !

```

 bertxfce@legion5ubuntu:~$ sudo systemctl status NetworkManager
&#9679; NetworkManager.service - Network Manager
     Loaded: loaded (/usr/lib/systemd/system/NetworkManager.service; enabled; preset: enabled)
     Active: active (running) since Wed 2024-04-10 10:17:21 CEST; 23h ago
       Docs: man:NetworkManager(8)
   Main PID: 1569 (NetworkManager)
      Tasks: 4 (limit: 38319)
     Memory: 12.9M (peak: 35.6M swap: 92.0K swap peak: 100.0K)
        CPU: 23.809s
     CGroup: /system.slice/NetworkManager.service
             &#9492;&#9472;1569 /usr/sbin/NetworkManager --no-daemon

apr 11 06:19:34 legion5ubuntu NetworkManager[1569]: <info>  [1712809174.3700] dhcp4 (wlp0s20f3): state changed new lease, address=192.168>
apr 11 06:19:35 legion5ubuntu NetworkManager[1569]: <info>  [1712809175.5709] dhcp4 (enp7s0): state changed new lease, address=192.168.12>
apr 11 07:19:34 legion5ubuntu NetworkManager[1569]: <info>  [1712812774.3628] dhcp4 (wlp0s20f3): state changed new lease, address=192.168>
apr 11 07:19:35 legion5ubuntu NetworkManager[1569]: <info>  [1712812775.5709] dhcp4 (enp7s0): state changed new lease, address=192.168.12>
apr 11 08:19:34 legion5ubuntu NetworkManager[1569]: <info>  [1712816374.3712] dhcp4 (wlp0s20f3): state changed new lease, address=192.168>
apr 11 08:19:35 legion5ubuntu NetworkManager[1569]: <info>  [1712816375.5708] dhcp4 (enp7s0): state changed new lease, address=192.168.12>
apr 11 09:19:34 legion5ubuntu NetworkManager[1569]: <info>  [1712819974.3701] dhcp4 (wlp0s20f3): state changed new lease, address=192.168>
apr 11 09:19:35 legion5ubuntu NetworkManager[1569]: <info>  [1712819975.5703] dhcp4 (enp7s0): state changed new lease, address=192.168.12>
apr 11 09:38:27 legion5ubuntu NetworkManager[1569]: <info>  [1712821107.9215] policy: set 'WiFi-2.4-0C28' (wlp0s20f3) as default for IPv6>
apr 11 09:38:28 legion5ubuntu NetworkManager[1569]: <info>  [1712821108.4721] policy: set 'Wired connection 1' (enp7s0) as default for IP>

```

So should one of them be disabled? Google search on this issue shows that in Fedora systemd-networkd is not used anymore, only NetworkManager.

Is this also the case for Ubuntu 24.04 Noble ?

---

### Post by bert.ram.aerts on 2024-04-11
I disabled systemd-networkd as follows:

```

sudo systemctl disable systemd-networkd.service
sudo systemctl mask systemd-networkd.service
sudo systemctl stop systemd-networkd.service

sudo systemctl disable systemd-networkd-wait-online.service
sudo systemctl mask systemd-networkd-wait-online.service
sudo systemctl stop systemd-networkd-wait-online.service

```

And networking works well, without issues / lost time at boot time.

---

