---
title: "Setting up remote File sharing server that runs on Ubuntu (clients on Win7)"
date: 2014-01-01
forum: Server Platforms
---

### Post by stype on 2014-01-01
Hello,

I run a small company, and now we are in the phase of growing a little bit, which means we have to find a way to share files in an efficient way.

Our computers are running on Win7 platform, and we would like to have a common network drive which holds our important files (project files, and an Microsoft access database file ).

It's also important that we can access this network drive no matter where are we in the world at the moment as long as we have internet connection, so a simple LAN is not an option because it is limited to a specific location.

Dropbox (our temporary solution) is a bad solution for us since it generates conflicted copies if more users are using the database file.

What I tried to do is to set up our own dedicated remote server running an Ubuntu platform (I downloaded the newest ubuntu version, don't know the version by heart but I can look it up if needed).

On this server I have installed Softether VPN server that creates a VPN connection between the server and the client computers which are running sofether on windows.
The plan was then to set up samba which would share a folder on server HDD to all of our client computers.
I installed samba, but I can not get the server name displayed on client computers when I go in My Computer->Network.

Do I need to configure samba so that it works through this VPN interface or you would suggest something else ?
I ask this because if I connect a computer in the LAN network together with the server then I can notice this shared drive. So it means samba is working but not through the VPN !

Since this is my first excursion to linux, it's possible that I did everything in much more complicated way. 

I am willing to listen all sorts of advices and critiques are very welcome.


Thank you everyone, and yes, I wish you all
- a happy New Year !

Cheers,
Stype

---

### Post by volkswagner on 2014-01-01
I'm not familiar with Softether VPN, but when using OpenVPN I have to make special config entries to get services such as SAMBA working
behind the VPN.  Things you may look for are DNS forwarding to vpn clients and firewall rules for allowing traffic.

Can you navigate directly to the share by entering the ip address of the server?

Can you ping the SAMBA server's ip address over the VPN?

---

### Post by BlinkinCat on 2014-01-01
Hi, welcome to the forums,

Excuse my ignorance, but there is a Documentation Page titled "How to create a Network Share via Samba ....." which is shown in NewDocs under "H".

A link for NewDocs can be found in my Signature. I have no idea if this is what you are after or not!

Good luck - :)


Edit : I couldn't post a direct link to the Page as it would not work - possibly due to length of Page Title.

---

### Post by stype on 2014-01-01
I can not navigate directly to the share by entering the ip address of the server.
I can not ping the servers ip directly through the VPN.

But all of my trafic is redirected through this server. Basically when the VPN is turned on and I surf the web, I see my IP address is the same like the IP address of the servers NAT.
So the communication between my computer and the server obviously exists.

To get you a better overview of my infrastructure I tried trace route to [www.google.com](www.google.com) and here is what i get.

1) 192.168.30.1 - IP address of the VPN network of the server. (my ip on VPN is 192.168.30.10)
2) 192.168.6.1 - This is already in local LAN of the server. Servers ip is 192.168.6.140, and main router is 192.168.6.1
3) ***.***.43.9 [NAT ip address of the router] - I can write this address in PM if needed. It's interesting that I connect to ***.***.43.10:1194 as a NAT IP address, but on a trace route it goes through the ***.***.43.9... I don't know if this is meaningful in any way...
4) then I see external ip addresses on the internet further on...

So on the main router I have managed to set port forwarding on the port 1194 which enables packages for my VPN to be forwarded to the ip address 192.168.6.140.

---

### Post by stype on 2014-01-01
> **BlinkinCat said:**
> Hi, welcome to the forums,

Excuse my ignorance, but there is a Documentation Page titled "How to create a Network Share via Samba ....." which is shown in NewDocs under "H".

A link for NewDocs can be found in my Signature. I have no idea if this is what you are after or not!

Good luck - :)


Thanks. I will study this now and let me know if it helped.

---

### Post by stype on 2014-01-01
> **stype said:**
> Thanks. I will study this now and let me know if it helped.

Nope. Those are the basic instructions, which I already have followed to create samba share.
My samba works in my LAN, but not over VPN, so I guess that's a bit more complicated.

I wanted to enter VPN interface in samba config file, so first I tried entering "ip addr" command in servers terminal to get the list of interfaces. 

