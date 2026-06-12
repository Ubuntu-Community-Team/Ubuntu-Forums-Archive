---
title: "Unable to instal sun-jdk5 or postgresql"
date: 2008-11-19
forum: Server Platforms
---

### Post by ndnd on 2008-11-19
Hi,
I am new to linux. I have installed 8.10 Server edition on my laptop. 

I have been able to connect to internet (Can Ping computers in my network as well as telnet to ubuntu) 

I was able to install the unzip package 

#sudo apt-get install unzip 

However, I can't get to install the other packages 

> $sudo -s
#sudo apt-get install sun-java5-jdk
Reading package lists...Done
Building dependency tree
Reading state information...Done
E:Couldn't find package sun-java5-jdk

#sudo apt-get install postgresql-8.2
Reading package lists...Done
Building dependency tree
Reading state information...Done
E:Couldn't find package postgresql_8.2

I had in the past as a workaround (when I did not have internet connection ) 

did the following to install MySQL

> $ sudo -s
# cd /etc/apt
# mv sources.list sources.list.save
# apt-cdrom add
# apt-get update
# apt-get install mysql-server

I have current done the following in case the above was a cause for a problem
> 
sudo -s
#sudo mv sources.list sources.list.oldcd
#sudo mv sources.list.save sources.list



I tried again installing jdk and postsql and still the same result. 

Again I do have internet connectivity and there is no firewall issue as 

apt-get install unzip - package was installed properly. 

I am new to linux - kindly provided detailed steps or in case you need more information (how to get that as well). 
Thanks in advance

---

### Post by ndnd on 2008-11-19
Solved. 
The sources list needed to be reverted back to the original sources.list (the one I had renamed as sources.list.save was renamed back to sources.list.save

Then I updated 
apt-get update

And all set..

---

