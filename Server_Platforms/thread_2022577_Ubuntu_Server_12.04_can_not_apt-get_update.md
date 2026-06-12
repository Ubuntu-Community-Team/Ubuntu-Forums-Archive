---
title: "Ubuntu Server 12.04 can not apt-get update"
date: 2012-07-11
forum: Server Platforms
---

### Post by xiaoxiong.100 on 2012-07-11
I can ping to the source server, but can not apt-get update, even download some files from the source server with wget.

Test1: ping security.ubuntu.com
=> OK

Test2: wget security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en.bz2
=>errors as follow:
--2012-07-11 17:36:26--  [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en.bz2)
Resolving security.ubuntu.com (security.ubuntu.com)... 91.189.92.184, 91.189.92.151, 91.189.92.166, ...
Connecting to security.ubuntu.com (security.ubuntu.com)|91.189.92.184|:80... failed: Connection timed out.
Connecting to security.ubuntu.com (security.ubuntu.com)|91.189.92.151|:80... ^C

Test3: visit the website with my laptop based on Ubuntu Desktop 10.10 witch located in the same network, and download the file:security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en.bz2
=> OK

Test 4: sudo apt-get update:
=> errrors as follow:
....
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en_US  
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources/DiffIndex
...
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]

...
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_US)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.


Test 5: sudo apt-get update in my laptop based on Ubuntu Desktop 10.10 (same network)
=> OK.

can not sudo apt-get update successfully even I change the source.list with mirrores.163.com, [cn.archive.ubuntu.com]("http://us.archive.ubuntu.com") and [tw.archive.ubuntu.com]("http://us.archive.ubuntu.com").  In this case, I can not install my subversion my my new server. Any buddy could give me some indication for resolve this problem? Thanks in advance!!!

---

### Post by xiaoxiong.100 on 2012-07-11
It is time go home, I will check tomorrow morning. Thanks every one!

---

### Post by papibe on 2012-07-11
Hi xiaoxiong.100. Welcome to the forums!

It looks like either the repository is down, or not accessible from where you are.

If you are not in a hurry, wait a while and try again. It should be up soon.

There's a way to find alternative repository servers on the Desktop Edition. Check the 'Download Server' section in this [help document]("https://help.ubuntu.com/community/Repositories/Ubuntu").

If you are in a hurry, you may do that on a desktop and then modify your sources on the server, but it is a delicate operation.

Tell us if you need more help with that.
Regards.

---

### Post by sanderj on 2012-07-11
Can the Ubuntu Server 12.04 visit any website at all? For example [www.google.com](www.google.com) and [www.baidu.com](www.baidu.com) using wget and using the webbrowser?

