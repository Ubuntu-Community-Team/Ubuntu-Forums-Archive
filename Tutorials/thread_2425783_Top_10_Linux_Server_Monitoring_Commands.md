---
title: "Top 10 Linux Server Monitoring Commands"
date: 2019-08-30
forum: Tutorials
---

### Post by milesweb on 2019-08-30
Linux server is a high-powered form of the Linux operating system, that is designed to handle the more complex and demanding needs of the business such as database management, system administration and Web services.
 
Managing Linux Server, Desktop and Workstation is not the same thing. Let&#8217;s see the differences between them.
 
**Server -** Computers that provide services like email or websites to other computers is called as a server. The server can be hardware like a desktop/laptop or dedicated server hardware.
These servers need to be installed with OS like Linux, Windows, iOS, etc. While running Linux, servers usually do not run the graphical console, as it is not necessary for regular tasks, and still consume resources like memory and CPU time.
 
But the Linux Administrators or Linux user can still use graphical console remotely, depending on the configuration required.
 
**Desktop -** Desktops and laptops can help you run graphical console to carry out your typical tasks like reading emails, browsing the website or watching videos. All these tasks become easier with the graphical environment.
 
**Workstation -** Workstations are like professional computers with more memory and better processor. According to Linux book, Workstation is similar to that of the desktop but just that it is more powerful. 
 
Thus, the monitoring of each needs to be carried out for the smooth functioning of the work. The server handling and monitoring is a bit tedious job, as it needs deep technical knowledge.
 
[SIZE=3]**Why is it important to monitor the Linux server?**[/SIZE]
 
**1) To avoid server failure -**
 
Those who are the amateurs working in the operating system might have understood that working on Linux isn&#8217;t an easy job. For the IT professionals, it becomes a challenge to troubleshoot the issue on the spot, that&#8217;s why it is very vital to continuously monitor the Linux server. This also helps to monitor the malware and cyber-attacks on your system, so as to fix the issue before it hampers you.
 
**2) Agent and Agentless Linux server monitoring -**
 
Agentless monitoring via SNMP collects performance metrics from the infrastructure without installing any agent software on the server to be monitored. On the other hand, agent software is required by the IT infrastructure, to collect performance metrics about the server. This collected information is then uploaded on to a management server for storage, analysis and reporting to administrators. That means, agent monitoring checks CPU, memory, network throughput, and disk utilisation, whereas, agents are designed to be installed and run on Linux system as per your needs.
 
Not, everyone knows what you should monitor in Linux server management. To keep the infrastructure healthy you need to have the monitoring team that speeds up and facilitates the technical problems and also, maintains and corrects your issues. Most of the web hosting providers has such skilled tech support team who works for you 24/7 to solve all your issues.
 
**3) Linux server is monitored by more experienced administrators**, however, when it comes to monitoring team, there can be a need of immediate reports and actions to be taken. So, the monitoring team makes your task easy by continuously keeping an eye on the server.
 
[SIZE=3]**What are the key performances metrics need to be monitored?**[/SIZE]
 
**(i) CPU &#8211;** CPU is a most important component of your computer system which has a high utilisation rate and temperature. That&#8217;s why it needs to be monitored on a primary basis. As CPU has multiple cores, and an application needs to be directed on only one of these cores, the danger of hardware behavior may also occur.
 
**(ii) Disk Capacity &#8211;** When you consider the image servers, files, and VMs, which can directly shut down your system or corrupt the operating system, then disk capacity is a vital parameter to be monitored. While monitoring disk capacity, eventual addition or change of a disk can also be done.
 
**(iii) Memory &#8211;** Memory monitoring is done because it can immediately stop a system due to memory overflow or misdirection for a single application.
 
**(iv) SWAP &#8211;** SWAP is a virtual memory created by the system, to be used in necessity. It needs to be monitored because its high utilisation may indicate that the amount of memory is insufficient for you. 
 
[SIZE=3]**Does monitoring a Linux Server solve all your problems?**[/SIZE]
No, it doesn&#8217;t, to operate the Linux you need to aware of its commands, too.
 
