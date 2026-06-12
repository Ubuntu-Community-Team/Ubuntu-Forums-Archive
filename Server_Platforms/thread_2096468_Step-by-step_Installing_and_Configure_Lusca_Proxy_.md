---
title: "Step-by-step Installing and Configure Lusca Proxy Server in Ubuntu Server 12.04"
date: 2012-12-20
forum: Server Platforms
---

### Post by codestream on 2012-12-20
**Step 1.** Install Ubuntu Server 12.04 and use manual partition with following partition table ( In this case I have 250 GB HDD and RAM 4 GB)

```
Type	Size	Location	FileSystem	Mount
Primary	30 GB	Beginning	ext4		/
Primary	500 MB	Beginning	ext4		/boot
Primary	8192 MB	Beginning	swap		swap
Logical	25 GB	End		btrfs		/cache-1
Logical	25 GB	End		btrfs		/cache-2
Logical	25 GB	End		btrfs		/cache-3
Logical	25 GB	End		btrfs		/cache-4
Logical	25 GB	End		btrfs		/cache-5
Logical	46 GB	End		ext4		/home
Logical	5 GB	End		ext4		/opt
Logical	5 GB	End		ext4		/srv
Logical	5 GB	End		ext4		/tmp
Logical	5 GB	End		ext4		/usr
Logical	5 GB	End		ext4		/usr/local
```

**Step 2.** Make sure your ubuntu package repositories and installed programs are up to date.
```
sudo apt-get update -y && sudo apt-get upgrade -y
```

**Step 3.** Install Lusca and other package
```
sudo apt-get install lusca squidclient squid-cgi ccze
```

**Step 4.** Backup old lusca file configuration and Create new lusca file configuration:
```
sudo /etc/lusca/squid.conf /etc/lusca/squid.conf.original
```
```
sudo touch /etc/lusca/squid.conf
```
```
sudo nano /etc/lusca/squid.conf
```
copy and paste squid configuration from [here]("http://ubuntuserverguide.com/2012/12/how-to-install-and-configure-lusca-as-proxy-server-in-ubuntu-server-12-04.html")
Set owner file /etc/lusca/squid.conf to user and group proxy
```
sudo chown proxy:proxy /etc/lusca/squid.conf
```

**Step 5.** Create directory /etc/squid and Store Url File Configuration (storeurl.conf):
```
sudo mkdir /etc/squid/
```
```
sudo touch /etc/squid/storeurl.pl
```
```
sudo nano /etc/squid/storeurl.pl
```
copy and paste store url from [here]("http://ubuntuserverguide.com/2012/12/how-to-install-and-configure-lusca-as-proxy-server-in-ubuntu-server-12-04.html")
Change Owner and permission file /etc/squid/storeurl.pl

```
sudo chown proxy:proxy /etc/squid/storeurl.pl
```
```
sudo chmod +x /etc/squid/storeurl.pl
```
**Step 6.** Change owner and permission lusca cache directory
```
sudo chown proxy:proxy /cache-{1,2,3,4,5}
```
```
sudo chmod 777 /cache-{1,2,3,4,5}
```

**Step 7.** Debug lusca, to check any erros with following command
```
lusca -d1
```

**Step 8. **IF ni have error Restart lusca daemon with following command

```
sudo service lusca restart
```

**Step 9.** Restart ubuntu server 12.04
```
sudo init 6
```

**Step 10.** Monitoring lusca access.log :

```
sudo tail -f /var/log/lusca/access.log | ccze
```

Source: [ubuntuserverguide.com]("http://ubuntuserverguide.com/2012/12/how-to-install-and-configure-lusca-as-proxy-server-in-ubuntu-server-12-04.html")

---

### Post by !! hack-back !! on 2013-01-24
thanks  a lot for you specially for the soreurl and refresh pattern that mentioned in conf file.
i have question ,
now we are in smart phone world , so how we can cache iphone and android apps ??
thank you again..

---

### Post by jefri new line on 2013-07-04
Hey codestream..!!

i want to ask something i had used lusca proxy on ubuntu 11.10 with my specification are proc : Amd x2 2.5ghz RAM : 2Gb And Hard Drive : 320Gb..!!

And the partitions table which like :

/cache = 50gb
Swap : 4gb
/ = 266gb

but the problem was lusca stopped where cache portion only in 30gb and lusca cache service stopped by itself..!

in few times i was tried to start lusca again but it doesn't start the service, but if i was deleted the cache partitions and then started lusca service again with "/usr/local/squid/sbin/squid -NDd1 &"..!!

My question are..!!

1. did you ever meet a problem that i had..?
2. could you give a direction how much i could set up this configuration cache_dir aufs /cache/ 50000 87 256 in my squid.conf..?

Thanks to codestream..!

---

### Post by salmankorrani on 2014-04-19
my master

while using proxy after configuration im having this message on browser [h=1]It works![/h]This is the default web page for this server.
The web server software is running but no content has been added, yet.

say something about this if i've missed alot or anything else

---

### Post by elico on 2014-04-19
I am not sure if 4GB of ram will be enough for 100GB of aufs cache but if it works fine and without swapping then fine.

---

