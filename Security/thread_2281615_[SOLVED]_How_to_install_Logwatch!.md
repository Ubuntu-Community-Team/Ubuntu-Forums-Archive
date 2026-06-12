---
title: "[SOLVED] How to install Logwatch!"
date: 2015-06-08
forum: Security
---

### Post by patrikmellq on 2015-06-08
Hello - Logwatch is a program that watch your system and creates logs.
You can pick different levels of your logs of your system - low, medium and high.
And you can pick what to monitor with your logging - http, sudo and more ...
This is a great way monitor you system - where you can pick to get yeasterdays logs or todays logs sent to your email.

First i just want to tell you how difficult it was to get all this working.
I try to get a working email system to work with my Ubuntu so Logwatch can send me emails using my Ubuntu system.
And i end up trying to configurating Postfix - i follow many guides online and none working.
This made me very angry.

But thanks to this great forum i describe my issue and got help to solve my problem.
A user suggest me to install SSMTP instead of Postfix and it did work direct after the first install and configuration.
After that i was going to install Logwatch - but then i notice that the guides say different things how to install Logwatch.
This was at first confusing - but at the end i solve the wrong information to a working solution to install and configurating Logwatch.

1) So now i will show you how to install and configurating the mail software SSMTP so you can get emails from Logwatch.

2) After getting SSMTP working i will show you how to install and configurating LOGWATCH.

3) During this installation process you need a gmail.com account to get this guide to work.
[B]
Installing and configurationg SSMTP to send emails from your Ubuntu system[/B]

First you run the following code to get updated system:

```

sudo apt-get update

```

After that you install ssmtp

```

sudo apt-get install ssmtp

```

Now you will open a text file using a editor with the name nano.
After editing a file you click on "ctrl" and "o" to save the changes and click "enter" then close nano with "ctrl" and "x"
This is the all commands you need to open, save and close using nano.

Type the following in the command line:

```

sudo nano /etc/ssmtp/ssmtp.conf

```

Then you will get a file and it should look like this:
You have to add the missing parts and add your email.

```

# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
#root=postmaster
root=MyEmailAddress@gmail.com

# The place where the mail goes. The actual machine name is required no
# MX records are consulted. Commonly mailhosts are named mail.domain.com
#mailhub=mail
mailhub=smtp.gmail.com:587

AuthUser=MyEmailAddress@gmail.com
AuthPass=MyPassword
UseTLS=YES
UseSTARTTLS=YES

# Where will the mail seem to come from?
#rewriteDomain=
rewriteDomain=gmail.com

# The full hostname
#hostname=MyMediaServer.home
hostname=MyEmailAddress@gmail.com

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
FromLineOverride=YES - See more at: http://www.havetheknowhow.com/Configure-the-server/Install-ssmtp.html#sthash.vpOeOryu.dpuf

# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
#root=postmaster
root=MyEmailAddress@gmail.com

# The place where the mail goes. The actual machine name is required no
# MX records are consulted. Commonly mailhosts are named mail.domain.com
#mailhub=mail
mailhub=smtp.gmail.com:587

AuthUser=MyEmailAddress@gmail.com
AuthPass=MyPassword
UseTLS=YES
UseSTARTTLS=YES

# Where will the mail seem to come from?
#rewriteDomain=
rewriteDomain=gmail.com

# The full hostname
#hostname=MyMediaServer.home
hostname=MyEmailAddress@gmail.com

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
FromLineOverride=YES

```

When you are done you can test to send email to your gmail account.
But at first it will not work because gmail will complain about you being spamming the email account and also issue how the deamon can know your password to your gmail account.
Then gmail will ask if you want to change secutiry settings and you should answaer yes or activate the funktion allowing emails from your Ubuntu system.
When this is done you can test send email again - then it should work just fine.

This is how you send email using the command line with ssmtp:

```

ssmtp recipient_YourEmail@gmail.com

```

Afer typing this into the command line you click on Enter and type your message.
For example:

```

Hello world

```

