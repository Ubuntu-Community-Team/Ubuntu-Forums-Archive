---
title: "debmirror not synchronizing debian-installer and *.udeb"
date: 2006-12-04
forum: Repositories &amp; Backports
---

### Post by nero on 2006-12-04
Hi all,

I have a problem using debmirror for synchronizing our local repository.
The following script never synchronize debian-installer/installer-i386/intaller-amd64 directory and *.udeb files

I allready try to bypass using 
--adddir=main/debian-installer (deprecate)
--include=m/*udeb/
without success

```
#!/bin/bash

LOG=/var/log/eib/`basename $0`.`date "+%Y%m%d"`.log
PROXY=http://your.proxy.dom:port/
DEST=/export/repository
HOST=archive.ubuntu.com
ARCH=i386,amd64
DIST=dapper,dapper-updates,dapper-security,edgy,edgy-updates,edgy-security
METHOD=http
SECTION=main,multiverse,restricted,universe
MAIL="xxx@xxx.dom"
SUBJECT="[DEBMIRROR][SYNCHRO]"
TITLE="[DEBMIRROR SYNCHRO REPORT]"


### FUNCTION ###
function removeLog () {
        if [ -f $LOG ]
        then
                rm $LOG
        fi
}

function sendLog () {
        if [ -f ${LOG} ]
        then
                echo ${TITLE} > ${LOG}.0
                echo "" >> ${LOG}.0
                cat ${LOG} >> ${LOG}.0
                cat ${LOG}.0 | mailx -s "${SUBJECT}" ${MAIL}
                rm ${LOG}.0
        fi
}


function update () {
        echo ""
        echo "UBUNTU REPOSITORY UPDATE"
        echo ""
        echo "Host: ${HOST}"
        echo "Architecture: ${ARCH}"
        echo "Distribution: ${DIST}"
        echo "Section: ${SECTION}"

        /usr/bin/debmirror      --host=${HOST} \
                                --root=ubuntu/ \
                                --proxy=${PROXY} \
                                --method=${METHOD} \
                                --progress --verbose \
                                --dist=${DIST} \
                                --ignore-release-gpg \
                                --ignore-missing-release \
                                --ignore-small-error \
                                --section=${SECTION} \
                                --arch=${ARCH} ${DEST}
}

### MAIN ###
removeLog
update | tee -a ${LOG}
sendLog
```

Thanks in advance
Jonathan

---

### Post by nero on 2006-12-04
For the one who are interested...

Add the option *--nosource* and the section *main/debian-installer* solve this issue.

Jonathan

---

