---
title: "Expect within Bash"
date: 2010-02-12
forum: Server Platforms
---

### Post by sanemanmad on 2010-02-12
Hi ALL, 

I am writing a simple script to perform certain tasks that I do rather regularly on >100 servers [HP/AIX/Sun/Linux] and I am at a snag.


I can successfully use my expect script by itself, however now I am attempting to integrate with another script I have.

My problem as follows:

This is expect and it works just fine.
```


#!/usr/local/bin/expect --
# wrapper to make passwd(1) be non-interactive
# username is passed as 1st arg, passwd as 2nd
# Executable only by root

set password [lindex $argv 1]
spawn /usr/bin/passwd [lindex $argv 0]
expect "password:"
send "$password\r"
expect "password:"
send "$password\r"
expect eof
```


Now here is my expect within bash:
```

        changeroot ()
        {
                /usr/local/bin/expect -- << EOF
                set password $newpasswd
                spawn /usr/bin/passwd root
                expect "password:"
                send "$password\r"
                expect "password:"
                send "$password\r"
                expect eof
EOF
        }
```


This is being called from inside a bash script and I am not sure how to successfully pass the Variable "newpasswd". 

Here is example usage:

```
bash-2.03$ sudo ./tasks.sh
Usage: tasks.sh 'vi | logs | backups | rootpw'

bash-2.03$ sudo ./tasks.sh rootpw
Must give [NEW] root password

bash-2.03$ sudo ./tasks.sh rootpw newpasswd
spawn /usr/bin/passwd root
New Password:
Re-enter new Password:
passwd: password successfully changed for root
bash-2.03$ su -
Password:
su: Sorry


```

As you can see it is passing something as variable since passwd is completing sucessfully, just not passing the "newpasswd" variable, as i am trying to su - and getting denied.

---

### Post by KiLaHuRtZ on 2010-02-12
```
        changeroot ()
        {
                /usr/local/bin/expect -- << EOF
-               set password $newpasswd
+               set password $2
                spawn /usr/bin/passwd root
                expect "password:"
                send "$password\r"
                expect "password:"
                send "$password\r"
                expect eof
EOF
        }
```

---

### Post by sanemanmad on 2010-02-14
Thank you for the reply. I should have mentioned this from the gitgo. I am already exporting 'newpasswd=$2' and regardless it still will not take. Does anyone know if expect still reads from stdin using a here script?

---