Here are some Linux monitoring commands that will help you know what is happening with your Linux server. 
 
**1) lsof:**

**lsof** stands for &#8216;*list of open files*&#8217;. It helps you find out all the opened files and processes along with the information about who has opened it.
How to use:
(i) To list down, all the files opened by particular process identification (PID) number on Linux -
    
```
 lsof -p PID
```

(ii) To count the number of files and processes
  
```
[root@localhost ~]# lsof -p 4271 | wc -l

34

[root@localhost ~]#
```

 
(iii) To check the current opened log file 
 
      ```
 lsof -p | grep log
```
 
**2) iostat:**

The **iostat** command is used to monitor *system input/output (I/O)* device loading by observing the time till which devices are active in relation to their average transfer rates.
(I ) the syntax of iostat to find disk utilisation report 
 
```
iostat -d -x interval count
```

 
Where,
    &#8226; -d: displays the device utilisation report (d == disk)
    &#8226; -x: displays extended statistics including disk utilisation.
    &#8226; interval: it is a time period in seconds between two samples. eg.- iostat4 will give the data at each 4 seconds interval.
    &#8226; Count:- It is considered as the number of times the data is needed.
 
**3) VmStat:**

**VmStat** command in Linux is use to display the statistics of **virtual memory**, **kernel threads**, **disks**, **system process**, **I/O blocks**, **interrupts**, **CPU activity**, etc. In Linux systems, VmStat command is not available by default. You will have to install a package called **sysstat** that includes a vmstat program.

```
vmstat
```

**4) meminfo and free :**

**Meminfo** gives the detailed list of what&#8217;s going on in memory. You need to access meminfo&#8217;s data by using another program such as a cat or gap.

```
cat /proc/meminfo
```

It gives you the information about what&#8217;s going on in your server&#8217;s memory at any given moment.
 
**5) Top:**

**top** command in Linux is a performance monitoring program. The top command is used to display all the running and active real-time processes. By default, it shows the most CPU-intensive tasks running on the server. You can sort the processes by ***PID (process ID)***, age, newest first, time, etc.
 
```
top
```

 
**6) Tcpdump:**

**Tcpdump** command is a network packet analyzer or a packet sniffer program that is used to capture and filter TCP/IP packets that are received or transferred on the network interface.

```
 tcpdump -i eth0
```

 
**7) uptime:**

**uptime** is used to check how long the server is been running and how many users are logged in.
 
```
 uptime [options]
```

 
Where,
**Options** stand for:
-h, --help &#8594; displays a brief message and exit.
-V, --version &#8594; displays the version information and exit.
 
**8) Arpwatch:**

**Arpwatch** program is designed to monitor Address Resolution (**MAC** and **IP** address changes) of **Ethernet** network traffic on a Linux network. It continuously keeps a watch on the Ethernet traffic.
 
```
arpwatch -i eth0
```

 
**9) VnStat PHP:**

**VnStat** PHP monitors the network traffic usage in a graphical mode.
 
```
vnstat
```

 
**10) Collectl:**

**collectl** command is used to collect information about Linux system resources such as CPU usage, memory, network, processes, TCP, sockets, etc. It is an all-in-one performance monitoring tool.
 
```
collectl
```

 
[SIZE=3]**Is Linux monitoring an easy job?**[/SIZE]
It is if you have the strong core knowledge about it. Linux Server Monitoring Commands need to be handled carefully, as one command can make changes in your whole system. So, mostly, it is advisable to hand over that work to the one who is well educated in Linux.

---

### Post by TheFu on 2019-08-30
Or just install monitoring and alarming tools like nagios, cacti, sysusage, monit, munin, zabbix or any of the 20 other clones to have a performance monitoring and alarming in an easy to use webapp.

---

### Post by cruzer001 on 2019-08-30
How many servers do you run?

---

### Post by milesweb on 2019-08-31
> **cruzer001 said:**
> How many servers do you run?

Depends on which node, we have many at different sizes. For example 10 servers on one node

---

### Post by uRock on 2019-08-31
Surprised I don't see **htop** on there. It is the most used command on my server. It shows me up time and what processes are eating my CPU and RAM.

