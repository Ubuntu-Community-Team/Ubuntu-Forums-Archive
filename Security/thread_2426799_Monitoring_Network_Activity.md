---
title: "Monitoring Network Activity"
date: 2019-09-13
forum: Security
---

### Post by jamesdinyorks on 2019-09-13
I've recenty installed UFW, however i'm after something that can analyse the logs it creates. I seem to be experiencing a spike in activity. I'm using wireshark to carry out some initial investigations. 

However it would be useful to have some logging creeated from UFW. 

As with other posts can someone direct me to a AV/Malware detection package. I use Norton on my windows instance, but they dont support ubuntu.

---

### Post by uRock on 2019-09-13
> **jamesdinyorks said:**
> I've recenty installed UFW, however i'm after something that can analyse the logs it creates. I seem to be experiencing a spike in activity. I'm using wireshark to carry out some initial investigations. 

However it would be useful to have some logging creeated from UFW. 

As with other posts can someone direct me to a AV/Malware detection package. I use Norton on my windows instance, but they dont support ubuntu.

Hello and welcome to the forums,

ClamAV can be installed from the repos, but you don't need an AV for Linux. I haven't used any of the apps mentioned in this link, but I am sure someone else may reply who has. [https://www.tecmint.com/linux-network-bandwidth-monitoring-tools/](https://www.tecmint.com/linux-network-bandwidth-monitoring-tools/)

---

### Post by (kyT%0) on 2019-09-15
> **jamesdinyorks said:**
> However it would be useful to have some logging creeated from UFW.

the gui for the ufw has a section / tab called logs if that is what you are looking for. to install :

```
sudo apt install gufw
```

> **jamesdinyorks said:**
> As with other posts can someone direct me to a AV/Malware detection  package.

as stated above, if you want you can get clamav & also clamtk which is the gui for clamav. to install :

```
sudo apt install clamav
```

```
sudo apt install clamtk
```

---

### Post by ecophobia on 2019-10-01
> **jamesdinyorks said:**
> I've recenty installed UFW, however i'm after something that can analyse the logs it creates. I seem to be experiencing a spike in activity. I'm using wireshark to carry out some initial investigations. 

However it would be useful to have some logging creeated from UFW. 

As with other posts can someone direct me to a AV/Malware detection package. I use Norton on my windows instance, but they dont support ubuntu.

UFW does create logs (see below) or for more advanced firewall you can use [Shorewall]("http://www.shorewall.net/")

[FONT=monospace]sudo ufw logging on[/FONT]

---

