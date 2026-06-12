---
title: "UBUNTU 15.10 RKHUNTER WARNING /usr/sbin/prelink"
date: 2015-11-17
forum: Server Platforms
---

### Post by rhandy2 on 2015-11-17
I dont understand warning

I have 2 ubuntu servers and file is equal

Rkhunter LOG

 ```
Warning: The command '/usr/sbin/prelink' has been replaced by a script: /usr/sbin/prelink: Bourne-Again shell script, ASCII text executable



```


File /usr/sbin/prelink

```


#!/bin/bash
#
# Prelink wrapper script
# Author: Andres Roldan <aroldan@debian.org>


# Needed to avoid annoying message in coreutils >= 6.0
export LC_ALL='C'


# Recommended minimun free space, 50MB
min_size=50000


will_prelink="$(for i in $(awk '! /#/ && ! /^-b/ && NF >= 1 {print $NF}' < /etc/prelink.conf); do test -e "$i"$
have_warn=0


df -P $will_prelink | sort | uniq | {
    have_warn=0
    while read part x x size x mount_point; do
        if $(echo $part | grep -qv "^/"); then
            continue;
        fi


        if [ $size -le "$min_size" ]; then
            echo "Partition $part ($mount_point) has only $size KB free." >&2
            have_warn=1
        fi
    done


    exit $have_warn     # Exit from piped subshell
}


if [ "$?" -eq "1" ]; then
    answer="No"
    if [ -t 1 ]; then
        echo
            echo "!! WARNING !!"
            echo "It's recommended to have at least $min_size KB of disk space."
            echo "Prelink would _really_ damage the ELF files on those partitions."
            read -t 20 -p "Do you really want to run prelink? (yes/No): " answer
    fi


    if [ "$answer" = "yes" ]; then
        echo "You were warned. Running prelink..."
        exec /usr/sbin/prelink.bin "$@"
    else
        echo
        echo "Aborting prelink."
        exit 1
    fi
fi >&2


exec /usr/sbin/prelink.bin "$@"



```

---

### Post by Habitual on 2015-11-17
Is this Warning 'new'?
When was the last time you ran rkhunter?

What version of rkhunter and where was it installed 'from'?

