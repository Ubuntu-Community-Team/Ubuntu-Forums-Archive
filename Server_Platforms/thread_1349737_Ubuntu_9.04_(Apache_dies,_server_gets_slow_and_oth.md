---
title: "Ubuntu 9.04 (Apache dies, server gets slow and other questions)"
date: 2009-12-08
forum: Server Platforms
---

### Post by ravingmad on 2009-12-08
Hi all, still quite a noob with Ubuntu but learned enough through forums to get an Ubuntu 9.04 set up running on VMware and web sites running on Apache with mySQL and PHP, no problem there. I've been hosting on Windows Servers for 18 years but decided a few months ago to give Ubuntu a real run for it's money. So far I've run into a couple of snags that seriously worry me as far as a mission critical stable platform goes.

What happens almost every week is that suddenly all web sites stop responding for no apparent reason. I then have to reboot the box and then all is working again for approximately another week until mysteriously one night I call a site in the browser and discover that all is dead. 
What can cause this and how can I prevent this?? 
Where can I check what is causing this??
Is there someway to restart Apache and relevant services once a day??

Secondly, being new to Ubuntu I loaded Gnome after the server install to have a more familiar interface to work with. Somehow I think this has brought along with it some problems. If I reboot the box it will not ping or respond to any outside network activity, no web sites will respond etc until I physically log in. Why can the "server" not just start "serving" without anyone being logged in? I've never experienced this kind of behaviour in all my time running Windows Servers and cannot believe that this behaviour is by design with Ubuntu. Can anyone elaborate on this or suggest a way for this to NOT happen?

Thirdly, as far as firewalls go, I read so many varying opinions on Ubuntu's firewall. Some people say it's not needed, that Ubuntu is secure on it's own. Others say the exact opposite. Being security conscious I tried UFW, applied some rules which appeared to work ok until I started outside testing and could still penetrate ports that I had specifically closed which concerned me. Then one day after a reboot I could access nothing from outside and had to turn UFW off completely and have not really looked further into it. What is the best firewall solution, I'm guessing straight IP tables but have yet to find a guide that speaks simple english or maybe I am not looking in the right place :)

I would really appreciate anyone who has some time to help me and answer some of my questions and give any advice. Would also like to know if choosing 9.04 was a big mistake or not, should I have used an older more robust 8.04 install?

Thanks in Advance

---

### Post by cdenley on 2009-12-08
1. Check your logs.
```

less /var/log/apache2/error.log

```
If you don't need to enter a password to decrypt any SSL certificated, then you can create a cronjob to restart the service daily, but I would try to actually fix the problem. Run this when apache doesn't seem to be working properly, then post the output here.
```

sudo ps -ef|grep apache
sudo lsof -n -i :80
echo -e "HEAD / HTTP/1.0\n"|nc localhost 80

```

2. That sounds like with gnome, you started using NetworkManager to configure your network interfaces. On a server, you should configure your network interfaces by editing /etc/network/interfaces. Once a device is configured in that file, NetworkManager should ignore it, I believe.

3. If you want a very simple firewall to filter inbound traffic, then UFW is the way to go. What kind of server processes were you able to access from outside?

4. I suggest 8.04, unless there is a feature in a newer version you really needed. On a server, it is better to upgrade every two years rather than every six months. Also, I think server software is used more often on LTS releases, so bugs tend to be found and fixed quicker in those versions. 9.04 is no longer the most current release. You will need to upgrade to 9.10 at some point. Perhaps an upgrade would solve some problems.

---

### Post by ravingmad on 2009-12-09
Hi cdenley

Thanks so much for your reply.

I checked the apache logs and found that a wordpress plugin (feedwordpress) which syndicates content from rss feeds would every now again encounter a hiccup and this error would just loop and loop bringing the whole of apache down with it. After some investigation I found which particular RSS feeds were causing this and removed them. So far all seems to be ok, I also found another error in the apache logs which required me to enable the includes and ssl modules in apache and that error is now also gone .... so I'm making some progress. Now that I know where to check I will check daily now for errors and keep ahead of the game this time.

As for Gnome and Network manager, I tried at one point to remove all devices from network manager and configure them using /etc/network/interfaces but could not get my networking to work at all so I had to revert back to network manager for now. When things quieten down in December I will spend some time and try and get this sorted for good. How would you suggest I tackle the switch over? First configure /etc/network/interfaces and then remove devices from network manager or completely uninstall network manager??? The problem I had last time was that I uninstalled network manager and due to a lack of no networking I could not even access the internet to re-download it .... lord knows how I fixed it eventually but I did, which is why I am hesitant to tamper with it now.

I did also try the 9.10 upgrade which is actually when all my networking went wrong in the first place, I then reverted back to a snapshot but still had problems getting my networking back online again so I think i will stick with 9.04 for the time being.

I will try UFW again when things quieten down and do some thorough testing, reboots etc to make sure all is dandy.

Thank so much again for your input.

---

