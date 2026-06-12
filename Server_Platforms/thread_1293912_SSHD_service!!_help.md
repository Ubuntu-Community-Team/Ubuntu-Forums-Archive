---
title: "SSHD service!! help?"
date: 2009-10-17
forum: Server Platforms
---

### Post by ericosuave on 2009-10-17
should I be worred about this?

when i run top on my server this is what i see...

10139 XXXXXX  20   0  2176 1196  452 S    1  0.0   0:00.80 sshd                                                                             
12165 XXXXXX  20   0  2176 1196  452 S    1  0.0   0:00.22 sshd                                                                             
12876 www-data  20   0  178m  10m 4284 S    1  0.1   0:00.60 apache2                                                                          
13061 XXXXXX  20   0  2176 1196  452 S    1  0.0   0:00.52 sshd                                                                             
14471 www-data  20   0  175m 8184 3456 S    1  0.1   0:00.02 apache2                                                                          
16173 XXXXXX  20   0  2176 1196  452 S    1  0.0   0:04.14 sshd                                                                             
18518 XXXXXX  20   0  2172 1184  452 S    1  0.0   0:01.98 sshd                                                                             
18581 XXXXXX  20   0  2172 1184  452 S    1  0.0   0:04.60 sshd                                                                             
18583 XXXXXX  20   0  2172 1184  452 S    1  0.0   0:04.60 sshd                                                                             
18609 XXXXXX  20   0  2172 1184  452 S    1  0.0   0:02.94 sshd                                                                             
18639 XXXXXX  20   0  2172 1184  452 S    1  0.0   0:04.28 sshd                                                                             
18834 XXXXXX  20   0  2172 1140  404 S    1  0.0   0:02.26 sshd                                                                             
18898 XXXXXX  20   0  2172 1188  452 S    1  0.0   0:01.60 sshd                                                                             
18960 XXXXXX  20   0  2172 1188  452 S    1  0.0   0:03.22 sshd                                                                             
25135 XXXXXX  20   0  2176 1148  404 S    1  0.0   0:04.88 sshd                                                                             
25250 XXXXXX  20   0  2176 1196  452 S    1  0.0   0:02.32 sshd                                                                             
25307 XXXXXX  20   0  2176 1196  452 S    1  0.0   0:02.76 sshd                                                                             
25320 XXXXXX  20   0  2176 1148  404 S    1  0.0   0:03.66 sshd                                                                             
25321 XXXXXX  20   0  2176 1196  452 S    1  0.0   0:02.72 sshd                                                                             
25351 XXXXXX  20   0  2176 1196  452 S    1  0.0   0:02.82 sshd                                                                             
25363 XXXXXX  20   0  2176 1196  452 S    1  0.0   0:01.16 sshd                                                                             
25375 XXXXXX  20   0  2176 1192  452 S    1  0.0   0:01.44 sshd                                                                             
25379 XXXXXX  20   0  2176 1196  452 S    1  0.0   0:02.34 sshd                                                                             
25390 XXXXXX  20   0  2176 1196  452 S    1  0.0   0:00.92 sshd                                                                             
25394 XXXXXX  20   0  2176 1196  452 S    1  0.0   0:02.86 sshd                                                                             
31254 XXXXXX  20   0  2176 1196  452 S    1  0.0   0:00.74 sshd                                                                             
32343 XXXXXX  20   0  2176 1196  452 S    1  0.0   0:01.98 sshd                                                                             
    1 root      20   0  4024  616  528 S    0  0.0   0:00.94 init                                                                             
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                         
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/0                                                                      
    4 root      15  -5     0    0    0 S    0  0.0   0:00.40 ksoftirqd/0                                                                      
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                       
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/1                                                                      
    7 root      15  -5     0    0    0 S    0  0.0   0:00.06 ksoftirqd/1                                                                      
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                       
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2                                                                      
   10 root      15  -5     0    0    0 S    0  0.0   0:00.04 ksoftirqd/2  


multiple sshd sessions from the user XXXXXX...?  is this right??

when i also do this command : ~$ sudo netstat -antp |grep ssh

