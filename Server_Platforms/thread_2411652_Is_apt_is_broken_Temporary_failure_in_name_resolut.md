---
title: "Is apt is broken? Temporary failure in name resolution (18.04)"
date: 2019-02-01
forum: Server Platforms
---

### Post by Drone4four on 2019-02-01
My Ubuntu 18.04 DigitalOcean droplet server is toast as of two days ago and I have no idea why or what changed. I first noticed the issue when my vhosts became inaccessible. Then I tried to ssh in from my localhost (with rsa keys in place) and the ssh session timed out completely. The only way I can access my server right now is from the QEMU web front end provided by DigitalOcean in my browser.

Since I can&#8217;t use ssh from my local host in my gnome terminal emulator, I can&#8217;t copy and paste the output easily. So I had to take screenshots. I realize taking screenshots isn&#8217;t best practices, but I don&#8217;t see any alternative. 

These are the errors as they appear when I try to use apt: [https://i.imgur.com/KPw0WVV.png](https://i.imgur.com/KPw0WVV.png)

Some of the key points describing apt&#8217;s wonky behaviour transcribed as best I can in the above screen shot include errors such as: 
> 
Err 2 http://<DigitalOcean.com>
W: Failed to fetch <mirrors>.DigitalOcean./ubuntu bionic
W: Failed to fetch <security>.Ubuntu.com/ubuntu 
...
Some index files failed to download. They have been ignored, or old ones used instead.


To better diagnosis, I have tried entering these commands:
```

$ apt policy netplan
$ ip address
$ ip route
$ cat /etc/network/interfaces
$ cat /etc/resolv.conf
$ cat /etc/nsswitch.conf 
$ nslookup ubuntu.com
$ dig ubuntuforums.org
$ ping 192.168.40.20
```
Here is the output: 

For nslookup + dig: [https://i.imgur.com/hJ4mG4n.png](https://i.imgur.com/hJ4mG4n.png)
ip route: [https://i.imgur.com/cczPbRt.png](https://i.imgur.com/cczPbRt.png) 
apt policy + ip address: [https://i.imgur.com/Mi63ZfB.png](https://i.imgur.com/Mi63ZfB.png) 
cat resolv.conf + cat nsswitch:  [https://i.imgur.com/Bbyofbi.png](https://i.imgur.com/Bbyofbi.png) 

Other Ubuntu users report experiencing this same issue or other similar issues going back 16.04 and 14.04. I have come across different suggestions offered as workarounds. I have tried many. But I am still not getting anywhere.

As suggested elsewhere on a different forum, I tried temporarily turning off my firewall and running apt update and which didn&#8217;t fix the issue. I promptly turned my firewall back on.

Elsewhere it has been suggested that disabling and then re-enabling systemd-resolved might help. This didn&#8217;t work for me.

A similar issue described over on DigitalOcean called, "[Apt-get update failing with unable to resolve error]("https://www.digitalocean.com/community/questions/apt-get-update-failing-with-unable-to-resolve-error")"
A veteran forum member there suggested:
```
$ sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

```
This didn&#8217;t fix the issue for me either.

What else would you people recommend I could try next? What other more information could I provide  you people with so could better help me?

By the way: ATTN moderators: I realize that I made a similar post in someone else&#8217;s older thread [here]("https://ubuntuforums.org/showthread.php?t=2391351"). But it has been a 4 days  since my last post there and no one responded. I figured I could cross post here with a fresh pair of eyes with a different group of regular forum members. I thought that this issue is more appropriate for the server sub forum anyways.

---

### Post by barroncm on 2019-02-04
What does the network config look like?
Im guessing this is probably going to be a network misconfig issue, I had something similar in 18.04 when I didnt config DNS servers in my static ip config.

---

### Post by Drone4four on 2019-02-04
Here are the contents of /etc/network/interfaces: [https://i.imgur.com/RGeij6g.png](https://i.imgur.com/RGeij6g.png)

Here is the output of *$ ifconfig*: [https://i.imgur.com/G5kQKW8.png](https://i.imgur.com/G5kQKW8.png) 

**@barroncm**: Is there anything else I could provide to better clarify what the issue might be?

---

### Post by barroncm on 2019-02-04
So is this an upgrade to 18.04 or did you start the server at 18.04?
Im guessing its an upgrade. Otherwise you would be using netplan and not /etc/network/interfaces.
can you ping by domain name?
How about by ip?

---

### Post by Drone4four on 2019-02-05
Thanks **@barroncm** for your patience so far.

With my firewall turned off, pinging 8.8.8.8 seems to work. No packet loss. But pinging [www.google.com](www.google.com) yields: `Temporary failure in name resolution`. Another member of the Ubuntu community on FreeNode suggested I try: `ip -4 route add default via 104.131.14.1 dev eth0`. The resulting output is `RTNETLINK answers: File exists`. See here for the raw output of all of the above: [https://i.imgur.com/cmlu7B9.png](https://i.imgur.com/cmlu7B9.png) 

Since pinging 8.8.8.8 works, what does that show or indicate from your perspective?

For what it&#8217;s worth, the only file present in /etc/netplan/ is `50-cloud-init.yaml`. It&#8217;s contents can be found here: [https://i.imgur.com/tfnzcTo.png](https://i.imgur.com/tfnzcTo.png)

edit: To clarify, I did not upgrade. In May of 2018 I nuked my aging 14.04 droplet and spawned a fresh 18.04 droplet, which is what I am working with today.

---

### Post by Drone4four on 2019-02-15
For the better part of the last week I have been going back and forth with tech support reps with DigitalOcean. They couldn't figure it out either. The front line rep eventually escalated to Developer Support who still can't help.

When running apt, the original DNS issue is still present. See here:  [https://i.imgur.com/kHaFNHF.png](https://i.imgur.com/kHaFNHF.png)

The escalations rep yesterday had me paint a more comprehensive picture of my networking stack. Here are the commands he suggested and their output:

[COLOR="#006400"]**$ cat /etc/netplan/50-cloud-init.yaml**[/COLOR]: [https://i.imgur.com/jumdfze.png](https://i.imgur.com/jumdfze.png)

[COLOR="#006400"]**$ ip addr**[/COLOR]: [https://i.imgur.com/qLLXncr.png](https://i.imgur.com/qLLXncr.png)

[COLOR="#006400"]**$ ip route, uname -a, ls -l /lib/modules**[/COLOR]: [https://imgur.com/HuG1EhN.png](https://imgur.com/HuG1EhN.png)

[COLOR="#006400"]**$ cat /etc/udev/rules.d/70-persistent-net.rules**[/COLOR]: This file doesn't exist. The only file found Inside /etc/udev/rules.d/ is a file named 99-digitalocean-automount.rules. The contents are 30 lines long. Here are two screenshots:
Lines 1-19: [https://i.imgur.com/5ABdgcn.png](https://i.imgur.com/5ABdgcn.png) 
Lines 19-30: [https://i.imgur.com/RqCiQJL.png](https://i.imgur.com/RqCiQJL.png)

[COLOR="#006400"]**$ sudo iptables -nvL --line-numbers**[/COLOR]: I can't take screenshots of this output because the output is some 180 lines long. If I had ssh access, this would be easy. But for now I am stuck with the web-based Droplet Console so the only way for me to convey information is with screenshots.

The Developer Support Escalations rep responded with: > All of that information looks fine as well, so again it's a bit of a head-scratcher here. Can you try taking a snapshot of this Droplet and then creating a new Droplet from that snapshot - then get back to us if it has the same issues? I've added a bit of credit to your account to pay for this testing. 

He also suggested that I take a snapshot. So with a new Droplet with this new snapshot, apt is still broken. See here: [https://i.imgur.com/UvXxf21.png](https://i.imgur.com/UvXxf21.png)

I'm wondering if I should file a bug report upstream. Another DO user encountered the same issue last year on 16.04: [https://www.digitalocean.com/community/questions/temporary-failure-resolving-digitalocean-mirrors](https://www.digitalocean.com/community/questions/temporary-failure-resolving-digitalocean-mirrors)
Unfortunately this user never received an answer.

An Ubuntu user elsewhere encountered a similar issue on 14.04: [https://askubuntu.com/questions/892569/apt-get-update-not-working-in-ubuntu-16-04-temporary-failure-resolving/954108#954108](https://askubuntu.com/questions/892569/apt-get-update-not-working-in-ubuntu-16-04-temporary-failure-resolving/954108#954108)

My final remark: > I'd be willing to delete my web content on my Droplet and hand over the keys to developers at Canonical to investigate further. But the problem with that outcome is the only way to access the shell on my Droplet is from the DigitalOcean Web Console which is bound to my DO Dashboard. It's not like I can grant Canonical remote access because ssh'ing in is not possible. The other problem with this end result is that it involves the minor inconvenience of me setting up my LAMP stack again from scratch. If this is what it comes down to, I understand. I just hope this is a one-off issue and I never encounter it again.

Before I go ahead and nuke my Droplet and rebuild my LAMP stack from scratch next week, I was hoping someone here in the Ubuntu community might be able to provide further clarity.

---

