---
title: "Feedback on my iptables setup..."
date: 2010-07-05
forum: Security
---

### Post by akelsall on 2010-07-05
I set up iptables based on the main HowTo. I'm running Ubuntu on my desktop. I have a wireless router that allows two other computers to attached to it. I'd like feedback as to whether or not this setup is secure enough. 

(I couldn't get the output to keep it's format, so I attached a screenshot for clarity). 


Thanks,

Andy

---

### Post by cariboo on 2010-07-05
You can pipe the output of any command to a texy file by using the [b]>[/b} symbol eg:

```
sudo iptables -L -v > iptables.txt
```

---

### Post by bodhi.zazen on 2010-07-05
> **akelsall said:**
> I set up iptables based on the main HowTo. I'm running Ubuntu on my desktop. I have a wireless router that allows two other computers to attached to it. I'd like feedback as to whether or not this setup is secure enough. 

(I couldn't get the output to keep it's format, so I attached a screenshot for clarity). 


Thanks,

Andy

Define "Secure enough" 

Are you running any servers ? What are your trying to firewall ? What are you trying to block ? What do you want to allow ?

---

### Post by akelsall on 2010-07-06
bodhi, this is my home desktop only. It's not providing any kind of server function. Just looking to prevent any type of intrusion or malicious activity.

The main things I do with it are surf the 'Net and download files. Do I even need to worry about setting up a firewall in that case?

Thanks,

Andy

---

### Post by OpSecShellshock on 2010-07-06
> **akelsall said:**
> bodhi, this is my home desktop only. It's not providing any kind of server function. Just looking to prevent any type of intrusion or malicious activity.

The main things I do with it are surf the 'Net and download files. Do I even need to worry about setting up a firewall in that case?

Thanks,

Andy

Well, you mentioned above that there's a hardware firewall between your internet connection and the three computers in your home. In that sense, as long as that firewall isn't just allowing things through without their first having been requested from a device inside the network then you should be fine (in other words, if there are no forwarded ports on the router and UPnP is disabled).

It's not really possible to secure your systems against abstractions (except when I'm on billable time, in which case of course it is), so it's kind of tricky to say that it's sufficient against any malicious activity. Your devices won't be available to parties who attempt to make unsolicited connection initiations from the internet, but that's one very specific and noisy thing. The rest is going to be down to securing the browser, sticking to the repositories for software installation (unless you understand exactly what the other software is going to do when it's installed), and then not getting scammed.

---

### Post by bodhi.zazen on 2010-07-06
> **akelsall said:**
> bodhi, this is my home desktop only. It's not providing any kind of server function. Just looking to prevent any type of intrusion or malicious activity.

The main things I do with it are surf the 'Net and download files. Do I even need to worry about setting up a firewall in that case?

Thanks,

Andy

If this is on an Ubuntu desktop :

```
sudo ufw default deny
sudo ufw enable
```should be sufficient.

If this is a gateway for the other boxen, use a firewall specific distro such as ipcop or similar.

---