PS, I know it isn't used much, if at all, in a commercial environment. Those environments use what TheFu recommended.

---

### Post by gngrn1nja on 2019-09-01
this is going to be helpful. thank you!

---

### Post by milesweb on 2019-10-14
> **uRock said:**
> Surprised I don't see **htop** on there. It is the most used command on my server. It shows me up time and what processes are eating my CPU and RAM.

PS, I know it isn't used much, if at all, in a commercial environment. Those environments use what TheFu recommended.

Thanks for your inputs uRock. 

I would be like to add your suggestion in this post, but it seems the "Edit" option is disabled now.

---

### Post by janruther on 2020-09-15
Well this is a really helpful article that helped me a lot. Thank !! I really like to read such articles, since they are written very clearly and sometimes it is very useful for refreshing knowledge, and this is very useful, since very often there are various updates that you need to be aware of in order to be able to configure everything correctly. I'm sure you all know that there is a huge amount of information on the Internet right now. Many people think that this is good, but just because of its huge and varied amount, it is very difficult to find exactly what you need. For example, I recently urgently needed a [server configuration service pack]("https://amasty.com/magento-server-configuration-service.html"). I spent a relatively long time until I found exactly what I was looking for.

---

### Post by dezintop on 2020-10-20
> **milesweb said:**
> Linux server is a high-powered form of the Linux operating system, that is designed to handle the more complex and demanding needs of the business such as database management, system administration and Web services.
 
Managing Linux Server, Desktop and Workstation is not the same thing. Let’s see the differences between them.
 
**Server -** Computers that provide services like email or websites to other computers is called as a server. The server can be hardware like a desktop/laptop or dedicated server hardware.
These servers need to be installed with OS like Linux, Windows, iOS, etc. While running Linux, servers usually do not run the graphical console, as it is not necessary for regular tasks, and still consume resources like memory and CPU time.
 
But the Linux Administrators or Linux user can still use graphical console remotely, depending on the configuration required.
 
**Desktop -** Desktops and laptops can help you run graphical console to carry out your typical tasks like reading emails, browsing the website or watching videos. All these tasks become easier with the graphical environment.
 
**Workstation -** Workstations are like professional computers with more memory and better processor. According to Linux book, Workstation is similar to that of the desktop but just that it is more powerful. 
 
Thus, the monitoring of each needs to be carried out for the smooth functioning of the work. The server handling and monitoring is a bit tedious job, as it needs deep technical knowledge.
 
[SIZE=3]**Why is it important to monitor the Linux server?**[/SIZE]
 
**1) To avoid server failure -**
 
Those who are the amateurs working in the operating system might have understood that working on Linux isn’t an easy job. For the IT professionals, it becomes a challenge to troubleshoot the issue on the spot, that’s why it is very vital to continuously monitor the Linux server. This also helps to monitor the malware and cyber-attacks on your system, so as to fix the issue before it hampers you.
 
**2) Agent and Agentless Linux server monitoring -**
 
Agentless monitoring via SNMP collects performance metrics from the infrastructure without installing any agent software on the server to be monitored. On the other hand, agent software is required by the IT infrastructure, to collect performance metrics about the server. This collected information is then uploaded on to a management server for storage, analysis and reporting to administrators. That means, agent monitoring checks CPU, memory, network throughput, and disk utilisation, whereas, agents are designed to be installed and run on Linux system as per your needs.
 
Not, everyone knows what you should monitor in Linux server management. To keep the infrastructure healthy you need to have the monitoring team that speeds up and facilitates the technical problems and also, maintains and corrects your issues. Most of the web hosting providers has such skilled tech support team who works for you 24/7 to solve all your issues.
 
**3) Linux server is monitored by more experienced administrators**, however, when it comes to monitoring team, there can be a need of immediate reports and actions to be taken. So, the monitoring team makes your task easy by continuously keeping an eye on the server.
 
[SIZE=3]**What are the key performances metrics need to be monitored?**[/SIZE]
 
