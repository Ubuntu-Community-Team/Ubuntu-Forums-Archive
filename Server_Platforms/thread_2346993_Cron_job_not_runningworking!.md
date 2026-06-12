---
title: "Cron job not running/working!"
date: 2016-12-20
forum: Server Platforms
---

### Post by agarwaldvk on 2016-12-20
Hi Everyone


I am trying to create a test cron job in preparation for scheduling my backups using 'Backup2l'. The root cron job that I created doesn't seem to work. Could someone please advise where have I gone wrong?

This is how the cron job definition looks like :-

40,42,44 22 20 12 * /home/agarwaldvk/test.sh

The idea is to run the test.sh at the 40th, 42nd and 44th minute past 10 pm (last night) on the 20th day of the month for the month of December. The last parameter was left as '*' as I would have deleted this job later if it had worked - so it would not repeat next year!

The test.sh file contains only one line of code to direct the output of the 'Date' command to a file named 'outputtest.txt' at '/home/agarwaldvk/' location. The code in the test.sh looks like this :-

```

#!/bin/bash
myvar=$(Date)
echo "The program was run at : $myvar" >> /home/agarwaldvk/outputtest.txt

```

I tested this code by running it on the terminal by typing the following command :-

./test.sh

and it ran and directed the output of the above command in the 'outputtest.txt file


BTW, the cron job was created using the following command :-

sudo crontab -e

I did check that this job exists when I typed the command :-

sudo crontab -l



So, why does this cron not run?



P.S.
I shall post the files (both test.sh and outputtest.txt) later tonight after I get home


Best regards


Deepak

---

### Post by ian-weisser on 2016-12-20
'Date' is not a valid command.
'date' (all lower case) will work.

---

### Post by agarwaldvk on 2016-12-20
Hi Ian


Thanks for your response.

I am so sorry - I got that wrong in my initial post. The actual command in the .sh file is "$(date)". I don't have the file here with me and my post was from memory. I will actually include the files later tonight after I get home!

Now that you mentioned it, I do remember that I did use the lower case 'date' rather than 'Date'. I can say that with conviction now because I did run the command from the file standalone and also the file itself on the terminal and they both produced the same output in the 'outputtest.txt file.

Sorry for the misinformation.


Best regards


Deepak

---

### Post by ian-weisser on 2016-12-20
Check the permissions on the output file: ls -l /home/agarwaldvk/outputtest.txt
Does a root cron job have permission to write to the file?

---

### Post by agarwaldvk on 2016-12-20
Hi Ian


I will do that this evening.

One quetion though - if 'agarwldvk' is the owner (I would think that would be the case as I created it having been logged on as 'agarwaldvk') then by default the permission on that file would be at least 655 if not 700.

In both case, wouldn't root cron job have permission to write to it - my understanding - flawed and/or limited as it might be - is that if a cron job has been created as a root cron job then this job would be run as 'root' - and 'root' will have access to everything and to do everything. Is that not correct?


Best regards


Deepak

---

### Post by agarwaldvk on 2016-12-21
Hi All


This is the output of the root cron job that I just ran but I don't see anything in the file that the output of the cron job was redirected to.

Here is the output of log :-

Dec 21 18:35:01 MyHomeServer CRON[23611]: (root) CMD (/home/agarwaldvk/test.sh)
Dec 21 18:35:33 MyHomeServer dhclient[1215]: DHCPREQUEST of 192.168.1.15 on enp3s0 to 192.168.1.254 port 67 (xid=0xd85e4ca)
Dec 21 18:35:33 MyHomeServer dhclient[1215]: DHCPACK of 192.168.1.15 from 192.168.1.254
Dec 21 18:35:33 MyHomeServer NetworkManager[808]: <info>  [1482305733.1247]   address 192.168.1.15
Dec 21 18:35:33 MyHomeServer NetworkManager[808]: <info>  [1482305733.1248]   plen 24 (255.255.255.0)
Dec 21 18:35:33 MyHomeServer NetworkManager[808]: <info>  [1482305733.1248]   gateway 192.168.1.254
Dec 21 18:35:33 MyHomeServer NetworkManager[808]: <info>  [1482305733.1248]   server identifier 192.168.1.254
Dec 21 18:35:33 MyHomeServer NetworkManager[808]: <info>  [1482305733.1248]   lease time 86400
Dec 21 18:35:33 MyHomeServer NetworkManager[808]: <info>  [1482305733.1248]   nameserver '192.168.1.254'
Dec 21 18:35:33 MyHomeServer NetworkManager[808]: <info>  [1482305733.1249]   domain name 'home.gateway'
Dec 21 18:35:33 MyHomeServer NetworkManager[808]: <info>  [1482305733.1249] dhcp4 (enp3s0): state changed bound -> bound
Dec 21 18:35:33 MyHomeServer dbus[776]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Dec 21 18:35:33 MyHomeServer dhclient[1215]: bound to 192.168.1.15 -- renewal in 40809 seconds.
Dec 21 18:35:33 MyHomeServer systemd[1]: Starting Network Manager Script Dispatcher Service...
Dec 21 18:35:33 MyHomeServer dbus[776]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 21 18:35:33 MyHomeServer systemd[1]: Started Network Manager Script Dispatcher Service.
Dec 21 18:35:33 MyHomeServer nm-dispatcher: req:1 'dhcp4-change' [enp3s0]: new request (1 scripts)
Dec 21 18:35:33 MyHomeServer nm-dispatcher: req:1 'dhcp4-change' [enp3s0]: start running ordered scripts...
Dec 21 18:36:47 MyHomeServer crontab[23691]: (root) LIST (root)

