---
title: "Send your logs/rootkits report on email"
date: 2008-08-25
forum: Security
---

### Post by qstraza on 2008-08-25
Well my system was hacked a week ago, so i decided to keep an extra eye on the logs and rootkits. You need 4 things in order to get this working. Luckily, all the packages are available via apt-get (dont you love this?)

well you need these
```
sudo apt-get install mutt rkhunter chkrootkit logwatch
```apt-get will install all the necessary packages... So lets get on.

You need an email script
```
#!/bin/bash
if [ $# -eq 0 ]; then
    echo Usage:
    echo $0 user@gmail.com subject attachment_file
    exit 1;
fi

date=`date +%d-%m-%y`
to=$1
sub=$2
subject="`hostname` $sub $date"
attach="$3"

mutt -s "$subject" -a $attach $to < /dev/null

```Copy this and paste it into a file named "email".
Save it in /usr/local/bin/ 
Also make sure you change it to executable file.
```
sudo mv email /usr/local/bin/
sudo chmod +x /usr/local/bin/email
```And try it if it works
```
echo "test 123" > readme ; email your@mail.here "testing script" readme ; rm readme
```If it works, you are good to continue, if it doesnt, please write here, i probably forgot what to install to get mutt to work.

Than you need a script which will be executed daily.

```

#!/bin/bash
date=`date +%d-%m-%y`
email="your email here"

## rkhunter
rkhunter --update
rkhunter --checkall --cronjob --report-warnings-only > rkhunter-check-$date.log
email $email rkhunter-check rkhunter-check-$date.log
rm rkhunter-check-$date.log
tar -cf rkhunter-log-$date.tar /var/log/rkhunter.log
gzip rkhunter-log-$date.tar
email $email rkhunter-log rkhunter-log-$date.tar.gz
rm rkhunter-log*.tar.gz

## chkrootkit
chkrootkit > chkrootkit-$date.log
email $email chkrootkit chkrootkit-$date.log
rm chkrootkit-$date.log

## logwatch
logwatch --output html --detail High --range All > logwatch-all-$date.html
logwatch --output html --detail High --range Today > logwatch-today-$date.html
logwatch --output html --detail High --range Yesterday > logwatch-yesterday-$date.html
email $email "logwatch all" logwatch-all-$date.html
email $email "logwatch today" logwatch-today-$date.html
email $email "logwatch yesterday" logwatch-yesterday-$date.html
rm -f logwatch-*.html


```Save it to what ever you like. Lets say "report-log". Chmod it and move to /etc/cron.daily/
```
sudo chmod +x report-log
sudo mv report-log /etc/cron.daily/
```Also make sure you change the email.

This is it. You should get few mails per day about your systems log and security...
I hope this helps. You can edit it and you can ask for questions, how to make.. etc

Please reply to let me know if it works with only these packages installed...

---

### Post by MJWitter on 2008-08-28
Hi, 

I really like this idea and have given it a try. All seems to run fine, except that I end up with a text file in my home directory instead of an email going out.  The test script gives the following(´...´=removed):

> From michael@... Thu Aug 28 23:35:24 2008
Date: Thu, 28 Aug 2008 23:35:24 +0200
From: ... <michael@...>
To: ...@....com
Subject: ... testing script 28-08-08
Message-ID: <20080828213524.GA9307@...>
MIME-Version: 1.0
Content-Type: multipart/mixed; boundary="k+w/mQv8wyuph6w0"
Content-Disposition: inline
User-Agent: Mutt/1.5.17+20080114 (2008-01-14)
Status: RO
Content-Length: 236
Lines: 13


--k+w/mQv8wyuph6w0
Content-Type: text/plain; charset=us-ascii
Content-Disposition: inline


--k+w/mQv8wyuph6w0
Content-Type: text/plain; charset=us-ascii
Content-Disposition: attachment; filename=readme

test 123

--k+w/mQv8wyuph6w0--


Any idea where I am going wrong?

Thanks in advance,
Michael

---

### Post by qstraza on 2008-08-28
install exim4.
```
sudo apt-get install exim4
```
Than run a setup for it
```
sudo dpkg-reconfigure exim4-config
```
Select the first option
```
internet site; mail is sent and received directly using SMTP
```

Than just press enter milion times, than try emailing again.```
echo "test 123" > readme ; email your@mail.here "testing script" readme ; rm readme
```

Please write the results

---

### Post by Camilia on 2008-08-29
qstraza 
Save it in /usr/sbin/ ? 
How do you save in /usr/sbin/?  I click save and get option of documents, pictures.

Pasted mutt rkhunter chkrootkit logwatch run and file not created yet. Create? Is this where i post the email?

Pressed internet site; mail is sent and received directly using SMTP and then got IP-addresses to listen on for incoming SMTP connections. Stopped there for uncertain what to do?

---

