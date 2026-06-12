---
title: "ufw logs formatting"
date: 2014-06-23
forum: Server Platforms
---

### Post by chiron69 on 2014-06-23
Good morning,

I'm on the way to configure a parser (split the ufw message) into syslog-ng, in order to feed a mysql database. I will afterwards use that into loganalyzer, but that's another story.

When I have a look at the ufw logs, I can see some lines like this (i have anonimyzed mac and ip):

```

Jun 23 08:51:22 server1 kernel: [486938.916177] [UFW BLOCK] IN=eth1 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=86.101.38.88 DST=xx.xx.xx.xx LEN=60 TOS=0x00 PREC=0x00 TTL=50 ID=51005 DF PROTO=TCP SPT=41945 DPT=16881 WINDOW=7300 RES=0x00 SYN URGP=0 

```


and others like this:

```

Jun 23 08:52:36 server1 kernel: [487012.604424] [UFW BLOCK] IN=eth1 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=46.138.41.210 DST=xx.xx.xx.xx LEN=129 TOS=0x00 PREC=0x00 TTL=112 ID=12729 PROTO=UDP SPT=6899 DPT=6881 LEN=109 

```

The problem is, I can't configure a parser if all messages do not have the same number of fields.
Is there any way to fix this?

Thanks.

---

### Post by SeijiSensei on 2014-06-23
Parse the line on spaces, then iterate over the paired entries.  In PHP I'd do something like:
```

<?php
$log=file("/var/log/somelog");  # reads whole file into a numbered array

for ($i=0; $i<count($log); $i++) {
     # read each line and parse it
     $fields=explode(" ",$log[$i]);
     $data=array();
     
     foreach ($fields as $field) {
         $fieldparts=explode("=",$field);
         # create an associative array of key-value pairs
         $data[$fieldparts[0]]=$fieldparts[1];
     }
}
?>

```

Now you can just use $data['PROTO'] to get the protocol or $data['SRC'] to get the source IP address.

---

### Post by chiron69 on 2014-06-26
Thanks a lot, but the problem is related to syslog-ng itself, I have to find a way to configure it. I'm going to create a new topic

---

