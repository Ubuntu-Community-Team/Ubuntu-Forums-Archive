---
title: "New to shell scripting, looking for creative methods for backup scripts"
date: 2009-08-16
forum: Server Platforms
---

### Post by nerr on 2009-08-16
Hi everyone, I'm working on a method right now of pulling data from Windows clients to an Ubuntu Server using CIFS.  I've created a script that does the job just fine, but there are a few small problems I would like to address.

Here's a basic stanza in the script:
```
#!/bin/sh:
currentdate=$(date +%m.%d.%y)
time=$(date +%H:%M:%S)

Nerr1="192.168.1.100"

 echo "$currentdate - $time: Beginning data pull from Nerr-1 ($Nerr1)." >> /home/nerr/sync.log
 mount -t cifs //$Nerr1/sync -o username=nerr,password=****** /mnt/sync
 rsync -avz --inplace --progress --del --chmod=a+rwx /mnt/sync/ /home/nerr/Nerr1/
 umount //$Nerr1/sync
 time=$(date +%H:%M:%S)
 echo "$currentdate - $time: Data pull from Nerr-1 ($Nerr1) complete." >> /home/nerr/sync.log
```This script works great.  It's incredibly fast, and really the only thing slowing it down is my network speed.  However, there is a catch.  At the moment, I must use an IP address instead of a hostname to access a share on a machine, and since this network uses DHCP, that could be a huge problem if the IP address of a machine suddenly changes and I don't update the script in time.

Here are my options as I see it:
1) Set static IPs for all clients (not preferrable, as some will roam to other networks and I don't want to have to keep switching between static and DHCP)
2) Find a method to resolve hostnames to IPs so I can enter a hostname instead, which will never require changing the script.
3) Possibly pull a DHCP client listing from my router (Linksys WRT350N, stock firmware) and use that information to set the IP addresses, and then run the script.  I doubt this is possible, but if it is, it may be worth a try.

Method 2 is probably the best solution, but I don't have a clue how to resolve Windows hostnames to IP addresses under Ubuntu Server.  If Samba or another utility can do this, let me know!  That'd be great.

I do have one more question though: Before the script hits a client, I'd like to ping that client to ensure the machine is powered on and online.  If the ping is successful, run backup routines.  If it fails, skip that machine, and log a message that said machine did not synchronize.  Is there a way to set this up?  Again, very new to shell scripting... but I'm learning. :)

Your advice is appreciated!  Thanks!

---

### Post by koenn on 2009-08-16
> **nerr said:**
> 

I do have one more question though: Before the script hits a client, I'd like to ping that client to ensure the machine is powered on and online.  If the ping is successful, run backup routines.  If it fails, skip that machine, and log a message that said machine did not synchronize.  Is there a way to set this up?  Again, very new to shell scripting... but I'm learning. :)

Your advice is appreciated!  Thanks!

```

if ping -c2  $SomeHost ; then 

      backup routine goes here ;
fi

```

cleaner : use a function

```


doBackup(){

  backup routine goes here ;
}


if ping -c2  $SomeHost ; then 
      doBackup ;
fi

```

---

### Post by koenn on 2009-08-16
> **nerr said:**
> 
Method 2 is probably the best solution, but I don't have a clue how to resolve Windows hostnames to IP addresses under Ubuntu Server.  If Samba or another utility can do this, let me know!  That'd be great.

I'm not sure if Samba can do WINS (netbios hostname resolution), but I'm sure you can find info about that on the samba website. 

the real easy solution is to run dnsmasq for dns+dhcp, so you can use dns to resolve addresses that were assigned by dhcp. 
since having 2 dhcp servers on your network will cause trouble, this means you'll have to disable the dhcp service on your router.

---

### Post by nerr on 2009-08-16
Thanks for the help, koenn!  I actually figured out a way to get around the WINS name lookup problem, and to use that to also verify that the machine is online.  Here's the new code.  It's not in a function yet as there are still quite a few variables that change from machine to machine, but this works great for now:

```
#!/bin/sh:
currentdate=$(date +%m.%d.%y)

Nerr1=$(nmblookup "Nerr-1" | grep 192.168.1.1 | cut -c 1-13)

# Nerr-1
echo "Nerr-1"
if [[ -n "$Nerr1" ]] ; then 
    time=$(date +%H:%M:%S)
    echo "$currentdate - $time: Beginning data pull from Nerr-1 ($Nerr1)." >> /var/www/status/Nerr-1.log
    mount -t cifs //$Nerr1/sync -o username=nerr,password=****** /mnt/sync
    rsync -avz --inplace --progress --del --chmod=a+rwx /mnt/sync/ /home/nerr/sync/Nerr-1/
    umount //$Nerr1/sync
    time=$(date +%H:%M:%S)
    echo "$currentdate - $time: Data pull from Nerr-1 ($Nerr1) complete." >> /var/www/status/Nerr-1.log
else
        time=$(date +%H:%M:%S)
        echo "$currentdate - $time: !! Nerr-1 is offline.  Skipping data pull." >> /var/www/status/Nerr-1.log
fi
```

Works like a charm!  If nmblookup returns a blank value for the IP, it skips the routine and makes an error in the log.  If it doesn't, the backup routine proceeds as planned.  I've been looking forward to the day when I got this working finally!  Thanks for your help!

---

### Post by koenn on 2009-08-16
yep, looks like you're getting there.

---

### Post by HermanAB on 2009-08-16
You can configure a DHCP server such that a particular machine will always get the same IP address.  Read the man page - not difficult.

---

### Post by nerr on 2009-08-16
But since my router already takes care of DHCP anyway, why make a change?  For the time being, this solution should do the trick!

---

