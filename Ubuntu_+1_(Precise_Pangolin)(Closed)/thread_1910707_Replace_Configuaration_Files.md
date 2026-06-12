---
title: "Replace Configuaration Files ??"
date: 2012-01-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2012-01-17
Sorry for the real bad pic.. it just popped up while doing an update with synaptic. It would not let me take a screenshot so I had to use my camera.

  It's asking me to either replace with a new network config or use the old one.

Any ideas?? berofre I proceed??

Edubuntu 12.04

---

### Post by hansum_rahul on 2012-01-17
the diff please!

---

### Post by ronacc on 2012-01-17
the only way to tell really is to lookat the diffs as hansum_rahul said , but with that said I usually choose to keep my existing config file since I am heavy into customizing and it really upsets me when an update ruins my work .

---

### Post by effenberg0x0 on 2012-01-17
Or just switch to a console and backup your current file to a safe location and only then accept changes / overwrite. If things go bad you can always replace the currently installed config file with your old config.  
sudo mkdir $HOME/backup
sudo cp /etc/init/network-interface-security.conf $HOME/backup/network-interface-security.conf.$(date +%d%m%y_%H:%M).backup

---

### Post by ventrical on 2012-01-17
> **effenberg0x0 said:**
> Or just switch to a console and backup your current file to a safe location and only then accept changes / overwrite. If things go bad you can always replace the currently installed config file with your old config.  
sudo mkdir $HOME/backup
sudo cp /etc/init/network-interface-security.conf $HOME/backup/network-interface-security.conf.$(date +%d%m%y_%H:%M).backup


I'll be back ..

---

### Post by ventrical on 2012-01-17
> **effenberg0x0 said:**
> Or just switch to a console and backup your current file to a safe location and only then accept changes / overwrite. If things go bad you can always replace the currently installed config file with your old config.  
sudo mkdir $HOME/backup
sudo cp /etc/init/network-interface-security.conf $HOME/backup/network-interface-security.conf.$(date +%d%m%y_%H:%M).backup


cp: cannot stat '/etc/init/network-interface-security.conf': No such file or directory

I put the code in there by hand , verbatim..

---

### Post by ventrical on 2012-01-17
> **hansum_rahul said:**
> the diff please!


 I tired to use the tool that came with the notice but nothing came up.

---

### Post by ventrical on 2012-01-17
> **ronacc said:**
> the only way to tell really is to lookat the diffs as hansum_rahul said , but with that said I usually choose to keep my existing config file since I am heavy into customizing and it really upsets me when an update ruins my work .

 At this stage of the game I took your step and decided to keep exisiting .conf file.  Man oh man I really chickened out .. but ya know .. this one particular install has been working so sweet -it's almost perfect- and I keep making the mistake of forgetting that I am working an alpha transition.

 So perhaps I can find the other file also....?

---

### Post by ventrical on 2012-01-17
Ok .. here is the proposed-

```
# network-interface-security - configure network device security
#
# This is a one-time start-up script to load AppArmor profiles needed
# before the network comes up.

description    "configure network device security"

# In order to avoid upstart bug LP: #447654, we cannot have an AND
# statement here (with the ORs).  An "and virtual-filesystems" is desired
# here to make sure that the securityfs is mounted, but since each of the
# ORed services already require virtual-filesystems be mounted, this is safe:
start on (starting network-interface
          or starting network-manager
          or starting networking)

# In order to handle the lack of upstart feature LP: #568860, we need to
# run multiple times, for each of the above "starting" service instances, or
# else another one might run while we're running, and not wait for us to
# finish.
instance $JOB${INTERFACE:+/}${INTERFACE:-}

# Since we need these profiles to be loaded before any of the above services
# begin running, this service must be a pre-start so that its pre-start
# script finishes before the above services' start scripts begin.
pre-start script
    [ -f /run/network-interface-security ] && exit 0 # already ran
    [ -d /rofs/etc/apparmor.d ]  && exit 0 # do not load on liveCD
    [ -d /sys/module/apparmor ]  || exit 0 # do not load without AppArmor
    [ -x /sbin/apparmor_parser ] || exit 0 # do not load without parser
    for link in /etc/apparmor/init/network-interface-security/* ; do
        [ -L $link ] && /sbin/apparmor_parser -r -W $link || true
    done
    > /run/network-interface-security
end script
```

Here is the current:

```
# network-interface - configure network device
#
# This service causes network devices to be brought up or down as a result
# of hardware being added or removed, including that which isn't ordinarily
# removable.

description    "configure network device"

emits net-device-up
emits net-device-down
emits static-network-up

start on net-device-added
stop on net-device-removed INTERFACE=$INTERFACE

instance $INTERFACE
export INTERFACE

pre-start script
    if [ "$INTERFACE" = lo ]; then
    # bring this up even if /etc/network/interfaces is broken
    ifconfig lo 127.0.0.1 up || true
    initctl emit -n net-device-up \
        IFACE=lo LOGICAL=lo ADDRFAM=inet METHOD=loopback || true
    fi
    mkdir -p /run/network
    exec ifup --allow auto $INTERFACE
end script

post-stop exec ifdown --allow auto $INTERFACE
```

---

### Post by ventrical on 2012-01-17
Thanks a million you guys . :)

---

### Post by ventrical on 2012-01-17
> **hansum_rahul said:**
> the diff please!

There was no way I could get that tool to work ..

[http://www.youtube.com/watch?v=oHRFbjEOti8](http://www.youtube.com/watch?v=oHRFbjEOti8)

---

### Post by cariboo on 2012-01-17
In a terminal, try:

```
diff old_file new_file
```

although from your listing, it's pretty easy to see the difference in the two files.

---

