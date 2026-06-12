---
title: "Email and Texting commands Howto:"
date: 2011-01-22
forum: Server Platforms
---

### Post by jeff.sadowski on 2011-01-22
If you have any questions I will answer them here.
I'd like structural comments if you disagree with some aspect of my solution to a computer that can respond to emails I'd like to here them. I think I locked my computer pretty tight but I could be wrong.

create a separate account than the one you use all the time.
create an email account for your computer on gmail.

login as this user that will read and execute commands
setup fetchmail to read the google account.

.fetchmail
```

poll pop.gmail.com with proto POP3 and options no dns
user '<servers gmail account>@gmail.com' there with password '<your computers email password>' is '<user you created to take and run commands>' here  options ssl

```

script to read and run commands

verify_and_run.sh
```

#!/bin/bash

onemail(){ 
#see how many messages there are
let cut=`echo q|mail|wc -l`-1
#get the first unread message from the mail program
message=`echo 1|mail 2>/dev/null`;
# get rid of the last 3 lines because they came from the mail program
let HEAD=`echo -e "$message"|wc -l`-3
# get rid of the first ${cut} lines because they came from the mail program
let TAIL=${HEAD}-${cut}
MSG=`echo -e "$message"|head -n $HEAD|tail -n $TAIL`
echo -e "$MSG"
#save the message
if [ "${MSG}" != "" ];then
FROM=`echo -e "$MSG"|grep -i "^From: "|sed "s/^From: //"|sed "s/.*<//"|sed "s/>.*//"|tr '[A-Z]' '[a-z]'`
SAVETO=`echo $FROM|cut -d@ -f1`
if [ "$SAVETO" = "" ];then
 SAVETO=unknown
fi
echo -e "$MSG" >> "${HOME}/Mail/${SAVETO}"
echo >> "${HOME}/Mail/${SAVETO}"
fi
}

# get email setup in .fetchmailrc
fetchmail -vk 2>/dev/null 1>/dev/null
message=`onemail`
FROM="nobody"
MSG="no mail"
while [ "${message}" != "" ];do
 FROM=`echo -e "$message"|grep -i "^From: "|sed "s/^From: //"|sed "s/.*<//"|sed "s/>.*//"|tr '[A-Z]' '[a-z]'`
 TOTAL=`echo -e "$message"|wc -l`
 BEFORE=`echo -e "$message"|grep -n "^$"|head -n 1|cut -d: -f1`
 let TAIL=${TOTAL}-${BEFORE}
 MSG=`echo -e "$message" | tail -n $TAIL`
 if [ -f "${HOME}/.trusted/${FROM}" ];then
  FIRST_WORD=`echo -e "$MSG"|head -n 1|awk '{print $1}'`
  if [ -f ${HOME}/.commands/${FIRST_WORD} ];then
   if [ "`echo -e "$MSG"|grep -n "^>"`" != "" ];then
    let NEW=`echo -e "$MSG"|grep -n "^>"|head -n 1|cut -d: -f1`-3
    REST=`echo -e "${MSG}"|head -n ${NEW}`
   else
    REST=`echo -e "${MSG}"`
   fi
   REST=`echo ${REST}|sed "s/.*${FIRST_WORD}//"`
   export FROM
   ${HOME}/.commands/${FIRST_WORD} ${REST} 2>/dev/null 1>/dev/null
  fi
 fi
 message=`onemail`
 FROM="nobody"
 MSG="no mail"
done

```

create a .trusted directory
```

mkdir .trusted

```

create users that can send commands to run via email/txtmessaging
```

cd .trusted
# for verizon
touch <10 digit phone number>@vtext.com
# for sprint
touch <10 digit phone number>@messaging.sprintpcs.com
touch <email address you want capable of sending commands>

```

create a .commands directory for commands you might want the users to run
```

mkdir .commands

```

