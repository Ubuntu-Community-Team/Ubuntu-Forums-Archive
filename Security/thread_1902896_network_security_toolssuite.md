---
title: "network security tools/suite"
date: 2012-01-01
forum: Security
---

### Post by z3nhakr on 2012-01-01
I'm working on a security tool for Linux to scan for vulnerabilities in my network. instead of trying to fix problems, it will work as a warning system and send me an email if it detects apr attacks, dos attacks or duplicate mac addresses. id be glad to pack this into a deb and open source it after i finish but for now im stuck on detecting duplicate macs/mac spoofing. i was thinking of using nmap to scan for hosts and then make a script to compare the results but nmap always gives to many details which makes comparing things a pain in the backside to do. does anyone know how to get a cleaner output from nmap or another network scaner with a cleaner output.

---

### Post by Dangertux on 2012-01-02
> **z3nhakr said:**
> I'm working on a security tool for Linux to scan for vulnerabilities in my network. instead of trying to fix problems, it will work as a warning system and send me an email if it detects apr attacks, dos attacks or duplicate mac addresses. id be glad to pack this into a deb and open source it after i finish but for now im stuck on detecting duplicate macs/mac spoofing. i was thinking of using nmap to scan for hosts and then make a script to compare the results but nmap always gives to many details which makes comparing things a pain in the backside to do. does anyone know how to get a cleaner output from nmap or another network scaner with a cleaner output.

nmap has a ton of options that you could explore. Particularly I would suggest ping scanning for this, or you can do a full scan output the file into grepable format and grep through it.

so an example command might be 

```

nmap -sP -oG filename 192.168.0.0/24

```then

```

cat filename | grep "[0-9]*:[0-9]*:[0-9*]:[0-9]*:[0-9]*:[0-9]*"

```Or whatever options you wanted to throw on there -A would probably be handy for nmap's output.

Also they have these types of tools already, they're called IDS. I would check out Snort or Suricatta. Hope this helps

---

### Post by mattxhand on 2012-01-03
So is this going to be something like Nessus?

---

### Post by Dangertux on 2012-01-03
> **mattxhand said:**
> So is this going to be something like Nessus?


From the description OP gave it sounds more like OSSEC or Snort. Nessus pretty much just scans versioning information and looks for known vulnerabilities. This seems more like it would detect certain attacks as they're happening as opposed to the potential for an attack to occur.

---

### Post by z3nhakr on 2012-01-08
Like dangertux said, im not trying to find holes but instead making a warning system that can notify me and possibly execute an emergency shutdown of vital network components. I tried grep-ing the nmap  results and it told me i had new mail in /var/mail/root but nothing was there from today!? BTW -A(os detection) doesn't work without a port scan.

---

### Post by Dangertux on 2012-01-08
> **z3nhakr said:**
> Like dangertux said, im not trying to find holes but instead making a warning system that can notify me and possibly execute an emergency shutdown of vital network components. I tried grep-ing the nmap  results and it told me i had new mail in /var/mail/root but nothing was there from today!? BTW -A(os detection) doesn't work without a port scan.

-O is OS Scan

-A is run all script in NSE (it also triggers a -sS scan automatically) 

In any case they were two seperate thoughts. One for mac addresses the other for OS fingerprinting.

:-/

---

### Post by z3nhakr on 2012-01-09
my bad :P
any ideas on why grep isn't working?

i had to run nmap as root to get mac addresses but grep has no output because nmap isn't including the macs in the output file

Here's the code