If so, I would say the Great Firewall is interfering (assuming you're in China): "security.ubuntu.com" may alert the Great Firewall.

If not, I would say it's a proxy setting problem

---

### Post by wojox on 2012-07-11
I think it's a VM problem maybe. :confused:

---

### Post by xiaoxiong.100 on 2012-07-11
Hi [[COLOR=#DD4814]**papibe**[/COLOR]]("http://ubuntuforums.org/member.php?u=774785"),
It is so nice to see your reply for my first post here ubuntufoums.org. Thanks so much!

Yours "It looks like either the repository is down"
=> I don't think so, since I tried many other repository.

"If you are in a hurry, you may do that on a desktop and then modify your sources on the server, but it is a delicate operation."
=> As I wrote in my post, It works in my laptop based on Ubuntu 10.10 Desktop (HP 6930), but can not works in my new server based on Ubuntu 12.04 Server (Dell R410). And both laptop and server are locate in the same network.

Appreciate for reply my first post here! Ha...

---

### Post by papibe on 2012-07-11
Let's discard a problem with network configuration (as sanderj suggested it).

Could you post the results of these commands?
```
ifconfig

route -n

nslookup ubuntu.com

dig ubuntu.com
```
Regards.

---

### Post by xiaoxiong.100 on 2012-07-11
> **sanderj said:**
> Can the Ubuntu Server 12.04 visit any website at all? For example [www.google.com]("http://www.google.com") and [www.baidu.com]("http://www.baidu.com") using wget and using the webbrowser?

If so, I would say the Great Firewall is interfering (assuming you're in China): "security.ubuntu.com" may alert the Great Firewall.

If not, I would say it's a proxy setting problem

=> Without GUI, I don't know how to visit google or baidu. But I can ping success to both [www.google.com](www.google.com) and [www.baidu.com](www.baidu.com). With the wget, I can not download anything from [http://mirrors.163.com/ubuntu/](http://mirrors.163.com/ubuntu/). 
I don't think it is firewall problem, since as I wrote in my post that my PC could execute the apt-get update which locate in the same network.
Yes, It could be the proxy setting problem. But I don't know how to set in Server without GUI. Appreciate if you can support!

---

### Post by xiaoxiong.100 on 2012-07-11
> **wojox said:**
> I think it's a VM problem maybe. :confused:
=> No, it is not a server in VM, but Dell R410 brand new server. Thanks.

---

### Post by xiaoxiong.100 on 2012-07-11
> **papibe said:**
> Let's discard a problem with network configuration (as sanderj suggested it).

Could you post the results of these commands?
```
ifconfig

route -n

nslookup ubuntu.com

dig ubuntu.com
```Regards.

=> Thanks for your quick reply! Please review the result from my terminal (Back groud: eth0 is connected from a ADSL router, and eth1 is connected from our company router):
userveradmin@Mustang:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr d4:ae:52:90:9e:c8  
          inet addr:192.168.100.17  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::d6ae:52ff:fe90:9ec8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:627117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:715918 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:190211451 (190.2 MB)  TX bytes:578061851 (578.0 MB)
          Interrupt:36 Memory:da000000-da012800 

eth1      Link encap:Ethernet  HWaddr d4:ae:52:90:9e:c9  
          inet addr:192.168.25.17  Bcast:192.168.25.255  Mask:255.255.255.0
          inet6 addr: fe80::d6ae:52ff:fe90:9ec9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1612484 errors:0 dropped:200 overruns:0 frame:0
          TX packets:1303935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:462020713 (462.0 MB)  TX bytes:779532249 (779.5 MB)
          Interrupt:48 Memory:dc000000-dc012800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:147681 errors:0 dropped:0 overruns:0 frame:0
          TX packets:147681 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29746248 (29.7 MB)  TX bytes:29746248 (29.7 MB)

virbr0    Link encap:Ethernet  HWaddr 36:00:04:18:43:10  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

userveradmin@Mustang:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.25.1    0.0.0.0         UG    100    0        0 eth1
192.168.25.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.100.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
userveradmin@Mustang:~$ nslookup ubuntu.com
Server:        192.168.30.28
Address:    192.168.30.28#53

Non-authoritative answer:
Name:    ubuntu.com
Address: 91.189.94.156

userveradmin@Mustang:~$ dig ubuntu.com

; <<>> DiG 9.8.1-P1 <<>> ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 3352
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ubuntu.com.            IN    A

;; ANSWER SECTION:
ubuntu.com.        594    IN    A    91.189.94.156

;; Query time: 0 msec
;; SERVER: 192.168.30.28#53(192.168.30.28)
;; WHEN: Wed Jul 11 19:52:28 2012
;; MSG SIZE  rcvd: 44

---

### Post by sanderj on 2012-07-11
> **papibe said:**
> Let's discard a problem with network configuration (as sanderj suggested it).

Could you post the results of these commands?
```
ifconfig

route -n

nslookup ubuntu.com

dig ubuntu.com
```
Regards.

I don't think there is an IP / routing network problem, as the OP's "ping security.ubuntu.com" is OK. It must be something with a Proxy or Firewall

---

### Post by xiaoxiong.100 on 2012-07-11
> **sanderj said:**
> I don't think there is an IP / routing network problem, as the OP "ping security.ubuntu.com" is OK. It must be something with Proxy or Firewall
=> Could be. But would you please indicate how to check the proxy in my server without GUI? Thanks.

---

### Post by papibe on 2012-07-11
Thanks.

It looks like the default route points to the company network.

Does that network have access to the internet, or does it block some sites?

Regards.

---

### Post by xiaoxiong.100 on 2012-07-11
Hi every one, one more information:
after execute the command sudo apt-get update, it will stop for about minutes with information:
0% [Connecting to us.archive.ubuntu.com (91.189.91.25)] [Connecting to security.ubuntu.com (91.189.92.184)]

And than pop up the error message in my post.

---

### Post by sanderj on 2012-07-11
On **both** your server and your laptop, can you do this, and post the output here:


```

printenv | grep -i proxy
wget --no-proxy www.baidu.com
wget www.baidu.com
mtr -nrc4 security.ubuntu.com

```

This will make clear if there is a proxy set, and if wget works without proxy.

EDIT: The mtr command will show to route to security.ubuntu.com. I expect it to be OK as you say your ping works OK.

HTH

---

### Post by xiaoxiong.100 on 2012-07-11
> **papibe said:**
> Thanks.

It looks like the default route points to the company network.

Does that network have access to the internet, or does it block some sites?

Regards.
=> Looks the possible root cause. But there is a separate IT department to maintain the company network. I have no idea right now since I am guy from Development department. But I think there must be some way to change the default route points. Do you have any idea to achieve it? Thanks!:P

---

### Post by xiaoxiong.100 on 2012-07-11
> **sanderj said:**
> On **both** your server and your laptop, can you do this, and post the output here:


```

printenv | grep -i proxy
wget --no-proxy www.baidu.com
wget www.baidu.com

```This will make clear if there is a proxy set, and if wget works without proxy.

HTH
=> Results from my laptop:
sam@SamUb:~$ printenv | grep -i proxy
UBUNTU_MENUPROXY=libappmenu.so
sam@SamUb:~$ wget --no-proxy [www.baidu.com](www.baidu.com)
--2012-07-11 20:09:51--  [http://www.baidu.com/](http://www.baidu.com/)
Resolving [www.baidu.com](www.baidu.com)... 220.181.111.148, 220.181.112.143
Connecting to [www.baidu.com|220.181.111.148|:80](www.baidu.com|220.181.111.148|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8028 (7.8K) [text/html]
Saving to: `index.html'

100%[======================================>] 8,028       --.-K/s   in 0.03s   

2012-07-11 20:09:53 (253 KB/s) - `index.html' saved [8028/8028]

sam@SamUb:~$ wget [www.baidu.com](www.baidu.com)
--2012-07-11 20:10:05--  [http://www.baidu.com/](http://www.baidu.com/)
Resolving [www.baidu.com](www.baidu.com)... 220.181.111.148, 220.181.112.143
Connecting to [www.baidu.com|220.181.111.148|:80](www.baidu.com|220.181.111.148|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8024 (7.8K) [text/html]
Saving to: `index.html.1'

100%[======================================>] 8,024       --.-K/s   in 0.03s   

2012-07-11 20:10:06 (259 KB/s) - `index.html.1' saved [8024/8024]
:P


=> Results from my server:
eradmin@Mustang:~$ printenv | grep -i proxy
userveradmin@Mustang:~$ wget --no-proxy [www.baidu.com](www.baidu.com)
--2012-07-11 20:09:16--  [http://www.baidu.com/](http://www.baidu.com/)
Resolving [www.baidu.com](www.baidu.com) ([www.baidu.com](www.baidu.com))... 220.181.112.143, 220.181.111.148
Connecting to [www.baidu.com](www.baidu.com) ([www.baidu.com)|220.181.112.143|:80](www.baidu.com)|220.181.112.143|:80)... failed: Connection timed out.
Connecting to [www.baidu.com](www.baidu.com) ([www.baidu.com)|220.181.111.148|:80](www.baidu.com)|220.181.111.148|:80)... ^C
userveradmin@Mustang:~$ wget [www.baidu.com](www.baidu.com)
--2012-07-11 20:11:10--  [http://www.baidu.com/](http://www.baidu.com/)
Resolving [www.baidu.com](www.baidu.com) ([www.baidu.com](www.baidu.com))... 220.181.111.148, 220.181.112.143
Connecting to [www.baidu.com](www.baidu.com) ([www.baidu.com)|220.181.111.148|:80](www.baidu.com)|220.181.111.148|:80)... failed: Connection timed out.
Connecting to [www.baidu.com](www.baidu.com) ([www.baidu.com)|220.181.112.143|:80](www.baidu.com)|220.181.112.143|:80)... ^C
:(

---

### Post by sanderj on 2012-07-11
So:

the laptop uses no proxy, and can succesfully connect. That means there is no Proxy needed. Good.
the server has no proxy set, but cannot connect at all via HTTP (but ping works, right?)

I added a "mtr" command to my post. Can you execute that too on both your laptop and server?

If laptop and server are really on the same LAN (which we can see via the mtr output), I'm starting to wonder if you have put a firewall on your own server ...

---

### Post by papibe on 2012-07-11
I have a couple of ideas.

Easiest: unplug your company ethernet cable, and run:
```
sudo service networking restart
```
Try updating again. If that does not work post the routes again:
```
route -n
```

The other one is a little more complex: adjusting your default route so you gain access to the ethernet using your DSL connection.

Tell us how it goes.
Regards.

---

### Post by xiaoxiong.100 on 2012-07-11
> **sanderj said:**
> So:

the laptop uses no proxy, and can succesfully connect. That means there is no Proxy needed. Good.
the server has no proxy set, but cannot connect at all via HTTP (but ping works, right?)

I added a "mtr" command to my post. Can you execute that too on both your laptop and server?

If laptop and server are really on the same LAN (which we can see via the mtr output), I'm starting to wonder if you have put a firewall on your own server ...
=>no copy support for this command. so, let me write by my self:
result from my laptop:
Host               Loss%   Snt    Last    Avg    Best    Wrst   StDev
1.localhost       0.0%    133    0.1      0.0    0.0     0.1       0.0

Result from my server:
Host               Loss%   Snt    Last    Avg    Best    Wrst   StDev
1.localhost       0.0%    144    0.0      0.0    0.0     0.1       0.0

---

### Post by sanderj on 2012-07-11
> **xiaoxiong.100 said:**
> =>no copy support for this command. so, let me write by my self:
result from my laptop:
Host               Loss%   Snt    Last    Avg    Best    Wrst   StDev
1.localhost       0.0%    133    0.1      0.0    0.0     0.1       0.0

Result from my server:
Host               Loss%   Snt    Last    Avg    Best    Wrst   StDev
1.localhost       0.0%    144    0.0      0.0    0.0     0.1       0.0

"no copy support for this command"? Just select with your mouse, and middle-click to paste it here in this forum.

Anyway: just one line? It should give 5 - 15 lines of output.

Oh, wait, you just typed "mtr"? You should type "mtr -nrc4 security.ubuntu.com" as stated in my post.

```
mtr -nrc4 security.ubuntu.com
```


HTH

---

### Post by xiaoxiong.100 on 2012-07-11
> **papibe said:**
> I have a couple of ideas.

Easiest: unplug your company ethernet cable, and run:
```
sudo service networking restart
```Try updating again. If that does not work post the routes again:
```
route -n
```The other one is a little more complex: adjusting your default route so you gain access to the ethernet using your DSL connection.

Tell us how it goes.
Regards.

=> Aha... I can not unplug the cable, since my server has install in IT department server house. But I tried sudo ifconfig eth1 down, and then sudo ifconfig eth1 up. But the result is the same. I can not down the eth0, since I am using this for the terminal.

=> How to "adjusting your default route "? I have no any knowledge about this.

---

### Post by xiaoxiong.100 on 2012-07-11
> **sanderj said:**
> "no copy support for this command"? Just select with your mouse, and middle-click to paste it here in this forum.

Anyway: just one line? It should give 5 - 15 lines of output.

Oh, wait, you just typed "mtr"? You should type "mtr -nrc4 security.ubuntu.com" as stated in my post.

```
mtr -nrc4 security.ubuntu.com
```
HTH

=> Sorry for my mistake! Please review the result again:
Results from laptop:
sam@SamUb:~$ mtr -nrc4 security.ubuntu.com
HOST: SamUb                       Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- ???                       100.0     4    0.0   0.0   0.0   0.0   0.0
  2.|-- 192.168.100.1              0.0%     4    1.9   1.9   1.8   2.0   0.1
  3.|-- ???                       100.0     4    0.0   0.0   0.0   0.0   0.0
  4.|-- 121.34.247.13             25.0%     4   23.8  23.3  22.6  23.8   0.6
  5.|-- 121.15.179.58             25.0%     4   22.8  36.0  22.8  62.0  22.5
  6.|-- 121.34.242.222             0.0%     4   26.3  26.5  25.9  27.6   0.7
  7.|-- 202.97.33.118              0.0%     4   25.5  25.4  24.8  25.8   0.4
  8.|-- 202.97.60.206              0.0%     4   26.8  27.2  26.8  27.8   0.5
  9.|-- 202.97.51.162             25.0%     4  217.9 212.9 207.6 217.9   5.2
 10.|-- 202.97.90.10              75.0%     4  182.2 182.2 182.2 182.2   0.0
 11.|-- 4.53.228.129              50.0%     4  267.8 267.1 266.5 267.8   0.9
 12.|-- 4.69.144.254               0.0%     4  274.8 274.3 273.0 275.3   1.0
 13.|-- 4.69.137.29               75.0%     4  276.2 276.2 276.2 276.2   0.0
 14.|-- 4.69.148.202              25.0%     4  211.3 211.6 211.3 211.8   0.3
 15.|-- 4.69.148.109              25.0%     4  200.9 197.5 195.2 200.9   3.0
 16.|-- 4.69.148.138               0.0%     4  204.0 203.4 202.6 204.0   0.7
 17.|-- 4.69.135.186              33.3%     3  265.1 264.8 264.4 265.1   0.5
 18.|-- 4.69.148.34                0.0%     3  277.4 278.5 276.3 281.7   2.9
 19.|-- 4.69.134.65               66.7%     3  264.2 264.2 264.2 264.2   0.0
 20.|-- 4.69.137.73               33.3%     3  334.5 334.0 333.6 334.5   0.6
 21.|-- ???                       100.0     3    0.0   0.0   0.0   0.0   0.0
 22.|-- ???                       100.0     2    0.0   0.0   0.0   0.0   0.0
 23.|-- ???                       100.0     2    0.0   0.0   0.0   0.0   0.0
 24.|-- 91.189.92.151             50.0%     2  334.1 334.1 334.1 334.1   0.0
sam@SamUb:~$ mtr -nrc4 us.ubuntu.com
HOST: SamUb                       Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- ???                       100.0     4    0.0   0.0   0.0   0.0   0.0
  2.|-- 192.168.100.1              0.0%     4    1.9   2.0   1.9   2.0   0.1
  3.|-- ???                       100.0     4    0.0   0.0   0.0   0.0   0.0
  4.|-- 121.34.247.13              0.0%     4   23.2  24.2  22.2  26.9   2.1
  5.|-- 121.15.179.78              0.0%     4   23.9  23.2  22.6  23.9   0.6
  6.|-- 119.145.47.58              0.0%     4   25.9  25.4  25.1  25.9   0.4
  7.|-- 61.140.0.17                0.0%     4   25.7  26.2  25.7  27.0   0.6
  8.|-- 121.10.40.155              0.0%     4   26.7  25.6  24.5  26.7   1.2


Result from server:
userveradmin@Mustang:~$ mtr -nrc4 security.ubuntu.com
Failed to resolve host: Name or service not known
userveradmin@Mustang:~$ mtr -nrc4 us.ubuntu.com
Failed to resolve host: Name or service not known

---

### Post by sanderj on 2012-07-11
> **xiaoxiong.100 said:**
> 

Result from server:
userveradmin@Mustang:~$ mtr -nrc4 security.ubuntu.com
Failed to resolve host: Name or service not known
userveradmin@Mustang:~$ mtr -nrc4 us.ubuntu.com
Failed to resolve host: Name or service not known

Ouch ... now even no name resolving anymore? :(

Let's solve that later; first your IP network. What is output of:

```
mtr -nrc4 91.189.92.151 
```

Post the output here ...

---

### Post by xiaoxiong.100 on 2012-07-11
> **sanderj said:**
> Ouch ... now even no name resolving anymore? :(

Let's solve that later; first your IP network. What is output of:

```
mtr -nrc4 91.189.92.151 
```Post the output here ...

=> After sudo /etc/init.d/networking restart, resolving works with security.ubuntu.com:

userveradmin@Mustang:~$ mtr -nrc4 security.ubuntu.com
HOST: Mustang                     Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.25.22              0.0%     4    1.8   8.1   1.8  26.3  12.1
  2.|-- 172.12.1.1                 0.0%     4    2.6   1.7   0.4   2.6   1.0
  3.|-- 58.61.147.222              0.0%     4    1.4   2.1   0.9   4.1   1.4
  4.|-- 58.60.24.166               0.0%     4    4.0   3.1   1.0   6.2   2.5
  5.|-- 121.15.179.78              0.0%     4    5.2   3.6   1.3   5.2   1.7
  6.|-- 119.145.47.62              0.0%     4    7.4   9.5   7.4  11.3   1.8
  7.|-- 202.97.35.190              0.0%     4    9.6   7.6   5.7   9.6   1.7
  8.|-- 202.97.60.158              0.0%     4    9.0   8.3   6.8  10.3   1.7
  9.|-- 202.97.58.234              0.0%     4  176.6 177.0 174.7 180.4   2.4
 10.|-- 202.97.50.66               0.0%     4  178.6 178.1 177.0 179.4   1.1
 11.|-- 4.71.114.101               0.0%     4  185.1 189.9 185.1 199.3   6.4
 12.|-- 4.69.152.126              50.0%     4  189.9 184.5 179.1 189.9   7.6
 13.|-- 4.69.153.5                 0.0%     4  197.0 196.1 195.1 197.0   0.8
 14.|-- 4.69.135.186              50.0%     4  251.5 250.1 248.8 251.5   1.9
 15.|-- 4.69.148.46               25.0%     4  249.0 250.1 247.8 253.6   3.0
 16.|-- 4.69.134.77               75.0%     4  248.4 248.4 248.4 248.4   0.0
 17.|-- 4.69.137.77               50.0%     4  328.1 330.6 328.1 333.1   3.5
 18.|-- 4.69.153.138              25.0%     4  326.3 327.9 326.3 329.1   1.4
 19.|-- ???                       100.0     4    0.0   0.0   0.0   0.0   0.0
 20.|-- 212.113.14.198            25.0%     4  315.8 316.9 315.8 317.7   1.0
 21.|-- 91.189.92.166             25.0%     4  321.0 320.6 320.2 321.0   0.4

But still can not works with us.ubuntu.com
userveradmin@Mustang:~$ mtr -nrc4 us.ubuntu.com
Failed to resolve host: Name or service not known

attached mtr IP in my server:
userveradmin@Mustang:~$ mtr -nrc4 91.189.92.151
HOST: Mustang                     Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.25.22              0.0%     4    1.9   2.4   1.8   4.0   1.1
  2.|-- 172.12.1.1                 0.0%     4    2.2   1.2   0.3   2.2   1.0
  3.|-- 58.61.147.222             75.0%     4    2.9   2.9   2.9   2.9   0.0
  4.|-- 58.60.24.166               0.0%     4    3.6   4.1   3.5   5.6   1.0
  5.|-- 119.145.220.90             0.0%     4    3.7   3.2   2.2   3.7   0.7
  6.|-- 119.145.47.54              0.0%     4    4.2   4.5   3.6   6.3   1.2
  7.|-- 202.97.33.118              0.0%     4    5.5   6.8   5.2  10.1   2.2
  8.|-- 202.97.61.226              0.0%     4    6.0   6.1   5.5   7.0   0.6
  9.|-- 202.97.51.42               0.0%     4  182.5 181.9 180.3 182.8   1.1
 10.|-- 202.97.90.10               0.0%     4  202.7 202.4 199.2 206.3   2.9
 11.|-- 4.53.228.129               0.0%     4  260.8 262.0 260.0 264.4   2.0
 12.|-- 4.69.144.190               0.0%     4  254.7 257.4 254.7 259.7   2.1
 13.|-- 4.69.137.25               25.0%     4  251.4 252.4 251.4 253.8   1.2
 14.|-- 4.69.148.202              25.0%     4  185.0 183.0 182.0 185.0   1.7
 15.|-- 4.69.148.109              25.0%     4  185.6 178.0 173.4 185.6   6.6
 16.|-- 4.69.148.138              25.0%     4  175.7 176.9 175.7 178.6   1.5
 17.|-- 4.69.135.186              25.0%     4  244.9 244.0 243.5 244.9   0.8
 18.|-- 4.69.148.46               50.0%     4  251.7 247.5 243.3 251.7   5.9
 19.|-- 4.69.134.77                0.0%     4  241.3 242.8 241.3 244.9   1.6
 20.|-- 4.69.137.73               50.0%     4  322.1 323.1 322.1 324.0   1.4
 21.|-- 4.69.153.134              25.0%     4  311.3 317.3 311.3 320.7   5.2
 22.|-- 4.69.139.106              50.0%     4  315.8 313.5 311.2 315.8   3.3
 23.|-- 212.113.14.198            25.0%     4  309.0 309.6 309.0 310.7   1.0
 24.|-- 91.189.92.151             25.0%     4  313.5 313.0 312.7 313.5   0.4

---

### Post by papibe on 2012-07-11
The correct repository address is:
```
us.archive.ubuntu.com 
```
Regards.

---

### Post by xiaoxiong.100 on 2012-07-11
Thank you [[COLOR=#DD4814]**papibe**[/COLOR]]("http://ubuntuforums.org/member.php?u=774785")! thank you [sanderj!]("http://ubuntuforums.org/member.php?u=754333")
It is 9:00 PM here. My wife is calling me! I have to stop my overtime! I will check tomorrow morning!
Appreciate for your support!

---

### Post by sanderj on 2012-07-11
Server:

userveradmin@Mustang:~$ mtr -nrc4 security.ubuntu.com
HOST: Mustang Loss% Snt Last Avg Best Wrst StDev
1.|-- 192.168.25.22 0.0% 4 1.8 8.1 1.8 26.3 12.1
2.|-- 172.12.1.1 0.0% 4 2.6 1.7 0.4 2.6 1.0
3.|-- 58.61.147.222 0.0% 4 1.4 2.1 0.9 4.1 1.4

Laptop:

sam@SamUb:~$ mtr -nrc4 security.ubuntu.com
HOST: SamUb Loss% Snt Last Avg Best Wrst StDev
1.|-- ??? 100.0 4 0.0 0.0 0.0 0.0 0.0
2.|-- 192.168.100.1 0.0% 4 1.9 1.9 1.8 2.0 0.1
3.|-- ??? 100.0 4 0.0 0.0 0.0 0.0 0.0
4.|-- 121.34.247.13 25.0% 4 23.8 23.3 22.6 23.8 0.6

Your server and your laptop show different routes / different IP addresses. And your server is on 192.168.25.x, whereas your laptop is on 192.168.100.x. So I would say they are on different LANs.

Furthermore your name resolving is not working correctly.

Are you sure you did not install a firewall on your own Ubuntu Server?
Another approach would be to boot a Ubuntu live-CD in the server, but I believe you have no physical access to the system?

If so, I would talk to the IT department what is going on.

---

### Post by mmib on 2012-07-11
I have same problem with us.archive.ubuntu.com 
It is very slow now!
Tried it from few different locations

---

### Post by xiaoxiong.100 on 2012-07-11
> **sanderj said:**
> Server:

userveradmin@Mustang:~$ mtr -nrc4 security.ubuntu.com
HOST: Mustang Loss% Snt Last Avg Best Wrst StDev
1.|-- 192.168.25.22 0.0% 4 1.8 8.1 1.8 26.3 12.1
2.|-- 172.12.1.1 0.0% 4 2.6 1.7 0.4 2.6 1.0
3.|-- 58.61.147.222 0.0% 4 1.4 2.1 0.9 4.1 1.4

Laptop:

sam@SamUb:~$ mtr -nrc4 security.ubuntu.com
HOST: SamUb Loss% Snt Last Avg Best Wrst StDev
1.|-- ??? 100.0 4 0.0 0.0 0.0 0.0 0.0
2.|-- 192.168.100.1 0.0% 4 1.9 1.9 1.8 2.0 0.1
3.|-- ??? 100.0 4 0.0 0.0 0.0 0.0 0.0
4.|-- 121.34.247.13 25.0% 4 23.8 23.3 22.6 23.8 0.6

Your server and your laptop show different routes / different IP addresses. And your server is on 192.168.25.x, whereas your laptop is on 192.168.100.x. So I would say they are on different LANs.

Furthermore your name resolving is not working correctly.

Are you sure you did not install a firewall on your own Ubuntu Server?
Another approach would be to boot a Ubuntu live-CD in the server, but I believe you have no physical access to the system?

If so, I would talk to the IT department what is going on.
=> Thanks! This could be the root cause: Company(eth1) firewall block it. But how to change it to eth0 (ADSL which is the same as my laptop)? 

Attache /etc/network/interfaces of my server:
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface (ADSL interface)
auto eth0
#iface eth0 inet dhcp    //Sam deactive this line and add all following lines
iface eth0 inet static
address 192.168.100.17
netmask 255.255.255.0
gateway 192.168.100.1
dns-nameservers 202.96.134.133 202.96.128.68

#The second network interface (company network)
auto eth1
iface eth1 inet static
address 192.168.25.17
netmask 255.255.255.0
gateway 192.168.25.1
dns-nameservers 192.168.30.28 192.168.30.27


Attach the contents of /etc/resolve.conf of my server:
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.30.28
nameserver 192.168.30.27

---

### Post by xiaoxiong.100 on 2012-07-11
Hi every one,
I think I have find the root causes:
1. eth1: Company firewall block our apt-get update;
2. eth0: has no DNS server for ADSL.

Attache /etc/network/interfaces of my laptop:
sam@SamUb:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

Attache /etc/resolv.conf of my laptop:
 sam@SamUb:~$ cat /etc/resolv.conf 
# Generated by NetworkManager
nameserver 202.96.134.133
nameserver 202.96.128.68

So, we have two solution:
1. negotiate with IT department for setting to firewall -- It is hard to push!
2. set correct the DNS server for my eth0 (ADSL network) -- How to set it correct? Any buddy could help me?

---

### Post by sanderj on 2012-07-11
Edit /etc/resolv.conf and 

```
nameserver 8.8.8.8

```
to the beginning of /etc/resolv.conf.

Does that work?

NB: /etc/resolv.conf will be overwritten on next boot

---

### Post by xiaoxiong.100 on 2012-07-11
> **sanderj said:**
> Edit /etc/resolv.conf and 

```
nameserver 8.8.8.8

```to the beginning of /etc/resolv.conf.

Does that work?

NB: /etc/resolv.conf will be overwritten on next boot
=> It looks work, but still incorrect. Please refer to follow results:
userveradmin@Mustang:~$ sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                   
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                  
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                      
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                         
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources/DiffIndex       
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg                 
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
...

---

### Post by sanderj on 2012-07-11
What's the output of:

```
host security.ubuntu.com 
host security.ubuntu.com 8.8.8.8

```

---

### Post by xiaoxiong.100 on 2012-07-11
> **sanderj said:**
> What's the output of:

```
host security.ubuntu.com 
host security.ubuntu.com 8.8.8.8

```
=> Please refer to follow result:

userveradmin@Mustang:~$ host security.ubuntu.com
;; connection timed out; no servers could be reached
userveradmin@Mustang:~$ host security.ubuntu.com 8.8.8.8
;; connection timed out; no servers could be reached

# with ADSL DNS server:
userveradmin@Mustang:~$ host security.ubuntu.com 202.96.134.133
;; connection timed out; no servers could be reached

#with company DNS server:
userveradmin@Mustang:~$ host security.ubuntu.com 192.168.30.27
Using domain server:
Name: 192.168.30.27
Address: 192.168.30.27#53
Aliases: 

security.ubuntu.com has address 91.189.92.151
security.ubuntu.com has address 91.189.92.166
security.ubuntu.com has address 91.189.92.181
security.ubuntu.com has address 91.189.92.184

---

### Post by xiaoxiong.100 on 2012-07-11
Hi Every one,
One more additional information:

userveradmin@Mustang:~$ sudo /etc/init.d/networking restart
[sudo] password for userveradmin: 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          ssh stop/waiting
ssh start/running, process 9258
RTNETLINK answers: File exists
Failed to bring up eth0.
                                                                         [ OK ]


I think the "Failed to bring up eth0." make my server can not connect with the DNS server 202.96.134.133

---

### Post by sanderj on 2012-07-11
I would talk to your IT department and ask how you should configure your system: two interfaces, an external firewall, an ADSL connection, working/non-working nameservers ... that's too complex to make it work by guessing and trying.

---

### Post by xiaoxiong.100 on 2012-07-11
> **sanderj said:**
> I would talk to your IT department and ask how you should configure your system: two interfaces, an external firewall, an ADSL connection, working/non-working nameservers ... that's too complex to make it work by guessing and trying.
=> Thanks! I will do it today later!:)

---

### Post by xiaoxiong.100 on 2012-07-11
> **sanderj said:**
> I would talk to your IT department and ask how you should configure your system: two interfaces, an external firewall, an ADSL connection, working/non-working nameservers ... that's too complex to make it work by guessing and trying.

=> Hi! Sanderj, I make it works!!!:P Even I still can not clear know the root cause:
I exit the terminal via ADSL network, and  connect to my server in my company network (means connect to server eth1), and execute:
userveradmin@Mustang:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          ssh stop/waiting
ssh start/running, process 11324
RTNETLINK answers: File exists
Failed to bring up eth1.
                                                                         [ OK ]

Note that, previously, when I connect to my server in ADSL network, the execute result is:
"Failed to bring up eth0." Now, it is "Failed to bring up eth1.", and the DNS for eth0 is working:
userveradmin@Mustang:~$ cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 202.96.134.133
nameserver 202.96.128.68
nameserver 202.96.174.66


I try to connect to server in ADSL network (via eth0) again, and execute sudo /etc/init.d/networking restart,  it is still "Failed to bring up eth1." and DNS for eth0 is still working!
Ha... I don't known what is the different to restart networking via eth0 and eth1.

Every one, Thank you very much for your support! I will continue to find the root cause. and will attach here later if I got it.

---

