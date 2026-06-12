---
title: "Wget Bash script restarting autossh and eth0 help"
date: 2013-04-03
forum: Server Platforms
---

### Post by Iamawesome on 2013-04-03
I just need some pointers on this script I am making. My goal is to have the server check that it is connected by using wget to three remote servers. I am going with three different remote servers in case any of them is ever down. If it does not receive any connections then it will restart eth0 and restart autossh. I want to try to stay away from curl. I am failing miserably at this script, any help would be greatly appreciated!


> #!/bin/bash


command1=`wget -c -t 0 http://server1/folder/ifuptest.txt`;
command2=`wget -c -t 0 http://server2/folder/ifuptest.txt`;
command3=`wget -c -t 0 http://server3/folder/ifuptest.txt`;


if [ $command1 -ne 0 ]
   then
      echo "wget finished normally on command 1"
   else
      echo "first wget failed $(date)" >>/home/admin/wgettest/ifconfig_results.txt
      if [ $command2 -ne 0 ]
         then
            echo "wget finished normally on command 2"
         else
            echo "second wget failed $(date)" >>/home/admin/wgettest/ifconfig_results.txt
            if [ $command3 -ne 0 ]
               then
                  echo "wget finished normally on command 2"
               else
                  echo "third wget failed $(date)" >>/home/admin/wgettest/ifconfig_results.txt
                  echo "wget finished unsuccessful $(date)"
                  TIMESTAMP=`date "+%Y-%m-%d %T"`
                  
                  /sbin/ifdown eth0
                  /sbin/ifup eth0
                  /etc/init.d/autossh stop
                  /etc/init.d/autossh start
            fi
      fi
fi


rm /home/admin/wgettest/ifuptest.txt


exit 0

---

### Post by schragge on 2013-04-03
To begin with, don't forget about quoting:
```
[ $command1 -ne 0 ]
``` should be ```
[ "$command1" -ne 0 ]
``` though I doubt it would work in any case. What exactly are you trying to check? Whether $command1 is empty? Then the proper test would be
```
[ -n "$command1" ]
``` I have many other questions to the code. Why aren't you just using ping?  Why are you setting wget options **-t 0** (infinite retries) and **-c** (continue)? Why so many *else*s? I don't think it's a valid shell syntax. Why are you saving the output of wget in variables when the only purpose of running wget is checking if a connection is alive? Why not just
```
if wget &#8230;;then
``` or even better doing this in a loop
```

fail=0
for server in server1 server2 server3;do
  if wget -q "$server";then
    echo wget has successfully connected to $server
    break
  fi
  ((fail++))
# logging the failure
done

if ((fail==3));then
  /sbin/ifdown eth0
  /sbin/ifup eth0
  /sbin/restart autossh
fi

```

---

### Post by Iamawesome on 2013-04-04
Thank you for the response schragge, I think i just threw my hands up after editing this test script over and over. I have people who are remote who just unplug their servers or have poor network connections/equipment and they think I am the go to guy 24/7. I am trying to avoid a phone call in the middle of the night. I am running this as a cron. I did use and it worked ok for the time....

> #!/bin/bash

if ! `ping -c 1 -w 1 -q [www.webaddress.com](www.webaddress.com) </dev/null &>/dev/null` ; then
echo "resetting eth0 $(date)" >>/home/admin/ifconfig_results.txt
TIMESTAMP=`date "+%Y-%m-%d %T"`
mysql -u admin -nonyabiz -e "INSERT INTO tbl_sometable"
/sbin/ifdown eth0
/sbin/ifup eth0
/etc/init.d/autossh stop
/etc/init.d/autossh start
else
echo "eth0 operational $(date)" >>/home/admin/ifconfig_results.txt
fi

exit 0



This was great for restarting their connection and getting autossh reconnected but now I am starting to run into proxy issues where the ping wont work.

---

### Post by Iamawesome on 2013-04-10
I tried this again and got it working correctly. It will search fro the wget file you downloaded and if it is not there it will reset eth0 and restart autossh. It also writes to my DB table I created. If you only need it to restart eth0 remove any of the lines with autossh in them. Leaving this here if anyone needs it in the future.

> #! /bin/bash





wget -T 3 /home/admin/iftest.txt [http://sometestserver.com/iftest.txt](http://sometestserver.com/iftest.txt) ;
wget -T 3 /home/admin/iftest.txt [http://sometestserver2.com/iftest.txt;](http://sometestserver2.com/iftest.txt;)
wget -T 3 /home/admin/iftest.txt [http://sometestserver3/iftest.txt;](http://sometestserver3/iftest.txt;)




           if [ ! -f "/home/admin/iftest.txt" ];
              then
                TIMESTAMP=`date "+%Y-%m-%d %T"`
                  mysql -u admin -enterpassword -e "INSERT INTO mysqldb.tbl_connectionLog
                                                         VALUES
                                                       ('$TIMESTAMP', 'Internet Connection Automatically Reset', 0, 'admin', 'Y');"
                sudo  /sbin/ifdown eth0
                sudo  /sbin/ifup eth0
                sudo killall autossh
                sudo killall autossh
                sudo killall autossh
                sudo killall autossh


                cd /usr/local/etc/autossh.d/ && ./0.conf
                cd /usr/local/etc/autossh.d/ && ./1.conf
                cd /usr/local/etc/autossh.d/ && ./2.conf
                cd /usr/local/etc/autossh.d/ && ./3.conf


                  rm /home/admin/iftest.tx*
           fi


rm /home/admin/iftest.tx*

exit 0

---

### Post by Habitual on 2013-04-10
> **Iamawesome said:**
> ```
sudo killall autossh
sudo killall autossh
sudo killall autossh
sudo killall autossh
```what's "that" about?

---

