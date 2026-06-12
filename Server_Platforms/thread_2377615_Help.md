---
title: "Help"
date: 2017-11-15
forum: Server Platforms
---

### Post by linuxnew9 on 2017-11-15
hello friends, i am a newbie and installed ubuntu 17.10 on oracle Vbox with windows 8 as my host. i want to set a static ip for the VM and i done the changes in yaml file located in  /etc/netplan  and run a debug, i get a error  of mapping interfaces missing, what to do?

---

### Post by darkod on 2017-11-15
The static IP on ubuntu server is configured in the file /etc/network/interfaces.

You have some instructions here: [https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html)

Also, for servers it is recommended to run only LTS releases, the current one is 16.04 LTS. The latest non-LTS release like 17.10 is OK for some quick testing but not to run servers on it long term. Non-LTS have very short support period.

---

### Post by linuxnew9 on 2017-11-15
> **darkod said:**
> The static IP on ubuntu server is configured in the file /etc/network/interfaces.

You have some instructions here: [https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html)

Also, for servers it is recommended to run only LTS releases, the current one is 16.04 LTS. The latest non-LTS release like 17.10 is OK for some quick testing but not to run servers on it long term. Non-LTS have very short support period.

unfortunately, the netplan is the default network configuration in ubuntu 17.10

[COLOR=#555555][FONT=&quot]the file is must ([/FONT][/COLOR]**[B]/etc/netplan/yourname.yaml)**[/B][COLOR=#555555][FONT=&quot] to configure Ubuntu interfaces.[/FONT][/COLOR]

---

### Post by coldraven on 2017-11-15
I don't know the answer to your question but you can get free ready-made Vbox server images from here: [https://virtualboxes.org/](https://virtualboxes.org/)

It may save you some time and is great for experimenting/testing/learning, don't forget to change the default password.

---

### Post by darkod on 2017-11-15
My recommendation: either use 16.04 LTS or wait for the 18.04 LTS next April.

In any case if you want someone's help with that yaml file at least post its content so we can see what you put in. :)

PS. Can this short tutorial help you confirm that you have set up the file correctly?
[https://websiteforstudents.com/configuring-static-ips-ubuntu-17-10-servers/](https://websiteforstudents.com/configuring-static-ips-ubuntu-17-10-servers/)

---

### Post by linuxnew9 on 2017-11-16
> **darkod said:**
> My recommendation: either use 16.04 LTS or wait for the 18.04 LTS next April.

In any case if you want someone's help with that yaml file at least post its content so we can see what you put in. :)

PS. Can this short tutorial help you confirm that you have set up the file correctly?
[https://websiteforstudents.com/configuring-static-ips-ubuntu-17-10-servers/](https://websiteforstudents.com/configuring-static-ips-ubuntu-17-10-servers/)

i did exactly as it said, i am using this server 17.10 on oracle VM box and do i have to change any network settings in VM box ?

all i am getting is either boolean value error or cant able to map on my interface, enp0s3. 

[COLOR=#FF0000]ethernets:
   ens33:[/COLOR]

---

### Post by darkod on 2017-11-16
You have to get the interface name correct. Is it ens33 or enp0s3? The correct one needs to be used in the config.

If you are unsure you should be able to get the interface name with something like:
```
sudo lshw -short | grep network
```

---

### Post by linuxnew9 on 2017-11-16
[IMG]https://i.imgur.com/kc0yZW7.png[/IMG]

---

### Post by linuxnew9 on 2017-11-16
my ip address on Virtualbox is

ipv4 address: 192.168.56.1
ivp4 netmask: 255.255.255.0


DHCP is enabled 
server address: 192.168.56.101 to 254

---

### Post by darkod on 2017-11-16
I can't be 100% sure but I think it is complaining because the gateway you are setting is not reachable from the IP. If you use IP 192.168.56.70/24 that can see only the 192.168.56.x subnet, nothing more. So how can it reach the gateway 192.168.1.1?

Why not set the virtual NIC in bridge mode, that way the VM is like in your local LAN and you avoid all the confusion with VBox NAT etc... I have always used VBox VMs just like that, to simulate like they are in my LAN.

In that case you use 192.168.1.x IP address on the virtual server and 192.168.1.1 as the gateway.

Otherwise you are stuck with VBox network translation and you need to use it correctly. It might work if the gateway is 192.168.56.1 but not when it is 192.168.1.1.

---

### Post by linuxnew9 on 2017-11-16
i would try the bridget NAt and i had the settings in Vbox as Nat and host only adapter

---

### Post by darkod on 2017-11-16
If the VM is in bridged mode you need to give it IP from the 192.168.1.x range. Have you tried that?

---

### Post by linuxnew9 on 2017-11-17
i havent tried that i had realised i made one mistake, setting up of ip address same as that of  my ISPs.

---

### Post by linuxnew9 on 2017-11-17
i have decided to use 16.04 version and now both the guest OSs are pinging each other but not able to take ssh. i updated the openssh too yet i am gettting the error as publickey, password

[IMG]https://i.imgur.com/XlDH5jE.png[/IMG]


[IMG]https://i.imgur.com/hNNDQkE.png[/IMG]

---

### Post by darkod on 2017-11-17
In the images above enp0s8 has public IP. Is that machine directly on the internet? Are you allowed to use that IP (is it assigned to you by the ISP)?

You know you can't simply select one public IP and try setting it up on your machine, right?

---

### Post by linuxnew9 on 2017-11-17
the previous errors were because of the  interface configuration as i tried to set static ip on enp0s3  and that prevented from accessing the internet as well as intranet. i configured enp0s3 as NAT for accessing internet and enp0s8 hooked onto  the host only adapter that enables intranet. In short i am using both the interfaces for internet and intranet. Now SSH issue has also been solved by uninstalling and reinstalling the ssh.

---

### Post by darkod on 2017-11-17
Well, I still see few issues here but if this is how you want to run things, then ok... Please mark the thread as Solved in Thread Tools above the first post.

---

### Post by linuxnew9 on 2017-11-17
> **darkod said:**
> Well, I still see few issues here but if this is how you want to run things, then ok... Please mark the thread as Solved in Thread Tools above the first post.
can you tell me what are the issues you see here?

---

### Post by darkod on 2017-11-17
Well, of course I don't have 100% visibility of your setup so maybe why I fail to understand some decisions...

1. Two NICs. Unless this machine is directly on internet, I don't see much need for two NICs because in most cases a server would have one NIC only with private IP from the local LAN. And this is VBox guest. So where how is the VBox host connected in all this and why the guest needs two NICs.

2. You said you have intranet, which is usually local. But that enp0s8 is the adapter for the intranet, and it has public IP on it. I fail to understand why public subnet would be used on intranet.

But as I said, if this works for you, great.

---

### Post by linuxnew9 on 2017-11-18
i would summarize my setup to clear the confusion.My base machine is windows 8.1 and on oracle Vbox, i installed two guest OSs(ubuntu) on it and faced the issue in interconnecting two Vms. One NIC is for the internet and another is for the interconnecting the two Vms. Maybe i have used the wrong term intranet for establishing link between two vms.

---

