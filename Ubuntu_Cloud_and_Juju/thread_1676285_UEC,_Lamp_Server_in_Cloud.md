---
title: "UEC, Lamp Server in Cloud"
date: 2011-01-26
forum: Ubuntu Cloud and Juju
---

### Post by ashishrevar on 2011-01-26
Hello there,
I am working on academic project in which I need to build Cloud and then deploy a **PHP application** on it, so others can get the access over it.

I've build a cloud in my laptop, but this is only command line cloud, no GUI. how to deal with it?
I am having my code for the php application with mysql database, so **how to run apache server and mysql server in cloud?**

**Where should I put this code and database?**

Waiting for positive response.

---

### Post by kim0 on 2011-01-27
Hi!
Please follow steps 6 and 7 for downloading and starting an instance on your cloud

[https://help.ubuntu.com/community/UEC/CDInstall#STEP](https://help.ubuntu.com/community/UEC/CDInstall#STEP) 6: Install an image from the store

Once started, you should ssh into the virtual instance, and deploy your php code like any other Linux server

---

### Post by ashishrevar on 2011-01-28
Hi Kim0,

How is it possible?
Those steps are about to install images of OS (Linux). But I want to run php application with mysql, what to do?

Do I need to bundle it and make an image of it?
Any tutorial of it available?

---

### Post by kim0 on 2011-02-02
Hi there,

Perhaps you will understand the workflow from my screencast showing how to run wordpress (LAMP app) in 60 seconds

[http://www.youtube.com/ubuntucloud#p/a/u/0/HinDARd72nQ](http://www.youtube.com/ubuntucloud#p/a/u/0/HinDARd72nQ)

---

### Post by raymdt on 2011-02-04
Hi ashishrevar,
you should first know that an Eucalyptus instance is much the same as a normal OS running on some PC (only some small differences ).

> 
I've build a cloud in my laptop, but this is only command line cloud, no GUI. how to deal with it?

You dont need a GUI to run a Webserver. It is even highly recommended to run a LAMP( Linux Apache mysql php ) on a server without GUI ( for security ).

> 
I am having my code for the php application with mysql database, so **how to run apache server and mysql server in cloud?**




1-Just run an Instance on your cloud
2-loggin into your instance
3- run  apt-get update && apt-get upgrade && apt-get -y install apache2 php5 libapache2-mod-php5  mysql-server
5- Create your mysql database
6- copy your php code into /var/www and remove /var/www/index.html
7- Et voila :guitar:

To see the result just type  http://<ipaddress>  to the Browser of your Laptop.

regards

---

### Post by kim0 on 2011-02-06
Rock on raymdt ;)

---

### Post by ShangWu on 2011-02-09
Don't forget to have the port 80 enabled from your policy.

---

### Post by raymdt on 2011-02-09
Yeah you're right.

---

### Post by ashishrevar on 2011-02-11
Hello there,

Thanks to all for sharing your knowledge.
My question is that I am having totally Non-GUI based environment in my cloud, so how to copy down my php code there?
Should I use pendrive or something else?

---

### Post by ashishrevar on 2011-02-11
Hello there,
I have one doubt about this. If I upload my php application and my MySQL database in cloud, then will it be accessible by outside world?

If I am running my cloud in my laptop at my home and I want to access that application from my college PC(Different Network) then how to deal with it?

---

### Post by raymdt on 2011-02-11
Hey,
you can use "scp" to copy your php and mysql scripts  into the instance.
It is very hard to understand how eucalyptus works when you dont have enough Linux knowledge.
You should go to the library to catch a book about Ubuntu.
Good luck!

---

### Post by yourwhiteshadow on 2011-02-18
Ashish, I think it is best if you just use a VPS from some webhosting company, you don't need to run your application in a cloud enviroment.

---

### Post by raymdt on 2011-02-18
Hi wrote
> 
I am working on academic project in which I need to build Cloud and then deploy a **PHP application** on it, so others can get the access over it.


He needs a Cloud for his Project. So he has to deal with Eucalyptus :guitar:

---

### Post by ashishrevar on 2011-02-25
Hello there,
I got all services running, in my cloud but I am not able to install images from the admin console ([https://A.B.C.D:8443](https://A.B.C.D:8443))

What is the reason? It is trying to download but all of a sudden it throws a error like below for every image.

Error 7: couldn't connect to host

How to overcome this error?

---

### Post by ashishrevar on 2011-02-25
Hello there,
My web console is showing several images which I am not able to download, as well as I am not able to get Extras menu.
The error is shown like below.

```
Eucalyptus-certified Images
[COLOR="Red"]Failed to load the list of images (visit the repository)[/COLOR]
Eucalyptus-compatible Tools
[COLOR="red"]Failed to load the list of images (visit the repository)[/COLOR]
```

Does it mean any kind of network problem?
If I do,
```
$ sudo euca_conf --no-rsync --discover-nodes
```

then it list out several errors,
```
ssh: could not resolve hostname fe80: Name or service not known
lost connection
failed.
``` 

If I try to do,
```
$ sudo apt-get update
```
then it prompts error,
connection failed.
several other tons of error code...

What's wrong with this?

---

### Post by ashishrevar on 2011-03-01
I am trying to download image from the store, but it throws error.

[COLOR="Red"]Error 7: couldn't connect to host[/COLOR]

Any guess about it? I am using network of my college, which is having gateway to access the outside world. That address (gateway), I have provided as proxy address at the time of installation.

---

### Post by ashishrevar on 2011-03-01
Hello there,
I am trying to run instances using command,

```
$ euca-run-instances emi-E2861098 -k mykey
```

But, it throws error like,
FinishVerify: Not enough resources available: addresses (try --addressing private) 

What's the problem?

---

### Post by kim0 on 2011-03-02
Every instance has 2 addresses associated with it
- Private address: Address inside the VM
- Public address: Address on the CLC and port forwarded (DNAT) to the instance

From that error, it seems it cannot allocate a public address for it, you were asked for that range during installation
Check [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall) Image 5/2. In order to change it now, check
[http://open.eucalyptus.com/forum/how-do-you-get-eucalyptus-recognize-change-vnetpublicips](http://open.eucalyptus.com/forum/how-do-you-get-eucalyptus-recognize-change-vnetpublicips)


OR, start your instance like
euca-run-instances emi-E2861098 -k mykey  --addressing private
Which will skip allocating a pub address for it, and the instance will start, but be only accessible from inside the cloud network (not public)

---

### Post by ashishrevar on 2011-03-03
As I have written in my previous post, 
[COLOR="Red"]Error 7: couldn't connect to host[/COLOR]

I guess my cloud is not able to access outside world.
How to change the proxy settings?
Should I write down my Institute's gateway as Proxy address?

Please help is needed urgently.

---

### Post by ashishrevar on 2011-03-04
Hey kim0,
Can I add my laptop's IP address there (range of the IPs needed by eucalyptus). I don't want to do another installation again as I am having exams of this, so not having so much time.
Where to write down IP address?

---

### Post by kim0 on 2011-03-04
Those (range of public IPs) are a "range" not just a single IP. They should be in the same public range as that of your CLC

---

### Post by ashishrevar on 2011-03-04
Hey Kim,
I am not able to get more IP addresses in my institute, is it necessary provide the range?
I am implementing Cloud in single machine so, I have only one IP.
Any solution to deal with it?:confused:

---

### Post by ashishrevar on 2011-03-05
If I run my instance with --addressing private then it throws an error,

[1998.78745] EXT2-fs (loop0): error: can't find an ext2 filesystem on dev loop0.

How to deal with it?
What is the significance of ext2 file system?

---

### Post by raymdt on 2011-03-05
It doesn't matter if you only have one Computer. The Ip-adresses are for the instances not for the computer.
Your supervisor has to provide you a second Computer for your tests. It is not very easy to become uec running on a single machine.

---

### Post by ashishrevar on 2011-03-07
Hey raymdt,

If I try to run instances without providing any IP range, 
using --addressing private

[1998.78745] EXT2-fs (loop0): error: can't find an ext2 filesystem on dev loop0.

It shows such kind of error then I try to watch the Instance and then status of Instance is pending for a long, sometimes it becomes terminated.

How to make it running state?:(

---

### Post by ashishrevar on 2011-03-08
Hi Folks,
I am not getting my instances in running mode, they are in pending mode only. 
Even though I try to log in, using this command

```
IPADDR=$(euca-describe-instances | grep emi-39F21608 | grep running | tail -n1 | awk '{print $4}')
ssh -i ~/.euca/mykey.priv ubuntu@10.1.3.34
```

So, it asks for password and supplied, but it prompts that permission denied, at third attempt it says Permission denied (publickry,password)

What is the problem? How to make instances in running mode?

---

### Post by vgokulakrishnan on 2011-03-08
sorry thread mistaken

---

### Post by vgokulakrishnan on 2011-03-08
wrongly replied

---

### Post by vgokulakrishnan on 2011-03-08
Ur doubts reveals that u as a newbie trying to explore a lot in clou.
Good, I'm too that kinda..
And, for ur ques, No u can't simply do that, if u re tryin to access far  from ur UEC network connected with switches..
I think ur setting up Private Cloud..
Know this, there r 2 kinds of clouds,
Private & Public..
U may try Public Cloud, which is much tougher than Private.. frankly.. ;)
All the best for ur cloud.. :)

---

### Post by ashishrevar on 2011-03-10
Hi Folks,

I have installed everything again using DHCP server (my ISP router). Everything was working fine, I was getting my instances in running state, but not able to log in them. ssh command was not working.

Permission denied (publickey, password).
What is the issue?

Second problem is that, I have turned off my laptop and after a while when I tried to run my cloud again, it fails.

UEC : euca-describe-availability-zones verbose fails with error : [Errno 113] No route to host

Any solution for these two issues?

---

### Post by ashishrevar on 2011-03-17
Hi,
I am not able to ssh into instances. They are in running state, but if I try to log into them, it prompts for password, I enter the password 3 times and every time it shows that 
[COLOR="Red"]Permission denied[/COLOR]

How to overcome this?

---

### Post by kim0 on 2011-03-18
You cannot log in by password, only by ssh key :) Read the manual, the step that uses euca-add-keypair

---

### Post by ashishrevar on 2011-03-21
Hello there,

If I want to access my php application deployed in Cloud, then how to do it? Do I need an static IP? I am using DHCP router in my room which provides a different IP every time I try to connect it.

Can I give that IP address to others to access this php application? How to bind my cloud to a specific location/name so it can be accessible every time from anywhere anytime?

---

### Post by ashishrevar on 2011-03-27
Hello there, I am using --addressing private in my instances,

I ran the following command...
ssh -i ~/.euca/mykey.priv ubuntu@172.19.1.2

So it says,
ssh: connect to host 172.19.1.2 port 22: No route to host

---

### Post by ashishrevar on 2011-03-27
If I try to ping my instances,
ping 172.19.1.2

icmp_seq=1 Destination host unreachable
what is the problem?

---