There I see 3 interfaces, but I don't know if the third interface is VPN. Here is a terminal copy-paste:
[FONT=courier new]stype@stypeserver:/usr/local/vpnserver$ ip addr[/FONT]
[FONT=courier new]1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN [/FONT]
[FONT=courier new]    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00[/FONT]
[FONT=courier new]    inet 127.0.0.1/8 scope host lo[/FONT]
[FONT=courier new]    inet6 ::1/128 scope host [/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]
[FONT=courier new]2: eth0: <BROADCAST,MULTICAST,PROMISC,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000[/FONT]
[FONT=courier new]    link/ether e4:11:5b:e6:25:34 brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=courier new]    inet 192.168.6.140/24 brd 192.168.6.255 scope global eth0[/FONT]
[FONT=courier new]    inet6 fe80::e611:5bff:fee6:2534/64 scope link [/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]
[FONT=courier new]3: eth1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN qlen 1000[/FONT]
[FONT=courier new]    link/ether e4:11:5b:e6:25:35 brd ff:ff:ff:ff:ff:ff[/FONT]

---

### Post by coldraven on 2014-01-01
Is this any use?
> Audience:
[INDENT] Network admins who want to connect two or more offices using an  encrypted, secure VPN over the public Internet. Clients at remote sites  will access the Internet directly through their local gateway while all  internal traffic is automatically routed via encrypted VPN links back to  the central site.
[/INDENT]