```

z3n@z3n-System-Product-Name:~$ nmap -sP -oG ./nout 10.0.1.0/24

Starting Nmap 5.21 ( http://nmap.org ) at 2012-01-09 18:29 GST
Nmap scan report for 10.0.1.1
Host is up (0.0017s latency).
Nmap scan report for 10.0.1.5
Host is up (0.0043s latency).
Nmap scan report for 10.0.1.6
Host is up (0.10s latency).
Nmap scan report for 10.0.1.9
Host is up (0.082s latency).
Nmap scan report for 10.0.1.10
Host is up (0.0067s latency).
Nmap scan report for 10.0.1.11
Host is up (0.015s latency).
Nmap scan report for 10.0.1.14
Host is up (0.082s latency).
Nmap scan report for 10.0.1.16
Host is up (0.43s latency).
Nmap scan report for 10.0.1.17
Host is up (0.041s latency).
Nmap scan report for 10.0.1.23
Host is up (0.0053s latency).
Nmap scan report for 10.0.1.27
Host is up (0.044s latency).
Nmap scan report for 10.0.1.37
Host is up (0.0067s latency).
Nmap scan report for 10.0.1.45
Host is up (0.00080s latency).
Nmap done: 256 IP addresses (13 hosts up) scanned in 28.86 seconds
z3n@z3n-System-Product-Name:~$ sudo nmap -sP -oG ./nout 10.0.1.0/24

Starting Nmap 5.21 ( http://nmap.org ) at 2012-01-09 18:30 GST
Nmap scan report for 10.0.1.1
Host is up (0.0020s latency).
MAC Address: 00:26:BB:73:B2:A0 (Apple)
Nmap scan report for 10.0.1.5
Host is up (0.0033s latency).
MAC Address: 00:25:4B:0A:B1:3E (Apple)
Nmap scan report for 10.0.1.6
Host is up (0.076s latency).
MAC Address: 34:15:9E:69:9F:62 (Unknown)
Nmap scan report for 10.0.1.9
Host is up (0.090s latency).
MAC Address: CC:08:E0:CC:04:7E (Unknown)
Nmap scan report for 10.0.1.10
Host is up (0.0026s latency).
MAC Address: 00:24:01:13:E4:B9 (D-Link)
Nmap scan report for 10.0.1.11
Host is up (0.33s latency).
MAC Address: 00:21:5A:B2:97:26 (Hewlett Packard)
Nmap scan report for 10.0.1.12
Host is up (0.27s latency).
MAC Address: A4:67:06:28:88:B7 (Unknown)
Nmap scan report for 10.0.1.13
Host is up (0.094s latency).
MAC Address: A8:6A:6F:CE:D4:3D (Unknown)
Nmap scan report for 10.0.1.14
Host is up (0.15s latency).
MAC Address: A4:67:06:12:C1:66 (Unknown)
Nmap scan report for 10.0.1.17
Host is up (0.0015s latency).
MAC Address: 00:24:8C:A7:80:4C (Asustek Computer)
Nmap scan report for 10.0.1.18
Host is up (0.097s latency).
MAC Address: 00:1C:DF:1B:D2:DB (Belkin International)
Nmap scan report for 10.0.1.23
Host is up (0.0015s latency).
MAC Address: E4:CE:8F:6D:CD:4E (Unknown)
Nmap scan report for 10.0.1.25
Host is up (0.30s latency).
MAC Address: 58:B0:35:34:2F:73 (Unknown)
Nmap scan report for 10.0.1.27
Host is up (0.11s latency).
MAC Address: 00:0C:F1:51:99:A0 (Intel)
Nmap scan report for 10.0.1.45
Host is up.
Nmap done: 256 IP addresses (15 hosts up) scanned in 9.54 seconds
z3n@z3n-System-Product-Name:~$ cat ./nout | grep "[0-9]*:[0-9]*:[0-9*]:[0-9]*:[0-9]*:[0-9]*"
z3n@z3n-System-Product-Name:~$ 

```And here is the output file

