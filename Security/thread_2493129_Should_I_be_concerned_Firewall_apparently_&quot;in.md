---
title: "Should I be concerned Firewall apparently &quot;inactive&quot; for months?"
date: 2023-12-04
forum: Security
---

### Post by AbleTassie on 2023-12-04
Hello all,

It appears that my firewall has not been enabled since a clean install of Lubuntu 22.04.3 LTS many months ago. Just on a whim, I just ran the terminal command: "sudo ufw status" and got back "Status: inactive" . So I ran the Terminal Command "sudo ufw enable" to enable the ufw.

Since it appears, however, that I have had the Firewall unintentionally turned off for months since the installation, should I be concerned  that my system has been compromised?

Is there anything I should do?

Thank you,

A.

---

### Post by Dennis N on 2023-12-04
Do you use a router? It should have a firewall that rejects any incoming traffic unless its associated with an outgoing request from your OS.

FYI, I don't have ufw installed.

---

### Post by ian-weisser on 2023-12-05
> **AbleTassie said:**
> It appears that my firewall has not been enabled since a clean install of Lubuntu 22.04.3 LTS many months ago.

Yes, that is normal.
A stock install of Ubuntu has only a couple listening services: DHCP and similar excitements. None of them have any known vulnerabilities. And you, using your sudo power, can turn any off  if you wish.

Try this command to see what ports your system is listening upon, and which applications are doing the listening.

```
sudo ss -tulpn
```

If you find a listening application that you don't understand, ask about it.

A firewall is not a magic talisman against all malice. 
A firewall is a tool. Know the purpose of the tool and use it properly.

---

### Post by AbleTassie on 2023-12-11
Thanks for your replies Dennis and ian. Ian I took your suggestion and ran "sudo ss -tulpn" and the output I got is attached as a screenshot (I could not easily copy and past the output into this post). Any comments you or anybody else has would be welcomed.

Thanks,

Able

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293186&stc=1[/IMG]

---

### Post by TheFu on 2023-12-11
Please post text, not images.  Hard to read the image or select/paste specific lines to help the discussion.
All the things listening on 127.x.x.x aren't any issue. Only the local system can access those.

Please make it easy for others to help you.

---

### Post by AbleTassie on 2023-12-19
Fu,

I pasted the output of the "sudo ss -tulpn" below. I tried to make the output as readable as possible.

Abe
```

able@able-x556uq:~$ sudo ss -tulpn

 [sudo] password for able:
 
 

 Netid       State   Recv-Q        Send-Q                                    Local Address:     Port                    Peer Address Port                           Process

 udp         UNCONN        0                                0         0.0.0.0:52189                    0.0.0.0:*                             users("pia-openvpn",pid=4317,fd=4))            

 udp         UNCONN        0                      0               127.0.0.53%lo:53                               0.0.0.0:*                                                   users("systemd-resolve",pid=585,fd=13))        

 udp         UNCONN        0                         0         0.0.0.0:631                     0.0.0.0:*                           users("cups-browsed",pid=2529,fd=7))           
 udp         UNCONN        0                         0         0.0.0.0:37749                 0.0.0.0:*                           users("avahi-daemon",pid=687,fd=14))           
 udp         UNCONN        0                         0         0.0.0.0:5353                   0.0.0.0:*                           users("avahi-daemon",pid=687,fd=12))           
 udp         UNCONN        0     0       [fe80::5305:a61b:25d2:4ef4]%wlp3s0:546                         [::]:*                 users("NetworkManager",pid=772,fd=27))         
 udp         UNCONN        0                        0        [::]:5353                            [::]:*                                 users("avahi-daemon",pid=687,fd=13))           
 udp         UNCONN        0             0       [::]:47458                           [::]:*                                     users("avahi-daemon",pid=687,fd=15))           
 tcp         LISTEN           0                       50    127.0.0.1:44031                     0.0.0.0:*                            users("pia-daemon",pid=813,fd=39))             
 tcp         LISTEN           0                      128  127.0.0.1:631                     0.0.0.0:*                            users("cupsd",pid=811,fd=8))                   
 tcp         LISTEN    0          4096                                      127.0.0.53%lo:53                                     0.0.0.0:*                      users("systemd-resolve",pid=585,fd=14))        
 tcp         LISTEN          0          128                                                  [::1]:631                               [::]:*                             users("cupsd",pid=811,fd=7))

```

---

### Post by ian-weisser on 2023-12-20
What exactly is your question about that output?

Did you read it?

---