tcp        0      0 67.228.25.130:36341     84.12.246.196:22        ESTABLISHED 20651/sshd      
tcp        0      0 67.228.25.130:39036     84.14.117.122:22        ESTABLISHED 12534/sshd      
tcp        0     68 67.228.25.130:46065     84.14.104.234:22        ESTABLISHED 1439/sshd       
tcp        0     20 67.228.25.130:47242     84.12.11.154:22         ESTABLISHED 18329/sshd      
tcp        0      1 67.228.25.130:51160     84.11.129.209:22        SYN_SENT    18007/sshd      
tcp        0      1 67.228.25.130:41914     84.12.250.18:22         SYN_SENT    21010/sshd      
tcp        0      0 67.228.25.130:50578     84.12.42.161:22         ESTABLISHED 18390/sshd      
tcp        0     68 67.228.25.130:59240     84.12.245.184:22        ESTABLISHED 20044/sshd      
tcp        0      0 67.228.25.130:47939     84.14.82.12:22          ESTABLISHED 30614/sshd      
tcp        0      0 67.228.25.130:52479     84.12.125.74:22         ESTABLISHED 18644/sshd      
tcp        0      0 67.228.25.130:54427     84.14.111.37:22         ESTABLISHED 8096/sshd       
tcp        0      1 67.228.25.130:50700     84.14.30.138:22         SYN_SENT    25239/sshd      
tcp        0     68 67.228.25.130:41963     84.14.55.190:22         ESTABLISHED 25377/sshd      
tcp        0    144 67.228.25.130:49473     84.13.181.2:22          ESTABLISHED 22665/sshd      
tcp        0      0 67.228.25.130:34499     84.14.44.106:22         ESTABLISHED 25318/sshd      
tcp        0      0 67.228.25.130:45689     84.14.46.7:22           ESTABLISHED 25329/sshd      
tcp        0      1 67.228.25.130:59228     84.14.52.190:22         SYN_SENT    25351/sshd      
tcp        0     84 67.228.25.130:41487     84.14.104.74:22         ESTABLISHED 1222/sshd       
tcp        0      0 67.228.25.130:50543     84.13.71.165:22         ESTABLISHED 22612/sshd      
tcp        0    144 67.228.25.130:54895     84.13.207.181:22        ESTABLISHED 22675/sshd      
tcp        0      1 67.228.25.130:33797     84.14.4.109:22          SYN_SENT    25127/sshd      
tcp        0     84 67.228.25.130:45663     84.10.60.37:22          ESTABLISHED 16173/sshd      
tcp        0     20 67.228.25.130:45673     84.12.245.92:22         ESTABLISHED 20704/sshd      
tcp        0     52 67.228.25.130:52550     84.14.100.90:22         ESTABLISHED 32714/sshd      
tcp        0      0 67.228.25.130:57154     84.12.243.1:22          ESTABLISHED 19933/sshd      
tcp        0      0 67.228.25.130:54616     84.14.104.225:22        ESTABLISHED 1795/sshd       
tcp        0      0 67.228.25.130:35130     84.13.235.138:22        ESTABLISHED 22689/sshd      
tcp        0      0 67.228.25.130:54343     84.12.251.136:22        ESTABLISHED 21394/sshd      
tcp        0    144 67.228.25.130:35235     84.12.166.194:22        ESTABLISHED 18781/sshd      
tcp        0      0 67.228.25.130:58655     84.12.90.204:22         ESTABLISHED 18521/sshd      
tcp        0    144 67.228.25.130:43529     84.14.112.54:22         ESTABLISHED 9469/sshd       
tcp        0      0 67.228.25.130:43108     84.14.17.70:22          ESTABLISHED 25208/sshd      
tcp        0     68 67.228.25.130:60614     84.14.105.172:22        ESTABLISHED 4997/sshd       
tcp        0    296 67.228.25.130:34556     84.12.107.155:22        ESTABLISHED 18585/sshd      
tcp        0    144 67.228.25.130:47333     84.14.8.3:22            ESTABLISHED 25136/sshd      
tcp        0      0 67.228.25.130:47154     84.11.131.53:22         ESTABLISHED 18019/sshd      
tcp        0      0 67.228.25.130:42239     84.14.105.75:22         ESTABLISHED 4610/sshd       
tcp        0      0 67.228.25.130:35603     84.14.53.148:22         ESTABLISHED 25363/sshd      
tcp        0      0 67.228.25.130:54143     84.14.57.155:22         ESTABLISHED 25397/sshd      
tcp        0     52 67.228.25.130:59884     84.12.96.253:22         ESTABLISHED 18533/sshd      
tcp        0      0 67.228.25.130:41332     84.13.95.141:22         ESTABLISHED 22622/sshd      
tcp        0    144 67.228.25.130:59823     84.13.122.38:22         ESTABLISHED 22630/sshd      
tcp        0      0 67.228.25.130:53627     84.14.16.193:22         ESTABLISHED 25225/sshd      
tcp        0     20 67.228.25.130:47173     84.14.53.139:22         ESTABLISHED 25360/sshd      
tcp        0      0 67.228.25.130:33478     84.14.105.164:22        ESTABLISHED 5148/sshd       
tcp        0    144 67.228.25.130:45454     84.14.118.155:22        ESTABLISHED 13061/sshd      
tcp        0      0 67.228.25.130:44981     84.14.110.137:22        ESTABLISHED 7901/sshd       
tcp        0      1 67.228.25.130:58784     84.14.92.2:22           SYN_SENT    32343/sshd      
tcp        0     20 67.228.25.130:51224     84.12.98.130:22         ESTABLISHED 18554/sshd      
tcp        0     84 67.228.25.130:58142     84.14.90.170:22         ESTABLISHED 31507/sshd      
tcp        0    144 67.228.25.130:47650     84.14.115.130:22        ESTABLISHED 12165/sshd      
tcp        0    296 67.228.25.130:33279     84.14.55.50:22          ESTABLISHED 25372/sshd      
tcp        0      0 67.228.25.130:42392     84.14.13.34:22          ESTABLISHED 25177/sshd      
tcp        0     84 67.228.25.130:47048     84.14.42.227:22         ESTABLISHED 25309/sshd      
tcp        0    296 67.228.25.130:41303     84.14.55.51:22          ESTABLISHED 25373/sshd      
tcp        0      0 67.228.25.130:59296     84.12.175.149:22        ESTABLISHED 18791/sshd      
tcp        0      0 67.228.25.130:59731     84.14.55.52:22          ESTABLISHED 25375/sshd      
tcp        0      0 67.228.25.130:36317     84.12.161.45:22         ESTABLISHED 18767/sshd      
tcp        0     68 67.228.25.130:59999     84.14.55.197:22         ESTABLISHED 25379/sshd      
tcp        0    296 67.228.25.130:38679     84.12.107.134:22        ESTABLISHED 18586/sshd      
tcp        0      0 67.228.25.130:42973     84.13.116.64:22         ESTABLISHED 22627/sshd      
tcp        0    296 67.228.25.130:43479     84.14.17.66:22          ESTABLISHED 25206/sshd      
tcp        0      0 67.228.25.130:53286     84.14.16.38:22          ESTABLISHED 25221/sshd      
tcp        0    296 67.228.25.130:58727     84.14.55.198:22         ESTABLISHED 25380/sshd      
tcp        0     84 67.228.25.130:36118     84.14.13.197:22         ESTABLISHED 25170/sshd      
tcp        0      0 67.228.25.130:41778     84.12.212.137:22        ESTABLISHED 18897/sshd      
tcp        0      0 67.228.25.130:44572     84.11.128.129:22        ESTABLISHED 18008/sshd      
tcp        0    296 67.228.25.130:48410     84.13.65.103:22         ESTABLISHED 22608/sshd      
tcp        0      0 67.228.25.130:42967     84.12.213.102:22        ESTABLISHED 18898/sshd      
tcp        0      0 67.228.25.130:52797     84.12.245.224:22        ESTABLISHED 20296/sshd      
tcp        0     52 67.228.25.130:48183     84.14.44.166:22         ESTABLISHED 25330/sshd      
tcp        0    296 67.228.25.130:42412     84.10.10.64:22          ESTABLISHED 16157/sshd      
tcp        0      0 67.228.25.130:50941     84.14.13.35:22          ESTABLISHED 25178/sshd      
tcp        0      0 67.228.25.130:40358     84.12.191.87:22         ESTABLISHED 18836/sshd      
tcp        0    144 67.228.25.130:46088     84.14.46.3:22           ESTABLISHED 25321/sshd      
tcp        0      0 67.228.25.130:33419     84.14.2.186:22          ESTABLISHED 25120/sshd      
tcp        0     52 67.228.25.130:45675     84.12.240.65:22         ESTABLISHED 19486/sshd      
tcp        0      0 67.228.25.130:43180     84.14.46.25:22          ESTABLISHED 25324/sshd      
tcp        0     52 67.228.25.130:37170     84.14.89.145:22         ESTABLISHED 31254/sshd      
tcp        0    296 67.228.25.130:37480     84.13.125.202:22        ESTABLISHED 22633/sshd      
tcp        0     84 67.228.25.130:33514     84.12.177.165:22        ESTABLISHED 18798/sshd      
tcp        0    296 67.228.25.130:54961     84.14.68.218:22         ESTABLISHED 25671/sshd      
tcp        0     52 67.228.25.130:42882     84.14.33.82:22          ESTABLISHED 25250/sshd      
tcp        0      0 67.228.25.130:58864     84.14.57.146:22         ESTABLISHED 25390/sshd      
tcp        0      0 67.228.25.130:55971     84.14.82.13:22          ESTABLISHED 28858/sshd      
tcp        0      0 67.228.25.130:55727     84.14.53.168:22         ESTABLISHED 25365/sshd      
tcp        0    144 67.228.25.130:41604     84.14.3.209:22          ESTABLISHED 25123/sshd      
tcp        0     68 67.228.25.130:46679     84.14.106.110:22        ESTABLISHED 5155/sshd       
tcp        0    144 67.228.25.130:51651     84.14.119.218:22        ESTABLISHED 13174/sshd      
tcp        0      0 67.228.25.130:49373     84.14.91.109:22         ESTABLISHED 32002/sshd      
tcp        0    296 67.228.25.130:52419     84.12.50.248:22         ESTABLISHED 18423/sshd      
tcp        0      0 67.228.25.130:34528     84.14.100.89:22         ESTABLISHED 32348/sshd      
tcp        0     84 67.228.25.130:57863     84.12.127.21:22         ESTABLISHED 18654/sshd      
tcp        0      0 67.228.25.130:52186     84.12.240.18:22         ESTABLISHED 19480/sshd      
tcp        0     84 67.228.25.130:46189     84.14.46.17:22          ESTABLISHED 25327/sshd      
tcp        0      0 67.228.25.130:32959     84.14.57.151:22         ESTABLISHED 25392/sshd      
tcp        0      0 67.228.25.130:59780     84.14.13.111:22         ESTABLISHED 25163/sshd      
tcp        0    144 67.228.25.130:42881     84.12.52.80:22          ESTABLISHED 18424/sshd      
tcp        0     52 67.228.25.130:39242     84.12.179.102:22        ESTABLISHED 18813/sshd      
tcp        0     52 67.228.25.130:58453     84.12.89.72:22          ESTABLISHED 18517/sshd      
tcp        0     68 67.228.25.130:58029     84.9.12.193:22          ESTABLISHED 14874/sshd      
tcp        0      0 67.228.25.130:35486     84.14.58.146:22         ESTABLISHED 25402/sshd      
tcp        0     84 67.228.25.130:44263     84.14.105.68:22         ESTABLISHED 4607/sshd       
tcp        0     68 67.228.25.130:37206     84.12.22.246:22         ESTABLISHED 18363/sshd      
tcp        0     84 67.228.25.130:54112     84.12.42.188:22         ESTABLISHED 18405/sshd      
tcp        0      0 67.228.25.130:34140     84.14.17.69:22          ESTABLISHED 25207/sshd      
tcp        0      0 67.228.25.130:34140     84.14.17.69:22          ESTABLISHED 25207/sshd      
tcp        0      0 67.228.25.130:44977     84.14.104.231:22        ESTABLISHED 2154/sshd       
tcp        0     68 67.228.25.130:34066     84.12.137.213:22        ESTABLISHED 18691/sshd      
tcp        0      0 67.228.25.130:35450     84.14.82.99:22          ESTABLISHED 28964/sshd      
tcp        0      0 67.228.25.130:50497     84.12.20.27:22          ESTABLISHED 18355/sshd      
tcp        0      0 67.228.25.130:41667     84.14.108.66:22         ESTABLISHED 6418/sshd       
tcp        0      0 67.228.25.130:34997     84.14.57.149:22         ESTABLISHED 25391/sshd      
tcp        0     84 67.228.25.130:53852     84.12.54.94:22          ESTABLISHED 18444/sshd      
tcp        0     84 67.228.25.130:52813     84.14.57.98:22          ESTABLISHED 25394/sshd      
tcp        0      0 67.228.25.130:54119     84.14.13.36:22          ESTABLISHED 25176/sshd      
tcp        0      0 67.228.25.130:60161     84.14.42.132:22         ESTABLISHED 25301/sshd      
tcp        0      0 67.228.25.130:59557     84.14.117.124:22        ESTABLISHED 12779/sshd      
tcp        0     84 67.228.25.130:48024     84.14.105.82:22         ESTABLISHED 4602/sshd       
tcp        0     84 67.228.25.130:48024     84.14.105.82:22         ESTABLISHED 4602/sshd       
tcp        0      0 67.228.25.130:49790     84.14.30.4:22           ESTABLISHED 25247/sshd      
tcp        0      0 67.228.25.130:59564     84.14.42.45:22          ESTABLISHED 25295/sshd      
tcp        0      0 67.228.25.130:59564     84.14.42.45:22          ESTABLISHED 25295/sshd      
tcp        0      0 67.228.25.130:37158     84.12.97.70:22          ESTABLISHED 18535/sshd      
tcp        0      0 67.228.25.130:49365     84.14.121.27:22         ESTABLISHED 13788/sshd      
tcp        0      0 67.228.25.130:34752     84.14.42.131:22         ESTABLISHED 25300/sshd      
tcp        0     20 67.228.25.130:60592     84.14.90.178:22         ESTABLISHED 31458/sshd      
tcp        0      0 67.228.25.130:42699     84.14.106.74:22         ESTABLISHED 6086/sshd       
tcp        0      1 67.228.25.130:42634     84.12.252.174:22        SYN_SENT    22201/sshd      
tcp        0      0 67.228.25.130:59596     84.14.64.234:22         ESTABLISHED 25422/sshd      
tcp6       0      0 :::22                   :::*                    LISTEN      18452/sshd      
tcp6       0      0 67.228.174.90:22        98.197.250.234:50731    ESTABLISHED 8937/sshd: ewingate

