---
title: "Redirect local PCs to server private IP address"
date: 2016-08-25
forum: Server Platforms
---

### Post by courtney2 on 2016-08-25
I am running a Nextcloud server and I am wanting to use secure TLS connections both internally and externally. I know I have to set up a DNS server, but I don't know fully where to begin with all of this. My server has a dynamic public IP address so I am using DuckDNS for dynamic IP management, and I also have a Let's Encrypt certificate for encryption. What I want is for people on the internal network to be able to type "serverdomain.duckdns.org" and have it go to internal IP of 10.0.0.50 and still use the certificate so I know I am making a secure connection and browsers don't throw any flags to the users. How do I set this up? I'm using Ubuntu Server 16.04

---

### Post by darkod on 2016-08-26
The certificate is installed on the server, right? So it shouldn't matter how you reach it (via which IP), it should apply and show the certificate correctly.

For local LAN clients to reach your URL on local IP, the best option would be hosts file, unless you also have local DNS in the local LAN. If you have a local DNS and the clients are using this DNS, you only make the A record for serverdomain.duckdns.org pointing to 10.0.0.50.

Otherwise in local hosts file on each client, create the entry:
10.0.0.50   serverdomain.duckdns.org

On linux the local hosts is /etc/hosts. On windows it's C:\windows\system32\drivers\etc\hosts.

---

### Post by courtney2 on 2016-08-27
Thank you very much! That helps. I'm thinking since some of these clients are mobile devices too it might be wise to set up a DNS server. Is the canned version of DNS that you can choose at install time all right? Pretty sure I remember choosing that option. It probably wouldn't be smart to run DNS and nextcloud on the same server would it? My devices are running thin :P I'm doing containerized operating systems to separate my services but I have limited RAM for the time being

---