```

# Nmap 5.21 scan initiated Mon Jan  9 18:30:25 2012 as: nmap -sP -oG ./nout 10.0.1.0/24 
Host: 10.0.1.0 ()    Status: Down
Host: 10.0.1.1 ()    Status: Up
Host: 10.0.1.2 ()    Status: Down
Host: 10.0.1.3 ()    Status: Down
Host: 10.0.1.4 ()    Status: Down
Host: 10.0.1.5 ()    Status: Up
Host: 10.0.1.6 ()    Status: Up
Host: 10.0.1.7 ()    Status: Down
Host: 10.0.1.8 ()    Status: Down
Host: 10.0.1.9 ()    Status: Up
Host: 10.0.1.10 ()    Status: Up
Host: 10.0.1.11 ()    Status: Up
Host: 10.0.1.12 ()    Status: Up
Host: 10.0.1.13 ()    Status: Up
Host: 10.0.1.14 ()    Status: Up
Host: 10.0.1.15 ()    Status: Down
Host: 10.0.1.16 ()    Status: Down
Host: 10.0.1.17 ()    Status: Up
Host: 10.0.1.18 ()    Status: Up
Host: 10.0.1.19 ()    Status: Down
Host: 10.0.1.20 ()    Status: Down
Host: 10.0.1.21 ()    Status: Down
Host: 10.0.1.22 ()    Status: Down
Host: 10.0.1.23 ()    Status: Up
Host: 10.0.1.24 ()    Status: Down
Host: 10.0.1.25 ()    Status: Up
Host: 10.0.1.26 ()    Status: Down
Host: 10.0.1.27 ()    Status: Up
Host: 10.0.1.28 ()    Status: Down
Host: 10.0.1.29 ()    Status: Down
Host: 10.0.1.30 ()    Status: Down
Host: 10.0.1.31 ()    Status: Down
Host: 10.0.1.32 ()    Status: Down
Host: 10.0.1.33 ()    Status: Down
Host: 10.0.1.34 ()    Status: Down
Host: 10.0.1.35 ()    Status: Down
Host: 10.0.1.36 ()    Status: Down
Host: 10.0.1.37 ()    Status: Down
Host: 10.0.1.38 ()    Status: Down
Host: 10.0.1.39 ()    Status: Down
Host: 10.0.1.40 ()    Status: Down
Host: 10.0.1.41 ()    Status: Down
Host: 10.0.1.42 ()    Status: Down
Host: 10.0.1.43 ()    Status: Down
Host: 10.0.1.44 ()    Status: Down
Host: 10.0.1.45 ()    Status: Up
Host: 10.0.1.46 ()    Status: Down
Host: 10.0.1.47 ()    Status: Down
Host: 10.0.1.48 ()    Status: Down
Host: 10.0.1.49 ()    Status: Down
Host: 10.0.1.50 ()    Status: Down
Host: 10.0.1.51 ()    Status: Down
Host: 10.0.1.52 ()    Status: Down
Host: 10.0.1.53 ()    Status: Down
Host: 10.0.1.54 ()    Status: Down
Host: 10.0.1.55 ()    Status: Down
Host: 10.0.1.56 ()    Status: Down
Host: 10.0.1.57 ()    Status: Down
Host: 10.0.1.58 ()    Status: Down
Host: 10.0.1.59 ()    Status: Down
Host: 10.0.1.60 ()    Status: Down
Host: 10.0.1.61 ()    Status: Down
Host: 10.0.1.62 ()    Status: Down
Host: 10.0.1.63 ()    Status: Down
Host: 10.0.1.64 ()    Status: Down
Host: 10.0.1.65 ()    Status: Down
Host: 10.0.1.66 ()    Status: Down
Host: 10.0.1.67 ()    Status: Down
Host: 10.0.1.68 ()    Status: Down
Host: 10.0.1.69 ()    Status: Down
Host: 10.0.1.70 ()    Status: Down
Host: 10.0.1.71 ()    Status: Down
Host: 10.0.1.72 ()    Status: Down
Host: 10.0.1.73 ()    Status: Down
Host: 10.0.1.74 ()    Status: Down
Host: 10.0.1.75 ()    Status: Down
Host: 10.0.1.76 ()    Status: Down
Host: 10.0.1.77 ()    Status: Down
Host: 10.0.1.78 ()    Status: Down
Host: 10.0.1.79 ()    Status: Down
Host: 10.0.1.80 ()    Status: Down
Host: 10.0.1.81 ()    Status: Down
Host: 10.0.1.82 ()    Status: Down
Host: 10.0.1.83 ()    Status: Down
Host: 10.0.1.84 ()    Status: Down
Host: 10.0.1.85 ()    Status: Down
Host: 10.0.1.86 ()    Status: Down
Host: 10.0.1.87 ()    Status: Down
Host: 10.0.1.88 ()    Status: Down
Host: 10.0.1.89 ()    Status: Down
Host: 10.0.1.90 ()    Status: Down
Host: 10.0.1.91 ()    Status: Down
Host: 10.0.1.92 ()    Status: Down
Host: 10.0.1.93 ()    Status: Down
Host: 10.0.1.94 ()    Status: Down
Host: 10.0.1.95 ()    Status: Down
Host: 10.0.1.96 ()    Status: Down
Host: 10.0.1.97 ()    Status: Down
Host: 10.0.1.98 ()    Status: Down
Host: 10.0.1.99 ()    Status: Down
Host: 10.0.1.100 ()    Status: Down
Host: 10.0.1.101 ()    Status: Down
Host: 10.0.1.102 ()    Status: Down
Host: 10.0.1.103 ()    Status: Down
Host: 10.0.1.104 ()    Status: Down
Host: 10.0.1.105 ()    Status: Down
Host: 10.0.1.106 ()    Status: Down
Host: 10.0.1.107 ()    Status: Down
Host: 10.0.1.108 ()    Status: Down
Host: 10.0.1.109 ()    Status: Down
Host: 10.0.1.110 ()    Status: Down
Host: 10.0.1.111 ()    Status: Down
Host: 10.0.1.112 ()    Status: Down
Host: 10.0.1.113 ()    Status: Down
Host: 10.0.1.114 ()    Status: Down
Host: 10.0.1.115 ()    Status: Down
Host: 10.0.1.116 ()    Status: Down
Host: 10.0.1.117 ()    Status: Down
Host: 10.0.1.118 ()    Status: Down
Host: 10.0.1.119 ()    Status: Down
Host: 10.0.1.120 ()    Status: Down
Host: 10.0.1.121 ()    Status: Down
Host: 10.0.1.122 ()    Status: Down
Host: 10.0.1.123 ()    Status: Down
Host: 10.0.1.124 ()    Status: Down
Host: 10.0.1.125 ()    Status: Down
Host: 10.0.1.126 ()    Status: Down
Host: 10.0.1.127 ()    Status: Down
Host: 10.0.1.128 ()    Status: Down
Host: 10.0.1.129 ()    Status: Down
Host: 10.0.1.130 ()    Status: Down
Host: 10.0.1.131 ()    Status: Down
Host: 10.0.1.132 ()    Status: Down
Host: 10.0.1.133 ()    Status: Down
Host: 10.0.1.134 ()    Status: Down
Host: 10.0.1.135 ()    Status: Down
Host: 10.0.1.136 ()    Status: Down
Host: 10.0.1.137 ()    Status: Down
Host: 10.0.1.138 ()    Status: Down
Host: 10.0.1.139 ()    Status: Down
Host: 10.0.1.140 ()    Status: Down
Host: 10.0.1.141 ()    Status: Down
Host: 10.0.1.142 ()    Status: Down
Host: 10.0.1.143 ()    Status: Down
Host: 10.0.1.144 ()    Status: Down
Host: 10.0.1.145 ()    Status: Down
Host: 10.0.1.146 ()    Status: Down
Host: 10.0.1.147 ()    Status: Down
Host: 10.0.1.148 ()    Status: Down
Host: 10.0.1.149 ()    Status: Down
Host: 10.0.1.150 ()    Status: Down
Host: 10.0.1.151 ()    Status: Down
Host: 10.0.1.152 ()    Status: Down
Host: 10.0.1.153 ()    Status: Down
Host: 10.0.1.154 ()    Status: Down
Host: 10.0.1.155 ()    Status: Down
Host: 10.0.1.156 ()    Status: Down
Host: 10.0.1.157 ()    Status: Down
Host: 10.0.1.158 ()    Status: Down
Host: 10.0.1.159 ()    Status: Down
Host: 10.0.1.160 ()    Status: Down
Host: 10.0.1.161 ()    Status: Down
Host: 10.0.1.162 ()    Status: Down
Host: 10.0.1.163 ()    Status: Down
Host: 10.0.1.164 ()    Status: Down
Host: 10.0.1.165 ()    Status: Down
Host: 10.0.1.166 ()    Status: Down
Host: 10.0.1.167 ()    Status: Down
Host: 10.0.1.168 ()    Status: Down
Host: 10.0.1.169 ()    Status: Down
Host: 10.0.1.170 ()    Status: Down
Host: 10.0.1.171 ()    Status: Down
Host: 10.0.1.172 ()    Status: Down
Host: 10.0.1.173 ()    Status: Down
Host: 10.0.1.174 ()    Status: Down
Host: 10.0.1.175 ()    Status: Down
Host: 10.0.1.176 ()    Status: Down
Host: 10.0.1.177 ()    Status: Down
Host: 10.0.1.178 ()    Status: Down
Host: 10.0.1.179 ()    Status: Down
Host: 10.0.1.180 ()    Status: Down
Host: 10.0.1.181 ()    Status: Down
Host: 10.0.1.182 ()    Status: Down
Host: 10.0.1.183 ()    Status: Down
Host: 10.0.1.184 ()    Status: Down
Host: 10.0.1.185 ()    Status: Down
Host: 10.0.1.186 ()    Status: Down
Host: 10.0.1.187 ()    Status: Down
Host: 10.0.1.188 ()    Status: Down
Host: 10.0.1.189 ()    Status: Down
Host: 10.0.1.190 ()    Status: Down
Host: 10.0.1.191 ()    Status: Down
Host: 10.0.1.192 ()    Status: Down
Host: 10.0.1.193 ()    Status: Down
Host: 10.0.1.194 ()    Status: Down
Host: 10.0.1.195 ()    Status: Down
Host: 10.0.1.196 ()    Status: Down
Host: 10.0.1.197 ()    Status: Down
Host: 10.0.1.198 ()    Status: Down
Host: 10.0.1.199 ()    Status: Down
Host: 10.0.1.200 ()    Status: Down
Host: 10.0.1.201 ()    Status: Down
Host: 10.0.1.202 ()    Status: Down
Host: 10.0.1.203 ()    Status: Down
Host: 10.0.1.204 ()    Status: Down
Host: 10.0.1.205 ()    Status: Down
Host: 10.0.1.206 ()    Status: Down
Host: 10.0.1.207 ()    Status: Down
Host: 10.0.1.208 ()    Status: Down
Host: 10.0.1.209 ()    Status: Down
Host: 10.0.1.210 ()    Status: Down
Host: 10.0.1.211 ()    Status: Down
Host: 10.0.1.212 ()    Status: Down
Host: 10.0.1.213 ()    Status: Down
Host: 10.0.1.214 ()    Status: Down
Host: 10.0.1.215 ()    Status: Down
Host: 10.0.1.216 ()    Status: Down
Host: 10.0.1.217 ()    Status: Down
Host: 10.0.1.218 ()    Status: Down
Host: 10.0.1.219 ()    Status: Down
Host: 10.0.1.220 ()    Status: Down
Host: 10.0.1.221 ()    Status: Down
Host: 10.0.1.222 ()    Status: Down
Host: 10.0.1.223 ()    Status: Down
Host: 10.0.1.224 ()    Status: Down
Host: 10.0.1.225 ()    Status: Down
Host: 10.0.1.226 ()    Status: Down
Host: 10.0.1.227 ()    Status: Down
Host: 10.0.1.228 ()    Status: Down
Host: 10.0.1.229 ()    Status: Down
Host: 10.0.1.230 ()    Status: Down
Host: 10.0.1.231 ()    Status: Down
Host: 10.0.1.232 ()    Status: Down
Host: 10.0.1.233 ()    Status: Down
Host: 10.0.1.234 ()    Status: Down
Host: 10.0.1.235 ()    Status: Down
Host: 10.0.1.236 ()    Status: Down
Host: 10.0.1.237 ()    Status: Down
Host: 10.0.1.238 ()    Status: Down
Host: 10.0.1.239 ()    Status: Down
Host: 10.0.1.240 ()    Status: Down
Host: 10.0.1.241 ()    Status: Down
Host: 10.0.1.242 ()    Status: Down
Host: 10.0.1.243 ()    Status: Down
Host: 10.0.1.244 ()    Status: Down
Host: 10.0.1.245 ()    Status: Down
Host: 10.0.1.246 ()    Status: Down
Host: 10.0.1.247 ()    Status: Down
Host: 10.0.1.248 ()    Status: Down
Host: 10.0.1.249 ()    Status: Down
Host: 10.0.1.250 ()    Status: Down
Host: 10.0.1.251 ()    Status: Down
Host: 10.0.1.252 ()    Status: Down
Host: 10.0.1.253 ()    Status: Down
Host: 10.0.1.254 ()    Status: Down
Host: 10.0.1.255 ()    Status: Down
# Nmap done at Mon Jan  9 18:30:34 2012 -- 256 IP addresses (15 hosts up) scanned in 9.54 seconds

```

