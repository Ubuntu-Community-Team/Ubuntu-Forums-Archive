---
title: "How to listen for remote connections"
date: 2009-04-16
forum: Server Platforms
---

### Post by MaxMcByte on 2009-04-16
Hello Fellow Ubuntuites;

I have 2 Intrepid machines "A" and "B" on the same subnet on my LAN. 
I am running some connectivity tests and observed that my machines only listen for network connections after a user has logged in. I need the machines to listen for connections regardless of whether someone is logged in or not, like a server. If there is a power outage or some other event that causes a restart I would not be able to remotely log into the machine.

Example

Test 1;
I log onto A while B awaits a login.
From A, I ping B and get "Destination Host Unreachable".

Test 2;
I log onto A and B.
From A, I ping B and this successfully returns "64 bytes from galactic (192.168.99.4): icmp_seq=12 ttl=64 time=0.189 ms
".

Is there a flag that needs to be set in a "conf" file? What am I missing?

Thank You!

---

### Post by Yashiro on 2009-04-16
Are they using wireless net connections?

---

### Post by MaxMcByte on 2009-04-16
Hello Yashiro;

It is now working! Let me state the problem and solution just in case it helps others. After reading many posts this is what I discovered.

Cause;
Because I am using static IP I had to "unchecked" the "System Setting check-box" in the "NetworkManager Applet 0.7.0" because "checking" it would overwrite the "manual" entries that I placed in the "Address Settings" on the "IPv4 Setting Tab" upon restart. _Because I originally unchecked the System Setting check-box to fix the overwrite problem described above results in the network connection *** not *** being active until login_.

Solution;
I found the solution to my problem partially in another post "[Network manager forgets config after restart - 8.10]("http://ubuntuforums.org/archive/index.php/t-955415.html")".

To get the system to listen for remote connections without being logged in and still using the "NetworkManager Applet 0.7.0" you;

1. Change the connection name to something else. Example "eth0" instead of "auto eth0".

2. Enter network setting as required (Address, Netmask, Gateway, DNS Servers)

3. Tick "ON" the System Settings Checkbox. (Note; I had to check, uncheck, re-check it a few times before it stayed on.

4. Press the Accept button, Ubuntu will ask for you password. At this point you are good to go.

5. Reboot and you can ping, ssh remote, etc. into your machine.

Thanks for responding.

MaxMcByte...

---

### Post by Yashiro on 2009-04-16
Yeah if NM is managing your connections and you've not set them up manually then you wont get anything until someone logs in.

Always happens with wireless (nm). Will sometimes occur with wired if your interfaces file gets mucked about.

Glad you worked it out.

---