I see that it mentions having a FQDN, maybe that is what's going wrong. I'm not an expert in this field :(
[http://tuxnetworks.blogspot.co.uk/2011/05/howto-easiest-vpn-setup-ever.html](http://tuxnetworks.blogspot.co.uk/2011/05/howto-easiest-vpn-setup-ever.html)

---

### Post by volkswagner on 2014-01-01
This is not a SAMBA issue.  This is a VPN, Network, Firewall, or routing issue.

I'm not familiar with Softether VPN, so you may have better luck asking at their forums.

Is Softether VPN server running on your ubuntu file server?

You will first need to be able to ping your file server via the VPN before trying to attach shares.

What instructions did you follow at [http://www.softether.org/?](http://www.softether.org/?)

Can you ping VPN Clients from Ubuntu File Server?

You likely need to add a route in VPN config or firewall entry.

If your VPN Server is also your file server, you may need to allow SAMBA to listen on VPN interface.

From File server what is output of:
```
ifconfig
```

---

### Post by volkswagner on 2014-01-01
Did you setup vpn using Bridge mode or route mode?
Can you post your vpn server config file?

---

### Post by stype on 2014-01-01
> **volkswagner said:**
> 
This is not a SAMBA issue. This is a VPN, Network, Firewall, or routing issue.

Is Softether VPN server running on your ubuntu file server?


Yes

> **volkswagner said:**
> 
You will first need to be able to ping your file server via the VPN before trying to attach shares.

What instructions did you follow at [http://www.softether.org/?](http://www.softether.org/?)

I have found and followed this article: [https://www.digitalocean.com/community/articles/how-to-setup-a-multi-protocol-vpn-server-using-softether](https://www.digitalocean.com/community/articles/how-to-setup-a-multi-protocol-vpn-server-using-softether)

> **volkswagner said:**
> 
Can you ping VPN Clients from Ubuntu File Server?

No.

> **volkswagner said:**
> 
You likely need to add a route in VPN config or firewall entry.

If your VPN Server is also your file server, you may need to allow SAMBA to listen on VPN interface.


The only problem is that I don't see VPN interface on a list. Or you think this was the last interface I saw on IP addr command ?
> **volkswagner said:**
> 
From File server what is output of:
```
ifconfig
```

```

stype@stypeserver:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e4:11:5b:e6:25:34  
          inet addr:192.168.6.140  Bcast:192.168.6.255  Mask:255.255.255.0
          inet6 addr: fe80::e611:5bff:fee6:2534/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:1958416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1319044 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:644378810 (644.3 MB)  TX bytes:439348915 (439.3 MB)
          Interrupt:16 


eth1      Link encap:Ethernet  HWaddr e4:11:5b:e6:25:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:230571 errors:0 dropped:0 overruns:0 frame:0
          TX packets:230571 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:143884630 (143.8 MB)  TX bytes:143884630 (143.8 MB)

```

---

### Post by stype on 2014-01-01
> **volkswagner said:**
> Did you setup vpn using Bridge mode or route mode?
Can you post your vpn server config file?

Here is the code of the vpn_server.config file:
```

?# Software Configuration File
# 
# You can edit this file when the program is not working.
# 
declare root
{
    uint ConfigRevision 9
    bool IPsecMessageDisplayed false
    bool VgsMessageDisplayed false


    declare DDnsClient
    {
        bool Disabled false
        byte Key qB8Gy/M7UqLxL/6wPN8iCopmEoQ=
        string LocalHostname stypeserver
        string ProxyHostName $
        uint ProxyPort 0
        uint ProxyType 0
        string ProxyUsername $
    }


    declare IPsec
    {
        bool EtherIP_IPsec true
        string IPsec_Secret simpsons
        string L2TP_DefaultHub VPN
        bool L2TP_IPsec true
        bool L2TP_Raw true
        declare EtherIP_IDSettingsList
        {
        }
    }


    declare ListenerList
    {
        declare Listener0
        {
            bool DisableDos false
            bool Enabled true
            uint Port 443
        }
        declare Listener1
        {
            bool DisableDos false
            bool Enabled true
            uint Port 992
        }
        declare Listener2
        {
            bool DisableDos false
            bool Enabled true
            uint Port 1194
        }
        declare Listener3
        {
            bool DisableDos false
            bool Enabled true
            uint Port 5555
        }
    }


    declare LocalBridgeList
    {
    }


    declare ServerConfiguration
    {
        uint64 AutoDeleteCheckDiskFreeSpaceMin 104857600
        uint AutoSaveConfigSpan 300
        bool BackupConfigOnlyWhenModified true
        string CipherName RC4-MD5
        uint CurrentBuild 9387
        bool DisableDeadLockCheck false
        bool DisableDosProction false
        bool DisableIntelAesAcceleration false
        bool DisableIPv6Listener false
        bool DisableNatTraversal false
        bool DisableOpenVPNServer false
        bool DisableSSTPServer false
        bool DontBackupConfig false
        bool EnableVpnAzure false
        bool EnableVpnOverDns true
        bool EnableVpnOverIcmp true
        byte HashedPassword MSo0Kgy3oTteui52U0wYnF3k0Pg=
        string KeepConnectHost keepalive.softether.org
        uint KeepConnectInterval 50
        uint KeepConnectPort 80
        uint KeepConnectProtocol 1
        uint MaxConnectionsPerIP 256
        uint MaxUnestablishedConnections 1000
        bool NoHighPriorityProcess false
        bool NoLinuxArpFilter false
        bool NoSendSignature false
        string OpenVPN_UdpPortList 1194
        bool SaveDebugLog false
        byte ServerCert MIIDGDCCAgACAQAwDQYJKoZIhvcNAQEFBQAwUjEVMBMGA1UEAxMMODUuMTE0LjQzLjEwMRUwEwYDVQQKEww4NS4xMTQuNDMuMTAxFTATBgNVBAsTDDg1LjExNC40My4xMDELMAkGA1UEBhMCVVMwHhcNMTMxMjI0MTgyNzU3WhcNMzYxMjMxMTgyNzU3WjBSMRUwEwYDVQQDEww4NS4xMTQuNDMuMTAxFTATBgNVBAoTDDg1LjExNC40My4xMDEVMBMGA1UECxMMODUuMTE0LjQzLjEwMQswCQYDVQQGEwJVUzCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAMHWF8nyb8npeIsnfXAxbuXgYrIoxNFOH7XK/RkTGrmGpLbNVbH1dISNa7CD2p4ITx9P6sO7i5YC3iqiu+QNW9wycTcse76y6M4yCqp9ZsDC209IEfhvZUTaMjhnYUZzKWRm4EDC942ZVYRvgoU/WAhs4YDFymcA8PYECcq0E33ywU+/fqQBd4wH/UQj16aXGYifgw8Sr2D9Ea/00Qy4RpGwkR9Pl0h4JOg0ix93pDBlvpTLWK7hTwnk1GBcEtLx1nFK1esbn0jJV+yCDLM7w6PfVCeVAXn0XqOIXNAKBAym4lPqUsveK0neJshm1wj8n9jrzu+i0NP0Tlfcr9e7kTUCAwEAATANBgkqhkiG9w0BAQUFAAOCAQEAdVvIJVgYmf7qN76bbZizA2m81NdzuifZ0zWUokZ7KWrxqq4vfeOJeExwfZgvjcJuP+G23PuO7ZckoZ+mqA/MigJEW1k5odnRcp9oteiVoKKhpU9wPT+2w4N3WiaI8AXEAcVUAe8JqF+M9DRfB1F+gnoK3rmUXPrTXRYRaEyCu4eLjQMHae4//d+oIBFPVkv7kPD2w1ludXp0YS83lQtb1xMBWMOpQn4I3Mi2l0uvBoas80UGUn1HmGUFaVnPy6qqtYRVdf+qVT+KS1fHhgfGygvy8mbUvNmt7vYjFew0VEjxiZa+uctrxbaR1fZjnSnxH16mqht5rlqHHyYDTIHZFg==
        byte ServerKey MIIEowIBAAKCAQEAwdYXyfJvyel4iyd9cDFu5eBisijE0U4ftcr9GRMauYakts1VsfV0hI1rsIPanghPH0/qw7uLlgLeKqK75A1b3DJxNyx7vrLozjIKqn1mwMLbT0gR+G9lRNoyOGdhRnMpZGbgQML3jZlVhG+ChT9YCGzhgMXKZwDw9gQJyrQTffLBT79+pAF3jAf9RCPXppcZiJ+DDxKvYP0Rr/TRDLhGkbCRH0+XSHgk6DSLH3ekMGW+lMtYruFPCeTUYFwS0vHWcUrV6xufSMlX7IIMszvDo99UJ5UBefReo4hc0AoEDKbiU+pSy94rSd4myGbXCPyf2OvO76LQ0/ROV9yv17uRNQIDAQABAoIBAGhwISsnHAJPcCqR4W1ExTrIdoUFoF4h2MYLk+khuQGDQVZZNjYHSXtt8zsNIAqL8Y2ucpB5iVEPRIL2YYQTio4PA581sYrjPLp0jfikTmvH0YBbFYulAYxigDKRyQC7Ze752xQpuFYr6r7LkiiXI6iOecX3TAHJqQr0zA3SjroJ1P+E6voHPJBzH81kqzBFYIBRIRNJb4uZRCSuoTHsk9GDqQiKJh5ukL3xllGfHwYji74guCK4gMoI3bQhrnXc9ZOU0jO9vCgzXo1bEYeH3SAuWnCBqptq6sI7n68al0usvF+Ss6FC5MPw9zdb1c2+ec3X1jvmNoOaeek54p9WxaECgYEA37rNMkkM/pY3Cfl0+5vr854TqXtf846shtsQYx1CscdolX7GFzkoqAGxM9rxdAN0/k80I3Te7FZ6YHUTOJoBZ02JtIzj61/iZr/svUE1LZHK7mhaNfpmSZuBvVrss9p/rQLnTxlWujHhq8dxRz7ufX7yLceKSjTzHV+P37IvAU0CgYEA3ct7BvIKZigGFw0zZblsJf+HszyUgMGzBOQGQD4i8R3VGPr4efVdkrgGR1/cN7iEmTKKup71hUWEgr69FdHSQcuK3AMB6rCyhSVZwsHm4pIlI+Av0VsE5h+mgThjPD4K7vYmDw7lU8xV+ps0/VSer255HE/fYSIlxTei6ATT24kCgYEAwVtwfEUmNeEdMEGoGMxo3+N+mrtF8fkconAxeXeQbJUqjglCqk98E7dirq5Kfzl9o0xQg1Q+VYNnwHVuZzyyedVJbgFV+daklKjKscXpb7jQ6brGPGBshrEfL8elSstMDPq1bmc3zTPPFecIv8pj05IjO+14Vynr8zbj4TDd7wECgYAryf+5KFJLRv2k0XNjUw96FRAqn/xFy3hXr9lYF6x4ZEZtTyd9lKbrz69VqiRlT+XGBUeEftvEeywlUBku1KUpXlFFDMb1Gfu08+Hb5MJ72xTAF4P5VnoKIReTjZlyDGHGOgzbjjpSqBYVi00T8v/9bNc2csKMf9xrKofcPQ/C2QKBgHrNzY4ktbF7YcUuz4T/2e0fALTTZLaIMvkrBZqhHo/oRPh7DdimiLv8EsizpdL4kG3lif/vjBt7c7y/SK+vAfJZp76kvNf1GxrJaWAwdYL8q2OLqJhMyKu5VgOKg5k0KwK29gcVnJICIw3LFl35L9UjNID/zcEngksCV6Rq94Qp
        uint ServerType 0
        bool UseKeepConnect true
        bool UseWebTimePage false
        bool UseWebUI false
        declare ServerTraffic
        {
            declare RecvTraffic
            {
                uint64 BroadcastBytes 19102547
                uint64 BroadcastCount 281560
                uint64 UnicastBytes 225490674
                uint64 UnicastCount 527975
            }
            declare SendTraffic
            {
                uint64 BroadcastBytes 3603633
                uint64 BroadcastCount 22811
                uint64 UnicastBytes 225152801
                uint64 UnicastCount 524525
            }
        }
        declare SyslogSettings
        {
            string HostName $
            uint Port 0
            uint SaveType 0
        }
    }


    declare VirtualHUB


    {
        declare DEFAULT
        {
            uint64 CreatedTime 1387876027449
            byte HashedPassword +WzqGYrR3VYXrAhLPZLGEHiIwO8=
            uint64 LastCommTime 1387876027448
            uint64 LastLoginTime 1387876027448
            uint NumLogin 0
            bool Online true
            uint RadiusRetryInterval 0
            uint RadiusServerPort 1812
            string RadiusSuffixFilter $
            byte SecurePassword bpw3X/O5E8a686ccnl4uXmDtkwI=
            uint Type 0
            declare AccessList
            {
            }
            declare AdminOption
            {
                uint allow_hub_admin_change_option 0
                uint deny_bridge 0
                uint deny_change_user_password 0
                uint deny_empty_password 0
                uint deny_hub_admin_change_ext_option 0
                uint deny_qos 0
                uint deny_routing 0
                uint max_accesslists 0
                uint max_bitrates_download 0
                uint max_bitrates_upload 0
                uint max_groups 0
                uint max_multilogins_per_user 0
                uint max_sessions 0
                uint max_sessions_bridge 0
                uint max_sessions_client 0
                uint max_sessions_client_bridge_apply 0
                uint max_users 0
                uint no_access_list_include_file 0
                uint no_cascade 0
                uint no_change_access_control_list 0
                uint no_change_access_list 0
                uint no_change_admin_password 0
                uint no_change_cert_list 0
                uint no_change_crl_list 0
                uint no_change_groups 0
                uint no_change_log_config 0
                uint no_change_log_switch_type 0
                uint no_change_msg 0
                uint no_change_users 0
                uint no_delay_jitter_packet_loss 0
                uint no_delete_iptable 0
                uint no_delete_mactable 0
                uint no_disconnect_session 0
                uint no_enum_session 0
                uint no_offline 0
                uint no_online 0
                uint no_query_session 0
                uint no_read_log_file 0
                uint no_securenat 0
                uint no_securenat_enabledhcp 0
                uint no_securenat_enablenat 0
            }


            declare CascadeList
            {
            }
            declare LogSetting
            {
                uint PacketLogSwitchType 4
                uint PACKET_LOG_ARP 0
                uint PACKET_LOG_DHCP 1
                uint PACKET_LOG_ETHERNET 0
                uint PACKET_LOG_ICMP 0
                uint PACKET_LOG_IP 0
                uint PACKET_LOG_TCP 0
                uint PACKET_LOG_TCP_CONN 1
                uint PACKET_LOG_UDP 0
                bool SavePacketLog true
                bool SaveSecurityLog true
                uint SecurityLogSwitchType 4
            }
            declare Message
            {
            }
            declare Option
            {
                uint AccessListIncludeFileCacheLifetime 30
                uint AdjustTcpMssValue 0
                bool ApplyIPv4AccessListOnArpPacket false
                bool BroadcastLimiterStrictMode false
                uint BroadcastStormDetectionThreshold 0
                uint ClientMinimumRequiredBuild 0
                bool DisableAdjustTcpMss false
                bool DisableCheckMacOnLocalBridge false
                bool DisableCorrectIpOffloadChecksum false
                bool DisableHttpParsing false
                bool DisableIPParsing false
                bool DisableKernelModeSecureNAT false
                bool DisableUdpAcceleration false
                bool DisableUdpFilterForLocalBridgeNic false
                bool DisableUserModeSecureNAT false
                bool DoNotSaveHeavySecurityLogs false
                bool FilterBPDU false
                bool FilterIPv4 false
                bool FilterIPv6 false
                bool FilterNonIP false
                bool FilterOSPF false
                bool FilterPPPoE false
                bool ManageOnlyLocalUnicastIPv6 true
                bool ManageOnlyPrivateIP true
                uint MaxLoggedPacketsPerMinute 0
                uint MaxSession 0
                bool NoArpPolling false
                bool NoDhcpPacketLogOutsideHub true
                bool NoEnum false
                bool NoIpTable false
                bool NoIPv4PacketLog false
                bool NoIPv6AddrPolling false
                bool NoIPv6DefaultRouterInRAWhenIPv6 true
                bool NoIPv6PacketLog false
                bool NoLookBPDUBridgeId false
                bool NoMacAddressLog true
                bool NoManageVlanId false
                bool NoSpinLockForPacketDelay false
                bool RemoveDefGwOnDhcpForLocalhost true
                uint RequiredClientId 0
                uint SecureNAT_MaxDnsSessionsPerIp 0
                uint SecureNAT_MaxIcmpSessionsPerIp 0
                uint SecureNAT_MaxTcpSessionsPerIp 0
                uint SecureNAT_MaxTcpSynSentPerIp 0
                uint SecureNAT_MaxUdpSessionsPerIp 0
                string VlanTypeId 0x8100
                bool YieldAfterStorePacket false
            }
            declare SecureNAT
            {
                bool Disabled true
                bool SaveLog true


                declare VirtualDhcpServer
                {
                    string DhcpDnsServerAddress 192.168.30.1
                    string DhcpDnsServerAddress2 0.0.0.0
                    string DhcpDomainName $
                    bool DhcpEnabled true
                    uint DhcpExpireTimeSpan 7200
                    string DhcpGatewayAddress 192.168.30.1
                    string DhcpLeaseIPEnd 192.168.30.200
                    string DhcpLeaseIPStart 192.168.30.10
                    string DhcpSubnetMask 255.255.255.0
                }
                declare VirtualHost
                {
                    string VirtualHostIp 192.168.30.1
                    string VirtualHostIpSubnetMask 255.255.255.0
                    string VirtualHostMacAddress 00-AC-61-98-AB-7C
                }
                declare VirtualRouter
                {
                    bool NatEnabled true
                    uint NatMtu 1500
                    uint NatTcpTimeout 1800
                    uint NatUdpTimeout 60
                }
            }
            declare SecurityAccountDatabase
            {
                declare CertList
                {
                }
                declare CrlList
                {
                }
                declare GroupList
                {
                }
                declare IPAccessControlList
                {
                }
                declare UserList
                {
                }
            }
            declare Traffic
            {
                declare RecvTraffic
                {
                    uint64 BroadcastBytes 0
                    uint64 BroadcastCount 0
                    uint64 UnicastBytes 0
                    uint64 UnicastCount 0
                }
                declare SendTraffic
                {
                    uint64 BroadcastBytes 0
                    uint64 BroadcastCount 0
                    uint64 UnicastBytes 0
                    uint64 UnicastCount 0
                }
            }
        }
        declare VPN
        {
            uint64 CreatedTime 1387876945565
            byte HashedPassword LS0LjI4oBlaMi8jfko455Kjj5K=
            uint64 LastCommTime 1388553310373
            uint64 LastLoginTime 1388552884762
            uint NumLogin 20
            bool Online true
            uint RadiusRetryInterval 0
            uint RadiusServerPort 1812
            string RadiusSuffixFilter $
            byte SecurePassword 68bdSovYm5DTF0KAsQZ6joi8AMI=
            uint Type 0


            declare AccessList
            {
            }
            declare AdminOption
            {
                uint allow_hub_admin_change_option 0
                uint deny_bridge 0
                uint deny_change_user_password 0
                uint deny_empty_password 0
                uint deny_hub_admin_change_ext_option 0
                uint deny_qos 0
                uint deny_routing 0
                uint max_accesslists 0
                uint max_bitrates_download 0
                uint max_bitrates_upload 0
                uint max_groups 0
                uint max_multilogins_per_user 0
                uint max_sessions 0
                uint max_sessions_bridge 0
                uint max_sessions_client 0
                uint max_sessions_client_bridge_apply 0
                uint max_users 0
                uint no_access_list_include_file 0
                uint no_cascade 0
                uint no_change_access_control_list 0
                uint no_change_access_list 0
                uint no_change_admin_password 0
                uint no_change_cert_list 0
                uint no_change_crl_list 0
                uint no_change_groups 0
                uint no_change_log_config 0
                uint no_change_log_switch_type 0
                uint no_change_msg 0
                uint no_change_users 0
                uint no_delay_jitter_packet_loss 0
                uint no_delete_iptable 0
                uint no_delete_mactable 0
                uint no_disconnect_session 0
                uint no_enum_session 0
                uint no_offline 0
                uint no_online 0
                uint no_query_session 0
                uint no_read_log_file 0
                uint no_securenat 0
                uint no_securenat_enabledhcp 0
                uint no_securenat_enablenat 0
            }
            declare CascadeList
            {
            }
            declare LogSetting
            {
                uint PacketLogSwitchType 4
                uint PACKET_LOG_ARP 0
                uint PACKET_LOG_DHCP 1
                uint PACKET_LOG_ETHERNET 0
                uint PACKET_LOG_ICMP 0
                uint PACKET_LOG_IP 0
                uint PACKET_LOG_TCP 0
                uint PACKET_LOG_TCP_CONN 1
                uint PACKET_LOG_UDP 0
                bool SavePacketLog true
                bool SaveSecurityLog true
                uint SecurityLogSwitchType 4
            }
            declare Message
            {
            }
            declare Option
            {
                uint AccessListIncludeFileCacheLifetime 30
                uint AdjustTcpMssValue 0
                bool ApplyIPv4AccessListOnArpPacket false
                bool BroadcastLimiterStrictMode false
                uint BroadcastStormDetectionThreshold 0
                uint ClientMinimumRequiredBuild 0
                bool DisableAdjustTcpMss false
                bool DisableCheckMacOnLocalBridge false
                bool DisableCorrectIpOffloadChecksum false
                bool DisableHttpParsing false
                bool DisableIPParsing false
                bool DisableKernelModeSecureNAT false
                bool DisableUdpAcceleration false
                bool DisableUdpFilterForLocalBridgeNic false
                bool DisableUserModeSecureNAT false
                bool DoNotSaveHeavySecurityLogs false
                bool FilterBPDU false
                bool FilterIPv4 false
                bool FilterIPv6 false
                bool FilterNonIP false
                bool FilterOSPF false
                bool FilterPPPoE false
                bool ManageOnlyLocalUnicastIPv6 true
                bool ManageOnlyPrivateIP true
                uint MaxLoggedPacketsPerMinute 0
                uint MaxSession 0
                bool NoArpPolling false
                bool NoDhcpPacketLogOutsideHub true
                bool NoEnum false
                bool NoIpTable false
                bool NoIPv4PacketLog false
                bool NoIPv6AddrPolling false
                bool NoIPv6DefaultRouterInRAWhenIPv6 true
                bool NoIPv6PacketLog false
                bool NoLookBPDUBridgeId false
                bool NoMacAddressLog true
                bool NoManageVlanId false
                bool NoSpinLockForPacketDelay false
                bool RemoveDefGwOnDhcpForLocalhost true
                uint RequiredClientId 0
                uint SecureNAT_MaxDnsSessionsPerIp 0
                uint SecureNAT_MaxIcmpSessionsPerIp 0
                uint SecureNAT_MaxTcpSessionsPerIp 0
                uint SecureNAT_MaxTcpSynSentPerIp 0
                uint SecureNAT_MaxUdpSessionsPerIp 0
                string VlanTypeId 0x8100
                bool YieldAfterStorePacket false
            }
            declare SecureNAT
            {
                bool Disabled false
                bool SaveLog true


            declare VirtualDhcpServer
                {
                    string DhcpDnsServerAddress 192.168.30.1
                    string DhcpDnsServerAddress2 0.0.0.0
                    string DhcpDomainName $
                    bool DhcpEnabled true
                    uint DhcpExpireTimeSpan 7200
                    string DhcpGatewayAddress 192.168.30.1
                    string DhcpLeaseIPEnd 192.168.30.200
                    string DhcpLeaseIPStart 192.168.30.10
                    string DhcpSubnetMask 255.255.255.0
                }
                declare VirtualHost
                {
                    string VirtualHostIp 192.168.30.1
                    string VirtualHostIpSubnetMask 255.255.255.0
                    string VirtualHostMacAddress 00-AC-41-0D-7A-5E
                }
                declare VirtualRouter
                {
                    bool NatEnabled true
                    uint NatMtu 1500
                    uint NatTcpTimeout 1800
                    uint NatUdpTimeout 60
                }
            }
            declare SecurityAccountDatabase
            {
                declare CertList
                {
                }
                declare CrlList
                {
                }
                declare GroupList
                {
                }
            declare IPAccessControlList
                {
                }
                declare UserList
                {
                    declare test
                    {
                        byte AuthNtLmSecureHash L+jjf4/fkkfljsnbo34/eA==
                        byte AuthPassword Jdgljoi25Kkldkgj45jkk50034k=
                        uint AuthType 1
                        uint64 CreatedTime 1387877131903
                        uint64 ExpireTime 0
                        uint64 LastLoginTime 1388552884762
                        string Note Testni
                        uint NumLogin 20
                        string RealName test0i1
                        uint64 UpdatedTime 1387877161040


                        declare Traffic
                        {
                            declare RecvTraffic
                            {
                                uint64 BroadcastBytes 779200
                                uint64 BroadcastCount 8312
                                uint64 UnicastBytes 190199571
                                uint64 UnicastCount 224982
                            }
                            declare SendTraffic
                            {
                                uint64 BroadcastBytes 2822581
                                uint64 BroadcastCount 14492
                                uint64 UnicastBytes 30126130
                                uint64 UnicastCount 176765
                            }
                        }
                    }
                }
            }
            declare Traffic
            {
                declare RecvTraffic
                {
                    uint64 BroadcastBytes 19102547
                    uint64 BroadcastCount 281560
                    uint64 UnicastBytes 225490674
                    uint64 UnicastCount 527975
                }
                declare SendTraffic
                {
                    uint64 BroadcastBytes 3603633
                    uint64 BroadcastCount 22811
                    uint64 UnicastBytes 225152801
                    uint64 UnicastCount 524525
                }
            }
        }
    }
    declare VirtualLayer3SwitchList
    {
    }
}

```

---

### Post by stype on 2014-01-01
I'm not sure weather it's been set as a bridge or a router, but I guess that it acts more like bridge...
Can you see this from the config file I've posted ?

---

### Post by stype on 2014-01-01
I would just like to emphasize that as long as we enable the file sharing all suggestions are fine for me.

It does not NEEDs to be the softether VPN, that just looked like the simplest solution to me. (obviously it's not)

If you have a suggestion that we do this by installing a (stable) windows os, I'm fine with that as well.
As long as someone can point me to a right way, I can format everything that I've done so far :).

Cheers, and thank you so much for the effort !

---

### Post by volkswagner on 2014-01-01
I'm sorry I just don't know enough about the VPN server software.

I have a hunch you need to learn/setup Cascade Connection Functions.

You are correct with your goal.  To properly/securely share files via SAMBA over WAN you will want a VPN connection.

Again, your best bet is to get help from the folks at [SoftEther VPN forums]("http://www.vpnusers.com/").

---

### Post by stype on 2014-01-01
> **volkswagner said:**
> I'm sorry I just don't know enough about the VPN server software.

I have a hunch you need to learn/setup Cascade Connection Functions.

You are correct with your goal.  To properly/securely share files via SAMBA over WAN you will want a VPN connection.

Again, your best bet is to get help from the folks at [SoftEther VPN forums]("http://www.vpnusers.com/").

OK I will try there.

Thank you so much for your wonderful will to help !

Cheers,
Stype

---

### Post by miguelpires on 2014-01-02
> **stype said:**
> OK I will try there.

Thank you so much for your wonderful will to help !

Cheers,
Stype

Hi,
I've a small company like you, and the solution we found best is to use Zentyal 3.0 (is ubuntu 12.04 + a Webinterface to configure)
Right now in our production server we have exactly what you are asking for: VPN to access all the shares and a way to work via VPN without any problem (except the poor internet connection that we sometimes face)

If you wana tray is use 3.0 and not 3.2 (in my private server I encounter problems with samba 4)

Regards
Miguel

---

### Post by Roasted on 2014-01-02
Am I understanding that you basically want Samba file-sharing like features, but available anywhere? If that's the case, look into ownCloud. If Dropbox can work for you but you want more space + more control + more features, ownCloud is it. Running it at home and work with great success. They have a web UI as well as a sync client for Linux/Mac/Windows.

---

### Post by stype on 2014-01-04
[COLOR=#000000]@Zentyal 3.0
Thank you for your suggestion. 
However I must dissapoint all of you. My knowledge of linux was just not enough to get this working.
I installed windows server 8 and set up everything with the help of softether.
Probably I could use built in VPN functionality, but I used this one since I assumed microsoft one could have problems with external NAT. 

@Roasted
[/COLOR][COLOR=#000000]ownCloud looks very good, maybe that's even better solution for us to avoid delays with server.
What I don't like with the systems which makes local copies of files is all those conflicting situations (when you get 'conflicted copies' of files in dropbox). This was a huge problem for us...
--

I know that I am a disgrace for an Ubuntu forum, but a man did what a man needed to do to get things running if you know what i mean...

[/COLOR]

---

