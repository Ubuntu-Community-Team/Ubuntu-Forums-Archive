---
title: "How to run apt-get update/install from behind a proxy"
date: 2013-07-01
forum: Tutorials
---

### Post by Andryg on 2013-07-01
Hi I wrote this script to use apt-get behind a proxy , My password must change everymonth due to company policy's , 
This makes it easier to update, ( you can mayby use this script with cron to force a user to update the password on a specific date 

```
#!/bin/bash
echo "New Username:" 
read usr
echo "New Password:"
read -s pass
echo "Proxy name or address:"
read name
echo "Proxy port:"
read port 


http='Acquire::http::Proxy "http://'"${usr}"':'"${pass}"'@'"${name}"':'"${port}"'/";'
ftp='Acquire::ftp::Proxy "ftp://'"${usr}"':'"${pass}"'@'"${name}"':'"${port}"'/";'
https='Acquire::https::Proxy "https://'"${usr}"':'"${pass}"'@'"${name}"':'"${port}"'/";'


if [ -f /etc/apt/apt.conf ];
then
rm -r /etc/apt/apt.conf
fi
touch /etc/apt/apt.conf
echo $http >> /etc/apt/apt.conf
echo $ftp >> /etc/apt/apt.conf
echo $https >> /etc/apt/apt.conf
```

---

