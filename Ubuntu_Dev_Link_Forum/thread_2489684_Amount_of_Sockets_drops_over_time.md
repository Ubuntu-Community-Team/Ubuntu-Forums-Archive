---
title: "Amount of Sockets drops over time"
date: 2023-08-07
forum: Ubuntu Dev Link Forum
---

### Post by okarpov on 2023-08-07
Hi there,

I have a small app (dotnet) which sends +1000 async requests per second to different servers/urls.

The main issue is that over about 5 minutes the amount of ESTABLISHED sockets drops from +1000 to 5-10 (and there are no a lot of WAIT/SYN sockets etc.)
until it stops sending requests at all. If i close the app and start it again then it starts sending +1000 requests again and then slowing down and so on over and over.

Any ideas on what may cause it?

Ubuntu 20.04/22.04 cloud-base images

i do track sockets and their states using the command:
netstat -n | awk '/^tcp/ {t[$NF]++}END{for(state in t){print state, t[state]} }'

Thx

---

### Post by okarpov on 2023-08-07
This is the code to create sockets (it has 3 public IPs on the same eth0):

```

                socket = new Socket(ip.AddressFamily, SocketType.Stream, ProtocolType.Tcp)
                {
                    // Turn off Nagle's algorithm since it degrades performance in most HttpClient scenarios.
                    NoDelay = true,
                    ReceiveBufferSize = respbufferSize,
                    SendBufferSize = reqbufferSize,
                    ExclusiveAddressUse = false,
                    Ttl = time_out,//64
                };


                socket.SetSocketOption(SocketOptionLevel.Socket, SocketOptionName.ReuseAddress, true);
                
                socket.Bind(endPoints[DateTime.UtcNow.Ticks%endPoints.Length]);


                await socket.ConnectAsync(ip, context.DnsEndPoint.Port, cancellationToken).ConfigureAwait(false);


                NetworkStream ns = new NetworkStream(socket, ownsSocket: true);


                return ns;

```

also i do set the following system params:
```

/sbin/sysctl -w net.core.somaxconn=65536
/sbin/sysctl -w net.ipv4.ip_local_port_range="1024 65535"
/sbin/sysctl -w net.ipv4.tcp_tw_reuse=1
/sbin/sysctl -w net.ipv4.tcp_fin_timeout=15

```

---

