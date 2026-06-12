---
title: "Vmware reconfiger 7.10"
date: 2008-01-02
forum: Virtualisation
---

### Post by arosenau on 2008-01-02
I have been trying several times to get Vmware to work on Ubuntu 7.10 server. I have tried both the repositories and the binaries from vmware. I install both vmware and the web management console, however everytime after a reboot I have to rerun vmware-config-mui.pl before vmware will work. I have seen several people talk about vmware creating a not-configured file in /etc/vmware however I have never seen a file like this. Does anybody have a solution to this. My goals is to get a ubuntu server setup to only run vmware. Would it be better if I used the LTS release?

Thanks

---

### Post by arosenau on 2008-01-03
Does anyone have a solution to this or a suggestion? It would be really nice to get this solved.

---

### Post by arosenau on 2008-01-03
Just an update that I have also tried this with the 6.0.6 LTS release of Ubuntu and have the same problem. Everytime I reboot I have to run /usr/bin/vmware-config-mui.pl and then it works

---

### Post by fjgaude on 2008-01-03
I'm sorry but I have not encountered such a situation as yours.

---

### Post by arosenau on 2008-01-04
Good news I have found a solutions that works in 6.0.6 I will be install 7.10 and testing it there also. It seems that the problem is a directory permission problem. I found the solution here 

[http://antoniolorusso.com/]("http://antoniolorusso.com/")

The solution was to add the following right at the start of the vmware_start_httpd() function

```

HTTPD_RUN_DIR="/var/run/vmware/httpd"
[ -d "$HTTPD_RUN_DIR" ] || mkdir $HTTPD_RUN_DIR
chmod 777 $HTTPD_RUN_DIR

```

---

### Post by fjgaude on 2008-01-04
Well, it seems such was not a problem with Gutsy, Feisty, and not even Edgy 6.10, AFAIK.

Anyway, it's good that you found how to correct the issue.

---

### Post by arosenau on 2008-01-04
Just an update in case anyone runs across this. I got it working in 7.10 and found a better solution here

[http://communities.vmware.com/thread/59819?tstart=0&start=15]("http://communities.vmware.com/thread/59819?tstart=0&start=15")

Create the following script as /etc/init.d/rundir.httpd.vmware,
then

chmod 755 /etc/init.d/rundir.httpd.vmware
cd /etc/rc2.d
ln -s ../init.d/rundir.httpd.vmware ./S90rundir.httpd.vmware

Scripts content:
------------------------------------------------------------------------------------------
#! /bin/sh
#
# /var/run gets purged at every reboot!

RUNDIR="/var/run/vmware/httpd"
OWNER="www-data"
GROUP="www-data"

/usr/bin/test -d "$RUNDIR" || \
/bin/mkdir -p "$RUNDIR" && /bin/chown "$OWNER:$GROUP" "$RUNDIR"
------------------------------------------------------------------------------------------


The advantage to this is you don't have to modify the vmware file and thus this fix will survive an upgrade to vmware, as the original poster mentioned.

---