Doesn't this tell me that the cron job ran?

the output file permissions are :-

agarwaldvk@MyHomeServer:~$ ls -l ./testoutput.txt
-rw-rw-r-- 1 agarwaldvk agarwaldvk 72 Dec 21 18:30 ./testoutput.txt

Do I need to change the owner/group to root?


Best regards


Deepak

---

### Post by untrustytahr on 2016-12-21
```
 	 	#!/bin/bash
myvar=$(Date)
echo "The program was run at : $myvar" >> /home/agarwaldvk/[COLOR=#ff0000]outputtest.txt[/COLOR] 

```


```
-rw-rw-r-- 1 agarwaldvk agarwaldvk 72 Dec 21 18:30 ./[COLOR=#ff0000]testoutput.txt[/COLOR]
```

these are two different files... or you had another 'from memory' glitch.

---

### Post by agarwaldvk on 2016-12-21
Hi  untrustytahr


Thanks for your response.

Oh, mate, what am I doing? I will retest it and send you all the output of the ls command on the showing the file permissions' details of the correct output file later today when I get home.

Nonetheless, do we think that this could be more related to the absence of MTA rather than file permissions issue?

I, however, did these 3 other things to test if anything else works :-

1. I removed the redirection of the output to a file. Instead, I tried to just display the output to the screen. In this case, I believe the job ran but it gave me the error (in the log file) to the effect of 'No MTA installed, discarding output"


2. I removed the redirection of the output to a file and also specified MAILTO="" as the first statement in the crontab file. Don't remember it now but I believe that the job again ran and again gave me the same error (in the log file) to the effect of 'No MTA installed, discarding output"

3. 1. I tried to redirect the output to a .log file but this file was again empty at the end of the cron job run.

In all cases, I believe the job ran.