Visually they may seem the same, but verify using technique shown in [http://ubuntuforums.org/showthread.php?t=2281658&p=13300452#post13300452](http://ubuntuforums.org/showthread.php?t=2281658&p=13300452#post13300452)

eg: ```
dpkg -S /path/to/file
```

---

### Post by rhandy2 on 2015-11-17
First importante thing

I upgrade ubuntu 14.04 to 15.10

rkhunter log with 150 suspect files

```
[[05:00:21]          Current inode: 2105236    Stored inode: 2112405
[05:00:21]          Current size: 97496    Stored size: 97464
[05:00:21]          Current file modification time: 1431947512 (18-Mai-2015 12:11:52)
[05:00:21]          Stored file modification time : 1420477560 (05-Jan-2015 17:06:00)
[05:00:21]   /usr/bin/telnet.netkit                          [ Warning ]
[05:00:21] Warning: The file properties have changed:
[05:00:21]          File: /usr/bin/telnet.netkit
[05:00:21]          Current hash: d3379c3587823675a2324fefe702c25f52776bc47cab73d7c128e82426887583
[05:00:21]          Stored hash : 3affc6bba107c7e36928687ef0616c36dd836c2b
[05:00:21]          Current inode: 2105176    Stored inode: 2106575
[05:00:21]          Current size: 99840    Stored size: 95424
[05:00:21]          Current file modification time: 1430918699 (06-Mai-2015 14:24:59)
[05:00:21]          Stored file modification time : 1349221219 (03-Out-2012 00:40:19)
[05:00:21]   /usr/bin/w.procps                               [ Warning ]
[05:00:21] Warning: The file properties have changed:
[05:00:21]          File: /usr/bin/w.procps
[05:00:21]          Current hash: 4acf846dd7c29c028a9453804b98483778390053011c132d7dec96e07d9149be
[05:00:21]          Stored hash : 99ce1984236d32783d579e73a4a8e81fa8380816
[05:00:21]          Current inode: 2104936    Stored inode: 2098878
[05:00:21]          Current file modification time: 1423596214 (10-Fev-2015 19:23:34)
[05:00:21]          Stored file modification time : 1423598898 (10-Fev-2015 20:08:18)
[05:00:22]   /bin/bash                                       [ Warning ]
[05:00:22] Warning: The file properties have changed:
[05:00:22]          File: /bin/bash
[05:00:22]          Current hash: 2b607f16148bcd2c95cc1069df4ca6c0ac60f1c049451f6d323c0b0b657f9206
[05:00:22]          Stored hash : 8e3aa19fdc42e87659746f6dc8ea3af74ab30362
[05:00:22]          Current inode: 655367    Stored inode: 655411
[05:00:22]          Current size: 1037464    Stored size: 1021112
[05:00:22]          Current file modification time: 1441063678 (01-Set-2015 00:27:58)
[05:00:22]          Stored file modification time : 1412709732 (07-Out-2014 20:22:12)
[05:00:22]   /bin/cat                                        [ Warning ]
[05:00:22] Warning: The file properties have changed:
[05:00:22]          File: /bin/cat
[05:00:22]          Current hash: 8d6da6a751b66c3cdfebb56cc89a72b9a64a42f4c4e7dc8e198698bba280008a
[05:00:22]          Stored hash : 9f07abe7be504bfdac9cc43561042b27f06a550c
[05:00:22]          Current inode: 655520    Stored inode: 655481
[05:00:22]          Current size: 52000    Stored size: 47904
[05:00:22]          Current file modification time: 1444864248 (15-Out-2015 00:10:48)
[05:00:22]          Stored file modification time : 1421207414 (14-Jan-2015 03:50:14)
[05:00:22]   /bin/chmod                                      [ Warning ]
[05:00:22] Warning: The file properties have changed:
[05:00:22]          File: /bin/chmod
[05:00:22]          Current hash: 28be01cf30115c49d511f92161455538c4fd44775e46a390ea8cce4eeb7ec63b
[05:00:22]          Stored hash : 3a6c66415f7a5361007beeaa67fb9ab29a2aae65
[05:00:22]          Current inode: 655518    Stored inode: 655489
[05:00:22]          Current file modification time: 1444864248 (15-Out-2015 00:10:48)
[05:00:22]          Stored file modification time : 1421207414 (14-Jan-2015 03:50:14)
[05:00:22]   /bin/chown                                      [ Warning ]
[05:00:22] Warning: The file properties have changed:
[05:00:22]          File: /bin/chown
[05:00:22]          Current hash: b2c06da3a417737602d9b486c6c3105ac52c8f9c0e019b58c7297bd7e266db91
[05:00:22]          Stored hash : efcaf2c8ff9b3939999f4487d3111131f658b0cb
[05:00:22]          Current inode: 655477    Stored inode: 655487
[05:00:22]          Current size: 64256    Stored size: 60160
[05:00:22]          Current file modification time: 1444864248 (15-Out-2015 00:10:48)
[05:00:22]          Stored file modification time : 1421207414 (14-Jan-2015 03:50:14)
[05:00:22]   /bin/cp                                         [ Warning ]
[05:00:22] Warning: The file properties have changed:
[05:00:22]          File: /bin/cp
[05:00:22]          Current hash: 43ee5f18dd9cdaff7c5ab8842cd6341c0e29be905b8195f24c9b069cc49ac196
[05:00:22]          Stored hash : 6acfc035a53057049db65e92e561dd8a76740ea3
[05:00:22]          Current inode: 655527    Stored inode: 655444
[05:00:22]          Current size: 150912    Stored size: 130304
[05:00:22]          Current file modification time: 1444864248 (15-Out-2015 00:10:48)
[05:00:22]          Stored file modification time : 1421207414 (14-Jan-2015 03:50:14)
[05:00:23]   /bin/date                                       [ Warning ]
[05:00:23] Warning: The file properties have changed:
[05:00:23]          File: /bin/date
[05:00:23]          Current hash: 6127e7afa1338ff0f031a31c5b8282b3515fe35a94ec9ab83bf7026a410ddec2
[05:00:23]          Stored hash : 51ea2eda16d34feda2f85a5873d10658f4943b82
[05:00:23]          Current inode: 655516    Stored inode: 655485
[05:00:23]          Current size: 64256    Stored size: 60160
[05:00:23]          Current file modification time: 1444864248 (15-Out-2015 00:10:48)
[05:00:23]          Stored file modification time : 1421207414 (14-Jan-2015 03:50:14)
[05:00:23]   /bin/df                                         [ Warning ]
[05:00:23] Warning: The file properties have changed:
[05:00:23]          File: /bin/df
[05:00:23]          Current hash: a421040f5aa9236a92148b98edc6b62e5ccae197aa788f488990f68509132151
[05:00:23]          Stored hash : 8c09be9654ea24f3a02b9ce71e3c4b518f6aeb2b
[05:00:23]          Current inode: 655533    Stored inode: 655490
[05:00:23]          Current size: 101928    Stored size: 97736
[05:00:23]          Current file modification time: 1444864248 (15-Out-2015 00:10:48)
[05:00:23]          Stored file modification time : 1421207414 (14-Jan-2015 03:50:14)
[05:00:23]   /bin/dmesg                                      [ Warning ]
[05:00:23] Warning: The file properties have changed:
[05:00:23]          File: /bin/dmesg
[05:00:23]          Current hash: 338db6578e6129ecc9e9ca4bd4641cab88bc8ae528a3a238b7f4d422ea2a6a91
[05:00:23]          Stored hash : c85152d3485b96b930965514e67f4dc7ae6d2300
[05:00:23]          Current inode: 655442    Stored inode: 655445
[05:00:23]          Current size: 56448    Stored size: 22896
[05:00:23]          Current file modification time: 1438739354 (05-Ago-2015 02:49:14)
[05:00:23]          Stored file modification time : 1438741218 (05-Ago-2015 03:20:18)
[05:00:23]   /bin/echo                                       [ Warning ]
[05:00:23] Warning: The file properties have changed:
[05:00:23]          File: /bin/echo
[05:00:23]          Current hash: 44c212c3828eb931b4b45d2ac672fd49dcd4b7ee50f52e8460f473c3c2758d87
[05:00:23]          Stored hash : b817ab5a96514751e620bf7cb2cc84a38fcfab2b
[05:00:23]          Current inode: 655528    Stored inode: 655488
[05:00:23]          Current size: 31264    Stored size: 31296
[05:00:23]          Current file modification time: 1444864248 (15-Out-2015 00:10:48)
[05:00:23]          Stored file modification time : 1421207414 (14-Jan-2015 03:50:14)
[05:00:24]   /bin/ed                                         [ Warning ]
[05:00:24] Warning: The file properties have changed:
[05:00:24]          File: /bin/ed
[05:00:24]          Current hash: c00c78fa172ac82d126ae0df152a2b72f252e7c5d19f14d592af0d39fea9f20b
[05:00:24]          Stored hash : 84267f122a106e6bc5a8823cf6b39d3586409bc3
[05:00:24]          Current inode: 655434    Stored inode: 655469
[05:00:24]          Current size: 51512    Stored size: 47712
[05:00:24]          Current file modification time: 1398497645 (26-Abr-2014 08:34:05)
[05:00:24]          Stored file modification time : 1374017142 (17-Jul-2013 00:25:42)
[05:00:24]   /bin/egrep                                      [ Warning ]
[05:00:24] Warning: The file properties have changed:
[05:00:24]          File: /bin/egrep
[05:00:24]          Current hash: 3c4178db943e4e8e667e32d9ac5992110f17dffdc0dfd3863d6184d693be2376
[05:00:24]          Stored hash : 25ff1d25e7e7e6b9be6cd07c53b98213c3b142a2
[05:00:24]          Current inode: 655369    Stored inode: 655373
[05:00:24]          Current size: 29    Stored size: 183696
[05:00:24]          Current file modification time: 1435878726 (03-Jul-2015 00:12:06)
[05:00:24]          Stored file modification time : 1390065148 (18-Jan-2014 17:12:28)
[05:00:24] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[05:00:24]   /bin/fgrep                                      [ Warning ]
[05:00:24] Warning: The file properties have changed:
[05:00:24]          File: /bin/fgrep
[05:00:24]          Current hash: f364bd304ababe3b2dd9149fbbf816fdf6e55c093ca3b1121859dd934e5dde2c
[05:00:24]          Stored hash : 59bb67e545ac1951ac0f274ff63e8d2cc78ef420
[05:00:24]          Current inode: 655479    Stored inode: 655374
[05:00:24]          Current size: 29    Stored size: 138352
[05:00:24]          Current file modification time: 1435878726 (03-Jul-2015 00:12:06)
[05:00:24]          Stored file modification time : 1390065148 (18-Jan-2014 17:12:28)
[05:00:24] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[05:00:24]   /bin/fuser                                      [ Warning ]
[05:00:24] Warning: The file properties have changed:
[05:00:24]          File: /bin/fuser
[05:00:24]          Current hash: 9c7eb7b89bbff88a1ba80b4f068c5eba00436407c8f4494aa851de9934ec0b29
[05:00:24]          Stored hash : 2b670e0df6725984aaa5ef17a356d0e47576dc0d
[05:00:24]          Current inode: 655406    Stored inode: 655506
[05:00:24]          Current size: 35992    Stored size: 31864
[05:00:24]          Current file modification time: 1417625913 (03-Dez-2014 16:58:33)
[05:00:24]          Stored file modification time : 1354203168 (29-Nov-2012 15:32:48)
[05:00:24]   /bin/grep                                       [ Warning ]
[05:00:24] Warning: The file properties have changed:
[05:00:24]          File: /bin/grep
[05:00:24]          Current hash: 5be890e64503dc898b9406378b95bb7d3487f1bfebb458ee49502e486e5fc921
[05:00:24]          Stored hash : d39d8732dd68c6167aba7ff8f126db377b509c73
[05:00:25]          Current inode: 655368    Stored inode: 655372
[05:00:25]          Current size: 207128    Stored size: 191952
[05:00:25]          Current file modification time: 1435878728 (03-Jul-2015 00:12:08)
[05:00:25]          Stored file modification time : 1390065148 (18-Jan-2014 17:12:28)
[05:00:25]   /bin/ip                                         [ Warning ]
[05:00:25] Warning: The file properties have changed:
[05:00:25]          File: /bin/ip
[05:00:25]          Current hash: d1a0a23a3a2686957237b350516569184af7d5a494b6b4443510fa1ae4784891
[05:00:25]          Stored hash : 2875b9b1d9ddbe144d64163ce0d7a2b0ad3b7f17
[05:00:25]          Current inode: 655411    Stored inode: 655400
[05:00:25]          Current size: 363680    Stored size: 307328
[05:00:25]          Current file modification time: 1439979807 (19-Ago-2015 11:23:27)
[05:00:25]          Stored file modification time : 1437668373 (23-Jul-2015 17:19:33)
[05:00:25]   /bin/kill                                       [ Warning ]
[05:00:25] Warning: The file properties have changed:
[05:00:25]          File: /bin/kill
[05:00:25]          Current hash: b566730c421725ab09f29ae8cdcda7aa83295fdb24d9bb246bae7f8ec7fdff5a
[05:00:25]          Stored hash : 610f93901a5eacbacc63f23cdf500ca97807589a
[05:00:25]          Current inode: 655431    Stored inode: 655365
[05:00:25]          Current file modification time: 1423596214 (10-Fev-2015 19:23:34)
[05:00:25]          Stored file modification time : 1423598898 (10-Fev-2015 20:08:18)
[05:00:25]   /bin/less                                       [ Warning ]
[05:00:25] Warning: The file properties have changed:
[05:00:25]          File: /bin/less
[05:00:25]          Current hash: 9d5de353eac7bbb6266e84b0ad7766216a6e65e6538a36360a0ea00d2287e054
[05:00:25]          Stored hash : c0ddf750a49a96e69173c772747ffd4467fa5d89
[05:00:25]          Current inode: 655396    Stored inode: 655440
[05:00:25]          Current size: 173624    Stored size: 153664
[05:00:25]          Current file modification time: 1414142062 (24-Out-2014 10:14:22)
[05:00:25]          Stored file modification time : 1370855898 (10-Jun-2013 10:18:18)
[05:00:25]   /bin/login                                      [ Warning ]
[05:00:26] Warning: The file properties have changed:
[05:00:26]          File: /bin/login
[05:00:26]          Current hash: cf692e9dbea54d1228ce9ec890ecb6d3c86e540b0100c0dcdf33895cd37901d9
[05:00:26]          Stored hash : 49e788bcc6e4a43d1bcec7e896524b2ad74f63dd
[05:00:26]          Current inode: 655379    Stored inode: 655394
[05:00:26]          Current size: 49232    Stored size: 49136
[05:00:26]          Current file modification time: 1437457457 (21-Jul-2015 06:44:17)
[05:00:26]          Stored file modification time : 1436988598 (15-Jul-2015 20:29:58)
[05:00:26]   /bin/ls                                         [ Warning ]
[05:00:26] Warning: The file properties have changed:
[05:00:26]          File: /bin/ls
[05:00:26]          Current hash: 0b786b336b0391b56dabb7b078a23ec4295115628cfd4b635f4d8ae5ae0cfafc
[05:00:26]          Stored hash : c664bf0df003af91573a57128ce022efbaae6e0d
[05:00:26]          Current inode: 655511    Stored inode: 655486
[05:00:26]          Current size: 118272    Stored size: 110080
[05:00:26]          Current file modification time: 1444864248 (15-Out-2015 00:10:48)
[05:00:26]          Stored file modification time : 1421207414 (14-Jan-2015 03:50:14)
[05:00:26]   /bin/lsmod                                      [ Warning ]
[05:00:26] Warning: The file properties have changed:
[05:00:26]          File: /bin/lsmod
[05:00:26]          Current hash: d5e40d5b77530f3053e7539f4704da5f38f52d79d3857070fc6a6c82fa0d4a3c
[05:00:26]          Stored hash : 7ed11bba8ef27b8fe8617f5446142a3a0613cc41
[05:00:26]          Current inode: 655426    Stored inode: 655397
[05:00:26]          Current file modification time: 1440083451 (20-Ago-2015 16:10:51)
[05:00:26]          Stored file modification time : 1397138876 (10-Abr-2014 15:07:56)
[05:00:26]   /bin/mktemp                                     [ Warning ]
[05:00:26] Warning: The file properties have changed:
[05:00:26]          File: /bin/mktemp
[05:00:26]          Current hash: cab2a03368627e01d9f5c7aba32b42a0657321b306a8133a4de4cfd68eda7976
[05:00:26]          Stored hash : 20d4cf4fc5488d852ccf2393d23344ce6029379d
[05:00:26]          Current inode: 655519    Stored inode: 655494
[05:00:26]          Current size: 39616    Stored size: 39648
[05:00:26]          Current file modification time: 1444864248 (15-Out-2015 00:10:48)
[05:00:26]          Stored file modification time : 1421207414 (14-Jan-2015 03:50:14)
[05:00:26]   /bin/more                                       [ Warning ]
[05:00:26] Warning: The file properties have changed:
[05:00:26]          File: /bin/more
[05:00:26]          Current hash: f52b8e3f464873032cc2e393fa2fa5d4f678fe17eb89b1398adebb7f826f91ff
[05:00:26]          Stored hash : 971e74ed5b8217f6ac78c284df189785469a6841
[05:00:26]          Current inode: 655448    Stored inode: 655510
[05:00:26]          Current size: 39704    Stored size: 39600
[05:00:27]          Current file modification time: 1438739354 (05-Ago-2015 02:49:14)
[05:00:27]          Stored file modification time : 1438741218 (05-Ago-2015 03:20:18)
[05:00:27]   /bin/mount                                      [ Warning ]
[05:00:27] Warning: The file properties have changed:
[05:00:27]          File: /bin/mount
[05:00:27]          Current hash: 37165d647b40243d219b947c060b3cecb91d8a8bb529afb7c8fdf5b00abffdef
[05:00:27]          Stored hash : 3fa9e29880eca775597a1e793ad224defcbcf903
[05:00:27]          Current inode: 655401    Stored inode: 655399
[05:00:27]          Current size: 40088    Stored size: 94792
[05:00:27]          Current file modification time: 1438739354 (05-Ago-2015 02:49:14)
[05:00:27]          Stored file modification time : 1438741218 (05-Ago-2015 03:20:18)
[05:00:27]   /bin/mv                                         [ Warning ]
[05:00:27] Warning: The file properties have changed:
[05:00:27]          File: /bin/mv
[05:00:27]          Current hash: 7457f616b3eab7910f7ed006e4f7145442a9d8e24126247556e8180222ff8d62
[05:00:27]          Stored hash : 7d937c607f0381ff672d63b1f3496b88724636c5
[05:00:27]          Current inode: 655526    Stored inode: 655504
[05:00:27]          Current size: 130376    Stored size: 122088
[05:00:27]          Current file modification time: 1444864248 (15-Out-2015 00:10:48)
[05:00:27]          Stored file modification time : 1421207414 (14-Jan-2015 03:50:14)
[05:00:27]   /bin/netstat                                    [ Warning ]
[05:00:27] Warning: The file properties have changed:
[05:00:27]          File: /bin/netstat
[05:00:27]          Current hash: b013c213d8c408e72d4bebcb471c9ed2a76f976c6c2ff5c90b396332928b78f1
[05:00:27]          Stored hash : 6cc63622c6476ec2412995b7e05c7aedff86812d
[05:00:27]          Current inode: 655393    Stored inode: 655415
[05:00:27]          Current file modification time: 1404134364 (30-Jun-2014 14:19:24)
[05:00:27]          Stored file modification time : 1407253475 (05-Ago-2014 16:44:35)
[05:00:27]   /bin/ping                                       [ Warning ]
[05:00:27] Warning: The file properties have changed:
[05:00:27]          File: /bin/ping
[05:00:27]          Current hash: 5249815d2afc2011df86ad95cb2990e4f225990c37372d5e0d6019085df7dee6
[05:00:27]          Stored hash : 2e19e3667a617f9381357e580f935ee783a98025
[05:00:27]          Current inode: 655416    Stored inode: 655404
[05:00:27]          Current file modification time: 1399491947 (07-Mai-2014 20:45:47)
[05:00:27]          Stored file modification time : 1399499506 (07-Mai-2014 22:51:46)
[05:00:28]   /bin/ps                                         [ Warning ]
[05:00:28] Warning: The file properties have changed:
[05:00:28]          File: /bin/ps
[05:00:28]          Current hash: 7ba7fbc891e831b58e3267d74237a06dd9701501c36515dff74153b9b2a64a92
[05:00:28]          Stored hash : ad5c532e715ab56b8d4fe6692b717150999e3bf8
[05:00:28]          Current inode: 655430    Stored inode: 655364
[05:00:28]          Current file modification time: 1423596214 (10-Fev-2015 19:23:34)
[05:00:28]          Stored file modification time : 1423598898 (10-Fev-2015 20:08:18)
[05:00:28]   /bin/pwd                                        [ Warning ]
[05:00:28] Warning: The file properties have changed:
[05:00:28]          File: /bin/pwd
[05:00:28]          Current hash: 8ad543e044f77020f4a8aeed95cd91a1bed4c759cc14cb1a517041ee8a6b0bc4
[05:00:28]          Stored hash : 9773d99aece91cda6b4a0d7d63fc9fb58f7de516
[05:00:28]          Current inode: 655515    Stored inode: 655501
[05:00:28]          Current size: 31360    Stored size: 31392
[05:00:28]          Current file modification time: 1444864248 (15-Out-2015 00:10:48)
[05:00:28]          Stored file modification time : 1421207414 (14-Jan-2015 03:50:14)
[05:00:28]   /bin/readlink                                   [ Warning ]
[05:00:28] Warning: The file properties have changed:
[05:00:28]          File: /bin/readlink
[05:00:28]          Current hash: 61359b5a4dfa37408032b8903e80110c0ee163b3f563c770a7031c6a9f22066f
[05:00:28]          Stored hash : ddf8b5f10f0eeb14187d2724d9a7304710d0a981
[05:00:28]          Current inode: 655529    Stored inode: 655491
[05:00:28]          Current file modification time: 1444864248 (15-Out-2015 00:10:48)
[05:00:28]          Stored file modification time : 1421207414 (14-Jan-2015 03:50:14)
[05:00:28]   /bin/sed                                        [ Warning ]
[05:00:28] Warning: The file properties have changed:
[05:00:28]          File: /bin/sed
[05:00:28]          Current hash: e80ef105ffd7e023f685a6480e8cc72c60b0528ed3a9abe0ad74976669c9e265
[05:00:28]          Stored hash : 1892c906fc5208a501f934d61fbd2e5ad9ab2fe0
[05:00:28]          Current inode: 655381    Stored inode: 655407
[05:00:28]          Current size: 73416    Stored size: 73352
[05:00:28]          Current file modification time: 1436406666 (09-Jul-2015 02:51:06)
[05:00:28]          Stored file modification time : 1392291482 (13-Fev-2014 11:38:02)
[05:00:28]   /bin/sh                                         [ Warning ]
[05:00:28] Warning: The file properties have changed:
[05:00:28]          File: /bin/sh
[05:00:28]          Current hash: e865a4ff01b0df1afec7b5fd7b3a8906baa57d77daaa4888a31dccbf004d011b
[05:00:28]          Stored hash : 647437c3d7543c7c8d381903834c9ef42eb4cf69
[05:00:29]          Current inode: 655444    Stored inode: 655369
[05:00:29]          Current file modification time: 1433418977 (04-Jun-2015 12:56:17)
[05:00:29]          Stored file modification time : 1392812032 (19-Fev-2014 12:13:52)
[05:00:29]   /bin/su                                         [ Warning ]
[05:00:29] Warning: The file properties have changed:
[05:00:29]          File: /bin/su
[05:00:29]          Current hash: bf143b29fbd67da0feb885a328d243bfc3c31c861ff71d74dab0608e41080007
[05:00:29]          Stored hash : 362df39a58c6d22c6ae8f920dbba1b1c6433d98f
[05:00:29]          Current inode: 655377    Stored inode: 655478
[05:00:29]          Current size: 37064    Stored size: 36936
[05:00:29]          Current file modification time: 1437457457 (21-Jul-2015 06:44:17)
[05:00:29]          Stored file modification time : 1436988598 (15-Jul-2015 20:29:58)
[05:00:29]   /bin/touch                                      [ Warning ]
[05:00:29] Warning: The file properties have changed:
[05:00:29]          File: /bin/touch
[05:00:29]          Current hash: 592bf9c6a1204f9a2adc782d410677c7eca3af1b8134caf85c54e1e9b75c39b9
[05:00:29]          Stored hash : 37169464b23d7eb2f17212c4edc15543cb2a784c
[05:00:29]          Current inode: 655510    Stored inode: 655492
[05:00:29]          Current file modification time: 1444864248 (15-Out-2015 00:10:48)
[05:00:29]          Stored file modification time : 1421207414 (14-Jan-2015 03:50:14)
[05:00:29]   /bin/uname                                      [ Warning ]
[05:00:29] Warning: The file properties have changed:
[05:00:29]          File: /bin/uname
[05:00:29]          Current hash: 20cfebd591ce1d3d2b78c55fd022ea1a94d0aac6675b0f75c9ade9567274e1ec
[05:00:29]          Stored hash : fb275d43e3bee86b5936dd8d8b70b60121cb3893
[05:00:29]          Current inode: 655513    Stored inode: 655497
[05:00:29]          Current file modification time: 1444864248 (15-Out-2015 00:10:48)
[05:00:29]          Stored file modification time : 1421207414 (14-Jan-2015 03:50:14)
[05:00:30]   /bin/which                                      [ Warning ]
[05:00:30] Warning: The file properties have changed:
[05:00:30]          File: /bin/which
[05:00:30]          Current hash: 7bdde142dc5cb004ab82f55adba0c56fc78430a6f6b23afd33be491d4c7c238b
[05:00:30]          Stored hash : cd2cdf42c04fba4123f4b8f12bca9bbd76552c95
[05:00:30]          Current inode: 655408    Stored inode: 655370
[05:00:30]          Current file modification time: 1432604119 (26-Mai-2015 02:35:19)
[05:00:30]          Stored file modification time : 1377668562 (28-Ago-2013 06:42:42)
[05:00:30] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[05:00:30]   /bin/kmod                                       [ Warning ]
[05:00:30] Warning: The file properties have changed:
[05:00:30]          File: /bin/kmod
[05:00:30]          Current hash: d5e40d5b77530f3053e7539f4704da5f38f52d79d3857070fc6a6c82fa0d4a3c
[05:00:30]          Stored hash : 7ed11bba8ef27b8fe8617f5446142a3a0613cc41
[05:00:30]          Current inode: 655425    Stored inode: 655396
[05:00:30]          Current size: 154624    Stored size: 154616
[05:00:30]          Current file modification time: 1440083452 (20-Ago-2015 16:10:52)
[05:00:30]          Stored file modification time : 1397138879 (10-Abr-2014 15:07:59)
[05:00:30]   /bin/dash                                       [ Warning ]
[05:00:30] Warning: The file properties have changed:
[05:00:30]          File: /bin/dash
[05:00:30]          Current hash: e865a4ff01b0df1afec7b5fd7b3a8906baa57d77daaa4888a31dccbf004d011b
[05:00:30]          Stored hash : 647437c3d7543c7c8d381903834c9ef42eb4cf69
[05:00:30]          Current inode: 655443    Stored inode: 655368
[05:00:30]          Current size: 125400    Stored size: 121272
[05:00:30]          Current file modification time: 1433418977 (04-Jun-2015 12:56:17)
[05:00:30]          Stored file modification time : 1392812032 (19-Fev-2014 12:13:52)
[05:00:30]   /bin/systemd                                    [ Warning ]
[05:00:30] Warning: The file '/bin/systemd' exists on the system, but it is not present in the 'rkhunter.dat' file.
[05:00:30]   /bin/systemctl                                  [ Warning ]
[05:00:30] Warning: The file '/bin/systemctl' exists on the system, but it is not present in the 'rkhunter.dat' file.
[05:00:31]   /sbin/depmod                                    [ Warning ]
[05:00:31] Warning: The file properties have changed:
[05:00:31]          File: /sbin/depmod
[05:00:31]          Current hash: d5e40d5b77530f3053e7539f4704da5f38f52d79d3857070fc6a6c82fa0d4a3c
[05:00:31]          Stored hash : 7ed11bba8ef27b8fe8617f5446142a3a0613cc41
[05:00:31]          Current inode: 7864358    Stored inode: 7864339
[05:00:31]          Current file modification time: 1440083451 (20-Ago-2015 16:10:51)
[05:00:31]          Stored file modification time : 1397138876 (10-Abr-2014 15:07:56)
[05:00:31]   /sbin/fsck                                      [ Warning ]
[05:00:31] Warning: The file properties have changed:
[05:00:31]          File: /sbin/fsck
[05:00:31]          Current hash: f2fe40a64cd998f49ca36918410559243eab39cb417b661eeaf1864aa8f07e36
[05:00:31]          Stored hash : 79ee5c91b87d62e259811ad0cbb56ffbe54b9dd6
[05:00:31]          Current inode: 7871851    Stored inode: 7871213
[05:00:31]          Current size: 35832    Stored size: 31608
[05:00:31]          Current file modification time: 1438739354 (05-Ago-2015 02:49:14)
[05:00:31]          Stored file modification time : 1438741218 (05-Ago-2015 03:20:18)
[05:00:31]   /sbin/ifconfig                                  [ Warning ]
[05:00:31] Warning: The file properties have changed:
[05:00:31]          File: /sbin/ifconfig
[05:00:31]          Current hash: 44731bbb6523d8bbfdcc09e2eb6f8341524c0656ef8ab6c62ed758afac95140c
[05:00:31]          Stored hash : 74421bca240d7e85b5e8c3ebb7d1d36020c17a38
[05:00:31]          Current inode: 7871845    Stored inode: 7864385
[05:00:31]          Current file modification time: 1404134364 (30-Jun-2014 14:19:24)
[05:00:31]          Stored file modification time : 1407253475 (05-Ago-2014 16:44:35)
[05:00:31]   /sbin/ifdown                                    [ Warning ]
[05:00:31] Warning: The file properties have changed:
[05:00:32]          File: /sbin/ifdown
[05:00:32]          Current hash: 6484df5d9545ec0f788ea36b0c8e24b787f58f0fcc9a414e2e40692c55e05d4c
[05:00:32]          Stored hash : 0106cefb5c512887463d6424f1248cb25c1fd283
[05:00:32]          Current inode: 7864435    Stored inode: 7864356
[05:00:32]          Current file modification time: 1436504199 (10-Jul-2015 05:56:39)
[05:00:32]          Stored file modification time : 1399911407 (12-Mai-2014 17:16:47)
[05:00:32]   /sbin/ifup                                      [ Warning ]
[05:00:32] Warning: The file properties have changed:
[05:00:32]          File: /sbin/ifup
[05:00:32]          Current hash: 6484df5d9545ec0f788ea36b0c8e24b787f58f0fcc9a414e2e40692c55e05d4c
[05:00:32]          Stored hash : 0106cefb5c512887463d6424f1248cb25c1fd283
[05:00:32]          Current inode: 7864432    Stored inode: 7864326
[05:00:32]          Current size: 59440    Stored size: 62960
[05:00:32]          Current file modification time: 1436504199 (10-Jul-2015 05:56:39)
[05:00:32]          Stored file modification time : 1399911408 (12-Mai-2014 17:16:48)
[05:00:32]   /sbin/init                                      [ Warning ]
[05:00:32] Warning: The file properties have changed:
[05:00:32]          File: /sbin/init
[05:00:32]          Current hash: d583d78142a807704dd95c9d34c3978126be5058ece7bdf96c3e60de36330a29
[05:00:32]          Stored hash : f8318fbf9490e34035d35494f99842cb1f57192e
[05:00:32]          Current permissions: 0777    Stored permissions: 0755
[05:00:32]          Current inode: 7871893    Stored inode: 7864438
[05:00:32]          Current size: 20    Stored size: 265848
[05:00:32]          Current file modification time: 1444910521 (15-Out-2015 13:02:01)
[05:00:32]          Stored file modification time : 1405676811 (18-Jul-2014 10:46:51)
[05:00:32] Warning: No symbolic link target found for file '/sbin/init' in the 'rkhunter.dat' file.
[05:00:32]   /sbin/insmod                                    [ Warning ]
[05:00:32] Warning: The file properties have changed:
[05:00:32]          File: /sbin/insmod
[05:00:32]          Current hash: d5e40d5b77530f3053e7539f4704da5f38f52d79d3857070fc6a6c82fa0d4a3c
[05:00:32]          Stored hash : 7ed11bba8ef27b8fe8617f5446142a3a0613cc41
[05:00:32]          Current inode: 7864469    Stored inode: 7864335
[05:00:32]          Current file modification time: 1440083451 (20-Ago-2015 16:10:51)
[05:00:32]          Stored file modification time : 1397138876 (10-Abr-2014 15:07:56)
[05:00:32]   /sbin/ip                                        [ Warning ]
[05:00:32] Warning: The file properties have changed:
[05:00:32]          File: /sbin/ip
[05:00:32]          Current hash: d1a0a23a3a2686957237b350516569184af7d5a494b6b4443510fa1ae4784891
[05:00:32]          Stored hash : 2875b9b1d9ddbe144d64163ce0d7a2b0ad3b7f17
[05:00:32]          Current inode: 7864375    Stored inode: 7871202
[05:00:32]          Current file modification time: 1439979802 (19-Ago-2015 11:23:22)
[05:00:32]          Stored file modification time : 1437668371 (23-Jul-2015 17:19:31)
[05:00:33]   /sbin/lsmod                                     [ Warning ]
[05:00:33] Warning: The file properties have changed:
[05:00:33]          File: /sbin/lsmod
[05:00:33]          Current hash: d5e40d5b77530f3053e7539f4704da5f38f52d79d3857070fc6a6c82fa0d4a3c
[05:00:33]          Stored hash : 7ed11bba8ef27b8fe8617f5446142a3a0613cc41
[05:00:33]          Current inode: 7864406    Stored inode: 7864343
[05:00:33]          Current file modification time: 1440083451 (20-Ago-2015 16:10:51)
[05:00:33]          Stored file modification time : 1397138876 (10-Abr-2014 15:07:56)
[05:00:33]   /sbin/modinfo                                   [ Warning ]
[05:00:33] Warning: The file properties have changed:
[05:00:33]          File: /sbin/modinfo
[05:00:33]          Current hash: d5e40d5b77530f3053e7539f4704da5f38f52d79d3857070fc6a6c82fa0d4a3c
[05:00:33]          Stored hash : 7ed11bba8ef27b8fe8617f5446142a3a0613cc41
[05:00:33]          Current inode: 7871198    Stored inode: 7864337
[05:00:33]          Current file modification time: 1440083451 (20-Ago-2015 16:10:51)
[05:00:33]          Stored file modification time : 1397138876 (10-Abr-2014 15:07:56)
[05:00:33]   /sbin/modprobe                                  [ Warning ]
[05:00:33] Warning: The file properties have changed:
[05:00:33]          File: /sbin/modprobe
[05:00:33]          Current hash: d5e40d5b77530f3053e7539f4704da5f38f52d79d3857070fc6a6c82fa0d4a3c
[05:00:33]          Stored hash : 7ed11bba8ef27b8fe8617f5446142a3a0613cc41
[05:00:33]          Current inode: 7864446    Stored inode: 7864341
[05:00:33]          Current file modification time: 1440083451 (20-Ago-2015 16:10:51)
[05:00:33]          Stored file modification time : 1397138876 (10-Abr-2014 15:07:56)
[05:00:34]   /sbin/rmmod                                     [ Warning ]
[05:00:34] Warning: The file properties have changed:
[05:00:34]          File: /sbin/rmmod
[05:00:34]          Current hash: d5e40d5b77530f3053e7539f4704da5f38f52d79d3857070fc6a6c82fa0d4a3c
[05:00:34]          Stored hash : 7ed11bba8ef27b8fe8617f5446142a3a0613cc41
[05:00:34]          Current inode: 7864461    Stored inode: 7864333
[05:00:34]          Current file modification time: 1440083451 (20-Ago-2015 16:10:51)
[05:00:34]          Stored file modification time : 1397138876 (10-Abr-2014 15:07:56)
[05:00:34]   /sbin/route                                     [ Warning ]
[05:00:34] Warning: The file properties have changed:
[05:00:34]          File: /sbin/route
[05:00:34]          Current hash: bcec0906e2f49b98182a810fd751735efb02192dbfb8d5e3d3787cfa63843af5
[05:00:34]          Stored hash : abd0a50c99356c128efc430b5b7aa4dec874f0f7
[05:00:34]          Current inode: 7871846    Stored inode: 7864387
[05:00:34]          Current file modification time: 1404134364 (30-Jun-2014 14:19:24)
[05:00:34]          Stored file modification time : 1407253475 (05-Ago-2014 16:44:35)
[05:00:34]   /sbin/runlevel                                  [ Warning ]
[05:00:34] Warning: The file properties have changed:
[05:00:34]          File: /sbin/runlevel
[05:00:34]          Current hash: d799cfbdf17d10d710019d1a107b82060022a39945084ec4c5dcabcc0ff69010
[05:00:34]          Stored hash : afaa083e3c603a7cc87f51137e6d22277a7322b4
[05:00:34]          Current permissions: 0777    Stored permissions: 0755
[05:00:34]          Current inode: 7864437    Stored inode: 7864324
[05:00:34]          Current size: 14    Stored size: 10240
[05:00:34]          Current file modification time: 1444910521 (15-Out-2015 13:02:01)
[05:00:34]          Stored file modification time : 1405676811 (18-Jul-2014 10:46:51)
[05:00:34] Warning: No symbolic link target found for file '/sbin/runlevel' in the 'rkhunter.dat' file.
[05:00:34]   /sbin/sulogin                                   [ Warning ]
[05:00:34] Warning: The file properties have changed:
[05:00:34]          File: /sbin/sulogin
[05:00:34]          Current hash: ab0e37346995372da64001067970dbcef03b871b459ba889ba09f60f68768119
[05:00:34]          Stored hash : 65190e4215cc434e4405ab06902cd4157981e445
[05:00:34]          Current inode: 7873526    Stored inode: 7864504
[05:00:35]          Current size: 39936    Stored size: 14904
[05:00:35]          Current file modification time: 1438739354 (05-Ago-2015 02:49:14)
[05:00:35]          Stored file modification time : 1434339069 (15-Jun-2015 04:31:09)
[05:00:35]   /sbin/sysctl                                    [ Warning ]
[05:00:35] Warning: The file properties have changed:
[05:00:35]          File: /sbin/sysctl
[05:00:35]          Current hash: fcbe69441937ec7453715cd8a35a356ca26f2ecf00df8a50d00570d17bb1cd5a
[05:00:35]          Stored hash : e902dc35ffa9eebe472e4d4be678913b97f7ba02
[05:00:35]          Current inode: 7864337    Stored inode: 7864390
[05:00:35]          Current file modification time: 1423596214 (10-Fev-2015 19:23:34)
[05:00:35]          Stored file modification time : 1423598898 (10-Fev-2015 20:08:18)
[05:00:35]   /usr/sbin/adduser                               [ Warning ]
[05:00:35] Warning: The file properties have changed:
[05:00:35]          File: /usr/sbin/adduser
[05:00:35]          Current hash: b26732ab356b3fa5e2e4a053e9a92cdaeb8c48197810701d38f3fbb4811741aa
[05:00:35]          Stored hash : 3676086256f82ece513d9942b8442e5ccfe8fa97
[05:00:35]          Current inode: 2108703    Stored inode: 2097598
[05:00:35]          Current size: 37276    Stored size: 35125
[05:00:35]          Current file modification time: 1435867882 (02-Jul-2015 21:11:22)
[05:00:35]          Stored file modification time : 1383833695 (07-Nov-2013 14:14:55)
[05:00:35] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[05:00:36]   /usr/sbin/chroot                                [ Warning ]
[05:00:36] Warning: The file properties have changed:
[05:00:36]          File: /usr/sbin/chroot
[05:00:36]          Current hash: abfbf805ef5d26118b56f9058648d4741b65a440ad2c0efbdd2c4e126f9eceb3
[05:00:36]          Stored hash : cca40a599f3dbd4b616d94e9a1afdbb474c58fe7
[05:00:36]          Current inode: 2114746    Stored inode: 2097197
[05:00:36]          Current size: 35520    Stored size: 31392
[05:00:36]          Current file modification time: 1444864248 (15-Out-2015 00:10:48)
[05:00:36]          Stored file modification time : 1421207414 (14-Jan-2015 03:50:14)
[05:00:36]   /usr/sbin/cron                                  [ Warning ]
[05:00:36] Warning: The file properties have changed:
[05:00:36]          File: /usr/sbin/cron
[05:00:36]          Current hash: 0ac0dec694553e356cdf565ea9a2f8dda3b23e7cdd8d54bce5b6f2165db5724f
[05:00:36]          Stored hash : 165768f0bfa442ef3a856888d4566ddad5f6c812
[05:00:36]          Current inode: 2097603    Stored inode: 2101710
[05:00:36]          Current size: 44536    Stored size: 44376
[05:00:36]          Current file modification time: 1414401982 (27-Out-2014 09:26:22)
[05:00:36]          Stored file modification time : 1360393343 (09-Fev-2013 07:02:23)
[05:00:36]   /usr/sbin/groupadd                              [ Warning ]
[05:00:36] Warning: The file properties have changed:
[05:00:36]          File: /usr/sbin/groupadd
[05:00:36]          Current hash: e2ee45e23194cdb414593cb2660db0b095dff8d00f0d15d7844964c39e5f7b5a
[05:00:36]          Stored hash : 954f25505f2a08c4ae7cb460d284172d3adb6f29
[05:00:36]          Current inode: 2098871    Stored inode: 2099052
[05:00:36]          Current size: 55704    Stored size: 55544
[05:00:36]          Current file modification time: 1437457455 (21-Jul-2015 06:44:15)
[05:00:36]          Stored file modification time : 1436988596 (15-Jul-2015 20:29:56)
[05:00:36]   /usr/sbin/groupdel                              [ Warning ]
[05:00:36] Warning: The file properties have changed:
[05:00:36]          File: /usr/sbin/groupdel
[05:00:36]          Current hash: 1bc6869cf0b2202491a5cff66a4b601b75d559f623d3088753bc94fcb5d60cfd
[05:00:36]          Stored hash : a5626676bf36ff7f6b61f340f52e5359eec59724
[05:00:36]          Current inode: 2101622    Stored inode: 2099053
[05:00:36]          Current size: 51472    Stored size: 51312
[05:00:36]          Current file modification time: 1437457455 (21-Jul-2015 06:44:15)
[05:00:37]          Stored file modification time : 1436988596 (15-Jul-2015 20:29:56)
[05:00:37]   /usr/sbin/groupmod                              [ Warning ]
[05:00:37] Warning: The file properties have changed:
[05:00:37]          File: /usr/sbin/groupmod
[05:00:37]          Current hash: 6fe6eb53b180de1893a0897661e3293a67bfeff37b3d5c6d339f027263c50a15
[05:00:37]          Stored hash : 8f838cfe13011b077c764bda1d6c538e70079420
[05:00:37]          Current inode: 2101627    Stored inode: 2099044
[05:00:37]          Current size: 66384    Stored size: 66096
[05:00:37]          Current file modification time: 1437457455 (21-Jul-2015 06:44:15)
[05:00:37]          Stored file modification time : 1436988596 (15-Jul-2015 20:29:56)
[05:00:37]   /usr/sbin/grpck                                 [ Warning ]
[05:00:37] Warning: The file properties have changed:
[05:00:37]          File: /usr/sbin/grpck
[05:00:37]          Current hash: 0f343ae25c43e9228fbafdc2d9dee1d060dab41a55b17a5a2889bdf14a5c59e8
[05:00:37]          Stored hash : 95fbe701e5cc8c69ad6bed55c4c82fe1c7d96cf3
[05:00:37]          Current inode: 2101628    Stored inode: 2099040
[05:00:37]          Current size: 51600    Stored size: 51408
[05:00:37]          Current file modification time: 1437457455 (21-Jul-2015 06:44:15)
[05:00:37]          Stored file modification time : 1436988596 (15-Jul-2015 20:29:56)
[05:00:37]   /usr/sbin/nologin                               [ Warning ]
[05:00:37] Warning: The file properties have changed:
[05:00:37]          File: /usr/sbin/nologin
[05:00:37]          Current hash: 271a3219f26d7a71acaf17fca7ddc46a6b7ee1030e81ab86d9af63c46f209441
[05:00:37]          Stored hash : 5ee9e6211d169e298d76595d3287384ba6014974
[05:00:38]          Current inode: 2098117    Stored inode: 2099004
[05:00:38]          Current file modification time: 1437457457 (21-Jul-2015 06:44:17)
[05:00:38]          Stored file modification time : 1436988598 (15-Jul-2015 20:29:58)
[05:00:38]   /usr/sbin/prelink                               [ Warning ]
[05:00:38] Warning: The file properties have changed:
[05:00:38]          File: /usr/sbin/prelink
[05:00:38]          Current hash: c5b7c346f852ba309820ff8e6654d48868be7c9ae390f0a77734602ad6a08c16
[05:00:38]          Stored hash : d7a81cfb35778229c04595907ca12f9787dde38b
[05:00:38]          Current inode: 2107037    Stored inode: 2111940
[05:00:38]          Current file modification time: 1398513048 (26-Abr-2014 12:50:48)
[05:00:38]          Stored file modification time : 1384617391 (16-Nov-2013 15:56:31)
[05:00:38] Warning: The command '/usr/sbin/prelink' has been replaced by a script: /usr/sbin/prelink: Bourne-Again shell script, ASCII text executable
[05:00:38]   /usr/sbin/pwck                                  [ Warning ]
[05:00:38] Warning: The file properties have changed:
[05:00:38]          File: /usr/sbin/pwck
[05:00:38]          Current hash: f3c3150240844035dcb780b11cf269e11bfb2cecdd8e1edf6d11b471b38b8390
[05:00:38]          Stored hash : 5431c29838632d26f1bcd12a0b46c86efd38f689
[05:00:38]          Current inode: 2101623    Stored inode: 2099043
[05:00:38]          Current size: 47448    Stored size: 47288
[05:00:38]          Current file modification time: 1437457455 (21-Jul-2015 06:44:15)
[05:00:38]          Stored file modification time : 1436988596 (15-Jul-2015 20:29:56)
[05:00:38]   /usr/sbin/rsyslogd                              [ Warning ]
[05:00:38] Warning: The file properties have changed:
[05:00:38]          File: /usr/sbin/rsyslogd
[05:00:38]          Current hash: 4fe70817c471d5f63c4cacc3ae28545eeb8c4101c03c5d78e53bed549a5eda95
[05:00:38]          Stored hash : b1c259538a8cf04b94c03eb03b86c53b09afcac6
[05:00:38]          Current inode: 2102050    Stored inode: 2101590
[05:00:38]          Current size: 595104    Stored size: 521824
[05:00:38]          Current file modification time: 1441200424 (02-Set-2015 14:27:04)
[05:00:38]          Stored file modification time : 1430945800 (06-Mai-2015 21:56:40)
[05:00:39]   /usr/sbin/sshd                                  [ Warning ]
[05:00:39] Warning: The file properties have changed:
[05:00:39]          File: /usr/sbin/sshd
[05:00:39]          Current hash: faf1a38c45030d12c7c7bc687f19fb7a3665cc4a563a4ae15430b425ebb39342
[05:00:39]          Stored hash : 2ee01c754b29085ff616f452fba208952fa6d35e
[05:00:39]          Current inode: 2105054    Stored inode: 2106168
[05:00:39]          Current size: 828232    Stored size: 766784
[05:00:39]          Current file modification time: 1441964023 (11-Set-2015 10:33:43)
[05:00:39]          Stored file modification time : 1439864061 (18-Ago-2015 03:14:21)
[05:00:39]   /usr/sbin/tcpd                                  [ Warning ]
[05:00:39] Warning: The file properties have changed:
[05:00:39]          File: /usr/sbin/tcpd
[05:00:39]          Current hash: e2f6d28d83953dcec5d713ba2015b23531864df372a1aa57c4ca8790b0d07b6c
[05:00:39]          Stored hash : cd9cfc19df7f0e4b7f9adfa4fe8c5d74caa53d86
[05:00:39]   /usr/sbin/useradd                               [ Warning ]
[05:00:39] Warning: The file properties have changed:
[05:00:39]          File: /usr/sbin/useradd
[05:00:39]          Current hash: b636841e0997c2b6f3733b75b9a457e554def076ff30af989ac9f121be876557
[05:00:39]          Stored hash : dbdaa0c2bb047a2bbf1354a075dd2bdefd472f27
[05:00:39]          Current inode: 2098865    Stored inode: 2099047
[05:00:39]          Current size: 114840    Stored size: 110456
[05:00:39]          Current file modification time: 1437457455 (21-Jul-2015 06:44:15)
[05:00:39]          Stored file modification time : 1436988596 (15-Jul-2015 20:29:56)
[05:00:39]   /usr/sbin/userdel                               [ Warning ]
[05:00:39] Warning: The file properties have changed:
[05:00:39]          File: /usr/sbin/userdel
[05:00:39]          Current hash: 3487ce49e0e8e37778a6a7937d2b392ca3f12f0a51f233d0e05bf8e2e7d12665
[05:00:39]          Stored hash : 7f85dc4cbd283d2672af53d4c96b438bbb9662a0
[05:00:39]          Current inode: 2098867    Stored inode: 2099056
[05:00:39]          Current size: 81048    Stored size: 76728
[05:00:39]          Current file modification time: 1437457455 (21-Jul-2015 06:44:15)
[05:00:39]          Stored file modification time : 1436988596 (15-Jul-2015 20:29:56)
[05:00:40]   /usr/sbin/usermod                               [ Warning ]
[05:00:40] Warning: The file properties have changed:
[05:00:40]          File: /usr/sbin/usermod
[05:00:40]          Current hash: 362a72fb83de4bb621ecf8caebbd0a44c80de12824230a785e88a36c0a5a2b96
[05:00:40]          Stored hash : f88246a39c60168da116ff3eee8e652785bd9a4e
[05:00:40]          Current inode: 2098872    Stored inode: 2099051
[05:00:40]          Current size: 110488    Stored size: 110264
[05:00:40]          Current file modification time: 1437457455 (21-Jul-2015 06:44:15)
[05:00:40]          Stored file modification time : 1436988596 (15-Jul-2015 20:29:56)
[05:00:40]   /usr/sbin/vipw                                  [ Warning ]
[05:00:40] Warning: The file properties have changed:
[05:00:40]          File: /usr/sbin/vipw
[05:00:40]          Current hash: e43edf7a25c5e198590bb05ceb104e1a3bebf93105a71ea4aa72785377f6905d
[05:00:40]          Stored hash : 868c03d988ec6bf8c5f3c478b42fb81f87ee07bd
[05:00:40]          Current inode: 2098866    Stored inode: 2099045
[05:00:40]          Current size: 54032    Stored size: 53808
[05:00:40]          Current file modification time: 1437457455 (21-Jul-2015 06:44:15)
[05:00:40]          Stored file modification time : 1436988596 (15-Jul-2015 20:29:56)
[05:00:40]   /usr/sbin/unhide-linux                          [ Warning ]
[05:00:40] Warning: The file properties have changed:
[05:00:40]          File: /usr/sbin/unhide-linux
[05:00:40]          Current hash: a41da60d4325d0805899b019f13ece793a2d9554cd667380bab8bb93a41b8332
[05:00:40]          Stored hash : b0a4f70f4284f3a0839f1ed33d15ec01b7ec8083
[05:00:40]   /usr/sbin/unhide-posix                          [ Warning ]
[05:00:40] Warning: The file properties have changed:
[05:00:40]          File: /usr/sbin/unhide-posix
[05:00:40]          Current hash: 589b2bfe9200677cf4a213488217ce06c70acfc62d666eaaf2fcc68a832714d2
[05:00:40]          Stored hash : 14defd2522a5becafff2d7a6b4192d194c3b096e
[05:00:40]   /usr/sbin/unhide-tcp                            [ Warning ]
[05:00:40] Warning: The file properties have changed:
[05:00:40]          File: /usr/sbin/unhide-tcp
[05:00:40]          Current hash: 92a492bda0c9277e0481ad1f3efc71eceb9a4ee3b04b897564c79402c8a143ce
[05:00:40]          Stored hash : 67d8f617e9e067c235e53d591f6ce64a7b65ab00
[05:00:42]   /usr/local/bin/rkhunter                         [ Warning ]
[05:00:42] Warning: The file properties have changed:
[05:00:42]          File: /usr/local/bin/rkhunter
[05:00:42]          Current hash: 136a8b9da96d5f62fa23df3da3a49cb8428837a861e67689eabba38d86dacaaf
[05:00:42]          Stored hash : cd87f594cbd5118dbd28ba51106f7a2f08863989
[05:00:46]   /lib/systemd/systemd                            [ Warning ]
[05:00:46] Warning: The file '/lib/systemd/systemd' exists on the system, but it is not present in the 'rkhunter.dat' file.
[05:00:47]
[05:00:47] Info: Starting test name 'rootkits'
[05:00:47] Checking for rootkits...
[05:00:47]
[05:00:47] Info: Starting test name 'known_rkts'
[05:00:47] Performing check of known rootkit files and directories
[05:00:47]
[05:00:47] Checking for 55808 Trojan - Variant A...
[05:00:47]   Checking for file '/tmp/.../r'                  [ Not found ]
[05:00:47]   Checking for file '/tmp/.../a'                  [ Not found ]
[05:00:47] 55808 Trojan - Variant A                          [ Not found ]
[05:00:47]
[05:00:47] Checking for ADM Worm...
[05:00:47]   Checking for string 'w0rm'                      [ Not found ]
[05:00:47] ADM Worm                                          [ Not found ]
[05:00:47]
[05:00:47] Checking for AjaKit Rootkit...
[05:00:47]   Checking for file '/dev/tux/.addr'              [ Not found ]
[05:00:47]   Checking for file '/dev/tux/.proc'              [ Not found ]
[05:00:47]   Checking for file '/dev/tux/.file'              [ Not found ]
[05:00:47]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[05:00:47]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[05:00:47]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[05:00:47]   Checking for directory '/dev/tux'               [ Not found ]
[05:00:47]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[05:00:47] AjaKit Rootkit                                    [ Not found ]
[05:00:47]
[05:00:47] Checking for Adore Rootkit...
[05:00:47]   Checking for file '/usr/secure'                 [ Not found ]
[05:00:47]   Checking for file '/usr/doc/sys/qrt'            [ Not found ]
[05:00:47]   Checking for file '/usr/doc/sys/run'            [ Not found ]
[05:00:47]   Checking for file '/usr/doc/sys/crond'          [ Not found ]
[05:00:47]   Checking for file '/usr/sbin/kfd'               [ Not found ]
[05:00:47]   Checking for file '/usr/doc/kern/var'           [ Not found ]
[05:00:47]   Checking for file '/usr/doc/kern/string.o'      [ Not found ]
[05:00:47]   Checking for file '/usr/doc/kern/ava'           [ Not found ]
[05:00:47]   Checking for file '/usr/doc/kern/adore.o'       [ Not found ]
[05:00:48]   Checking for file '/var/log/ssh/old'            [ Not found ]
[05:00:48]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[05:00:48]   Checking for directory '/usr/doc/kern'          [ Not found ]
[05:00:48]   Checking for directory '/usr/doc/backup'        [ Not found ]
[05:00:48]   Checking for directory '/usr/doc/backup/txt'    [ Not found ]
[05:00:48]   Checking for directory '/lib/backup'            [ Not found ]
[05:00:48]   Checking for directory '/lib/backup/txt'        [ Not found ]
[05:00:48]   Checking for directory '/usr/doc/work'          [ Not found ]
[05:00:48]   Checking for directory '/usr/doc/sys'           [ Not found ]
[05:00:48]   Checking for directory '/var/log/ssh'           [ Not found ]
[05:00:48]   Checking for directory '/usr/doc/.spool'        [ Not found ]
[05:00:48]   Checking for directory '/usr/lib/kterm'         [ Not found ]
[05:00:48] Adore Rootkit                                     [ Not found ]
[05:00:48]
[05:00:48] Checking for aPa Kit...
[05:00:48]   Checking for file '/usr/share/.aPa'             [ Not found ]
[05:00:48] aPa Kit                                           [ Not found ]
[05:00:48]
[05:00:48] Checking for Apache Worm...
[05:00:48]   Checking for file '/bin/.log'                   [ Not found ]
[05:00:48] Apache Worm                                       [ Not found ]
[05:00:48]
[05:00:48] Checking for Ambient (ark) Rootkit...
[05:00:48]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[05:00:48]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[05:00:48]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[05:00:48]   Checking for file '/dev/ptyxx/.proc'            [ Not found ]
[05:00:48]   Checking for file '/dev/ptyxx/.addr'            [ Not found ]
[05:00:48]   Checking for directory '/dev/ptyxx'             [ Not found ]
[05:00:48] Ambient (ark) Rootkit                             [ Not found ]
[05:00:48]
[05:00:48] Checking for Balaur Rootkit...
[05:00:48]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[05:00:48]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[05:00:48]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[05:00:48]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[05:00:48] Balaur Rootkit                                    [ Not found ]
[05:00:48]
[05:00:48] Checking for BeastKit Rootkit...
[05:00:48]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[05:00:48]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[05:00:48]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[05:00:48]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[05:00:48]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[05:00:48]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[05:00:48]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[05:00:48]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[05:00:48]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[05:00:48]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[05:00:48] BeastKit Rootkit                                  [ Not found ]
[05:00:48]
[05:00:48] Checking for beX2 Rootkit...
[05:00:48]   Checking for file '/usr/info/termcap.info-5.gz' [ Not found ]
[05:00:48]   Checking for file '/usr/bin/sshd2'              [ Not found ]
[05:00:49]   Checking for directory '/usr/include/bex'       [ Not found ]
[05:00:49] beX2 Rootkit                                      [ Not found ]
[05:00:49]
[05:00:49] Checking for BOBKit Rootkit...
[05:00:49]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[05:00:49]   Checking for file '/usr/sbin/.../bkit-ava'      [ Not found ]
[05:00:49]   Checking for file '/usr/sbin/.../bkit-d'        [ Not found ]
[05:00:49]   Checking for file '/usr/sbin/.../bkit-shd'      [ Not found ]
[05:00:49]   Checking for file '/usr/sbin/.../bkit-f'        [ Not found ]
[05:00:49]   Checking for file '/usr/include/.../proc.h'     [ Not found ]
[05:00:49]   Checking for file '/usr/include/.../.bash_history' [ Not found ]
[05:00:49]   Checking for file '/usr/include/.../bkit-get'   [ Not found ]
[05:00:49]   Checking for file '/usr/include/.../bkit-dl'    [ Not found ]
[05:00:49]   Checking for file '/usr/include/.../bkit-screen' [ Not found ]
[05:00:49]   Checking for file '/usr/include/.../bkit-sleep' [ Not found ]
[05:00:49]   Checking for file '/usr/lib/.../bkit-adore.o'   [ Not found ]
[05:00:49]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[05:00:49]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[05:00:49]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[05:00:49]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[05:00:49]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[05:00:49]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[05:00:49]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[05:00:49]   Checking for file '/usr/lib/.../bkit-ssh/bkit-mots' [ Not found ]
[05:00:49]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[05:00:49]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[05:00:49]   Checking for file '/usr/lib/.../find'           [ Not found ]
[05:00:49]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[05:00:49]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[05:00:49]   Checking for file '/usr/lib/.../du'             [ Not found ]
[05:00:49]   Checking for file '/usr/lib/.../top'            [ Not found ]
[05:00:49]   Checking for directory '/usr/sbin/...'          [ Not found ]
[05:00:49]   Checking for directory '/usr/include/...'       [ Not found ]
[05:00:49]   Checking for directory '/usr/include/.../.tmp'  [ Not found ]
[05:00:49]   Checking for directory '/usr/lib/...'           [ Not found ]
[05:00:49]   Checking for directory '/usr/lib/.../.ssh'      [ Not found ]
[05:00:49]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[05:00:49]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[05:00:49]   Checking for directory '/tmp/.bkp'              [ Not found ]
[05:00:49] BOBKit Rootkit                                    [ Not found ]
[05:00:49]
[05:00:49] Checking for cb Rootkit...
[05:00:49]   Checking for file '/dev/srd0'                   [ Not found ]
[05:00:49]   Checking for file '/lib/libproc.so.2.0.6'       [ Not found ]
[05:00:49]   Checking for file '/dev/mounnt'                 [ Not found ]
[05:00:49]   Checking for file '/etc/rc.d/init.d/init'       [ Not found ]
[05:00:49]   Checking for file '/usr/bin/.zeen/..<SP>/cl'    [ Not found ]
[05:00:50]   Checking for file '/usr/bin/.zeen/..<SP>/.x.tgz' [ Not found ]
[05:00:50]   Checking for file '/usr/bin/.zeen/..<SP>/statdx' [ Not found ]
[05:00:50]   Checking for file '/usr/bin/.zeen/..<SP>/wted'  [ Not found ]
[05:00:50]   Checking for file '/usr/bin/.zeen/..<SP>/write' [ Not found ]
[05:00:50]   Checking for file '/usr/bin/.zeen/..<SP>/scan'  [ Not found ]
[05:00:50]   Checking for file '/usr/bin/.zeen/..<SP>/sc'    [ Not found ]
[05:00:50]   Checking for file '/usr/bin/.zeen/..<SP>/sl2'   [ Not found ]
[05:00:50]   Checking for file '/usr/bin/.zeen/..<SP>/wroot' [ Not found ]
[05:00:50]   Checking for file '/usr/bin/.zeen/..<SP>/wscan' [ Not found ]
[05:00:50]   Checking for file '/usr/bin/.zeen/..<SP>/wu'    [ Not found ]
[05:00:50]   Checking for file '/usr/bin/.zeen/..<SP>/v'     [ Not found ]
[05:00:50]   Checking for file '/usr/bin/.zeen/..<SP>/read'  [ Not found ]
[05:00:50]   Checking for file '/usr/lib/sshrc'              [ Not found ]
[05:00:50]   Checking for file '/usr/lib/ssh_host_key'       [ Not found ]
[05:00:50]   Checking for file '/usr/lib/ssh_host_key.pub'   [ Not found ]
[05:00:50]   Checking for file '/usr/lib/ssh_random_seed'    [ Not found ]
[05:00:50]   Checking for file '/usr/lib/sshd_config'        [ Not found ]
[05:00:50]   Checking for file '/usr/lib/shosts.equiv'       [ Not found ]
[05:00:50]   Checking for file '/usr/lib/ssh_known_hosts'    [ Not found ]
[05:00:50]   Checking for file '/u/zappa/.ssh/pid'           [ Not found ]
[05:00:50]   Checking for file '/usr/bin/.system/..<SP>/tcp.log' [ Not found ]
[05:00:50]   Checking for file '/usr/bin/.zeen/..<SP>/curatare/attrib' [ Not found ]
[05:00:50]   Checking for file '/usr/bin/.zeen/..<SP>/curatare/chattr' [ Not found ]
[05:00:50]   Checking for file '/usr/bin/.zeen/..<SP>/curatare/ps' [ Not found ]
[05:00:50]   Checking for file '/usr/bin/.zeen/..<SP>/curatare/pstree' [ Not found ]
[05:00:50]   Checking for file '/usr/bin/.system/..<SP>/.x/xC.o' [ Not found ]
[05:00:50]   Checking for directory '/usr/bin/.zeen'         [ Not found ]
[05:00:50]   Checking for directory '/usr/bin/.zeen/..<SP>/curatare' [ Not found ]
[05:00:50]   Checking for directory '/usr/bin/.zeen/..<SP>/scan' [ Not found ]
[05:00:50]   Checking for directory '/usr/bin/.system/..<SP>' [ Not found ]
[05:00:50] cb Rootkit                                        [ Not found ]
[05:00:50]
[05:00:50] Checking for CiNIK Worm (Slapper.B variant)...
[05:00:50]   Checking for file '/tmp/.cinik'                 [ Not found ]
[05:00:50]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[05:00:50] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[05:00:50]
[05:00:50] Checking for Danny-Boy's Abuse Kit...
[05:00:50]   Checking for file '/dev/mdev'                   [ Not found ]
[05:00:50]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[05:00:50] Danny-Boy's Abuse Kit                             [ Not found ]
[05:00:50]
[05:00:50] Checking for Devil RootKit...
[05:00:50]   Checking for file '/var/lib/games/.src'         [ Not found ]
[05:00:50]   Checking for file '/dev/dsx'                    [ Not found ]
[05:00:50]   Checking for file '/dev/caca'                   [ Not found ]
[05:00:50]   Checking for file '/dev/pro'                    [ Not found ]
[05:00:50]   Checking for file '/bin/bye'                    [ Not found ]
[05:00:50]   Checking for file '/bin/homedir'                [ Not found ]
[05:00:51]   Checking for file '/usr/bin/xfss'               [ Not found ]
[05:00:51]   Checking for file '/usr/sbin/tzava'             [ Not found ]
[05:00:51]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/holber' [ Not found ]
[05:00:51]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/sense' [ Not found ]
[05:00:51]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/clear' [ Not found ]
[05:00:51]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/tzava' [ Not found ]
[05:00:51]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/citeste' [ Not found ]
[05:00:51]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/killrk' [ Not found ]
[05:00:51]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/searchlog' [ Not found ]
[05:00:51]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/gaoaza' [ Not found ]
[05:00:51]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/cleaner' [ Not found ]
[05:00:51]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/shk' [ Not found ]
[05:00:51]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/srs' [ Not found ]
[05:00:51]   Checking for file '/usr/doc/tar/.../.dracusor/utile.tgz' [ Not found ]
[05:00:51]   Checking for file '/usr/doc/tar/.../.dracusor/webpage' [ Not found ]
[05:00:51]   Checking for file '/usr/doc/tar/.../.dracusor/getpsy' [ Not found ]
[05:00:51]   Checking for file '/usr/doc/tar/.../.dracusor/getbnc' [ Not found ]
[05:00:51]   Checking for file '/usr/doc/tar/.../.dracusor/getemech' [ Not found ]
[05:00:51]   Checking for file '/usr/doc/tar/.../.dracusor/localroot.sh' [ Not found ]
[05:00:51]   Checking for file '/usr/doc/tar/.../.dracusor/stuff/old/sense' [ Not found ]
[05:00:51]   Checking for directory '/usr/doc/tar/.../.dracusor' [ Not found ]
[05:00:51] Devil RootKit                                     [ Not found ]
[05:00:51]
[05:00:51] Checking for Dica-Kit Rootkit...
[05:00:51]   Checking for file '/lib/.sso'                   [ Not found ]
[05:00:51]   Checking for file '/lib/.so'                    [ Not found ]
[05:00:51]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[05:00:51]   Checking for file '/var/run/...dica/dxr'        [ Not found ]
[05:00:51]   Checking for file '/var/run/...dica/read'       [ Not found ]
[05:00:51]   Checking for file '/var/run/...dica/write'      [ Not found ]
[05:00:51]   Checking for file '/var/run/...dica/lf'         [ Not found ]
[05:00:51]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[05:00:51]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[05:00:51]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[05:00:51]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[05:00:51]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[05:00:51]   Checking for file '/var/run/...dica/va'         [ Not found ]
[05:00:51]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[05:00:51]   Checking for file '/var/run/...dica/last.log'   [ Not found ]
[05:00:51]   Checking for file '/usr/bin/.etc'               [ Not found ]
[05:00:51]   Checking for file '/etc/sshd_config'            [ Not found ]
[05:00:51]   Checking for file '/etc/ssh_host_key'           [ Not found ]
[05:00:51]   Checking for file '/etc/ssh_random_seed'        [ Not found ]
[05:00:51]   Checking for directory '/var/run/...dica'       [ Not found ]
[05:00:51]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[05:00:52]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[05:00:52] Dica-Kit Rootkit                                  [ Not found ]
[05:00:52]
[05:00:52] Checking for Dreams Rootkit...
[05:00:52]   Checking for file '/dev/ttyoa'                  [ Not found ]
[05:00:52]   Checking for file '/dev/ttyof'                  [ Not found ]
[05:00:52]   Checking for file '/dev/ttyop'                  [ Not found ]
[05:00:52]   Checking for file '/usr/bin/sense'              [ Not found ]
[05:00:52]   Checking for file '/usr/bin/sl2'                [ Not found ]
[05:00:52]   Checking for file '/usr/bin/logclear'           [ Not found ]
[05:00:52]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[05:00:52]   Checking for file '/usr/bin/initrd'             [ Not found ]
[05:00:52]   Checking for file '/usr/bin/crontabs'           [ Not found ]
[05:00:52]   Checking for file '/usr/bin/snfs'               [ Not found ]
[05:00:52]   Checking for file '/usr/lib/libsss'             [ Not found ]
[05:00:52]   Checking for file '/usr/lib/libsnf.log'         [ Not found ]
[05:00:52]   Checking for file '/usr/lib/libshtift/top'      [ Not found ]
[05:00:52]   Checking for file '/usr/lib/libshtift/ps'       [ Not found ]
[05:00:52]   Checking for file '/usr/lib/libshtift/netstat'  [ Not found ]
[05:00:52]   Checking for file '/usr/lib/libshtift/ls'       [ Not found ]
[05:00:52]   Checking for file '/usr/lib/libshtift/ifconfig' [ Not found ]
[05:00:52]   Checking for file '/usr/include/linseed.h'      [ Not found ]
[05:00:52]   Checking for file '/usr/include/linpid.h'       [ Not found ]
[05:00:52]   Checking for file '/usr/include/linkey.h'       [ Not found ]
[05:00:52]   Checking for file '/usr/include/linconf.h'      [ Not found ]
[05:00:52]   Checking for file '/usr/include/iceseed.h'      [ Not found ]
[05:00:52]   Checking for file '/usr/include/icepid.h'       [ Not found ]
[05:00:52]   Checking for file '/usr/include/icekey.h'       [ Not found ]
[05:00:52]   Checking for file '/usr/include/iceconf.h'      [ Not found ]
[05:00:52]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[05:00:52]   Checking for directory '/usr/lib/libshtift'     [ Not found ]
[05:00:52] Dreams Rootkit                                    [ Not found ]
[05:00:52]
[05:00:52] Checking for Duarawkz Rootkit...
[05:00:52]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[05:00:52]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[05:00:52] Duarawkz Rootkit                                  [ Not found ]
[05:00:52]
[05:00:52] Checking for Enye LKM...
[05:00:52]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[05:00:52]   Checking for file '/etc/.enyelkmOCULTAR.ko'     [ Not found ]
[05:00:52] Enye LKM                                          [ Not found ]
[05:00:52]
[05:00:52] Checking for Flea Linux Rootkit...
[05:00:52]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[05:00:52]   Checking for file '/lib/security/.config/ssh/sshd_config' [ Not found ]
[05:00:52]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[05:00:52]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[05:00:52]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[05:00:52]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[05:00:53]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[05:00:53]   Checking for file '/usr/lib/ldlibps.so'         [ Not found ]
[05:00:53]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[05:00:53]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[05:00:53]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[05:00:53]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[05:00:53]   Checking for directory '/dev/..0'               [ Not found ]
[05:00:53]   Checking for directory '/dev/..0/backup'        [ Not found ]
[05:00:53] Flea Linux Rootkit                                [ Not found ]
[05:00:53]
[05:00:53] Checking for Fu Rootkit...
[05:00:53]   Checking for file '/sbin/xc'                    [ Not found ]
[05:00:53]   Checking for file '/usr/include/ivtype.h'       [ Not found ]
[05:00:53]   Checking for file '/bin/.lib'                   [ Not found ]
[05:00:53] Fu Rootkit                                        [ Not found ]
[05:00:53]
[05:00:53] Checking for ****`it Rootkit...
[05:00:53]   Checking for file '/lib/libproc.so.2.0.7'       [ Not found ]
[05:00:53]   Checking for file '/dev/proc/.bash_profile'     [ Not found ]
[05:00:53]   Checking for file '/dev/proc/.bashrc'           [ Not found ]
[05:00:53]   Checking for file '/dev/proc/.cshrc'            [ Not found ]
[05:00:53]   Checking for file '/dev/proc/****it/hax0r'      [ Not found ]
[05:00:53]   Checking for file '/dev/proc/****it/hax0rshell' [ Not found ]
[05:00:53]   Checking for file '/dev/proc/****it/config/lports' [ Not found ]
[05:00:53]   Checking for file '/dev/proc/****it/config/rports' [ Not found ]
[05:00:53]   Checking for file '/dev/proc/****it/config/rkconf' [ Not found ]
[05:00:53]   Checking for file '/dev/proc/****it/config/password' [ Not found ]
[05:00:53]   Checking for file '/dev/proc/****it/config/progs' [ Not found ]
[05:00:53]   Checking for file '/dev/proc/****it/system-bins/init' [ Not found ]
[05:00:53]   Checking for file '/usr/lib/libcps.a'           [ Not found ]
[05:00:53]   Checking for file '/usr/lib/libtty.a'           [ Not found ]
[05:00:53]   Checking for directory '/dev/proc'              [ Not found ]
[05:00:53]   Checking for directory '/dev/proc/****it'       [ Not found ]
[05:00:53]   Checking for directory '/dev/proc/****it/system-bins' [ Not found ]
[05:00:53]   Checking for directory '/dev/proc/toolz'        [ Not found ]
[05:00:53] ****`it Rootkit                                   [ Not found ]
[05:00:53]
[05:00:53] Checking for GasKit Rootkit...
[05:00:53]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[05:00:53]   Checking for directory '/dev/dev'               [ Not found ]
[05:00:53]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[05:00:53]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[05:00:53] GasKit Rootkit                                    [ Not found ]
[05:00:53]
[05:00:53] Checking for Heroin LKM...
[05:00:53]   Checking for kernel symbol 'heroin'             [ Not found ]
[05:00:53] Heroin LKM                                        [ Not found ]
[05:00:53]
[05:00:53] Checking for HjC Kit...
[05:00:53]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[05:00:54] HjC Kit                                           [ Not found ]
[05:00:54]
[05:00:54] Checking for ignoKit Rootkit...
[05:00:54]   Checking for file '/lib/defs/p'                 [ Not found ]
[05:00:54]   Checking for file '/lib/defs/q'                 [ Not found ]
[05:00:54]   Checking for file '/lib/defs/r'                 [ Not found ]
[05:00:54]   Checking for file '/lib/defs/s'                 [ Not found ]
[05:00:54]   Checking for file '/lib/defs/t'                 [ Not found ]
[05:00:54]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[05:00:54]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[05:00:54]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[05:00:54]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[05:00:54]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[05:00:54]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[05:00:54]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[05:00:54]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[05:00:54]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[05:00:54] ignoKit Rootkit                                   [ Not found ]
[05:00:54]
[05:00:54] Checking for IntoXonia-NG Rootkit...
[05:00:54]   Checking for kernel symbol 'funces'             [ Not found ]
[05:00:54]   Checking for kernel symbol 'ixinit'             [ Not found ]
[05:00:54]   Checking for kernel symbol 'tricks'             [ Not found ]
[05:00:54]   Checking for kernel symbol 'kernel_unlink'      [ Not found ]
[05:00:54]   Checking for kernel symbol 'rootme'             [ Not found ]
[05:00:54]   Checking for kernel symbol 'hide_module'        [ Not found ]
[05:00:54]   Checking for kernel symbol 'find_sys_call_tbl'  [ Not found ]
[05:00:54] IntoXonia-NG Rootkit                              [ Not found ]
[05:00:54]
[05:00:54] Checking for Irix Rootkit...
[05:00:54]   Checking for directory '/dev/pts/01'            [ Not found ]
[05:00:54]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[05:00:54]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[05:00:55]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[05:00:55] Irix Rootkit                                      [ Not found ]
[05:00:55]
[05:00:55] Checking for Jynx Rootkit...
[05:00:55]   Checking for file '/xochikit/bc'                [ Not found ]
[05:00:55]   Checking for file '/xochikit/ld_poison.so'      [ Not found ]
[05:00:55]   Checking for file '/omgxochi/bc'                [ Not found ]
[05:00:55]   Checking for file '/omgxochi/ld_poison.so'      [ Not found ]
[05:00:55]   Checking for file '/var/local/^^/bc'            [ Not found ]
[05:00:55]   Checking for file '/var/local/^^/ld_poison.so'  [ Not found ]
[05:00:55]   Checking for directory '/xochikit'              [ Not found ]
[05:00:55]   Checking for directory '/omgxochi'              [ Not found ]
[05:00:55]   Checking for directory '/var/local/^^'          [ Not found ]
[05:00:55] Jynx Rootkit                                      [ Not found ]
[05:00:55]
[05:00:55] Checking for KBeast Rootkit...
[05:00:55]   Checking for file '/usr/_h4x_/ipsecs-kbeast-v1.ko' [ Not found ]
[05:00:55]   Checking for file '/usr/_h4x_/_h4x_bd'          [ Not found ]
[05:00:55]   Checking for file '/usr/_h4x_/acctlog'          [ Not found ]
[05:00:55]   Checking for directory '/usr/_h4x_'             [ Not found ]
[05:00:55]   Checking for kernel symbol 'h4x_delete_module'  [ Not found ]
[05:00:55]   Checking for kernel symbol 'h4x_getdents64'     [ Not found ]
[05:00:55]   Checking for kernel symbol 'h4x_kill'           [ Not found ]
[05:00:55]   Checking for kernel symbol 'h4x_open'           [ Not found ]
[05:00:55]   Checking for kernel symbol 'h4x_read'           [ Not found ]
[05:00:55]   Checking for kernel symbol 'h4x_rename'         [ Not found ]
[05:00:55]   Checking for kernel symbol 'h4x_rmdir'          [ Not found ]
[05:00:55]   Checking for kernel symbol 'h4x_tcp4_seq_show'  [ Not found ]
[05:00:56]   Checking for kernel symbol 'h4x_write'          [ Not found ]
[05:00:56] KBeast Rootkit                                    [ Not found ]
[05:00:56]
[05:00:56] Checking for Kitko Rootkit...
[05:00:56]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[05:00:56] Kitko Rootkit                                     [ Not found ]
[05:00:56]
[05:00:56] Checking for Knark Rootkit...
[05:00:56]   Checking for file '/proc/knark/pids'            [ Not found ]
[05:00:56]   Checking for directory '/proc/knark'            [ Not found ]
[05:00:56] Knark Rootkit                                     [ Not found ]
[05:00:56]
[05:00:56] Checking for ld-linuxv.so Rootkit...
[05:00:56]   Checking for file '/lib/ld-linuxv.so.1'         [ Not found ]
[05:00:56]   Checking for directory '/var/opt/_so_cache'     [ Not found ]
[05:00:56]   Checking for directory '/var/opt/_so_cache/ld'  [ Not found ]
[05:00:56]   Checking for directory '/var/opt/_so_cache/lc'  [ Not found ]
[05:00:56] ld-linuxv.so Rootkit                              [ Not found ]
[05:00:56]
[05:00:56] Checking for Li0n Worm...
[05:00:56]   Checking for file '/bin/in.telnetd'             [ Not found ]
[05:00:56]   Checking for file '/bin/mjy'                    [ Not found ]
[05:00:56]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[05:00:56]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[05:00:56]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[05:00:56]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[05:00:56]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[05:00:56]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[05:00:56]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[05:00:56]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[05:00:56]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[05:00:56]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[05:00:56]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[05:00:56]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[05:00:56]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[05:00:56]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[05:00:56]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[05:00:56]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[05:00:56]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[05:00:56]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[05:00:56] Li0n Worm                                         [ Not found ]
[05:00:56]
[05:00:56] Checking for Lockit / LJK2 Rootkit...
[05:00:56]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[05:00:56]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[05:00:56]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[05:00:56]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[05:00:56]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[05:00:56]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[05:00:56]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parse' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[05:00:57]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[05:00:57]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[05:00:57] Lockit / LJK2 Rootkit                             [ Not found ]
[05:00:57]
[05:00:57] Checking for Mood-NT Rootkit...
[05:00:57]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[05:00:57]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[05:00:57]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[05:00:57]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[05:00:57]   Checking for directory '/_cthulhu'              [ Not found ]
[05:00:57] Mood-NT Rootkit                                   [ Not found ]
[05:00:57]
[05:00:57] Checking for MRK Rootkit...
[05:00:57]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[05:00:57]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[05:00:57]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[05:00:57]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[05:00:57]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[05:00:57]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[05:00:57] MRK Rootkit                                       [ Not found ]
[05:00:57]
[05:00:57] Checking for Ni0 Rootkit...
[05:00:57]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[05:00:57]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[05:00:58]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[05:00:58]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[05:00:58]   Checking for directory '/tmp/waza'              [ Not found ]
[05:00:58]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[05:00:58]   Checking for directory '/usr/sbin/es'           [ Not found ]
[05:00:58] Ni0 Rootkit                                       [ Not found ]
[05:00:58]
[05:00:58] Checking for Ohhara Rootkit...
[05:00:58]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[05:00:58]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[05:00:58]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[05:00:58]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[05:00:58]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[05:00:58]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[05:00:58]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[05:00:58] Ohhara Rootkit                                    [ Not found ]
[05:00:58]
[05:00:58] Checking for Optic Kit (Tux) Worm...
[05:00:58]   Checking for directory '/dev/tux'               [ Not found ]
[05:00:58]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[05:00:58]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[05:00:58]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[05:00:58] Optic Kit (Tux) Worm                              [ Not found ]
[05:00:58]
[05:00:58] Checking for Oz Rootkit...
[05:00:58]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[05:00:58]   Checking for directory '/dev/.oz'               [ Not found ]
[05:00:58] Oz Rootkit                                        [ Not found ]
[05:00:58]
[05:00:58] Checking for Phalanx Rootkit...
[05:00:58]   Checking for file '/uNFuNF'                     [ Not found ]
[05:00:58]   Checking for file '/etc/host.ph1'               [ Not found ]
[05:00:58]   Checking for file '/bin/host.ph1'               [ Not found ]
[05:00:58]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[05:00:58]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[05:00:58]   Checking for file '/usr/share/.home.ph1/kebab'  [ Not found ]
[05:00:58]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[05:00:58]   Checking for directory '/usr/share/.home.ph1/tty' [ Not found ]
[05:00:58] Phalanx Rootkit                                   [ Not found ]
[05:00:58]
[05:00:58] Checking for Phalanx2 Rootkit...
[05:00:58]   Checking for file '/etc/khubd.p2/.p2rc'         [ Not found ]
[05:00:58]   Checking for file '/etc/khubd.p2/.phalanx2'     [ Not found ]
[05:00:58]   Checking for file '/etc/khubd.p2/.sniff'        [ Not found ]
[05:00:58]   Checking for file '/etc/khubd.p2/sshgrab.py'    [ Not found ]
[05:00:58]   Checking for file '/etc/lolzz.p2/.p2rc'         [ Not found ]
[05:00:58]   Checking for file '/etc/lolzz.p2/.phalanx2'     [ Not found ]
[05:00:58]   Checking for file '/etc/lolzz.p2/.sniff'        [ Not found ]
[05:00:58]   Checking for file '/etc/lolzz.p2/sshgrab.py'    [ Not found ]
[05:00:58]   Checking for file '/etc/cron.d/zupzzplaceholder' [ Not found ]
[05:00:58]   Checking for file '/usr/lib/zupzz.p2/.p-2.3d'   [ Not found ]
[05:00:58]   Checking for file '/usr/lib/zupzz.p2/.p2rc'     [ Not found ]
[05:00:58]   Checking for directory '/etc/khubd.p2'          [ Not found ]
[05:00:59]   Checking for directory '/etc/lolzz.p2'          [ Not found ]
[05:00:59]   Checking for directory '/usr/lib/zupzz.p2'      [ Not found ]
[05:00:59] Phalanx2 Rootkit                                  [ Not found ]
[05:00:59]
[05:00:59] Checking for Phalanx2 Rootkit (extended tests)...
[05:00:59]   Checking for directory '/etc/khubd.p2'          [ Not found ]
[05:00:59]   Checking for directory '/etc/lolzz.p2'          [ Not found ]
[05:00:59]   Checking for directory '/usr/lib/zupzz.p2'      [ Not found ]
[05:00:59] Phalanx2 Rootkit (extended tests)                 [ Not found ]
[05:00:59]
[05:00:59] Checking for Portacelo Rootkit...
[05:00:59]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[05:00:59]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[05:00:59]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[05:00:59]   Checking for file '/var/lib/.../.p'             [ Not found ]
[05:00:59]   Checking for file '/var/lib/.../getty'          [ Not found ]
[05:00:59]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[05:00:59]   Checking for file '/var/lib/.../show'           [ Not found ]
[05:00:59]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[05:00:59]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[05:00:59]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[05:00:59]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[05:00:59]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[05:00:59]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[05:00:59] Portacelo Rootkit                                 [ Not found ]
[05:00:59]
[05:00:59] Checking for R3dstorm Toolkit...
[05:00:59]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[05:00:59]   Checking for file '/var/log/tk02/.scris'        [ Not found ]
[05:00:59]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[05:00:59]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[05:00:59]   Checking for file '/bin/.../see_all'            [ Not found ]
[05:00:59]   Checking for directory '/var/log/tk02'          [ Not found ]
[05:00:59]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[05:00:59]   Checking for directory '/bin/...'               [ Not found ]
[05:00:59] R3dstorm Toolkit                                  [ Not found ]
[05:00:59]
[05:00:59] Checking for RH-Sharpe's Rootkit...
[05:00:59]   Checking for file '/bin/lps'                    [ Not found ]
[05:00:59]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[05:00:59]   Checking for file '/usr/bin/ltop'               [ Not found ]
[05:00:59]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[05:00:59]   Checking for file '/usr/bin/ldu'                [ Not found ]
[05:00:59]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[05:00:59]   Checking for file '/usr/bin/wp'                 [ Not found ]
[05:00:59]   Checking for file '/usr/bin/shad'               [ Not found ]
[05:00:59]   Checking for file '/usr/bin/vadim'              [ Not found ]
[05:00:59]   Checking for file '/usr/bin/slice'              [ Not found ]
[05:00:59]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[05:01:00]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[05:01:00] RH-Sharpe's Rootkit                               [ Not found ]
[05:01:00]
[05:01:00] Checking for RSHA's Rootkit...
[05:01:00]   Checking for file '/bin/kr4p'                   [ Not found ]
[05:01:00]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[05:01:00]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[05:01:00]   Checking for file '/usr/bin/slice2'             [ Not found ]
[05:01:00]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[05:01:00]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[05:01:00]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[05:01:00]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[05:01:00] RSHA's Rootkit                                    [ Not found ]
[05:01:00]
[05:01:00] Checking for Scalper Worm...
[05:01:00]   Checking for file '/tmp/.a'                     [ Not found ]
[05:01:00]   Checking for file '/tmp/.uua'                   [ Not found ]
[05:01:00] Scalper Worm                                      [ Not found ]
[05:01:00]
[05:01:00] Checking for Sebek LKM...
[05:01:00]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[05:01:00] Sebek LKM                                         [ Not found ]
[05:01:00]
[05:01:00] Checking for Shutdown Rootkit...
[05:01:00]   Checking for file '/usr/man/man5/..<SP>/.dir/scannah/asus' [ Not found ]
[05:01:00]   Checking for file '/usr/man/man5/..<SP>/.dir/see' [ Not found ]
[05:01:00]   Checking for file '/usr/man/man5/..<SP>/.dir/nscd' [ Not found ]
[05:01:00]   Checking for file '/usr/man/man5/..<SP>/.dir/alpd' [ Not found ]
[05:01:00]   Checking for file '/etc/rc.d/rc.local<SP>'      [ Not found ]
[05:01:00]   Checking for directory '/usr/man/man5/..<SP>/.dir' [ Not found ]
[05:01:00]   Checking for directory '/usr/man/man5/..<SP>/.dir/scannah' [ Not found ]
[05:01:00]   Checking for directory '/etc/rc.d/rc0.d/..<SP>/.dir' [ Not found ]
[05:01:00] Shutdown Rootkit                                  [ Not found ]
[05:01:00]
[05:01:00] Checking for SHV4 Rootkit...
[05:01:00]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[05:01:00]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[05:01:00]   Checking for file '/lib/lidps1.so'              [ Not found ]
[05:01:00]   Checking for file '/lib/libproc.a'              [ Not found ]
[05:01:00]   Checking for file '/lib/libproc.so.2.0.6'       [ Not found ]
[05:01:00]   Checking for file '/lib/ldd.so/tks'             [ Not found ]
[05:01:00]   Checking for file '/lib/ldd.so/tkp'             [ Not found ]
[05:01:00]   Checking for file '/lib/ldd.so/tksb'            [ Not found ]
[05:01:00]   Checking for file '/lib/security/.config/sshd'  [ Not found ]
[05:01:00]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[05:01:00]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[05:01:00]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[05:01:00]   Checking for file '/usr/include/file.h'         [ Not found ]
[05:01:00]   Checking for file '/usr/include/hosts.h'        [ Not found ]
[05:01:00]   Checking for file '/usr/include/lidps1.so'      [ Not found ]
[05:01:01]   Checking for file '/usr/include/log.h'          [ Not found ]
[05:01:01]   Checking for file '/usr/include/proc.h'         [ Not found ]
[05:01:01]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[05:01:01]   Checking for file '/dev/srd0'                   [ Not found ]
[05:01:01]   Checking for directory '/lib/ldd.so'            [ Not found ]
[05:01:01]   Checking for directory '/lib/security/.config'  [ Not found ]
[05:01:01]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[05:01:01] SHV4 Rootkit                                      [ Not found ]
[05:01:01]
[05:01:01] Checking for SHV5 Rootkit...
[05:01:01]   Checking for file '/etc/sh.conf'                [ Not found ]
[05:01:01]   Checking for file '/lib/libproc.a'              [ Not found ]
[05:01:01]   Checking for file '/lib/libproc.so.2.0.6'       [ Not found ]
[05:01:01]   Checking for file '/lib/lidps1.so'              [ Not found ]
[05:01:01]   Checking for file '/lib/libsh.so/bash'          [ Not found ]
[05:01:01]   Checking for file '/usr/include/file.h'         [ Not found ]
[05:01:01]   Checking for file '/usr/include/hosts.h'        [ Not found ]
[05:01:01]   Checking for file '/usr/include/log.h'          [ Not found ]
[05:01:01]   Checking for file '/usr/include/proc.h'         [ Not found ]
[05:01:01]   Checking for file '/lib/libsh.so/shdcf2'        [ Not found ]
[05:01:01]   Checking for file '/lib/libsh.so/shhk'          [ Not found ]
[05:01:01]   Checking for file '/lib/libsh.so/shhk.pub'      [ Not found ]
[05:01:01]   Checking for file '/lib/libsh.so/shrs'          [ Not found ]
[05:01:01]   Checking for file '/usr/lib/libsh/.bashrc'      [ Not found ]
[05:01:01]   Checking for file '/usr/lib/libsh/shsb'         [ Not found ]
[05:01:01]   Checking for file '/usr/lib/libsh/hide'         [ Not found ]
[05:01:01]   Checking for file '/usr/lib/libsh/.sniff/shsniff' [ Not found ]
[05:01:01]   Checking for file '/usr/lib/libsh/.sniff/shp'   [ Not found ]
[05:01:01]   Checking for file '/dev/srd0'                   [ Not found ]
[05:01:01]   Checking for directory '/lib/libsh.so'          [ Not found ]
[05:01:01]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[05:01:01]   Checking for directory '/usr/lib/libsh/utilz'   [ Not found ]
[05:01:01]   Checking for directory '/usr/lib/libsh/.backup' [ Not found ]
[05:01:01] SHV5 Rootkit                                      [ Not found ]
[05:01:01]
[05:01:01] Checking for Sin Rootkit...
[05:01:01]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[05:01:01]   Checking for file '/dev/ttyoa'                  [ Not found ]
[05:01:01]   Checking for file '/dev/ttyof'                  [ Not found ]
[05:01:01]   Checking for file '/dev/ttyop'                  [ Not found ]
[05:01:01]   Checking for file '/dev/ttyos'                  [ Not found ]
[05:01:01]   Checking for file '/usr/lib/.lib'               [ Not found ]
[05:01:01]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[05:01:01]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[05:01:01]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[05:01:01]   Checking for file '/usr/man/man1/...'           [ Not found ]
[05:01:01]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[05:01:01]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[05:01:02]   Checking for directory '/usr/lib/sn'            [ Not found ]
[05:01:02]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[05:01:02]   Checking for directory '/dev/.haos'             [ Not found ]
[05:01:02] Sin Rootkit                                       [ Not found ]
[05:01:02]
[05:01:02] Checking for Slapper Worm...
[05:01:02]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[05:01:02]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[05:01:02]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[05:01:02]   Checking for file '/tmp/httpd'                  [ Not found ]
[05:01:02]   Checking for file '/tmp/.unlock'                [ Not found ]
[05:01:02]   Checking for file '/tmp/update'                 [ Not found ]
[05:01:02]   Checking for file '/tmp/.cinik'                 [ Not found ]
[05:01:02]   Checking for file '/tmp/.b'                     [ Not found ]
[05:01:02] Slapper Worm                                      [ Not found ]
[05:01:02]
[05:01:02] Checking for Sneakin Rootkit...
[05:01:02]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[05:01:02] Sneakin Rootkit                                   [ Not found ]
[05:01:02]
[05:01:02] Checking for 'Spanish' Rootkit...
[05:01:02]   Checking for file '/dev/ptyq'                   [ Not found ]
[05:01:02]   Checking for file '/bin/ad'                     [ Not found ]
[05:01:02]   Checking for file '/bin/ava'                    [ Not found ]
[05:01:02]   Checking for file '/bin/server'                 [ Not found ]
[05:01:02]   Checking for file '/usr/sbin/rescue'            [ Not found ]
[05:01:02]   Checking for file '/usr/share/.../chrps'        [ Not found ]
[05:01:02]   Checking for file '/usr/share/.../chrifconfig'  [ Not found ]
[05:01:02]   Checking for file '/usr/share/.../netstat'      [ Not found ]
[05:01:02]   Checking for file '/usr/share/.../linsniffer'   [ Not found ]
[05:01:02]   Checking for file '/usr/share/.../charbd'       [ Not found ]
[05:01:02]   Checking for file '/usr/share/.../charbd2'      [ Not found ]
[05:01:02]   Checking for file '/usr/share/.../charbd3'      [ Not found ]
[05:01:02]   Checking for file '/usr/share/.../charbd4'      [ Not found ]
[05:01:02]   Checking for file '/usr/man/tmp/update.tgz'     [ Not found ]
[05:01:02]   Checking for file '/var/lib/rpm/db.rpm'         [ Not found ]
[05:01:02]   Checking for file '/var/cache/man/.cat'         [ Not found ]
[05:01:02]   Checking for file '/var/spool/lpd/remote/.lpq'  [ Not found ]
[05:01:02]   Checking for directory '/usr/share/...'         [ Not found ]
[05:01:02] 'Spanish' Rootkit                                 [ Not found ]
[05:01:02]
[05:01:02] Checking for Suckit Rootkit...
[05:01:02]   Checking for file '/sbin/initsk12'              [ Not found ]
[05:01:02]   Checking for file '/sbin/initxrk'               [ Not found ]
[05:01:02]   Checking for file '/usr/bin/null'               [ Not found ]
[05:01:02]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[05:01:02]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[05:01:02]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[05:01:02]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[05:01:02]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[05:01:02]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[05:01:03]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[05:01:03]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[05:01:03]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[05:01:03]   Checking for directory '/etc/.MG'               [ Not found ]
[05:01:03]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[05:01:03]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[05:01:03] Suckit Rootkit                                    [ Not found ]
[05:01:03]
[05:01:03] Checking for Superkit Rootkit...
[05:01:03]   Checking for file '/usr/man/.sman/sk/backsh'    [ Not found ]
[05:01:03]   Checking for file '/usr/man/.sman/sk/izbtrag'   [ Not found ]
[05:01:03]   Checking for file '/usr/man/.sman/sk/sksniff'   [ Not found ]
[05:01:03]   Checking for file '/var/www/cgi-bin/cgiback.cgi' [ Not found ]
[05:01:03]   Checking for directory '/usr/man/.sman/sk'      [ Not found ]
[05:01:03] Superkit Rootkit                                  [ Not found ]
[05:01:03]
[05:01:03] Checking for TBD (Telnet BackDoor)...
[05:01:03]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[05:01:03] TBD (Telnet BackDoor)                             [ Not found ]
[05:01:03]
[05:01:03] Checking for TeLeKiT Rootkit...
[05:01:03]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[05:01:03]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[05:01:03]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[05:01:03]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[05:01:03]   Checking for file '/dev/ptyr'                   [ Not found ]
[05:01:03]   Checking for file '/dev/ptyp'                   [ Not found ]
[05:01:03]   Checking for file '/dev/ptyq'                   [ Not found ]
[05:01:03]   Checking for file '/dev/hda06'                  [ Not found ]
[05:01:03]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[05:01:03]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[05:01:03]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[05:01:03]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[05:01:03] TeLeKiT Rootkit                                   [ Not found ]
[05:01:03]
[05:01:03] Checking for T0rn Rootkit...
[05:01:03]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[05:01:03]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[05:01:03]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[05:01:03]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[05:01:03]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[05:01:03]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[05:01:03]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[05:01:03]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[05:01:03]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[05:01:03]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[05:01:03]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[05:01:03]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[05:01:03]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[05:01:03]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[05:01:04]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[05:01:04]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[05:01:04]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[05:01:04]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[05:01:04]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[05:01:04]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[05:01:04]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[05:01:04]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[05:01:04]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[05:01:04]   Checking for file '/usr/src/.puta/.1addr'       [ Not found ]
[05:01:04]   Checking for file '/usr/src/.puta/.1file'       [ Not found ]
[05:01:04]   Checking for file '/usr/src/.puta/.1proc'       [ Not found ]
[05:01:04]   Checking for file '/usr/src/.puta/.1logz'       [ Not found ]
[05:01:04]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[05:01:04]   Checking for directory '/dev/.lib'              [ Not found ]
[05:01:04]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[05:01:04]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[05:01:04]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[05:01:04]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[05:01:04]   Checking for directory '/usr/src/.puta'         [ Not found ]
[05:01:04]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[05:01:04]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[05:01:04]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[05:01:04]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[05:01:04] T0rn Rootkit                                      [ Not found ]
[05:01:04]
[05:01:04] Checking for trNkit Rootkit...
[05:01:04]   Checking for file '/usr/lib/libbins.la'         [ Not found ]
[05:01:04]   Checking for file '/usr/lib/libtcs.so'          [ Not found ]
[05:01:04]   Checking for file '/dev/.ttpy/ulogin.sh'        [ Not found ]
[05:01:04]   Checking for file '/dev/.ttpy/tcpshell.sh'      [ Not found ]
[05:01:04]   Checking for file '/dev/.ttpy/bupdu'            [ Not found ]
[05:01:04]   Checking for file '/dev/.ttpy/buloc'            [ Not found ]
[05:01:04]   Checking for file '/dev/.ttpy/buloc1'           [ Not found ]
[05:01:04]   Checking for file '/dev/.ttpy/buloc2'           [ Not found ]
[05:01:04]   Checking for file '/dev/.ttpy/stat'             [ Not found ]
[05:01:04]   Checking for file '/dev/.ttpy/backps'           [ Not found ]
[05:01:04]   Checking for file '/dev/.ttpy/tree'             [ Not found ]
[05:01:04]   Checking for file '/dev/.ttpy/topk'             [ Not found ]
[05:01:04]   Checking for file '/dev/.ttpy/wold'             [ Not found ]
[05:01:04]   Checking for file '/dev/.ttpy/whoold'           [ Not found ]
[05:01:04]   Checking for file '/dev/.ttpy/backdoors'        [ Not found ]
[05:01:04] trNkit Rootkit                                    [ Not found ]
[05:01:04]
[05:01:04] Checking for Trojanit Kit...
[05:01:04]   Checking for file '/bin/.ls'                    [ Not found ]
[05:01:05]   Checking for file '/bin/.ps'                    [ Not found ]
[05:01:05]   Checking for file '/bin/.netstat'               [ Not found ]
[05:01:05]   Checking for file '/usr/bin/.nop'               [ Not found ]
[05:01:05]   Checking for file '/usr/bin/.who'               [ Not found ]
[05:01:05] Trojanit Kit                                      [ Not found ]
[05:01:05]
[05:01:05] Checking for Tuxtendo Rootkit...
[05:01:05]   Checking for file '/lib/libproc.so.2.0.7'       [ Not found ]
[05:01:05]   Checking for file '/usr/bin/xchk'               [ Not found ]
[05:01:05]   Checking for file '/usr/bin/xsf'                [ Not found ]
[05:01:05]   Checking for file '/dev/tux/suidsh'             [ Not found ]
[05:01:05]   Checking for file '/dev/tux/.addr'              [ Not found ]
[05:01:05]   Checking for file '/dev/tux/.cron'              [ Not found ]
[05:01:05]   Checking for file '/dev/tux/.file'              [ Not found ]
[05:01:05]   Checking for file '/dev/tux/.log'               [ Not found ]
[05:01:05]   Checking for file '/dev/tux/.proc'              [ Not found ]
[05:01:05]   Checking for file '/dev/tux/.iface'             [ Not found ]
[05:01:05]   Checking for file '/dev/tux/.pw'                [ Not found ]
[05:01:05]   Checking for file '/dev/tux/.df'                [ Not found ]
[05:01:05]   Checking for file '/dev/tux/.ssh'               [ Not found ]
[05:01:05]   Checking for file '/dev/tux/.tux'               [ Not found ]
[05:01:05]   Checking for file '/dev/tux/ssh2/sshd2_config'  [ Not found ]
[05:01:05]   Checking for file '/dev/tux/ssh2/hostkey'       [ Not found ]
[05:01:05]   Checking for file '/dev/tux/ssh2/hostkey.pub'   [ Not found ]
[05:01:05]   Checking for file '/dev/tux/ssh2/logo'          [ Not found ]
[05:01:05]   Checking for file '/dev/tux/ssh2/random_seed'   [ Not found ]
[05:01:05]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[05:01:05]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[05:01:05]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[05:01:05]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[05:01:05]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[05:01:05]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[05:01:05]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[05:01:05]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[05:01:05]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[05:01:05]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[05:01:05]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[05:01:05]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[05:01:05]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[05:01:05]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[05:01:05]   Checking for directory '/dev/tux'               [ Not found ]
[05:01:05]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[05:01:05]   Checking for directory '/dev/tux/backup'        [ Not found ]
[05:01:05] Tuxtendo Rootkit                                  [ Not found ]
[05:01:05]
[05:01:05] Checking for URK Rootkit...
[05:01:05]   Checking for file '/dev/prom/sn.l'              [ Not found ]
[05:01:05]   Checking for file '/usr/lib/ldlibps.so'         [ Not found ]
[05:01:06]   Checking for file '/usr/lib/ldlibnet.so'        [ Not found ]
[05:01:06]   Checking for file '/dev/pts/01/uconf.inv'       [ Not found ]
[05:01:06]   Checking for file '/dev/pts/01/cleaner'         [ Not found ]
[05:01:06]   Checking for file '/dev/pts/01/bin/psniff'      [ Not found ]
[05:01:06]   Checking for file '/dev/pts/01/bin/du'          [ Not found ]
[05:01:06]   Checking for file '/dev/pts/01/bin/ls'          [ Not found ]
[05:01:06]   Checking for file '/dev/pts/01/bin/passwd'      [ Not found ]
[05:01:06]   Checking for file '/dev/pts/01/bin/ps'          [ Not found ]
[05:01:06]   Checking for file '/dev/pts/01/bin/psr'         [ Not found ]
[05:01:06]   Checking for file '/dev/pts/01/bin/su'          [ Not found ]
[05:01:06]   Checking for file '/dev/pts/01/bin/find'        [ Not found ]
[05:01:06]   Checking for file '/dev/pts/01/bin/netstat'     [ Not found ]
[05:01:06]   Checking for file '/dev/pts/01/bin/ping'        [ Not found ]
[05:01:06]   Checking for file '/dev/pts/01/bin/strings'     [ Not found ]
[05:01:06]   Checking for file '/dev/pts/01/bin/bash'        [ Not found ]
[05:01:06]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[05:01:06]   Checking for file '/usr/man/man1/xxxxxxbin/ls'  [ Not found ]
[05:01:06]   Checking for file '/usr/man/man1/xxxxxxbin/passwd' [ Not found ]
[05:01:06]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[05:01:06]   Checking for file '/usr/man/man1/xxxxxxbin/psr' [ Not found ]
[05:01:06]   Checking for file '/usr/man/man1/xxxxxxbin/su'  [ Not found ]
[05:01:06]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[05:01:06]   Checking for file '/usr/man/man1/xxxxxxbin/netstat' [ Not found ]
[05:01:06]   Checking for file '/usr/man/man1/xxxxxxbin/ping' [ Not found ]
[05:01:06]   Checking for file '/usr/man/man1/xxxxxxbin/strings' [ Not found ]
[05:01:06]   Checking for file '/usr/man/man1/xxxxxxbin/bash' [ Not found ]
[05:01:06]   Checking for file '/tmp/conf.inv'               [ Not found ]
[05:01:06]   Checking for directory '/dev/prom'              [ Not found ]
[05:01:06]   Checking for directory '/dev/pts/01'            [ Not found ]
[05:01:06]   Checking for directory '/dev/pts/01/bin'        [ Not found ]
[05:01:06]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[05:01:06] URK Rootkit                                       [ Not found ]
[05:01:06]
[05:01:06] Checking for Vampire Rootkit...
[05:01:06]   Checking for kernel symbol 'new_getdents'       [ Not found ]
[05:01:06]   Checking for kernel symbol 'old_getdents'       [ Not found ]
[05:01:06]   Checking for kernel symbol 'should_hide_file_name' [ Not found ]
[05:01:07]   Checking for kernel symbol 'should_hide_task_name' [ Not found ]
[05:01:07] Vampire Rootkit                                   [ Not found ]
[05:01:07]
[05:01:07] Checking for VcKit Rootkit...
[05:01:07]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[05:01:07]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[05:01:07] VcKit Rootkit                                     [ Not found ]
[05:01:07]
[05:01:07] Checking for Volc Rootkit...
[05:01:07]   Checking for file '/usr/bin/volc'               [ Not found ]
[05:01:07]   Checking for file '/usr/lib/volc/backdoor/divine' [ Not found ]
[05:01:07]   Checking for file '/usr/lib/volc/linsniff'      [ Not found ]
[05:01:07]   Checking for file '/etc/rc.d/rc1.d/S25sysconf'  [ Not found ]
[05:01:07]   Checking for file '/etc/rc.d/rc2.d/S25sysconf'  [ Not found ]
[05:01:07]   Checking for file '/etc/rc.d/rc3.d/S25sysconf'  [ Not found ]
[05:01:07]   Checking for file '/etc/rc.d/rc4.d/S25sysconf'  [ Not found ]
[05:01:07]   Checking for file '/etc/rc.d/rc5.d/S25sysconf'  [ Not found ]
[05:01:07]   Checking for directory '/var/spool/.recent'     [ Not found ]
[05:01:07]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[05:01:07]   Checking for directory '/usr/lib/volc'          [ Not found ]
[05:01:07]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[05:01:07] Volc Rootkit                                      [ Not found ]
[05:01:07]
[05:01:07] Checking for Xzibit Rootkit...
[05:01:07]   Checking for file '/dev/dsx'                    [ Not found ]
[05:01:07]   Checking for file '/dev/caca'                   [ Not found ]
[05:01:07]   Checking for file '/dev/ida/.inet/linsniffer'   [ Not found ]
[05:01:07]   Checking for file '/dev/ida/.inet/logclear'     [ Not found ]
[05:01:07]   Checking for file '/dev/ida/.inet/sense'        [ Not found ]
[05:01:07]   Checking for file '/dev/ida/.inet/sl2'          [ Not found ]
[05:01:07]   Checking for file '/dev/ida/.inet/sshdu'        [ Not found ]
[05:01:07]   Checking for file '/dev/ida/.inet/s'            [ Not found ]
[05:01:07]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[05:01:07]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[05:01:07]   Checking for file '/dev/ida/.inet/sl2new.c'     [ Not found ]
[05:01:07]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[05:01:07]   Checking for file '/home/httpd/cgi-bin/becys.cgi' [ Not found ]
[05:01:07]   Checking for file '/usr/local/httpd/cgi-bin/becys.cgi' [ Not found ]
[05:01:07]   Checking for file '/usr/local/apache/cgi-bin/becys.cgi' [ Not found ]
[05:01:07]   Checking for file '/www/httpd/cgi-bin/becys.cgi' [ Not found ]
[05:01:07]   Checking for file '/www/cgi-bin/becys.cgi'      [ Not found ]
[05:01:07]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[05:01:07] Xzibit Rootkit                                    [ Not found ]
[05:01:07]
[05:01:07] Checking for zaRwT.KiT Rootkit...
[05:01:07]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[05:01:07]   Checking for file '/dev/ttyf'                   [ Not found ]
[05:01:07]   Checking for file '/dev/ttyp'                   [ Not found ]
[05:01:07]   Checking for file '/dev/ttyn'                   [ Not found ]
[05:01:08]   Checking for file '/rk/tulz'                    [ Not found ]
[05:01:08]   Checking for directory '/rk'                    [ Not found ]
[05:01:08]   Checking for directory '/dev/rd/s'              [ Not found ]
[05:01:08] zaRwT.KiT Rootkit                                 [ Not found ]
[05:01:08]
[05:01:08] Checking for ZK Rootkit...
[05:01:08]   Checking for file '/usr/share/.zk/zk'           [ Not found ]
[05:01:08]   Checking for file '/usr/X11R6/.zk/xfs'          [ Not found ]
[05:01:08]   Checking for file '/usr/X11R6/.zk/echo'         [ Not found ]
[05:01:08]   Checking for file '/etc/1ssue.net'              [ Not found ]
[05:01:08]   Checking for file '/etc/sysconfig/console/load.zk' [ Not found ]
[05:01:08]   Checking for directory '/usr/share/.zk'         [ Not found ]
[05:01:08]   Checking for directory '/usr/X11R6/.zk'         [ Not found ]
[05:01:08] ZK Rootkit                                        [ Not found ]
[05:01:08]
[05:01:08] Info: Starting test name 'additional_rkts'
[05:01:08] Performing additional rootkit checks
[05:01:08]
[05:01:08]   Performing Suckit Rookit additional checks
[05:01:08]     Checking hard link count on '/sbin/init'      [ OK ]
[05:01:08]     Checking for hidden file extensions           [ None found ]
[05:01:08]     Running skdet command                         [ Skipped ]
[05:01:08] Info: Unable to find the 'skdet' command
[05:01:08]   Suckit Rookit additional checks                 [ OK ]
[05:01:08]
[05:01:08] Info: Starting test name 'possible_rkt_files'
[05:01:08]   Performing check of possible rootkit files and directories
[05:01:08]     Checking for file '/dev/sdr0'                 [ Not found ]
[05:01:08]     Checking for file '/dev/pisu'                 [ Not found ]
[05:01:08]     Checking for file '/dev/xdta'                 [ Not found ]
[05:01:08]     Checking for file '/dev/saux'                 [ Not found ]
[05:01:08]     Checking for file '/dev/hdx'                  [ Not found ]
[05:01:08]     Checking for file '/dev/hdx1'                 [ Not found ]
[05:01:08]     Checking for file '/dev/hdx2'                 [ Not found ]
[05:01:08]     Checking for file '/dev/ptyy'                 [ Not found ]
[05:01:08]     Checking for file '/dev/ptyu'                 [ Not found ]
[05:01:08]     Checking for file '/dev/ptyv'                 [ Not found ]
[05:01:08]     Checking for file '/dev/hdbb'                 [ Not found ]
[05:01:08]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[05:01:08]     Checking for file '/tmp/.bash_history'        [ Not found ]
[05:01:08]     Checking for file '/usr/info/.clib'           [ Not found ]
[05:01:08]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[05:01:08]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[05:01:08]     Checking for file '/sbin/create'              [ Not found ]
[05:01:09]     Checking for file '/dev/ttypz'                [ Not found ]
[05:01:09]     Checking for file '/var/log/tcp.log'          [ Not found ]
[05:01:09]     Checking for file '/usr/include/audit.h'      [ Not found ]
[05:01:09]     Checking for file '/usr/bin/sourcemask'       [ Not found ]
[05:01:09]     Checking for file '/usr/bin/ras2xm'           [ Not found ]
[05:01:09]     Checking for file '/dev/xmx'                  [ Not found ]
[05:01:09]     Checking for file '/usr/sbin/gpm.root'        [ Not found ]
[05:01:09]     Checking for file '/bin/vobiscum'             [ Not found ]
[05:01:09]     Checking for file '/bin/psr'                  [ Not found ]
[05:01:09]     Checking for file '/dev/kdx'                  [ Not found ]
[05:01:09]     Checking for file '/dev/dkx'                  [ Not found ]
[05:01:09]     Checking for file '/usr/sbin/sshd3'           [ Not found ]
[05:01:09]     Checking for file '/usr/sbin/jcd'             [ Not found ]
[05:01:09]     Checking for file '/etc/rc.d/init.d/jcd'      [ Not found ]
[05:01:09]     Checking for file '/usr/sbin/atd2'            [ Not found ]
[05:01:09]     Checking for file '/home/httpd/cgi-bin/linux.cgi' [ Not found ]
[05:01:09]     Checking for file '/home/httpd/cgi-bin/psid'  [ Not found ]
[05:01:09]     Checking for file '/home/httpd/cgi-bin/void.cgi' [ Not found ]
[05:01:09]     Checking for file '/etc/rc.d/init.d/system'   [ Not found ]
[05:01:09]     Checking for file '/etc/rc.d/rc3.d/S93users'  [ Not found ]
[05:01:09]     Checking for file '/tmp/.ush'                 [ Not found ]
[05:01:09]     Checking for file '/usr/lib/libhidefile.so'   [ Not found ]
[05:01:09]     Checking for file '/etc/cron.d/kmod'          [ Not found ]
[05:01:09]     Checking for file '/usr/lib/dmis/dmisd'       [ Not found ]
[05:01:09]     Checking for file '/lib/secure/libhij.so'     [ Not found ]
[05:01:09]     Checking for file '/usr/sbin/sshd3'           [ Not found ]
[05:01:09]     Checking for file '/etc/rc.d/init.d/crontab'  [ Not found ]
[05:01:09]     Checking for file '/etc/rc.d/init.d/jcd'      [ Not found ]
[05:01:09]     Checking for file '/usr/sbin/atd2'            [ Not found ]
[05:01:09]     Checking for file '/etc/rc.d/rc5.d/S93users'  [ Not found ]
[05:01:09]     Checking for file '/usr/include/mysql/mysql.hh1' [ Not found ]
[05:01:09]     Checking for file '/etc/init.d/xfs3'          [ Not found ]
[05:01:09]     Checking for file '/usr/sbin/t.txt'           [ Not found ]
[05:01:10]     Checking for file '/usr/sbin/change'          [ Not found ]
[05:01:10]     Checking for file '/usr/sbin/s'               [ Not found ]
[05:01:10]     Checking for file '/bin/f'                    [ Not found ]
[05:01:10]     Checking for file '/bin/i'                    [ Not found ]
[05:01:10]     Checking for file '/lib/libncom.so.4.0.1'     [ Not found ]
[05:01:10]     Checking for file '/sbin/zinit'               [ Not found ]
[05:01:10]     Checking for file '/tmp/pass_ssh.log'         [ Not found ]
[05:01:10]     Checking for file '/usr/include/gpm2.h'       [ Not found ]
[05:01:10]     Checking for file '/etc/ssh/.sshd_auth'       [ Not found ]
[05:01:10]     Checking for file '/usr/lib/.sshd.h'          [ Not found ]
[05:01:10]     Checking for file '/var/run/.defunct'         [ Not found ]
[05:01:10]     Checking for file '/etc/httpd/run/.defunct'   [ Not found ]
[05:01:10]     Checking for file '/usr/share/pci.r'          [ Not found ]
[05:01:10]     Checking for file '/etc/cron.daily/dnsquery'  [ Not found ]
[05:01:10]     Checking for file '/usr/lib/libutil1.2.1.2.so' [ Not found ]
[05:01:10]     Checking for file '/bin/ceva'                 [ Not found ]
[05:01:10]     Checking for file '/sbin/syslogd<SP>'         [ Not found ]
[05:01:10]     Checking for file '/usr/include/shup.h'       [ Not found ]
[05:01:10]     Checking for file '/etc/rpm/sshdOLD'          [ Not found ]
[05:01:10]     Checking for file '/etc/rpm/sshOLD'           [ Not found ]
[05:01:10]     Checking for file '/usr/share/passwd.h'       [ Not found ]
[05:01:10]     Checking for file '/lib/.xsyslog'             [ Not found ]
[05:01:10]     Checking for file '/etc/.xsyslog'             [ Not found ]
[05:01:10]     Checking for file '/lib/.ssyslog'             [ Not found ]
[05:01:10]     Checking for file '/tmp/.sendmail'            [ Not found ]
[05:01:10]     Checking for file '/usr/share/sshd.sync'      [ Not found ]
[05:01:10]     Checking for file '/bin/zcut'                 [ Not found ]
[05:01:10]     Checking for file '/usr/bin/zmuie'            [ Not found ]
[05:01:10]     Checking for file '/lib/libkeyutils.so.1.9'   [ Not found ]
[05:01:10]     Checking for file '/lib64/libkeyutils.so.1.9' [ Not found ]
[05:01:10]     Checking for file '/usr/lib/libkeyutils.so.1.9' [ Not found ]
[05:01:10]     Checking for file '/usr/lib64/libkeyutils.so.1.9' [ Not found ]
[05:01:10]     Checking for directory '/dev/ptyas'           [ Not found ]
[05:01:10]     Checking for directory '/usr/bin/take'        [ Not found ]
[05:01:10]     Checking for directory '/usr/src/.lib'        [ Not found ]
[05:01:11]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[05:01:11]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[05:01:11]     Checking for directory '/usr/sbin/...'        [ Not found ]
[05:01:11]     Checking for directory '/usr/share/.gun'      [ Not found ]
[05:01:11]     Checking for directory '/unde/vrei/tu/sa/te/ascunzi/in/server' [ Not found ]
[05:01:11]     Checking for directory '/usr/man/man1/..<SP><SP>/.dir' [ Not found ]
[05:01:11]     Checking for directory '/usr/X11R6/include/X11/...' [ Not found ]
[05:01:11]     Checking for directory '/usr/X11R6/lib/X11/.fonts/misc/...' [ Not found ]
[05:01:11]     Checking for directory '/tmp/.sys'            [ Not found ]
[05:01:11]     Checking for directory '/tmp/''               [ Not found ]
[05:01:11]     Checking for directory '/tmp/.,'              [ Not found ]
[05:01:11]     Checking for directory '/tmp/,.,'             [ Not found ]
[05:01:11]     Checking for directory '/dev/shm/emilien'     [ Not found ]
[05:01:11]     Checking for directory '/var/tmp/.log'        [ Not found ]
[05:01:11]     Checking for directory '/tmp/zmeu/...<SP>'    [ Not found ]
[05:01:11]     Checking for directory '/var/log/ssh'         [ Not found ]
[05:01:11]     Checking for directory '/dev/ida'             [ Not found ]
[05:01:11]     Checking for directory '/var/lib/games/.src/ssk/****' [ Not found ]
[05:01:11]     Checking for directory '/usr/lib/libshtift'   [ Not found ]
[05:01:11]     Checking for directory '/usr/src/.poop'       [ Not found ]
[05:01:11]     Checking for directory '/dev/wd4'             [ Not found ]
[05:01:11]     Checking for directory '/var/run/.tmp'        [ Not found ]
[05:01:11]     Checking for directory '/usr/man/man1/lib/.lib' [ Not found ]
[05:01:11]     Checking for directory '/dev/portd'           [ Not found ]
[05:01:11]     Checking for directory '/dev/...'             [ Not found ]
[05:01:11]     Checking for directory '/usr/share/man/mansps' [ Not found ]
[05:01:11]     Checking for directory '/lib/.so'             [ Not found ]
[05:01:11]     Checking for directory '/lib/.sso'            [ Not found ]
[05:01:11]     Checking for directory '/usr/include/sslv3'   [ Not found ]
[05:01:11]     Checking for directory '/dev/shm/sshd'        [ Not found ]
[05:01:11]     Checking for directory '/usr/share/locale/mk/.dev/sk' [ Not found ]
[05:01:11]     Checking for directory '/usr/share/locale/mk/.dev' [ Not found ]
[05:01:11]     Checking for directory '/usr/include/netda.h' [ Not found ]
[05:01:11]     Checking for directory '/usr/include/.ssh'    [ Not found ]
[05:01:12]     Checking for directory '/usr/share/locale/jp/.<SP>' [ Not found ]
[05:01:12]     Checking for directory '/usr/share/.sqe'      [ Not found ]
[05:01:12]   Checking for possible rootkit files and directories [ None found ]
[05:01:12]
[05:01:12] Info: Starting test name 'possible_rkt_strings'
[05:01:12]   Performing check for possible rootkit strings
[05:01:12] Info: Using system startup paths: /etc/rc.local /etc/init.d
[05:01:12]     Checking for string 'phalanx'                 [ Not found ]
[05:01:12]     Checking for string '/dev/proc/****it'        [ Not found ]
[05:01:12]     Checking for string '****'                    [ Not found ]
[05:01:12]     Checking for string 'backdoor'                [ Not found ]
[05:01:12]     Checking for string '/usr/bin/rcpc'           [ Not found ]
[05:01:12]     Checking for string '/usr/sbin/login'         [ Not found ]
[05:01:12]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[05:01:12]     Checking for string 'vt200'                   [ Not found ]
[05:01:12]     Checking for string '/usr/bin/xstat'          [ Not found ]
[05:01:12]     Checking for string '/bin/envpc'              [ Not found ]
[05:01:12]     Checking for string 'L4m3r0x'                 [ Not found ]
[05:01:12]     Checking for string '/lib/libext'             [ Not found ]
[05:01:12]     Checking for string '/usr/sbin/login'         [ Not found ]
[05:01:12]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[05:01:12]     Checking for string 'sendmail'                [ Not found ]
[05:01:12]     Checking for string 'cocacola'                [ Not found ]
[05:01:12]     Checking for string 'joao'                    [ Not found ]
[05:01:12]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[05:01:12]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[05:01:12]     Checking for string '/dev/sgk'                [ Not found ]
[05:01:12]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[05:01:13]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[05:01:13]     Checking for string '/dev/proc/****it'        [ Not found ]
[05:01:13]     Checking for string '/lib/.sso'               [ Not found ]
[05:01:13]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[05:01:13]     Checking for string '/dev/caca'               [ Not found ]
[05:01:13]     Checking for string '/dev/ttyoa'              [ Not found ]
[05:01:13]     Checking for string '/usr/lib/ldlibns.so'     [ Not found ]
[05:01:13]     Checking for string '/dev/ptyxx/.addr'        [ Not found ]
[05:01:13]     Checking for string 'syg'                     [ Not found ]
[05:01:13]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[05:01:13]     Checking for string '/dev/pts/01'             [ Not found ]
[05:01:13]     Checking for string 'tw33dl3'                 [ Not found ]
[05:01:13]     Checking for string 'psniff'                  [ Not found ]
[05:01:13]     Checking for string 'uconf.inv'               [ Not found ]
[05:01:13]     Checking for string 'lib/ldlibps.so'          [ Not found ]
[05:01:13]     Checking for string '/usr/lib/ldlibpst.so'    [ Not found ]
[05:01:13]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[05:01:13]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[05:01:13]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[05:01:13]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[05:01:13]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[05:01:13]     Checking for string '/bin/bash'               [ Not found ]
[05:01:13]     Checking for string '/dev/ptyxx'              [ Not found ]
[05:01:13]     Checking for string '/.config'                [ Not found ]
[05:01:14]     Checking for string '\$.*\$\!.*\!\!\$'        [ Not found ]
[05:01:14]     Checking for string 'backdoor.h'              [ Not found ]
[05:01:14]     Checking for string 'backdoor_active'         [ Not found ]
[05:01:14]     Checking for string 'magic_pass_active'       [ Not found ]
[05:01:14]     Checking for string '/usr/include/gpm2.h'     [ Not found ]
[05:01:14]     Checking for string '/usr/include/openssl'    [ Not found ]
[05:01:14]     Checking for string 'aion'                    [ Not found ]
[05:01:14]     Checking for string 'pcszPass'                [ Not found ]
[05:01:14]     Checking for string 'LogPass'                 [ Not found ]
[05:01:14]     Checking for string 'Login_Check'             [ Not found ]
[05:01:14]     Checking for string 'includes.h'              [ Not found ]
[05:01:14]     Checking for string 'DecodeString'            [ Not found ]
[05:01:14]     Checking for string 'EncodeString'            [ Not found ]
[05:01:14]     Checking for string '/dev/xdta'               [ Not found ]
[05:01:14]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[05:01:14]     Checking for string '/dev/ptyxx/.proc'        [ Not found ]
[05:01:15]     Checking for string 'in.inetd'                [ Not found ]
[05:01:15]     Checking for string '#<HIDE_.*>'              [ Not found ]
[05:01:15]     Checking for string 'bin/xchk'                [ Not found ]
[05:01:15]     Checking for string 'bin/xsf'                 [ Not found ]
[05:01:16]     Checking for string '/usr/bin/ssh2d'          [ Not found ]
[05:01:16]     Checking for string '/usr/sbin/xntps'         [ Not found ]
[05:01:16]     Checking for string 'ttyload'                 [ Not found ]
[05:01:16]     Checking for string '/etc/rc.d/init.d/init'   [ Not found ]
[05:01:17]     Checking for string 'usr/bin/xfss'            [ Not found ]
[05:01:17]     Checking for string '/usr/sbin/rpc.netinet'   [ Not found ]
[05:01:17]     Checking for string '/usr/lib/.fx/cons.saver' [ Not found ]
[05:01:17]     Checking for string '/usr/lib/.fx/xs'         [ Not found ]
[05:01:17]     Checking for string '/ssh2d'                  [ Not found ]
[05:01:18]     Checking for string '/dev/kmod'               [ Not found ]
[05:01:18]     Checking for string '/crth.o'                 [ Not found ]
[05:01:18]     Checking for string '/crtz.o'                 [ Not found ]
[05:01:18]     Checking for string '/dev/dos'                [ Not found ]
[05:01:19]     Checking for string '/lpq'                    [ Not found ]
[05:01:19]     Checking for string '/usr/sbin/rescue'        [ Not found ]
[05:01:19]     Checking for string '/usr/lib/lpstart'        [ Not found ]
[05:01:19]     Checking for string '/volc'                   [ Not found ]
[05:01:19]     Checking for string 'sourcemask'              [ Not found ]
[05:01:20]     Checking for string '/bin/vobiscum'           [ Not found ]
[05:01:20]     Checking for string '/usr/sbin/in.telnet'     [ Not found ]
[05:01:20]     Checking for string '/usr/bin/hdparm?-t1?-X53?-p' [ Not found ]
[05:01:20]     Checking for string '/lib/.xsyslog'           [ Not found ]
[05:01:21]     Checking for string '/etc/.xsyslog'           [ Not found ]
[05:01:21]     Checking for string '/lib/.ssyslog'           [ Not found ]
[05:01:21]     Checking for string '/tmp/.sendmail'          [ Not found ]
[05:01:21]     Checking for string '/lib/ldd.so/tkps'        [ Not found ]
[05:01:21]     Checking for string 't0rnkit'                 [ Not found ]
[05:01:21]     Checking for string '/dev/proc/****it'        [ Not found ]
[05:01:21]     Checking for string 'backdoor.h'              [ Not found ]
[05:01:21]     Checking for string 'backdoor_active'         [ Not found ]
[05:01:21]     Checking for string 'magic_pass_active'       [ Not found ]
[05:01:21]     Checking for string '/usr/include/gpm2.h'     [ Not found ]
[05:01:21]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[05:01:21]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[05:01:21]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[05:01:22]     Checking for string '/usr/lib/ldlibct.so'     [ Not found ]
[05:01:22]     Checking for string '/usr/lib/ldlibdu.so'     [ Not found ]
[05:01:22]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[05:01:22]     Checking for string 'libproc.so.2.0.7'        [ Not found ]
[05:01:22]     Checking for string '/dev/ida/.inet'          [ Not found ]
[05:01:22]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[05:01:22]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[05:01:22]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[05:01:22]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[05:01:22]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[05:01:22]     Checking for string '/usr/include/mysql/mysql.hh1' [ Not found ]
[05:01:22]     Checking for string 'backconnect'             [ Not found ]
[05:01:22]     Checking for string 'magic?packet?received'   [ Not found ]
[05:01:22]   Checking for possible rootkit strings           [ None found ]
[05:01:22]
[05:01:22] Info: Starting test name 'malware'
[05:01:22] Performing malware checks
[05:01:22]
[05:01:22] Info: Test 'deleted_files' disabled at users request.
[05:01:22]
[05:01:22] Info: Starting test name 'running_procs'
[05:01:23]   Checking running processes for suspicious files [ None found ]
[05:01:23]
[05:01:23] Info: Test 'hidden_procs' disabled at users request.
[05:01:23]
[05:01:23] Info: Test 'suspscan' disabled at users request.
[05:01:23]
[05:01:23] Info: Starting test name 'other_malware'
[05:01:23]   Performing check for login backdoors
[05:01:23]     Checking for '/bin/.login'                    [ Not found ]
[05:01:23]     Checking for '/sbin/.login'                   [ Not found ]
[05:01:23]   Checking for login backdoors                    [ None found ]
[05:01:23]
[05:01:23]   Performing check for suspicious directories
[05:01:23]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[05:01:23]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[05:01:23]   Checking for suspicious directories             [ None found ]
[05:01:23]
[05:01:23]   Checking for software intrusions                [ Skipped ]
[05:01:23] Info: Check skipped - tripwire not installed
[05:01:23]
[05:01:23]   Performing check for sniffer log files
[05:01:23]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[05:01:23]     Checking for file '/dev/prom/sn.l'            [ Not found ]
[05:01:23]     Checking for file '/dev/fd/.88/zxsniff.log'   [ Not found ]
[05:01:23]   Checking for sniffer log files                  [ None found ]
[05:01:23]
[05:01:23] Suspicious Shared Memory segments
[05:01:24]   Suspicious Shared Memory segments               [ None found ]
[05:01:24]
[05:01:24] Info: Starting test name 'trojans'
[05:01:24] Performing trojan specific checks
[05:01:24]   Checking for enabled inetd services             [ Skipped ]
[05:01:24] Info: Check skipped - file '/etc/inetd.conf' does not exist.
[05:01:24]
[05:01:24]   Performing check for enabled xinetd services
[05:01:24]   Checking for enabled xinetd services            [ Skipped ]
[05:01:24] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[05:01:24]   Checking for Apache backdoor                    [ Not found ]
[05:01:24]
[05:01:24] Info: Starting test name 'os_specific'
[05:01:24] Performing Linux specific checks
[05:01:24]   Checking loaded kernel modules                  [ OK ]
[05:01:24] Info: Using modules pathname of '/lib/modules/3.16.0-53-generic'
[05:01:24]   Checking kernel module names                    [ OK ]
[05:01:24]
[05:01:24] Info: Starting test name 'network'
[05:01:24] Checking the network...
[05:01:24]
[05:01:24] Performing checks on the network ports
[05:01:24] Info: Starting test name 'ports'
[05:01:24]   Performing check for backdoor ports
[05:01:24]     Checking for TCP port 1524                    [ Not found ]
[05:01:24]     Checking for TCP port 1984                    [ Not found ]
[05:01:24]     Checking for UDP port 2001                    [ Not found ]
[05:01:24]     Checking for TCP port 2006                    [ Not found ]
[05:01:24]     Checking for TCP port 2128                    [ Not found ]
[05:01:24]     Checking for TCP port 6666                    [ Not found ]
[05:01:24]     Checking for TCP port 6667                    [ Not found ]
[05:01:24]     Checking for TCP port 6668                    [ Not found ]
[05:01:24]     Checking for TCP port 6669                    [ Not found ]
[05:01:24]     Checking for TCP port 7000                    [ Not found ]
[05:01:25]     Checking for TCP port 13000                   [ Not found ]
[05:01:25]     Checking for TCP port 14856                   [ Not found ]
[05:01:25]     Checking for TCP port 25000                   [ Not found ]
[05:01:25]     Checking for TCP port 29812                   [ Not found ]
[05:01:25]     Checking for TCP port 31337                   [ Not found ]
[05:01:25]     Checking for TCP port 32982                   [ Not found ]
[05:01:25]     Checking for TCP port 33369                   [ Not found ]
[05:01:25]     Checking for TCP port 47107                   [ Not found ]
[05:01:25]     Checking for TCP port 47018                   [ Not found ]
[05:01:25]     Checking for TCP port 60922                   [ Not found ]
[05:01:25]     Checking for TCP port 62883                   [ Not found ]
[05:01:25]     Checking for TCP port 65535                   [ Not found ]
[05:01:25]   Checking for backdoor ports                     [ None found ]
[05:01:25]
[05:01:25] Info: Starting test name 'hidden_ports'
[05:01:25] Info: Found the 'unhide-tcp' command: /usr/sbin/unhide-tcp
[05:01:26]   Checking for hidden ports                       [ None found ]
[05:01:26]
[05:01:26] Performing checks on the network interfaces
[05:01:26] Info: Starting test name 'promisc'
[05:01:26]   Checking for promiscuous interfaces             [ None found ]
[05:01:26]
[05:01:26] Info: Test 'packet_cap_apps' disabled at users request.
[05:01:26]
[05:01:26] Info: Starting test name 'local_host'
[05:01:26] Checking the local host...
[05:01:26]
[05:01:26] Info: Starting test name 'startup_files'
[05:01:26] Performing system boot checks
[05:01:26]   Checking for local host name                    [ Found ]
[05:01:26]
[05:01:26] Info: Starting test name 'startup_malware'
[05:01:26]   Checking for system startup files               [ Found ]
[05:01:27]   Checking system startup files for malware       [ None found ]
[05:01:27]
[05:01:27] Info: Starting test name 'group_accounts'
[05:01:27] Performing group and account checks
[05:01:27]   Checking for passwd file                        [ Found ]
[05:01:27] Info: Found password file: /etc/passwd
[05:01:27]   Checking for root equivalent (UID 0) accounts   [ None found ]
[05:01:27] Info: Found shadow file: /etc/shadow
[05:01:27]   Checking for passwordless accounts              [ None found ]
[05:01:27]
[05:01:27] Info: Starting test name 'passwd_changes'
[05:01:27]   Checking for passwd file changes                [ None found ]
[05:01:27]
[05:01:27] Info: Starting test name 'group_changes'
[05:01:27]   Checking for group file changes                 [ None found ]
[05:01:27]   Checking root account shell history files       [ OK ]
[05:01:27]
[05:01:27] Info: Starting test name 'system_configs'
[05:01:27] Performing system configuration file checks
[05:01:28]   Checking for an SSH configuration file          [ Found ]
[05:01:28] Info: Found an SSH configuration file: /etc/ssh/sshd_config
[05:01:28] Info: Rkhunter option ALLOW_SSH_ROOT_USER set to 'no'.
[05:01:28] Info: Rkhunter option ALLOW_SSH_PROT_V1 set to '0'.
[05:01:28]   Checking if SSH root access is allowed          [ Not allowed ]
[05:01:28]   Checking if SSH protocol v1 is allowed          [ Not allowed ]
[05:01:28]   Checking for a running system logging daemon    [ Found ]
[05:01:28] Info: A running 'rsyslog' daemon has been found.
[05:01:28] Info: A running 'systemd-journald' daemon has been found.
[05:01:28] Info: Found an rsyslog configuration file: /etc/rsyslog.conf
[05:01:28] Info: Found a systemd configuration file: /etc/systemd/journald.conf
[05:01:28]   Checking for a system logging configuration file [ Found ]
[05:01:28]   Checking if syslog remote logging is allowed    [ Not allowed ]
[05:01:28]
[05:01:28] Info: Starting test name 'filesystem'
[05:01:28] Performing filesystem checks
[05:01:28] Info: SCAN_MODE_DEV set to 'THOROUGH'
[05:01:30]   Checking /dev for suspicious file types         [ Warning ]
[05:01:30] Warning: Suspicious file types found in /dev:
[05:01:30]          /dev/shm/PostgreSQL.1804289383: data
[05:01:30]   Checking for hidden files and directories       [ Warning ]
[05:01:30] Warning: Hidden file found: /etc/.resol.conf.swp: data
[05:01:30]   Checking for missing log files                  [ Skipped ]
[05:01:30]   Checking for empty log files                    [ Skipped ]
[05:01:30]
[05:01:30] Info: Test 'apps' disabled at users request.
[05:01:30]
[05:01:30] System checks summary
[05:01:30] =====================
[05:01:30]
[05:01:30] File properties checks...
[05:01:30] Required commands check failed
[05:01:30] Files checked: 150
[05:01:30] Suspect files: 150
[05:01:30]
[05:01:30] Rootkit checks...
[05:01:30] Rootkits checked : 380
[05:01:30] Possible rootkits: 0
[05:01:30]
[05:01:30] Applications checks...
[05:01:30] All checks skipped
[05:01:30]
[05:01:30] The system checks took: 1 minute and 27 seconds
[05:01:30]
[05:01:30] Info: End date is Seg Nov 16 05:01:30 WET 2015

```

---

### Post by rhandy2 on 2015-11-17
Rootkit Hunter 1.4.2


after 

```
# rkhunter --propupd
```

only one suspect file

```
[COLOR=#000000]*Warning: The command '/usr/sbin/prelink' has been replaced by a script: /usr/sbin/prelink: Bourne-Again shell script, ASCII text executable*[/COLOR]

```

Making some checks and results
```
root@example.com:~# dpkg -S /usr/sbin/prelink
prelink: /usr/sbin/prelink
root@example.com]:~# which ls
/bin/ls
root@example.com:~# dpkg -S /bin/ls
coreutils: /bin/ls
root@example.com:~# dpkg -S $(which ls)
coreutils: /bin/ls
root@example.com:~# debsums -c coreutils
root@example.com:~# python -c 'print hex(3 << ((1024/4)-2))[:-1]'
0xc000000000000000000000000000000000000000000000000000000000000000
root@example.com:~# python -c 'print hex((1 << (1024/4))-1)[:-1]'
0xffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff

```

---

### Post by Habitual on 2015-11-17
Add ```
SCRIPTWHITELIST=/usr/sbin/prelink
``` to /etc/rkhunter.conf and then re-run
```
rkhunter --propupd
```
and then re-run ```
rkhunter -c -sk
``` and see what happens.

---

### Post by rhandy2 on 2015-11-18
Thanks HABITUAL!!!

warning disapear for prelink disapear.

> Checking for hidden files and directories                [ Warning ]



System checks summary
=====================


File properties checks...
    Files checked: 150
    Suspect files: 0


Rootkit checks...
    Rootkits checked : 380
    Possible rootkits: 0


Applications checks...
    All checks skipped




Only have this warning

> [COLOR=#000000]*Checking for hidden files and directories [ Warning ]*[/COLOR]


>  Warning: Hidden file found: /usr/sbin/.prelink.swp

---

### Post by Habitual on 2015-11-18
use ALLOWHIDDENFILE= 
for that file.
in /etc/rkhunter.conf and **upd**ate the **prop**erties data file and re-scan

---

### Post by rhandy2 on 2015-11-19
Hello

I allow that file

After run rkhunter see log

> Checking for hidden files and directories       [ Warning ][13:11:11] Warning: Hidden file found: /etc/.sources.list.swp: data
[13:11:11] Warning: Hidden file found: /usr/sbin/.prelink.swp.suspectious: data
[13:11:11]   Checking for missing log files                  [ Skipped ]
[13:11:11]   Checking for empty log files                    [ Skipped ]
[13:11:11]
[13:11:11] Info: Test 'apps' disabled at users request.
[13:11:11]
[13:11:11] System checks summary
[13:11:11] =====================
[13:11:11]
[13:11:11] File properties checks...
[13:11:11] Files checked: 150
[13:11:11] Suspect files: 0
[13:11:11]
[13:11:11] Rootkit checks...
[13:11:11] Rootkits checked : 380
[13:11:11] Possible rootkits: 0
[13:11:11]
[13:11:11] Applications checks...
[13:11:11] All checks skipped
[13:11:11]
[13:11:11] The system checks took: 1 minute and 13 seconds





open files
nano /pathtofiles

> 
b0nano 2.4.2^@^@^@^@^@^@^@^@^@^@^@^@&#65533;f^@^@root^@^@^@^@^@^@^@^@^@^@^@^@


---

### Post by Habitual on 2015-11-19
On 15.10 I cannot say what the file is.
I can guess that it is a swap file used during an edit where the editor closed unexpectedly.
vi[m] does this.
HOWEVER, the period in the file's location is suspect. eg: /etc/**[COLOR=#ff0000].[/COLOR]**sources.list.swp

When you posted the /usr/sbin/prelink script above, did you use nano to view it's contents?
Have you also edited /etc/.resol.conf ? (that should be resolv.conf)

If you can clarify that you did indeed edit these files, or attempted to and then canceled out of the editor?

---

### Post by rhandy2 on 2015-11-19
Yes,

I think is swap file, I use nano to see prelink file and edit sources.list  and resolv.conf.

---

### Post by Habitual on 2015-11-19
> **rhandy2 said:**
> Yes,

I think is swap file, I use nano to see prelink file and edit sources.list  and resolv.conf.
Then you can delete those .swp files and re-scan with ```
rkhunter -c -sk
```

---

### Post by Habitual on 2015-11-19
Note:
Every time you update your system, you'll need to re-run ```
rkhunter --propupd
```

---

