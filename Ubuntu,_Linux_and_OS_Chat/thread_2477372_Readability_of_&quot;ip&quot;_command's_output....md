---
title: "Readability of &quot;ip&quot; command's output..."
date: 2022-07-22
forum: Ubuntu, Linux and OS Chat
---

### Post by rooker2 on 2022-07-22
Hello everyone :)

I'm really hoping I'm not stepping on anyone's toes here, and maybe I'm just getting older, but:
Am I the only one finding the output of the "ip" shell command way harder and less intuitive (or tutorialize/teachable)?
IMO, of course.

Here's a sample:


```
$ route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.138      0.0.0.0         UG    100    0        0 enx00e04c68021c
10.0.0.0        0.0.0.0         255.255.255.0   U     100    0        0 enx00e04c68021c
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enx00e04c68021c
```

Compared to:

```
$ ip route

default via 10.0.0.138 dev enx00e04c68021c proto dhcp metric 100 
10.0.0.0/24 dev enx00e04c68021c proto kernel scope link src 10.0.0.22 metric 100 
169.254.0.0/16 dev enx00e04c68021c scope link metric 1000 
```

To me this feels like going backwards in accessibility, by making CLI harder to interpret (by people)?
What is you opinion about this?
How do you deal with this in tutorials and the like?

** I'm seriously asking this, because I teach FOSS in workshops - and I experience that I have a harder time trying to introduce "how to use this information" in tutorials and classes. :) :cool:**

What bugs me most is that I cannot answer their questions, like:
> "So, why is it harder now than it was before?"


Thanks in advance for any input!

---

### Post by rooker2 on 2022-07-22
Oh! I forgot to mention:
> $ ifconfig
versus:
> $ ip a

Have you compared those yet? ;)
If anyone knows what the advantage (or reason) for this new-and-improved? output formatting?

Thanks!

---

### Post by jeremy31 on 2022-07-22
Moved to Ubuntu, Linux chat as this is not a tutorial and I don't really view it as a support question

---

### Post by DuckHook on 2022-07-22
I'm going on nothing but hearsay, so take what follows with a grain of salt. To my understanding, the new utilities are based on a more thorough inspection of the OS whereas the old utils were not and therefore were prone to more errors, sometimes of a subtle sort.

Frankly, many of the assertions by its proponents are so technical as to be beyond me, but [here's a brief explanation]("https://opensource.com/article/21/1/ifconfig-ip-linux"). You will want to focus on the section at the end: "Pros and cons of ip and ifconfig"

I agree though that a lot more can be done with ordering the output to be more human readable.

---

### Post by TheFu on 2022-07-23
Yep.  The newer commands suck for being human readable. Hopefully, they will make a -h switch that is useful, someday.

For now, use the 'column' command

```
ip route |column -t
```

It doesn't work great for all the possible ip options, unfortunately.

OTOH, the newer commands **are** more easily parsed by normal unix text tools like cut, paste, sed, and the 50 others.

---

### Post by him610 on 2022-07-24
Totally agree with the majority sentiment in the conversation. Here is what TheFu's commands require in columns:
> ip route |column -t
```
~$ ip route |column -t
default           via  10.0.0.1       dev    enp5s0  proto   dhcp  metric  100
default           via  192.168.100.1  dev    wlp4s0  proto   dhcp  metric  600
10.0.0.0/24       dev  enp5s0         proto  kernel  scope   link  src     10.0.0.190       metric  100
169.254.0.0/16    dev  wlp4s0         scope  link    metric  1000
192.168.100.0/24  dev  wlp4s0         proto  kernel  scope   link  src     192.168.100.111  metric  600

```
It took 104 columns to display all the information in orderly columns.
Now, here is what it takes in columns to display ***ip a |column -t***
```
ip a |column -t
1:             lo:                                       <LOOPBACK,UP,LOWER_UP>             mtu                65536          qdisc          noqueue        state          UNKNOWN  group  default  qlen  1000
link/loopback  00:00:00:00:00:00                         brd                                00:00:00:00:00:00
inet           127.0.0.1/8                               scope                              host               lo
valid_lft      forever                                   preferred_lft                      forever
inet6          ::1/128                                   scope                              host
valid_lft      forever                                   preferred_lft                      forever
2:             enp5s0:                                   <BROADCAST,MULTICAST,UP,LOWER_UP>  mtu                1500           qdisc          fq_codel       state          UP       group  default  qlen  1000
link/ether     a8:a1:59:08:1d:1e                         brd                                ff:ff:ff:ff:ff:ff
inet           10.0.0.190/24                             brd                                10.0.0.255         scope          global         dynamic        noprefixroute  enp5s0
valid_lft      121429sec                                 preferred_lft                      121429sec
inet6          2601:983:380:5400:a939:4d97:a42d:12d9/64  scope                              global             temporary      dynamic
valid_lft      215242sec                                 preferred_lft                      26085sec
inet6          2601:983:380:5400::8852/128               scope                              global             dynamic        noprefixroute
valid_lft      391418sec                                 preferred_lft                      391418sec
inet6          2601:983:380:5400:cfdf:1f29:936d:6d2a/64  scope                              global             temporary      deprecated     dynamic
valid_lft      215242sec                                 preferred_lft                      0sec
inet6          2601:983:380:5400:fa38:d3a1:d7b5:2e67/64  scope                              global             dynamic        mngtmpaddr     noprefixroute
valid_lft      215242sec                                 preferred_lft                      215242sec
inet6          fe80::4605:bcf2:f6b0:21ef/64              scope                              link               noprefixroute
valid_lft      forever                                   preferred_lft                      forever
3:             wlp4s0:                                   <BROADCAST,MULTICAST,UP,LOWER_UP>  mtu                1500           qdisc          noqueue        state          UP       group  default  qlen  1000
link/ether     c0:b8:83:b2:86:26                         brd                                ff:ff:ff:ff:ff:ff
inet           192.168.100.111/24                        brd                                192.168.100.255    scope          global         dynamic        noprefixroute  wlp4s0
valid_lft      49244sec                                  preferred_lft                      49244sec
inet6          fe80::2528:7cc6:dc03:e146/64              scope                              link               noprefixroute
valid_lft      forever                                   preferred_lft                      forever

```
Using ***ip a |column -t*** from the terminal requires 207 columns. How many folks have a monitor that can display 207 columns? I use a 29" monitor and stretching out the terminal window exceeds more than half the width of my monitor.
As one can see, there is much more information to be displayed with the newer commands. I was unaware of the pipe to columns routine - thanks TheFu. It is gratifying to learn something new.

---

