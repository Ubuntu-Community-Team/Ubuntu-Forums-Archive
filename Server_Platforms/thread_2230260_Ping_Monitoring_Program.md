---
title: "Ping Monitoring Program"
date: 2014-06-18
forum: Server Platforms
---

### Post by 74kumi on 2014-06-18
Here is my current project: I work for a small ISP and answer tech calls on occasion. When a customer calls in to complain about an "intermittent connection" we currently start a ping and let it run over night if no issues arise we cancel the process and don't worry about it. The issue comes up because we have multiple technicians that do this test and its not documented at all, and if a customer calls back and they talked with tech A yesterday and today they talk with tech B then maybe talk to tech C the next day we just ran 3 overnight tests for the same customer with no documented results. 

So the system im working on is to be simple, tech ssh to server with ping as user soon as they are logged in they are prompted for customers display name, and IP. then are forced to log off. The script should start a ping with time stamps for ever failed ping and write that to a file in /var/www/pings, I already have the webpage setup to display any logs in the folder to my index page. The part where im having issues is with the script and permissions. Since i only gave root permissions to ping to only run one file that script its having some issues with writing or cating. 

script i wrote 
```
#!/bin/bash

echo "Enter Displayed Name for Customer:"
read name
echo "Enter Ip Address (example:192.168.1.1):"
read ip


echo "cat | pingi $ip  |grep --color=auto --color=auto down >> /var/www/$name &"


sudo touch /var/www/pings/$name
sudo chmod 777 /var/www/pings/$name
sudo bash -c "cat | pingi $ip |grep --color=auto down >> /var/www/pings/$name &"



```

pingi script im using
```
#!/bin/bash

host=$1


if [ -z $host ]; then
    echo "Usage: `basename $0` [HOST]"
    exit 1
fi


while :; do
    result=`ping -W 1 -c 1 $host | grep 'bytes from '`
    if [ $? -gt 0 ]; then
        echo -e "`date +'%Y/%m/%d %H:%M:%S'` - host $host is down"
    else
         echo -e "`date +'%Y/%m/%d %H:%M:%S'` - host $host is \033[0;32mok\033[0m -`echo $result | cut -d ':' -f 2`"
        sleep 1 # avoid ping rain
    fi
done



```

and current results
```
ping@shinku:~$ sudo ./ping Enter Displayed Name for Customer:
test
Enter Ip Address (example:192.168.1.1):
8.8.8.8
cat | pingi 8.8.8.8  |grep --color=auto --color=auto down >> /var/www/test &
ping@shinku:~$ cat: -: Input/output error



```

check list
[LIST]
[*]working script
[*]execute on log-in
[*]log-off when done
[/LIST]

If anyone wants more information about just about anything related ill see what i can do.
Thanks

---

### Post by defunkt on 2014-06-18
Try This:
Launcher script to run the pingi script
```

#!/bin/bash

echo "Enter Displayed Name for Customer:"
read name
echo "Enter Ip Address (example:192.168.1.1):"
read ip

sudo mkdir -p /var/www/pings/
sudo chmod -R 755 /var/www/pings
echo "echo -e "`date +'%Y/%m/%d %H:%M:%S'` - Monitoring started" >> /var/www/pings/$name

./pingi $ip | grep --color=auto down >> /var/www/pings/$name &

```



I did not touch the pingi script... but here it is anyway.


```

#!/bin/bash

host=$1


if [ -z $host ]; then
    echo "Usage: `basename $0` [HOST]"
    exit 1
fi


while :; do
    result=`ping -W 1 -c 1 $host | grep 'bytes from '`
    if [ $? -gt 0 ]; then
        echo -e "`date +'%Y/%m/%d %H:%M:%S'` - host $host is down"
    else
         echo -e "`date +'%Y/%m/%d %H:%M:%S'` - host $host is \033[0;32mok\033[0m -`echo $result | cut -d ':' -f 2`"
        sleep 1 # avoid ping rain
    fi
done

```

---

### Post by 74kumi on 2014-06-18
After a few changes i was able to get that to work
```


echo "Enter Displayed Name for Customer:"
read name
echo "Enter Ip Address (example:192.168.1.1):"
read ip


sudo mkdir -p /var/www/pings/
sudo chmod -R 755 /var/www/pings
echo " `date +'%Y/%m/%d %H:%M:%S'` - Monitoring started" >> /var/www/pings/$name


pingi $ip | grep --color=auto down >> /var/www/pings/$name &



```

Is there anyway to add a PID number after the Monitoring started date? Just so i can kill it later without killing the wrong monitoring.

---

### Post by defunkt on 2014-06-18
echo $$ 

would produce the PID of the running process.  So adding that below should work.

---