**(i) CPU –** CPU is a most important component of your computer system which has a high utilisation rate and temperature. That’s why it needs to be monitored on a primary basis. As CPU has multiple cores, and an application needs to be directed on only one of these cores, the danger of hardware behavior may also occur.
 
**(ii) Disk Capacity –** When you consider the image servers, files, and VMs, which can directly shut down your system or corrupt the operating system, then disk capacity is a vital parameter to be monitored. While monitoring disk capacity, eventual addition or change of a disk can also be done.
 
**(iii) Memory –** Memory monitoring is done because it can immediately stop a system due to memory overflow or misdirection for a single application.
 
**(iv) SWAP –** SWAP is a virtual memory created by the system, to be used in necessity. It needs to be monitored because its high utilisation may indicate that the amount of memory is insufficient for you. 
 
[SIZE=3]**Does monitoring a Linux Server solve all your problems?**[/SIZE]
No, it doesn’t, to operate the Linux you need to aware of its commands, too.
 
Here are some Linux monitoring commands that will help you know what is happening with your Linux server. 
 
**1) lsof:**

**lsof** stands for ‘*list of open files*’. It helps you find out all the opened files and processes along with the information about who has opened it.
How to use:
(i) To list down, all the files opened by particular process identification (PID) number on Linux -
    
```
 lsof -p PID
```

(ii) To count the number of files and processes
  
```
[root@localhost ~]# lsof -p 4271 | wc -l

34

[root@localhost ~]#
```

 
(iii) To check the current opened log file 
 
      ```
 lsof -p | grep log
```
 
**2) iostat:**

The **iostat** command is used to monitor *system input/output (I/O)* device loading by observing the time till which devices are active in relation to their average transfer rates.
(I ) the syntax of iostat to find disk utilisation report 
 
```
iostat -d -x interval count
```

 
Where,
    • -d: displays the device utilisation report (d == disk)
    • -x: displays extended statistics including disk utilisation.
    • interval: it is a time period in seconds between two samples. eg.- iostat4 will give the data at each 4 seconds interval.
    • Count:- It is considered as the number of times the data is needed.
 
**3) VmStat:**

**VmStat** command in Linux is use to display the statistics of **virtual memory**, **kernel threads**, **disks**, **system process**, **I/O blocks**, **interrupts**, **CPU activity**, etc. In Linux systems, VmStat command is not available by default. You will have to install a package called **sysstat** that includes a vmstat program.

```
vmstat
```

**4) meminfo and free :**

**Meminfo** gives the detailed list of what’s going on in memory. You need to access meminfo’s data by using another program such as a cat or gap.

```
cat /proc/meminfo
```

It gives you the information about what’s going on in your server’s memory at any given moment.
 
**5) Top:**

**top** command in Linux is a performance monitoring program. The top command is used to display all the running and active real-time processes. By default, it shows the most CPU-intensive tasks running on the server. You can sort the processes by ***PID (process ID)***, age, newest first, time, etc.
 
```
top
```

 
**6) Tcpdump:**

**Tcpdump** command is a network packet analyzer or a packet sniffer program that is used to capture and filter TCP/IP packets that are received or transferred on the network interface.

```
 tcpdump -i eth0
```

 
**7) uptime:**

**uptime** is used to check how long the server is been running and how many users are logged in.
 
```
 uptime [options]
```

 
Where,
**Options** stand for:
-h, --help &#8594; displays a brief message and exit.
-V, --version &#8594; displays the version information and exit.
 
**8) Arpwatch:**

**Arpwatch** program is designed to monitor Address Resolution (**MAC** and **IP** address changes) of **Ethernet** network traffic on a Linux network. It continuously keeps a watch on the Ethernet traffic.
 
```
arpwatch -i eth0
```

 
**9) VnStat PHP:**

**VnStat** PHP monitors the network traffic usage in a graphical mode.
 
```
vnstat
```

 
**10) Collectl:**

**collectl** command is used to collect information about Linux system resources such as CPU usage, memory, network, processes, TCP, sockets, etc. It is an all-in-one performance monitoring tool.
 
```
collectl
```

 


This is what I was looking for.

---