some of this just doesnt seem right... we only have about 4 users on the server... and to me it seems like there are multiple SSH sessions?  or maybe like someone trying to guess the passwords of our users by making multiple connections?!?!

I dont know.. someone please help before my server gets HACKED!! thank you!

---

### Post by tubasoldier on 2009-10-17
If no one in your organization uses SSH then turn it off.

---

### Post by yeats on 2009-10-17
What is this server used for?  Do you have any sort of firewall set up?

---

### Post by ericosuave on 2009-10-17
this server is a webserver.. no firewalls were setup.  we host multiple websites on this machine.  I use SSH to access the machine remotely.  The machine resides in Dallas and I am in Houston.  so i have to use SSH to access it.

---

### Post by yeats on 2009-10-17
You might want to set an alternative SSH port.  Do you have any KVM capability that will allow you to access your machine without using SSH?

You will also want to set up IPTABLES or a similar firewall.  Part I of a multi-part video tutorial is here:

[http://www.youtube.com/watch?v=ldB8kDEtTZA](http://www.youtube.com/watch?v=ldB8kDEtTZA)

---

### Post by ericosuave on 2009-10-17
in the mean time is there any way that i can kill that user and stop those SSH services?  well without killing the SSH service, cause it will boot me off the machine as well.

I do also have access to KVM.. so should I do it from there and just STOP SSH until i get iptables working?  I am also thinking of installing fail2ban..

---

### Post by Neezer on 2009-10-17
> **ericosuave said:**
> in the mean time is there any way that i can kill that user and stop those SSH services?  well without killing the SSH service, cause it will boot me off the machine as well.

I do also have access to KVM.. so should I do it from there and just STOP SSH until i get iptables working?  I am also thinking of installing fail2ban..

setting up a key to log in will help if you don't already have it set up. I went through the process of setting up keys and it is somewhat documented here:
[http://ubuntuforums.org/showthread.php?t=1276544](http://ubuntuforums.org/showthread.php?t=1276544)

Hope that helps....

also, once you have the key setup, I used fail2ban, that bans ip addresses if they try to log in and fail more than 4 or 5 times. That way you cannot be brute force hacked. the key is a lot more secure than a password. Especially if your user password isn't a very good one.

---

### Post by ericosuave on 2009-10-17
ok so now there is a process called Pscan2 that is running... everytime i kill it, it just comes back on again.  It seems as if ive been hacked...  what is the proper steps to take so i can get this hacker off my machine and secure it?

how can i find out where this pscan2 service is running from?

---

### Post by ericosuave on 2009-10-17
ok i kind of figured out what the hacker is doing....  there is something called pscan2 that is running first than calls sshd to be run as well... multiple times..

when i terminate the sshd process.. all the sshd instances are removed from top, but than like 2 seconds later, this pscan2 process runs and all the SSHD processes start coming back again..

how can i find this pscan2 thing and kill it?  im sure its a file somewhere that automatically runs.  I did some research and found out that it was a C program that runs.   But i dont know where to find the damn thing!

---

### Post by cariboo on 2009-10-17
Maybe this [thread]("http://ubuntuforums.org/archive/index.php/t-253373.html") will help

---

### Post by ericosuave on 2009-10-17
wow... just to let you guys know.. i got the problem fixed.  someone did hack our server and they created multiple files that exploited our server..  we found these files and moved them to another home directory account...  also killed pearl process because thats what was fueling the fire.. and we werent using pearl so we just got rid of it!

---

### Post by Lars Noodén on 2009-10-18
First, if you can give some sanitized description, how did they get in?  e.g. PHP?

Second, if you are connecting from the same ip addresses or sub-nets, you can use tcpd to limit which connections sshd accepts.  See the man pages for [URL="http://linux.die.net/man/5/hosts.allow"]hosts.allow
[/URL] and [URL="http://linux.die.net/man/5/hosts.deny"]hosts.deny
[/URL]

From /etc/hosts.allow:
[INDENT][FONT="Courier New"]sshd: 84.14.0.0/16
[/FONT][/INDENT]

From /etc/hosts.deny:
[INDENT][FONT="Courier New"]sshd: all
[/FONT][/INDENT]

---

### Post by ericosuave on 2009-10-19
I dont understand? how could they get in with PHP? im new to this...

---

### Post by Lars Noodén on 2009-10-19
Without going into private details, how did they get into your system?

---

### Post by CharlesA on 2009-10-19
If there was no security in place, probably ended up brute forcing the user/pass. Especially since SSH was running on the default port.

just a guess, since I am not a security expert.

As it's been said: Limit SSH connectivity using hosts.allow and hosts.deny. Also, you can set up an auth key to be used instead of a password to help secure your server. Something like DenyHosts or fail2ban to lock it down if you want to use passwords would help as well.

Not to mention moving the ssh port to a non-standard port.

---

### Post by Lars Noodén on 2009-10-19
> **CharlesA said:**
> If there was no security in place, probably ended up brute forcing the user/pass. Especially since SSH was running on the default port.


Brute force attacks has to do with the passwords being used not the port being used.  Can be done on any port that sshd responds to, even non-standard ports.

---

### Post by CharlesA on 2009-10-19
> **Lars Noodén said:**
> Brute force attacks has to do with the passwords being used not the port being used.  Can be done on any port that sshd responds to, even non-standard ports.

That's true, yes, but the thing is that it was running on the default port. As far as I know there are many bots/whatever that scan for port 22 and try to hack in that way without trying different ports. If I am wrong, please let me know. :)

---

### Post by Lars Noodén on 2009-10-20
> **CharlesA said:**
> That's true, yes, but the thing is that it was running on the default port. As far as I know there are many bots/whatever that scan for port 22 and try to hack in that way without trying different ports. If I am wrong, please let me know. :)

That happens, too.  Not running sshd daemonized and using inetd instead, with a bit of delay, will also send that kind of scanner on its way.  

You'll also see probes that scan for open ports to inventory the services.  This can happen when there are exploits available, but not necessarily acknowledged by the vendor, and an attack is in the making.  

Moving the port isn't really clever, it's just making an inconvenience.  Though some people enjoy that, not realizing that Effort != Result.  
If you don't want to use the standardized communications port for ssh, then why not jump in with both feet and try [port knocking](http://ubuntuforums.org/showthread.php?t=812573)?  [knockd](http://linux.die.net/man/1/knockd) is just one of several and I see how you could probably make your own with just IP Tables.
[http://www.ducea.com/2006/07/05/how-to-safely-connect-from-anywhere-to-your-closed-linux-firewall/](http://www.ducea.com/2006/07/05/how-to-safely-connect-from-anywhere-to-your-closed-linux-firewall/)

---

### Post by CharlesA on 2009-10-20
Thanks for the infos! I was mainly saying that changing the port number in addition to any other security settings would help secure SSH. I might take a look at port knocking, but for the time being, I've locked my server down so that it can only be accessed from 2 IP addresses and drops packets from everything else. So far no problems.

---

### Post by virtuoosi on 2009-10-20
In my case I was advised to set ssh to use RSA keys instead of plain passwords. Key based logins combined with a custom port is a pretty good combo, adds a nice layer of security to your server. :)

Here's the link I followed to set up the keys
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

