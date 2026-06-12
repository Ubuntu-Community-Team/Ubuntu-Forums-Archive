---
title: "exim4 cannot receive email from remote domain"
date: 2010-02-20
forum: Server Platforms
---

### Post by Face_Man on 2010-02-20
hello all,
My ISP recently decided to kill outbound traffic on port 25 for some reason. Therefore, I change the SMTP port to 24, everything work fine so far i can send email to local domain and remote. However, i cannot receive Emails from remote domain. i try use online "mail server test services" and all i got is timeout. 

Any help would be much appreciated.

---

### Post by mbehamin on 2010-02-20
hi
for receiving emails from remote domain you need to accept inbound packet with port 25. just redirect your all your inbound packet with port 25 to your mail server port which you set 24,

---

### Post by Face_Man on 2010-02-20
> **mbehamin said:**
> hi
for receiving emails from remote domain you need to accept inbound packet with port 25. just redirect your all your inbound packet with port 25 to your mail server port which you set 24,

well, i think port 25 is dropped before reaching my machine. 
i do have a firewall that port FORWARD 25 and 24 to my mail server 

```

    iptables -A FORWARD -i $InternetIP -o $LocalIP -d $IP -p tcp --dport $24 -j ACCEPT
    iptables -t nat -A PREROUTING -i $eth0 -d $InternetIP -p tcp --dport $24 -j DNAT --to $IP

    iptables -A FORWARD -i $InternetIP -o $LocalIP -d $IP -p tcp --dport $25 -j ACCEPT
    iptables -t nat -A PREROUTING -i $eth0 -d $InternetIP -p tcp --dport $25 -j DNAT --to $IP
 

```
 
so could you explain in more details plz.

---

