---
title: "juju status -e maas -v i got Error details: no reachable servers"
date: 2013-09-22
forum: Ubuntu Cloud and Juju
---

### Post by alaa4 on 2013-09-22
i installed maas server on ubuntu 12.4 and added 2 nodes on it and i made ```
[COLOR=#FFFFFF][FONT=monospace]juju bootstrap[/FONT][/COLOR]
``` but when i try to get environment information using ```
juju status
``` or trying to deploy any service i got the error massage 

Error details: no reachable servers 

does any one have any suggesting

---

### Post by mrsirroger on 2014-02-24
I'm getting this as well any one have a clue what it could be.

It looks like its working fine then **bam** [COLOR=#000000]no reachable servers


[/COLOR]

---

### Post by mrsirroger on 2014-02-24
ok I thought I would give more details.

[COLOR=#000000][FONT=Helvetica]maas is working I can spin up and down nodes from inside maas...
Juju appears to be working. I can
root@MAAS01:~# juju bootstrap -v
and I get
INFO juju supercommand.go:286 command finished[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]but when I
root@MAAS01:~# juju status -e maas[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]I get:[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]ERROR Unable to connect to environment "maas".
Please check your credentials or use 'juju bootstrap' to create a new environment.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Error details:
no reachable servers[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]--------------------------------
other information you might need.
-----------------------------------------------------
my environment file is:
root@MAAS01:~# nano /root/.juju/environments.yaml[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]environments:
  maas:
    type: maas
    maas-server: '[http://172.16.0.11:80/MAAS']("http://172.16.0.11/MAAS'")
    maas-oauth: 'the mass key from maas preferences'
    admin-secret: 'the super secret password for my root on the local box'
    default-series: precise
    authorized-keys-path: '/root/.ssh/id_dsa.pub'[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]--------------------------------
obviously the names have been changed to protect the not always so innocent.
--------------------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]also I am running
root@MAAS01:~# uname -a
Linux MAAS01 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]that is Ubuntu Server 13.10 in case you are not sure.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]root@MAAS01:~# maas version
1.5.4[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]root@MAAS01:~# juju version
1.16.3-saucy-amd64
--------------------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]the weirdest part about this whole things is that when I run the bootstrap command it stats the machine like it going to work but I can't get the status ... I can't deploy ... I and can't juju-quickstart... I think the issue is in the environment file but I can't figure out what I'm doing wrong and the docs are ... well kinda vague.[/FONT][/COLOR]

---

### Post by luix2 on 2014-02-27
I have the same problem here... DNS is working fine and I can ping all nodes through FQDNs.

---

