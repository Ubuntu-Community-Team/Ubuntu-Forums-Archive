---
title: "new to ufw, how to block country IPs"
date: 2012-02-25
forum: Security
---

### Post by honeyjar on 2012-02-25
I started using ufw to configure ubuntu firewall.

At the moment I have a basic setup that blocks all traffic except a few ports that I want:
```

sudo ufw default deny incoming
sudo ufw default deny outgoing
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 25/tcp
sudo ufw allow 443/tcp
sudo ufw enable
```

- My first question is, will this block udp traffic since I specified the default to deny incoming and outgoing?

- My second questions is, how can I get ufw to insert rules to block the IPs listed on the website? I know I have to write a script that wgets the files, but I'm not sure how to apply it to ufw. Furthermore, even if there's a way to apply it, how would one easily allow access by country again? Is there something along the lines of:

```

sudo ufw deny India.txt
sudo ufw deny Sweden.txt

Then if I want:
sudo ufw allow India.txt
sudo ufw allow Sweden.txt

```

 The list of IPs by country is here:  [http://www.ipdeny.com/ipblocks/](http://www.ipdeny.com/ipblocks/)

- My third question is, if someone uses a proxy to bypass the above deny by country IP, is there a way for ufw to automatically block that specific IP after a certain amount of tries? I know there's the limit command:

ie, 
```
sudo ufw limit ssh/tcp

```
But I am unsure if the IP will be blocked permanently or just temporarily by ufw? That is, will it automagically insert rules before my other rules that I've defined, and it'll show up in ufw status?

---

### Post by arxel on 2012-06-13
Were you able to find the solution for this? 

Also looking for this.

---

### Post by rdsmith12 on 2012-12-25
I was trying to figure out how to block China because I was finding in my system logs a lot of attempts from China, Viet Nam, Philipines (and the US) to log in via ssh. I was adding all those IP addresses manually in ufw.

I got to thinking and found this script at nixCraft called "Linux Iptables Just Block By Country" [http://www.cyberciti.biz/faq/block-entier-country-using-iptables/](http://www.cyberciti.biz/faq/block-entier-country-using-iptables/)

The instructions are pretty straight forward but had to figure out crontab though.
Here's the howto for crotab.
[http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/](http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/)
Check it out.
I ran the script jsut before replying.

---

### Post by chadk5utc on 2012-12-25
This is really simple to do with iptables I will include the script I use and a sample ipaddress list. First create a new file:> 
#!/bin/bash
# add Banned IP's to firewall can be single IP, CIDR, or a RANGE
#
BLOCK_LIST=/root/cidr.txt
if [ ! -f $BLOCK_LIST ]
then
echo "Unable to add blocks to IPTABLES because file $BLOCK_LIST is missing"
exit
fi
CURRENT_RULES=`iptables -nL`

while read entries ;do
# skip comment lines starting with ; or #
case $entries in
\#*|\;*)
continue
;;
esac

if [[ $CURRENT_RULES =~ $entries ]]
then
printf "%-20s %20s\n" $entries 'already referenced in iptable - skipping'
else
# is this CIDR, range or single IP?
if [[ $entries =~ "-" ]]
then
#--src-range
printf "%-20s %20s %1s %1s\n" 'ADDING RULE:' 'iptables -A INPUT --src-range' $entries '-j DROP'
iptables -A INPUT --src-range $entries -j DROP
else
#--CIDR or single
printf "%-20s %20s %1s %1s\n" 'ADDING RULE:' 'iptables -A INPUT -s' $entries '-j DROP'
iptables -A INPUT -s $entries -j DROP
fi
fi
done < $BLOCK_LIST
 I saved this as filename:ban then chmod +x ban to make this exacutable
Then create a filenamed cidr.txt for all the addresses you want blocked
> 5.132.9.0/24
5.224.9.0/24
5.225.9.0/24
 within this file save addresses one per line so the script will read them there are a few sites online that will create a list for you based on Country then to run the file type> ./banand it will display as it creates the iptables rules also worth mentioning some of the scripts found online to do this will also create a number of other iptables settings the script I have posted strictly blocks addresses listed in the cidr.txt only. Then once you have set all firewall rules you need and want to save then type> iptables-save > whateverfilename this will save them, then youll need to do a few more things to ensure they survive a reboot. Directions for that can be found here [http://www.debian-administration.org/articles/445](http://www.debian-administration.org/articles/445)

---