After that you need to end this session with Ctrl D.
Now you can check your email and you will see your message Hello world.
Here is the ssmtp guide i follow [http://www.havetheknowhow.com/Configure-the-server/Install-ssmtp.html](http://www.havetheknowhow.com/Configure-the-server/Install-ssmtp.html)

Now when you get this working you can move on to next part - installing and configurating Logwatch.
[B]
Installing and configurationg LOGWATCH to send security logs to your email account:[/B]

First we install Logwatch

```

sudo apt-get install logwatch

```

We have to create a directory that Logwatch dosent do by default.
Write the following code to create /var/cache/logwatch
```

sudo mkdir /var/cache/logwatch



```

Now we should not add and configurationg the logwatch.conf file using this path /usr/share/logwatch
We should copy logwatch.conf to /etc/logwatch/conf/ and that is the file we will configurate.
So now we copy the file using following code
```

sudo cp /usr/share/logwatch/default.conf/logwatch.conf /etc/logwatch/conf/

```

Now you open up the logwatch.conf file using following path

```

sudo nano /etc/logwatch/conf/logwatch.conf

```

First you change the output to mail and mailto with your email account.

```

Output = mail
MailTo = YourEmail@gmail.com
```

Then you can add your email again at this line

```
MailFrom = Logwatch



```

Now you can set the reports to yesterday or today - i pick Today

```

Range = Today

```

At last you can pick if you want low security issues or medium or high - i pick medium

```

Detail = Medium

```

Now you can test Logwatch to send security report to your mail.
Just write logwatch in the command line and check your email account.

```

sudo logwatch

```

I follow different guides to understand how to install and configurate Logwatch correct.
I post them in the order you should read and refering to the guides to understand what is correct settings with Logwatch.
First guide to use is [https://help.ubuntu.com/community/Logwatch](https://help.ubuntu.com/community/Logwatch)
Secound guide to use is [https://wiki.amahi.org/index.php/Monitor_System_Logs_via_E-mail](https://wiki.amahi.org/index.php/Monitor_System_Logs_via_E-mail)
And last guide to get more details [https://www.digitalocean.com/community/tutorials/how-to-install-and-use-logwatch-log-analyzer-and-reporter-on-a-vps](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-logwatch-log-analyzer-and-reporter-on-a-vps)

---

### Post by patrikmellq on 2015-06-08
You also might need to unlock the captcha by visiting this page [https://www.google.com/accounts/DisplayUnlockCaptcha](https://www.google.com/accounts/DisplayUnlockCaptcha)
But if the email working then there is no need.

Cheers

---

### Post by patrikmellq on 2015-06-08
I forgot to mention that you need to test your internet provider if they allow you to connect using smtp.gmail.com.

Here's a simple test.  Open a terminal and run the command:
     Code:
```


     telnet alt1.gmail-smtp-in.l.google.com 25
``` 
If you can connect, you'll see GMail reply with its "banner" like this:
     Code:[/code]
```

     Trying 74.125.24.27...
Connected to alt1.gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP s1si2787214wiy.52 - gsmt
``` 
If you don't see that, you'll need to talk to your ISP and make sure they are not filtering traffic to remote SMTP servers.
To close the telnet session, hold down the Ctrl key and type the "]" character.  Then type "quit" at the prompt.

---

### Post by CharlesA on 2015-06-08
Note, most ISPs I have seen will block any traffic on port 25 if the connection is residential. If this is the case, it is unlikely they will unblock it, so you would need to send email via port 587, instead of port 25.

This sounds like something that might be better suited for the wiki.

---

### Post by patrikmellq on 2015-06-09
Thanks CharlesA

Note, i will also check the cron job, the settings to get daily emails and add more details to this Howto ...

Cheers

---

### Post by patrikmellq on 2015-06-09
One cool thing happen to me - when i try to change settings with cron to get automatic emails by Logwatch - i wrote the wrong password for root using sudo and i got a email 2 secounds later - guess what - it was a security report from Logwatch.
HAHAHA that is pretty cool - my mobile phone sound pling and telling me i got a new email in the present time from Logwatch.

Feels great :-)

---

### Post by CharlesA on 2015-06-09
> **patrikmellq said:**
> Thanks CharlesA

Note, i will also check the cron job, the settings to get daily emails and add more details to this Howto ...

Cheers

I was thinking of moving to the the tutorials area, but I think it needs more detail.

As far as the security email you got was, was it actually from logwatch or are you running another login failure or intrusion detection software? I use CSF (and LFD) to keep an eye on changed files and login errors/successes.

---

### Post by patrikmellq on 2015-06-10
Hello CharlesA

I run Tripwire and made a HowTo on this forum - a member at this forum teach me how to do all settings and configuration.
I have the Tripwire database on removable media.

Some days have gone as the installation and cofiguration above and its working - i get security reports each day from Logwatch.
What would you suggest i should add to this HowTo? to make it more complete!

Cheers

Here is my Tripwire HowTo [http://ubuntuforums.org/showthread.php?t=2235300&highlight=tripwire](http://ubuntuforums.org/showthread.php?t=2235300&highlight=tripwire)

---

### Post by CharlesA on 2015-06-10
Tripwire should be a seperate thing. Logwatch is mostly used to monitor the logs and help system admins get an idea if they are having issues or not.

---

