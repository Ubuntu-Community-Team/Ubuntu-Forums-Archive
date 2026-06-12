---
title: "rsync --read-batch over ssh"
date: 2013-02-01
forum: Server Platforms
---

### Post by slakkie on 2013-02-01
Hello all,

I have a question regarding rsync --read-batch=file over ssh.

I'm doing the following:

```

function exec_rsync() {
    local host=$1
    shift
    ssh $host mkdir -p $src
    eval sudo rsync --write-batch=/tmp/rsync_disk $rsync_opts -e "'ssh'" $DIRS "'user@${host}:$src'"
#    eval sudo rsync $rsync_opts -e "'ssh'" $DIRS "'user@${host}:$src'"
    [ $? -ne 0 ] && exit 1

    for host in $* ; do
        ssh $host mkdir -p $src
#        eval sudo rsync $rsync_opts -e "'ssh'" $DIRS "'user@${host}:$src'"
        eval sudo rsync --read-batch=/tmp/rsync_disk $rsync_opts -e "'ssh'" $DIRS "'user@${host}:$src'"
        [ $? -ne 0 ] && exit 1
    done
}

```

When I execute the script, I get the following error:

```

(zsh)$ rsync_disks host host2     
user@host password: 
building file list ... 
14498 files to consider
[snip]
sent 414055 bytes  received 60 bytes  75293.64 bytes/sec
total size is 34045203836  speedup is 82211.96
remote destination is not allowed with --read-batch
rsync error: syntax or usage error (code 1) at main.c(1218) [Receiver=3.0.9]

```

Can someone tell me what I'm doing wrong, if I should be setting up an rsync daemon because batch-files aren't supported over ssh, etc?

---

### Post by koenn on 2013-02-01
I'm not familiar with the batch options, but at first glance it looks to me that batch mode is rather a special case thet requires a rather different approach that 'rsync this there'

Have you read the BATCH MODE section in the man page ?

---

### Post by slakkie on 2013-02-01
> **koenn said:**
> I'm not familiar with the batch options, but at first glance it looks to me that batch mode is rather a special case thet requires a rather different approach that 'rsync this there'

Have you read the BATCH MODE section in the man page ?

Yes I did, but I expected similar syntax as to the rsync over ssh, as you see in my code snippet.

Now I'm doing this and it works:

```

function exec_rsync() {
    local batch_file=/tmp/rsync_disk
    local host=$1
    local user=someuser

    if [ ! -e $batch_file ] ; then
        eval sudo rsync --only-write-batch=$batch_file $rsync_opts $DIRS -e 'ssh' $user@$host:$src
        [ $? -ne 0 ] && exit 1
    fi

    for host in $* ; do
        sudo cat $batch_file | eval ssh $user@$host rsync $rsync_opts --read-batch=- $src
        [ $? -ne 0 ] && exit 1
    done
    sudo rm $batch_file
}

```

---

### Post by koenn on 2013-02-01
Good job.

---