create some useful commands
.commands/run
```

#!/bin/bash
file1=`tempfile -d /tmp -p stdo_ -s .txt`
file2=`tempfile -d /tmp -p stde_ -s .txt`

/bin/bash -c "$*" 2>${file1} 1>${file2}

if [ "${FROM}" != "" ];then
echo -e "stderr:`cat ${file1}`\rstdout:`cat ${file2}`" | sudo /usr/sbin/scripts/sendEmail \
          -t "${FROM}" \
           1> /dev/null 2>/dev/null
else
echo stderr:`cat ${file1}`
echo stdout:`cat ${file2}`
fi
rm -rf ${file1}
rm -rf ${file2}

```

/usr/sbin/scripts/sendEmail
```

#!/bin/bash
username="<servers gmail account>"
password="<servers password for its gmail account>"

sendEmail -f "${username}@gmail.com" \
          -s smtp.gmail.com:587 \
          -o tls=yes \
          -xu "${username}" \
          -xp "${password}" \
          $*

```

```

chmod go-wrx /usr/sbin/scripts
echo "<user you created to accept and run email>  ALL=NOPASSWD:/usr/sbin/scripts/sendEmail,/etc/init.d/ssh,/usr/bin/apt-get,/usr/sbin/scripts/allow.sh" >> /etc/sudoers

```

/usr/sbin/scripts/allow.sh
```

#!/bin/bash
iptables -I INPUT 1 -s $1 -j ACCEPT

```

.commands/allow
```

#!/bin/bash
sudo /usr/sbin/scripts/allow.sh $1

```

I have a firewall creating script that looks as follows
/etc/init.d/setupiptables
```

start(){
for ip in `grep -v -e "^;" -e "^$" /etc/whitelist`;do /usr/sbin/scripts/allow.sh $ip;done
iptables -A INPUT -s 127.0.0.1 -j ACCEPT
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A INPUT -s 0.0.0.0/0 -j DROP
}

stop(){
iptables -F
}

restart(){
stop
start
}

usage(){
 echo "$0 start|stop|restart"
}

case "$1" in
start)
        start
;;
stop)
        stop
;;
restart)
        restart
;;
*)
        usage
;;
esac

```

/etc/whitelist
```

192.168.0.0/24

```

I have a script that removes non whitelisted addresses every night at midnight

/root/remove_non_whitelistings.sh
```

greplist=" -v -e 127.0.0.1 -e RELATED -e DROP -e ^Chain -e ^target -e ^\$"
for ip in `cat /etc/whitelist`; do
 greplist="${greplist} -e $ip"
done
/sbin/iptables -L -n |grep ${greplist} > /tmp/removed.txt
rid=`/sbin/iptables -L -n |grep ${greplist}|awk '{print $4}'`

for ip in ${rid}; do
/sbin/iptables -D INPUT -s $ip -j ACCEPT
done

```

and roots crontab looks as follows
```

0 0 * * * /root/remove_non_whitelistings.sh

```

.commands/myip
```

#!/bin/bash
file1=`tempfile -d /tmp -p stdo_ -s .txt`
file2=`tempfile -d /tmp -p stde_ -s .txt`

/bin/bash -c "${HOME}/.commands/myip.sh" 2>${file1} 1>${file2}

if [ "${FROM}" != "" ];then
echo -e "stderr:`cat ${file1}`\rstdout:`cat ${file2}`"|sudo /usr/sbin/scripts/sendEmail \
          -t "${FROM}" \
           1> /dev/null 2>/dev/null
else
echo stderr:`cat ${file1}`
echo stdout:`cat ${file2}`
fi
rm -rf ${file1}
rm -rf ${file2}

```

${HOME}/.commands/myip.sh
```

#!/bin/bash
ip=`lynx -dump http://www.Whatismyip.Com |grep "Your IP Address Is"|cut -d: -f2`
echo $ip

```

user that reads and executes commands crontab
```

* * * * * ${HOME}/verify_and_run.sh

```


this makes it so that no one not even I can ssh to my box without first sending "allow <ipaddress of box I am sitting at>" from a trusted email address unless I am on my 192.168.0.0/24 subnet that is in my whitelist.

I first send the command "myip" to my servers email address from my phone
then I lookup the address of the machine I am sitting at. Then I send
"allow <ipaddress of box I am sitting at>" from my phone and wahla I can ssh to my box next time my script reads email in less than a minute.

then at midnight the firewall is reset and my box is locked down again.

---

