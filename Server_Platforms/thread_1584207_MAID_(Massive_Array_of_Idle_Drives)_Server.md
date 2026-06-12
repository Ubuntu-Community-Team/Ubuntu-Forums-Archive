---
title: "MAID (Massive Array of Idle Drives) Server?"
date: 2010-09-28
forum: Server Platforms
---

### Post by WolfyEB on 2010-09-28
Is there any kind of MAID (Massive Array of Idle Drives) Server systems that can be deployed using ubuntu? I have a large library of stock HD video that I'd like to not have to power up and down my file server to access.

---

### Post by CharlesA on 2010-09-28
I guess you will have to explain why you are taking down the file server. I've been running a RAID array on my file server since day 1 and it's not failed me. Granted, my array is only 4TB, but I've not even used half of that.

Do you want to consolidate everything, or what exactly do you want to accomplish?

---

### Post by WolfyEB on 2010-09-28
I have a 48 Terabyte system that consumes about 2000 watts and it's in my house. I really don't want to pay for the electricity bills on that :wink:

---

### Post by CharlesA on 2010-09-28
> **WolfyEB said:**
> I have a 48 Terabyte system that consumes about 2000 watts and it's in my house. I really don't want to pay for the electricity bills on that :wink:

Good lord. For something that large, I don't know what you'd do tbh.

---

### Post by WolfyEB on 2010-09-28
Ya :-\ I'm a digital Pack Rat. hehe. 

I've herd of MAIDs but theres no documentation on them except a wikipedia article. I could probably kill most of that wattage if I could get my hard drives to spin down when i'm not using them.

---

### Post by CharlesA on 2010-09-28
Take a look at [hdparm]("http://www.debianadmin.com/tune-your-hard-disk-for-high-performance-using-hdparm.html") for some info on how to see if the drives will spin down when not in use.

---

### Post by arrrghhh on 2010-09-28
I've been hashing hdparm with an individual on another forum, but I haven't had a good answer...

Doesn't Ubuntu use this by default...?  I mean, doesn't Ubuntu spin down my disks when they're not in use anyways...?

Oh, dude.  What kind of a rig do you have 48tb in?  Do you have a freakin data center rack in your basement?  I so want one (mainly for a lab environment, among other things...), I have a feeling the girlfriend would kill me LOL!

---

### Post by jbrown96 on 2010-09-29
I have a four disk array and use the following to keep my disks spun down aggressively.

In /etc/rc.local:
```
hdparm -B 10 /dev/sd{a,b,d,e}
```

I'm not even sure how disks are named after /dev/sda--/dev/sdz. If you can give me a schema, this will be better
```
for i in {a..z}; do 
hdparm -B 10 /dev/sd$i
done
```
That will give you the first 26 devices.

Note that not all drives support spin-down.

---

### Post by djurny on 2010-09-29
if you're talking about automatic spindown of harddisks; usually all drives support spindown (standby/sleep) after a configurable timeout.. advanced power management is one that not all drives support.. i wrote the following `/etc/init.d/hdparm' replacement to configure all drives in my server (with detectable filesystems on them) to disable advanced pm and just use sensible spindown timeouts and acoustic settings.. hth!


```
#!/bin/bash

shopt -s extglob

ME="${0}"

OPT_NOACT=1

RET=0



loginfo() {
        echo "$*"
        logger -t "${ME}" -p user.info "$*"
}

logerror() {
        echo "$*" 1>&2
        logger -t "${ME}" -p user.error "$*"
}

maybe() {
        if [[ "${OPT_NOACT}" -ne 0 ]]
        then
                eval $@
        else
                echo "# $@"
        fi
}

get_aam_apm()
{
        /sbin/hdparm -iI ${1:?} 2>/dev/null | awk '
                BEGIN {
                        aam = 128       # quiet
                        apm = 255       # off

                        set_aam = 0
                        set_apm = 0
                }

                /AdvancedPM=[Yy][Ee][Ss]/ {
                        set_apm = 1
                }

                /^[ \t]+Recommended acoustic management value:[ \t]+.*$/ {
                        sub(/^[ \t]+Recommended acoustic management value:[ \t]+/, "")
                        aam_recommended = $1

                        sub(/[0-9]+, current value:[ \t]+/, "")
                        aam_current = $1

                        if (aam_current != aam_recommended) {
                                set_aam = 1
                                aam = aam_recommended
                        }
                }

                END {
                        if (set_apm) {
                                printf("APM=%d\n", apm)
                        }
                        if (set_aam) {
                                printf("AAM=%d\n", aam)
                        }
                }'
}

##

if [ `id -u` -ne 0 ]
then
        logerror "need root priviliges"
        exit 1
fi

while getopts "n" OPT
do
        case "${OPT}" in
        n)      OPT_NOACT=0
                ;;
        esac
done
shift $(( ${OPTIND} - 1 ))

##

DEV=""
DEVS=`awk '$4 ~ /^sd[a-z]+$/ { print $4 }' /proc/partitions | sort -u`

case "${1}" in
thaw|resume|start|restart|reload|force-reload)
        for DEV in ${DEVS}
        do
                unset AAM
                unset APM
                SPINDOWN="242"

                eval $(get_aam_apm "/dev/${DEV}")

                loginfo "setting hd parameters for \`${DEV}'"
                maybe /sbin/hdparm      ${AAM:+-qM}             ${AAM}          \
                                        ${APM:+-qB}             ${APM}          \
                                        ${SPINDOWN:+-qS}        ${SPINDOWN}     \
                                        /dev/${DEV}
        done
        ;;

hibernate|suspend|stop)
        for DEV in ${DEVS}
        do
                loginfo "putting \`${DEV}' to sleep"
                maybe /sbin/hdparm -Y /dev/${DEV}
        done
        ;;

*)
        loginfo "need something to do"
        exit 22
        ;;
esac

test ${RET} -eq 0

# EOF

```

---

### Post by BkkBonanza on 2010-09-29
> **WolfyEB said:**
> I have a 48 Terabyte system that consumes about 2000 watts and it's in my house. I really don't want to pay for the electricity bills on that :wink:

Ha ha. Sure let others pay the bill to archive your files. Makes sense if you can find willing participants. I read once about such a scheme but can't recall the name now. I'm sure Google would turn up something though.

Ideally you'd use some form of distributed file system where each user is a sharing member that benefits from joining and sharing their space all together. 

Hmmm. 2000 Watts @ 0.10/KwH = 0.20 x 24 x 30 = $144/mo. 

On Amazon S3 you'd pay 0.10 x 48000 = $4800/mo. (reduced redundancy mode).

So if you were to charge for your MAID array you could make money.

This may interest you: [GlusterFS]("http://www.gluster.com/community/documentation/index.php/Main_Page"). Surprisingly, it's actually in the Ubuntu repos!

---