### Post by qstraza on 2008-08-29
copy this ```
#!/bin/bash
if [ $# -eq 0 ]; then
    echo Usage:
    echo $0 user@gmail.com subject attachment_file
    exit 1;
fi

date=`date +%d-%m-%y`
to=$1
sub=$2
subject="`hostname` $sub $date"
attach="$3"

mutt -s "$subject" -a $attach $to < /dev/null
```

and paste it in to a file.
Do it like in windows. Open your text editor, paste above code in it and save it in your home directory as email.
Than open a terminal type "cd" so you will be in your home dir and type "chmod +x email" and than "sudo mv email /usr/local/bin/", now your email script should be in /usr/local/bin/.

The same goes for ```
sudo apt-get install mutt rkhunter chkrootkit logwatch
```
Copy this and paste it in your TERMINAL. You should see stuff installing...

Than try that thing which sends you mail to check if it is working, and follow the steps...

Hope this helps, if not, ill try to explain it even more

---

### Post by Camilia on 2008-08-29
Now I am very confused. I don't know what a text editor is. Also why do make a program that is mailed to me. Seems this leaves an opening for a virus. I thought this to be a simple root test.

Why Get your logs/rootkit reports and send it to email daily?
I just want a program to scan my computer. For don't want to a chance that I accidentally let a virus in, as happened in windows after copying pictures for my avatar.

---

### Post by cariboo on 2008-08-30
To Camilla:

You can find a test editor in Applications-->Accessories-->Text Editor. You can use it to edit configuration files and create scripts.

to qstraza:

You should never save scripts in /usr/sbin, the proper place would be /usr/local/bin

Jim

---

### Post by qstraza on 2008-08-30
> **cariboo907 said:**
> To Camilla:

You can find a test editor in Applications-->Accessories-->Text Editor. You can use it to edit configuration files and create scripts.

to qstraza:

You should never save scripts in /usr/sbin, the proper place would be /usr/local/bin

Jim
Ok, changed, thanks

---

### Post by qstraza on 2008-08-30
> **Camilia said:**
> Now I am very confused. I don't know what a text editor is. Also why do make a program that is mailed to me. Seems this leaves an opening for a virus. I thought this to be a simple root test.

Why Get your logs/rootkit reports and send it to email daily?
I just want a program to scan my computer. For don't want to a chance that I accidentally let a virus in, as happened in windows after copying pictures for my avatar.
well if you dont like emailing reports, than you can edit the script, which wont send you an email but will save reports on hdd. Or you can run checking manually if you want

---

### Post by Camilia on 2008-08-30
You can run checking manually if you want. How is this done?
 