---

### Post by z3nhakr on 2012-01-09
**UPDATE**

i got the macs in the output file by using :

```
nmap -sP 10.0.1.0/24 >> ./nout

```but it still wont grep right. here's what I've tried and what i get:


```
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep ": [0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*"
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep "[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*"
MAC Address: A4:67:06:28:88:B7 (Unknown)
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep "**:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*"
MAC Address: A4:67:06:28:88:B7 (Unknown)
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep "[0-9][a-f]:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*"
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep "[0-9].:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*"
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep ".[0-9]:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*"
MAC Address: A4:67:06:28:88:B7 (Unknown)
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep "[0-9][.]:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*"
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep "[0-9]*:[0-9]:[0-9]*:[0-9]*:[0-9]*:[0-9]*"
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep "[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*"
MAC Address: A4:67:06:28:88:B7 (Unknown)
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep "[0-9].*:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*"
MAC Address: A4:67:06:28:88:B7 (Unknown)
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep ".[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*"
MAC Address: A4:67:06:28:88:B7 (Unknown)
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep "[0-9][a-f]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*"
MAC Address: A4:67:06:28:88:B7 (Unknown)
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep "[0-9][A-F]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*"
MAC Address: A4:67:06:28:88:B7 (Unknown)
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep "[0-9][a-z]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*"
MAC Address: A4:67:06:28:88:B7 (Unknown)
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep "[abcdef0123456789]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*"
MAC Address: A4:67:06:28:88:B7 (Unknown)
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep "{abcdef0123456789}*:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*"
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep "[abcdef0123456789]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*"
MAC Address: A4:67:06:28:88:B7 (Unknown)
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep "{abcdef0123456789}*:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*"
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep '[abcdef0123456789]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*'
MAC Address: A4:67:06:28:88:B7 (Unknown)
z3n@z3n-System-Product-Name:~$ sudo cat ./nout | grep -o '[abcdef0123456789]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*:[0-9]*'
4:67:06:28:88:
```
you cant see it here but only 4:67:06:28:88: is highlighted. Maybe letters are confusing it?