I then got caught up in trying to install a MTA (playing with the idea of installing Postfix - seemingly easier to install and configure - but haven't been able to do so yet.

removed the redirection of the output to a file. Instead, I tried to just display the output to the screen. In this case, I believe the job ran but it gave me the error (in the log file) to the effect of 'No MTA installed, discarding output"


Best regards


Deepak

---

### Post by untrustytahr on 2016-12-21
No, you do not need an MTA for cron to work nor do I think it's a permission problem as root would be able to write to any file.  I think the problem is a simple disconnect between what you thought you typed and what you actually did type... aka normal bug.

---

### Post by agarwaldvk on 2016-12-21
Hi


Ok. This is the content on the test.sh file


#!/bin/bash
todaysdatetime=$(date)
mytext="the program has been run at :"
echo "$mytext $todaysdatetime" >> ./testoutput.txt
#echo "$mytext $todaysdatetime" >> ./testoutput.log
#ls

The redirection file is actually "testoutput.txt

The output file permissions are :-
 agarwaldvk@MyHomeServer:~$ ls -l ./testoutput.txt
-rw-rw-r-- 1 agarwaldvk agarwaldvk 72 Dec 21 18:30 ./testoutput.txt


The contents of the output file are :-
agarwaldvk@MyHomeServer:~$ cat ./testoutput.txt
the program has been run at : Wednesday 21 December  18:30:52 AEDT 2016

after running the script file manually

I will try and execute the cron job as well and show you the contents of the output file shortly.




Deepak

---

### Post by steeldriver on 2016-12-21
It's not recommended to use relative paths such as

```

./testoutput.txt

```

in these contexts - remember `cron` won't be running this in your user's home directory (likely you will find a file called 'testoutput.txt' in the filesystem root directory, `/`)

---

### Post by agarwaldvk on 2016-12-21
Hi Steeldriver


Thanks. I will change the path specifying the paths as absolute paths like so :-

/home/agarwaldvk/testoutput.txt

and hopefully this time around it might just work.

Will keep you posted.


Deepak

---

### Post by agarwaldvk on 2016-12-21
Hi Steeldrive

That seemed to have worked. No worries at all.

Hi untrustytahr
As advised by Steeldrive, I just needed to specify the full path and not the relative path and it worked.


Thanks to all of you for that  - greatly appreicated.

The  next issue is that I don't get any notification of this job having been run when the output is redirected to a file. Is this because I don't have any messaging application installed as yet?

However, when the redirection is taken out of the equation, it comes up with the error saying that I have no MTA installed and hence the output is being discarded.

To be notified in both these scenarios, would it notify me if I were to install the 'ssmtp' application or similar say 'Postfix' ?



Best regards


Deepak

---

### Post by kevdog on 2016-12-21
Ok guys I'm going to take a stab at this one.

Unfortunately cron doesn't have  user environment like a user.   You've already proven your script works manually if you invoke the script at the command line of a normal user, however I believe you've stated it doesnt work in a cron type environment.

You've listed the cron job as the following:
```

40,42,44 22 20 12 * /home/agarwaldvk/test.sh

```

Here is however is what I would have your crontab look like:
```

SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin  #<---MODIFY THE PATH TO INCLUDE PATH TO BASH
40,42,44 22 20 12 * /home/agarwaldvk/test.sh

```

You can see the above code assigns a shell to the cron command -- the bash shell is more inclusive than the normal shell.  In terms of permission..I believe if you just activate the executable bit for the appropriate user you'll be fine.

---

### Post by Graham_Willis on 2016-12-22
[quote="agarwaldvk"]The next issue is that I don't get any notification of this job having been run when the output is redirected to a file. Is this because I don't have any messaging application installed as yet?

However, when the redirection is taken out of the equation, it comes up with the error saying that I have no MTA installed and hence the output is being discarded.[/quote]

What exactly do you mean? First, by "notification" do you mean something what is displayed on the screen, gets written to the file or an e-mail notification? When you start your script by hand, do you get this notification?

---

### Post by agarwaldvk on 2016-12-22
Hi Graham


Just saw your message.

Sorry I just presumed that it could only be by email. Yes, I was looking at notifications by email.


Best regards


Deepak

---

### Post by agarwaldvk on 2016-12-22
Hi Kevdog


Thanks for your response but how is that going to help! Please educate me on that! I don't know very much about these things!


Best regards


Deepak

---

### Post by ian-weisser on 2016-12-22
One simple option to get the (discarded) output is 'redirection'. Then you can see what the error is.
You probably ran across it while looking for instructon on writing the cronjob.

1 1 1 1 1 /path/to/script > /path/to/output 2>&1

Add '2>&1' to redirect error messages into the normal output.
You should see the error messages in  your output file.
No need for an MTA.

---

### Post by agarwaldvk on 2016-12-22
Hi Ian


Thanks again!


What if the script only 'echo'ed the contents of a variable like so :-

echo "$myvar"

and the cron job was something like this :-

1 1 1 1 1 /path/to/script

then, would the contents of the variable 'myvar' not be displayed on the screen - the normal output device by default as also the error messages?

The reason I ask this is that when I had my script file to just echo the contents of a variable on the screen by not redirecting the output anywhere, and the script was run as a part of the cron job, nothing was displayed on the screen and log said the output was being discarded as there was not MTA installed. Of course, the cron job did not have the path of output speciified - I had only specified the script file to run on the assumption that output would go the normal stdout - the screen!

Why do I need to specify the cron job like so (what you have shown) :-


1 1 1 1 1 /path/to/script > /path/to/output 2>&1                  #redirect normal output to screen and error to discard


Best regards


Deepak

---

### Post by ian-weisser on 2016-12-22
> **agarwaldvk said:**
> 
echo "$myvar"
[...]
then, would the contents of the variable 'myvar' not be displayed on the screen [...]?

Correct. myvar will NOT be displayed on a screen in a cronjob.
Cron runs headless. There is no display associated with the cron environment for echo display to.

> **agarwaldvk said:**
> Why do I need to specify the cron job like so (what you have shown)

Redirection is simply easier than installing an MTA to learn what the error is. You may structure your cron job any way you wish.
2>&1 does not discard stderr. Look at it again.

---

