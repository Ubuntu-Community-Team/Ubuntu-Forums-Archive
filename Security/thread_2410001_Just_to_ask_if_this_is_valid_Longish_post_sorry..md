---
title: "Just to ask if this is valid? Longish post sorry."
date: 2019-01-09
forum: Security
---

### Post by adrian-h on 2019-01-09
I have a very simple and small server that is hosting a trial setup in GPS tracking, it is not commercial but I have ports open to the outside world for it to work, I am unsure how to monitor activity on the ports needed for the GPS devices to see if the open ports are being spammed by any bots.  So I look to apache logs and ssh logs for guidance, for example I leave the ssh port open to the outside work for a set period of time, a bit like a 'honey pot'

Look at the logs and then add IP rules with ufw.

I see these messages in the apache2 access.log where bots rea trying to attach mysql etc

I open the ssh port for a set period a bit like a honey pot to see what is IP is attaching and I tend to close off whole swathes of addresses where I see several say in the 118 range or 221 range.  i do check the would not effect my server but as it is a test server and used only for family within the UK I do not see an issue.

I use a command line to give me a simple report such as :
```
cat /var/log/apache2/access.log | grep '09/Jan' | grep -E -o "([0-9]{1,3}[\.]){3}[0-9]{1,3}" | sort | uniq -c | sort -nr
```
for the apache log and
```
cat /var/log/auth.log | grep 'Jan  9' | grep -E -o "([0-9]{1,3}[\.]){3}[0-9]{1,3}" | sort | uniq -c | sort -nr
```
for ssh.

Now to my question, it seems to my mind it is faster to have the ufw rules ordered by magnitude, but I am unsure if this is OK or just to have the rules in any order as may be presented first come first banned by a program.

So I have set my rules simply structured as below.

[ 1] Anywhere                   DENY IN     60.0.0.0/6                
[ 2] Anywhere                   DENY IN     218.0.0.0/7               
[ 3] Anywhere                   DENY IN     222.0.0.0/7               
[ 4] Anywhere                   DENY IN     85.0.0.0/8                
[ 5] Anywhere                   DENY IN     87.0.0.0/8                
[ 6] Anywhere                   DENY IN     88.0.0.0/8                
[ 7] Anywhere                   DENY IN     91.0.0.0/8                
[ 8] Anywhere                   DENY IN     217.0.0.0/8               
[ 9] Anywhere                   DENY IN     45.119.0.0/16             
[10] Anywhere                   DENY IN     58.242.0.0/16             
[11] Anywhere                   DENY IN     114.224.0.0/16            
[12] Anywhere                   DENY IN     117.156.0.0/16            
[13] Anywhere                   DENY IN     125.72.0.0/16             
[14] Anywhere                   DENY IN     129.28.0.0/16             
[15] Anywhere                   DENY IN     134.175.0.0/16            
[16] Anywhere                   DENY IN     103.89.88.0/22            
[17] Anywhere                   DENY IN     41.234.140.0/24           
[18] Anywhere                   DENY IN     119.4.250.0/24            
[19] Anywhere                   DENY IN     121.235.201.0/24          
[20] Anywhere                   DENY IN     155.4.69.0/24             
[21] Anywhere                   DENY IN     185.143.223.0/24          
[22] Anywhere                   DENY IN     196.52.43.0/24

Am I correct in my thinking, or is this a waste of time and it makes no difference to the computer.  All i know is one attach on 22 took the processor up to 28% from idle so my brain thinks keep it structured to drop the ranges first?

Adrian

---

### Post by SeijiSensei on 2019-01-09
If you know where legitimate traffic originates, it's a lot easier to permit those sources and deny everything else.  For instance, my public servers only accept SSH connections from networks I control.  
```
/sbin/iptables -A INPUT -s 10.10.10.0/24 -p tcp --dport 22 -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 22 -j REJECT 

```
That allows SSH traffic from 10.10.10.0/24 and denies all other connections.,

Doing it the other way around is a lot more work.

---

### Post by adrian-h on 2019-01-09
@SeijiSensi

Yes I can understand what you are saying.

Some times however, when using a mobile connection as yet I have to learn where my own connection could be as there are several networks and ranges they use.

But two questions, the gps ports I use somewhere in the 5xxx range, the app logs are only showing INFO status i.e. what is working OK I can not see if the ports are being spammed, so is checking other logs valid and is a structured approach as I am trying to keep better than listing IP's in a first come banned list, does it save on cpu cycles having them structured.?

Adrian

---

### Post by SeijiSensei on 2019-01-11
```
/sbin/iptables -I INPUT -p tcp --dport 5xxx -j LOG
```

will write a record to /var/log/kern.log for every packet that arrives on port 5xxx.  If you're running a UDP service, replace "tcp" with "udp".

---

### Post by adrian-h on 2019-01-12
@SeijiSensei

Sorry I did not see your reply I am not getting any messages to say anyone has replied, even though set as email.
I will have a go thank, you for your response.

Cheers

Adrian.

p.s.

Just wondering, as I am learning all this and basically I have been using UFW to set rules and these included a few fules such as:
sudo ufw allow 5xxx

I will see if I can also include logging to that.  

I had a look at iptables -L and the output put me off a bit, it needs a lot of understanding on my part.

I will read more community docs, see if I can follow it better, then give it a go when I am not tired.

---

### Post by SeijiSensei on 2019-01-14
The rule I wrote will be placed above all the other rules in the INPUT chain because I used the "-I" parameter.

So you can run your usual UFW rules, then add the rule I specified from the command prompt.  You'll need to preface the command with sudo since you need root privileges to modify the firewall rules.

Rather than relying on email notices, you could just revisit this URL a few times a day.

---

### Post by adrian-h on 2019-01-14
Thank you , I could not find a line to use in ufw apart from a general one to set logging level.

My router is dealing with port scans generally so they are not filtering down to my home server, but quick question I can add this rule and give it a try for a while and see what the port is putting up with, would I delete it by using sudo nano type messages and I am assume it would be in any before rules, think I have the correct, or would there be another command line to remove it?

to install 

[SIZE=2][FONT=arial]cd/sbin 
sudo iptables -I INPUT -p tcp --dport 5xxx -j LOG


To remove
cd/sbin[/FONT][/SIZE][SIZE=2][FONT=arial]
sudo iptables -D INPUT -p tcp --dport 5xxx -j LOG

Sorry I am being cautious as I just managed to screw one backup server up, it's how I learn

And I did get an email for your response this time, who would have guessed it!

I appreciate your time to answer.  I am also having fun reporting and blocking web app attacks from IP's

Adrian
[/FONT][/SIZE]

---

### Post by SeijiSensei on 2019-01-14
Yes, you would use -D to remove the rule.

You don't need to be in the /sbin directory.  It's in the standard PATH:

```

$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:**/sbin**:/bin:/usr/games:/usr/local/games:/snap/bin

```

so you can just type "sudo iptables ..." from anywhere in the filesystem.

---

### Post by adrian-h on 2019-01-14
[SIZE=2]Thank you very much.

Adrian
[/SIZE]

---