---

### Post by hackertarget on 2012-01-11
From the output you have with that command there is no need to get fancy with grep. 

"Grep MAC" to get the MAC Address line and then use cut to pull out the field. Since the output is standardized you will always have the 3rd field as the MAC address.

```

cat ./nout | grep MAC | cut -f 3 -d ' '

```
or all in one command
```

nmap -sP 10.0.1.0/24 | grep MAC | cut -f 3 -d ' ' > mac-addresses.txt

```

A last note, I would suggest not using sudo when manipulating text files and bash scripting unless you really need it. Otherwise mistakes can be made that can break your system.

---

### Post by z3nhakr on 2012-01-16
_***WORKS!!!***_

Is there a way to find duplicates without deleting them?

right now i'm using "sort -u >> ./nout2" and then " if diff" to compare ./nout and ./nout2 but it would be faster if i could do it with one command.

---

### Post by hackertarget on 2012-01-16
Like this?

```
cat ./nout | grep MAC | cut -f 3 -d ' ' | sort | uniq
```

---

### Post by emiller12345 on 2012-01-18
try this...
```
$ sudo nmap -sP -n 10.0.1.0/24 | grep -o "\([0-9A-F]\{2\}:\)\{5\}[0-9A-F]\{2\}" | sort | uniq -c
```

---