Clicked save. Save to kim as hd. 
#!/bin/bash
if [ $# -eq 0 ]; then
    echo Usage:
    echo $0 [email]user@gmail.com[/email] subject attachment_file
    exit 1;
fi

date=`date +%d-%m-%y`
to=$1
sub=$2
subject="`hostname` $sub $date"
attach="$3"

mutt -s "$subject" -a $attach $to < /dev/null

What does this mean?

If I save it as email where does the email get sent?

---

### Post by cariboo on 2008-08-30
Press Alt-F2 and enter:

```
gksu nautilus
```

enter your pass word and navigate to /var/log, this is where all the log files are located. You can open the logs in a text editor, by double clicking a file, nad then reading there.

Personally I use logwatch, but then again it emails me a copy everyday. To do this install exim4 and just use the default configuration.

Jim

---

### Post by MJWitter on 2008-08-30
Hi, 

I tried your suggestion and it still ends up in the sent file in home folder.. 
I tracked down the exim4 log file and the last entry is:
> 2008-08-31 00:11:23 1KZYey-0006ZS-C8 == [email]...@....com[/email] R=dnslookup defer (-1): host lookup did not complete

Would this be the problem(quite new here, but learning)?

Thanks again for your help!
Michael

---

### Post by Camilia on 2008-08-31
Pressed Alt +f2 and got run in terminal or with file
shows list of applications. Thus I am confused again. This not what you said would be there. Got no request for password.

---

### Post by qstraza on 2008-09-10
please write your problems again, we will try to figure them out together.
I just tried this from scratch and i works.

I have to use my isp's mail, cuz they are blocking port 25.

---

### Post by Camilia on 2008-09-10
I read that as long as I don't have a server roots can't get into my computer. I don't have a server so I am not going try to understand rootkit reports.

---

### Post by qstraza on 2008-09-10
well if your computer is not exposed online 24/7 than you probably dont need this.

---

### Post by qstraza on 2008-09-10
> **MJWitter said:**
> Hi, 

I tried your suggestion and it still ends up in the sent file in home folder.. 
I tracked down the exim4 log file and the last entry is:


Would this be the problem(quite new here, but learning)?

Thanks again for your help!
Michael
dns lookup faild, that indicated like the host of the email was wrong, could it be?

---

### Post by MJWitter on 2008-09-11
The email ad was ...@gmail.com, so it should have been fine.. 

I have been messing with the pc since then, so Im going to have to redo this when its up and running again. 

Thanks again for the help!

---

### Post by AgainstTheDarkArts on 2008-09-28
I'm also having trouble with this. When I run the test, nothing appears to happen. The terminal drops to the next line and a cursor.

I get no indication of success or failure, yet the email never reaches ...@gmail.com  or ...@yahoo.com.

edit: oops, the log file states:

2008-09-28 12:54:17 1KjzXB-0003Xe-RZ ** ...@gmail.com R=dnslookup T=remote_smtp: SMTP error from remote mail server after end of data: host gmail-smtp-in.l.google.com [xx.xxx.47.27]: 550-5.7.1 [xx.xx.xxx.xxx] The IP you're using to send mail is not authorized\n550-5.7.1 to send email directly to our servers. Please use the SMTP\n550-5.7.1 relay at your service provider instead. Learn more at\n550 5.7.1 [http://mail.google.com/support/bin/answer.py?answer=10336](http://mail.google.com/support/bin/answer.py?answer=10336) 6si1089221ywp.3

I have evolution set up and working correctly with gmail.  Can this script be modified to use evolution?  How would I do that?

---

### Post by qstraza on 2008-09-28
> **AgainstTheDarkArts said:**
>  relay at your service provider instead. 

Try using your isps email in test script, it should work.

---

### Post by Camilia on 2008-09-28
Re: Get your logs/rootkit reports and send it to email daily

---

### Post by g0nzal01 on 2008-10-06
thanks for all your help. i cant get past this test
echo "test 123" > readme ; email [email]your@mail.here[/email] "testing script" readme ; rm readme
 but it does not sent me the cron job once i have put it in there. 

thanx in advance,
g0nzal01

---

### Post by Freiheit on 2010-01-31
have to *bump* this, its really useable, especially for the rkhunter  checks to be sent via email. otherwise rkhunter would only send an email  like 'Perhaps your system is compromised, login to check', which is not  very useful.
All scripts work like a charm, thank you.

The described problems of the other users like Camilia and g0nzal01 are  not mentionable. A user, who does not know what a text editor is  (Camilla), or someone who does not even read your explanations and  changes 'your@mail.here' to something he can use (root@localhost for  desktop installations or a valid mailaddress for internet servers), wont  get the job done, no matter what.

Again, all works perfect with just  copy&paste, you spared me some hours of work. thank you

---

### Post by projectX on 2010-01-31
I know this was posted some time ago but I thought I would take a shot at it and since my computer is connected 24/7 to the net. I got everything installed and properly placed etc, etc but the one thing I keep running into a problem with is the test to see if it works properly and I keep getting:

> 
mjl08@michael:~$ echo "test 123" > readme ; email *******@gmail.com here "testing script" readme ; rm readme
Can't stat testing: No such file or directory
testing: unable to attach file.
mjl08@michael:~$ 


So I went back to double check everything and make sure I didn't miss a step, but I keep getting the same thing "shrug". It might be something simple that I just looked over but was wondering if any one else got this and if so, how did they fix it.

---

### Post by DZ* on 2010-02-01
> **qstraza said:**
> Well my system was hacked a week ago

What did they do to hack you?

---

### Post by sTpny on 2010-08-12
> **projectX said:**
> I know this was posted some time ago but I thought I would take a shot at it and since my computer is connected 24/7 to the net. I got everything installed and properly placed etc, etc but the one thing I keep running into a problem with is the test to see if it works properly and I keep getting:



So I went back to double check everything and make sure I didn't miss a step, but I keep getting the same thing "shrug". It might be something simple that I just looked over but was wondering if any one else got this and if so, how did they fix it.
I had the same issue. If I remember correctly You need to run mutt once without the > dev/null in order to have it ask to create a mail directory for you. once that's done, it should work. (my still isn't working though, but I get no visible errors anymore.

---

### Post by cariboo on 2010-08-12
Installing logwatch, which is in the repositories, accomplishes the same thing. If I remember correctly it installs postfix as a dependency, then all you have to do setup where you and how you want the email sent.

---

### Post by sTpny on 2010-08-17
Hello people.. 

I've made a set of scripts based mainly on these scripts.. The only real difference is that the setup is more automatic, and it also sets the computer up for remote administration, only it isn't working, and I can't seem to make it work.. 

[http://ubuntuforums.org/showthread.php?p=9728883#post9728883](http://ubuntuforums.org/showthread.php?p=9728883#post9728883)

I need to run this script on a dozen (and growing) or so computers that I need to keep running smoothly. I've been taking care of them in person, but I need to be able to do it remotely as well, because I'm moving at the end of next month.  All help is greatly appreciated. Thanks.

---

