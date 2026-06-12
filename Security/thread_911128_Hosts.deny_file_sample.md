---
title: "Hosts.deny file sample??"
date: 2008-09-05
forum: Security
---

### Post by matey3 on 2008-09-05
Hello;

Can someone post either copy of IP inputs in their /etc/hosts.deny file or post the Correct way of inputting the IP addresses in there please?

No matter what I put there I get an error. (My log file is /var/log/auth.log btw,)

Like when I put : (colon) to separate the IP addresses I get:
 warning: /etc/hosts.deny, line 21: missing ":" separator

Or when I put a \ (backslash) I get:

 warning: /etc/hosts.deny, line 31: missing newline or line too long

Here's part of my hosts.deny:   (And I dont care if YOUR IP address is in the *hitlist) :D lol j/k ;)

# versions of Debian this has been the default.
# ALL: PARANOID
ALL:
79.187.241.62\
82.50.250.22\
82.179.130.135\
69.80.255.165\
219.150.196.6\
83.16.112.18\
222.191.240.194\
219.150.196.0/12\
168.234.227.2\
219.150.196.6\
200.228.120.130\



I Have searched the net but found many diff. versions. many of them put a comma , between the IP addresses but that was the 1st try and of course got the same error?!But most site won't even post this portion of their .deny file I dont know why? May be CYA policy? but any way they could've used private IP addresses or A.B.C.. as examples...

Thanks a lot!

oh I am using Debian/Ubuntu Feisty 7.04 btw.

---

### Post by brian_p on 2008-09-05
> **matey3 said:**
> 

Like when I put : (colon) to separate the IP addresses I get:
 warning: /etc/hosts.deny, line 21: missing ":" separator

I think there has to be a space after a ':'.

>  warning: /etc/hosts.deny, line 31: missing newline or line too long

# versions of Debian this has been the default.
# ALL: PARANOID
ALL:
79.187.241.62\


```
ALL: \
```

---

### Post by matey3 on 2008-09-05
Thanks a lot Brian.
I am getting no errors now...
here what it looks like:
(I took no chances and tried to mix/match to see what line number gives error. No errors but I just got attacked by that damn 200 IP again?)


# ALL: PARANOID
ALL:
79.187.241.62:,
82.50.250.22:,
82.179.130.135:,\
69.80.255.165:,
219.150.196.6:,
83.16.112.18:\
222.191.240.194:\
219.150.196.0/12:,
168.234.227.2:,
219.150.196.6:,  
200.228.120.130:,
222.168.56.78:,
222.168.*:,

---

### Post by hyper_ch on 2008-09-05
my hosts.deny looks like:
```

ALL: 74.52.109.98
ALL: 203.200.160.166
ALL: 70.84.177.26
ALL: 203.177.104.72
ALL: 213.243.33.163
ALL: 216.180.225.226
ALL: 210.180.41.198
ALL: 70.87.154.194
ALL: 67.59.38.170
ALL: 85.43.61.93
ALL: 220.135.29.35
ALL: 62.44.196.12
ALL: 219.80.36.222
ALL: 88.119.144.14
ALL: 59.126.248.179
ALL: 72.232.216.162
ALL: 200.181.121.140
ALL: 61.177.143.205
ALL: 190.144.188.90
ALL: 85.17.134.223
ALL: 24.166.56.143
ALL: 81.91.67.98
ALL: 85.17.141.40
ALL: 82.160.94.71
ALL: 208.78.42.82
ALL: 201.26.212.89
ALL: 88.156.186.98
ALL: 92.65.178.51
ALL: 200.157.247.126
ALL: 61.194.81.36
ALL: 218.75.61.125
ALL: 82.187.180.163
ALL: 83.9.100.117
ALL: 80.241.169.31
ALL: 212.248.196.12
ALL: 207.6.70.91
ALL: 66.46.41.11
ALL: 218.228.194.214
ALL: 200.108.192.37
ALL: 89.107.213.45
ALL: 64.33.51.237
ALL: 70.90.124.130
ALL: 213.203.143.213
ALL: 85.5.93.56
ALL: 64.71.25.210
ALL: 78.159.108.172
ALL: 194.153.254.66
[...]

```

---

### Post by brian_p on 2008-09-05
> **matey3 said:**
> 

# ALL: PARANOID
ALL:
79.187.241.62:,
82.50.250.22:,
82.179.130.135:,\


From hosts_access(5):

```
All other lines should satisfy the following format, things between [] being
optional:

daemon_list : client_list [ : shell_command ]
```

and

```
client_list is a list of one or more host names, host addresses, patterns 
or wildcards (see below) that will be matched against the client host name 
or address.
```

and

```
List elements should be separated by blanks and/or commas
```.

On one line:

```
ALL: 79.187.241.62,82.50.250.22,82.179.130.135
```

or

```
ALL: 79.187.241.62 82.50.250.22 82.179.130.135
```

Alternatively:

```
ALL: \
79.187.241.62,\
82.50.250.22,\
82.179.130.135
```

I'm uneasy about the lack of backslashes and the appearance of colons in your example.

```
sudo tcpdchk
```

---

### Post by Thingymebob on 2011-05-04
I know this is an old topic but incase anyone else comes acroos the same problem read the warning box around half way down the page: [http://www.centos.org/docs/5/html/5.1/Deployment_Guide/s1-tcpwrappers-access.html](http://www.centos.org/docs/5/html/5.1/Deployment_Guide/s1-tcpwrappers-access.html) (I couldn't find an equivalent in ubuntu doc).

You need to end the last line with a newline character e.g press enter otherwise the last command will fail.

The spacing around the colon doesn't appear important I have entries that are both foo : bar and foo: bar and foo:bar none of which fail. (Suppose I should clean it up really and make it consistent)

---

