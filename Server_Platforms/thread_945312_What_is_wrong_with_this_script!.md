---
title: "What is wrong with this script?!"
date: 2008-10-12
forum: Server Platforms
---

### Post by zefferno on 2008-10-12
I am trying to run the following script using sh but I keep getting error 24: "Syntax error: end of file unexpected (expecting "then")"

](*,)What is wrong with it??

(expecting "then")

```

#!/bin/sh

unset PATH

CLAMSCAN=/usr/bin/clamscan;
LOG_FILE=/var/log/clamav/clamscan-cron.log;
SCAN_FOLDER=/home/user1234;
EMAIL_ADDRESS=someemail@email.com

echo $(date) Starting  ClamAV scanning... > $LOG_FILE;

$CLAMSCAN -v -r --stdout --exclude-dir=/var/log/clamav/infected --move=/var/log/clamav/infected $SCAN_FOLDER >> $LOG_FILE;

if [ $? -eq 1 ]; then
        echo "ClamAV found virus during scan!\n$LOG_FILE is attached to the message." | mutt -a $LOG_FILE -F /etc/muttrc -s "FTP notification" $EMAIL_ADDRESS
fi

# Finish
echo >> $LOG_FILE
echo $(date) ...................................... Scan finished. >> $LOG_FILE;

```

---

### Post by zefferno on 2008-10-12
Problem solved. It appears to be carrage return chars in the file.

---

