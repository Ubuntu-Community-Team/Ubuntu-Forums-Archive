---
title: "Transmission over SSL don't start the trorrents."
date: 2024-02-02
forum: Ubuntu Cloud and Juju
---

### Post by slavy2 on 2024-02-02
Hello all, 
I'm new in Ubuntu!
Today I put transmission-daemon behind the apache2 web server using reverse proxy, get SSL certificate to my.domain.com and have https:// access using web interface with port 9091 closed in the firewall, can upload and add torrent's, but the torrent's stay on Idle status and never start download - 0 peers.  Till this moment all's work well. Do I miss something wich need to do? Port forwarding in to the router... some changes in transmission config file... or something else to reach peers and starting the download process normal ?


Server system:
Linux @@@@ 5.15.0-92-generic #102-Ubuntu SMP Wed Jan 10 09:33:48 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

apache v.host config file

<VirtualHost *:80>
    ServerName my.doamn.com
    ServerAlias [www.my.domain.com]("http://www.my.domain.com")
    ServerAdmin [EMAIL="mymail@mail.com"]mymail@mail.com[/EMAIL]
    ErrorLog /var/log/apache2/transmission-error.log
    CustomLog /var/log/apache2/transmission-access.log combined

    ProxyPreserveHost On

    ProxyPass "/embywebsocket" "ws://127.0.0.1:9091/embywebsocket"
        ProxyPassReverse "/embywebsocket" "ws://127.0.0.1:9091/embywebsocket"

    ProxyPass "/" "http://127.0.0.1:9091/"
        ProxyPassReverse "/" "http://127.0.0.1:9091/"
RewriteEngine on
RewriteCond %{SERVER_NAME} =www.my.domain.com [OR]
RewriteCond %{SERVER_NAME} =my.domain.com
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>

$ sudo cat  /var/lib/transmission-daemon/info/settings.json
{
    "alt-speed-down": 7500,
    "alt-speed-enabled": true,
    "alt-speed-time-begin": 450,
    "alt-speed-time-day": 127,
    "alt-speed-time-enabled": true,
    "alt-speed-time-end": 0,
    "alt-speed-up": 3500,
    "bind-address-ipv4": "127.0.0.1",
    "bind-address-ipv6": "::",
    "blocklist-enabled": false,
    "blocklist-url": "http://www.example.com/blocklist",
    "cache-size-mb": 4,
    "dht-enabled": true,
    "download-dir": "/jellyfin/16tb/Transmission//Downloads",
    "download-limit": 7500,
    "download-limit-enabled": true,
    "download-queue-enabled": true,
    "download-queue-size": 5,
    "encryption": 1,
    "idle-seeding-limit": 3500,
    "idle-seeding-limit-enabled": true,
    "incomplete-dir": "/jellyfin/16tb/Transmission/Incomplate",
    "incomplete-dir-enabled": true,
    "lpd-enabled": false,
    "max-peers-global": 200,
    "message-level": 1,
    "peer-congestion-algorithm": "",
    "peer-id-ttl-hours": 6,
    "peer-limit-global": 200,
    "peer-limit-per-torrent": 50,
    "peer-port": 51413,
    "peer-port-random-high": 65535,
    "peer-port-random-low": 49152,
    "peer-port-random-on-start": false,
    "peer-socket-tos": "default",
    "pex-enabled": true,
    "port-forwarding-enabled": false,
    "preallocation": 1,
    "prefetch-enabled": true,
    "queue-stalled-enabled": true,
    "queue-stalled-minutes": 30,
    "ratio-limit": 2.5000,
    "ratio-limit-enabled": true,
    "rename-partial-files": true,
    "rpc-authentication-required": true,
    "rpc-bind-address": "0.0.0.0",
    "rpc-enabled": true,
    "rpc-host-whitelist": "",
    "rpc-host-whitelist-enabled": true,
    "rpc-password": "{e0891c8c4faa1acfd9b631f6cc7f75b72a3ce4acdvACQ0Eg",
    "rpc-port": 9091,
    "rpc-url": "/transmission/",
    "rpc-username": "@@@",
    "rpc-whitelist": "127.0.0.1",
    "rpc-whitelist-enabled": false,
    "scrape-paused-torrents-enabled": true,
    "script-torrent-done-enabled": false,
    "script-torrent-done-filename": "",
    "seed-queue-enabled": false,
    "seed-queue-size": 10,
    "speed-limit-down": 7500,
    "speed-limit-down-enabled": false,
    "speed-limit-up": 3500,
    "speed-limit-up-enabled": false,
    "start-added-torrents": true,
    "trash-original-torrent-files": false,
    "umask": 2,
    "upload-limit": 100,
    "upload-limit-enabled": 0,
    "upload-slots-per-torrent": 14,
    "utp-enabled": true
}

$ sudo netstat -lntp
[sudo] password for slavy: 
Sorry, try again.
[sudo] password for slavy: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -                   
tcp        0      0 0.0.0.0:35173           0.0.0.0:*               LISTEN      940/rpc.statd       
tcp        0      0 0.0.0.0:35463           0.0.0.0:*               LISTEN      17400/rpc.mountd    
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1023/mariadbd       
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      853/systemd-resolve 
tcp        0      0 127.0.0.1:51413         0.0.0.0:*               LISTEN      45720/transmission- 
tcp        0      0 0.0.0.0:8096            0.0.0.0:*               LISTEN      907/jellyfin        
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      1/init              
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      990/sshd: /usr/sbin 
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      1039/smbd           
tcp        0      0 0.0.0.0:41471           0.0.0.0:*               LISTEN      17400/rpc.mountd    
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      1039/smbd           
tcp        0      0 0.0.0.0:37493           0.0.0.0:*               LISTEN      -                   
tcp        0      0 0.0.0.0:45735           0.0.0.0:*               LISTEN      17400/rpc.mountd    
tcp        0      0 0.0.0.0:9091            0.0.0.0:*               LISTEN      45720/transmission- 
tcp6       0      0 :::2049                 :::*                    LISTEN      -                   
tcp6       0      0 :::59611                :::*                    LISTEN      17400/rpc.mountd    
tcp6       0      0 :::51413                :::*                    LISTEN      45720/transmission- 
tcp6       0      0 :::39419                :::*                    LISTEN      -                   
tcp6       0      0 :::52909                :::*                    LISTEN      17400/rpc.mountd    
tcp6       0      0 :::80                   :::*                    LISTEN      29846/apache2       
tcp6       0      0 :::45171                :::*                    LISTEN      940/rpc.statd       
tcp6       0      0 :::111                  :::*                    LISTEN      1/init              
tcp6       0      0 :::21                   :::*                    LISTEN      951/vsftpd          
tcp6       0      0 :::22                   :::*                    LISTEN      990/sshd: /usr/sbin 
tcp6       0      0 :::139                  :::*                    LISTEN      1039/smbd           
tcp6       0      0 :::445                  :::*                    LISTEN      1039/smbd           
tcp6       0      0 :::443                  :::*                    LISTEN      29846/apache2       
tcp6       0      0 :::59167                :::*                    LISTEN      17400/rpc.mountd

$ ls -l /jellyfin/16tb/Transmission
total 8
drwxrwxr-x 7 debian-transmission debian-transmission 4096 Feb  1 16:49 Downloads
drwxrwxr-x 2 debian-transmission debian-transmission 4096 Feb  2 13:16 Incomplate

---

